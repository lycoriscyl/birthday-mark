<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Happy Birthday, Mark! 🎂</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Tone.js for vintage ragtime synthesized audio -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.js"></script>
  <!-- Google Fonts: Vintage Cartoon, Vaudeville & Typewriter fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Bungee+Inline&family=Fredericka+the+Great&family=Patrick+Hand+SC&family=Special+Elite&display=swap" rel="stylesheet">

  <style>
    :root {
      --sepia-bg: #ece2c6;
      --film-ink: #1b1612;
      --film-accent: #2e241c;
      --parchment: #f6efe0;
    }

    body {
      font-family: 'Special Elite', cursive, monospace;
      background-color: #12100e;
      color: var(--film-ink);
      overflow-x: hidden;
      user-select: none;
    }

    .font-vaudeville {
      font-family: 'Fredericka the Great', serif;
    }

    .font-cartoon {
      font-family: 'Bungee Inline', cursive, sans-serif;
    }

    .font-hand {
      font-family: 'Patrick Hand SC', cursive;
    }

    /* Mobile touch responsiveness and fast-tap optimization */
    * {
      -webkit-tap-highlight-color: transparent;
      touch-action: manipulation;
    }

    /* 1930s Film Projector Flicker and Scratches */
    .film-projector-filter {
      filter: sepia(0.38) contrast(1.18) brightness(0.96);
      animation: filmJitter 0.12s infinite;
    }

    @keyframes filmJitter {
      0% { transform: translate(0, 0); }
      25% { transform: translate(-0.6px, 0.4px); }
      50% { transform: translate(0.4px, -0.4px); }
      75% { transform: translate(-0.4px, -0.2px); }
      100% { transform: translate(0.5px, 0.3px); }
    }

    @keyframes lightFlicker {
      0%, 100% { opacity: 0.96; }
      30% { opacity: 1; }
      55% { opacity: 0.92; }
      80% { opacity: 0.98; }
    }

    /* Rubber Hose Character Bouncing Animations */
    @keyframes rubberBounce {
      0% {
        transform: translateY(0px) scale(1, 1);
      }
      50% {
        transform: translateY(12px) scale(1.08, 0.92);
      }
      100% {
        transform: translateY(-8px) scale(0.94, 1.06);
      }
    }

    @keyframes rubberBounceOffset {
      0% {
        transform: translateY(10px) scale(1.06, 0.94);
      }
      50% {
        transform: translateY(-8px) scale(0.93, 1.07);
      }
      100% {
        transform: translateY(0px) scale(1, 1);
      }
    }

    @keyframes chewJaw {
      0%, 100% { transform: scaleY(1); }
      50% { transform: scaleY(0.85) scaleX(1.1); }
    }

    @keyframes wagTail {
      0% { transform: rotate(-14deg); }
      50% { transform: rotate(18deg); }
      100% { transform: rotate(-14deg); }
    }

    @keyframes tossFeed {
      0% { transform: rotate(0deg) translateY(0); }
      35% { transform: rotate(-25deg) translateY(-8px); }
      70% { transform: rotate(12deg) translateY(4px); }
      100% { transform: rotate(0deg) translateY(0); }
    }

    @keyframes noteFloat {
      0% { transform: translateY(0) scale(0.7) rotate(0deg); opacity: 0; }
      30% { opacity: 0.9; }
      80% { transform: translateY(-70px) scale(1.2) rotate(15deg); opacity: 0.7; }
      100% { transform: translateY(-110px) scale(1.4) rotate(-10deg); opacity: 0; }
    }

    /* Animation utility classes */
    .anim-bounce-sync {
      animation: rubberBounce 0.58s infinite ease-in-out alternate;
      transform-origin: bottom center;
    }

    .anim-bounce-sync-offset {
      animation: rubberBounceOffset 0.58s infinite ease-in-out alternate;
      transform-origin: bottom center;
    }

    .anim-chew {
      animation: chewJaw 0.35s infinite ease-in-out;
      transform-origin: center;
    }

    .anim-tail {
      animation: wagTail 0.7s infinite ease-in-out;
      transform-origin: 20% 80%;
    }

    .anim-toss {
      animation: tossFeed 1.16s infinite ease-in-out;
      transform-origin: 30% 60%;
    }

    /* Vintage vignette and halftone texture */
    .vignette-layer {
      box-shadow: inset 0 0 90px rgba(25, 18, 12, 0.85), inset 0 0 180px rgba(10, 8, 5, 0.6);
      pointer-events: none;
    }

    .border-vintage {
      border: 6px double #241c15;
    }

    /* Iris Wipe In / Out Animation for Opening */
    .iris-mask {
      clip-path: circle(100% at 50% 50%);
      transition: clip-path 1.2s cubic-bezier(0.77, 0, 0.175, 1);
    }
    .iris-closed {
      clip-path: circle(0% at 50% 50%);
    }

    /* Film grain canvas overlay */
    #grainCanvas {
      pointer-events: none;
      opacity: 0.22;
      mix-blend-mode: overlay;
    }
  </style>
</head>

