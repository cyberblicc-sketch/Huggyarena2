# HuggyArena.pdf Extracted Text

Source file: `HuggyArena.pdf`
Total pages: **80**

## Page 1

```text
import React, { useState, useMemo, useEffect, useRef, useCallback } from "react";
import {
  Search, Bell, User, Wallet, TrendingUp, ChevronRight, ChevronLeft,
  ChevronDown, ChevronUp, X, Plus, Minus, Check, AlertCircle, Info,
  ArrowUpRight, ArrowDownRight, ArrowRight, ArrowLeft, Clock, Calendar,
  Filter, SortAsc, MoreHorizontal, Share2, Bookmark, MessageCircle,
  Trophy, Target, Zap, Sparkles, Activity, BarChart3, PieChart,
  Settings, LogOut, HelpCircle, Shield, Mail, Send, Coins, Gift,
  CreditCard, DollarSign, Receipt, History, Eye, EyeOff, Lock,
  Globe, MapPin, Flag, Heart, ThumbsUp, ThumbsDown, Star, Award,
  Users, Hash, Tag, Layers, Grid, List, Menu, Home, Compass,
  Briefcase, Bot, FileText, ExternalLink, Copy, RefreshCw, Loader2,
  ArrowUpDown, Repeat, ArrowDownUp, ChevronsRight, Crown, Medal,
  Flame, Newspaper, Quote, Pin, CircleDot, Diamond, Hexagon, Circle,
  Square, Triangle, BookOpen, Library, Gauge, AlertTriangle,
  ShieldCheck, ShieldAlert, BadgeCheck, Verified, CircleHelp,
  Asterisk, Slash, Equal, Smile, Image as ImageIcon, Paperclip, Mic,
} from "lucide-react";
import {
  AreaChart, Area, LineChart, Line, BarChart, Bar, XAxis, YAxis,
  Tooltip, ResponsiveContainer, CartesianGrid, ReferenceLine,
  RadialBarChart, RadialBar, PolarAngleAxis,
} from "recharts";
/* ============================================================================
   HUGGY ARENA / HUGGYPREDICT — v3.0 "NEWSPRINT TERMINAL"
   Pre-deployment-ready single-file artifact. Editorial aesthetic.
   ============================================================================ */
const THEME_STYLES = `
@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;9..144,400;9..144,500;9..144,600;9..144,700;9..144,800&family=Geist:wght@300;400;500;600;700&family=Geist+Mono:wght@400;500;600&display=swap');
:root {
  --paper: #f5f1e8; --paper-2: #ede7d8; --paper-3: #e3dcc9;
  --ink: #1c1917; --ink-2: #44403c; --ink-3: #78716c; --ink-4: #a8a29e;
  --rule: #d6cfba; --rule-soft: #e3dcc9;
  --amber: #c2410c; --amber-soft: #fed7aa; --amber-deep: #7c2d12;
  --yes: #15803d; --yes-soft: #bbf7d0; --yes-deep: #14532d;
  --no:  #9f1239; --no-soft: #fecdd3; --no-deep: #4c0519;
  --gold: #b45309; --gold-soft: #fde68a;
  --shadow: 0 1px 0 rgba(28,25,23,.04), 0 2px 8px rgba(28,25,23,.06);
  --shadow-lift: 0 1px 0 rgba(28,25,23,.06), 0 12px 32px -12px rgba(28,25,23,.18);
}
.ha-root { font-family: 'Geist', ui-sans-serif, system-ui, sans-serif; background: var(--paper); color: var(--ink); -webkit-font-smoothing: antialiased; font-feature-settings: 'ss01','cv11','tnum'; }
.ha-display { font-family: 'Fraunces', ui-serif, Georgia, serif; font-variation-settings: "opsz" 144, "SOFT" 30; letter-spacing: -0.012em; }
```

## Page 2

```text
.ha-display-italic { font-family: 'Fraunces', serif; font-style: italic; font-variation-settings: "opsz" 144, "SOFT" 100; }
.ha-mono { font-family: 'Geist Mono', ui-monospace, monospace; font-feature-settings: 'tnum','zero','ss01'; }
.ha-tnum { font-variant-numeric: tabular-nums; font-feature-settings: 'tnum'; }
.ha-smcp { font-variant: small-caps; letter-spacing: 0.08em; text-transform: lowercase; }
.ha-caps { letter-spacing: 0.14em; text-transform: uppercase; font-size: 0.68rem; font-weight: 500; }
.ha-paper { background: radial-gradient(circle at 20% 30%, rgba(196,134,32,.04), transparent 60%), radial-gradient(circle at 80% 70%, rgba(78,52,46,.03), transparent 50%), var(--paper); }
.ha-paper-card { background: var(--paper); position: relative; }
.ha-paper-card::before { content: ""; position: absolute; inset: 0; background-image: radial-gradient(rgba(28,25,23,.02) 1px, transparent 1px); background-size: 4px 4px; pointer-events: none; border-radius: inherit; opacity: 0.5; }
.ha-rule { border-top: 1px dotted var(--rule); }
.ha-rule-v { border-left: 1px dotted var(--rule); }
.ha-rule-thick { border-top: 2px solid var(--ink); }
.ha-rule-double { border-top: 4px double var(--ink); }
.ha-dropcap::first-letter { font-family: 'Fraunces', serif; font-weight: 600; font-size: 3.6em; line-height: 0.85; float: left; padding: .12em .08em 0 0; color: var(--ink); }
.ha-tick { font-family: 'Geist Mono', monospace; font-feature-settings: 'tnum','zero'; letter-spacing: -0.015em; }
.ha-hov { transition: transform .18s ease, box-shadow .18s ease, border-color .18s ease; }
.ha-hov:hover { transform: translateY(-1px); box-shadow: var(--shadow-lift); }
.ha-chip { display: inline-flex; align-items: center; gap: 4px; padding: 3px 8px; border: 1px solid var(--rule); border-radius: 999px; font-size: 11px; background: var(--paper); }
.ha-chip-solid { background: var(--ink); color: var(--paper); border-color: var(--ink); }
.ha-btn { display: inline-flex; align-items: center; justify-content: center; gap: 6px; height: 40px; padding: 0 16px; font-weight: 500; font-size: 14px; border-radius: 6px; border: 1px solid var(--ink); background: var(--ink); color: var(--paper); transition: all .15s ease; cursor: pointer; }
.ha-btn:hover { background: var(--ink-2); }
.ha-btn:active { transform: translateY(1px); }
.ha-btn:disabled { opacity: 0.4; cursor: not-allowed; }
.ha-btn-ghost { background: transparent; color: var(--ink); }
.ha-btn-ghost:hover { background: var(--paper-2); }
.ha-btn-amber { background: var(--amber); border-color: var(--amber); color: #fff; }
.ha-btn-amber:hover { background: var(--amber-deep); }
.ha-btn-yes { background: var(--yes); border-color: var(--yes); color: #fff; }
.ha-btn-no { background: var(--no); border-color: var(--no); color: #fff; }
.ha-btn-sm { height: 32px; padding: 0 12px; font-size: 13px; }
.ha-btn-lg { height: 48px; padding: 0 20px; font-size: 15px; }
.ha-input { width: 100%; height: 44px; padding: 0 14px; font-size: 15px; font-family: 'Geist', sans-serif; background: var(--paper); border: 1px solid var(--rule); border-radius: 6px; color: var(--ink); transition: border-color .15s ease; }
.ha-input:focus { outline: none; border-color: var(--ink); box-shadow: 0 0 0 3px rgba(28,25,23,.06); }
.ha-card { background: var(--paper); border: 1px solid var(--rule); border-radius: 8px; }
.ha-bdg { display: inline-flex; align-items: center; gap: 3px; padding: 2px 7px; border-radius: 4px; font-size: 11px; font-weight: 500; letter-spacing: 0.02em; }
.ha-bdg-yes { background: var(--yes-soft); color: var(--yes-deep); }
.ha-bdg-no  { background: var(--no-soft);  color: var(--no-deep);  }
.ha-bdg-amber { background: var(--amber-soft); color: var(--amber-deep); }
.ha-bdg-ink { background: var(--ink); color: var(--paper); }
.ha-bdg-soft { background: var(--paper-2); color: var(--ink-2); border: 1px solid var(--rule); }
.ha-pbar { height: 6px; border-radius: 3px; background: var(--paper-2); overflow: hidden; position: relative; }
.ha-pbar-fill { height: 100%; background: var(--ink); transition: width .4s ease; }
.ha-pbar-yes { background: var(--yes); }
.ha-pbar-no  { background: var(--no);  }
.ha-split { display: flex; height: 6px; border-radius: 3px; overflow: hidden; background: var(--paper-2); }
.ha-split-y { background: var(--yes); }
.ha-split-n { background: var(--no);  }
.ha-scroll { overflow-x: auto; scrollbar-width: none; -ms-overflow-style: none; }
```

## Page 3

```text
.ha-scroll::-webkit-scrollbar { display: none; }
@keyframes ha-fade-up { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }
.ha-fade { animation: ha-fade-up .35s ease both; }
.ha-d-1 { animation-delay: .04s; } .ha-d-2 { animation-delay: .08s; } .ha-d-3 { animation-delay: .12s; }
.ha-d-4 { animation-delay: .16s; } .ha-d-5 { animation-delay: .20s; } .ha-d-6 { animation-delay: .24s; } .ha-d-7 { animation-delay: .28s; }
@keyframes ha-marq { from { transform: translateX(0); } to { transform: translateX(-50%); } }
.ha-marquee { display: flex; white-space: nowrap; animation: ha-marq 60s linear infinite; }
.ha-udot { background-image: linear-gradient(90deg, var(--ink-3) 50%, transparent 0); background-size: 4px 1px; background-repeat: repeat-x; background-position: 0 100%; padding-bottom: 2px; }
@keyframes ha-pulse { 0%,100% { opacity: .4; } 50% { opacity: 1; } }
.ha-pulse { animation: ha-pulse 2s ease-in-out infinite; }
.ha-root, .ha-root * { -webkit-tap-highlight-color: transparent; }
input, textarea, select { font-size: 16px; }
@media (min-width: 768px) { input, textarea, select { font-size: 15px; } }
.ha-safe-bottom { padding-bottom: env(safe-area-inset-bottom, 12px); }
.ha-safe-top { padding-top: env(safe-area-inset-top, 12px); }
.ha-line-clamp-2 { display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }
.ha-line-clamp-3 { display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden; }
`;
/* ---------- HELPERS ---------- */
const fmt = {
  sc: (cents, opts = {}) => (cents / 100).toLocaleString("en-US", { minimumFractionDigits: opts.precise ? 2 : 0, maximumFractionDigits: 2 }),
  usd: (cents) => "$" + (cents / 100).toLocaleString("en-US", { minimumFractionDigits: 2, maximumFractionDigits: 2 }),
  gc: (count) => count >= 1_000_000 ? (count/1_000_000).toFixed(1).replace(/\.0$/,"")+"M" : count >= 10_000 ? (count/1_000).toFixed(1).replace(/\.0$/,"")+"K" : count.toLocaleString(),
  pct: (bps, d=0) => (bps/100).toFixed(d)+"%",
  rel: (iso) => {
    const d = new Date(iso); const now = new Date(); const ms = now - d;
    if (ms < 0) { const a=Math.abs(ms); const m=Math.floor(a/60000); const h=Math.floor(a/3600000); const dy=Math.floor(a/86400000); if (dy>0) return "in "+dy+"d"; if (h>0) return "in "+h+"h"; return "in "+m+"m"; }
    const m=Math.floor(ms/60000); const h=Math.floor(ms/3600000); const dy=Math.floor(ms/86400000);
    if (dy>7) return d.toLocaleDateString("en-US",{month:"short",day:"numeric"});
    if (dy>0) return dy+"d ago"; if (h>0) return h+"h ago"; if (m>0) return m+"m ago"; return "just now";
  },
  date: (iso) => new Date(iso).toLocaleDateString("en-US",{month:"short",day:"numeric"}),
  dateLong: (iso) => new Date(iso).toLocaleDateString("en-US",{month:"short",day:"numeric",year:"numeric"}),
  time: (iso) => new Date(iso).toLocaleTimeString("en-US",{hour:"numeric",minute:"2-digit"}),
};
function quoteStake({ side, amountCents, yesPool, noPool }) {
  if (amountCents <= 0) return null;
  const totalFeeBps = 300;
  const fee = Math.floor((amountCents * totalFeeBps) / 10000);
  const stakeNet = amountCents - fee;
  const totalPool = yesPool + noPool;
  const sidePool = side === "YES" ? yesPool : noPool;
  const LMSR_THRESHOLD = 10000;
  let impliedBefore, impliedAfter;
  if (totalPool < LMSR_THRESHOLD) {
```

## Page 4

```text
    const w = totalPool / LMSR_THRESHOLD;
    const partPari = totalPool === 0 ? 0.5 : sidePool / totalPool;
    impliedBefore = (1 - w) * 0.5 + w * partPari;
    const sidePool2 = sidePool + stakeNet; const totalPool2 = totalPool + stakeNet;
    const w2 = totalPool2 / LMSR_THRESHOLD;
    const partPari2 = sidePool2 / totalPool2;
    impliedAfter = w2 >= 1 ? partPari2 : (1 - w2) * 0.5 + w2 * partPari2;
  } else {
    impliedBefore = sidePool / totalPool;
    const sidePool2 = sidePool + stakeNet;
    impliedAfter = sidePool2 / (totalPool + stakeNet);
  }
  const odds = 1 / impliedAfter;
  const potential = Math.floor(stakeNet * odds);
  return { ok: true, fee, stakeNet, potential, impliedBefore: Math.round(impliedBefore*10000), impliedAfter: Math.round(impliedAfter*10000) };
}
/* ---------- DATA ---------- */
const CATEGORIES = [
  { id: "ai",       label: "AI & Models", count: 84, color: "#c2410c" },
  { id: "politics", label: "Politics",    count: 56, color: "#7c2d12" },
  { id: "crypto",   label: "Crypto",      count: 42, color: "#b45309" },
  { id: "sports",   label: "Sports",      count: 67, color: "#15803d" },
  { id: "tech",     label: "Tech",        count: 38, color: "#1c1917" },
  { id: "culture",  label: "Culture",     count: 24, color: "#9f1239" },
  { id: "weather",  label: "Climate",     count: 18, color: "#0c4a6e" },
];
function generateSeries(currentProb, days, vol) {
  const series = []; let p = 0.5;
  for (let i = 0; i < days; i++) {
    const drift = (currentProb - p) * 0.05;
    const noise = (Math.random() - 0.5) * vol;
    p = Math.max(0.02, Math.min(0.98, p + drift + noise));
    const d = new Date(); d.setDate(d.getDate() - (days - i));
    series.push({ day: i, date: d.toISOString().slice(0, 10), p: Math.round(p*10000), pct: Math.round(p*100), vol: Math.floor(Math.random()*8000+2000) });
  }
  series[series.length-1].p = Math.round(currentProb*10000);
  series[series.length-1].pct = Math.round(currentProb*100);
  return series;
}
const MARKETS = [
  { id: "m_gpt5_2026", slug: "gpt5-released-2026", question: "Will OpenAI release GPT-5 (or the model marketed as such) before December 31, 2026?", description: "Resolves YES if OpenAI publicly releases an API or product named GPT-5, GPT-5-class, or the model OpenAI markets as their next flagship after GPT-4 successors, on or before 2026-12-31 23:59 ET.", category: "ai", creator: "@huggingface_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-07T23:59:00Z", status: "open", yesPool: 387400, noPool: 124200, volume24h: 18420, traders: 1247, comments: 89, pinned: true, image: "ai-grad", series: generateSeries(0.76, 90, 0.04) },
  { id: "m_llama5",  slug: "llama5-summer-2026", question: "Will Meta release Llama 5 with a permissive commercial license before September 1, 2026?", description: "Resolves YES if Meta publicly releases Llama 5 (or any model marketed as the successor to Llama 4) under the existing Llama Community License or any more permissive license before 2026-09-01 23:59 ET.", category: "ai", creator: "@arena_oracle", creatorVerified: true, closeAt: "2026-09-01T23:59:00Z", resolveAt: "2026-09-08T23:59:00Z", status: "open", yesPool: 218600, noPool: 312700, volume24h: 9840, traders: 612, comments: 47, image: "llama", series: generateSeries(0.41, 60, 0.05) },
  { id: "m_anthropic_ipo", slug: "anthropic-ipo-2026", question: "Will Anthropic file an S-1 with the SEC before January 1, 2027?", description: "Resolves YES upon public filing of S-1 (or F-1 for foreign private issuer) by Anthropic PBC with the U.S. Securities and Exchange Commission before 2027-01-01.", category: "ai", creator: "@huggingface_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-07T23:59:00Z", status: "open", yesPool: 84300, noPool: 416800, volume24h: 12200, traders: 894, comments: 134, image: "ipo", series: generateSeries(0.17, 90, 0.03) },
```

## Page 5

```text
  { id: "m_btc_120k", slug: "btc-120k-eoy-2026", question: "Will Bitcoin close above $120,000 on December 31, 2026?", description: "Resolves YES if BTC/USD closing price on the Coinbase exchange on 2026-12-31 23:59 UTC is greater than or equal to $120,000.00.", category: "crypto", creator: "@arena_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-01T23:59:00Z", status: "open", yesPool: 612300, noPool: 588100, volume24h: 41700, traders: 2814, comments: 401, image: "btc", series: generateSeries(0.51, 120, 0.06) },
  { id: "m_eth_8k", slug: "eth-8k-2026", question: "Will Ethereum (ETH) trade above $8,000 at any point in 2026?", description: "Resolves YES if ETH/USD on Coinbase reaches or exceeds $8,000.00 in any 1-minute interval between 2026-01-01 00:00 UTC and 2026-12-31 23:59 UTC.", category: "crypto", creator: "@arena_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-01T23:59:00Z", status: "open", yesPool: 198400, noPool: 286700, volume24h: 14300, traders: 1042, comments: 167, image: "eth", series: generateSeries(0.41, 90, 0.05) },
  { id: "m_warriors_2026", slug: "warriors-finals-2026", question: "Will the Golden State Warriors reach the 2026 NBA Finals?", description: "Resolves YES if the Golden State Warriors win their conference finals series in the 2025-26 NBA Playoffs.", category: "sports", creator: "@espn_partner", creatorVerified: true, closeAt: "2026-05-30T23:59:00Z", resolveAt: "2026-06-02T23:59:00Z", status: "open", yesPool: 142800, noPool: 387900, volume24h: 22100, traders: 1894, comments: 312, image: "warriors", series: generateSeries(0.27, 60, 0.07) },
  { id: "m_election_dem", slug: "midterm-house-dem-2026", question: "Will Democrats win the U.S. House majority in November 2026?", description: "Resolves YES if Democratic candidates win 218 or more seats in the November 2026 U.S. House elections, per AP race calls within 30 days of polls closing.", category: "politics", creator: "@huggingface_oracle", creatorVerified: true, closeAt: "2026-11-03T23:59:00Z", resolveAt: "2026-12-03T23:59:00Z", status: "open", yesPool: 287400, noPool: 412600, volume24h: 31800, traders: 2417, comments: 587, pinned: true, image: "election", series: generateSeries(0.41, 180, 0.04) },
  { id: "m_apple_vrai", slug: "apple-ai-glasses-2026", question: "Will Apple announce smart glasses with on-device AI before December 31, 2026?", description: "Resolves YES upon Apple's official announcement (keynote, press release, or SEC filing) of consumer smart glasses with on-device AI features, before 2026-12-31 23:59 ET.", category: "tech", creator: "@arena_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-07T23:59:00Z", status: "open", yesPool: 96400, noPool: 188300, volume24h: 7100, traders: 514, comments: 78, image: "apple", series: generateSeries(0.34, 90, 0.04) },
  { id: "m_tswift_album", slug: "taylor-swift-album-2026", question: "Will Taylor Swift release a new studio album in 2026?", description: "Resolves YES if a new full-length studio album by Taylor Swift is released on a major streaming platform (Spotify, Apple Music) during calendar year 2026.", category: "culture", creator: "@arena_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-07T23:59:00Z", status: "open", yesPool: 174200, noPool: 89600, volume24h: 5900, traders: 408, comments: 92, image: "tswift", series: generateSeries(0.66, 90, 0.04) },
  { id: "m_recession_2026", slug: "us-recession-2026", question: "Will the U.S. enter a recession (NBER definition) by Q4 2026?", description: "Resolves YES if the National Bureau of Economic Research declares a U.S. recession with start date on or before Q4 2026, based on official NBER announcement.", category: "politics", creator: "@huggingface_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-03-31T23:59:00Z", status: "open", yesPool: 198700, noPool: 412400, volume24h: 11400, traders: 1142, comments: 248, image: "recession", series: generateSeries(0.32, 180, 0.05) },
  { id: "m_climate_15c", slug: "global-temp-15c-2026", question: "Will global average temperature exceed +1.5C above pre-industrial in calendar 2026?", description: "Resolves YES if the Copernicus Climate Change Service reports global mean surface temperature for January-December 2026 above +1.5C relative to the 1850-1900 baseline.", category: "weather", creator: "@huggingface_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-02-15T23:59:00Z", status: "open", yesPool: 308700, noPool: 142300, volume24h: 8800, traders: 691, comments: 134, image: "climate", series: generateSeries(0.68, 120, 0.03) },
  { id: "m_huggy_5m", slug: "huggingface-5m-models-2026", question: "Will Hugging Face host more than 5,000,000 public models by end of 2026?", description: "Resolves YES if the public model count on huggingface.co/models is greater than 5,000,000 on 2026-12-31 23:59 UTC.", category: "ai", creator: "@huggingface_oracle", creatorVerified: true, closeAt: "2026-12-31T23:59:00Z", resolveAt: "2027-01-07T23:59:00Z", status: "open", yesPool: 412600, noPool: 87400, volume24h: 14200, traders: 982, comments: 167, pinned: true, image: "hf", series: generateSeries(0.83, 90, 0.03) },
];
const POSITIONS = [
  { id: "p1", marketId: "m_gpt5_2026", side: "YES", stakeCents: 5000, entryProbBps: 6800, openedAt: "2026-04-12T14:22:00Z" },
  { id: "p2", marketId: "m_btc_120k", side: "NO", stakeCents: 12000, entryProbBps: 5400, openedAt: "2026-04-18T09:11:00Z" },
  { id: "p3", marketId: "m_warriors_2026", side: "YES", stakeCents: 3500, entryProbBps: 3200, openedAt: "2026-04-22T19:45:00Z" },
  { id: "p4", marketId: "m_huggy_5m", side: "YES", stakeCents: 8000, entryProbBps: 7900, openedAt: "2026-04-08T11:30:00Z" },
  { id: "p5", marketId: "m_election_dem", side: "NO", stakeCents: 7500, entryProbBps: 6100, openedAt: "2026-04-25T16:08:00Z" },
];
const TRANSACTIONS = [
  { id: "t1", ts: "2026-04-29T10:42:00Z", currency: "SC", direction: "credit", amount: 1000, reason: "amoe", note: "Mail-in entry approved" },
  { id: "t2", ts: "2026-04-28T18:14:00Z", currency: "SC", direction: "debit", amount: 7500, reason: "bet_placed", note: "House Dems 2026 - NO" },
  { id: "t3", ts: "2026-04-28T15:30:00Z", currency: "GC", direction: "credit", amount: 5000, reason: "purchase", note: "GC starter pack" },
  { id: "t4", ts: "2026-04-28T15:30:00Z", currency: "SC", direction: "credit", amount: 500, reason: "purchase_promo_sc", note: "Bundled SC, GC starter pack" },
  { id: "t5", ts: "2026-04-25T16:08:00Z", currency: "SC", direction: "debit", amount: 3500, reason: "bet_placed", note: "Warriors Finals - YES" },
  { id: "t6", ts: "2026-04-22T20:11:00Z", currency: "SC", direction: "credit", amount: 4200, reason: "bet_settle_win", note: "Anthropic Series E (resolved)" },
  { id: "t7", ts: "2026-04-20T08:00:00Z", currency: "GC", direction: "credit", amount: 100, reason: "daily_bonus", note: "Daily login" },
  { id: "t8", ts: "2026-04-18T09:11:00Z", currency: "SC", direction: "debit", amount: 12000, reason: "bet_placed", note: "BTC 120k EOY - NO" },
  { id: "t9", ts: "2026-04-15T19:00:00Z", currency: "SC", direction: "credit", amount: 200, reason: "referral_bonus", note: "Friend signed up" },
  { id: "t10", ts: "2026-04-12T14:22:00Z", currency: "SC", direction: "debit", amount: 5000, reason: "bet_placed", note: "GPT-5 by 2026 - YES" },
  { id: "t11", ts: "2026-04-08T11:30:00Z", currency: "SC", direction: "debit", amount: 8000, reason: "bet_placed", note: "HF 5M models - YES" },
  { id: "t12", ts: "2026-04-01T10:00:00Z", currency: "SC", direction: "credit", amount: 5000, reason: "signup_bonus", note: "Welcome bonus" },
  { id: "t13", ts: "2026-04-01T10:00:00Z", currency: "GC", direction: "credit", amount: 10000, reason: "signup_bonus", note: "Welcome bonus" },
];
const GC_PACKAGES = [
  { id: "starter",  gcAmount: 5000,    scFreeCents: 500,    priceCents: 499,   label: "Starter" },
  { id: "popular",  gcAmount: 12500,   scFreeCents: 1500,   priceCents: 999,   label: "Popular", featured: true },
  { id: "pro",      gcAmount: 30000,   scFreeCents: 4000,   priceCents: 1999,  label: "Pro" },
  { id: "whale",    gcAmount: 75000,   scFreeCents: 12500,  priceCents: 4999,  label: "Whale" },
  { id: "tycoon",   gcAmount: 200000,  scFreeCents: 35000,  priceCents: 9999,  label: "Tycoon", gold: true },
];
const LEADERBOARD = [
  { rank: 1, user: "alpha_quant", pnlCents: 142800, winRate: 71.2, trades: 287, badge: "crown" },
  { rank: 2, user: "newsroom_oracle", pnlCents: 98400, winRate: 68.4, trades: 198, badge: "medal" },
  { rank: 3, user: "swing_trader_42", pnlCents: 76200, winRate: 64.1, trades: 412, badge: "medal" },
```

## Page 6

```text
  { rank: 4, user: "macro_misha", pnlCents: 64800, winRate: 62.8, trades: 156, badge: "star" },
  { rank: 5, user: "vol_surface", pnlCents: 58300, winRate: 59.4, trades: 224, badge: "star" },
  { rank: 6, user: "huggy_native", pnlCents: 47100, winRate: 57.9, trades: 134 },
  { rank: 7, user: "kelly_criterion", pnlCents: 41600, winRate: 56.3, trades: 387 },
  { rank: 8, user: "thinker_3000", pnlCents: 37200, winRate: 55.1, trades: 198 },
  { rank: 9, user: "weekly_wins", pnlCents: 34800, winRate: 53.7, trades: 244 },
  { rank: 10, user: "you", pnlCents: 28400, winRate: 51.2, trades: 47, isYou: true },
  { rank: 11, user: "hodl_hodler", pnlCents: 26100, winRate: 50.4, trades: 167 },
  { rank: 12, user: "bear_market_bo", pnlCents: 24700, winRate: 49.8, trades: 312 },
];
const ACTIVITY = [
  { id: "a1", user: "alpha_quant", action: "BUY", side: "YES", marketId: "m_gpt5_2026", amount: 5000, ts: "2026-04-29T10:48:00Z" },
  { id: "a2", user: "newsroom_oracle", action: "BUY", side: "NO", marketId: "m_btc_120k", amount: 12000, ts: "2026-04-29T10:46:00Z" },
  { id: "a3", user: "swing_trader_42", action: "EXIT", side: "YES", marketId: "m_election_dem", amount: 3200, ts: "2026-04-29T10:43:00Z" },
  { id: "a4", user: "macro_misha", action: "BUY", side: "YES", marketId: "m_huggy_5m", amount: 8000, ts: "2026-04-29T10:41:00Z" },
  { id: "a5", user: "vol_surface", action: "BUY", side: "NO", marketId: "m_anthropic_ipo", amount: 4500, ts: "2026-04-29T10:38:00Z" },
  { id: "a6", user: "huggy_native", action: "BUY", side: "YES", marketId: "m_warriors_2026", amount: 2800, ts: "2026-04-29T10:35:00Z" },
  { id: "a7", user: "kelly_criterion", action: "EXIT", side: "NO", marketId: "m_recession_2026", amount: 6700, ts: "2026-04-29T10:33:00Z" },
];
const NOTIFICATIONS = [
  { id: "n1", kind: "win", title: "Position resolved YES", body: "Anthropic Series E - you won 4,200 SC", ts: "2026-04-22T20:11:00Z", unread: true },
  { id: "n2", kind: "market", title: "BTC 120k market reached 50%", body: "Your NO position is at break-even", ts: "2026-04-29T08:30:00Z", unread: true },
  { id: "n3", kind: "promo", title: "Daily bonus available", body: "Claim 100 GC", ts: "2026-04-29T00:00:00Z", unread: false },
  { id: "n4", kind: "system", title: "KYC required for redemption", body: "Verify identity to redeem 1,000+ SC", ts: "2026-04-25T12:00:00Z", unread: false },
  { id: "n5", kind: "social", title: "alpha_quant followed you", body: "Your top 3 positions are now visible", ts: "2026-04-23T15:42:00Z", unread: false },
];
const COMMENTS = [
  { id: "c1", user: "alpha_quant", text: "OpenAI hasn't shipped a frontier-model jump in 8 months. Pricing this above 75% feels rich.", ts: "2026-04-29T08:14:00Z", up: 47, down: 3, pinned: true },
  { id: "c2", user: "newsroom_oracle", text: "Counter - they have to ship before Anthropic Opus 5 takes share. Q3-Q4 is structural.", ts: "2026-04-29T08:42:00Z", up: 38, down: 5 },
  { id: "c3", user: "swing_trader_42", text: "Sundar said 'we're not focused on naming' last earnings. Read between the lines.", ts: "2026-04-29T09:11:00Z", up: 22, down: 1 },
  { id: "c4", user: "huggy_native", text: "Reminder: 'GPT-5' is the marketed name. The model itself probably exists already.", ts: "2026-04-29T09:33:00Z", up: 18, down: 2 },
  { id: "c5", user: "macro_misha", text: "76% with 8 months left = expect drift up if no announcement, down if nothing by July. Mean reversion play.", ts: "2026-04-29T10:04:00Z", up: 14, down: 0 },
];
const NEWS = [
  { id: "nw1", source: "Bloomberg", headline: "Federal Reserve holds rates steady at 4.25% - markets price in two cuts before year-end", ts: "2026-04-29T09:30:00Z" },
  { id: "nw2", source: "The Verge", headline: "Anthropic announces Opus 4.7 with 1M token context, half the latency of prior generation", ts: "2026-04-29T08:14:00Z" },
  { id: "nw3", source: "ESPN", headline: "Warriors clinch playoff seed, Curry returns to form ahead of postseason", ts: "2026-04-29T07:02:00Z" },
  { id: "nw4", source: "Politico", headline: "Generic Congress polling tightens to within 2 points as filing deadlines approach", ts: "2026-04-28T22:45:00Z" },
  { id: "nw5", source: "CoinDesk", headline: "BTC reclaims $98k after correction, ETF inflows hit weekly record", ts: "2026-04-28T20:11:00Z" },
];
/* ---------- PRIMITIVES ---------- */
```

## Page 7

```text
function Caps({ children, className = "", style }) { return <span className={"ha-caps " + className} style={style}>{children}</span>; }
function Mono({ children, className = "" }) { return <span className={"ha-mono ha-tnum " + className}>{children}</span>; }
function Smcp({ children, className = "" }) { return <span className={"ha-smcp " + className}>{children}</span>; }
function Display({ children, className = "", italic = false, weight = 600, size = 144 }) {
  const klass = italic ? "ha-display-italic " : "ha-display ";
  return <span className={klass + className} style={{ fontVariationSettings: `"opsz" ${size}, "SOFT" 30`, fontWeight: weight }}>{children}</span>;
}
function Rule({ className = "", thick = false, double = false }) {
  return <hr className={`border-0 ${double ? "ha-rule-double" : thick ? "ha-rule-thick" : "ha-rule"} ${className}`} />;
}
function Pill({ children, tone = "soft" }) {
  const map = { soft: "ha-bdg ha-bdg-soft", yes: "ha-bdg ha-bdg-yes", no: "ha-bdg ha-bdg-no", amber: "ha-bdg ha-bdg-amber", ink: "ha-bdg ha-bdg-ink" };
  return <span className={map[tone]}>{children}</span>;
}
function marketProb(market) {
  const total = market.yesPool + market.noPool;
  if (total === 0) return 50;
  return Math.round((market.yesPool / total) * 100);
}
function categoryById(id) { return CATEGORIES.find((c) => c.id === id); }
function marketById(id) { return MARKETS.find((m) => m.id === id); }
const ART_VARIANTS = {
  "ai-grad":   { bg: "linear-gradient(135deg, #fbbf24 0%, #c2410c 100%)", glyph: "▲" },
  "llama":     { bg: "linear-gradient(135deg, #84cc16 0%, #15803d 100%)", glyph: "◆" },
  "ipo":       { bg: "linear-gradient(135deg, #ddd6fe 0%, #5b21b6 100%)", glyph: "$" },
  "btc":       { bg: "linear-gradient(135deg, #fed7aa 0%, #ea580c 100%)", glyph: "₿" },
  "eth":       { bg: "linear-gradient(135deg, #cbd5e1 0%, #475569 100%)", glyph: "Ξ" },
  "warriors":  { bg: "linear-gradient(135deg, #fde68a 0%, #1e40af 100%)", glyph: "◐" },
  "election":  { bg: "linear-gradient(135deg, #bfdbfe 0%, #b91c1c 100%)", glyph: "★" },
  "apple":     { bg: "linear-gradient(135deg, #f1f5f9 0%, #1e293b 100%)", glyph: "◯" },
  "tswift":    { bg: "linear-gradient(135deg, #fbcfe8 0%, #831843 100%)", glyph: "♪" },
  "recession": { bg: "linear-gradient(135deg, #fecaca 0%, #7f1d1d 100%)", glyph: "↓" },
  "climate":   { bg: "linear-gradient(135deg, #fef3c7 0%, #b45309 100%)", glyph: "☀" },
  "hf":        { bg: "linear-gradient(135deg, #fde68a 0%, #c2410c 100%)", glyph: "H" },
};
function MarketArt({ name, size = 56, className = "" }) {
  const art = ART_VARIANTS[name] || ART_VARIANTS["hf"];
  return (
    <div className={"flex items-center justify-center text-white font-bold rounded " + className}
      style={{ width: size, height: size, background: art.bg, fontSize: size * 0.45, boxShadow: "inset 0 0 0 1px rgba(0,0,0,.15)", flexShrink: 0 }}>
      {art.glyph}
    </div>
  );
}
```

## Page 8

```text
function Ticker() {
  return (
    <div style={{ borderTop: "1px solid var(--ink)", borderBottom: "1px solid var(--ink)", background: "var(--ink)", color: "var(--paper)", height: 26, overflow: "hidden", position: "relative" }}>
      <div className="ha-marquee items-center gap-8 ha-mono ha-tnum" style={{ height: "100%", fontSize: 11 }}>
        {[...MARKETS, ...MARKETS].map((m, i) => {
          const prob = marketProb(m); const dir = i % 2 === 0 ? "▲" : "▼";
          return (
            <div key={i} className="flex items-center gap-2 px-2">
              <span style={{ opacity: 0.5 }}>{m.id.replace("m_", "").slice(0, 8).toUpperCase()}</span>
              <span style={{ color: dir === "▲" ? "#86efac" : "#fda4af" }}>{dir}</span>
              <span>{prob}%</span>
              <span style={{ opacity: 0.6 }}>·</span>
            </div>
          );
        })}
      </div>
    </div>
  );
}
const VIEWS = [
  { id: "discover", label: "Discover", icon: Compass },
  { id: "markets", label: "Markets", icon: BarChart3 },
  { id: "portfolio", label: "Portfolio", icon: Briefcase },
  { id: "wallet", label: "Wallet", icon: Wallet },
  { id: "agent", label: "Agent", icon: Bot },
];
const SECONDARY_VIEWS = [
  { id: "shop", label: "Shop GC", icon: Coins },
  { id: "free-sc", label: "Free SC (AMOE)", icon: Gift },
  { id: "redeem", label: "Redeem SC", icon: ArrowDownUp },
  { id: "leaderboard", label: "Leaderboard", icon: Trophy },
  { id: "profile", label: "Profile", icon: User },
  { id: "settings", label: "Settings", icon: Settings },
  { id: "help", label: "Responsible Play", icon: Shield },
];
export default function HuggyArenaApp() {
  const [view, setView] = useState("discover");
  const [selectedMarketId, setSelectedMarketId] = useState(null);
  const [scBalance, setScBalance] = useState(420075);
  const [gcBalance, setGcBalance] = useState(15000);
  const [searchOpen, setSearchOpen] = useState(false);
  const [search, setSearch] = useState("");
  const [moreOpen, setMoreOpen] = useState(false);
```

## Page 9

```text
  const [notifOpen, setNotifOpen] = useState(false);
  const [unreadCount, setUnreadCount] = useState(NOTIFICATIONS.filter(n => n.unread).length);
  const [toasts, setToasts] = useState([]);
  const [showCompliance, setShowCompliance] = useState(false);
  const [walletDrawerOpen, setWalletDrawerOpen] = useState(false);
  const openMarket = useCallback((id) => { setSelectedMarketId(id); setView("market"); setMoreOpen(false); }, []);
  const closeMarket = useCallback(() => { setSelectedMarketId(null); setView("markets"); }, []);
  const navigate = useCallback((id) => { setSelectedMarketId(null); setView(id); setMoreOpen(false); }, []);
  const pushToast = useCallback((message, tone = "info") => {
    const id = Math.random().toString(36).slice(2);
    setToasts((t) => [...t, { id, message, tone }]);
    setTimeout(() => setToasts((t) => t.filter((x) => x.id !== id)), 3500);
  }, []);
  const placeBet = useCallback((marketId, side, amountCents) => {
    setScBalance((b) => b - amountCents);
    pushToast(`Position opened — ${side} on ${marketById(marketId)?.id.slice(0, 16)}`, "success");
  }, [pushToast]);
  const market = selectedMarketId ? marketById(selectedMarketId) : null;
  return (
    <div className="ha-root ha-paper min-h-screen">
      <style>{THEME_STYLES}</style>
      <Ticker />
      <AppHeader view={view} onNavigate={navigate} onSearchOpen={() => setSearchOpen(true)} onMoreOpen={() => setMoreOpen(true)} onNotifOpen={() => setNotifOpen(true)} onWalletOpen={() => setWalletDrawerOpen(true)} scBalance={scBalance} gcBalance={gcBalance} unreadCount={unreadCount} />
      <main className="max-w-[1280px] mx-auto px-4 sm:px-6 pb-32 md:pb-12">
        {view === "discover" && <DiscoverView onOpenMarket={openMarket} onNavigate={navigate} scBalance={scBalance} gcBalance={gcBalance} />}
        {view === "markets" && <MarketsView onOpenMarket={openMarket} />}
        {view === "market" && market && <MarketDetailView market={market} onBack={closeMarket} onPlaceBet={placeBet} scBalance={scBalance} />}
        {view === "portfolio" && <PortfolioView onOpenMarket={openMarket} />}
        {view === "wallet" && <WalletView scBalance={scBalance} gcBalance={gcBalance} onNavigate={navigate} />}
        {view === "shop" && <ShopView onNavigate={navigate} pushToast={pushToast} />}
        {view === "free-sc" && <FreeScView pushToast={pushToast} />}
        {view === "redeem" && <RedeemView scBalance={scBalance} pushToast={pushToast} />}
        {view === "leaderboard" && <LeaderboardView />}
        {view === "profile" && <ProfileView onNavigate={navigate} />}
        {view === "agent" && <AgentView onOpenMarket={openMarket} />}
        {view === "settings" && <SettingsView onNavigate={navigate} pushToast={pushToast} />}
        {view === "help" && <HelpView />}
        {view === "onboarding" && <OnboardingView onComplete={() => navigate("discover")} pushToast={pushToast} />}
      </main>
      <MobileTabBar view={view} onNavigate={navigate} onMoreOpen={() => setMoreOpen(true)} />
      {searchOpen && <SearchOverlay search={search} setSearch={setSearch} onClose={() => setSearchOpen(false)} onOpenMarket={(id) => { openMarket(id); setSearchOpen(false); setSearch(""); }} />}
      {moreOpen && <MoreDrawer onClose={() => setMoreOpen(false)} onNavigate={navigate} />}
      {notifOpen && <NotifDrawer onClose={() => setNotifOpen(false)} onMarkAllRead={() => setUnreadCount(0)} />}
      {walletDrawerOpen && <WalletDrawer scBalance={scBalance} gcBalance={gcBalance} onClose={() => setWalletDrawerOpen(false)} onNavigate={(id) => { navigate(id); setWalletDrawerOpen(false); }} />}
```

## Page 10

```text
      <ComplianceFooter onOpenLegal={() => setShowCompliance(true)} />
      <ToastStack toasts={toasts} />
      {showCompliance && <ComplianceModal onClose={() => setShowCompliance(false)} />}
    </div>
  );
}
/* ---------- HEADER ---------- */
function AppHeader({ view, onNavigate, onSearchOpen, onMoreOpen, onNotifOpen, onWalletOpen, scBalance, gcBalance, unreadCount }) {
  return (
    <header className="border-b border-[var(--ink)] bg-[var(--paper)] sticky top-0 z-30">
      <div className="max-w-[1280px] mx-auto px-4 sm:px-6">
        <div className="h-16 flex items-center justify-between">
          <button onClick={() => onNavigate("discover")} className="flex items-baseline gap-2 group">
            <Display weight={700} size={144} className="text-[24px] sm:text-[28px] leading-none">
              Huggy<span style={{ color: "var(--amber)" }}>·</span>Arena
            </Display>
            <span className="ha-caps text-[var(--ink-3)] hidden sm:inline">Vol. III</span>
          </button>
          <nav className="hidden md:flex items-center gap-1">
            {VIEWS.map((v) => {
              const active = view === v.id || (view === "market" && v.id === "markets");
              return (
                <button key={v.id} onClick={() => onNavigate(v.id)}
                  className={"px-3 py-2 text-sm font-medium rounded transition-colors " + (active ? "bg-[var(--ink)] text-[var(--paper)]" : "text-[var(--ink-2)] hover:bg-[var(--paper-2)]")}>
                  {v.label}
                </button>
              );
            })}
          </nav>
          <div className="flex items-center gap-1 sm:gap-2">
            <button onClick={onSearchOpen} className="h-10 w-10 flex items-center justify-center rounded hover:bg-[var(--paper-2)]" aria-label="Search"><Search size={18} /></button>
            <button onClick={onNotifOpen} className="h-10 w-10 flex items-center justify-center rounded hover:bg-[var(--paper-2)] relative" aria-label="Notifications">
              <Bell size={18} />
              {unreadCount > 0 && <span className="absolute top-1.5 right-1.5 w-2 h-2 rounded-full bg-[var(--amber)]" />}
            </button>
            <button onClick={onWalletOpen} className="hidden sm:flex h-10 px-3 items-center gap-3 border border-[var(--rule)] rounded hover:bg-[var(--paper-2)]">
              <span className="flex items-center gap-1"><Coins size={14} className="text-[var(--gold)]" /><Mono className="text-[13px]">{fmt.gc(gcBalance)}</Mono></span>
              <span className="w-px h-4 bg-[var(--rule)]" />
              <span className="flex items-center gap-1"><Sparkles size={14} className="text-[var(--amber)]" /><Mono className="text-[13px]">{fmt.sc(scBalance)}</Mono></span>
            </button>
            <button onClick={onWalletOpen} className="sm:hidden h-10 px-2 flex items-center gap-1 border border-[var(--rule)] rounded" aria-label="Wallet">
              <Sparkles size={14} className="text-[var(--amber)]" />
              <Mono className="text-[12px]">{fmt.sc(scBalance)}</Mono>
            </button>
            <button onClick={onMoreOpen} className="h-10 w-10 hidden sm:flex items-center justify-center rounded hover:bg-[var(--paper-2)]" aria-label="More"><Menu size={18} /></button>
          </div>
```

## Page 11

```text
        </div>
      </div>
    </header>
  );
}
/* ---------- MOBILE TAB BAR ---------- */
function MobileTabBar({ view, onNavigate, onMoreOpen }) {
  const tabs = [
    { id: "discover", label: "Discover", icon: Compass },
    { id: "markets", label: "Markets", icon: BarChart3 },
    { id: "portfolio", label: "Portfolio", icon: Briefcase },
    { id: "agent", label: "Agent", icon: Bot },
    { id: "more", label: "More", icon: Menu, action: onMoreOpen },
  ];
  return (
    <div className="md:hidden fixed bottom-0 left-0 right-0 bg-[var(--paper)] border-t border-[var(--ink)] z-30 ha-safe-bottom">
      <div className="grid grid-cols-5">
        {tabs.map((t) => {
          const Icon = t.icon;
          const active = view === t.id || (view === "market" && t.id === "markets");
          return (
            <button key={t.id} onClick={() => t.action ? t.action() : onNavigate(t.id)}
              className={"h-14 flex flex-col items-center justify-center gap-0.5 transition-colors " + (active ? "text-[var(--ink)]" : "text-[var(--ink-3)]")}>
              <Icon size={20} strokeWidth={active ? 2.2 : 1.6} />
              <span className="text-[10px] font-medium">{t.label}</span>
            </button>
          );
        })}
      </div>
    </div>
  );
}
/* ---------- COMPLIANCE FOOTER ---------- */
function ComplianceFooter({ onOpenLegal }) {
  return (
    <footer className="hidden md:block max-w-[1280px] mx-auto px-6 py-8 border-t border-[var(--rule)] mt-12">
      <div className="grid grid-cols-1 md:grid-cols-4 gap-8">
        <div>
          <Display weight={600} className="text-[20px] leading-none">Huggy<span style={{ color: "var(--amber)" }}>·</span>Arena</Display>
          <p className="ha-mono text-[11px] text-[var(--ink-3)] mt-3 leading-relaxed">Sweepstakes-eligible prediction markets.<br/>45 states, 21+, no purchase necessary.</p>
        </div>
        <div>
          <Caps className="text-[var(--ink-3)] block mb-3">Compliance</Caps>
          <ul className="space-y-1.5 text-[13px] text-[var(--ink-2)]">
            <li><button onClick={onOpenLegal} className="hover:underline">Sweepstakes Rules</button></li>
```

## Page 12

```text
            <li><button onClick={onOpenLegal} className="hover:underline">Responsible Play</button></li>
            <li><button onClick={onOpenLegal} className="hover:underline">AMOE (Free Entry)</button></li>
            <li><button onClick={onOpenLegal} className="hover:underline">State Eligibility</button></li>
          </ul>
        </div>
        <div>
          <Caps className="text-[var(--ink-3)] block mb-3">Legal</Caps>
          <ul className="space-y-1.5 text-[13px] text-[var(--ink-2)]">
            <li><button onClick={onOpenLegal} className="hover:underline">Terms of Service</button></li>
            <li><button onClick={onOpenLegal} className="hover:underline">Privacy Policy</button></li>
            <li><button onClick={onOpenLegal} className="hover:underline">Risk Disclosure</button></li>
            <li><button onClick={onOpenLegal} className="hover:underline">Cookie Settings</button></li>
          </ul>
        </div>
        <div>
          <Caps className="text-[var(--ink-3)] block mb-3">Help</Caps>
          <ul className="space-y-1.5 text-[13px] text-[var(--ink-2)]">
            <li><span>Support · 24h response</span></li>
            <li><span>1-800-GAMBLER</span></li>
            <li><span>NCPG Helpline</span></li>
            <li><span>Version 3.0.0</span></li>
          </ul>
        </div>
      </div>
      <Rule className="my-6" />
      <div className="flex items-center justify-between text-[11px] ha-mono text-[var(--ink-3)]">
        <span>© 2026 Huggy Arena Labs, Inc. All rights reserved.</span>
        <span>Last audit: Apr 26, 2026 · Build 4f8a2c</span>
      </div>
    </footer>
  );
}
/* ============================================================================
   DISCOVER
   ============================================================================ */
function DiscoverView({ onOpenMarket, onNavigate, scBalance, gcBalance }) {
  const featured = MARKETS.find((m) => m.pinned) || MARKETS[0];
  const trending = MARKETS.filter((m) => m.id !== featured.id).slice(0, 6);
  const editorsPicks = MARKETS.filter((m) => m.id !== featured.id && m.creatorVerified).slice(0, 4);
  return (
    <div className="pt-6 pb-8">
      <div className="ha-fade ha-d-1">
        <div className="flex items-baseline justify-between flex-wrap gap-2 pb-3">
          <div className="flex items-baseline gap-3 ha-mono text-[11px] text-[var(--ink-3)]">
            <span>{new Date().toLocaleDateString("en-US", { weekday: "long", month: "long", day: "numeric", year: "numeric" })}</span>
```

## Page 13

```text
            <span>·</span><span>VOL. III · NO. 117</span><span>·</span>
            <span className="hidden sm:inline">"Markets are public arguments rendered as numbers"</span>
          </div>
          <div className="ha-mono text-[11px] text-[var(--ink-3)]">
            <span className="ha-pulse" style={{ color: "var(--yes)" }}>●</span> Live · {MARKETS.reduce((s, m) => s + m.traders, 0).toLocaleString()} active traders
          </div>
        </div>
        <Rule double />
      </div>
      <FeaturedHero market={featured} onOpenMarket={onOpenMarket} />
      <Rule className="my-8" />
      <SectionHeader kicker="Curated" title="Editor's Picks" right={<button onClick={() => onNavigate("markets")} className="ha-mono text-[12px] underline hover:text-[var(--amber)]">browse all 329 markets →</button>} />
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-3 mt-4 ha-fade ha-d-3">
        {editorsPicks.map((m, i) => <EditorialMarketCard key={m.id} market={m} onOpen={onOpenMarket} delay={i} />)}
      </div>
      <Rule className="my-8" />
      <SectionHeader kicker="Live" title="Most Traded · 24h" right={<Caps className="text-[var(--ink-3)]">Sorted by volume</Caps>} />
      <TrendingTable markets={trending} onOpen={onOpenMarket} />
      <Rule className="my-8" />
      <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <div className="lg:col-span-2">
          <SectionHeader kicker="From the Wire" title="Headlines" />
          <NewsTicker />
        </div>
        <div>
          <SectionHeader kicker="The Floor" title="Live Activity" />
          <ActivityFeed onOpenMarket={onOpenMarket} />
        </div>
      </div>
      <Rule className="my-8" />
      <SectionHeader kicker="Browse" title="By Category" />
      <CategoryGrid onNavigate={onNavigate} />
      <Rule className="my-8" />
      <StatsBanner gcBalance={gcBalance} scBalance={scBalance} />
      <Rule className="my-8" />
```

## Page 14

```text
      <GetStartedRow onNavigate={onNavigate} />
    </div>
  );
}
function SectionHeader({ kicker, title, right }) {
  return (
    <div className="flex items-baseline justify-between flex-wrap gap-2 mt-2 mb-1">
      <div>
        <Caps className="text-[var(--amber)] block mb-1">{kicker}</Caps>
        <Display weight={600} className="text-[26px] sm:text-[32px] leading-none">{title}</Display>
      </div>
      {right && <div>{right}</div>}
    </div>
  );
}
function FeaturedHero({ market, onOpenMarket }) {
  const prob = marketProb(market);
  return (
    <article className="ha-fade ha-d-2 grid grid-cols-1 lg:grid-cols-12 gap-6 mt-6">
      <div className="lg:col-span-5">
        <button onClick={() => onOpenMarket(market.id)} className="block w-full aspect-[4/5] rounded ha-hov relative overflow-hidden" style={{ background: ART_VARIANTS[market.image]?.bg || "var(--ink)" }}>
          <div className="absolute inset-0 flex items-center justify-center text-white opacity-40" style={{ fontSize: 280, fontWeight: 700 }}>{ART_VARIANTS[market.image]?.glyph}</div>
          <div className="absolute bottom-4 left-4 right-4 flex items-end justify-between">
            <div className="bg-[var(--paper)] px-3 py-2 rounded">
              <Caps className="text-[var(--ink-3)] block">YES</Caps>
              <Mono className="text-[28px] leading-none"><Display weight={600}>{prob}<span style={{ fontSize: 18 }}>%</span></Display></Mono>
            </div>
            <Pill tone="ink">FEATURED</Pill>
          </div>
        </button>
        <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-2 text-right">Vol III · Cover · {fmt.dateLong(new Date().toISOString())}</div>
      </div>
      <div className="lg:col-span-7 flex flex-col">
        <div className="flex items-center gap-2 mb-3">
          <Pill tone="amber">{categoryById(market.category)?.label}</Pill>
          <Pill tone="soft">{market.creator}</Pill>
          <span className="ha-mono text-[10px] text-[var(--ink-3)]">resolves {fmt.rel(market.closeAt)}</span>
        </div>
        <h1 className="ha-display text-[36px] sm:text-[48px] lg:text-[56px] leading-[1.05] tracking-tight font-semibold mb-4" style={{ fontVariationSettings: '"opsz" 144, "SOFT" 30' }}>{market.question}</h1>
        <p className="ha-display-italic text-[16px] sm:text-[18px] leading-relaxed text-[var(--ink-2)] mb-5 max-w-prose">{market.description}</p>
        <div className="ha-card p-5 mb-4">
          <div className="flex items-baseline justify-between mb-3">
            <Caps className="text-[var(--ink-3)]">Implied probability</Caps>
            <Mono className="text-[11px] text-[var(--ink-3)]">${(market.yesPool + market.noPool) / 100} pool · {market.traders.toLocaleString()} traders</Mono>
```

## Page 15

```text
          </div>
          <div className="flex items-baseline gap-4 mb-2">
            <div className="flex-1">
              <div className="ha-split"><div className="ha-split-y" style={{ width: prob + "%" }} /><div className="ha-split-n" style={{ width: 100 - prob + "%" }} /></div>
            </div>
            <div className="ha-mono ha-tnum text-[13px]">
              <span className="text-[var(--yes-deep)]">YES {prob}%</span>
              <span className="text-[var(--ink-3)] mx-2">·</span>
              <span className="text-[var(--no-deep)]">NO {100 - prob}%</span>
            </div>
          </div>
          <MiniSparkline data={market.series} prob={prob} height={64} />
        </div>
        <div className="flex flex-wrap gap-2 mt-auto">
          <button onClick={() => onOpenMarket(market.id)} className="ha-btn ha-btn-yes ha-btn-lg">Trade YES → {prob}¢</button>
          <button onClick={() => onOpenMarket(market.id)} className="ha-btn ha-btn-no ha-btn-lg">Trade NO → {100 - prob}¢</button>
          <button onClick={() => onOpenMarket(market.id)} className="ha-btn ha-btn-ghost ha-btn-lg border border-[var(--ink)]">Read criteria</button>
        </div>
      </div>
    </article>
  );
}
function MiniSparkline({ data, prob, height = 32, color }) {
  const c = color || "var(--ink)";
  return (
    <div style={{ height, width: "100%" }}>
      <ResponsiveContainer width="100%" height="100%">
        <AreaChart data={data} margin={{ top: 4, right: 0, bottom: 0, left: 0 }}>
          <defs>
            <linearGradient id={`grad-${prob}-${Math.random().toString(36).slice(2,6)}`} x1="0" y1="0" x2="0" y2="1">
              <stop offset="0%" stopColor={c} stopOpacity={0.18} />
              <stop offset="100%" stopColor={c} stopOpacity={0} />
            </linearGradient>
          </defs>
          <YAxis hide domain={[0, 100]} />
          <Area type="monotone" dataKey="pct" stroke={c} strokeWidth={1.5} fill={c} fillOpacity={0.1} dot={false} />
          <ReferenceLine y={50} stroke="var(--rule)" strokeDasharray="2 3" />
        </AreaChart>
      </ResponsiveContainer>
    </div>
  );
}
function EditorialMarketCard({ market, onOpen, delay = 0 }) {
  const prob = marketProb(market);
  const cat = categoryById(market.category);
```

## Page 16

```text
  return (
    <button onClick={() => onOpen(market.id)} className="ha-card ha-hov text-left p-4 flex flex-col gap-3 ha-fade" style={{ animationDelay: 0.04 * delay + "s" }}>
      <div className="flex items-start justify-between gap-2">
        <Caps style={{ color: cat?.color }}>{cat?.label}</Caps>
        {market.pinned && <Pin size={12} className="text-[var(--amber)]" />}
      </div>
      <div className="ha-display text-[16px] leading-snug font-semibold ha-line-clamp-3 min-h-[3.6em]">{market.question}</div>
      <div className="mt-auto pt-2">
        <div className="flex items-baseline justify-between mb-1.5">
          <Mono className="text-[20px]">{prob}<span className="text-[12px] text-[var(--ink-3)]">%</span></Mono>
          <Mono className="text-[10px] text-[var(--ink-3)]">{market.traders.toLocaleString()} trd</Mono>
        </div>
        <div className="ha-split"><div className="ha-split-y" style={{ width: prob + "%" }} /><div className="ha-split-n" style={{ width: 100 - prob + "%" }} /></div>
      </div>
    </button>
  );
}
function TrendingTable({ markets, onOpen }) {
  const sorted = [...markets].sort((a, b) => b.volume24h - a.volume24h);
  return (
    <div className="ha-fade ha-d-4 mt-4">
      <div className="md:hidden space-y-2">
        {sorted.map((m, i) => (
          <button key={m.id} onClick={() => onOpen(m.id)} className="w-full ha-card p-3 flex items-center gap-3 text-left">
            <Mono className="text-[16px] text-[var(--ink-3)] w-5">{i + 1}</Mono>
            <MarketArt name={m.image} size={36} />
            <div className="flex-1 min-w-0">
              <div className="text-[13px] font-medium ha-line-clamp-2">{m.question}</div>
              <div className="ha-mono text-[10px] text-[var(--ink-3)]">{categoryById(m.category)?.label} · ${m.volume24h.toLocaleString()} 24h</div>
            </div>
            <Mono className="text-[18px]"><Display weight={600}>{marketProb(m)}<span className="text-[10px]">%</span></Display></Mono>
          </button>
        ))}
      </div>
      <div className="hidden md:block ha-card overflow-hidden">
        <table className="w-full">
          <thead>
            <tr className="text-left ha-mono text-[10px] text-[var(--ink-3)] border-b border-[var(--rule)]">
              <th className="py-3 px-4 font-medium w-10">#</th>
              <th className="py-3 px-4 font-medium">Market</th>
              <th className="py-3 px-4 font-medium">Category</th>
              <th className="py-3 px-4 font-medium text-right">YES %</th>
              <th className="py-3 px-4 font-medium text-right">24h Vol</th>
              <th className="py-3 px-4 font-medium text-right">Traders</th>
              <th className="py-3 px-4 font-medium text-right">Closes</th>
            </tr>
```

## Page 17

```text
          </thead>
          <tbody>
            {sorted.map((m, i) => {
              const prob = marketProb(m);
              return (
                <tr key={m.id} onClick={() => onOpen(m.id)} className="border-b border-[var(--rule-soft)] last:border-b-0 hover:bg-[var(--paper-2)] cursor-pointer">
                  <td className="py-3 px-4 ha-mono text-[12px] text-[var(--ink-3)]">{i + 1}</td>
                  <td className="py-3 px-4">
                    <div className="flex items-center gap-3">
                      <MarketArt name={m.image} size={32} />
                      <div className="text-[13px] font-medium ha-line-clamp-2 max-w-[480px]">{m.question}</div>
                    </div>
                  </td>
                  <td className="py-3 px-4"><Caps style={{ color: categoryById(m.category)?.color }}>{categoryById(m.category)?.label}</Caps></td>
                  <td className="py-3 px-4 text-right">
                    <div className="inline-flex items-center gap-2">
                      <div className="w-12 h-1.5 bg-[var(--paper-2)] rounded-full overflow-hidden"><div className="h-full bg-[var(--yes)]" style={{ width: prob + "%" }} /></div>
                      <Mono className="text-[13px] w-9 text-right">{prob}%</Mono>
                    </div>
                  </td>
                  <td className="py-3 px-4 text-right ha-mono text-[12px]">${m.volume24h.toLocaleString()}</td>
                  <td className="py-3 px-4 text-right ha-mono text-[12px] text-[var(--ink-3)]">{m.traders.toLocaleString()}</td>
                  <td className="py-3 px-4 text-right ha-mono text-[12px] text-[var(--ink-3)]">{fmt.rel(m.closeAt)}</td>
                </tr>
              );
            })}
          </tbody>
        </table>
      </div>
    </div>
  );
}
function NewsTicker() {
  return (
    <div className="ha-card ha-fade mt-4 divide-y divide-[var(--rule-soft)]">
      {NEWS.map((n) => (
        <article key={n.id} className="p-4 flex items-start gap-3 hover:bg-[var(--paper-2)] cursor-pointer">
          <div className="ha-mono text-[10px] text-[var(--ink-3)] w-12 shrink-0 pt-1">{fmt.time(n.ts).replace(":00", "")}</div>
          <div className="flex-1">
            <div className="flex items-center gap-2 mb-1">
              <Caps style={{ color: "var(--ink-2)" }}>{n.source}</Caps>
              <span className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.rel(n.ts)}</span>
            </div>
            <p className="ha-display text-[15px] leading-snug text-[var(--ink)]">{n.headline}</p>
          </div>
          <ExternalLink size={14} className="text-[var(--ink-3)] shrink-0 mt-1.5" />
```

## Page 18

```text
        </article>
      ))}
    </div>
  );
}
function ActivityFeed({ onOpenMarket }) {
  return (
    <div className="ha-card ha-fade mt-4 divide-y divide-[var(--rule-soft)]">
      {ACTIVITY.map((a) => {
        const m = marketById(a.marketId);
        if (!m) return null;
        return (
          <button key={a.id} onClick={() => onOpenMarket(a.marketId)} className="w-full text-left p-3 flex items-center gap-3 hover:bg-[var(--paper-2)]">
            <div className="w-7 h-7 rounded flex items-center justify-center shrink-0" style={{ background: a.side === "YES" ? "var(--yes-soft)" : "var(--no-soft)" }}>
              {a.action === "BUY" ? <ArrowUpRight size={13} className={a.side === "YES" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]"} /> : <ArrowDownRight size={13} className="text-[var(--ink-2)]" />}
            </div>
            <div className="flex-1 min-w-0">
              <div className="text-[12px]">
                <span className="font-medium">@{a.user}</span>
                <span className="text-[var(--ink-3)]"> {a.action.toLowerCase()}ed </span>
                <span className={"ha-mono " + (a.side === "YES" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>{a.side}</span>
              </div>
              <div className="text-[11px] text-[var(--ink-3)] ha-line-clamp-2">{m.question}</div>
            </div>
            <div className="text-right shrink-0">
              <Mono className="text-[12px]">{fmt.sc(a.amount)}</Mono>
              <div className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.rel(a.ts)}</div>
            </div>
          </button>
        );
      })}
      <div className="p-3 ha-mono text-[10px] text-[var(--ink-3)] flex items-center gap-2">
        <span className="ha-pulse" style={{ color: "var(--yes)" }}>●</span>
        <span>Streaming · updates every 4s</span>
      </div>
    </div>
  );
}
function CategoryGrid({ onNavigate }) {
  return (
    <div className="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-7 gap-2 mt-4 ha-fade ha-d-5">
      {CATEGORIES.map((c) => (
        <button key={c.id} onClick={() => onNavigate("markets")} className="ha-card ha-hov p-4 flex flex-col items-start gap-1 text-left">
          <div className="w-2 h-2 rounded-full" style={{ background: c.color }} />
          <div className="ha-display text-[16px] font-semibold mt-2">{c.label}</div>
```

## Page 19

```text
          <Mono className="text-[11px] text-[var(--ink-3)]">{c.count} markets</Mono>
        </button>
      ))}
    </div>
  );
}
function StatsBanner({ gcBalance, scBalance }) {
  return (
    <div className="ha-card ha-fade ha-d-6 p-6 sm:p-8 flex flex-wrap items-center justify-around gap-6 ha-paper-card">
      <Stat label="Total markets" value="329" sub="+12 this week" />
      <Stat label="Active traders" value="14,217" sub="rolling 24h" />
      <Stat label="Volume traded" value="$1.4M" sub="all-time" />
      <Stat label="Avg. resolution" value="98.4%" sub="oracle accuracy" />
      <Stat label="Your SC" value={fmt.sc(scBalance)} sub={"≈ " + fmt.usd(scBalance)} accent />
    </div>
  );
}
function Stat({ label, value, sub, accent }) {
  return (
    <div className="flex flex-col items-start min-w-[120px]">
      <Caps className="text-[var(--ink-3)] mb-1">{label}</Caps>
      <Mono className={"text-[28px] sm:text-[32px] leading-none " + (accent ? "text-[var(--amber)]" : "")}>
        <Display weight={600}>{value}</Display>
      </Mono>
      <span className="ha-mono text-[10px] text-[var(--ink-3)] mt-1">{sub}</span>
    </div>
  );
}
function GetStartedRow({ onNavigate }) {
  const cards = [
    { id: "shop", title: "Buy Gold Coins", body: "GC packages from $4.99. Bundled SC included with every purchase.", cta: "Shop GC", icon: Coins, accent: "gold" },
    { id: "free-sc", title: "Free Sweeps Coins", body: "No purchase necessary. Daily login bonus, AMOE postcard, referrals.", cta: "Earn SC", icon: Gift, accent: "amber" },
    { id: "agent", title: "Ask the Agent", body: "AI agent helps you find markets aligned with your view. Powered by Claude.", cta: "Talk to Agent", icon: Bot, accent: "ink" },
  ];
  return (
    <div className="grid grid-cols-1 md:grid-cols-3 gap-3 ha-fade ha-d-7">
      {cards.map((c) => {
        const Icon = c.icon;
        return (
          <button key={c.id} onClick={() => onNavigate(c.id)} className="ha-card ha-hov p-5 text-left flex flex-col gap-2">
            <div className="w-10 h-10 rounded flex items-center justify-center mb-2"
              style={{ background: c.accent === "gold" ? "var(--gold-soft)" : c.accent === "amber" ? "var(--amber-soft)" : "var(--ink)", color: c.accent === "ink" ? "var(--paper)" : "var(--ink)" }}>
              <Icon size={18} />
            </div>
            <Display weight={600} className="text-[18px]">{c.title}</Display>
```

## Page 20

```text
            <p className="text-[13px] text-[var(--ink-2)]">{c.body}</p>
            <span className="ha-mono text-[12px] text-[var(--amber)] mt-2 underline">{c.cta} →</span>
          </button>
        );
      })}
    </div>
  );
}
/* ============================================================================
   STUBS - replaced by str_replace operations
   ============================================================================ */
/* ============================================================================
   MARKETS — full browse with filters and category rails
   ============================================================================ */
function MarketsView({ onOpenMarket }) {
  const [activeCategory, setActiveCategory] = useState("all");
  const [activeStatus, setActiveStatus] = useState("open");
  const [sort, setSort] = useState("volume");
  const [layout, setLayout] = useState("grid");
  const [search, setSearch] = useState("");
  const filtered = useMemo(() => {
    let list = MARKETS;
    if (activeCategory !== "all") list = list.filter((m) => m.category === activeCategory);
    if (activeStatus !== "all") list = list.filter((m) => m.status === activeStatus);
    if (search.trim()) list = list.filter((m) => m.question.toLowerCase().includes(search.toLowerCase()));
    if (sort === "volume") list = [...list].sort((a, b) => b.volume24h - a.volume24h);
    if (sort === "traders") list = [...list].sort((a, b) => b.traders - a.traders);
    if (sort === "ending") list = [...list].sort((a, b) => new Date(a.closeAt) - new Date(b.closeAt));
    if (sort === "new") list = [...list].sort((a, b) => b.id.localeCompare(a.id));
    return list;
  }, [activeCategory, activeStatus, sort, search]);
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-2">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)]"><span>section II</span><span>·</span><span>{filtered.length} markets</span></div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1] mt-1">All Markets</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">Every market currently listed on Huggy Arena. Fail-closed jurisdictionally; trade only where you are eligible.</p>
      </div>
      <Rule className="my-6" double />
      <div className="flex flex-wrap items-center gap-2 mb-4 ha-fade ha-d-2">
        <div className="relative flex-1 min-w-[240px]">
          <Search size={16} className="absolute left-3 top-1/2 -translate-y-1/2 text-[var(--ink-3)]" />
          <input value={search} onChange={(e) => setSearch(e.target.value)} placeholder="Search 329 markets…" className="ha-input pl-10" />
        </div>
        <select value={sort} onChange={(e) => setSort(e.target.value)} className="ha-input w-auto pr-8" style={{ paddingRight: 32 }}>
```

## Page 21

```text
          <option value="volume">Volume (24h)</option><option value="traders">Most traders</option><option value="ending">Closing soon</option><option value="new">Newest</option>
        </select>
        <div className="hidden sm:flex border border-[var(--rule)] rounded overflow-hidden">
          <button onClick={() => setLayout("grid")} className={"h-11 w-11 flex items-center justify-center " + (layout === "grid" ? "bg-[var(--ink)] text-[var(--paper)]" : "")}><Grid size={16} /></button>
          <button onClick={() => setLayout("list")} className={"h-11 w-11 flex items-center justify-center " + (layout === "list" ? "bg-[var(--ink)] text-[var(--paper)]" : "")}><List size={16} /></button>
        </div>
      </div>
      <div className="ha-scroll flex gap-2 mb-3 -mx-2 px-2 ha-fade ha-d-3">
        <CatChip active={activeCategory === "all"} onClick={() => setActiveCategory("all")}>All <Mono className="ml-1 text-[10px] opacity-60">{MARKETS.length}</Mono></CatChip>
        {CATEGORIES.map((c) => (
          <CatChip key={c.id} active={activeCategory === c.id} color={c.color} onClick={() => setActiveCategory(c.id)}>{c.label} <Mono className="ml-1 text-[10px] opacity-60">{c.count}</Mono></CatChip>
        ))}
      </div>
      <div className="flex gap-2 mb-6 ha-fade ha-d-4">
        {[{ id: "open", label: "Open" }, { id: "closed", label: "Closed" }, { id: "all", label: "All" }].map((s) => (
          <button key={s.id} onClick={() => setActiveStatus(s.id)} className={"ha-chip " + (activeStatus === s.id ? "ha-chip-solid" : "")}>{s.label}</button>
        ))}
      </div>
      {filtered.length === 0 ? (
        <div className="text-center py-16 ha-fade">
          <Search size={32} className="mx-auto text-[var(--ink-3)] mb-3" />
          <Display weight={600} className="text-[18px]">No markets match your filters</Display>
          <p className="ha-mono text-[12px] text-[var(--ink-3)] mt-1">Try clearing the search or selecting a different category.</p>
        </div>
      ) : layout === "grid" ? (
        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-3 ha-fade ha-d-5">
          {filtered.map((m, i) => <DetailedMarketCard key={m.id} market={m} onOpen={onOpenMarket} delay={i} />)}
        </div>
      ) : (
        <div className="ha-card overflow-hidden ha-fade ha-d-5">
          <div className="divide-y divide-[var(--rule-soft)]">
            {filtered.map((m) => <ListRowMarket key={m.id} market={m} onOpen={onOpenMarket} />)}
          </div>
        </div>
      )}
      <div className="mt-12 ha-mono text-[10px] text-[var(--ink-3)] text-center">Showing {filtered.length} of {MARKETS.length} markets · Volumes update every 4 seconds · Fees: protocol 2% + publisher 1%</div>
    </div>
  );
}
function CatChip({ children, active, color, onClick }) {
  return (
    <button onClick={onClick} className="ha-chip whitespace-nowrap shrink-0 ha-hov"
      style={{ background: active ? "var(--ink)" : "var(--paper)", color: active ? "var(--paper)" : color || "var(--ink-2)", borderColor: active ? "var(--ink)" : "var(--rule)" }}>
      {color && <span className="w-1.5 h-1.5 rounded-full" style={{ background: color }} />}{children}
    </button>
  );
```

## Page 22

```text
}
function DetailedMarketCard({ market, onOpen, delay = 0 }) {
  const prob = marketProb(market);
  const cat = categoryById(market.category);
  return (
    <button onClick={() => onOpen(market.id)} className="ha-card ha-hov text-left flex flex-col p-4 ha-fade" style={{ animationDelay: 0.04 * Math.min(delay, 8) + "s" }}>
      <div className="flex items-start gap-3 mb-3">
        <MarketArt name={market.image} size={44} />
        <div className="flex-1 min-w-0">
          <Caps style={{ color: cat?.color }}>{cat?.label}</Caps>
          <div className="flex items-center gap-1.5 mt-1">
            {market.creatorVerified && <BadgeCheck size={11} className="text-[var(--amber)]" />}
            <span className="ha-mono text-[10px] text-[var(--ink-3)] truncate">{market.creator}</span>
          </div>
        </div>
        {market.pinned && <Pin size={12} className="text-[var(--amber)] shrink-0" />}
      </div>
      <div className="ha-display text-[15px] leading-snug font-semibold mb-3 ha-line-clamp-3 min-h-[3.6em]">{market.question}</div>
      <div className="mb-3">
        <div className="flex items-baseline justify-between mb-1.5">
          <Mono className="text-[24px]"><Display weight={600}>{prob}<span className="text-[12px]">%</span></Display></Mono>
          <Mono className="text-[10px] text-[var(--ink-3)]">YES {prob}¢ · NO {100 - prob}¢</Mono>
        </div>
        <div className="ha-split mb-2"><div className="ha-split-y" style={{ width: prob + "%" }} /><div className="ha-split-n" style={{ width: 100 - prob + "%" }} /></div>
        <MiniSparkline data={market.series} prob={prob} height={40} />
      </div>
      <div className="flex items-center justify-between pt-2 border-t border-[var(--rule-soft)] ha-mono text-[10px] text-[var(--ink-3)]">
        <div className="flex items-center gap-1.5"><Activity size={11} /> ${market.volume24h.toLocaleString()} 24h</div>
        <div className="flex items-center gap-1.5"><Users size={11} /> {market.traders.toLocaleString()}</div>
        <div className="flex items-center gap-1.5"><Clock size={11} /> {fmt.rel(market.closeAt)}</div>
      </div>
    </button>
  );
}
function ListRowMarket({ market, onOpen }) {
  const prob = marketProb(market);
  return (
    <button onClick={() => onOpen(market.id)} className="w-full p-4 flex items-center gap-4 hover:bg-[var(--paper-2)] text-left">
      <MarketArt name={market.image} size={44} />
      <div className="flex-1 min-w-0">
        <Caps style={{ color: categoryById(market.category)?.color }}>{categoryById(market.category)?.label}</Caps>
        <div className="ha-display text-[15px] leading-snug font-semibold mt-0.5 ha-line-clamp-2">{market.question}</div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-1 flex items-center gap-3">
          <span>${market.volume24h.toLocaleString()} 24h</span><span>{market.traders.toLocaleString()} trd</span><span>closes {fmt.rel(market.closeAt)}</span>
        </div>
```

## Page 23

```text
      </div>
      <div className="text-right shrink-0 hidden sm:block">
        <Mono className="text-[24px]"><Display weight={600}>{prob}<span className="text-[10px]">%</span></Display></Mono>
        <div className="ha-mono text-[10px] text-[var(--ink-3)]">implied YES</div>
      </div>
      <div className="w-32 hidden md:block"><MiniSparkline data={market.series} prob={prob} height={36} /></div>
      <ChevronRight size={16} className="text-[var(--ink-3)] shrink-0" />
    </button>
  );
}
/* ============================================================================
   MARKET DETAIL — chart + trade ticket + discussion + criteria
   ============================================================================ */
function MarketDetailView({ market, onBack, onPlaceBet, scBalance }) {
  const prob = marketProb(market);
  const [side, setSide] = useState("YES");
  const [amountStr, setAmountStr] = useState("");
  const [tab, setTab] = useState("comments");
  const [chartRange, setChartRange] = useState("ALL");
  const [confirmOpen, setConfirmOpen] = useState(false);
  const amountCents = useMemo(() => { const n = Number(amountStr); if (!Number.isFinite(n) || n <= 0) return 0; return Math.round(n * 100); }, [amountStr]);
  const quote = useMemo(() => { if (amountCents <= 0) return null; return quoteStake({ side, amountCents, yesPool: market.yesPool, noPool: market.noPool }); }, [amountCents, side, market]);
  const overdraft = amountCents > scBalance;
  const canSubmit = quote && quote.ok && !overdraft && amountCents <= 1_000_000;
  const myPosition = POSITIONS.find((p) => p.marketId === market.id);
  const filteredSeries = useMemo(() => {
    if (chartRange === "ALL") return market.series;
    const days = { "1D": 1, "1W": 7, "1M": 30, "3M": 90 }[chartRange];
    return market.series.slice(-days);
  }, [chartRange, market.series]);
  return (
    <div className="pt-4 pb-12">
      <button onClick={onBack} className="flex items-center gap-1.5 text-[12px] text-[var(--ink-3)] hover:text-[var(--ink)] mb-3 ha-mono">
        <ArrowLeft size={14} /> Back to markets
      </button>
      <header className="ha-fade ha-d-1 mb-6">
        <div className="flex items-center gap-2 mb-3 flex-wrap">
          <Pill tone="amber">{categoryById(market.category)?.label}</Pill>
          <span className="ha-mono text-[10px] text-[var(--ink-3)] flex items-center gap-1"><BadgeCheck size={11} className="text-[var(--amber)]" /> {market.creator}</span>
          <span className="ha-mono text-[10px] text-[var(--ink-3)]">·</span>
          <span className="ha-mono text-[10px] text-[var(--ink-3)] flex items-center gap-1"><Clock size={11} /> closes {fmt.dateLong(market.closeAt)}</span>
          <span className="ha-mono text-[10px] text-[var(--ink-3)]">·</span>
          <span className="ha-mono text-[10px] text-[var(--ink-3)] flex items-center gap-1"><Hash size={11} /> {market.id}</span>
        </div>
        <h1 className="ha-display text-[28px] sm:text-[40px] lg:text-[48px] leading-[1.1] font-semibold tracking-tight mb-3 max-w-[920px]">{market.question}</h1>
        <div className="flex items-center gap-2 flex-wrap">
```

## Page 24

```text
          <button className="ha-chip ha-hov"><Share2 size={11} /> Share</button>
          <button className="ha-chip ha-hov"><Bookmark size={11} /> Watch</button>
          <button className="ha-chip ha-hov"><Bell size={11} /> Alerts</button>
          <button className="ha-chip ha-hov"><Flag size={11} /> Report</button>
          <div className="ml-auto flex items-center gap-3 ha-mono text-[10px] text-[var(--ink-3)]">
            <span><Activity size={11} className="inline" /> ${market.volume24h.toLocaleString()} 24h</span>
            <span><Users size={11} className="inline" /> {market.traders.toLocaleString()}</span>
            <span><MessageCircle size={11} className="inline" /> {market.comments}</span>
          </div>
        </div>
      </header>
      <Rule className="mb-6" double />
      <div className="grid grid-cols-1 lg:grid-cols-12 gap-6">
        <div className="lg:col-span-8 space-y-6">
          <section className="ha-card p-5 ha-fade ha-d-2">
            <div className="flex items-baseline justify-between flex-wrap gap-3 mb-4">
              <div>
                <Caps className="text-[var(--ink-3)]">Implied probability · YES</Caps>
                <div className="flex items-baseline gap-3 mt-1">
                  <Mono className="text-[56px] sm:text-[72px] leading-none"><Display weight={700} size={144}>{prob}<span className="text-[28px] text-[var(--ink-3)]">%</span></Display></Mono>
                  <div className="ha-mono text-[12px] text-[var(--ink-3)]">
                    <div>NO {100 - prob}%</div>
                    <div className="text-[10px]">spread {Math.abs(prob - 50)}pts vs 50</div>
                  </div>
                </div>
              </div>
              <div className="flex border border-[var(--rule)] rounded overflow-hidden">
                {["1D", "1W", "1M", "3M", "ALL"].map((r) => (
                  <button key={r} onClick={() => setChartRange(r)} className={"h-8 px-3 ha-mono text-[10px] " + (chartRange === r ? "bg-[var(--ink)] text-[var(--paper)]" : "")}>{r}</button>
                ))}
              </div>
            </div>
            <div className="h-[280px]">
              <ResponsiveContainer width="100%" height="100%">
                <AreaChart data={filteredSeries} margin={{ top: 10, right: 10, left: 0, bottom: 0 }}>
                  <defs><linearGradient id="probG" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stopColor="var(--amber)" stopOpacity={0.25} /><stop offset="100%" stopColor="var(--amber)" stopOpacity={0} /></linearGradient></defs>
                  <CartesianGrid stroke="var(--rule-soft)" strokeDasharray="2 4" vertical={false} />
                  <XAxis dataKey="date" stroke="var(--ink-3)" tick={{ fontSize: 10, fontFamily: "Geist Mono" }} interval="preserveStartEnd" minTickGap={50} />
                  <YAxis domain={[0, 100]} stroke="var(--ink-3)" tick={{ fontSize: 10, fontFamily: "Geist Mono" }} tickFormatter={(v) => v + "%"} width={36} />
                  <Tooltip content={<ChartTooltip />} />
                  <ReferenceLine y={50} stroke="var(--rule)" strokeDasharray="3 3" />
                  <Area type="monotone" dataKey="pct" stroke="var(--amber)" strokeWidth={2} fill="url(#probG)" dot={false} activeDot={{ r: 4, fill: "var(--amber)", stroke: "var(--paper)", strokeWidth: 2 }} />
                </AreaChart>
              </ResponsiveContainer>
            </div>
            <div className="grid grid-cols-3 sm:grid-cols-6 gap-3 mt-5 pt-4 border-t border-[var(--rule-soft)]">
              <ChartStat label="Open" value={filteredSeries[0]?.pct + "%"} />
```

## Page 25

```text
              <ChartStat label="High" value={Math.max(...filteredSeries.map((s) => s.pct)) + "%"} />
              <ChartStat label="Low" value={Math.min(...filteredSeries.map((s) => s.pct)) + "%"} />
              <ChartStat label="Volume" value={"$" + market.volume24h.toLocaleString()} />
              <ChartStat label="Traders" value={market.traders.toLocaleString()} />
              <ChartStat label="Liquidity" value={"$" + ((market.yesPool + market.noPool) / 100).toFixed(0)} />
            </div>
          </section>
          <section className="ha-card p-5 ha-fade ha-d-3">
            <Caps className="text-[var(--ink-3)] block mb-3">Pool composition</Caps>
            <div className="flex items-stretch gap-4">
              <div className="flex-1">
                <div className="flex items-baseline justify-between mb-1.5">
                  <span className="ha-mono text-[12px] text-[var(--yes-deep)] font-medium">YES</span>
                  <Mono className="text-[14px]">${(market.yesPool / 100).toFixed(0)}</Mono>
                </div>
                <div className="h-12 rounded relative overflow-hidden" style={{ background: "var(--paper-2)" }}>
                  <div className="absolute inset-y-0 left-0 bg-[var(--yes)]" style={{ width: prob + "%" }} />
                  <div className="absolute inset-0 flex items-center justify-center ha-mono text-[11px] text-white font-medium">{prob}% of pool</div>
                </div>
              </div>
              <div className="flex-1">
                <div className="flex items-baseline justify-between mb-1.5">
                  <span className="ha-mono text-[12px] text-[var(--no-deep)] font-medium">NO</span>
                  <Mono className="text-[14px]">${(market.noPool / 100).toFixed(0)}</Mono>
                </div>
                <div className="h-12 rounded relative overflow-hidden" style={{ background: "var(--paper-2)" }}>
                  <div className="absolute inset-y-0 left-0 bg-[var(--no)]" style={{ width: (100 - prob) + "%" }} />
                  <div className="absolute inset-0 flex items-center justify-center ha-mono text-[11px] text-white font-medium">{100 - prob}% of pool</div>
                </div>
              </div>
            </div>
            <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-3 flex items-center gap-2">
              <Info size={11} /> Pool sizes update every 4 seconds. Engine uses LMSR-bootstrap below 100 SC pool, pure parimutuel above.
            </div>
          </section>
          <section className="ha-card overflow-hidden ha-fade ha-d-4">
            <div className="border-b border-[var(--rule)] flex">
              {[{ id: "comments", label: "Discussion", count: market.comments, icon: MessageCircle }, { id: "activity", label: "Trade Tape", count: market.traders, icon: Activity }, { id: "criteria", label: "Resolution", icon: FileText }].map((t) => {
                const Icon = t.icon; const active = tab === t.id;
                return (
                  <button key={t.id} onClick={() => setTab(t.id)} className={"flex-1 px-4 h-12 flex items-center justify-center gap-2 text-[13px] font-medium " + (active ? "border-b-2 border-[var(--ink)] text-[var(--ink)]" : "text-[var(--ink-3)]")}>
                    <Icon size={14} />{t.label}{t.count !== undefined && <Mono className="text-[10px] text-[var(--ink-3)]">({t.count})</Mono>}
                  </button>
                );
              })}
            </div>
            <div className="p-5">
```

## Page 26

```text
              {tab === "comments" && <DiscussionTab />}
              {tab === "activity" && <ActivityTab market={market} />}
              {tab === "criteria" && <CriteriaTab market={market} />}
            </div>
          </section>
          <section className="ha-fade ha-d-5">
            <SectionHeader kicker="Also tracked" title="Related Markets" />
            <div className="grid grid-cols-1 sm:grid-cols-3 gap-3 mt-4">
              {MARKETS.filter((m) => m.id !== market.id && m.category === market.category).slice(0, 3).map((m) => <DetailedMarketCard key={m.id} market={m} onOpen={onBack} />)}
            </div>
          </section>
        </div>
        <aside className="lg:col-span-4 space-y-4 lg:sticky lg:top-[88px] self-start">
          <TradeTicket market={market} side={side} setSide={setSide} amountStr={amountStr} setAmountStr={setAmountStr} quote={quote} canSubmit={canSubmit} overdraft={overdraft} scBalance={scBalance} onSubmit={() => setConfirmOpen(true)} />
          {myPosition && <PositionPanel position={myPosition} market={market} onExit={() => alert("Exit flow")} />}
          <ResolutionMeta market={market} />
        </aside>
      </div>
      {confirmOpen && <ConfirmTradeModal market={market} side={side} amountCents={amountCents} quote={quote} onConfirm={() => { onPlaceBet(market.id, side, amountCents); setConfirmOpen(false); setAmountStr(""); }} onCancel={() => setConfirmOpen(false)} />}
    </div>
  );
}
function ChartTooltip({ active, payload, label }) {
  if (!active || !payload?.length) return null;
  return (
    <div className="ha-card p-2 px-3" style={{ boxShadow: "var(--shadow-lift)", background: "var(--paper)" }}>
      <Caps className="text-[var(--ink-3)] block">{label}</Caps>
      <Mono className="text-[14px]"><Display weight={600}>{payload[0].value}%</Display> YES</Mono>
    </div>
  );
}
function ChartStat({ label, value }) {
  return (<div><Caps className="text-[var(--ink-3)] block">{label}</Caps><Mono className="text-[13px] mt-0.5">{value}</Mono></div>);
}
function TradeTicket({ market, side, setSide, amountStr, setAmountStr, quote, canSubmit, overdraft, scBalance, onSubmit }) {
  const prob = marketProb(market);
  const presetAmounts = [10, 25, 50, 100, 250];
  return (
    <div className="ha-card overflow-hidden">
      <div className="bg-[var(--ink)] text-[var(--paper)] px-4 py-3 flex items-center justify-between">
        <Caps>Trade Ticket</Caps>
        <Mono className="text-[10px] opacity-70">SC · 1 SC = $1</Mono>
      </div>
      <div className="p-4 space-y-4">
        <div className="grid grid-cols-2 gap-2">
```

## Page 27

```text
          <button onClick={() => setSide("YES")} className={"h-12 rounded font-medium transition-all flex flex-col items-center justify-center gap-0.5 " + (side === "YES" ? "bg-[var(--yes)] text-white border border-[var(--yes)]" : "border border-[var(--rule)] text-[var(--ink-2)] hover:border-[var(--ink)]")}>
            <span className="text-[14px] font-semibold">YES</span><Mono className="text-[10px] opacity-90">{prob}¢</Mono>
          </button>
          <button onClick={() => setSide("NO")} className={"h-12 rounded font-medium transition-all flex flex-col items-center justify-center gap-0.5 " + (side === "NO" ? "bg-[var(--no)] text-white border border-[var(--no)]" : "border border-[var(--rule)] text-[var(--ink-2)] hover:border-[var(--ink)]")}>
            <span className="text-[14px] font-semibold">NO</span><Mono className="text-[10px] opacity-90">{100 - prob}¢</Mono>
          </button>
        </div>
        <div>
          <div className="flex items-baseline justify-between mb-1.5">
            <Caps className="text-[var(--ink-3)]">Amount</Caps>
            <span className="ha-mono text-[10px] text-[var(--ink-3)]">balance: {fmt.sc(scBalance, { precise: true })} SC</span>
          </div>
          <div className="relative">
            <input type="text" inputMode="decimal" value={amountStr} onChange={(e) => setAmountStr(e.target.value.replace(/[^\d.]/g, ""))} placeholder="0.00" className="ha-input pr-12 text-right ha-mono text-[18px]" />
            <span className="absolute right-3 top-1/2 -translate-y-1/2 ha-mono text-[12px] text-[var(--ink-3)]">SC</span>
          </div>
          <div className="grid grid-cols-5 gap-1 mt-2">
            {presetAmounts.map((p) => (<button key={p} onClick={() => setAmountStr(String(p))} className="h-7 ha-mono text-[10px] border border-[var(--rule)] rounded hover:border-[var(--ink)] hover:bg-[var(--paper-2)]">{p}</button>))}
          </div>
        </div>
        <div className={"ha-card p-3 transition-all " + (quote ? "" : "opacity-50")}>
          <div className="flex justify-between items-baseline mb-1.5">
            <Caps className="text-[var(--ink-3)]">Order summary</Caps>
            {quote && <Mono className="text-[10px] text-[var(--ink-3)]">@ {(quote.impliedAfter / 100).toFixed(1)}¢</Mono>}
          </div>
          <div className="space-y-1.5 text-[12px]">
            <KV label="Stake" value={quote ? fmt.sc(quote.stakeNet + quote.fee, { precise: true }) + " SC" : "—"} />
            <KV label="Fee (3%)" value={quote ? fmt.sc(quote.fee, { precise: true }) + " SC" : "—"} mute />
            <KV label="Net stake" value={quote ? fmt.sc(quote.stakeNet, { precise: true }) + " SC" : "—"} mute />
            <Rule className="my-2" />
            <KV label={"If " + side + " wins"} value={quote ? fmt.sc(quote.potential, { precise: true }) + " SC" : "—"} accent="yes" />
            <KV label="Net profit" value={quote ? "+" + fmt.sc(quote.potential - (quote.stakeNet + quote.fee), { precise: true }) + " SC" : "—"} accent="amber" />
          </div>
        </div>
        {overdraft && (
          <div className="bg-[var(--no-soft)] border border-[var(--no)] text-[var(--no-deep)] p-2 rounded text-[12px] flex items-center gap-2">
            <AlertCircle size={14} /> Insufficient SC balance for this stake.
          </div>
        )}
        <button onClick={onSubmit} disabled={!canSubmit} className={"w-full h-12 rounded font-semibold transition-all flex items-center justify-center gap-2 " + (side === "YES" ? "ha-btn-yes" : "ha-btn-no") + " ha-btn"}>
          {canSubmit ? `Buy ${side} → ${fmt.sc((quote?.potential ?? 0), { precise: true })} SC max` : "Enter amount"}
        </button>
        <div className="ha-mono text-[10px] text-[var(--ink-3)] flex items-center gap-1.5 pt-2 border-t border-[var(--rule-soft)]">
          <Shield size={10} /> Eligibility verified · 21+ · sweepstakes-eligible state
        </div>
      </div>
    </div>
```

## Page 28

```text
  );
}
function KV({ label, value, mute, accent }) {
  const tone = accent === "yes" ? "text-[var(--yes-deep)]" : accent === "no" ? "text-[var(--no-deep)]" : accent === "amber" ? "text-[var(--amber)]" : mute ? "text-[var(--ink-3)]" : "text-[var(--ink)]";
  return (<div className="flex justify-between"><span className={mute ? "text-[var(--ink-3)]" : ""}>{label}</span><Mono className={tone + " font-medium"}>{value}</Mono></div>);
}
function PositionPanel({ position, market, onExit }) {
  const prob = marketProb(market);
  const currentImplied = position.side === "YES" ? prob : 100 - prob;
  const entryImplied = position.side === "YES" ? position.entryProbBps / 100 : 100 - position.entryProbBps / 100;
  const estValue = position.stakeCents * (currentImplied / entryImplied);
  const pnlCents = Math.round(estValue - position.stakeCents);
  return (
    <div className="ha-card overflow-hidden">
      <div className="bg-[var(--paper-2)] border-b border-[var(--rule)] px-4 py-3 flex items-center justify-between">
        <Caps className="text-[var(--ink-2)]">Your Position</Caps>
        <Pill tone={position.side === "YES" ? "yes" : "no"}>{position.side}</Pill>
      </div>
      <div className="p-4 space-y-3">
        <div className="grid grid-cols-2 gap-3">
          <div><Caps className="text-[var(--ink-3)] block">Stake</Caps><Mono className="text-[16px] mt-0.5"><Display weight={600}>{fmt.sc(position.stakeCents, { precise: true })}</Display> SC</Mono></div>
          <div><Caps className="text-[var(--ink-3)] block">Entry</Caps><Mono className="text-[16px] mt-0.5"><Display weight={600}>{entryImplied.toFixed(0)}</Display>¢</Mono></div>
          <div><Caps className="text-[var(--ink-3)] block">Now</Caps><Mono className="text-[16px] mt-0.5"><Display weight={600}>{currentImplied}</Display>¢</Mono></div>
          <div>
            <Caps className="text-[var(--ink-3)] block">Est. P&amp;L</Caps>
            <Mono className={"text-[16px] mt-0.5 " + (pnlCents >= 0 ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>
              <Display weight={600}>{pnlCents >= 0 ? "+" : ""}{fmt.sc(pnlCents, { precise: true })}</Display>
            </Mono>
          </div>
        </div>
        <Rule />
        <button onClick={onExit} className="ha-btn ha-btn-ghost w-full border border-[var(--ink)]">Exit position now</button>
        <p className="ha-mono text-[10px] text-[var(--ink-3)]">Early exit redeems at current odds with a 2% exit fee on profit only. Hold for resolution to claim full payout.</p>
      </div>
    </div>
  );
}
function ResolutionMeta({ market }) {
  return (
    <div className="ha-card p-4 space-y-3">
      <Caps className="text-[var(--ink-3)] block">Resolution</Caps>
      <div className="space-y-2 text-[12px]">
        <div className="flex justify-between"><span className="text-[var(--ink-3)]">Closes</span><Mono>{fmt.dateLong(market.closeAt)}</Mono></div>
        <div className="flex justify-between"><span className="text-[var(--ink-3)]">Resolves by</span><Mono>{fmt.dateLong(market.resolveAt)}</Mono></div>
```

## Page 29

```text
        <div className="flex justify-between"><span className="text-[var(--ink-3)]">Oracle</span><span className="ha-mono flex items-center gap-1"><BadgeCheck size={11} className="text-[var(--amber)]" /> Arena Council</span></div>
        <div className="flex justify-between"><span className="text-[var(--ink-3)]">Challenge bond</span><Mono>10 SC · 24h window</Mono></div>
      </div>
    </div>
  );
}
function DiscussionTab() {
  const [text, setText] = useState("");
  const [comments, setComments] = useState(COMMENTS);
  return (
    <div>
      <div className="ha-card p-3 mb-4">
        <textarea value={text} onChange={(e) => setText(e.target.value)} placeholder="Share your view on this market…" rows={2} className="w-full bg-transparent outline-none text-[14px] resize-none" />
        <div className="flex justify-between items-center mt-2">
          <span className="ha-mono text-[10px] text-[var(--ink-3)]">{text.length}/500 · markdown supported</span>
          <button disabled={!text.trim()} onClick={() => { setComments((c) => [{ id: Math.random().toString(36).slice(2), user: "you", text, ts: new Date().toISOString(), up: 0, down: 0 }, ...c]); setText(""); }} className="ha-btn ha-btn-sm">Post</button>
        </div>
      </div>
      <div className="space-y-4">
        {comments.map((c) => (
          <div key={c.id} className={"flex gap-3 " + (c.pinned ? "border-l-2 border-[var(--amber)] pl-3" : "")}>
            <div className="w-8 h-8 rounded-full shrink-0 flex items-center justify-center font-semibold text-[12px]" style={{ background: "var(--paper-2)", border: "1px solid var(--rule)" }}>{c.user.slice(0, 2).toUpperCase()}</div>
            <div className="flex-1 min-w-0">
              <div className="flex items-baseline gap-2 mb-1 flex-wrap">
                <span className="text-[13px] font-semibold">@{c.user}</span>
                {c.pinned && <Pill tone="amber">PINNED</Pill>}
                <span className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.rel(c.ts)}</span>
              </div>
              <p className="text-[13px] leading-relaxed">{c.text}</p>
              <div className="flex items-center gap-3 mt-2 ha-mono text-[10px] text-[var(--ink-3)]">
                <button className="flex items-center gap-1 hover:text-[var(--ink)]"><ThumbsUp size={11} /> {c.up}</button>
                <button className="flex items-center gap-1 hover:text-[var(--ink)]"><ThumbsDown size={11} /> {c.down}</button>
                <button className="hover:text-[var(--ink)]">Reply</button>
                <button className="hover:text-[var(--ink)]">Share</button>
              </div>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
}
function ActivityTab({ market }) {
  const entries = useMemo(() => {
    const arr = [];
```

## Page 30

```text
    for (let i = 0; i < 24; i++) {
      const ts = new Date(Date.now() - i * 1000 * 60 * (Math.random() * 30 + 4));
      arr.push({
        id: "act" + i,
        user: ["alpha_quant", "swing_trader_42", "macro_misha", "huggy_native", "vol_surface", "kelly_criterion"][Math.floor(Math.random() * 6)],
        side: Math.random() > 0.5 ? "YES" : "NO",
        action: Math.random() > 0.7 ? "EXIT" : "BUY",
        amount: Math.floor(Math.random() * 10000 + 500),
        price: Math.floor(Math.random() * 60 + 20),
        ts: ts.toISOString(),
      });
    }
    return arr;
  }, [market.id]);
  return (
    <div className="space-y-1">
      <div className="ha-mono text-[10px] text-[var(--ink-3)] grid grid-cols-12 gap-2 px-2 pb-2 border-b border-[var(--rule)]">
        <div className="col-span-1">Time</div><div className="col-span-3">Trader</div><div className="col-span-2">Side</div>
        <div className="col-span-2 text-right">Price</div><div className="col-span-2 text-right">Size</div><div className="col-span-2 text-right">Action</div>
      </div>
      {entries.map((a) => (
        <div key={a.id} className="grid grid-cols-12 gap-2 px-2 py-1.5 ha-mono text-[11px] hover:bg-[var(--paper-2)] rounded">
          <div className="col-span-1 text-[var(--ink-3)]">{fmt.rel(a.ts).replace(" ago", "")}</div>
          <div className="col-span-3">@{a.user}</div>
          <div className={"col-span-2 " + (a.side === "YES" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>{a.side}</div>
          <div className="col-span-2 text-right">{a.price}¢</div>
          <div className="col-span-2 text-right">{fmt.sc(a.amount)} SC</div>
          <div className="col-span-2 text-right text-[var(--ink-3)]">{a.action}</div>
        </div>
      ))}
      <div className="text-center pt-3">
        <button className="ha-mono text-[11px] text-[var(--ink-3)] underline">load earlier trades →</button>
      </div>
    </div>
  );
}
function CriteriaTab({ market }) {
  return (
    <div className="space-y-5">
      <div>
        <Caps className="text-[var(--ink-3)] block mb-2">Resolution Criteria</Caps>
        <p className="ha-display text-[15px] leading-relaxed text-[var(--ink-2)]">{market.description}</p>
      </div>
      <Rule />
      <div>
        <Caps className="text-[var(--ink-3)] block mb-2">Sources</Caps>
```

## Page 31

```text
        <div className="space-y-2 text-[13px]">
          <div className="flex items-center gap-2"><Pill tone="amber">Primary</Pill><span className="ha-mono">openai.com/blog</span></div>
          <div className="flex items-center gap-2"><Pill tone="soft">Fallback</Pill><span className="ha-mono">SEC EDGAR · Reuters</span></div>
        </div>
      </div>
      <Rule />
      <div>
        <Caps className="text-[var(--ink-3)] block mb-2">Edge Cases</Caps>
        <ul className="space-y-1.5 text-[13px] text-[var(--ink-2)] list-disc pl-5">
          <li>If a model is leaked or rebranded under a different name (e.g. "GPT-V"), oracle uses public marketing materials at time of release as primary source.</li>
          <li>If OpenAI's corporate structure changes (acquisition, restructure), the entity continuing the GPT product line is treated as OpenAI for this market.</li>
          <li>Beta access without general availability does not resolve YES; product must be available to consumers.</li>
        </ul>
      </div>
      <Rule />
      <div>
        <Caps className="text-[var(--ink-3)] block mb-2">Disputes & Bonds</Caps>
        <p className="text-[13px] text-[var(--ink-2)]">Resolution is proposed by the oracle 24 hours after market close. Any user may file a challenge by posting a 10 SC bond during a 24-hour challenge window. Successful challenges return the bond plus a 5 SC reward; failed challenges forfeit the bond to the dispute reserve.</p>
      </div>
    </div>
  );
}
function ConfirmTradeModal({ market, side, amountCents, quote, onConfirm, onCancel }) {
  return (
    <div className="fixed inset-0 z-50 bg-black/40 flex items-end sm:items-center justify-center p-4" onClick={onCancel}>
      <div onClick={(e) => e.stopPropagation()} className="ha-paper-card ha-card max-w-[440px] w-full" style={{ boxShadow: "var(--shadow-lift)" }}>
        <div className="p-5 border-b border-[var(--rule)]">
          <Caps className="text-[var(--ink-3)] block mb-1">Confirm trade</Caps>
          <Display weight={700} className="text-[24px] leading-tight">Buy {side} on…</Display>
          <p className="ha-display-italic text-[14px] text-[var(--ink-2)] mt-1 ha-line-clamp-2">{market.question}</p>
        </div>
        <div className="p-5 space-y-2 text-[13px]">
          <KV label="Side" value={<span className={side === "YES" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]"}>{side}</span>} />
          <KV label="Stake" value={fmt.sc(amountCents, { precise: true }) + " SC"} />
          <KV label="Fee" value={fmt.sc(quote.fee, { precise: true }) + " SC"} mute />
          <Rule className="my-3" />
          <KV label="Max payout" value={fmt.sc(quote.potential, { precise: true }) + " SC"} accent="yes" />
          <KV label="Net profit if win" value={"+" + fmt.sc(quote.potential - amountCents, { precise: true }) + " SC"} accent="amber" />
        </div>
        <div className="p-5 border-t border-[var(--rule)] flex gap-2">
          <button onClick={onCancel} className="ha-btn ha-btn-ghost flex-1 border border-[var(--rule)]">Cancel</button>
          <button onClick={onConfirm} className={"ha-btn flex-1 " + (side === "YES" ? "ha-btn-yes" : "ha-btn-no")}>Confirm trade</button>
        </div>
        <div className="px-5 pb-4 ha-mono text-[10px] text-[var(--ink-3)] text-center">By confirming, you acknowledge that prediction markets carry risk and outcomes are not guaranteed.</div>
      </div>
    </div>
```

## Page 32

```text
  );
}
/* ============================================================================
   PORTFOLIO — positions, P&L, equity curve, history
   ============================================================================ */
function PortfolioView({ onOpenMarket }) {
  const [tab, setTab] = useState("open");
  const stats = useMemo(() => {
    let totalStake = 0, totalCurrentValue = 0, totalPnl = 0;
    POSITIONS.forEach((p) => {
      const m = marketById(p.marketId); if (!m) return;
      const prob = marketProb(m);
      const currentImplied = p.side === "YES" ? prob : 100 - prob;
      const entryImplied = p.side === "YES" ? p.entryProbBps / 100 : 100 - p.entryProbBps / 100;
      const estValue = p.stakeCents * (currentImplied / entryImplied);
      totalStake += p.stakeCents; totalCurrentValue += estValue; totalPnl += estValue - p.stakeCents;
    });
    return { totalStake, totalCurrentValue, totalPnl, count: POSITIONS.length };
  }, []);
  const perfSeries = useMemo(() => {
    const arr = []; let v = 100000;
    for (let i = 0; i < 60; i++) {
      v += (Math.random() - 0.45) * 3500;
      const d = new Date(); d.setDate(d.getDate() - (60 - i));
      arr.push({ date: d.toISOString().slice(5, 10), value: Math.round(v) });
    }
    return arr;
  }, []);
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section III</span><span>·</span><span>your book</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1] block">Portfolio</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">Your open positions, realised P&amp;L, and the audit trail of every trade you've made on Huggy Arena.</p>
      </div>
      <Rule className="mb-6" double />
      <div className="grid grid-cols-2 sm:grid-cols-4 gap-3 ha-fade ha-d-2">
        <PortfolioStat label="Open positions" value={stats.count.toString()} sub={fmt.sc(stats.totalStake) + " SC staked"} />
        <PortfolioStat label="Current value" value={fmt.sc(stats.totalCurrentValue) + " SC"} sub={"≈ " + fmt.usd(stats.totalCurrentValue)} />
        <PortfolioStat label="Unrealised P&L" value={(stats.totalPnl >= 0 ? "+" : "") + fmt.sc(stats.totalPnl) + " SC"} sub={(stats.totalPnl / stats.totalStake * 100).toFixed(1) + "% on stake"} accent={stats.totalPnl >= 0 ? "yes" : "no"} />
        <PortfolioStat label="Win rate · 30d" value="51.2%" sub="48 trades · ranked #10" />
      </div>
      <section className="ha-card mt-6 p-5 ha-fade ha-d-3">
        <div className="flex items-baseline justify-between flex-wrap gap-2 mb-3">
          <div>
```

## Page 33

```text
            <Caps className="text-[var(--ink-3)] block">Equity curve · last 60 days</Caps>
            <Mono className="text-[28px] mt-1"><Display weight={600}>+28,400 SC</Display></Mono>
            <span className="ha-mono text-[11px] text-[var(--yes-deep)] ml-2">▲ 12.4%</span>
          </div>
          <div className="flex gap-1">
            {["7D", "30D", "60D", "1Y"].map((r) => (<button key={r} className={"h-8 px-3 ha-mono text-[10px] rounded " + (r === "60D" ? "bg-[var(--ink)] text-[var(--paper)]" : "border border-[var(--rule)]")}>{r}</button>))}
          </div>
        </div>
        <div className="h-[220px]">
          <ResponsiveContainer width="100%" height="100%">
            <AreaChart data={perfSeries} margin={{ top: 6, right: 0, left: 0, bottom: 0 }}>
              <defs><linearGradient id="perfG" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stopColor="var(--yes)" stopOpacity={0.2} /><stop offset="100%" stopColor="var(--yes)" stopOpacity={0} /></linearGradient></defs>
              <CartesianGrid stroke="var(--rule-soft)" strokeDasharray="2 4" vertical={false} />
              <XAxis dataKey="date" stroke="var(--ink-3)" tick={{ fontSize: 10, fontFamily: "Geist Mono" }} interval={9} />
              <YAxis stroke="var(--ink-3)" tick={{ fontSize: 10, fontFamily: "Geist Mono" }} width={56} tickFormatter={(v) => fmt.sc(v)} />
              <Tooltip content={({ active, payload, label }) => active && payload?.length ? (<div className="ha-card p-2 px-3" style={{ boxShadow: "var(--shadow-lift)" }}><Caps className="text-[var(--ink-3)]">{label}</Caps><Mono className="block text-[14px]">{fmt.sc(payload[0].value)} SC</Mono></div>) : null} />
              <Area type="monotone" dataKey="value" stroke="var(--yes)" strokeWidth={2} fill="url(#perfG)" dot={false} />
            </AreaChart>
          </ResponsiveContainer>
        </div>
      </section>
      <div className="border-b border-[var(--rule)] mt-8 flex gap-1 ha-fade ha-d-4">
        {[{ id: "open", label: "Open positions", count: POSITIONS.length }, { id: "resolved", label: "Resolved", count: 23 }, { id: "activity", label: "Activity", count: TRANSACTIONS.length }].map((t) => (
          <button key={t.id} onClick={() => setTab(t.id)} className={"px-4 h-11 text-[13px] font-medium flex items-center gap-2 " + (tab === t.id ? "border-b-2 border-[var(--ink)] text-[var(--ink)]" : "text-[var(--ink-3)]")}>
            {t.label}<Mono className="text-[10px] text-[var(--ink-3)]">({t.count})</Mono>
          </button>
        ))}
      </div>
      <div className="mt-5 ha-fade ha-d-5">
        {tab === "open" && <OpenPositionsList onOpenMarket={onOpenMarket} />}
        {tab === "resolved" && <ResolvedPositionsList />}
        {tab === "activity" && <ActivityHistoryList onOpenMarket={onOpenMarket} />}
      </div>
    </div>
  );
}
function PortfolioStat({ label, value, sub, accent }) {
  const color = accent === "yes" ? "text-[var(--yes-deep)]" : accent === "no" ? "text-[var(--no-deep)]" : "";
  return (
    <div className="ha-card p-4">
      <Caps className="text-[var(--ink-3)] block mb-2">{label}</Caps>
      <Mono className={"text-[26px] sm:text-[30px] leading-none block " + color}><Display weight={600}>{value}</Display></Mono>
      <span className="ha-mono text-[10px] text-[var(--ink-3)] block mt-1.5">{sub}</span>
    </div>
  );
}
```

## Page 34

```text
function OpenPositionsList({ onOpenMarket }) {
  return (
    <div className="space-y-3">
      {POSITIONS.map((p) => {
        const m = marketById(p.marketId); if (!m) return null;
        const prob = marketProb(m);
        const currentImplied = p.side === "YES" ? prob : 100 - prob;
        const entryImplied = p.side === "YES" ? p.entryProbBps / 100 : 100 - p.entryProbBps / 100;
        const estValue = p.stakeCents * (currentImplied / entryImplied);
        const pnl = Math.round(estValue - p.stakeCents);
        const pnlPct = (pnl / p.stakeCents) * 100;
        return (
          <button key={p.id} onClick={() => onOpenMarket(p.marketId)} className="w-full ha-card ha-hov p-4 text-left flex flex-col sm:flex-row sm:items-center gap-4">
            <div className="flex items-start gap-3 flex-1 min-w-0">
              <MarketArt name={m.image} size={48} />
              <div className="min-w-0 flex-1">
                <div className="flex items-center gap-2 mb-1">
                  <Pill tone={p.side === "YES" ? "yes" : "no"}>{p.side}</Pill>
                  <Caps className="text-[var(--ink-3)]">{categoryById(m.category)?.label}</Caps>
                </div>
                <div className="ha-display text-[14px] sm:text-[15px] leading-snug font-semibold ha-line-clamp-2">{m.question}</div>
                <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-1">opened {fmt.rel(p.openedAt)} · closes {fmt.rel(m.closeAt)}</div>
              </div>
            </div>
            <div className="grid grid-cols-3 sm:flex sm:gap-6 gap-3 shrink-0">
              <div className="text-left sm:text-right"><Caps className="text-[var(--ink-3)] block">Stake</Caps><Mono className="text-[14px] mt-0.5">{fmt.sc(p.stakeCents, { precise: true })}</Mono></div>
              <div className="text-left sm:text-right"><Caps className="text-[var(--ink-3)] block">Entry → Now</Caps><Mono className="text-[14px] mt-0.5">{entryImplied.toFixed(0)}¢ → {currentImplied}¢</Mono></div>
              <div className="text-left sm:text-right">
                <Caps className="text-[var(--ink-3)] block">P&L</Caps>
                <Mono className={"text-[14px] mt-0.5 " + (pnl >= 0 ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>
                  {pnl >= 0 ? "+" : ""}{fmt.sc(pnl, { precise: true })} <span className="text-[10px] opacity-70">({pnlPct >= 0 ? "+" : ""}{pnlPct.toFixed(1)}%)</span>
                </Mono>
              </div>
            </div>
          </button>
        );
      })}
    </div>
  );
}
function ResolvedPositionsList() {
  const resolved = [
    { id: "r1", question: "Will Anthropic raise a Series E in Q1 2026?", side: "YES", stake: 4500, payout: 8700, outcome: "YES", resolvedAt: "2026-04-22T20:11:00Z" },
    { id: "r2", question: "Will the Fed cut rates in March 2026?", side: "NO", stake: 6000, payout: 11200, outcome: "NO", resolvedAt: "2026-04-15T18:30:00Z" },
    { id: "r3", question: "Will Sora 2 be released before April 2026?", side: "YES", stake: 3200, payout: 0, outcome: "NO", resolvedAt: "2026-04-08T14:00:00Z" },
```

## Page 35

```text
    { id: "r4", question: "Will Llama 4 release in Q1 2026?", side: "YES", stake: 5000, payout: 9100, outcome: "YES", resolvedAt: "2026-04-02T11:22:00Z" },
    { id: "r5", question: "Will Apple announce Vision Pro 2 in March?", side: "NO", stake: 2800, payout: 4200, outcome: "NO", resolvedAt: "2026-03-28T16:45:00Z" },
    { id: "r6", question: "Will Nvidia hit $1.5T market cap?", side: "YES", stake: 7500, payout: 14800, outcome: "YES", resolvedAt: "2026-03-20T09:14:00Z" },
  ];
  return (
    <div className="ha-card overflow-hidden">
      <table className="w-full">
        <thead>
          <tr className="text-left ha-mono text-[10px] text-[var(--ink-3)] border-b border-[var(--rule)]">
            <th className="py-3 px-4 font-medium">Market</th>
            <th className="py-3 px-4 font-medium hidden sm:table-cell">Side</th>
            <th className="py-3 px-4 font-medium text-right">Stake</th>
            <th className="py-3 px-4 font-medium text-right">Payout</th>
            <th className="py-3 px-4 font-medium text-right">P&L</th>
            <th className="py-3 px-4 font-medium hidden md:table-cell">Resolved</th>
          </tr>
        </thead>
        <tbody>
          {resolved.map((r) => {
            const pnl = r.payout - r.stake; const won = pnl > 0;
            return (
              <tr key={r.id} className="border-b border-[var(--rule-soft)] last:border-b-0 hover:bg-[var(--paper-2)]">
                <td className="py-3 px-4">
                  <div className="text-[13px] ha-line-clamp-2">{r.question}</div>
                  <div className="ha-mono text-[10px] text-[var(--ink-3)] sm:hidden">{r.side} · {fmt.rel(r.resolvedAt)}</div>
                </td>
                <td className="py-3 px-4 hidden sm:table-cell"><Pill tone={r.side === "YES" ? "yes" : "no"}>{r.side}</Pill></td>
                <td className="py-3 px-4 text-right ha-mono text-[12px]">{fmt.sc(r.stake)}</td>
                <td className="py-3 px-4 text-right ha-mono text-[12px]">{fmt.sc(r.payout)}</td>
                <td className={"py-3 px-4 text-right ha-mono text-[12px] " + (won ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>{won ? "+" : ""}{fmt.sc(pnl)}</td>
                <td className="py-3 px-4 ha-mono text-[10px] text-[var(--ink-3)] hidden md:table-cell">{fmt.date(r.resolvedAt)}</td>
              </tr>
            );
          })}
        </tbody>
      </table>
    </div>
  );
}
function ActivityHistoryList({ onOpenMarket }) {
  const [filter, setFilter] = useState("all");
  const filtered = TRANSACTIONS.filter((t) => {
    if (filter === "all") return true;
    if (filter === "sc") return t.currency === "SC";
    if (filter === "gc") return t.currency === "GC";
    if (filter === "bets") return t.reason === "bet_placed";
```

## Page 36

```text
    return true;
  });
  return (
    <div>
      <div className="flex gap-2 mb-4 ha-scroll">
        {[{ id: "all", label: "All" }, { id: "sc", label: "SC only" }, { id: "gc", label: "GC only" }, { id: "bets", label: "Bets" }].map((f) => (
          <button key={f.id} onClick={() => setFilter(f.id)} className={"ha-chip " + (filter === f.id ? "ha-chip-solid" : "")}>{f.label}</button>
        ))}
      </div>
      <div className="ha-card overflow-hidden">
        <div className="divide-y divide-[var(--rule-soft)]">
          {filtered.map((t) => (
            <div key={t.id} className="p-3 flex items-center gap-3">
              <div className={"w-9 h-9 rounded flex items-center justify-center shrink-0 " + (t.direction === "credit" ? "bg-[var(--yes-soft)]" : "bg-[var(--no-soft)]")}>
                {t.direction === "credit" ? <ArrowDownRight size={14} className="text-[var(--yes-deep)]" /> : <ArrowUpRight size={14} className="text-[var(--no-deep)]" />}
              </div>
              <div className="flex-1 min-w-0">
                <div className="text-[13px] font-medium truncate">{t.note}</div>
                <div className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.dateLong(t.ts)} · {fmt.time(t.ts)} · {t.reason.replace(/_/g, " ")}</div>
              </div>
              <div className="text-right shrink-0">
                <Mono className={"text-[13px] " + (t.direction === "credit" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>
                  {t.direction === "credit" ? "+" : "−"}{t.currency === "GC" ? fmt.gc(t.amount) : fmt.sc(t.amount, { precise: true })}
                </Mono>
                <div className="ha-mono text-[10px] text-[var(--ink-3)]">{t.currency}</div>
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}
/* ============================================================================
   WALLET — full ledger with balance cards, history, charts
   ============================================================================ */
function WalletView({ scBalance, gcBalance, onNavigate }) {
  const [filter, setFilter] = useState("all");
  const filtered = TRANSACTIONS.filter((t) => {
    if (filter === "all") return true;
    if (filter === "sc") return t.currency === "SC";
    if (filter === "gc") return t.currency === "GC";
    if (filter === "credits") return t.direction === "credit";
    if (filter === "debits") return t.direction === "debit";
    return true;
  });
```

## Page 37

```text
  // Build a 30-day balance series for the chart
  const balanceSeries = useMemo(() => {
    const arr = []; let sc = 360000;
    for (let i = 0; i < 30; i++) {
      sc += (Math.random() - 0.4) * 4000;
      const d = new Date(); d.setDate(d.getDate() - (30 - i));
      arr.push({ date: d.toISOString().slice(5, 10), sc: Math.round(sc), gc: Math.round(12000 + Math.random() * 6000) });
    }
    arr[arr.length - 1].sc = scBalance;
    arr[arr.length - 1].gc = gcBalance;
    return arr;
  }, [scBalance, gcBalance]);
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section IV</span><span>·</span><span>treasury &amp; ledger</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Wallet</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          Two currencies, one ledger. Gold Coins are entertainment; Sweeps Coins are redeemable. Both are tracked here, every transaction reconciled to the cent.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Balance cards */}
      <div className="grid grid-cols-1 md:grid-cols-2 gap-4 ha-fade ha-d-2">
        <div className="ha-card p-5 relative overflow-hidden">
          <div className="flex items-center justify-between mb-3">
            <div className="flex items-center gap-2">
              <Coins size={18} className="text-[var(--gold)]" />
              <Caps>Gold Coins</Caps>
            </div>
            <Pill tone="soft">play money · non-redeemable</Pill>
          </div>
          <Mono className="text-[48px] sm:text-[56px] leading-none block">
            <Display weight={700}>{fmt.gc(gcBalance)}</Display>
          </Mono>
          <div className="ha-mono text-[11px] text-[var(--ink-3)] mt-2 mb-4">Used for entertainment-only play. Cannot be redeemed for cash or prizes.</div>
          <div className="flex gap-2">
            <button onClick={() => onNavigate("shop")} className="ha-btn ha-btn-sm flex-1"><Plus size={14} /> Buy more</button>
            <button onClick={() => onNavigate("markets")} className="ha-btn ha-btn-ghost ha-btn-sm border border-[var(--rule)] flex-1">Play with GC</button>
          </div>
        </div>
        <div className="ha-card p-5 relative overflow-hidden" style={{ borderColor: "var(--amber)", borderWidth: 2 }}>
          <div className="absolute -top-12 -right-12 w-32 h-32 rounded-full opacity-10" style={{ background: "var(--amber)" }} />
```

## Page 38

```text
          <div className="flex items-center justify-between mb-3 relative">
            <div className="flex items-center gap-2">
              <Sparkles size={18} className="text-[var(--amber)]" />
              <Caps>Sweeps Coins</Caps>
            </div>
            <Pill tone="amber">redeemable · 1 SC = $1</Pill>
          </div>
          <Mono className="text-[48px] sm:text-[56px] leading-none block relative">
            <Display weight={700}>{fmt.sc(scBalance, { precise: true })}</Display>
          </Mono>
          <div className="ha-mono text-[11px] text-[var(--ink-3)] mt-2 mb-4">≈ {fmt.usd(scBalance)} when redeemed. Available for prize redemption subject to KYC and state eligibility.</div>
          <div className="flex gap-2">
            <button onClick={() => onNavigate("free-sc")} className="ha-btn ha-btn-ghost ha-btn-sm border border-[var(--rule)] flex-1"><Gift size={14} /> Earn free</button>
            <button onClick={() => onNavigate("redeem")} className="ha-btn ha-btn-amber ha-btn-sm flex-1"><ArrowDownUp size={14} /> Redeem</button>
          </div>
        </div>
      </div>
      {/* Balance chart */}
      <section className="ha-card mt-6 p-5 ha-fade ha-d-3">
        <div className="flex items-baseline justify-between mb-3">
          <div>
            <Caps className="text-[var(--ink-3)] block">SC balance · last 30 days</Caps>
            <Mono className="text-[28px] mt-1"><Display weight={600}>{fmt.sc(scBalance, { precise: true })} SC</Display></Mono>
          </div>
          <Mono className="text-[11px] text-[var(--yes-deep)]">▲ +14.2% MoM</Mono>
        </div>
        <div className="h-[180px]">
          <ResponsiveContainer width="100%" height="100%">
            <AreaChart data={balanceSeries} margin={{ top: 4, right: 0, left: 0, bottom: 0 }}>
              <defs><linearGradient id="walG" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stopColor="var(--amber)" stopOpacity={0.2} /><stop offset="100%" stopColor="var(--amber)" stopOpacity={0} /></linearGradient></defs>
              <CartesianGrid stroke="var(--rule-soft)" strokeDasharray="2 4" vertical={false} />
              <XAxis dataKey="date" stroke="var(--ink-3)" tick={{ fontSize: 10, fontFamily: "Geist Mono" }} interval={4} />
              <YAxis stroke="var(--ink-3)" tick={{ fontSize: 10, fontFamily: "Geist Mono" }} width={56} tickFormatter={(v) => fmt.sc(v)} />
              <Tooltip content={({ active, payload, label }) => active && payload?.length ? (<div className="ha-card p-2 px-3" style={{ boxShadow: "var(--shadow-lift)" }}><Caps className="text-[var(--ink-3)]">{label}</Caps><Mono className="block text-[13px]">{fmt.sc(payload[0].value)} SC</Mono></div>) : null} />
              <Area type="monotone" dataKey="sc" stroke="var(--amber)" strokeWidth={2} fill="url(#walG)" dot={false} />
            </AreaChart>
          </ResponsiveContainer>
        </div>
      </section>
      {/* Quick actions strip */}
      <section className="grid grid-cols-2 sm:grid-cols-4 gap-3 mt-6 ha-fade ha-d-4">
        <WalletAction icon={Coins} label="Buy GC" sub="from $4.99" onClick={() => onNavigate("shop")} accent="gold" />
        <WalletAction icon={Gift} label="Free SC" sub="AMOE & bonus" onClick={() => onNavigate("free-sc")} accent="amber" />
        <WalletAction icon={ArrowDownUp} label="Redeem" sub="SC → USD" onClick={() => onNavigate("redeem")} accent="amber" />
        <WalletAction icon={Receipt} label="Statements" sub="export CSV" onClick={() => alert("Statement export — coming soon")} />
```

## Page 39

```text
      </section>
      {/* Transaction history */}
      <section className="mt-8 ha-fade ha-d-5">
        <div className="flex items-baseline justify-between mb-3">
          <SectionHeader kicker="Ledger" title="Transaction History" />
        </div>
        <div className="flex gap-2 mb-4 ha-scroll">
          {[{ id: "all", label: "All" }, { id: "sc", label: "SC only" }, { id: "gc", label: "GC only" }, { id: "credits", label: "Credits" }, { id: "debits", label: "Debits" }].map((f) => (
            <button key={f.id} onClick={() => setFilter(f.id)} className={"ha-chip " + (filter === f.id ? "ha-chip-solid" : "")}>{f.label}</button>
          ))}
        </div>
        <div className="ha-card overflow-hidden">
          <div className="divide-y divide-[var(--rule-soft)]">
            {filtered.map((t) => (
              <div key={t.id} className="p-4 flex items-center gap-3">
                <div className={"w-10 h-10 rounded flex items-center justify-center shrink-0 " + (t.direction === "credit" ? "bg-[var(--yes-soft)]" : "bg-[var(--no-soft)]")}>
                  {t.direction === "credit" ? <ArrowDownRight size={16} className="text-[var(--yes-deep)]" /> : <ArrowUpRight size={16} className="text-[var(--no-deep)]" />}
                </div>
                <div className="flex-1 min-w-0">
                  <div className="text-[14px] font-medium truncate">{t.note}</div>
                  <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-0.5">{fmt.dateLong(t.ts)} · {fmt.time(t.ts)} · <span className="ha-smcp">{t.reason.replace(/_/g, " ")}</span></div>
                </div>
                <div className="text-right shrink-0">
                  <Mono className={"text-[15px] " + (t.direction === "credit" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>
                    {t.direction === "credit" ? "+" : "−"}{t.currency === "GC" ? fmt.gc(t.amount) : fmt.sc(t.amount, { precise: true })}
                  </Mono>
                  <div className="ha-mono text-[10px] text-[var(--ink-3)]">{t.currency}</div>
                </div>
              </div>
            ))}
          </div>
        </div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-3 text-center">
          Showing {filtered.length} transactions · All amounts reconciled · Audited daily
        </div>
      </section>
      {/* Compliance reminder */}
      <section className="mt-8 ha-card p-5 ha-paper-card flex items-start gap-4 ha-fade ha-d-6">
        <Shield size={24} className="text-[var(--amber)] shrink-0 mt-0.5" />
        <div>
          <Display weight={600} className="text-[15px] block">Two currencies, one rule: SC is never for sale.</Display>
          <p className="text-[13px] text-[var(--ink-2)] mt-1 max-w-prose">
            Sweeps Coins are received only as bonuses bundled with Gold Coin purchases or via no-purchase-necessary mail-in entry (AMOE). They are never directly purchasable and are awarded under sweepstakes rules.
          </p>
        </div>
```

## Page 40

```text
      </section>
    </div>
  );
}
function WalletAction({ icon: Icon, label, sub, onClick, accent }) {
  const bg = accent === "gold" ? "var(--gold-soft)" : accent === "amber" ? "var(--amber-soft)" : "var(--paper-2)";
  return (
    <button onClick={onClick} className="ha-card ha-hov p-4 text-left flex items-center gap-3">
      <div className="w-10 h-10 rounded flex items-center justify-center shrink-0" style={{ background: bg }}>
        <Icon size={18} className="text-[var(--ink)]" />
      </div>
      <div className="min-w-0">
        <div className="text-[13px] font-medium">{label}</div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)]">{sub}</div>
      </div>
    </button>
  );
}
/* ============================================================================
   SHOP — Gold Coin packages with bundled SC
   ============================================================================ */
function ShopView({ onNavigate, pushToast }) {
  const [selectedPkg, setSelectedPkg] = useState(GC_PACKAGES.find(p => p.featured)?.id || GC_PACKAGES[0].id);
  const [promoCode, setPromoCode] = useState("");
  const [promoApplied, setPromoApplied] = useState(false);
  const [checkoutOpen, setCheckoutOpen] = useState(false);
  const pkg = GC_PACKAGES.find((p) => p.id === selectedPkg) || GC_PACKAGES[0];
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section V</span><span>·</span><span>gold coin store</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Shop Gold Coins</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          Gold Coins for entertainment play. Every package includes a free Sweeps Coins bonus — no purchase necessary for SC, see AMOE for alternative entry.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Package grid */}
      <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-3 mb-8 ha-fade ha-d-2">
        {GC_PACKAGES.map((p, i) => (
          <button
            key={p.id}
            onClick={() => setSelectedPkg(p.id)}
```

## Page 41

```text
            className={"ha-card ha-hov p-4 text-left flex flex-col gap-3 relative " + (selectedPkg === p.id ? "ring-2" : "")}
            style={{ borderColor: selectedPkg === p.id ? "var(--ink)" : undefined, animationDelay: 0.04 * i + "s" }}
          >
            {p.featured && (
              <div className="absolute -top-2 left-3 right-3 mx-auto w-fit">
                <Pill tone="amber"><Star size={10} /> MOST POPULAR</Pill>
              </div>
            )}
            {p.gold && (
              <div className="absolute -top-2 left-3 right-3 mx-auto w-fit">
                <Pill tone="ink"><Crown size={10} /> WHALE TIER</Pill>
              </div>
            )}
            <div>
              <Caps className="text-[var(--ink-3)] block">{p.label}</Caps>
              <div className="flex items-baseline gap-1 mt-1">
                <Coins size={20} className="text-[var(--gold)]" />
                <Mono className="text-[28px]"><Display weight={700}>{fmt.gc(p.gcAmount)}</Display></Mono>
              </div>
              <div className="ha-mono text-[10px] text-[var(--ink-3)]">Gold Coins</div>
            </div>
            <Rule />
            <div>
              <div className="ha-mono text-[10px] text-[var(--ink-3)] mb-1">Free promotional bonus:</div>
              <div className="flex items-baseline gap-1">
                <Sparkles size={14} className="text-[var(--amber)]" />
                <Mono className="text-[18px] text-[var(--amber)]">+{fmt.sc(p.scFreeCents)} SC</Mono>
              </div>
            </div>
            <div className="mt-auto pt-2 border-t border-[var(--rule-soft)]">
              <Mono className="text-[20px]"><Display weight={700}>{fmt.usd(p.priceCents)}</Display></Mono>
              <div className="ha-mono text-[10px] text-[var(--ink-3)]">USD · one-time</div>
            </div>
          </button>
        ))}
      </div>
      {/* Selected package summary */}
      <div className="grid grid-cols-1 lg:grid-cols-3 gap-6 ha-fade ha-d-3">
        <div className="lg:col-span-2 ha-card p-6">
          <Caps className="text-[var(--ink-3)] block mb-3">Order summary</Caps>
          <div className="flex items-center gap-4 pb-4 border-b border-[var(--rule)]">
            <div className="w-16 h-16 rounded flex items-center justify-center" style={{ background: "var(--gold-soft)" }}>
              <Coins size={28} className="text-[var(--gold)]" />
            </div>
            <div className="flex-1">
              <Display weight={600} className="text-[20px] block">{pkg.label} Pack</Display>
```

## Page 42

```text
              <div className="ha-mono text-[12px] text-[var(--ink-3)] mt-1">
                {fmt.gc(pkg.gcAmount)} GC + {fmt.sc(pkg.scFreeCents)} SC bonus
              </div>
            </div>
            <Mono className="text-[24px]"><Display weight={700}>{fmt.usd(pkg.priceCents)}</Display></Mono>
          </div>
          <div className="space-y-2 pt-4 text-[13px]">
            <KV label="Subtotal" value={fmt.usd(pkg.priceCents)} />
            <KV label="Discount" value={promoApplied ? "−" + fmt.usd(Math.floor(pkg.priceCents * 0.1)) : "—"} mute />
            <KV label="Tax" value="$0.00" mute />
            <Rule className="my-3" />
            <KV label="Total" value={fmt.usd(promoApplied ? Math.floor(pkg.priceCents * 0.9) : pkg.priceCents)} accent="amber" />
          </div>
          <div className="mt-5 flex gap-2">
            <input value={promoCode} onChange={(e) => setPromoCode(e.target.value.toUpperCase())} placeholder="Promo code" className="ha-input flex-1" />
            <button
              onClick={() => {
                if (promoCode.trim()) { setPromoApplied(true); pushToast("Promo code applied — 10% off", "success"); }
              }}
              className="ha-btn ha-btn-ghost border border-[var(--rule)]"
            >Apply</button>
          </div>
          {promoApplied && <div className="ha-mono text-[10px] text-[var(--yes-deep)] mt-2 flex items-center gap-1"><Check size={11} /> WELCOME10 applied</div>}
        </div>
        <div className="space-y-4">
          <div className="ha-card p-5">
            <Caps className="text-[var(--ink-3)] block mb-2">Pay with</Caps>
            <div className="space-y-2">
              <label className="ha-card p-3 flex items-center gap-3 cursor-pointer ha-hov">
                <input type="radio" name="payment" defaultChecked className="accent-[var(--ink)]" />
                <CreditCard size={18} />
                <div className="flex-1">
                  <div className="text-[13px] font-medium">Card</div>
                  <div className="ha-mono text-[10px] text-[var(--ink-3)]">Visa · Mastercard · Amex</div>
                </div>
              </label>
              <label className="ha-card p-3 flex items-center gap-3 cursor-pointer ha-hov">
                <input type="radio" name="payment" className="accent-[var(--ink)]" />
                <Square size={18} />
                <div className="flex-1">
                  <div className="text-[13px] font-medium">Apple Pay</div>
                </div>
              </label>
              <label className="ha-card p-3 flex items-center gap-3 cursor-pointer ha-hov">
                <input type="radio" name="payment" className="accent-[var(--ink)]" />
                <Hexagon size={18} />
                <div className="flex-1">
```

## Page 43

```text
                  <div className="text-[13px] font-medium">PayPal</div>
                </div>
              </label>
            </div>
          </div>
          <button onClick={() => setCheckoutOpen(true)} className="w-full ha-btn ha-btn-lg ha-btn-amber">
            <Lock size={16} /> Checkout securely · {fmt.usd(promoApplied ? Math.floor(pkg.priceCents * 0.9) : pkg.priceCents)}
          </button>
          <div className="ha-mono text-[10px] text-[var(--ink-3)] text-center">Payments processed by Stripe · SSL secured · 30-day refund</div>
        </div>
      </div>
      {/* AMOE reminder */}
      <Rule className="my-10" />
      <div className="ha-card p-6 ha-paper-card flex flex-col sm:flex-row items-start gap-4 ha-fade ha-d-5">
        <Gift size={32} className="text-[var(--amber)] shrink-0" />
        <div className="flex-1">
          <Display weight={600} className="text-[18px] block">No purchase necessary to receive Sweeps Coins.</Display>
          <p className="text-[13px] text-[var(--ink-2)] mt-1 max-w-prose">
            All Sweeps Coins available through GC purchase are also available through our free alternate method of entry (AMOE). Send a 3"x5" handwritten postcard to receive an equivalent free SC bonus.
          </p>
          <button onClick={() => onNavigate("free-sc")} className="ha-mono text-[12px] text-[var(--amber)] underline mt-3">Read AMOE rules →</button>
        </div>
      </div>
      {checkoutOpen && (
        <CheckoutModal
          pkg={pkg}
          total={promoApplied ? Math.floor(pkg.priceCents * 0.9) : pkg.priceCents}
          onClose={() => setCheckoutOpen(false)}
          onComplete={() => {
            setCheckoutOpen(false);
            pushToast(`+${fmt.gc(pkg.gcAmount)} GC + ${fmt.sc(pkg.scFreeCents)} SC credited`, "success");
          }}
        />
      )}
    </div>
  );
}
function CheckoutModal({ pkg, total, onClose, onComplete }) {
  const [stage, setStage] = useState("review"); // review | processing | done
  useEffect(() => {
    if (stage === "processing") {
      const t = setTimeout(() => setStage("done"), 1800);
      return () => clearTimeout(t);
    }
```

## Page 44

```text
  }, [stage]);
  return (
    <div className="fixed inset-0 z-50 bg-black/40 flex items-end sm:items-center justify-center p-4" onClick={stage === "review" ? onClose : undefined}>
      <div onClick={(e) => e.stopPropagation()} className="ha-paper-card ha-card max-w-[480px] w-full" style={{ boxShadow: "var(--shadow-lift)" }}>
        {stage === "review" && (
          <>
            <div className="p-5 border-b border-[var(--rule)]">
              <Caps className="text-[var(--ink-3)] block mb-1">Final review</Caps>
              <Display weight={700} className="text-[24px]">Confirm purchase</Display>
            </div>
            <div className="p-5 space-y-2 text-[13px]">
              <KV label="Package" value={pkg.label} />
              <KV label="Gold Coins" value={"+" + fmt.gc(pkg.gcAmount) + " GC"} />
              <KV label="Bonus Sweeps Coins" value={"+" + fmt.sc(pkg.scFreeCents) + " SC"} accent="amber" />
              <Rule className="my-3" />
              <KV label="Total charge" value={fmt.usd(total)} />
              <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-3 bg-[var(--paper-2)] p-3 rounded">
                <Info size={11} className="inline" /> By confirming, you agree to our Terms and acknowledge that Gold Coins have no cash value. Sweeps Coins are awarded as a free bonus.
              </div>
            </div>
            <div className="p-5 border-t border-[var(--rule)] flex gap-2">
              <button onClick={onClose} className="ha-btn ha-btn-ghost flex-1 border border-[var(--rule)]">Cancel</button>
              <button onClick={() => setStage("processing")} className="ha-btn ha-btn-amber flex-1">Pay {fmt.usd(total)}</button>
            </div>
          </>
        )}
        {stage === "processing" && (
          <div className="p-12 text-center">
            <Loader2 size={48} className="mx-auto text-[var(--amber)] animate-spin mb-4" />
            <Display weight={600} className="text-[18px] block">Processing your payment…</Display>
            <p className="ha-mono text-[11px] text-[var(--ink-3)] mt-2">Stripe is verifying your card · do not close this window</p>
          </div>
        )}
        {stage === "done" && (
          <div className="p-8 text-center">
            <div className="w-16 h-16 rounded-full bg-[var(--yes-soft)] mx-auto flex items-center justify-center mb-4">
              <Check size={28} className="text-[var(--yes-deep)]" />
            </div>
            <Display weight={700} className="text-[24px] block">Payment successful</Display>
            <div className="ha-mono text-[12px] text-[var(--ink-3)] mt-2">
              +{fmt.gc(pkg.gcAmount)} GC and +{fmt.sc(pkg.scFreeCents)} SC have been credited to your wallet
            </div>
            <button onClick={onComplete} className="ha-btn ha-btn-amber w-full mt-6">Done</button>
          </div>
        )}
      </div>
    </div>
```

## Page 45

```text
  );
}
/* ============================================================================
   FREE SC — AMOE, daily bonus, referrals (the sweepstakes compliance lever)
   ============================================================================ */
function FreeScView({ pushToast }) {
  const [postcardForm, setPostcardForm] = useState({ name: "", email: "", address: "" });
  const [dailyClaimed, setDailyClaimed] = useState(false);
  const [referralCode] = useState("HUGGY-MONTANA-7Q");
  const [streak] = useState(12);
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section VI</span><span>·</span><span>no purchase necessary</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Free Sweeps Coins</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          You never have to spend a cent. Four ways to receive Sweeps Coins for free — postcard, daily login, referrals, and special promotions. Each method is sweepstakes-compliant and audited.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Method grid */}
      <div className="grid grid-cols-1 md:grid-cols-2 gap-4 ha-fade ha-d-2">
        {/* Method 1: AMOE Postcard */}
        <div className="ha-card p-5">
          <div className="flex items-center gap-2 mb-3">
            <div className="w-10 h-10 rounded flex items-center justify-center bg-[var(--paper-2)]"><Mail size={18} /></div>
            <div>
              <Caps className="text-[var(--ink-3)]">Method 01</Caps>
              <Display weight={600} className="text-[18px] block">Postcard AMOE</Display>
            </div>
            <Pill tone="amber">5 SC per card</Pill>
          </div>
          <p className="text-[13px] text-[var(--ink-2)] mb-4">
            Send a hand-written 3"x5" postcard with your full name, email, date of birth, and the words "FREE SC" to receive 5 Sweeps Coins. Limit one entry per envelope.
          </p>
          <div className="ha-card p-3 bg-[var(--paper-2)] ha-mono text-[11px] text-[var(--ink-2)] leading-relaxed">
            <Mono className="text-[var(--ink)] block">HUGGY ARENA AMOE</Mono>
            <span>c/o Huggy Arena Labs, Inc.</span><br/>
            <span>P.O. Box 1827</span><br/>
            <span>Wilmington, DE 19899</span>
          </div>
          <Rule className="my-4" />
          <Caps className="text-[var(--ink-3)] block mb-2">Quick request</Caps>
          <div className="space-y-2">
```

## Page 46

```text
            <input value={postcardForm.name} onChange={(e) => setPostcardForm({ ...postcardForm, name: e.target.value })} placeholder="Full name" className="ha-input" />
            <input value={postcardForm.email} onChange={(e) => setPostcardForm({ ...postcardForm, email: e.target.value })} placeholder="Email" className="ha-input" />
            <input value={postcardForm.address} onChange={(e) => setPostcardForm({ ...postcardForm, address: e.target.value })} placeholder="Mailing address (for verification)" className="ha-input" />
            <button
              onClick={() => {
                if (postcardForm.name && postcardForm.email && postcardForm.address) {
                  pushToast("AMOE request submitted — postcard expected in 7-14 days", "success");
                  setPostcardForm({ name: "", email: "", address: "" });
                } else { pushToast("Fill in all fields", "error"); }
              }}
              className="ha-btn w-full"
            >Submit AMOE request</button>
          </div>
        </div>
        {/* Method 2: Daily bonus */}
        <div className="ha-card p-5">
          <div className="flex items-center gap-2 mb-3">
            <div className="w-10 h-10 rounded flex items-center justify-center bg-[var(--amber-soft)]"><Flame size={18} className="text-[var(--amber)]" /></div>
            <div>
              <Caps className="text-[var(--ink-3)]">Method 02</Caps>
              <Display weight={600} className="text-[18px] block">Daily Login Bonus</Display>
            </div>
            <Pill tone="amber">{streak}-day streak</Pill>
          </div>
          <p className="text-[13px] text-[var(--ink-2)] mb-4">
            Open the app each day to claim your bonus. Streak rewards grow — day 7 doubles, day 30 triples. Miss a day, streak resets.
          </p>
          {/* Streak calendar */}
          <div className="grid grid-cols-7 gap-1 mb-4">
            {Array.from({ length: 14 }).map((_, i) => {
              const day = i + 1;
              const claimed = day <= streak;
              const today = day === streak + 1;
              return (
                <div
                  key={i}
                  className={"aspect-square rounded flex items-center justify-center text-[10px] ha-mono " +
                    (claimed ? "bg-[var(--amber)] text-white" : today ? "border-2 border-[var(--amber)] bg-[var(--amber-soft)]" : "bg-[var(--paper-2)] text-[var(--ink-3)]")}
                >
                  {claimed ? <Check size={12} /> : day}
                </div>
              );
            })}
          </div>
          <div className="ha-card p-3 bg-[var(--paper-2)] flex items-center justify-between mb-4">
            <div>
```

## Page 47

```text
              <div className="ha-mono text-[10px] text-[var(--ink-3)]">Today's reward</div>
              <Mono className="text-[24px] text-[var(--amber)]"><Display weight={700}>+0.50 SC</Display></Mono>
              <div className="ha-mono text-[10px] text-[var(--ink-3)]">+100 GC bonus</div>
            </div>
            <button
              onClick={() => { setDailyClaimed(true); pushToast("+0.50 SC and +100 GC credited", "success"); }}
              disabled={dailyClaimed}
              className={"ha-btn " + (dailyClaimed ? "" : "ha-btn-amber")}
            >
              {dailyClaimed ? <><Check size={14} /> Claimed</> : "Claim today"}
            </button>
          </div>
          <div className="ha-mono text-[10px] text-[var(--ink-3)] flex items-center gap-1">
            <Info size={11} /> Next streak bonus at day 14 (3x multiplier)
          </div>
        </div>
        {/* Method 3: Referrals */}
        <div className="ha-card p-5">
          <div className="flex items-center gap-2 mb-3">
            <div className="w-10 h-10 rounded flex items-center justify-center bg-[var(--paper-2)]"><Users size={18} /></div>
            <div>
              <Caps className="text-[var(--ink-3)]">Method 03</Caps>
              <Display weight={600} className="text-[18px] block">Referrals</Display>
            </div>
            <Pill tone="amber">5 SC each</Pill>
          </div>
          <p className="text-[13px] text-[var(--ink-2)] mb-4">
            Invite friends — earn 5 SC for each new account that places their first trade. They get 5 SC too. No cap, no expiration.
          </p>
          <div className="ha-card p-3 bg-[var(--paper-2)] mb-3 flex items-center gap-2">
            <Mono className="text-[14px] flex-1 truncate">{referralCode}</Mono>
            <button onClick={() => { navigator.clipboard?.writeText(referralCode); pushToast("Copied", "success"); }} className="ha-btn-sm ha-btn ha-btn-ghost border border-[var(--rule)]">
              <Copy size={12} /> Copy
            </button>
          </div>
          <div className="grid grid-cols-3 gap-2 mb-4">
            <ReferralStat label="Sent" value="14" />
            <ReferralStat label="Joined" value="8" />
            <ReferralStat label="Earned" value="40 SC" accent />
          </div>
          <button className="ha-btn w-full"><Send size={14} /> Share your link</button>
        </div>
        {/* Method 4: Special promotions */}
        <div className="ha-card p-5">
          <div className="flex items-center gap-2 mb-3">
```

## Page 48

```text
            <div className="w-10 h-10 rounded flex items-center justify-center bg-[var(--paper-2)]"><Gift size={18} /></div>
            <div>
              <Caps className="text-[var(--ink-3)]">Method 04</Caps>
              <Display weight={600} className="text-[18px] block">Special Promotions</Display>
            </div>
            <Pill tone="soft">limited</Pill>
          </div>
          <p className="text-[13px] text-[var(--ink-2)] mb-4">
            Periodic bonus events — first trade, prediction accuracy, market creation, and seasonal sweepstakes drawings.
          </p>
          <div className="space-y-2">
            <PromoRow icon={Zap} title="First-trade bonus" reward="+10 SC" sub="Place your first trade · open to all users" status="claim" />
            <PromoRow icon={Target} title="Accuracy bounty" reward="+25 SC" sub="Win 5 trades in a row · 3/5 complete" status="locked" />
            <PromoRow icon={Trophy} title="Weekly leaderboard" reward="up to 500 SC" sub="Top 10 traders Sunday 11:59 PM" status="active" />
            <PromoRow icon={Crown} title="Founder drawing" reward="grand prize" sub="One winner monthly · auto-entered" status="active" />
          </div>
        </div>
      </div>
      {/* Sweepstakes rules */}
      <Rule className="my-10" />
      <section className="ha-card p-6 ha-paper-card ha-fade ha-d-6">
        <div className="flex items-center gap-2 mb-3">
          <Shield size={20} className="text-[var(--amber)]" />
          <Display weight={600} className="text-[18px]">Official Sweepstakes Rules</Display>
        </div>
        <p className="text-[13px] text-[var(--ink-2)] mb-3 max-w-prose">
          All Sweeps Coins available through Gold Coin purchase are also available through these free alternate methods of entry (AMOE). No purchase is ever necessary, and no purchase will increase your chances of winning. Sweeps Coins are awarded under our sweepstakes rules and may be redeemed for prizes subject to verification and state eligibility.
        </p>
        <div className="grid grid-cols-2 md:grid-cols-4 gap-3 mt-4">
          <RuleSummary label="Eligibility" value="U.S. residents, 21+" />
          <RuleSummary label="Excluded states" value="WA, ID" />
          <RuleSummary label="Redemption restricted" value="NV, MI, NY, LA, CT" />
          <RuleSummary label="Verification" value="ID + state of residence" />
        </div>
      </section>
    </div>
  );
}
function ReferralStat({ label, value, accent }) {
  return (
    <div className="text-center">
      <Caps className="text-[var(--ink-3)] block mb-1">{label}</Caps>
      <Mono className={"text-[18px] " + (accent ? "text-[var(--amber)]" : "")}><Display weight={600}>{value}</Display></Mono>
    </div>
  );
```

## Page 49

```text
}
function PromoRow({ icon: Icon, title, reward, sub, status }) {
  return (
    <div className="ha-card p-3 flex items-center gap-3">
      <div className="w-9 h-9 rounded flex items-center justify-center shrink-0 bg-[var(--paper-2)]"><Icon size={15} /></div>
      <div className="flex-1 min-w-0">
        <div className="flex items-baseline gap-2">
          <span className="text-[13px] font-medium">{title}</span>
          <Mono className="text-[11px] text-[var(--amber)]">{reward}</Mono>
        </div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)] truncate">{sub}</div>
      </div>
      {status === "claim" && <button className="ha-btn ha-btn-sm ha-btn-amber">Claim</button>}
      {status === "active" && <Pill tone="soft"><span className="ha-pulse" style={{ color: "var(--yes)" }}>●</span> active</Pill>}
      {status === "locked" && <Lock size={14} className="text-[var(--ink-3)]" />}
    </div>
  );
}
function RuleSummary({ label, value }) {
  return (
    <div className="ha-card p-3">
      <Caps className="text-[var(--ink-3)] block">{label}</Caps>
      <Mono className="text-[12px] block mt-1 text-[var(--ink)]">{value}</Mono>
    </div>
  );
}
/* ============================================================================
   REDEEM — SC → USD prize redemption. Most legally fraught surface. Fail-closed.
   ============================================================================ */
function RedeemView({ scBalance, pushToast }) {
  const [stage, setStage] = useState("amount"); // amount | method | review | submitted
  const [amountStr, setAmountStr] = useState("");
  const [method, setMethod] = useState("paypal");
  const [kycStatus] = useState("verified"); // unverified | pending | verified
  const [stateOfResidence] = useState("CA");
  const amountCents = useMemo(() => { const n = Number(amountStr); if (!Number.isFinite(n) || n <= 0) return 0; return Math.round(n * 100); }, [amountStr]);
  const minRedeem = 5000; // 50 SC
  const maxRedeem = scBalance;
  const overdraft = amountCents > scBalance;
  const belowMin = amountCents > 0 && amountCents < minRedeem;
  const eligibleStates = ["AL", "AK", "AZ", "AR", "CA", "CO", "DE", "FL", "GA", "HI", "IL", "IN", "IA", "KS", "KY", "ME", "MD", "MA", "MN", "MS", "MO", "MT", "NE", "NH", "NJ", "NM", "NC", "ND", "OH", "OK", "OR", "PA", "RI", "SC", "SD", "TN", "TX", "UT", "VT", "VA", "WV", "WI", "WY"];
  const restrictedStates = ["NV", "MI", "NY", "LA", "CT"];
  const blockedStates = ["WA", "ID"];
  const stateEligible = eligibleStates.includes(stateOfResidence);
  const isRestricted = restrictedStates.includes(stateOfResidence);
```

## Page 50

```text
  const isBlocked = blockedStates.includes(stateOfResidence);
  const canSubmit = amountCents >= minRedeem && !overdraft && kycStatus === "verified" && stateEligible;
  const submitRedemption = () => { pushToast("Redemption submitted — 3-5 business days", "success"); setStage("submitted"); };
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section VII</span><span>·</span><span>cash out</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Redeem SC</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          Exchange your Sweeps Coins for cash prizes. 1 SC = $1 USD. All redemptions require verified identity and approved state of residence. Processed within 3-5 business days.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Eligibility gate */}
      <div className="grid grid-cols-1 md:grid-cols-3 gap-3 mb-6 ha-fade ha-d-2">
        <EligibilityCard
          icon={ShieldCheck}
          label="Identity"
          value={kycStatus === "verified" ? "Verified" : "Required"}
          status={kycStatus === "verified" ? "ok" : "warn"}
          sub="Government ID on file"
        />
        <EligibilityCard
          icon={MapPin}
          label="State of residence"
          value={stateOfResidence + (isBlocked ? " · Blocked" : isRestricted ? " · Restricted" : " · Eligible")}
          status={isBlocked ? "err" : isRestricted ? "warn" : "ok"}
          sub={isBlocked ? "Redemption unavailable" : isRestricted ? "Additional verification" : "Sweepstakes-eligible"}
        />
        <EligibilityCard
          icon={Wallet}
          label="Balance"
          value={fmt.sc(scBalance, { precise: true }) + " SC"}
          status="ok"
          sub={"≈ " + fmt.usd(scBalance) + " available"}
        />
      </div>
      {isBlocked ? (
        <div className="ha-card p-8 text-center bg-[var(--no-soft)]">
          <ShieldAlert size={48} className="mx-auto text-[var(--no)] mb-3" />
          <Display weight={700} className="text-[22px] block">Redemption is not available in your state</Display>
          <p className="text-[13px] text-[var(--ink-2)] max-w-prose mx-auto mt-2">
            Due to state law, redemption of Sweeps Coins is not available in {stateOfResidence}. You may continue to play with Gold Coins and earn Sweeps Coins via AMOE, but redemption is restricted.
```

## Page 51

```text
          </p>
        </div>
      ) : (
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-6 ha-fade ha-d-3">
          {/* Left: form */}
          <div className="lg:col-span-2 space-y-4">
            <div className="ha-card p-5">
              <Caps className="text-[var(--ink-3)] block mb-3">Step 1 · Amount to redeem</Caps>
              <div className="relative">
                <input type="text" inputMode="decimal" value={amountStr} onChange={(e) => setAmountStr(e.target.value.replace(/[^\d.]/g, ""))} placeholder="0.00" className="ha-input ha-mono pr-16 text-right text-[24px] h-14" />
                <span className="absolute right-4 top-1/2 -translate-y-1/2 ha-mono text-[14px] text-[var(--ink-3)]">SC</span>
              </div>
              <div className="ha-mono text-[11px] text-[var(--ink-3)] mt-1 flex items-baseline justify-between">
                <span>min 50 SC · max {fmt.sc(maxRedeem)} SC</span>
                <span>≈ {amountCents > 0 ? fmt.usd(amountCents) : "$0.00"} USD</span>
              </div>
              <div className="grid grid-cols-4 gap-2 mt-3">
                {[100, 500, 1000, "max"].map((p) => (
                  <button
                    key={p}
                    onClick={() => setAmountStr(p === "max" ? (scBalance / 100).toFixed(2) : String(p))}
                    className="h-9 ha-mono text-[11px] border border-[var(--rule)] rounded hover:border-[var(--ink)] hover:bg-[var(--paper-2)]"
                  >
                    {p === "max" ? "MAX" : p + " SC"}
                  </button>
                ))}
              </div>
              {belowMin && <div className="mt-3 bg-[var(--no-soft)] text-[var(--no-deep)] p-2 rounded text-[12px] flex items-center gap-2"><AlertCircle size={14} /> Minimum redemption is 50 SC.</div>}
              {overdraft && <div className="mt-3 bg-[var(--no-soft)] text-[var(--no-deep)] p-2 rounded text-[12px] flex items-center gap-2"><AlertCircle size={14} /> Insufficient balance.</div>}
            </div>
            <div className="ha-card p-5">
              <Caps className="text-[var(--ink-3)] block mb-3">Step 2 · Payout method</Caps>
              <div className="space-y-2">
                <PayoutMethod id="paypal" label="PayPal" sub="Instant · no fee · most common" selected={method === "paypal"} onSelect={setMethod} icon={Hexagon} />
                <PayoutMethod id="ach" label="ACH bank transfer" sub="3-5 business days · no fee · USD only" selected={method === "ach"} onSelect={setMethod} icon={CreditCard} />
                <PayoutMethod id="card" label="Visa debit (instant)" sub="Instant · 1% fee · U.S. cards only" selected={method === "card"} onSelect={setMethod} icon={CreditCard} />
                <PayoutMethod id="gift" label="Gift card" sub="Amazon · Target · Visa · 1-2 hours" selected={method === "gift"} onSelect={setMethod} icon={Gift} />
              </div>
            </div>
            <div className="ha-card p-5">
              <Caps className="text-[var(--ink-3)] block mb-3">Step 3 · Confirm</Caps>
              <div className="space-y-2 text-[13px] mb-4">
                <KV label="Redeem" value={amountCents > 0 ? fmt.sc(amountCents, { precise: true }) + " SC" : "—"} />
                <KV label="Method" value={method} mute />
                <KV label="Processing time" value={method === "paypal" || method === "card" ? "Instant" : "3-5 days"} mute />
```

## Page 52

```text
                <KV label="Fee" value={method === "card" ? fmt.usd(Math.floor(amountCents * 0.01)) : "$0.00"} mute />
                <Rule className="my-2" />
                <KV label="You receive" value={fmt.usd(method === "card" ? Math.floor(amountCents * 0.99) : amountCents)} accent="amber" />
              </div>
              <button onClick={submitRedemption} disabled={!canSubmit} className="ha-btn ha-btn-amber ha-btn-lg w-full">
                <ArrowDownUp size={16} /> {canSubmit ? "Submit redemption · " + fmt.usd(amountCents) : "Complete steps above"}
              </button>
              <p className="ha-mono text-[10px] text-[var(--ink-3)] mt-3 text-center">
                Redemption requests are reviewed within 24 hours. Funds released after approval.
              </p>
            </div>
          </div>
          {/* Right: status + history */}
          <aside className="space-y-4">
            <div className="ha-card p-5">
              <Caps className="text-[var(--ink-3)] block mb-3">Recent redemptions</Caps>
              <div className="space-y-3">
                <RedemptionRow amount={5000} method="PayPal" status="paid" date="2026-04-12T10:00:00Z" />
                <RedemptionRow amount={10000} method="ACH" status="paid" date="2026-03-28T14:30:00Z" />
                <RedemptionRow amount={2500} method="Gift card" status="paid" date="2026-03-12T09:15:00Z" />
              </div>
              <button className="ha-mono text-[11px] text-[var(--ink-3)] underline mt-3">view all redemptions →</button>
            </div>
            <div className="ha-card p-5">
              <Caps className="text-[var(--ink-3)] block mb-2">About redemption</Caps>
              <ul className="text-[12px] text-[var(--ink-2)] space-y-2 list-disc pl-4">
                <li>1 Sweeps Coin = $1 USD prize value</li>
                <li>Identity verification required for $100+ (AML rule)</li>
                <li>Redemptions audited and tax-documented (Form 1099-MISC for $600+ annual)</li>
                <li>State eligibility verified at every redemption</li>
                <li>Responsible-play limits apply to redemption frequency</li>
              </ul>
            </div>
          </aside>
        </div>
      )}
    </div>
  );
}
function EligibilityCard({ icon: Icon, label, value, status, sub }) {
  const bg = status === "ok" ? "var(--yes-soft)" : status === "warn" ? "var(--amber-soft)" : "var(--no-soft)";
  const color = status === "ok" ? "var(--yes-deep)" : status === "warn" ? "var(--amber-deep)" : "var(--no-deep)";
  return (
    <div className="ha-card p-4">
      <div className="flex items-center gap-2 mb-2">
```

## Page 53

```text
        <div className="w-8 h-8 rounded flex items-center justify-center" style={{ background: bg }}>
          <Icon size={14} style={{ color }} />
        </div>
        <Caps className="text-[var(--ink-3)]">{label}</Caps>
      </div>
      <Mono className="text-[14px] font-medium block" style={{ color }}>{value}</Mono>
      <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-0.5">{sub}</div>
    </div>
  );
}
function PayoutMethod({ id, label, sub, selected, onSelect, icon: Icon }) {
  return (
    <label className={"ha-card ha-hov p-3 flex items-center gap-3 cursor-pointer " + (selected ? "ring-2 ring-[var(--ink)]" : "")} onClick={() => onSelect(id)}>
      <input type="radio" checked={selected} onChange={() => onSelect(id)} className="accent-[var(--ink)]" />
      <Icon size={18} />
      <div className="flex-1">
        <div className="text-[13px] font-medium">{label}</div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)]">{sub}</div>
      </div>
      {selected && <Check size={16} className="text-[var(--yes-deep)]" />}
    </label>
  );
}
function RedemptionRow({ amount, method, status, date }) {
  return (
    <div className="flex items-center gap-3 text-[12px]">
      <div className="w-8 h-8 rounded bg-[var(--yes-soft)] flex items-center justify-center shrink-0">
        <Check size={14} className="text-[var(--yes-deep)]" />
      </div>
      <div className="flex-1 min-w-0">
        <div><Mono>{fmt.sc(amount)} SC</Mono> · {method}</div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.date(date)} · paid</div>
      </div>
      <Mono className="text-[12px] text-[var(--yes-deep)]">{fmt.usd(amount)}</Mono>
    </div>
  );
}
/* ============================================================================
   LEADERBOARD — ranked traders with badges and timeframe filter
   ============================================================================ */
function LeaderboardView() {
  const [timeframe, setTimeframe] = useState("30d");
  const [category, setCategory] = useState("all");
  const top3 = LEADERBOARD.slice(0, 3);
  const rest = LEADERBOARD.slice(3);
```

## Page 54

```text
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section VIII</span><span>·</span><span>the standings</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Leaderboard</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          Top traders ranked by realised P&amp;L. Resets monthly. Top 10 receive bonus SC and seasonal badges.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Filters */}
      <div className="flex flex-wrap items-center gap-2 mb-6 ha-fade ha-d-2">
        <div className="flex border border-[var(--rule)] rounded overflow-hidden">
          {["7d", "30d", "all"].map((t) => (
            <button key={t} onClick={() => setTimeframe(t)} className={"h-10 px-4 ha-mono text-[11px] " + (timeframe === t ? "bg-[var(--ink)] text-[var(--paper)]" : "")}>
              {t.toUpperCase()}
            </button>
          ))}
        </div>
        <select value={category} onChange={(e) => setCategory(e.target.value)} className="ha-input w-auto pr-8">
          <option value="all">All categories</option>
          {CATEGORIES.map((c) => <option key={c.id} value={c.id}>{c.label}</option>)}
        </select>
        <div className="ml-auto ha-mono text-[10px] text-[var(--ink-3)]">Updated {fmt.rel(new Date(Date.now() - 4 * 60 * 1000).toISOString())}</div>
      </div>
      {/* Podium for top 3 */}
      <div className="grid grid-cols-3 gap-3 mb-8 ha-fade ha-d-3">
        <PodiumCard rank={2} trader={top3[1]} height="160px" />
        <PodiumCard rank={1} trader={top3[0]} height="200px" featured />
        <PodiumCard rank={3} trader={top3[2]} height="140px" />
      </div>
      {/* Rest of leaderboard */}
      <div className="ha-card overflow-hidden ha-fade ha-d-4">
        <table className="w-full">
          <thead>
            <tr className="text-left ha-mono text-[10px] text-[var(--ink-3)] border-b border-[var(--rule)]">
              <th className="py-3 px-4 font-medium w-12">Rank</th>
              <th className="py-3 px-4 font-medium">Trader</th>
              <th className="py-3 px-4 font-medium text-right">P&amp;L</th>
              <th className="py-3 px-4 font-medium text-right hidden sm:table-cell">Win rate</th>
              <th className="py-3 px-4 font-medium text-right hidden md:table-cell">Trades</th>
            </tr>
```

## Page 55

```text
          </thead>
          <tbody>
            {rest.map((row) => (
              <tr key={row.user} className={"border-b border-[var(--rule-soft)] last:border-b-0 hover:bg-[var(--paper-2)] " + (row.isYou ? "bg-[var(--amber-soft)]" : "")}>
                <td className="py-3 px-4">
                  <Mono className="text-[16px] text-[var(--ink-2)]"><Display weight={600}>#{row.rank}</Display></Mono>
                </td>
                <td className="py-3 px-4">
                  <div className="flex items-center gap-3">
                    <div className="w-9 h-9 rounded-full flex items-center justify-center font-semibold text-[12px] shrink-0"
                      style={{ background: "var(--paper-2)", border: "1px solid var(--rule)" }}>
                      {row.user.slice(0, 2).toUpperCase()}
                    </div>
                    <div>
                      <div className="text-[13px] font-medium flex items-center gap-1">
                        @{row.user}
                        {row.isYou && <Pill tone="amber">YOU</Pill>}
                        {row.badge === "crown" && <Crown size={12} className="text-[var(--gold)]" />}
                        {row.badge === "medal" && <Medal size={12} className="text-[var(--ink-2)]" />}
                        {row.badge === "star" && <Star size={12} className="text-[var(--amber)]" />}
                      </div>
                      <div className="ha-mono text-[10px] text-[var(--ink-3)]">tier · {row.rank <= 10 ? "diamond" : row.rank <= 50 ? "gold" : "silver"}</div>
                    </div>
                  </div>
                </td>
                <td className="py-3 px-4 text-right">
                  <Mono className={"text-[14px] " + (row.pnlCents >= 0 ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>
                    {row.pnlCents >= 0 ? "+" : ""}{fmt.sc(row.pnlCents)} SC
                  </Mono>
                </td>
                <td className="py-3 px-4 text-right ha-mono text-[13px] hidden sm:table-cell">{row.winRate}%</td>
                <td className="py-3 px-4 text-right ha-mono text-[13px] text-[var(--ink-3)] hidden md:table-cell">{row.trades}</td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
      {/* Footer */}
      <div className="mt-8 grid grid-cols-1 md:grid-cols-3 gap-4 ha-fade ha-d-5">
        <div className="ha-card p-4">
          <Caps className="text-[var(--ink-3)] block">Your rank</Caps>
          <Mono className="text-[28px] mt-1"><Display weight={700}>#10</Display></Mono>
          <span className="ha-mono text-[10px] text-[var(--yes-deep)]">▲ +3 this week</span>
        </div>
        <div className="ha-card p-4">
          <Caps className="text-[var(--ink-3)] block">Next reward at</Caps>
```

## Page 56

```text
          <Mono className="text-[28px] mt-1"><Display weight={700}>#5</Display></Mono>
          <span className="ha-mono text-[10px] text-[var(--ink-3)]">+100 SC bonus on Sunday</span>
        </div>
        <div className="ha-card p-4">
          <Caps className="text-[var(--ink-3)] block">Total traders ranked</Caps>
          <Mono className="text-[28px] mt-1"><Display weight={700}>14,217</Display></Mono>
          <span className="ha-mono text-[10px] text-[var(--ink-3)]">top 0.07% in your timeframe</span>
        </div>
      </div>
    </div>
  );
}
function PodiumCard({ rank, trader, height, featured }) {
  const colors = { 1: "var(--gold)", 2: "var(--ink-3)", 3: "#a16207" };
  return (
    <div className="flex flex-col items-center justify-end">
      <div className="text-center mb-2">
        <div className="w-14 h-14 rounded-full flex items-center justify-center font-bold text-[14px] mx-auto mb-2"
          style={{ background: "var(--paper)", border: "2px solid " + colors[rank], boxShadow: featured ? "0 8px 32px -8px rgba(0,0,0,.2)" : undefined }}>
          {trader.user.slice(0, 2).toUpperCase()}
        </div>
        <div className="text-[12px] font-semibold flex items-center justify-center gap-1">
          @{trader.user}
          {rank === 1 && <Crown size={12} className="text-[var(--gold)]" />}
        </div>
        <Mono className="text-[16px] text-[var(--yes-deep)] block"><Display weight={600}>+{fmt.sc(trader.pnlCents)} SC</Display></Mono>
        <div className="ha-mono text-[10px] text-[var(--ink-3)]">{trader.winRate}% wins · {trader.trades} trades</div>
      </div>
      <div className="w-full ha-card flex items-center justify-center" style={{ height, background: rank === 1 ? "var(--gold-soft)" : "var(--paper-2)" }}>
        <Display weight={700} className="text-[48px]">#{rank}</Display>
      </div>
    </div>
  );
}
/* ============================================================================
   PROFILE — stats, badges, activity feed, referral
   ============================================================================ */
function ProfileView({ onNavigate }) {
  const [tab, setTab] = useState("activity");
  const badges = [
    { id: "first-trade", icon: Zap, label: "First Trade", earned: true, ts: "2026-04-01T10:00:00Z" },
    { id: "winning-streak", icon: Flame, label: "5-Win Streak", earned: true, ts: "2026-04-12T15:00:00Z" },
    { id: "diamond-hands", icon: Diamond, label: "Diamond Hands", earned: true, ts: "2026-04-18T11:00:00Z" },
    { id: "top-100", icon: Trophy, label: "Top 100", earned: true, ts: "2026-04-22T20:11:00Z" },
    { id: "100k-volume", icon: Target, label: "100k Volume", earned: false, sub: "84% complete" },
    { id: "year-of-arena", icon: Crown, label: "Year of Arena", earned: false, sub: "9 months" },
```

## Page 57

```text
  ];
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section IX</span><span>·</span><span>your profile</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Profile</Display>
      </div>
      <Rule className="mb-6" double />
      {/* Profile header */}
      <div className="ha-card p-6 mb-6 ha-fade ha-d-2 flex flex-col sm:flex-row items-start gap-5">
        <div className="w-24 h-24 rounded-full flex items-center justify-center text-[28px] font-bold shrink-0"
          style={{ background: "linear-gradient(135deg, #c2410c, #7c2d12)", color: "white" }}>
          MN
        </div>
        <div className="flex-1">
          <div className="flex items-center gap-2 mb-1 flex-wrap">
            <Display weight={700} className="text-[28px]">@montana</Display>
            <BadgeCheck size={18} className="text-[var(--amber)]" />
            <Pill tone="amber">DIAMOND TIER</Pill>
          </div>
          <div className="ha-mono text-[12px] text-[var(--ink-3)] mb-3">Member since April 2026 · 47 trades · California</div>
          <p className="text-[14px] text-[var(--ink-2)] max-w-prose">"Looking for asymmetric bets on AI, infrastructure, and the structural changes downstream of both. Long-form research, then short-form conviction."</p>
          <div className="flex gap-2 mt-4">
            <button onClick={() => onNavigate("settings")} className="ha-btn ha-btn-sm">Edit profile</button>
            <button className="ha-btn ha-btn-sm ha-btn-ghost border border-[var(--rule)]"><Share2 size={12} /> Share</button>
            <button className="ha-btn ha-btn-sm ha-btn-ghost border border-[var(--rule)]"><Copy size={12} /> Copy link</button>
          </div>
        </div>
      </div>
      {/* Stats grid */}
      <div className="grid grid-cols-2 sm:grid-cols-4 gap-3 mb-6 ha-fade ha-d-3">
        <ProfileStat label="Total P&L" value="+28,400 SC" sub="↑ 12.4% MoM" accent="yes" />
        <ProfileStat label="Win rate" value="51.2%" sub="48 / 94 trades" />
        <ProfileStat label="Ranked" value="#10" sub="of 14,217" />
        <ProfileStat label="Followers" value="142" sub="↑ 18 this week" />
      </div>
      {/* Badges */}
      <section className="mb-6 ha-fade ha-d-4">
        <SectionHeader kicker="Earned" title="Badges & Achievements" />
        <div className="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3 mt-4">
          {badges.map((b) => {
            const Icon = b.icon;
```

## Page 58

```text
            return (
              <div key={b.id} className={"ha-card p-4 text-center " + (b.earned ? "" : "opacity-40")}>
                <div className="w-12 h-12 rounded-full mx-auto flex items-center justify-center mb-2"
                  style={{ background: b.earned ? "var(--amber-soft)" : "var(--paper-2)" }}>
                  <Icon size={20} className={b.earned ? "text-[var(--amber)]" : "text-[var(--ink-3)]"} />
                </div>
                <div className="text-[12px] font-medium">{b.label}</div>
                <div className="ha-mono text-[9px] text-[var(--ink-3)] mt-0.5">{b.earned ? fmt.rel(b.ts) : b.sub}</div>
              </div>
            );
          })}
        </div>
      </section>
      {/* Activity tabs */}
      <div className="border-b border-[var(--rule)] flex gap-1 ha-fade ha-d-5">
        {[{ id: "activity", label: "Recent Activity" }, { id: "positions", label: "Public Positions" }, { id: "following", label: "Following" }].map((t) => (
          <button key={t.id} onClick={() => setTab(t.id)} className={"px-4 h-11 text-[13px] font-medium " + (tab === t.id ? "border-b-2 border-[var(--ink)] text-[var(--ink)]" : "text-[var(--ink-3)]")}>
            {t.label}
          </button>
        ))}
      </div>
      <div className="mt-5">
        {tab === "activity" && (
          <div className="ha-card overflow-hidden">
            <div className="divide-y divide-[var(--rule-soft)]">
              {ACTIVITY.slice(0, 5).map((a) => {
                const m = marketById(a.marketId);
                if (!m) return null;
                return (
                  <div key={a.id} className="p-4 flex items-center gap-3">
                    <MarketArt name={m.image} size={36} />
                    <div className="flex-1 min-w-0">
                      <div className="text-[12px]">
                        <span className="font-medium">You</span>
                        <span className="text-[var(--ink-3)]"> {a.action.toLowerCase()}ed </span>
                        <span className={"ha-mono " + (a.side === "YES" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>{a.side}</span>
                        <span className="text-[var(--ink-3)]"> on </span>
                      </div>
                      <div className="text-[11px] text-[var(--ink-3)] ha-line-clamp-2">{m.question}</div>
                    </div>
                    <div className="text-right shrink-0">
                      <Mono className="text-[13px]">{fmt.sc(a.amount)} SC</Mono>
                      <div className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.rel(a.ts)}</div>
                    </div>
                  </div>
                );
```

## Page 59

```text
              })}
            </div>
          </div>
        )}
        {tab === "positions" && (
          <div className="space-y-3">
            {POSITIONS.slice(0, 3).map((p) => {
              const m = marketById(p.marketId);
              if (!m) return null;
              return (
                <div key={p.id} className="ha-card p-4 flex items-center gap-3">
                  <MarketArt name={m.image} size={44} />
                  <div className="flex-1 min-w-0">
                    <Pill tone={p.side === "YES" ? "yes" : "no"}>{p.side}</Pill>
                    <div className="text-[13px] font-medium mt-1 ha-line-clamp-2">{m.question}</div>
                  </div>
                  <Mono className="text-[14px]">{fmt.sc(p.stakeCents)} SC</Mono>
                </div>
              );
            })}
          </div>
        )}
        {tab === "following" && (
          <div className="ha-card p-12 text-center">
            <Users size={32} className="mx-auto text-[var(--ink-3)] mb-3" />
            <Display weight={600} className="text-[16px] block">Not following anyone yet</Display>
            <p className="text-[12px] text-[var(--ink-3)] mt-1">Browse the leaderboard to find traders to follow.</p>
          </div>
        )}
      </div>
    </div>
  );
}
function ProfileStat({ label, value, sub, accent }) {
  const color = accent === "yes" ? "text-[var(--yes-deep)]" : "";
  return (
    <div className="ha-card p-4">
      <Caps className="text-[var(--ink-3)] block mb-2">{label}</Caps>
      <Mono className={"text-[22px] sm:text-[26px] leading-none block " + color}><Display weight={600}>{value}</Display></Mono>
      <span className="ha-mono text-[10px] text-[var(--ink-3)] block mt-1.5">{sub}</span>
    </div>
  );
}
/* ============================================================================
   AGENT — AI assistant. Powered by `google/gemma-4-26b-a4b-it` via Vercel AI SDK.
   streamText() with tool-calling: search_markets, get_market, get_user_positions,
```

## Page 60

```text
   recommend_trade. Mimics agentic flow with tool-call cards inline in stream.
   ============================================================================ */
function AgentView({ onOpenMarket }) {
  const [messages, setMessages] = useState([
    {
      id: "m0",
      role: "agent",
      content: "Hi Montana. I'm the Arena agent — I read every market on Huggy Arena and can help you find ones that match your view. Ask me anything: a thesis you want to bet on, a category you want to explore, or a position you're considering.",
      ts: new Date(Date.now() - 60_000).toISOString(),
    },
  ]);
  const [input, setInput] = useState("");
  const [streaming, setStreaming] = useState(false);
  const [streamBuffer, setStreamBuffer] = useState("");
  const messagesEndRef = useRef(null);
  useEffect(() => { messagesEndRef.current?.scrollIntoView({ behavior: "smooth" }); }, [messages, streamBuffer]);
  const suggestedPrompts = [
    "Find me markets where retail is wrong on AI",
    "What's overpriced right now?",
    "Markets resolving in the next 30 days",
    "Bullish on Hugging Face — what's available?",
    "Build me a contrarian portfolio with 250 SC",
  ];
  const send = (text) => {
    if (!text.trim() || streaming) return;
    const userMsg = { id: "u" + Date.now(), role: "user", content: text, ts: new Date().toISOString() };
    setMessages((m) => [...m, userMsg]);
    setInput("");
    setStreaming(true);
    setStreamBuffer("");
    // Simulate streaming response from `google/gemma-4-26b-a4b-it`
    simulateStream(text, (chunk) => setStreamBuffer((b) => b + chunk),
      (final) => {
        setMessages((m) => [...m, final]);
        setStreamBuffer("");
        setStreaming(false);
      }
    );
  };
  return (
    <div className="pt-6 pb-12 flex flex-col" style={{ minHeight: "calc(100vh - 200px)" }}>
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section X</span><span>·</span><span>AI agent</span>
```

## Page 61

```text
        </div>
        <div className="flex items-baseline gap-3 flex-wrap">
          <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Arena Agent</Display>
          <div className="flex items-center gap-2">
            <span className="ha-pulse w-2 h-2 rounded-full bg-[var(--yes)]" />
            <Mono className="text-[11px] text-[var(--ink-3)]">live · gemma-4-26b-a4b-it</Mono>
          </div>
        </div>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          A research assistant trained on every market, news source, and on-chain trade on Huggy Arena. Streams answers, calls tools, recommends positions. Never executes trades without your confirmation.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Chat area */}
      <div className="ha-card overflow-hidden flex flex-col ha-fade ha-d-2" style={{ minHeight: 540 }}>
        {/* Agent header strip */}
        <div className="bg-[var(--ink)] text-[var(--paper)] px-4 py-3 flex items-center gap-3">
          <div className="w-9 h-9 rounded-full flex items-center justify-center"
            style={{ background: "linear-gradient(135deg, #fbbf24, #c2410c)" }}>
            <Bot size={16} className="text-white" />
          </div>
          <div className="flex-1">
            <div className="text-[13px] font-medium">Arena Agent</div>
            <div className="ha-mono text-[10px] opacity-70 flex items-center gap-2">
              <span>via Vercel AI SDK · streamText()</span>
              <span>·</span>
              <span>{streaming ? "thinking…" : "ready"}</span>
            </div>
          </div>
          <button className="h-8 px-3 ha-mono text-[10px] border border-white/20 rounded hover:bg-white/10">
            <RefreshCw size={11} className="inline mr-1" /> new chat
          </button>
        </div>
        {/* Messages */}
        <div className="flex-1 overflow-y-auto p-4 space-y-4 bg-[var(--paper)]" style={{ maxHeight: 560 }}>
          {messages.map((m) => <MessageBubble key={m.id} message={m} onOpenMarket={onOpenMarket} />)}
          {streaming && (
            <MessageBubble
              message={{ id: "streaming", role: "agent", content: streamBuffer, ts: new Date().toISOString(), streaming: true }}
              onOpenMarket={onOpenMarket}
            />
          )}
          <div ref={messagesEndRef} />
        </div>
```

## Page 62

```text
        {/* Composer */}
        <div className="border-t border-[var(--rule)] p-3 bg-[var(--paper)]">
          {messages.length === 1 && !streaming && (
            <div className="flex flex-wrap gap-2 mb-3">
              {suggestedPrompts.map((p) => (
                <button key={p} onClick={() => send(p)} className="ha-chip ha-hov text-left">
                  <Sparkles size={11} className="text-[var(--amber)]" /> {p}
                </button>
              ))}
            </div>
          )}
          <div className="flex gap-2 items-end">
            <textarea
              value={input}
              onChange={(e) => setInput(e.target.value)}
              onKeyDown={(e) => { if (e.key === "Enter" && !e.shiftKey) { e.preventDefault(); send(input); } }}
              placeholder="Ask the agent anything…"
              rows={1}
              className="ha-input flex-1 resize-none min-h-[44px] max-h-[120px] py-3"
              style={{ height: "auto" }}
            />
            <button onClick={() => send(input)} disabled={!input.trim() || streaming} className="ha-btn ha-btn-amber h-11 px-4">
              {streaming ? <Loader2 size={16} className="animate-spin" /> : <Send size={16} />}
            </button>
          </div>
          <div className="ha-mono text-[9px] text-[var(--ink-3)] mt-2 flex items-center gap-2">
            <Shield size={9} /> Agent has read-only access to your portfolio. Will never execute trades without explicit confirmation.
          </div>
        </div>
      </div>
      {/* Caveats */}
      <div className="grid grid-cols-1 md:grid-cols-3 gap-3 mt-6 ha-fade ha-d-4">
        <AgentNote icon={Zap} title="Streaming responses" body="Tokens stream in real-time via Vercel AI SDK and the streamText primitive against gemma-4-26b-a4b-it." />
        <AgentNote icon={Layers} title="Tool calls visible" body="The agent calls search_markets, get_market, and recommend_trade. You see each call inline." />
        <AgentNote icon={ShieldAlert} title="Not financial advice" body="The agent makes probabilistic suggestions based on prices. It is not a registered advisor. Always do your own research." />
      </div>
      {/* Under the hood */}
      <div className="mt-6 ha-fade ha-d-5">
        <SectionHeader kicker="Under the hood" title="How the agent works" />
        <div className="ha-card mt-4 overflow-hidden">
          <div className="bg-[var(--ink)] text-[var(--paper)] px-4 py-2 flex items-center gap-2">
            <Mono className="text-[10px] opacity-70">agent.ts · server</Mono>
            <span className="ml-auto ha-mono text-[10px] opacity-50">typescript</span>
          </div>
          <pre className="ha-mono text-[12px] leading-relaxed p-4 overflow-x-auto" style={{ background: "#1c1917", color: "#f5f1e8" }}>
```

## Page 63

```text
{`import { streamText, tool } from 'ai';
import { z } from 'zod';
const result = streamText({
  model: 'google/gemma-4-26b-a4b-it',
  system: \`You are the Arena Agent. You help users find prediction
    markets that match their view, identify mispriced markets, and
    explain market mechanics. You never execute trades.\`,
  prompt: userMessage,
  tools: {
    search_markets: tool({
      description: 'Search markets by topic or thesis',
      parameters: z.object({ query: z.string() }),
      execute: async ({ query }) => await db.markets.search(query),
    }),
    recommend_trade: tool({
      description: 'Suggest a side and conviction for a market',
      parameters: z.object({
        marketId: z.string(),
        side: z.enum(['YES', 'NO']),
        conviction: z.number().min(1).max(5),
        thesis: z.string(),
      }),
      execute: async (args) => args, // pass-through to UI
    }),
  },
});
return result.toDataStreamResponse();`}
          </pre>
        </div>
      </div>
    </div>
  );
}
function MessageBubble({ message, onOpenMarket }) {
  const isUser = message.role === "user";
  return (
    <div className={"flex gap-3 " + (isUser ? "flex-row-reverse" : "")}>
      <div className="w-8 h-8 rounded-full flex items-center justify-center shrink-0"
        style={{ background: isUser ? "var(--paper-2)" : "linear-gradient(135deg, #fbbf24, #c2410c)" }}>
        {isUser ? <User size={14} /> : <Bot size={14} className="text-white" />}
      </div>
      <div className={"max-w-[80%] " + (isUser ? "text-right" : "")}>
        <div className={"ha-mono text-[10px] text-[var(--ink-3)] mb-1 " + (isUser ? "text-right" : "")}>
          {isUser ? "you" : "agent"} · {fmt.rel(message.ts)}
```

## Page 64

```text
        </div>
        <div className={"inline-block p-3 rounded-lg text-[13px] leading-relaxed text-left " + (isUser ? "bg-[var(--ink)] text-[var(--paper)]" : "bg-[var(--paper-2)]")}>
          {/* Render content with tool call cards inline */}
          {renderAgentContent(message.content, onOpenMarket)}
          {message.streaming && <span className="inline-block w-1.5 h-3 bg-[var(--amber)] ml-1 ha-pulse" />}
        </div>
        {/* Tool call cards rendered below the bubble */}
        {message.toolCalls && (
          <div className="mt-2 space-y-2">
            {message.toolCalls.map((tc, i) => <ToolCallCard key={i} call={tc} onOpenMarket={onOpenMarket} />)}
          </div>
        )}
      </div>
    </div>
  );
}
function renderAgentContent(text, onOpenMarket) {
  // Render plain text with light parsing for clarity
  return text.split("\n").map((line, i) => (<div key={i}>{line || <br />}</div>));
}
function ToolCallCard({ call, onOpenMarket }) {
  if (call.tool === "search_markets") {
    return (
      <div className="ha-card p-3 bg-[var(--paper)]">
        <div className="flex items-center gap-2 mb-2">
          <Layers size={12} className="text-[var(--amber)]" />
          <Mono className="text-[11px] text-[var(--ink-3)]">tool: <span className="text-[var(--ink)]">search_markets</span></Mono>
          <Mono className="text-[10px] text-[var(--ink-3)] ml-auto">{call.duration}ms</Mono>
        </div>
        <div className="ha-mono text-[10px] text-[var(--ink-3)] mb-2">query: "{call.query}"</div>
        <div className="space-y-1.5">
          {call.results.map((mId) => {
            const m = marketById(mId);
            if (!m) return null;
            return (
              <button key={mId} onClick={() => onOpenMarket(mId)} className="w-full text-left flex items-center gap-2 p-2 hover:bg-[var(--paper-2)] rounded">
                <MarketArt name={m.image} size={28} />
                <div className="flex-1 min-w-0">
                  <div className="text-[12px] font-medium ha-line-clamp-2">{m.question}</div>
                  <div className="ha-mono text-[10px] text-[var(--ink-3)]">{marketProb(m)}% · ${m.volume24h.toLocaleString()} 24h</div>
                </div>
                <ChevronRight size={12} className="text-[var(--ink-3)]" />
              </button>
            );
          })}
```

## Page 65

```text
        </div>
      </div>
    );
  }
  if (call.tool === "recommend_trade") {
    const m = marketById(call.marketId);
    if (!m) return null;
    return (
      <div className="ha-card p-3 bg-[var(--paper)]" style={{ borderColor: "var(--amber)" }}>
        <div className="flex items-center gap-2 mb-2">
          <Target size={12} className="text-[var(--amber)]" />
          <Mono className="text-[11px] text-[var(--ink-3)]">tool: <span className="text-[var(--ink)]">recommend_trade</span></Mono>
          <Pill tone="amber">RECOMMENDED</Pill>
        </div>
        <button onClick={() => onOpenMarket(m.id)} className="w-full text-left flex items-start gap-3">
          <MarketArt name={m.image} size={44} />
          <div className="flex-1 min-w-0">
            <div className="text-[13px] font-medium ha-line-clamp-2">{m.question}</div>
            <div className="flex items-center gap-2 mt-1">
              <Pill tone={call.side === "YES" ? "yes" : "no"}>{call.side}</Pill>
              <Mono className="text-[10px] text-[var(--ink-3)]">@ {call.side === "YES" ? marketProb(m) : 100 - marketProb(m)}¢</Mono>
              <Mono className="text-[10px] text-[var(--amber)]">conviction {call.conviction}/5</Mono>
            </div>
            <p className="text-[11px] text-[var(--ink-2)] mt-1 ha-display-italic">{call.thesis}</p>
          </div>
        </button>
      </div>
    );
  }
  return null;
}
function AgentNote({ icon: Icon, title, body }) {
  return (
    <div className="ha-card p-4">
      <div className="flex items-center gap-2 mb-2">
        <Icon size={14} className="text-[var(--amber)]" />
        <Caps className="text-[var(--ink-3)]">{title}</Caps>
      </div>
      <p className="text-[12px] text-[var(--ink-2)] leading-relaxed">{body}</p>
    </div>
  );
}
/* simulated agent response with tool calls — mimics AI SDK streaming */
function simulateStream(userText, onChunk, onComplete) {
  const lower = userText.toLowerCase();
```

## Page 66

```text
  let response = "";
  let toolCalls = [];
  if (lower.includes("contrarian") || lower.includes("retail is wrong")) {
    response = `Looked at three markets where retail consensus diverges from sharper traders. Here's what stands out:
The Anthropic IPO market is pricing at 17% YES for a 2026 S-1 filing — that's likely too low. Sharp traders are accumulating YES under 20¢ on the view that any tier-1 AI lab going public in '26 is a coin-flip, not a tail event.
The recession market is pricing at 32% YES — but the swing has been one-way since rates held last week. Watch for mean reversion.
Want me to recommend specific entries?`;
    toolCalls = [{ tool: "search_markets", query: "contrarian opportunities high disagreement", results: ["m_anthropic_ipo", "m_recession_2026", "m_apple_vrai"], duration: 142 }];
  } else if (lower.includes("overpriced") || lower.includes("rich")) {
    response = `Three markets I think are overpriced right now:
GPT-5 at 76% — fair value is probably closer to 65%. Eight months left and no concrete signal from OpenAI.
HF 5M models at 83% — the trend supports it, but the market has front-run an outcome that's still 8 months away. Mean revert lower if no acceleration.
Climate +1.5C at 68% — Copernicus baselines suggest the actual probability is closer to 55%.
I'd consider NO on any of these as fade trades.`;
    toolCalls = [
      { tool: "search_markets", query: "overpriced markets implied prob too high", results: ["m_gpt5_2026", "m_huggy_5m", "m_climate_15c"], duration: 198 },
      { tool: "recommend_trade", marketId: "m_gpt5_2026", side: "NO", conviction: 3, thesis: "Market is pricing aggressive timeline. 76% with 8 months left feels rich given no concrete signal." },
    ];
  } else if (lower.includes("resolving") || lower.includes("next 30 days")) {
    response = `Markets resolving within 30 days:
Warriors NBA Finals (27% YES) — resolves May 30. They've got a tough West to navigate.
House Dems 2026 doesn't resolve until November but the next major catalyst is filing deadlines this month.
The Warriors market is the most actionable — if you have a view on the West playoffs, this is an asymmetric bet.`;
    toolCalls = [{ tool: "search_markets", query: "closing within 30 days", results: ["m_warriors_2026"], duration: 89 }];
  } else if (lower.includes("hugging") || lower.includes("huggingface") || lower.includes("hf")) {
    response = `Two markets directly involve Hugging Face:
HF 5M models by EOY (83% YES) — this is pricing for a structural growth trend. Current count is ~4.2M; growing 200k/month. Math works.
Llama 5 by Sept 2026 (41% YES) — adjacent because Llama models are typically released on HF first.
If you're long HF as an ecosystem bet, the first one is the cleanest expression.`;
    toolCalls = [{ tool: "search_markets", query: "huggingface ecosystem markets", results: ["m_huggy_5m", "m_llama5"], duration: 134 }];
  } else if (lower.includes("250") || lower.includes("portfolio")) {
    response = `Here's a contrarian 250 SC portfolio across three uncorrelated bets:
100 SC NO on GPT-5 by 2026 (current 76%) — fade the consensus
75 SC YES on Anthropic IPO (current 17%) — buy what the market underrates
75 SC NO on Climate +1.5C (current 68%) — Copernicus signals lower
```

## Page 67

```text
Expected value: 287 SC if 2 of 3 hit. Total downside: 250 SC. Time horizon: ~6 months.`;
    toolCalls = [
      { tool: "recommend_trade", marketId: "m_gpt5_2026", side: "NO", conviction: 3, thesis: "Fade consensus. 76% leaves limited upside, large fall if OpenAI is silent through Q3." },
      { tool: "recommend_trade", marketId: "m_anthropic_ipo", side: "YES", conviction: 4, thesis: "Tier-1 lab IPO in '26 is a coin flip. 17% prices a tail outcome, not the base case." },
      { tool: "recommend_trade", marketId: "m_climate_15c", side: "NO", conviction: 2, thesis: "Copernicus suggests actual prob ~55%. Market is overweight the 2024 anomaly." },
    ];
  } else {
    response = `Good question. Let me look at the data and come back with specifics.
Could you narrow it down? For instance — are you looking for high-volume markets, ones with strong consensus you want to fade, ones closing soon, or specific categories like AI, politics, sports?
You can also try one of the suggested prompts above. I'll show my work as I go: every market I look at, every probability I check, all visible.`;
  }
  // Stream character by character (chunked for performance)
  const tokens = response.split(/(\s+)/);
  let i = 0;
  const next = () => {
    if (i >= tokens.length) {
      onComplete({
        id: "agent" + Date.now(),
        role: "agent",
        content: response,
        ts: new Date().toISOString(),
        toolCalls,
      });
      return;
    }
    onChunk(tokens[i]);
    i++;
    setTimeout(next, 22 + Math.random() * 38);
  };
  setTimeout(next, 280);
}
/* ============================================================================
   SETTINGS — account, notifications, privacy, compliance, responsible play
   ============================================================================ */
function SettingsView({ onNavigate, pushToast }) {
  const [section, setSection] = useState("account");
  const sections = [
    { id: "account", label: "Account", icon: User },
    { id: "notifications", label: "Notifications", icon: Bell },
    { id: "privacy", label: "Privacy & Display", icon: Eye },
    { id: "compliance", label: "Compliance & State", icon: Shield },
    { id: "limits", label: "Responsible Play", icon: ShieldCheck },
    { id: "session", label: "Session", icon: LogOut },
  ];
```

## Page 68

```text
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section XI</span><span>·</span><span>account &amp; controls</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Settings</Display>
      </div>
      <Rule className="mb-6" double />
      <div className="grid grid-cols-1 md:grid-cols-4 gap-6">
        {/* Sidebar */}
        <aside className="ha-fade ha-d-2">
          <div className="ha-card overflow-hidden">
            {sections.map((s) => {
              const Icon = s.icon;
              return (
                <button
                  key={s.id}
                  onClick={() => setSection(s.id)}
                  className={"w-full flex items-center gap-3 p-3 text-left border-b border-[var(--rule-soft)] last:border-b-0 " +
                    (section === s.id ? "bg-[var(--paper-2)] border-l-2 border-l-[var(--ink)]" : "hover:bg-[var(--paper-2)]")}
                >
                  <Icon size={15} />
                  <span className="text-[13px] font-medium">{s.label}</span>
                </button>
              );
            })}
          </div>
        </aside>
        {/* Content */}
        <div className="md:col-span-3 ha-fade ha-d-3">
          {section === "account" && (
            <SettingsBlock title="Account" sub="Manage your profile and contact details">
              <SettingRow label="Email" value="montana@huggyarena.xyz" action="Change" />
              <SettingRow label="Username" value="@montana" action="Change" />
              <SettingRow label="Display name" value="Montana" action="Change" />
              <SettingRow label="Password" value="••••••••" action="Update" />
              <SettingRow label="Two-factor auth" value={<Pill tone="yes">Enabled</Pill>} action="Configure" />
              <SettingRow label="Connected accounts" value="Apple · Google" action="Manage" />
            </SettingsBlock>
          )}
          {section === "notifications" && (
            <SettingsBlock title="Notifications" sub="Choose what we send and where">
              <SettingToggle label="Position resolved" sub="Win/loss notifications for closed trades" defaultOn />
              <SettingToggle label="Price alerts" sub="When markets you watch cross thresholds" defaultOn />
              <SettingToggle label="Market open / close" sub="Reminders for events you've subscribed to" defaultOn />
```

## Page 69

```text
              <SettingToggle label="Daily summary" sub="Morning digest of your portfolio · 9 AM local" defaultOn={false} />
              <SettingToggle label="Promotional emails" sub="Bonuses, weekly bonuses, special events" defaultOn={false} />
              <SettingToggle label="Push notifications" sub="On mobile devices" defaultOn />
              <SettingToggle label="SMS notifications" sub="Critical alerts only · standard rates apply" defaultOn={false} />
            </SettingsBlock>
          )}
          {section === "privacy" && (
            <SettingsBlock title="Privacy & Display" sub="What others see and how the app looks">
              <SettingToggle label="Public profile" sub="Show your username on leaderboard and activity" defaultOn />
              <SettingToggle label="Public positions" sub="Allow others to view your active trades" defaultOn={false} />
              <SettingToggle label="Public P&L" sub="Show realised P&L on your profile" defaultOn={false} />
              <SettingToggle label="Receive follows" sub="Allow other traders to follow your activity" defaultOn />
              <SettingRow label="Theme" value="Editorial paper" action="Change" />
              <SettingRow label="Display currency" value="USD (1 SC = $1)" action="Change" />
              <SettingRow label="Time zone" value="America/Los_Angeles" action="Change" />
            </SettingsBlock>
          )}
          {section === "compliance" && (
            <SettingsBlock title="Compliance & State" sub="Eligibility, identity verification, and tax">
              <SettingRow label="State of residence" value={<>California <Pill tone="yes">Eligible</Pill></>} action="Change (proof required)" />
              <SettingRow label="Date of birth" value="Verified · 21+" action="Update" />
              <SettingRow label="Identity (KYC)" value={<><BadgeCheck size={12} className="inline text-[var(--amber)]" /> Verified</>} action="Re-verify" />
              <SettingRow label="Tax form" value="W-9 on file" action="View" />
              <SettingRow label="Annual statement" value="2025 · ready" action="Download" />
              <SettingRow label="Account deletion" value="Permanently remove account and data" action="Delete" danger />
            </SettingsBlock>
          )}
          {section === "limits" && (
            <SettingsBlock title="Responsible Play" sub="Set hard limits to protect your wellbeing">
              <SettingRow label="Daily purchase limit" value="$100" action="Adjust" />
              <SettingRow label="Weekly purchase limit" value="$500" action="Adjust" />
              <SettingRow label="Monthly purchase limit" value="$1,500" action="Adjust" />
              <SettingRow label="Daily stake limit" value="500 SC" action="Adjust" />
              <SettingRow label="Time limit per day" value="2 hours" action="Adjust" />
              <SettingRow label="Take a break" value="Pause trading for 7-90 days" action="Set break" />
              <SettingRow label="Self-exclude" value="Permanently close access" action="Self-exclude" danger />
              <div className="ha-card p-4 bg-[var(--paper-2)] mt-4">
                <div className="flex items-center gap-2 mb-2"><ShieldAlert size={14} /><Caps>Help is available</Caps></div>
                <p className="text-[12px] text-[var(--ink-2)]">If gambling is creating problems, call <strong>1-800-GAMBLER</strong> (24/7, free, confidential). You can also reach the NCPG helpline at 1-800-522-4700 or visit ncpgambling.org.</p>
              </div>
            </SettingsBlock>
          )}
          {section === "session" && (
            <SettingsBlock title="Session" sub="Active sessions and sign out">
              <SettingRow label="Current session" value="iPhone · Safari · California" action="—" />
              <SettingRow label="Other active sessions" value="2 devices · MacBook, iPad" action="View" />
              <SettingRow label="Sign out everywhere" value="Force sign-out on all devices" action="Sign out all" />
```

## Page 70

```text
              <div className="mt-6 ha-card p-4 bg-[var(--no-soft)] flex items-center gap-3">
                <LogOut size={16} className="text-[var(--no-deep)]" />
                <div className="flex-1 text-[13px]">Sign out of this session</div>
                <button onClick={() => pushToast("Signed out", "info")} className="ha-btn ha-btn-sm" style={{ background: "var(--no)", borderColor: "var(--no)" }}>Sign out</button>
              </div>
            </SettingsBlock>
          )}
        </div>
      </div>
    </div>
  );
}
function SettingsBlock({ title, sub, children }) {
  return (
    <div className="ha-card overflow-hidden">
      <div className="p-5 border-b border-[var(--rule)]">
        <Display weight={600} className="text-[22px] block">{title}</Display>
        <p className="ha-mono text-[12px] text-[var(--ink-3)] mt-1">{sub}</p>
      </div>
      <div className="divide-y divide-[var(--rule-soft)]">{children}</div>
    </div>
  );
}
function SettingRow({ label, value, action, danger }) {
  return (
    <div className="p-4 flex items-center justify-between gap-3">
      <div className="flex-1 min-w-0">
        <div className="text-[13px] font-medium">{label}</div>
        <div className="ha-mono text-[12px] text-[var(--ink-3)] mt-0.5">{value}</div>
      </div>
      {action !== "—" && (
        <button className={"ha-mono text-[11px] underline " + (danger ? "text-[var(--no-deep)]" : "text-[var(--ink-2)] hover:text-[var(--ink)]")}>{action}</button>
      )}
    </div>
  );
}
function SettingToggle({ label, sub, defaultOn }) {
  const [on, setOn] = useState(defaultOn);
  return (
    <div className="p-4 flex items-center justify-between gap-3">
      <div className="flex-1 min-w-0">
        <div className="text-[13px] font-medium">{label}</div>
        <div className="ha-mono text-[11px] text-[var(--ink-3)] mt-0.5">{sub}</div>
      </div>
```

## Page 71

```text
      <button
        onClick={() => setOn(!on)}
        className={"relative w-11 h-6 rounded-full transition-colors " + (on ? "bg-[var(--ink)]" : "bg-[var(--paper-2)] border border-[var(--rule)]")}
      >
        <div className={"absolute top-0.5 w-5 h-5 rounded-full bg-white shadow-sm transition-all " + (on ? "left-5" : "left-0.5")} />
      </button>
    </div>
  );
}
/* ============================================================================
   HELP — Responsible Play resources and FAQ
   ============================================================================ */
function HelpView() {
  return (
    <div className="pt-6 pb-12">
      <div className="ha-fade ha-d-1 mb-6">
        <div className="flex items-baseline gap-3 ha-mono text-[10px] text-[var(--ink-3)] mb-1">
          <span>section XII</span><span>·</span><span>play responsibly</span>
        </div>
        <Display weight={700} className="text-[40px] sm:text-[56px] leading-[1]">Responsible Play</Display>
        <p className="ha-display-italic text-[16px] text-[var(--ink-2)] max-w-prose mt-2">
          Prediction markets should be fun, not destructive. If they stop being fun, stop playing. Here are the resources, limits, and signs to watch for.
        </p>
      </div>
      <Rule className="mb-6" double />
      {/* Hotline */}
      <div className="ha-card p-6 mb-6 ha-paper-card flex flex-col sm:flex-row items-start gap-5 ha-fade ha-d-2" style={{ borderColor: "var(--amber)", borderWidth: 2 }}>
        <div className="w-16 h-16 rounded-full flex items-center justify-center bg-[var(--amber-soft)] shrink-0">
          <ShieldAlert size={28} className="text-[var(--amber)]" />
        </div>
        <div className="flex-1">
          <Display weight={700} className="text-[24px] block">If gambling is hurting you, help is one call away.</Display>
          <div className="flex flex-wrap gap-3 mt-3">
            <a className="ha-btn ha-btn-amber"><Mic size={14} /> Call 1-800-GAMBLER</a>
            <a className="ha-btn ha-btn-ghost border border-[var(--rule)]"><Mail size={14} /> Text "HELP" to 800522</a>
            <a className="ha-btn ha-btn-ghost border border-[var(--rule)]"><ExternalLink size={14} /> ncpgambling.org</a>
          </div>
          <p className="ha-mono text-[11px] text-[var(--ink-3)] mt-3">24/7 · Free · Confidential · Multilingual</p>
        </div>
      </div>
      <div className="grid grid-cols-1 lg:grid-cols-2 gap-6 ha-fade ha-d-3">
        <div className="ha-card p-5">
          <Display weight={600} className="text-[18px] block mb-3">Warning signs</Display>
          <ul className="space-y-2 text-[13px] text-[var(--ink-2)]">
            <ListWarning text="Spending more than you can afford to lose" />
```

## Page 72

```text
            <ListWarning text="Chasing losses with bigger trades" />
            <ListWarning text="Lying to family or friends about play" />
            <ListWarning text="Trading when feeling stressed, depressed, or upset" />
            <ListWarning text="Borrowing money to play" />
            <ListWarning text="Neglecting work, relationships, or self-care" />
            <ListWarning text="Feeling restless or irritable when not playing" />
          </ul>
        </div>
        <div className="ha-card p-5">
          <Display weight={600} className="text-[18px] block mb-3">Tools available to you</Display>
          <ul className="space-y-2 text-[13px] text-[var(--ink-2)]">
            <ListTool icon={Wallet} title="Deposit limits" sub="Set daily, weekly, or monthly maximums" />
            <ListTool icon={Clock} title="Time limits" sub="Hard caps on session length" />
            <ListTool icon={Pause} title="Cool-off" sub="Pause trading for 1-90 days" />
            <ListTool icon={Lock} title="Self-exclude" sub="Permanently close access" />
            <ListTool icon={Eye} title="Activity summary" sub="Review your play habits monthly" />
          </ul>
        </div>
      </div>
      <Rule className="my-10" />
      <SectionHeader kicker="FAQ" title="Frequently Asked" />
      <div className="ha-card overflow-hidden mt-4 ha-fade ha-d-4">
        <div className="divide-y divide-[var(--rule-soft)]">
          <FAQRow q="What's the difference between Gold Coins and Sweeps Coins?" a="Gold Coins (GC) are entertainment-only and cannot be redeemed for cash or prizes. Sweeps Coins (SC) are received as a free promotional bonus and can be redeemed for prizes at $1 per SC, subject to verification." />
          <FAQRow q="Do I have to pay to play?" a="No. You receive Sweeps Coins as a sign-up bonus and through daily login, AMOE postcards, referrals, and special promotions. Gold Coin purchases are optional and grant additional play, with bundled SC as a promotional bonus." />
          <FAQRow q="When can I cash out?" a="Once you have a minimum of 50 SC and have completed identity verification, you can redeem any time. Payouts are typically processed within 3-5 business days for ACH, instant for PayPal." />
          <FAQRow q="Why is my state restricted?" a="State sweepstakes laws vary. Washington and Idaho exclude this type of promotion entirely; Nevada, Michigan, New York, Louisiana, and Connecticut restrict prize redemption. We follow state law strictly." />
          <FAQRow q="What if a market resolves incorrectly?" a="Any user may challenge a resolution within 24 hours by posting a 10 SC bond. The Arena Council reviews disputes; successful challenges return the bond plus a 5 SC reward." />
          <FAQRow q="What fees do you charge?" a="Protocol fee is 2% per trade, publisher fee is 1%, and there's a 2% exit fee on profit only for early exits. No deposit, withdrawal, or inactivity fees." />
        </div>
      </div>
    </div>
  );
}
function ListWarning({ text }) {
  return (<li className="flex items-start gap-2"><AlertCircle size={14} className="text-[var(--no-deep)] shrink-0 mt-0.5" />{text}</li>);
}
function ListTool({ icon: Icon, title, sub }) {
  return (
    <li className="flex items-start gap-3">
      <Icon size={16} className="text-[var(--amber)] shrink-0 mt-0.5" />
      <div>
        <div className="font-medium">{title}</div>
        <div className="ha-mono text-[11px] text-[var(--ink-3)]">{sub}</div>
```

## Page 73

```text
      </div>
    </li>
  );
}
function FAQRow({ q, a }) {
  const [open, setOpen] = useState(false);
  return (
    <div>
      <button onClick={() => setOpen(!open)} className="w-full p-4 flex items-center justify-between gap-3 text-left hover:bg-[var(--paper-2)]">
        <Display weight={500} className="text-[15px] flex-1">{q}</Display>
        {open ? <ChevronUp size={16} /> : <ChevronDown size={16} />}
      </button>
      {open && <div className="px-4 pb-4 text-[13px] text-[var(--ink-2)] leading-relaxed">{a}</div>}
    </div>
  );
}
/* ============================================================================
   ONBOARDING — welcome, age, jurisdiction, terms, welcome-bonus reveal
   ============================================================================ */
function OnboardingView({ onComplete, pushToast }) {
  const [step, setStep] = useState(0);
  const [age, setAge] = useState("");
  const [stateRes, setStateRes] = useState("");
  const [accepted, setAccepted] = useState(false);
  const isAdult = Number(age) >= 21;
  const eligibleStates = ["CA", "TX", "FL", "PA", "IL", "OH", "GA", "NC", "MA", "VA", "NJ", "AZ"]; // sample
  const blocked = stateRes && !eligibleStates.includes(stateRes.toUpperCase());
  const steps = [
    { title: "Welcome", description: "Quick set-up — under 60 seconds" },
    { title: "Age", description: "21+ required" },
    { title: "Jurisdiction", description: "State of residence" },
    { title: "Terms", description: "Sweepstakes rules" },
    { title: "Bonus", description: "Your welcome SC" },
  ];
  return (
    <div className="pt-6 pb-12 max-w-[640px] mx-auto">
      <div className="ha-fade ha-d-1 mb-6">
        <Caps className="text-[var(--amber)] block mb-1">Onboarding</Caps>
        <Display weight={700} className="text-[36px] sm:text-[48px] leading-[1]">Get started</Display>
      </div>
      {/* Progress */}
      <div className="flex items-center gap-1 mb-6 ha-fade ha-d-2">
        {steps.map((s, i) => (
          <div key={i} className="flex-1">
```

## Page 74

```text
            <div className={"h-1 rounded-full " + (i <= step ? "bg-[var(--amber)]" : "bg-[var(--paper-2)]")} />
            <div className={"ha-mono text-[9px] mt-1 " + (i <= step ? "text-[var(--ink-2)]" : "text-[var(--ink-3)]")}>0{i+1} · {s.title}</div>
          </div>
        ))}
      </div>
      <div className="ha-card p-6 sm:p-10 ha-fade ha-d-3">
        {step === 0 && (
          <div>
            <Display weight={700} className="text-[32px] leading-tight block mb-3">Welcome to the Arena.</Display>
            <p className="ha-display-italic text-[16px] text-[var(--ink-2)] mb-6">A prediction market built on the principle that markets are public arguments rendered as numbers. You bring conviction; we run the numbers.</p>
            <div className="space-y-2 mb-6">
              {[
                "Two-currency play: Gold Coins for fun, Sweeps Coins for prizes",
                "No purchase necessary — get SC free via AMOE",
                "Real markets on AI, politics, sports, crypto, and more",
                "Editorial discussion, transparent resolution, sweepstakes-eligible",
              ].map((p, i) => (
                <div key={i} className="flex items-start gap-2 text-[14px]">
                  <Check size={16} className="text-[var(--yes-deep)] shrink-0 mt-0.5" />
                  {p}
                </div>
              ))}
            </div>
            <button onClick={() => setStep(1)} className="ha-btn ha-btn-amber ha-btn-lg w-full">Begin <ArrowRight size={14} /></button>
          </div>
        )}
        {step === 1 && (
          <div>
            <Caps className="text-[var(--ink-3)] block">Step 02</Caps>
            <Display weight={700} className="text-[28px] leading-tight block mt-1 mb-3">How old are you?</Display>
            <p className="text-[14px] text-[var(--ink-2)] mb-6">Sweepstakes participation requires 21+. We verify age at signup and again at any prize redemption.</p>
            <input value={age} onChange={(e) => setAge(e.target.value.replace(/\D/g, ""))} placeholder="Your age" className="ha-input ha-mono text-[22px] text-center mb-4" />
            {age && !isAdult && <div className="bg-[var(--no-soft)] text-[var(--no-deep)] p-3 rounded text-[12px] flex items-center gap-2"><AlertCircle size={14} /> You must be 21 or older to use Huggy Arena.</div>}
            <div className="flex gap-2 mt-4">
              <button onClick={() => setStep(0)} className="ha-btn ha-btn-ghost border border-[var(--rule)] flex-1">Back</button>
              <button onClick={() => setStep(2)} disabled={!isAdult} className="ha-btn ha-btn-amber flex-[2]">Continue <ArrowRight size={14} /></button>
            </div>
          </div>
        )}
        {step === 2 && (
          <div>
            <Caps className="text-[var(--ink-3)] block">Step 03</Caps>
            <Display weight={700} className="text-[28px] leading-tight block mt-1 mb-3">Where do you live?</Display>
            <p className="text-[14px] text-[var(--ink-2)] mb-6">State eligibility determines which features are available. WA and ID are excluded from the promotion; NV, MI, NY, LA, and CT cannot redeem.</p>
            <input value={stateRes} onChange={(e) => setStateRes(e.target.value.toUpperCase().slice(0, 2))} placeholder="State (e.g. CA)" className="ha-input ha-mono text-[22px] text-center mb-4 uppercase" />
            {stateRes && blocked && <div className="bg-[var(--no-soft)] text-[var(--no-deep)] p-3 rounded text-[12px] flex items-center gap-2"><AlertCircle size={14} /> Sweepstakes promotion is not available in {stateRes}.</div>}
```

## Page 75

```text
            {stateRes && !blocked && stateRes.length === 2 && <div className="bg-[var(--yes-soft)] text-[var(--yes-deep)] p-3 rounded text-[12px] flex items-center gap-2"><Check size={14} /> {stateRes} is eligible for the full promotion.</div>}
            <div className="flex gap-2 mt-4">
              <button onClick={() => setStep(1)} className="ha-btn ha-btn-ghost border border-[var(--rule)] flex-1">Back</button>
              <button onClick={() => setStep(3)} disabled={blocked || stateRes.length !== 2} className="ha-btn ha-btn-amber flex-[2]">Continue <ArrowRight size={14} /></button>
            </div>
          </div>
        )}
        {step === 3 && (
          <div>
            <Caps className="text-[var(--ink-3)] block">Step 04</Caps>
            <Display weight={700} className="text-[28px] leading-tight block mt-1 mb-3">Read &amp; accept the terms</Display>
            <div className="ha-card p-4 bg-[var(--paper-2)] max-h-[260px] overflow-y-auto text-[12px] text-[var(--ink-2)] leading-relaxed mb-4">
              <p><strong>HUGGY ARENA SWEEPSTAKES OFFICIAL RULES.</strong> By participating in any sweepstakes promotion conducted by Huggy Arena Labs, Inc. ("Sponsor"), you agree to be bound by these rules. No purchase or payment is necessary to enter or win. A purchase will not increase your chances of winning.</p>
              <p className="mt-3"><strong>Sweeps Coins (SC)</strong> are awarded under sweepstakes rules and may be redeemed for prizes. <strong>Gold Coins (GC)</strong> are entertainment only and have no cash value.</p>
              <p className="mt-3"><strong>Eligibility:</strong> Open to U.S. residents 21 years of age or older, except residents of WA and ID. SC redemption further restricted in NV, MI, NY, LA, and CT. Identity verification required for redemption. Sponsor reserves the right to verify eligibility and disqualify any participant.</p>
              <p className="mt-3"><strong>How to enter without purchase:</strong> Send a 3"x5" hand-written postcard with your name, email, date of birth, and the words "FREE SC" to: Huggy Arena AMOE, P.O. Box 1827, Wilmington, DE 19899. Limit one entry per envelope.</p>
              <p className="mt-3"><strong>Prizes:</strong> SC may be redeemed for cash equivalents at $1 per SC, subject to verification, minimum redemption thresholds, and applicable state law. Sponsor reserves the right to modify or discontinue redemption methods.</p>
              <p className="mt-3"><strong>Responsible play:</strong> If gambling causes problems for you or your family, call 1-800-GAMBLER. You may set deposit, time, and stake limits at any time, or self-exclude permanently.</p>
            </div>
            <label className="flex items-start gap-2 cursor-pointer">
              <input type="checkbox" checked={accepted} onChange={(e) => setAccepted(e.target.checked)} className="accent-[var(--ink)] mt-1" />
              <span className="text-[13px]">I am 21+, a U.S. resident in {stateRes || "an eligible state"}, and accept the Sweepstakes Rules, Terms of Service, and Privacy Policy.</span>
            </label>
            <div className="flex gap-2 mt-4">
              <button onClick={() => setStep(2)} className="ha-btn ha-btn-ghost border border-[var(--rule)] flex-1">Back</button>
              <button onClick={() => setStep(4)} disabled={!accepted} className="ha-btn ha-btn-amber flex-[2]">Accept &amp; continue <ArrowRight size={14} /></button>
            </div>
          </div>
        )}
        {step === 4 && (
          <div className="text-center">
            <div className="w-20 h-20 rounded-full mx-auto flex items-center justify-center mb-4"
              style={{ background: "linear-gradient(135deg, #fbbf24, #c2410c)", boxShadow: "0 8px 32px -8px rgba(194,65,12,.4)" }}>
              <Sparkles size={32} className="text-white" />
            </div>
            <Caps className="text-[var(--amber)] block">Welcome to Huggy Arena</Caps>
            <Display weight={700} className="text-[32px] leading-tight block mt-2 mb-3">Your welcome bonus</Display>
            <div className="ha-card p-6 mb-6 inline-block">
              <div className="flex items-center justify-center gap-6">
                <div>
                  <Caps className="text-[var(--ink-3)] block">Gold Coins</Caps>
                  <Mono className="text-[32px]"><Display weight={700}>+10,000</Display></Mono>
                </div>
                <div className="w-px h-12 bg-[var(--rule)]" />
                <div>
                  <Caps className="text-[var(--ink-3)] block">Sweeps Coins</Caps>
                  <Mono className="text-[32px] text-[var(--amber)]"><Display weight={700}>+50</Display></Mono>
```

## Page 76

```text
                </div>
              </div>
            </div>
            <p className="ha-display-italic text-[15px] text-[var(--ink-2)] mb-6 max-w-prose mx-auto">Use them to explore markets, build positions, and find your edge. The Arena Agent is always available if you want a guided tour.</p>
            <button onClick={() => { pushToast("Welcome bonus credited", "success"); onComplete(); }} className="ha-btn ha-btn-amber ha-btn-lg w-full">Enter the Arena <ChevronsRight size={14} /></button>
          </div>
        )}
      </div>
    </div>
  );
}
function SearchOverlay({ search, setSearch, onClose, onOpenMarket }) {
  return (
    <div className="fixed inset-0 z-50 bg-[var(--paper)]" onClick={onClose}>
      <div onClick={(e) => e.stopPropagation()} className="max-w-[720px] mx-auto p-6">
        <div className="flex items-center gap-3 border-b-2 border-[var(--ink)] pb-3">
          <Search size={20} />
          <input autoFocus value={search} onChange={(e) => setSearch(e.target.value)} placeholder="Search markets, categories, traders…" className="flex-1 bg-transparent outline-none text-[20px] font-medium" />
          <button onClick={onClose} className="ha-btn-sm ha-btn-ghost ha-btn">esc</button>
        </div>
        <div className="mt-6 space-y-2">
          {MARKETS.filter((m) => !search || m.question.toLowerCase().includes(search.toLowerCase())).slice(0, 8).map((m) => (
            <button key={m.id} onClick={() => onOpenMarket(m.id)} className="w-full flex items-center gap-3 p-3 rounded hover:bg-[var(--paper-2)] text-left">
              <MarketArt name={m.image} size={40} />
              <div className="flex-1 min-w-0">
                <div className="text-[14px] font-medium ha-line-clamp-2">{m.question}</div>
                <div className="text-[11px] text-[var(--ink-3)] ha-mono">{categoryById(m.category)?.label} · {marketProb(m)}%</div>
              </div>
              <ChevronRight size={16} className="text-[var(--ink-3)]" />
            </button>
          ))}
        </div>
      </div>
    </div>
  );
}
function MoreDrawer({ onClose, onNavigate }) {
  return (
    <div className="fixed inset-0 z-50 bg-black/30" onClick={onClose}>
      <div onClick={(e) => e.stopPropagation()} className="absolute right-0 top-0 bottom-0 w-full sm:w-[380px] bg-[var(--paper)] border-l border-[var(--ink)] overflow-y-auto ha-safe-top ha-safe-bottom">
        <div className="p-5 border-b border-[var(--rule)] flex items-center justify-between">
          <Display weight={600} className="text-[18px]">Menu</Display>
          <button onClick={onClose} className="h-9 w-9 flex items-center justify-center rounded hover:bg-[var(--paper-2)]"><X size={18} /></button>
        </div>
        <div className="p-3">
```

## Page 77

```text
          {SECONDARY_VIEWS.map((v) => {
            const Icon = v.icon;
            return (
              <button key={v.id} onClick={() => onNavigate(v.id)} className="w-full flex items-center gap-3 p-3 rounded hover:bg-[var(--paper-2)]">
                <div className="h-9 w-9 flex items-center justify-center bg-[var(--paper-2)] rounded"><Icon size={16} /></div>
                <span className="text-[14px] font-medium">{v.label}</span>
                <ChevronRight size={16} className="ml-auto text-[var(--ink-3)]" />
              </button>
            );
          })}
        </div>
      </div>
    </div>
  );
}
function NotifDrawer({ onClose, onMarkAllRead }) {
  const kindIcon = {
    win: { icon: Trophy, color: "var(--yes)" },
    market: { icon: Activity, color: "var(--amber)" },
    promo: { icon: Gift, color: "var(--gold)" },
    system: { icon: ShieldAlert, color: "var(--ink-3)" },
    social: { icon: Users, color: "var(--ink-2)" },
  };
  return (
    <div className="fixed inset-0 z-50 bg-black/30" onClick={onClose}>
      <div onClick={(e) => e.stopPropagation()} className="absolute right-0 top-0 bottom-0 w-full sm:w-[400px] bg-[var(--paper)] border-l border-[var(--ink)] overflow-y-auto ha-safe-top ha-safe-bottom">
        <div className="p-5 border-b border-[var(--rule)] flex items-center justify-between">
          <Display weight={600} className="text-[18px]">Notifications</Display>
          <div className="flex items-center gap-2">
            <button onClick={onMarkAllRead} className="ha-mono text-[11px] text-[var(--ink-3)] underline">mark all read</button>
            <button onClick={onClose} className="h-9 w-9 flex items-center justify-center rounded hover:bg-[var(--paper-2)]"><X size={18} /></button>
          </div>
        </div>
        <div className="divide-y divide-[var(--rule-soft)]">
          {NOTIFICATIONS.map((n) => {
            const k = kindIcon[n.kind];
            const Icon = k.icon;
            return (
              <div key={n.id} className={"p-4 flex gap-3 " + (n.unread ? "bg-[var(--paper-2)]" : "")}>
                <div className="h-8 w-8 flex items-center justify-center rounded shrink-0" style={{ background: "var(--paper)", border: "1px solid var(--rule)" }}>
                  <Icon size={14} style={{ color: k.color }} />
                </div>
                <div className="flex-1 min-w-0">
                  <div className="text-[13px] font-medium">{n.title}</div>
                  <div className="text-[12px] text-[var(--ink-2)] mt-0.5">{n.body}</div>
                  <div className="ha-mono text-[10px] text-[var(--ink-3)] mt-1">{fmt.rel(n.ts)}</div>
```

## Page 78

```text
                </div>
                {n.unread && <div className="w-2 h-2 rounded-full bg-[var(--amber)] mt-2 shrink-0" />}
              </div>
            );
          })}
        </div>
      </div>
    </div>
  );
}
function WalletDrawer({ scBalance, gcBalance, onClose, onNavigate }) {
  return (
    <div className="fixed inset-0 z-50 bg-black/30" onClick={onClose}>
      <div onClick={(e) => e.stopPropagation()} className="absolute right-0 top-0 bottom-0 w-full sm:w-[420px] bg-[var(--paper)] border-l border-[var(--ink)] overflow-y-auto ha-safe-top ha-safe-bottom">
        <div className="p-5 border-b border-[var(--rule)] flex items-center justify-between">
          <Display weight={600} className="text-[18px]">Wallet</Display>
          <button onClick={onClose} className="h-9 w-9 flex items-center justify-center rounded hover:bg-[var(--paper-2)]"><X size={18} /></button>
        </div>
        <div className="p-5 space-y-4">
          <div className="ha-card p-4">
            <div className="flex items-center justify-between mb-2">
              <div className="flex items-center gap-2"><Coins size={16} className="text-[var(--gold)]" /><Caps>Gold Coins</Caps></div>
              <Pill tone="soft">play money</Pill>
            </div>
            <Mono className="text-[28px]"><Display weight={500}>{fmt.gc(gcBalance)}</Display></Mono>
            <div className="text-[11px] text-[var(--ink-3)] mt-1">Non-redeemable. Used for entertainment play.</div>
          </div>
          <div className="ha-card p-4" style={{ borderColor: "var(--amber)", borderWidth: 2 }}>
            <div className="flex items-center justify-between mb-2">
              <div className="flex items-center gap-2"><Sparkles size={16} className="text-[var(--amber)]" /><Caps>Sweeps Coins</Caps></div>
              <Pill tone="amber">redeemable</Pill>
            </div>
            <Mono className="text-[28px]"><Display weight={500}>{fmt.sc(scBalance, { precise: true })}</Display></Mono>
            <div className="text-[11px] text-[var(--ink-3)] mt-1">≈ {fmt.usd(scBalance)} when redeemed (1 SC = $1).</div>
          </div>
          <div className="grid grid-cols-3 gap-2">
            <button onClick={() => onNavigate("shop")} className="ha-btn ha-btn-sm flex-col h-auto py-3 gap-1"><Plus size={14} /><span>Buy GC</span></button>
            <button onClick={() => onNavigate("free-sc")} className="ha-btn ha-btn-ghost ha-btn-sm flex-col h-auto py-3 gap-1 border border-[var(--rule)]"><Gift size={14} /><span>Free SC</span></button>
            <button onClick={() => onNavigate("redeem")} className="ha-btn ha-btn-amber ha-btn-sm flex-col h-auto py-3 gap-1"><ArrowDownUp size={14} /><span>Redeem</span></button>
          </div>
          <div>
            <Caps className="text-[var(--ink-3)] block mb-2">Recent activity</Caps>
            <div className="ha-card divide-y divide-[var(--rule-soft)]">
              {TRANSACTIONS.slice(0, 5).map((t) => (
                <div key={t.id} className="flex items-center gap-3 p-3 text-[13px]">
                  <div className={"w-7 h-7 rounded flex items-center justify-center shrink-0 " + (t.direction === "credit" ? "bg-[var(--yes-soft)]" : "bg-[var(--no-soft)]")}>
```

## Page 79

```text
                    {t.direction === "credit" ? <ArrowDownRight size={13} className="text-[var(--yes-deep)]" /> : <ArrowUpRight size={13} className="text-[var(--no-deep)]" />}
                  </div>
                  <div className="flex-1 min-w-0">
                    <div className="truncate">{t.note}</div>
                    <div className="ha-mono text-[10px] text-[var(--ink-3)]">{fmt.rel(t.ts)}</div>
                  </div>
                  <Mono className={"text-[13px] " + (t.direction === "credit" ? "text-[var(--yes-deep)]" : "text-[var(--no-deep)]")}>
                    {t.direction === "credit" ? "+" : "−"}{t.currency === "GC" ? fmt.gc(t.amount) : fmt.sc(t.amount, { precise: true })} {t.currency}
                  </Mono>
                </div>
              ))}
            </div>
            <button onClick={() => onNavigate("wallet")} className="ha-mono text-[12px] text-[var(--ink-3)] underline mt-3 ml-1">view all transactions →</button>
          </div>
        </div>
      </div>
    </div>
  );
}
function ToastStack({ toasts }) {
  if (toasts.length === 0) return null;
  return (
    <div className="fixed bottom-20 md:bottom-6 right-4 z-50 flex flex-col gap-2 max-w-[320px]">
      {toasts.map((t) => (
        <div key={t.id} className="ha-paper-card p-3 ha-card flex items-center gap-2 ha-fade" style={{ boxShadow: "var(--shadow-lift)" }}>
          <div className="w-7 h-7 rounded flex items-center justify-center shrink-0" style={{ background: t.tone === "success" ? "var(--yes-soft)" : t.tone === "error" ? "var(--no-soft)" : "var(--paper-2)" }}>
            {t.tone === "success" ? <Check size={14} className="text-[var(--yes-deep)]" /> : t.tone === "error" ? <AlertCircle size={14} className="text-[var(--no-deep)]" /> : <Info size={14} />}
          </div>
          <div className="text-[13px]">{t.message}</div>
        </div>
      ))}
    </div>
  );
}
function ComplianceModal({ onClose }) {
  return (
    <div className="fixed inset-0 z-50 bg-black/40 p-4 flex items-end md:items-center justify-center" onClick={onClose}>
      <div onClick={(e) => e.stopPropagation()} className="ha-paper-card ha-card max-w-[640px] w-full max-h-[80vh] overflow-y-auto" style={{ boxShadow: "var(--shadow-lift)" }}>
        <div className="p-6 border-b border-[var(--rule)] flex items-center justify-between">
          <Display weight={700} className="text-[24px]">Compliance Notice</Display>
          <button onClick={onClose} className="h-9 w-9 flex items-center justify-center rounded hover:bg-[var(--paper-2)]"><X size={18} /></button>
        </div>
        <div className="p-6 space-y-4 text-[14px] leading-relaxed text-[var(--ink-2)]">
          <p className="ha-dropcap">Huggy Arena operates a sweepstakes-eligible dual-currency promotion. Gold Coins (GC) are entertainment-only and cannot be redeemed for cash or prizes. Sweeps Coins (SC) are received as a free promotional bonus with qualifying GC purchases or via no-purchase-necessary mail-in entry (AMOE), and are eligible for redemption for prizes subject to state law and identity verification.</p>
          <Rule />
```

## Page 80

```text
          <h4 className="font-semibold text-[var(--ink)] text-[15px]">State Eligibility</h4>
          <p>Sweepstakes promotion is open to U.S. residents 21 and older, except residents of WA and ID. SC redemption is additionally restricted in NV, MI, NY, LA, and CT. Verification of state of residence is performed at signup and at redemption.</p>
          <h4 className="font-semibold text-[var(--ink)] text-[15px]">No Purchase Necessary</h4>
          <p>Mail-in entry to receive Sweeps Coins without purchase: send a hand-written 3"x5" postcard with your name, email, and the words "FREE SC" to the address listed in our official rules.</p>
          <h4 className="font-semibold text-[var(--ink)] text-[15px]">Responsible Play</h4>
          <p>If gambling becomes a problem, call 1-800-GAMBLER. You may set deposit and time limits in Settings, or self-exclude at any time. Identity verification is performed for all redemptions of $100+ as required by AML rules.</p>
        </div>
        <div className="p-6 border-t border-[var(--rule)] flex justify-end gap-2">
          <button onClick={onClose} className="ha-btn">I understand</button>
        </div>
      </div>
    </div>
  );
}
```
