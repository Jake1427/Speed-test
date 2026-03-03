import React, { useState, useEffect, useRef, useMemo } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { motion, AnimatePresence } from "framer-motion";
import { LineChart, Line, XAxis, YAxis, Tooltip, ResponsiveContainer, CartesianGrid } from "recharts";

/* =========================
   CONFIG / UTILITIES
========================= */

const WORD_BANK = [
  "focus","speed","clean","minimal","keyboard","reaction","accuracy","precision","smooth","timing",
  "design","motion","simple","modern","rapid","flow","track","sharp","logic","swift",
  "stable","robust","future","optimize","latency","memory","signal","frame","render","input"
];

const TIME_OPTIONS = [1,5,10,30];

function generateWords(count = 40) {
  return Array.from({ length: count }, () =>
    WORD_BANK[Math.floor(Math.random() * WORD_BANK.length)]
  );
}

function ratingWPM(wpm){
  if(wpm < 30) return "Beginner";
  if(wpm < 50) return "Solid";
  if(wpm < 70) return "Fast";
  if(wpm < 90) return "Cracked";
  return "Elite";
}

function ratingCPS(cps){
  if(cps < 4) return "Casual";
  if(cps < 6) return "Quick";
  if(cps < 8) return "Fast";
  if(cps < 10) return "Speed Demon";
  return "Inhuman";
}

/* =========================
   MAIN COMPONENT
========================= */