<body class="min-h-screen flex flex-col items-center justify-center p-2 sm:p-6 bg-stone-950">

  <!-- Streamlined Mobile-Friendly Top Bar -->
  <header class="w-full max-w-5xl flex items-center justify-between text-[#ece2c6] mb-2 px-1 sm:px-2">
    <div class="flex items-center space-x-2">
      <span class="inline-block w-2.5 h-2.5 rounded-full bg-amber-400 animate-pulse"></span>
      <span class="text-xs sm:text-sm font-bold tracking-wider text-amber-200">
        BIRTHDAY EDITION 🎂
      </span>
    </div>
    
    <div class="flex items-center gap-2">
      <!-- Music & Sound Toggle Button -->
      <button id="toggleAudioBtn" class="flex items-center gap-1.5 px-3 py-1.5 rounded-full bg-emerald-900/90 hover:bg-emerald-800 text-emerald-200 text-xs font-bold transition border border-emerald-600/50 shadow-sm active:scale-95">
        <svg id="audioIcon" class="w-3.5 h-3.5" fill="currentColor" viewBox="0 0 20 20">
          <path d="M9.383 3.076A1 1 0 0110 4v12a1 1 0 01-1.707.707L4.586 13H2a1 1 0 01-1-1V8a1 1 0 011-1h2.586l3.707-3.707a1 1 0 011.09-.217zM14.657 2.929a1 1 0 011.414 0A9.972 9.972 0 0119 10a9.972 9.972 0 01-2.929 7.071 1 1 0 01-1.414-1.414A7.971 7.971 0 0017 10c0-2.21-.894-4.208-2.343-5.657a1 1 0 010-1.414zm-2.829 2.828a1 1 0 011.415 0A5.983 5.983 0 0115 10a5.984 5.984 0 01-1.757 4.243 1 1 0 01-1.415-1.415A3.984 3.984 0 0013 10a3.983 3.983 0 00-1.172-2.828 1 1 0 010-1.415z"/>
        </svg>
        <span id="audioStatusText">Music: Playing 🎵</span>
      </button>
    </div>
  </header>

  <!-- Card Film Screen Frame -->
  <main class="relative w-full max-w-5xl bg-[#ebdcc2] border-vintage rounded-2xl shadow-2xl overflow-hidden film-projector-filter" style="min-height: 520px;">

    <!-- Static Projector Grain Canvas -->
    <canvas id="grainCanvas" class="absolute inset-0 w-full h-full z-40 pointer-events-none"></canvas>
    <div class="absolute inset-0 vignette-layer z-30 pointer-events-none"></div>

    <!-- Retro Projector Scratch Lines -->
    <div class="absolute inset-0 pointer-events-none z-30 opacity-20 overflow-hidden">
      <div class="w-[1px] h-full bg-black/60 absolute left-1/4 animate-[filmJitter_0.2s_infinite]"></div>
      <div class="w-[2px] h-full bg-black/40 absolute left-2/3 animate-[filmJitter_0.15s_infinite]"></div>
      <div class="w-[1px] h-full bg-white/70 absolute left-1/2 animate-[filmJitter_0.3s_infinite]"></div>
    </div>

    <!-- Title Header Band Personalized for Mark -->
    <div class="relative z-20 pt-3 pb-2 text-center border-b-4 border-dashed border-[#34271c] bg-[#e4d2b2]/90 select-none px-2">
      <h2 id="cardTitleDisplay" class="text-2xl sm:text-4xl md:text-5xl font-cartoon tracking-wider text-[#201811] drop-shadow">
        HAPPY BIRTHDAY, MARK!
      </h2>
      <p id="cardSubtitleDisplay" class="text-xs sm:text-base font-hand text-[#433224] tracking-wider mt-0.5">
        "Wishing you the swellest day packed with giggles, treats, and good company!"
      </p>
    </div>

    <!-- The Stage / Forest Animated Scene -->
    <div id="sceneContainer" class="relative w-full h-[360px] sm:h-[470px] overflow-hidden cursor-crosshair">
      
      <!-- Interactive Click Instructions Tooltip -->
      <div class="absolute top-2 left-1/2 -translate-x-1/2 z-20 pointer-events-none w-max max-w-[90%] text-center">
        <span class="bg-[#241c14]/85 text-[#fbf5e6] text-[10px] sm:text-xs px-3 py-1 rounded-full border border-amber-900 shadow">
          🌰 Tap anywhere to toss treats to the chubbies!
        </span>
      </div>

      <!-- Animated SVG Cartoon Artwork -->
      <svg id="stageSvg" viewBox="0 0 1000 600" class="w-full h-full object-cover select-none" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <!-- 1930s Halftone Dot Texture -->
          <pattern id="halftoneDots" width="10" height="10" patternUnits="userSpaceOnUse">
            <circle cx="2" cy="2" r="1.3" fill="#2d2218" opacity="0.18" />
          </pattern>
          <!-- Plaid Pattern for Wg Guy's Classic Shirt -->
          <pattern id="wgPlaid" width="18" height="18" patternUnits="userSpaceOnUse">
            <rect width="18" height="18" fill="#a89a87"/>
            <line x1="0" y1="9" x2="18" y2="9" stroke="#362920" stroke-width="3"/>
            <line x1="9" y1="0" x2="9" y2="18" stroke="#362920" stroke-width="3"/>
          </pattern>
        </defs>

        <!-- Background Sky and Halftone Layer -->
        <rect width="1000" height="600" fill="#e8d8be" />
        <rect width="1000" height="600" fill="url(#halftoneDots)" />

        <!-- 1930s Cartoon Sun with Pie-Eyes -->
        <g transform="translate(500, 110)" class="anim-bounce-sync-offset">
          <circle cx="0" cy="0" r="48" fill="#e3c794" stroke="#251c14" stroke-width="4.5" />
          <!-- Sun Rays -->
          <path d="M-60,0 L-75,0 M60,0 L75,0 M0,-60 L0,-75 M0,60 L0,75 M-45,-45 L-55,-55 M45,45 L55,55 M45,-45 L55,-55 M-45,45 L-55,55" 
                stroke="#251c14" stroke-width="4.5" stroke-linecap="round" />
          <!-- Sun Cartoon Face -->
          <!-- Left Pie Eye -->
          <path d="M-18,-8 A7,7 0 1 1 -18,-9 L-18,-8 Z" fill="#251c14"/>
          <polygon points="-18,-8 -12,-11 -15,-5" fill="#e8d8be" />
          <!-- Right Pie Eye -->
          <path d="M18,-8 A7,7 0 1 1 18,-9 L18,-8 Z" fill="#251c14"/>
          <polygon points="18,-8 24,-11 21,-5" fill="#e8d8be" />
          <!-- Smiling mouth with cheek folds -->
          <path d="M-22,12 Q0,32 22,12" fill="none" stroke="#251c14" stroke-width="4" stroke-linecap="round"/>
          <path d="M-24,10 L-20,16 M24,10 L20,16" stroke="#251c14" stroke-width="3.5" stroke-linecap="round"/>
        </g>

        <!-- Whimsical 1930s Background Forest Trees with Curly Trunks -->
        <g stroke="#241b13" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round">
          <!-- Left Big Pine -->
          <path d="M-30,420 C30,320 10,210 60,110 C80,60 140,50 160,100 C210,210 180,310 220,440" fill="#d2c1a3" />
          <path d="M40,190 Q90,160 130,200 M65,270 Q110,230 165,275" fill="none" stroke-width="3" stroke-dasharray="3,3" />

          <!-- Center Distance Hills -->
          <path d="M0,450 Q250,380 500,430 T1000,440 L1000,600 L0,600 Z" fill="#d8c7a8" />

          <!-- Right Tree Trunk with Spirals -->
          <path d="M840,430 C860,280 810,190 870,70 C890,30 950,40 970,90 C1010,200 980,310 1030,440" fill="#cfbe9f" />
          <path d="M860,220 Q920,180 960,230 M850,310 Q910,270 980,320" fill="none" stroke-width="3" stroke-dasharray="3,3" />
        </g>

        <!-- Foreground Log where Wg Guy sits -->
        <g transform="translate(560, 360)">
          <!-- Wood Log -->
          <path d="M0,70 C60,55 180,55 350,70 C360,71 370,110 350,130 C200,145 70,140 0,120 Z" fill="#bfae91" stroke="#241b13" stroke-width="4.5"/>
          <!-- Log rings on the cut end -->
          <ellipse cx="20" cy="95" rx="20" ry="25" fill="#d0be9f" stroke="#241b13" stroke-width="4"/>
          <ellipse cx="20" cy="95" rx="11" ry="14" fill="none" stroke="#241b13" stroke-width="2.5"/>
          <ellipse cx="20" cy="95" rx="4" ry="5" fill="#241b13"/>
          <path d="M80,85 Q160,80 260,88 M120,105 Q220,100 310,106" stroke="#241b13" stroke-width="2" stroke-linecap="round" fill="none"/>
        </g>

        <!-- ==============================================
             LEFT CHARACTER: YOU (The User)
             Bouncing rubber-hose animation, feeding chubbies
             ============================================== -->
        <g id="userChar" transform="translate(180, 240)" class="anim-bounce-sync">
          <!-- Shadow -->
          <ellipse cx="60" cy="235" rx="55" ry="12" fill="#241c14" opacity="0.25" />

          <!-- Rubbery Legs with classic spat shoes -->
          <!-- Left Leg -->
          <path d="M40,175 C30,200 20,220 25,235" fill="none" stroke="#241c14" stroke-width="16" stroke-linecap="round"/>
          <path d="M40,175 C30,200 20,220 25,235" fill="none" stroke="#3d493a" stroke-width="9" stroke-linecap="round"/>
          <!-- Right Leg -->
          <path d="M75,175 C78,195 90,215 95,235" fill="none" stroke="#241c14" stroke-width="16" stroke-linecap="round"/>
          <path d="M75,175 C78,195 90,215 95,235" fill="none" stroke="#3d493a" stroke-width="9" stroke-linecap="round"/>
          <!-- Cartoon Shoes with bulbous toes -->
          <path d="M10,230 C20,220 40,222 45,236 C45,244 20,248 10,244 C3,240 5,232 10,230 Z" fill="#241c14"/>
          <path d="M85,230 C95,220 115,222 120,236 C120,244 95,248 85,244 C78,240 80,232 85,230 Z" fill="#241c14"/>

          <!-- Torso / Hoodie (Warm olive green rubber-hose style) -->
          <path d="M30,110 C20,140 25,180 60,180 C95,180 100,140 90,110 Z" fill="#586b52" stroke="#241c14" stroke-width="4.5" />
          <!-- Hoodie strings -->
          <path d="M52,112 C50,128 45,138 48,144 M68,112 C70,128 75,138 72,144" fill="none" stroke="#241c14" stroke-width="2.5" stroke-linecap="round"/>

          <!-- Left Arm holding brown treat bag -->
          <path d="M30,120 C5,135 15,165 35,160" fill="none" stroke="#241c14" stroke-width="14" stroke-linecap="round"/>
          <path d="M30,120 C5,135 15,165 35,160" fill="none" stroke="#586b52" stroke-width="7" stroke-linecap="round"/>
          <!-- Treat paper bag -->
          <path d="M28,145 L48,140 L52,175 L26,178 Z" fill="#b39268" stroke="#241c14" stroke-width="3.5" />
          <path d="M27,144 Q38,148 49,139" fill="none" stroke="#241c14" stroke-width="2.5" />

          <!-- Right Rubber Hose Arm tossing food -->
          <g class="anim-toss">
            <path d="M85,120 C115,105 135,115 145,95" fill="none" stroke="#241c14" stroke-width="14" stroke-linecap="round"/>
            <path d="M85,120 C115,105 135,115 145,95" fill="none" stroke="#586b52" stroke-width="7" stroke-linecap="round"/>
            <!-- 1930s Mickey/Rubber 4-Finger White Glove -->
            <g transform="translate(145, 95) rotate(-20)">
              <circle cx="0" cy="0" r="10" fill="#fcf9ee" stroke="#241c14" stroke-width="3"/>
              <!-- Finger nubs -->
              <circle cx="6" cy="-6" r="4.5" fill="#fcf9ee" stroke="#241c14" stroke-width="2.5"/>
              <circle cx="10" cy="0" r="4" fill="#fcf9ee" stroke="#241c14" stroke-width="2.5"/>
              <circle cx="8" cy="6" r="4" fill="#fcf9ee" stroke="#241c14" stroke-width="2.5"/>
              <!-- Three black darts/ribs on glove back -->
              <line x1="-3" y1="-4" x2="3" y2="-4" stroke="#241c14" stroke-width="2" stroke-linecap="round"/>
              <line x1="-3" y1="0" x2="3" y2="0" stroke="#241c14" stroke-width="2" stroke-linecap="round"/>
              <line x1="-3" y1="4" x2="3" y2="4" stroke="#241c14" stroke-width="2" stroke-linecap="round"/>
            </g>
          </g>

          <!-- Head & Tousled Hair -->
          <circle cx="60" cy="72" r="38" fill="#ecd8bf" stroke="#241c14" stroke-width="4.5" />
          <!-- Tousled brown cartoon hair locks -->
          <path d="M25,65 C18,30 45,20 60,22 C75,18 102,28 98,62 C90,45 80,48 70,42 C60,50 50,42 40,55 C32,52 28,60 25,65 Z" 
                fill="#4a3625" stroke="#241c14" stroke-width="4.5" stroke-linejoin="round"/>

          <!-- 1930s Rubber Pie-Eyes -->
          <!-- Left Eye -->
          <g transform="translate(48, 68)">
            <ellipse cx="0" cy="0" rx="7" ry="10" fill="#241c14" />
            <polygon points="0,0 -8,-3 -5,-8" fill="#ecd8bf" />
          </g>
          <!-- Right Eye -->
          <g transform="translate(72, 68)">
            <ellipse cx="0" cy="0" rx="7" ry="10" fill="#241c14" />
            <polygon points="0,0 8,-3 5,-8" fill="#ecd8bf" />
          </g>
          <!-- Cheerful Wide Open Mouth with Tongue -->
          <path d="M44,85 Q60,112 76,85 Z" fill="#241c14" stroke="#241c14" stroke-width="2"/>
          <path d="M50,97 Q60,90 70,97 Q60,108 50,97" fill="#b96a66" />
          <!-- Rosy Cheek circles -->
          <ellipse cx="40" cy="82" rx="5" ry="3" fill="#b96a66" opacity="0.5"/>
          <ellipse cx="80" cy="82" rx="5" ry="3" fill="#b96a66" opacity="0.5"/>
        </g>

        <!-- ==============================================
             RIGHT CHARACTER: WG GUY
             Bouncing on the log, wearing glasses, laughing
             ============================================== -->
        <g id="wgChar" transform="translate(680, 210)" class="anim-bounce-sync-offset">
          <!-- Shadow on log -->
          <ellipse cx="40" cy="225" rx="50" ry="10" fill="#241c14" opacity="0.3" />

          <!-- Bent rubber legs sitting on the log -->
          <path d="M15,160 C0,185 5,215 15,225" fill="none" stroke="#241c14" stroke-width="15" stroke-linecap="round"/>
          <path d="M15,160 C0,185 5,215 15,225" fill="none" stroke="#756b5c" stroke-width="8" stroke-linecap="round"/>
          <path d="M45,160 C55,185 60,215 70,225" fill="none" stroke="#241c14" stroke-width="15" stroke-linecap="round"/>
          <path d="M45,160 C55,185 60,215 70,225" fill="none" stroke="#756b5c" stroke-width="8" stroke-linecap="round"/>
          <!-- Shoes -->
          <path d="M5,220 C18,212 32,224 25,233 C15,236 0,230 5,220 Z" fill="#241c14"/>
          <path d="M60,220 C73,212 87,224 80,233 C70,236 55,230 60,220 Z" fill="#241c14"/>

          <!-- Plaid Flannel Shirt / Vest -->
          <path d="M10,105 C5,135 10,165 45,165 C80,165 85,135 80,105 Z" fill="url(#wgPlaid)" stroke="#241c14" stroke-width="4.5" />
          <path d="M10,105 C5,135 10,165 45,165 C80,165 85,135 80,105 Z" fill="none" stroke="#241c14" stroke-width="4.5" />

          <!-- Left Arm holding snack seeds in open palm -->
          <path d="M15,115 C-15,130 -20,150 -5,160" fill="none" stroke="#241c14" stroke-width="13" stroke-linecap="round"/>
          <path d="M15,115 C-15,130 -20,150 -5,160" fill="none" stroke="#8b3a3a" stroke-width="6" stroke-linecap="round"/>
          <!-- White cartoon glove with open palm & seeds -->
          <g transform="translate(-5, 160)">
            <ellipse cx="0" cy="0" rx="9" ry="7" fill="#fcf9ee" stroke="#241c14" stroke-width="3"/>
            <circle cx="-5" cy="-2" r="3" fill="#6d4c2d" />
            <circle cx="2" cy="-1" r="2.5" fill="#6d4c2d" />
            <circle cx="-1" cy="3" r="2.7" fill="#6d4c2d" />
          </g>

          <!-- Right Arm waving treats -->
          <g class="anim-toss">
            <path d="M75,115 C95,125 110,120 115,145" fill="none" stroke="#241c14" stroke-width="13" stroke-linecap="round"/>
            <path d="M75,115 C95,125 110,120 115,145" fill="none" stroke="#8b3a3a" stroke-width="6" stroke-linecap="round"/>
            <circle cx="115" cy="145" r="8" fill="#fcf9ee" stroke="#241c14" stroke-width="3"/>
          </g>

          <!-- Head, Wavy Gray Hair and Warm Laugh -->
          <circle cx="45" cy="68" r="36" fill="#ecd8bf" stroke="#241c14" stroke-width="4.5"/>
          <!-- Distinctive Classic Wavy Gray / Silver Hair -->
          <path d="M12,62 C8,28 35,16 50,18 C65,14 85,25 80,62 C74,40 65,38 52,40 C40,38 25,44 12,62 Z" 
                fill="#d8d3cb" stroke="#241c14" stroke-width="4" stroke-linejoin="round"/>
          <path d="M30,32 Q45,26 60,32 M25,44 Q45,36 65,42" fill="none" stroke="#241c14" stroke-width="2.5"/>

          <!-- 1930s Iconic Round Wire Spectacles -->
          <!-- Left Lens -->
          <circle cx="34" cy="66" r="12" fill="#fff" fill-opacity="0.6" stroke="#241c14" stroke-width="3.5" />
          <!-- Right Lens -->
          <circle cx="60" cy="66" r="12" fill="#fff" fill-opacity="0.6" stroke="#241c14" stroke-width="3.5" />
          <!-- Bridge and temples -->
          <line x1="46" y1="66" x2="48" y2="66" stroke="#241c14" stroke-width="3.5" />
          <line x1="22" y1="64" x2="12" y2="60" stroke="#241c14" stroke-width="3" />
          <line x1="72" y1="64" x2="80" y2="60" stroke="#241c14" stroke-width="3" />

          <!-- Laughing Closed Joyful Pie Eyes (>< style or crescents) -->
          <path d="M27,66 L33,63 L28,69 M41,66 L35,63 L40,69" stroke="#241c14" stroke-width="3" stroke-linecap="round"/>
          <path d="M53,66 L59,63 L54,69 M67,66 L61,63 L66,69" stroke="#241c14" stroke-width="3" stroke-linecap="round"/>

          <!-- Big Happy Grin -->
          <path d="M34,84 Q48,102 62,84 Z" fill="#241c14" stroke="#241c14" stroke-width="2"/>
          <path d="M40,92 Q48,88 56,92 Q48,100 40,92" fill="#b96a66" />
          <!-- Smile wrinkle creases -->
          <path d="M28,82 Q32,86 34,84 M68,82 Q64,86 62,84" stroke="#241c14" stroke-width="2.5" fill="none"/>
        </g>

        <!-- ==============================================
             THE ABSURDLY OBESE WOODLAND CRITTERS
             Spherical, bouncy, chewing, completely stuffed!
             ============================================== -->

        <!-- 1. THE TITANIC SPHERICAL FAWN / DEER (Left Foreground) -->
        <g id="critterDeer" transform="translate(40, 310)" class="anim-bounce-sync cursor-pointer">
          <!-- Shadow -->
          <ellipse cx="110" cy="225" rx="105" ry="18" fill="#241c14" opacity="0.3" />

          <!-- Tiny Chubby Hooves that can barely touch the ground -->
          <ellipse cx="65" cy="220" rx="16" ry="10" fill="#241c14" />
          <ellipse cx="160" cy="220" rx="16" ry="10" fill="#241c14" />
          <ellipse cx="35" cy="180" rx="14" ry="10" fill="#241c14" />
          <ellipse cx="190" cy="175" rx="14" ry="10" fill="#241c14" />

          <!-- Massive Perfectly Round Deer Body -->
          <ellipse cx="115" cy="135" rx="100" ry="92" fill="#b2794c" stroke="#241c14" stroke-width="5" />
          <!-- Huge Creamy Tummy -->
          <ellipse cx="120" cy="155" rx="68" ry="60" fill="#ebdfc8" stroke="#241c14" stroke-width="3.5" />

          <!-- Bambi White Spots on back -->
          <circle cx="50" cy="90" r="7" fill="#f5ede0"/>
          <circle cx="70" cy="75" r="9" fill="#f5ede0"/>
          <circle cx="95" cy="65" r="8" fill="#f5ede0"/>
          <circle cx="55" cy="120" r="8" fill="#f5ede0"/>
          <circle cx="40" cy="145" r="6" fill="#f5ede0"/>

          <!-- Tiny Cute Antlers -->
          <path d="M85,45 C80,20 70,12 60,10 M75,25 C65,22 62,28 60,30" stroke="#241c14" stroke-width="4.5" stroke-linecap="round" fill="none"/>
          <path d="M140,45 C145,20 155,12 165,10 M150,25 C160,22 163,28 165,30" stroke="#241c14" stroke-width="4.5" stroke-linecap="round" fill="none"/>

          <!-- Big Cute Floppy Ears -->
          <path d="M50,55 C25,45 20,60 45,70 Z" fill="#b2794c" stroke="#241c14" stroke-width="4"/>
          <path d="M175,55 C200,45 205,60 180,70 Z" fill="#b2794c" stroke="#241c14" stroke-width="4"/>

          <!-- Big Rubber Hose Pac-Man Pie Eyes -->
          <g transform="translate(90, 85)">
            <ellipse cx="0" cy="0" rx="12" ry="16" fill="#241c14" />
            <polygon points="0,0 -12,-5 -8,-14" fill="#ebdfc8" />
            <circle cx="5" cy="5" r="3.5" fill="#ebdfc8" />
          </g>
          <g transform="translate(140, 85)">
            <ellipse cx="0" cy="0" rx="12" ry="16" fill="#241c14" />
            <polygon points="0,0 12,-5 8,-14" fill="#ebdfc8" />
            <circle cx="-5" cy="5" r="3.5" fill="#ebdfc8" />
          </g>

          <!-- Little Deer Snout & Chubby Cheeks Nibbling -->
          <g class="anim-chew">
            <ellipse cx="115" cy="108" rx="8" ry="5.5" fill="#241c14" />
            <path d="M102,116 Q115,128 128,116" fill="none" stroke="#241c14" stroke-width="3.5" stroke-linecap="round"/>
            <!-- Cookie held in tiny hooves -->
            <circle cx="115" cy="135" r="11" fill="#c49a6c" stroke="#241c14" stroke-width="2.5" />
            <circle cx="112" cy="132" r="2" fill="#241c14" />
            <circle cx="118" cy="137" r="1.8" fill="#241c14" />
          </g>
        </g>

        <!-- 2. ULTRA-CHONKY BUNNY (Middle-Left) -->
        <g id="critterBunny" transform="translate(290, 395)" class="anim-bounce-sync-offset cursor-pointer">
          <!-- Shadow -->
          <ellipse cx="55" cy="120" rx="55" ry="12" fill="#241c14" opacity="0.3" />

          <!-- Tiny flopping ears -->
          <path d="M40,25 C30,-8 15,0 30,30 Z" fill="#ebded0" stroke="#241c14" stroke-width="3.5"/>
          <path d="M68,25 C78,-8 95,0 78,30 Z" fill="#ebded0" stroke="#241c14" stroke-width="3.5"/>

          <!-- Spherical Fluff Body -->
          <ellipse cx="55" cy="75" rx="52" ry="46" fill="#f7eee4" stroke="#241c14" stroke-width="4.5" />
          <ellipse cx="55" cy="84" rx="35" ry="30" fill="#fff" />

          <!-- Tiny bunny tail -->
          <circle cx="5" cy="85" r="14" fill="#f7eee4" stroke="#241c14" stroke-width="3"/>

          <!-- Pie Eyes -->
          <circle cx="42" cy="55" r="6" fill="#241c14" />
          <circle cx="68" cy="55" r="6" fill="#241c14" />
          <!-- Chewing Face with huge round cheeks -->
          <g class="anim-chew">
            <ellipse cx="55" cy="65" rx="4" ry="3" fill="#b96a66" />
            <path d="M48,72 Q55,78 62,72" fill="none" stroke="#241c14" stroke-width="2.5"/>
            <!-- Acorn/nut -->
            <ellipse cx="55" cy="82" rx="7" ry="9" fill="#96613d" stroke="#241c14" stroke-width="2"/>
          </g>
        </g>

        <!-- 3. MASSIVE ROUND RACCOON (Center Ground) -->
        <g id="critterRaccoon" transform="translate(440, 385)" class="anim-bounce-sync cursor-pointer">
          <!-- Shadow -->
          <ellipse cx="65" cy="135" rx="60" ry="13" fill="#241c14" opacity="0.32" />

          <!-- Striped Round Tail -->
          <g class="anim-tail">
            <path d="M110,110 C140,115 160,95 155,75 C150,60 130,70 120,85 Z" fill="#888177" stroke="#241c14" stroke-width="4" />
            <!-- Tail Stripes -->
            <path d="M125,95 L135,85 M137,105 L147,93 M145,112 L155,100" stroke="#241c14" stroke-width="4"/>
          </g>

          <!-- Huge Round Raccoon Body -->
          <ellipse cx="65" cy="85" rx="58" ry="52" fill="#756f67" stroke="#241c14" stroke-width="4.5" />
          <ellipse cx="65" cy="95" rx="38" ry="35" fill="#cfc8be" stroke="#241c14" stroke-width="3" />

          <!-- Raccoon Ears -->
          <path d="M25,45 L40,35 L42,52 Z" fill="#4d4740" stroke="#241c14" stroke-width="3.5" />
          <path d="M105,45 L90,35 L88,52 Z" fill="#4d4740" stroke="#241c14" stroke-width="3.5" />

          <!-- Iconic Bandit Mask -->
          <path d="M22,60 C40,50 90,50 108,60 C105,75 88,78 65,75 C42,78 25,75 22,60 Z" fill="#241c14" />
          
          <!-- Eyes inside mask -->
          <ellipse cx="44" cy="63" rx="6" ry="7" fill="#fcfaf2" />
          <circle cx="45" cy="63" r="4" fill="#241c14" />
          <ellipse cx="86" cy="63" rx="6" ry="7" fill="#fcfaf2" />
          <circle cx="85" cy="63" r="4" fill="#241c14" />

          <!-- Snout and little paws holding a peanut -->
          <g class="anim-chew">
            <ellipse cx="65" cy="78" rx="5" ry="4" fill="#241c14" />
            <path d="M58,85 Q65,92 72,85" stroke="#241c14" stroke-width="2.5" fill="none"/>
            <ellipse cx="65" cy="100" rx="9" ry="6" fill="#cca66e" stroke="#241c14" stroke-width="2.5"/>
          </g>
        </g>

        <!-- 4. COLOSSAL CHIPMUNK / SQUIRREL (Right Foreground) -->
        <g id="critterSquirrel" transform="translate(670, 335)" class="anim-bounce-sync-offset cursor-pointer">
          <!-- Shadow -->
          <ellipse cx="80" cy="195" rx="80" ry="16" fill="#241c14" opacity="0.3" />

          <!-- Colossal Bouncing Bushy Tail -->
          <g class="anim-tail">
            <path d="M125,160 C210,170 230,50 170,10 C140,-10 110,30 135,70 C155,100 135,130 115,140 Z" 
                  fill="#c08552" stroke="#241c14" stroke-width="4.5" />
            <path d="M165,30 Q185,70 155,115" stroke="#241c14" stroke-width="3" fill="none" stroke-linecap="round"/>
          </g>

          <!-- Gigantic Balloon Body -->
          <ellipse cx="75" cy="120" rx="72" ry="68" fill="#c08552" stroke="#241c14" stroke-width="5" />
          <!-- Stuffed Pale Belly -->
          <ellipse cx="70" cy="135" rx="46" ry="45" fill="#f3e5ce" stroke="#241c14" stroke-width="3.5" />

          <!-- Back Chipmunk Stripes -->
          <path d="M22,85 Q25,120 30,150 M12,95 Q15,125 18,145" stroke="#241c14" stroke-width="4" stroke-linecap="round" fill="none"/>

          <!-- Colossal Cheeks stuffed with nuts -->
          <ellipse cx="38" cy="85" rx="20" ry="17" fill="#f0d5b5" stroke="#241c14" stroke-width="3.5"/>
          <ellipse cx="102" cy="85" rx="20" ry="17" fill="#f0d5b5" stroke="#241c14" stroke-width="3.5"/>

          <!-- Cute Tiny Ears -->
          <circle cx="48" cy="40" r="10" fill="#c08552" stroke="#241c14" stroke-width="3.5"/>
          <circle cx="92" cy="40" r="10" fill="#c08552" stroke="#241c14" stroke-width="3.5"/>

          <!-- Pie Eyes -->
          <g transform="translate(52, 65)">
            <ellipse cx="0" cy="0" rx="8" ry="10" fill="#241c14" />
            <polygon points="0,0 -8,-2 -4,-8" fill="#f3e5ce" />
          </g>
          <g transform="translate(88, 65)">
            <ellipse cx="0" cy="0" rx="8" ry="10" fill="#241c14" />
            <polygon points="0,0 8,-2 4,-8" fill="#f3e5ce" />
          </g>

          <!-- Gigantic Acorn in Paws -->
          <g class="anim-chew">
            <ellipse cx="70" cy="74" rx="4.5" ry="3.5" fill="#241c14" />
            <path d="M63,82 Q70,88 77,82" stroke="#241c14" stroke-width="2.5" fill="none"/>
            <!-- Acorn -->
            <path d="M52,98 C52,88 88,88 88,98 Z" fill="#583c28" stroke="#241c14" stroke-width="2.5"/>
            <path d="M54,98 C54,120 70,126 70,126 C70,126 86,120 86,98 Z" fill="#9e6738" stroke="#241c14" stroke-width="2.5"/>
          </g>
        </g>

        <!-- 5. CHUBBY SINGING SONGBIRDS -->
        <!-- Flying chubby bird dropping a musical note -->
        <g transform="translate(880, 160)" class="anim-bounce-sync">
          <ellipse cx="0" cy="0" rx="19" ry="16" fill="#e8d2a0" stroke="#241c14" stroke-width="3.5"/>
          <circle cx="-5" cy="-4" r="3.5" fill="#241c14" />
          <polygon points="-16,-2 -25,2 -16,6" fill="#b96a66" stroke="#241c14" stroke-width="2"/>
          <path d="M10,-4 C22,-18 28,-5 16,5 Z" fill="#bfae91" stroke="#241c14" stroke-width="2.5"/>
        </g>

        <!-- Musical Notes Floating in the Air -->
        <g fill="#241c14" opacity="0.8">
          <path d="M380,180 C380,170 395,160 405,165 L405,185 A6,5 0 1,1 395,180" class="anim-bounce-sync" style="animation-duration: 1.4s;"/>
          <path d="M620,130 C620,120 635,110 645,115 L645,135 A6,5 0 1,1 635,130" class="anim-bounce-sync-offset" style="animation-duration: 1.8s;"/>
        </g>

        <!-- Dynamic Food Treats Group (Populated on user click) -->
        <g id="droppedFoodGroup"></g>
      </svg>
    </div>

    <!-- Vintage Card Message & Mobile-Optimized Interactive Control Deck -->
    <div class="relative z-20 p-3 sm:p-5 bg-[#e4d3b5] border-t-4 border-[#2b2016]">
      <div class="flex flex-col md:flex-row items-center justify-between gap-3 sm:gap-4">
        
        <!-- Left: Personable Telegram Greeting for Mark -->
        <div class="w-full md:w-2/3 bg-[#f6eee0] p-3 rounded-lg border-2 border-[#3d2f23] shadow-inner text-sm leading-relaxed">
          <div class="flex items-center justify-between border-b border-[#cca677] pb-1 mb-1.5 font-mono text-[11px] sm:text-xs text-[#6e5842]">
            <span>BIRTHDAY TELEGRAM • SPECIAL DELIVERY</span>
            <span id="currentDateStamp">OCT 07, 2026</span>
          </div>
          <p id="telegramMessage" class="text-[#2b2016] font-hand text-base sm:text-lg">
            DEAR MARK: HOPING YOUR BIRTHDAY IS OVERFLOWING WITH HUGE GIGGLES, BIG HELPINGS OF CAKE, AND ENDLESS REASONS TO CELEBRATE! WE'RE SENDING YOU OUR WARMEST WISHES FOR AN INCREDIBLE YEAR AHEAD! BEST BIRTHDAY WISHES FROM WG GUY, ME, AND THE WHOLE CHONKY WOODLAND GANG!
          </p>
        </div>

        <!-- Right: Touch-Optimized Action Buttons -->
        <div class="w-full md:w-1/3 flex flex-col gap-2">
          <!-- Toss Food Button -->
          <button id="tossTreatsBtn" class="w-full py-3 px-4 rounded-xl bg-[#2e2319] hover:bg-[#433427] text-[#faedd8] font-cartoon text-xs sm:text-sm tracking-wider uppercase shadow-md active:scale-95 transition flex items-center justify-center gap-2">
            <span>🥜 Toss Treats to Critters!</span>
          </button>

          <div class="grid grid-cols-2 gap-2">
            <!-- Confetti Blast -->
            <button id="confettiBtn" class="py-2.5 px-3 rounded-lg bg-[#b48858] hover:bg-[#9f7447] text-stone-950 font-bold text-xs uppercase shadow transition active:scale-95 text-center">
              🎉 Party Pop!
            </button>
            <!-- Copy Greeting Link / Wish -->
            <button id="copyWishBtn" class="py-2.5 px-3 rounded-lg bg-[#60705a] hover:bg-[#505f4b] text-stone-100 font-bold text-xs uppercase shadow transition active:scale-95 text-center">
              📋 Copy Wish
            </button>
          </div>
        </div>

      </div>

      <!-- Feed Count Ticker -->
      <div class="mt-2.5 flex items-center justify-between text-xs text-[#523f2f] border-t border-[#d8c39e] pt-2">
        <span id="treatCountText">Total Snacks Fed: <strong>0</strong> acorns & cookies</span>
        <span class="font-bold text-amber-900">🎂 Celebrating Mark's Big Day!</span>
      </div>
    </div>

    <!-- Toast Notification for Actions -->
    <div id="toastMessage" class="absolute bottom-6 left-1/2 -translate-x-1/2 z-50 px-4 py-2 bg-[#251c14] text-[#f7efdc] text-xs font-bold rounded-full shadow-2xl border border-amber-500/40 opacity-0 pointer-events-none transition duration-300">
      Treats tossed!
    </div>
  </main>

  <script>
    // State
    let treatsFed = 0;
    let isPlayingMusic = false;
    let synth = null;
    let bassSynth = null;
    let melodyPart = null;
    let bassPart = null;

    // Canvas Film Grain Generator
    const grainCanvas = document.getElementById('grainCanvas');
    const ctx = grainCanvas.getContext('2d');

    function resizeGrain() {
      if (!grainCanvas) return;
      grainCanvas.width = grainCanvas.offsetWidth / 2 || 400;
      grainCanvas.height = grainCanvas.offsetHeight / 2 || 300;
    }
    window.addEventListener('resize', resizeGrain);
    resizeGrain();

    function renderGrain() {
      if (!ctx || grainCanvas.width === 0) return;
      const w = grainCanvas.width;
      const h = grainCanvas.height;
      const imgData = ctx.createImageData(w, h);
      const buffer = new Uint32Array(imgData.data.buffer);
      for (let i = 0; i < buffer.length; i++) {
        if (Math.random() < 0.12) {
          const val = Math.random() < 0.5 ? 40 : 220;
          buffer[i] = (255 << 24) | (val << 16) | (val << 8) | val;
        }
      }
      ctx.putImageData(imgData, 0, 0);
      requestAnimationFrame(renderGrain);
    }
    renderGrain();

    // 1930s Ragtime "Happy Birthday" Synthesizer using Tone.js
    async function setupRagtimeAudio() {
      if (synth) return;

      // Vintage Honky-Tonk / Tin-Pan Piano Style PolySynth
      synth = new Tone.PolySynth(Tone.Synth, {
        oscillator: { type: "triangle" },
        envelope: { attack: 0.01, decay: 0.35, sustain: 0.1, release: 0.4 }
      }).toDestination();
      synth.volume.value = -6;

      // Rubbery Bass Tuba for the 1930s two-step bounce
      bassSynth = new Tone.MembraneSynth({
        pitchDecay: 0.05,
        octaves: 3,
        oscillator: { type: "sine" },
        envelope: { attack: 0.001, decay: 0.3, sustain: 0.01, release: 0.2 }
      }).toDestination();
      bassSynth.volume.value = -4;

      const ragtimeMelody = [
        { time: "0:0", note: "C4", dur: "8n." },
        { time: "0:0:3", note: "C4", dur: "16n" },
        { time: "0:1", note: "D4", dur: "4n" },
        { time: "0:2", note: "C4", dur: "4n" },
        { time: "0:3", note: "F4", dur: "4n" },
        { time: "1:0", note: "E4", dur: "2n" },

        { time: "1:2", note: "C4", dur: "8n." },
        { time: "1:2:3", note: "C4", dur: "16n" },
        { time: "1:3", note: "D4", dur: "4n" },
        { time: "2:0", note: "C4", dur: "4n" },
        { time: "2:1", note: "G4", dur: "4n" },
        { time: "2:2", note: "F4", dur: "2n" },

        { time: "3:0", note: "C4", dur: "8n." },
        { time: "3:0:3", note: "C4", dur: "16n" },
        { time: "3:1", note: "C5", dur: "4n" },
        { time: "3:2", note: "A4", dur: "4n" },
        { time: "3:3", note: "F4", dur: "4n" },
        { time: "4:0", note: "E4", dur: "4n" },
        { time: "4:1", note: "D4", dur: "4n" },

        { time: "4:2", note: "Bb4", dur: "8n." },
        { time: "4:2:3", note: "Bb4", dur: "16n" },
        { time: "4:3", note: "A4", dur: "4n" },
        { time: "5:0", note: "F4", dur: "4n" },
        { time: "5:1", note: "G4", dur: "4n" },
        { time: "5:2", note: "F4", dur: "2n" }
      ];

      const bassLine = [
        { time: "0:0", note: "F2" }, { time: "0:2", note: "C3" },
        { time: "1:0", note: "F2" }, { time: "1:2", note: "C3" },
        { time: "2:0", note: "C2" }, { time: "2:2", note: "G2" },
        { time: "3:0", note: "F2" }, { time: "3:2", note: "C3" },
        { time: "4:0", note: "Bb2" }, { time: "4:2", note: "F2" },
        { time: "5:0", note: "C3" }, { time: "5:2", note: "F2" }
      ];

      melodyPart = new Tone.Part((time, value) => {
        synth.triggerAttackRelease(value.note, value.dur, time);
      }, ragtimeMelody);

      bassPart = new Tone.Part((time, value) => {
        bassSynth.triggerAttackRelease(value.note, "8n", time);
      }, bassLine);

      melodyPart.loop = true;
      melodyPart.loopEnd = "6:0";
      bassPart.loop = true;
      bassPart.loopEnd = "6:0";

      Tone.Transport.bpm.value = 118;
      melodyPart.start(0);
      bassPart.start(0);
    }

    const toggleAudioBtn = document.getElementById('toggleAudioBtn');
    const audioStatusText = document.getElementById('audioStatusText');

    function updateAudioButtonUI(playing) {
      isPlayingMusic = playing;
      if (playing) {
        audioStatusText.textContent = "Music: Playing 🎵";
        toggleAudioBtn.classList.remove('bg-stone-800', 'text-stone-300', 'border-stone-600');
        toggleAudioBtn.classList.add('bg-emerald-900/90', 'text-emerald-200', 'border-emerald-600/50');
      } else {
        audioStatusText.textContent = "Music: Muted 🔇";
        toggleAudioBtn.classList.remove('bg-emerald-900/90', 'text-emerald-200', 'border-emerald-600/50');
        toggleAudioBtn.classList.add('bg-stone-800', 'text-stone-300', 'border-stone-600');
      }
    }

    async function startMusic() {
      try {
        await setupRagtimeAudio();
        await Tone.start();
        Tone.Transport.start();
        updateAudioButtonUI(true);
      } catch (err) {
        // Autoplay may be deferred until first user interaction on strict mobile browsers
      }
    }

    function stopMusic() {
      Tone.Transport.stop();
      updateAudioButtonUI(false);
    }

    // Toggle Audio Handler
    toggleAudioBtn.addEventListener('click', async (e) => {
      e.stopPropagation();
      if (!isPlayingMusic) {
        await startMusic();
        showToast("🎵 Playing Birthday Ragtime!");
      } else {
        stopMusic();
        showToast("🔇 Music paused");
      }
    });

    // Automatic playback trigger on load, with mobile first-gesture fallback
    window.addEventListener('load', () => {
      startMusic();
    });

    // First user gesture listener unlocks audio instantly on iOS/Android if initially restricted
    const unlockOnFirstTouch = async () => {
      if (!isPlayingMusic) {
        await startMusic();
      }
      window.removeEventListener('pointerdown', unlockOnFirstTouch);
      window.removeEventListener('touchstart', unlockOnFirstTouch);
      window.removeEventListener('click', unlockOnFirstTouch);
    };
    window.addEventListener('pointerdown', unlockOnFirstTouch, { passive: true });
    window.addEventListener('touchstart', unlockOnFirstTouch, { passive: true });
    window.addEventListener('click', unlockOnFirstTouch, { passive: true });

    // Cartoon SFX for eating & bouncing
    function playCartoonBoing() {
      try {
        const audioCtx = Tone.context.rawContext || new (window.AudioContext || window.webkitAudioContext)();
        const osc = audioCtx.createOscillator();
        const gain = audioCtx.createGain();
        osc.type = 'sine';
        const now = audioCtx.currentTime;
        osc.frequency.setValueAtTime(180, now);
        osc.frequency.exponentialRampToValueAtTime(540, now + 0.15);
        gain.gain.setValueAtTime(0.25, now);
        gain.gain.linearRampToValueAtTime(0.01, now + 0.2);
        osc.connect(gain);
        gain.connect(audioCtx.destination);
        osc.start(now);
        osc.stop(now + 0.2);
      } catch (err) {}
    }

    // Dropping Treats on Canvas / SVG
    const sceneContainer = document.getElementById('sceneContainer');
    const droppedFoodGroup = document.getElementById('droppedFoodGroup');
    const treatCountText = document.getElementById('treatCountText');

    function throwFood(clientX, clientY) {
      const rect = sceneContainer.getBoundingClientRect();
      const svgX = ((clientX - rect.left) / rect.width) * 1000;
      const svgY = ((clientY - rect.top) / rect.height) * 600;

      const foodItem = document.createElementNS('http://www.w3.org/2000/svg', 'g');
      foodItem.setAttribute('transform', `translate(${svgX}, ${svgY})`);

      const isAcorn = Math.random() > 0.5;
      if (isAcorn) {
        foodItem.innerHTML = `
          <ellipse cx="0" cy="0" rx="8" ry="11" fill="#804e28" stroke="#241c14" stroke-width="2.5" />
          <path d="M-8,-4 C-8,-12 8,-12 8,-4 Z" fill="#4d321d" stroke="#241c14" stroke-width="2" />
          <circle cx="0" cy="-12" r="1.5" fill="#241c14" />
        `;
      } else {
        foodItem.innerHTML = `
          <circle cx="0" cy="0" r="9" fill="#cca36c" stroke="#241c14" stroke-width="2.5" />
          <circle cx="-3" cy="-3" r="1.5" fill="#241c14" />
          <circle cx="3" cy="2" r="1.8" fill="#241c14" />
          <circle cx="-1" cy="4" r="1.4" fill="#241c14" />
        `;
      }

      droppedFoodGroup.appendChild(foodItem);
      playCartoonBoing();
      triggerCritterChomp(svgX);

      treatsFed++;
      treatCountText.innerHTML = `Total Snacks Fed: <strong>${treatsFed}</strong> acorns & cookies`;

      setTimeout(() => {
        foodItem.style.transition = 'transform 0.4s ease-out, opacity 0.4s';
        foodItem.style.transform = `translate(${svgX}, ${Math.min(svgY + 40, 520)}) scale(0.6)`;
        foodItem.style.opacity = '0';
        setTimeout(() => {
          if (foodItem.parentNode) foodItem.parentNode.removeChild(foodItem);
        }, 400);
      }, 700);
    }

    function triggerCritterChomp(x) {
      let critterId = 'critterBunny';
      if (x < 240) critterId = 'critterDeer';
      else if (x < 420) critterId = 'critterBunny';
      else if (x < 620) critterId = 'critterRaccoon';
      else critterId = 'critterSquirrel';

      const critter = document.getElementById(critterId);
      if (critter) {
        critter.style.transition = 'transform 0.15s ease-out';
        critter.style.transform = `${critter.getAttribute('transform')} scale(1.18, 0.88)`;
        setTimeout(() => {
          critter.style.transform = '';
        }, 220);
      }
    }

    // Touch & Click listener for mobile feeding
    sceneContainer.addEventListener('pointerdown', (e) => {
      throwFood(e.clientX, e.clientY);
    });

    // "Toss Treats" Button Trigger
    document.getElementById('tossTreatsBtn').addEventListener('click', () => {
      const rect = sceneContainer.getBoundingClientRect();
      const randX = rect.left + 150 + Math.random() * (rect.width - 300);
      const randY = rect.top + 250 + Math.random() * 150;
      throwFood(randX, randY);
      showToast("Fed a round friend!");
    });

    // Confetti Burst
    const confettiBtn = document.getElementById('confettiBtn');
    confettiBtn.addEventListener('click', () => {
      createVintageConfetti();
      playCartoonBoing();
      showToast("🎉 Happy Birthday Mark!");
    });

    function createVintageConfetti() {
      const colors = ['#241c14', '#ebdcc2', '#b3824c', '#5a6d54', '#8a3c3c', '#d6be96'];
      for (let i = 0; i < 36; i++) {
        const el = document.createElement('div');
        el.className = 'fixed pointer-events-none z-50 rounded-sm';
        el.style.width = `${Math.random() * 10 + 6}px`;
        el.style.height = `${Math.random() * 8 + 6}px`;
        el.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
        el.style.border = '1px solid #1a140f';
        el.style.left = '50%';
        el.style.top = '45%';
        document.body.appendChild(el);

        const destX = (Math.random() - 0.5) * 600;
        const destY = (Math.random() - 0.5) * 400 + 100;
        const rot = Math.random() * 720;

        el.animate([
          { transform: 'translate(0, 0) rotate(0deg)', opacity: 1 },
          { transform: `translate(${destX}px, ${destY}px) rotate(${rot}deg)`, opacity: 0 }
        ], {
          duration: 1200 + Math.random() * 600,
          easing: 'cubic-bezier(0.25, 1, 0.5, 1)'
        }).onfinish = () => el.remove();
      }
    }

    // Copy Birthday Wish to Clipboard for Mark
    const copyWishBtn = document.getElementById('copyWishBtn');
    copyWishBtn.addEventListener('click', () => {
      const title = document.getElementById('cardTitleDisplay').innerText;
      const msg = document.getElementById('telegramMessage').innerText;
      const textToCopy = `🎂 ${title} 🎂\n\n"${msg}"\n\n— Sent with love from Wg Guy & the whole woodland gang!`;

      const tempInput = document.createElement('textarea');
      tempInput.value = textToCopy;
      document.body.appendChild(tempInput);
      tempInput.select();
      document.execCommand('copy');
      document.body.removeChild(tempInput);

      showToast("📋 Copied Mark's Birthday Wish!");
    });

    // Toast notification helper
    const toast = document.getElementById('toastMessage');
    let toastTimeout = null;
    function showToast(msg) {
      if (!toast) return;
      toast.innerText = msg;
      toast.classList.remove('opacity-0');
      toast.classList.add('opacity-100');
      clearTimeout(toastTimeout);
      toastTimeout = setTimeout(() => {
        toast.classList.remove('opacity-100');
        toast.classList.add('opacity-0');
      }, 2200);
    }
  </script>
</body>
</html>