export default function SpeedTestApp(){

  const [mode,setMode] = useState("typing");
  const [timeLimit,setTimeLimit] = useState(10);
  const [timeLeft,setTimeLeft] = useState(10);
  const [isActive,setIsActive] = useState(false);
  const [darkMode,setDarkMode] = useState(false);

  const [words,setWords] = useState(generateWords());
  const [input,setInput] = useState("");
  const [startedTyping,setStartedTyping] = useState(false);

  const [clicks,setClicks] = useState(0);

  const [reactionState,setReactionState] = useState("idle");
  const [reactionStart,setReactionStart] = useState(null);
  const [reactionTime,setReactionTime] = useState(null);

  const [history,setHistory] = useState([]);
  const [popup,setPopup] = useState(null);

  const intervalRef = useRef(null);
  const timeoutRef = useRef(null);
  const inputRef = useRef(null);

/* =========================
   RESET / SAFETY
========================= */

  const clearTimers = () => {
    if(intervalRef.current) clearInterval(intervalRef.current);
    if(timeoutRef.current) clearTimeout(timeoutRef.current);
  };

  useEffect(()=>{
    return ()=> clearTimers();
  },[]);

  useEffect(()=>{
    setTimeLeft(timeLimit);
  },[timeLimit]);

/* =========================
   TYPING MODE
========================= */

  const startTyping = () => {
    clearTimers();
    setWords(generateWords());
    setInput("");
    setStartedTyping(false);
    setTimeLeft(timeLimit);
    setIsActive(true);
    setTimeout(()=> inputRef.current?.focus(),100);
  };

  const finishTyping = () => {
    clearTimers();
    setIsActive(false);

    const typedWords = input.trim().split(/\s+/);
    let totalChars = 0;
    let correctChars = 0;

    words.forEach((word,i)=>{
      totalChars += word.length;
      if(!typedWords[i]) return;
      for(let j=0;j<word.length;j++){
        if(typedWords[i][j] === word[j]) correctChars++;
      }
    });

    const minutes = timeLimit/60;
    const wpm = Math.max(0,Math.round((correctChars/5)/minutes));
    const accuracy = totalChars === 0 ? 0 : Math.round((correctChars/totalChars)*100);

    const result = { id: Date.now(), mode:"typing", score:wpm, accuracy };
    setHistory(prev=>[...prev,result]);

    setPopup({
      title:`${wpm} WPM`,
      subtitle:`${accuracy}% Accuracy`,
      rating:ratingWPM(wpm)
    });
  };

  const handleTyping = (e) => {
    if(!startedTyping){
      setStartedTyping(true);
      intervalRef.current = setInterval(()=>{
        setTimeLeft(prev=>{
          if(prev<=1){ finishTyping(); return 0; }
          return prev-1;
        });
      },1000);
    }
    setInput(e.target.value);
  };

  const typedWords = input.split(" ");

/* =========================
   CLICKING MODE
========================= */

  const startClicking = () => {
    clearTimers();
    setClicks(0);
    setTimeLeft(timeLimit);
    setIsActive(true);

    intervalRef.current = setInterval(()=>{
      setTimeLeft(prev=>{
        if(prev<=1){ finishClicking(); return 0; }
        return prev-1;
      });
    },1000);
  };

  const finishClicking = () => {
    clearTimers();
    setIsActive(false);

    const cps = Number((clicks/timeLimit).toFixed(2));
    const result = { id: Date.now(), mode:"clicking", score:cps };
    setHistory(prev=>[...prev,result]);

    setPopup({
      title:`${cps} CPS`,
      subtitle:`${clicks} clicks in ${timeLimit}s`,
      rating:ratingCPS(cps)
    });
  };

/* =========================
   REACTION MODE
========================= */

  const startReaction = () => {
    clearTimers();
    setReactionTime(null);
    setReactionState("red");

    const yellowDelay = 400 + Math.random()*1200;
    const greenDelay = yellowDelay + 600 + Math.random()*2000;

    timeoutRef.current = setTimeout(()=>setReactionState("yellow"),yellowDelay);
    setTimeout(()=>{
      setReactionState("green");
      setReactionStart(performance.now());
    },greenDelay);
  };

  const handleReactionClick = () => {
    if(reactionState === "green"){
      const delay = Math.round(performance.now() - reactionStart);
      setReactionTime(delay);
      setReactionState("idle");

      const result = { id: Date.now(), mode:"reaction", score:delay };
      setHistory(prev=>[...prev,result]);

      setPopup({
        title:`${delay} ms`,
        subtitle:`Reaction time`,
        rating: delay < 200 ? "Insane" : delay < 250 ? "Fast" : "Human"
      });
    }
    else if(reactionState !== "idle"){
      setReactionTime("Too Early");
      setReactionState("idle");
    }
  };

/* =========================
   PERSONAL BEST
========================= */

  const personalBest = useMemo(()=>{
    const filtered = history.filter(h=>h.mode===mode);
    if(filtered.length===0) return null;

    if(mode === "reaction"){
      return Math.min(...filtered.map(h=>h.score));
    }
    return Math.max(...filtered.map(h=>h.score));
  },[history,mode]);

/* =========================
   STYLES
========================= */

  const containerClass = darkMode
    ? "min-h-screen bg-black text-white flex items-center justify-center p-4"
    : "min-h-screen bg-gray-50 text-black flex items-center justify-center p-4";

/* =========================
   UI
========================= */

  return (
    <div className={containerClass}>
      <Card className="w-full max-w-4xl rounded-2xl shadow-xl">
        <CardContent className="p-6 sm:p-10 space-y-8">

          {/* Header */}
          <div className="flex justify-between items-center">
            <h1 className="text-2xl font-semibold">Speed Lab</h1>
            <Button variant="outline" onClick={()=>setDarkMode(!darkMode)}>
              {darkMode?"Light":"Dark"}
            </Button>
          </div>

          {/* Mode */}
          <div className="flex gap-3 justify-center flex-wrap">
            {["typing","clicking","reaction"].map(m=> (
              <Button key={m} variant={mode===m?"default":"outline"} onClick={()=>setMode(m)}>
                {m.charAt(0).toUpperCase()+m.slice(1)}
              </Button>
            ))}
          </div>

          {/* Time */}
          {mode!=="reaction" && (
            <div className="flex gap-2 justify-center flex-wrap">
              {TIME_OPTIONS.map(t=>(
                <Button key={t} variant={timeLimit===t?"default":"outline"} onClick={()=>setTimeLimit(t)}>
                  {t}s
                </Button>
              ))}
            </div>
          )}

          {/* PERSONAL BEST */}
          {personalBest !== null && (
            <div className="text-center text-sm opacity-70">
              Personal Best: {personalBest} {mode==="reaction"?"ms":mode==="typing"?"WPM":"CPS"}
            </div>
          )}

          {/* TYPING */}
          {mode==="typing" && (
            <div className="space-y-4">
              <div className="text-center">Time: {timeLeft}s</div>

              <div className="relative border rounded-xl p-4 min-h-[120px] text-lg leading-relaxed break-words cursor-text"
                onClick={()=>inputRef.current?.focus()}>
                {words.map((word,i)=>{
                  const typed = typedWords[i];
                  let color="";
                  if(typed!=null){
                    color = typed===word?"text-green-500":"text-red-500";
                  }
                  return <span key={i} className={`${color} mr-2`}>{word}</span>;
                })}
                <input
                  ref={inputRef}
                  value={input}
                  onChange={handleTyping}
                  disabled={!isActive}
                  className="absolute inset-0 w-full h-full opacity-0"
                />
              </div>

              <div className="flex justify-center">
                {!isActive ?
                  <Button onClick={startTyping}>Start</Button>
                  : <Button variant="outline" onClick={finishTyping}>Stop</Button>
                }
              </div>
            </div>
          )}

          {/* CLICKING */}
          {mode==="clicking" && (
            <div className="space-y-6 text-center">
              <div>Time: {timeLeft}s</div>
              <motion.div whileTap={{scale:0.9}}
                className="w-40 h-40 mx-auto rounded-2xl bg-black text-white flex items-center justify-center text-xl font-semibold cursor-pointer"
                onClick={()=> isActive && setClicks(c=>c+1)}>
                Click
              </motion.div>
              {!isActive ?
                <Button onClick={startClicking}>Start</Button>
                : <div>{clicks} clicks</div>
              }
            </div>
          )}

          {/* REACTION */}
          {mode==="reaction" && (
            <div className="space-y-6 text-center">
              <div
                onClick={handleReactionClick}
                className={`w-40 h-40 mx-auto rounded-2xl flex items-center justify-center text-white text-xl font-semibold cursor-pointer
                ${reactionState==="red"?"bg-red-500":""}
                ${reactionState==="yellow"?"bg-yellow-400 text-black":""}
                ${reactionState==="green"?"bg-green-500":""}
                ${reactionState==="idle"?"bg-gray-400":""}`}
              >
                {reactionState==="idle"?"Wait":reactionState.toUpperCase()}
              </div>
              <Button onClick={startReaction}>Start</Button>
            </div>
          )}

          {/* GRAPH */}
          {history.length>0 && (
            <div className="pt-6">
              <ResponsiveContainer width="100%" height={250}>
                <LineChart data={history.filter(h=>h.mode===mode)}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="id" hide />
                  <YAxis />
                  <Tooltip />
                  <Line type="monotone" dataKey="score" strokeWidth={3} dot />
                </LineChart>
              </ResponsiveContainer>
            </div>
          )}

          {/* POPUP */}
          <AnimatePresence>
            {popup && (
              <motion.div
                initial={{opacity:0,y:20}}
                animate={{opacity:1,y:0}}
                exit={{opacity:0}}
                className="fixed bottom-6 right-6 bg-black text-white px-6 py-4 rounded-2xl shadow-2xl">
                <div className="text-lg font-semibold">{popup.title}</div>
                <div className="text-sm opacity-70">{popup.subtitle}</div>
                <div className="text-sm mt-1">{popup.rating}</div>
                <div className="text-right mt-2">
                  <Button size="sm" variant="outline" onClick={()=>setPopup(null)}>Close</Button>
                </div>
              </motion.div>
            )}
          </AnimatePresence>

        </CardContent>
      </Card>
    </div>
  );
}
