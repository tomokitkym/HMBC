<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>HMBC - Basketball Utility</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter & JetBrains Mono -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@500;700&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FBFBFB;
            color: #3F3F46;
            overscroll-behavior: none;
            user-select: none;
            -webkit-user-select: none;
            margin: 0;
            padding: 0;
            overflow: hidden;
        }
        .font-mono-num {
            font-family: 'JetBrains Mono', monospace;
            font-variant-numeric: tabular-nums;
        }
        .swipe-area {
            touch-action: none;
            transition: transform 0.1s ease, background-color 0.15s ease;
        }
        .swipe-area:active {
            transform: scale(0.99);
        }
        .player-token {
            touch-action: none;
            cursor: grab;
            transition: box-shadow 0.15s ease;
        }
        .player-token:active {
            cursor: grabbing;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.2);
            z-index: 50;
        }
        ::-webkit-scrollbar {
            width: 4px;
            height: 4px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: #E4E4E7;
            border-radius: 9999px;
        }

        /* アプリ全体のコンテナ：常に画面いっぱい（上下5px余白） */
        #app-wrapper {
            width: 100vw;
            height: 100dvh;
            padding: 5px 8px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            background-color: #FBFBFB;
        }

        /* 12色カラーピッカー用ポップオーバー */
        .color-palette-popover {
            position: absolute;
            top: 100%;
            right: 0;
            margin-top: 4px;
            z-index: 40;
        }

        /* スマホ（幅767px以下）かつ縦向きの場合は、自動的に90度回転して横画面表示にする */
        @media screen and (max-width: 767px) and (orientation: portrait) {
            #app-wrapper {
                position: fixed;
                top: 0;
                left: 100vw;
                width: 100dvh;
                height: 100vw;
                transform: rotate(90deg);
                transform-origin: top left;
            }
        }
    </style>
</head>
<body>

    <div id="app-wrapper">
        <!-- ヘッダー（リセットボタンを右側に配置） -->
        <header class="bg-white border border-zinc-200/80 rounded-xl shrink-0 mb-1.5 shadow-sm">
            <div class="w-full px-3 h-9 md:h-11 flex items-center justify-between gap-2">
                <div class="flex items-center gap-2 shrink-0">
                    <div class="w-6 h-6 md:w-7 md:h-7 rounded-lg bg-zinc-700 text-white flex items-center justify-center font-bold text-xs tracking-tighter">
                        HM
                    </div>
                    <span class="font-bold text-zinc-700 tracking-tight text-sm md:text-base">HMBC</span>
                </div>

                <!-- タブ切り替え（中央配置） -->
                <nav class="flex bg-zinc-100/80 p-0.5 rounded-lg">
                    <button id="tab-timer" onclick="switchTab('timer')" class="px-3 md:px-5 py-1 rounded-md text-xs md:text-sm font-semibold transition-all bg-white text-zinc-800 shadow-sm">
                        タイマー・得点
                    </button>
                    <button id="tab-board" onclick="switchTab('board')" class="px-3 md:px-5 py-1 rounded-md text-xs md:text-sm font-semibold transition-all text-zinc-400 hover:text-zinc-700">
                        作戦盤
                    </button>
                </nav>

                <!-- 全リセットボタン（ヘッダー右端に配置） -->
                <button onclick="resetAllGame()" class="px-2.5 md:px-3.5 py-1 rounded-lg bg-red-50/80 text-red-500 border border-red-200/80 hover:bg-red-100/70 active:scale-95 transition flex items-center gap-1 text-xs md:text-sm font-bold shrink-0" title="時計・ピリオド・得点を初期化">
                    <i data-lucide="rotate-ccw" class="w-3.5 h-3.5 md:w-4 md:h-4"></i>
                    <span>全リセット</span>
                </button>
            </div>
        </header>

        <!-- メインコンテンツ（横幅100%・残り高さをすべて使用） -->
        <main class="flex-1 w-full min-h-0 flex flex-col">

            <!-- ==========================================
                 1. タイマー & スコアボード画面
            ========================================== -->
            <section id="view-timer" class="flex-1 flex flex-col justify-between gap-1.5 md:gap-2.5 min-h-0">
                
                <!-- 上段：メインタイマー（#3E3F46） + ピリオド＆ポゼッション（少し濃いグレー） + 24秒ショットクロック（#3E3F46） -->
                <div class="grid grid-cols-12 gap-1.5 md:gap-2.5 h-[45%] min-h-0">
                    
                    <!-- メインタイマー (5カラム分：背景#3E3F46・文字白・中央揃え大きく) -->
                    <div class="col-span-5 bg-[#3E3F46] rounded-2xl border border-[#52535C] px-3 py-1.5 md:p-3 flex flex-col items-center justify-between shadow-sm relative overflow-hidden text-zinc-50">
                        <div class="w-full flex justify-center items-center gap-2 text-[10px] md:text-xs font-semibold text-zinc-300">
                            <span class="flex items-center gap-1"><i data-lucide="clock" class="w-3 h-3 md:w-3.5 md:h-3.5"></i> GAME CLOCK</span>
                            <span id="timer-status-badge" class="px-2 py-0.5 rounded-full bg-zinc-600 text-zinc-200 text-[9px] md:text-xs">STOPPED</span>
                        </div>

                        <!-- タップ＆スワイプ対応タイマー表示 -->
                        <div id="main-timer-area" class="swipe-area w-full flex-1 rounded-xl flex flex-col items-center justify-center cursor-pointer hover:bg-white/10 select-none text-center" title="タップで開始/停止、停止中に上下スワイプで秒数調整">
                            <div id="main-timer-display" class="font-mono-num text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-bold tracking-tight text-white leading-none text-center">
                                05:00
                            </div>
                        </div>

                        <!-- 下部コントロール：1分プラス・マイナスボタン -->
                        <div class="w-full flex items-center justify-center gap-2">
                            <button onclick="subOneMinute()" class="flex-1 max-w-[110px] py-1 md:py-1.5 rounded-lg bg-zinc-600 text-zinc-100 text-xs md:text-sm font-semibold hover:bg-zinc-500 active:scale-95 transition flex items-center justify-center gap-1">
                                <i data-lucide="minus" class="w-3.5 h-3.5"></i> 1分
                            </button>
                            <button onclick="addOneMinute()" class="flex-1 max-w-[110px] py-1 md:py-1.5 rounded-lg bg-zinc-100 text-zinc-800 text-xs md:text-sm font-bold hover:bg-white active:scale-95 transition flex items-center justify-center gap-1">
                                <i data-lucide="plus" class="w-3.5 h-3.5"></i> 1分
                            </button>
                        </div>
                    </div>

                    <!-- ピリオド ＆ ポゼッションアロー表示 (2カラム分：タイマーと24秒の間に配置・少し濃いグレー) -->
                    <div id="period-area" tabindex="0" class="swipe-area col-span-2 bg-zinc-600 rounded-2xl border border-zinc-500 p-1.5 md:p-2.5 flex flex-col items-center justify-between shadow-sm focus:outline-none focus:ring-2 focus:ring-zinc-300 cursor-ns-resize h-full text-center">
                        <!-- 上部：ピリオド表示 -->
                        <div class="w-full flex-1 flex flex-col items-center justify-center cursor-ns-resize" title="上下スワイプでピリオド切替">
                            <span class="text-[9px] md:text-xs font-bold text-zinc-200 tracking-wider mb-0.5">PERIOD</span>
                            <span id="period-display" class="font-mono-num text-3xl sm:text-4xl md:text-5xl font-bold text-white leading-none text-center">Q1</span>
                        </div>

                        <div class="w-full h-px bg-zinc-500 my-1"></div>

                        <!-- 下部：ポゼッションアロー -->
                        <div id="possession-area" onclick="togglePossession()" class="w-full flex-1 flex flex-col items-center justify-center cursor-pointer rounded-xl hover:bg-white/10 active:scale-95 transition select-none" title="タップでポゼッション方向を変更">
                            <span class="text-[8px] md:text-[10px] font-bold text-zinc-200 tracking-wider mb-0.5">POSSESSION</span>
                            <div id="possession-display" class="flex items-center justify-center h-7 md:h-9 transition-transform duration-150">
                                <i data-lucide="arrow-right" class="w-7 h-7 md:w-8 md:h-8 stroke-[2.5]"></i>
                            </div>
                        </div>
                    </div>

                    <!-- 24秒ショットクロック (5カラム分：背景#3E3F46・アンバー文字) -->
                    <div class="col-span-5 bg-[#3E3F46] rounded-2xl border border-[#52535C] px-3 py-1.5 md:p-3 flex flex-col items-center justify-between shadow-sm">
                        <div class="w-full flex justify-center items-center gap-2 text-[10px] md:text-xs font-semibold text-zinc-300">
                            <span>SHOT CLOCK</span>
                            <span id="shot-status-badge" class="px-2 py-0.5 rounded-full bg-zinc-600 text-zinc-200 text-[9px] md:text-xs shrink-0">STOPPED</span>
                        </div>

                        <div id="shot-clock-area" class="swipe-area w-full flex-1 rounded-xl flex flex-col items-center justify-center cursor-pointer hover:bg-white/10 transition select-none text-center" title="タップで開始/停止、停止中に上下スワイプで秒数調整">
                            <div id="shot-clock-display" class="font-mono-num text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-bold text-amber-400 leading-none text-center">
                                24
                            </div>
                        </div>

                        <div class="w-full flex items-center justify-center gap-2">
                            <button onclick="resetShotClock(24)" class="flex-1 max-w-[110px] py-1 md:py-1.5 rounded-lg bg-zinc-100 text-zinc-800 text-xs md:text-sm font-bold hover:bg-white active:scale-95 transition">
                                24s
                            </button>
                            <button onclick="resetShotClock(14)" class="flex-1 max-w-[110px] py-1 md:py-1.5 rounded-lg bg-zinc-600 text-zinc-100 text-xs md:text-sm font-semibold hover:bg-zinc-500 active:scale-95 transition">
                                14s
                            </button>
                        </div>
                    </div>

                </div>

                <!-- 下段：スコアボード（HOME ＆ GUEST 大きく中央揃え・12色カラー選択対応） -->
                <div class="grid grid-cols-2 gap-1.5 md:gap-2.5 flex-1 min-h-0">
                    
                    <!-- HOME チーム -->
                    <div id="score-area-home" tabindex="0" style="background-color: #FFFFFF; color: #3F3F46;" class="swipe-area rounded-2xl border border-zinc-200/80 px-3 py-2 md:p-4 flex flex-col items-center justify-between shadow-sm focus:outline-none focus:ring-2 focus:ring-zinc-400 cursor-ns-resize relative transition-colors duration-200">
                        <!-- チーム名入力（中央揃え）＋ 背景色選択ボタン -->
                        <div class="w-full flex items-center justify-center relative">
                            <div id="team-input-box-home" class="flex items-center justify-center gap-1.5 w-[72%] bg-black/[0.04] hover:bg-black/[0.08] focus-within:ring-2 focus-within:ring-current px-3 py-1 rounded-lg transition">
                                <i data-lucide="pencil" class="w-3.5 h-3.5 opacity-50 shrink-0"></i>
                                <input type="text" id="team-name-home" value="HOME" placeholder="チーム名" aria-label="ホームチーム名" class="font-bold text-sm sm:text-base md:text-xl tracking-wide bg-transparent focus:outline-none w-full text-center">
                            </div>

                            <!-- 12色カラー選択トリガー -->
                            <div class="absolute right-0">
                                <button type="button" onclick="toggleColorPicker(event, 'home')" class="p-1.5 rounded-lg bg-black/[0.06] hover:bg-black/[0.12] transition flex items-center justify-center" title="背景色を変更">
                                    <i data-lucide="palette" class="w-4 h-4"></i>
                                </button>
                                <div id="color-picker-home" class="hidden color-palette-popover bg-white border border-zinc-200 rounded-xl p-2 shadow-lg grid grid-cols-6 gap-1.5 w-[180px]" onclick="event.stopPropagation()"></div>
                            </div>
                        </div>
                        
                        <!-- 得点表示（特大・中央揃え） -->
                        <div id="score-display-home" class="font-mono-num text-6xl sm:text-7xl md:text-8xl lg:text-9xl font-bold leading-none text-center my-auto">
                            0
                        </div>

                        <div class="text-[10px] md:text-xs opacity-50 text-center flex items-center justify-center gap-1 font-medium">
                            <i data-lucide="arrow-up-down" class="w-3 h-3"></i> 上下スワイプで得点調整
                        </div>
                    </div>

                    <!-- GUEST チーム -->
                    <div id="score-area-guest" tabindex="0" style="background-color: #FFFFFF; color: #3F3F46;" class="swipe-area rounded-2xl border border-zinc-200/80 px-3 py-2 md:p-4 flex flex-col items-center justify-between shadow-sm focus:outline-none focus:ring-2 focus:ring-zinc-400 cursor-ns-resize relative transition-colors duration-200">
                        <!-- チーム名入力（中央揃え）＋ 背景色選択ボタン -->
                        <div class="w-full flex items-center justify-center relative">
                            <div id="team-input-box-guest" class="flex items-center justify-center gap-1.5 w-[72%] bg-black/[0.04] hover:bg-black/[0.08] focus-within:ring-2 focus-within:ring-current px-3 py-1 rounded-lg transition">
                                <i data-lucide="pencil" class="w-3.5 h-3.5 opacity-50 shrink-0"></i>
                                <input type="text" id="team-name-guest" value="GUEST" placeholder="チーム名" aria-label="ゲストチーム名" class="font-bold text-sm sm:text-base md:text-xl tracking-wide bg-transparent focus:outline-none w-full text-center">
                            </div>

                            <!-- 12色カラー選択トリガー -->
                            <div class="absolute right-0">
                                <button type="button" onclick="toggleColorPicker(event, 'guest')" class="p-1.5 rounded-lg bg-black/[0.06] hover:bg-black/[0.12] transition flex items-center justify-center" title="背景色を変更">
                                    <i data-lucide="palette" class="w-4 h-4"></i>
                                </button>
                                <div id="color-picker-guest" class="hidden color-palette-popover bg-white border border-zinc-200 rounded-xl p-2 shadow-lg grid grid-cols-6 gap-1.5 w-[180px]" onclick="event.stopPropagation()"></div>
                            </div>
                        </div>
                        
                        <!-- 得点表示（特大・中央揃え） -->
                        <div id="score-display-guest" class="font-mono-num text-6xl sm:text-7xl md:text-8xl lg:text-9xl font-bold leading-none text-center my-auto">
                            0
                        </div>

                        <div class="text-[10px] md:text-xs opacity-50 text-center flex items-center justify-center gap-1 font-medium">
                            <i data-lucide="arrow-up-down" class="w-3 h-3"></i> 上下スワイプで得点調整
                        </div>
                    </div>

                </div>
            </section>

            <!-- ==========================================
                 2. 作戦盤画面（横画面に最適な左右2カラム構成）
            ========================================== -->
            <section id="view-board" class="hidden flex-1 grid grid-cols-12 gap-1.5 md:gap-3 min-h-0">
                
                <!-- 左カラム（8カラム分）：コートを画面いっぱい大きく表示 -->
                <div class="col-span-8 bg-white rounded-2xl border border-zinc-200/80 p-1.5 md:p-2 shadow-sm flex items-center justify-center overflow-hidden h-full">
                    <div id="court-container" class="relative h-full max-w-full aspect-[626/400] rounded-xl overflow-hidden select-none bg-cover bg-center shadow-inner">
                        <!-- 手書き線描画用キャンバス -->
                        <canvas id="drawing-canvas" class="absolute inset-0 w-full h-full z-10"></canvas>

                        <!-- 選手・ボールマーカー配置レイヤー -->
                        <div id="players-layer" class="absolute inset-0 z-20 pointer-events-none"></div>
                    </div>
                </div>

                <!-- 右カラム（4カラム分）：作戦名・ツール・選手操作・メモを縦に集約 -->
                <div class="col-span-4 flex flex-col gap-1.5 md:gap-2 min-h-0 h-full">
                    
                    <!-- 作戦名入力 -->
                    <div class="bg-white rounded-xl border border-zinc-200/80 px-2.5 py-1.5 flex items-center gap-1.5 shadow-sm shrink-0">
                        <i data-lucide="clipboard-list" class="w-3.5 h-3.5 text-zinc-400 shrink-0"></i>
                        <input type="text" id="tactic-name" placeholder="作戦名（例：ホーンセット）" class="w-full text-xs md:text-sm font-medium text-zinc-700 placeholder-zinc-400 bg-transparent focus:outline-none">
                    </div>

                    <!-- 描画ツール切り替え -->
                    <div class="bg-white rounded-xl border border-zinc-200/80 p-1.5 flex flex-wrap items-center justify-between gap-1 shadow-sm shrink-0">
                        <div class="flex items-center gap-1 bg-zinc-100/80 p-0.5 rounded-lg w-full justify-between">
                            <button id="tool-move" onclick="setBoardTool('move')" class="flex-1 py-1 px-1.5 rounded-md text-[11px] md:text-xs font-medium bg-white text-zinc-800 shadow-sm flex items-center justify-center gap-1" title="選手・ボール移動">
                                <i data-lucide="hand" class="w-3.5 h-3.5"></i><span>移動</span>
                            </button>
                            <div id="pen-tool-wrapper" class="flex-1 flex items-center justify-center gap-1">
                                <button id="tool-pen" onclick="setBoardTool('pen')" class="w-full py-1 px-1.5 rounded-md text-[11px] md:text-xs font-medium text-zinc-500 hover:text-zinc-800 flex items-center justify-center gap-1" title="線を描く">
                                    <i data-lucide="pen-tool" class="w-3.5 h-3.5"></i><span>ペン</span>
                                </button>
                            </div>
                            <button id="tool-eraser" onclick="setBoardTool('eraser')" class="flex-1 py-1 px-1.5 rounded-md text-[11px] md:text-xs font-medium text-zinc-500 hover:text-zinc-800 flex items-center justify-center gap-1" title="線を消す">
                                <i data-lucide="eraser" class="w-3.5 h-3.5"></i><span>消す</span>
                            </button>
                        </div>

                        <!-- ペン色選択 ＆ 線全消去サブバー -->
                        <div class="w-full flex items-center justify-between px-1 pt-0.5">
                            <div class="flex items-center gap-2">
                                <span class="text-[10px] text-zinc-400">ペン色:</span>
                                <button id="pen-color-black" onclick="setPenColor('#3F3F46')" class="w-4 h-4 rounded-full bg-zinc-700 border border-white shadow-sm ring-2 ring-offset-1 ring-zinc-300" title="チャコールペン"></button>
                                <button id="pen-color-red" onclick="setPenColor('#EF4444')" class="w-4 h-4 rounded-full bg-red-500 border border-white shadow-sm ring-1 ring-zinc-200" title="ソフトレッドペン"></button>
                            </div>
                            <button onclick="clearLines()" class="px-2 py-0.5 rounded-md text-[10px] md:text-xs font-medium text-red-500 hover:bg-red-50 flex items-center gap-1" title="線をすべて消す">
                                <i data-lucide="trash-2" class="w-3 h-3"></i><span>線全消去</span>
                            </button>
                        </div>
                    </div>

                    <!-- 選手・ボール追加・削除コントロール -->
                    <div class="bg-white rounded-xl border border-zinc-200/80 p-2 flex flex-col gap-1.5 shadow-sm shrink-0">
                        <!-- オフェンス -->
                        <div class="flex items-center justify-between">
                            <div class="flex items-center gap-1.5">
                                <span class="w-2.5 h-2.5 rounded-full bg-zinc-700 shrink-0"></span>
                                <span class="text-[11px] md:text-xs font-semibold text-zinc-600">オフェンス (<span id="offense-count">5</span>)</span>
                            </div>
                            <div class="flex items-center gap-1">
                                <button onclick="removePlayer('offense')" class="w-6 h-6 rounded-md bg-zinc-100 hover:bg-zinc-200 text-zinc-600 flex items-center justify-center transition">
                                    <i data-lucide="minus" class="w-3 h-3"></i>
                                </button>
                                <button onclick="addPlayer('offense')" class="w-6 h-6 rounded-md bg-zinc-700 hover:bg-zinc-600 text-white flex items-center justify-center transition">
                                    <i data-lucide="plus" class="w-3 h-3"></i>
                                </button>
                            </div>
                        </div>

                        <!-- ディフェンス -->
                        <div class="flex items-center justify-between">
                            <div class="flex items-center gap-1.5">
                                <span class="w-2.5 h-2.5 rounded-full bg-white border-2 border-red-400 shrink-0"></span>
                                <span class="text-[11px] md:text-xs font-semibold text-zinc-600">ディフェンス (<span id="defense-count">5</span>)</span>
                            </div>
                            <div class="flex items-center gap-1">
                                <button onclick="removePlayer('defense')" class="w-6 h-6 rounded-md bg-zinc-100 hover:bg-zinc-200 text-zinc-600 flex items-center justify-center transition">
                                    <i data-lucide="minus" class="w-3 h-3"></i>
                                </button>
                                <button onclick="addPlayer('defense')" class="w-6 h-6 rounded-md bg-red-400 hover:bg-red-500 text-white flex items-center justify-center transition">
                                    <i data-lucide="plus" class="w-3 h-3"></i>
                                </button>
                            </div>
                        </div>

                        <!-- ボール -->
                        <div class="flex items-center justify-between">
                            <div class="flex items-center gap-1.5">
                                <span class="w-3 h-3 rounded-full bg-amber-400 text-white text-[8px] font-bold flex items-center justify-center shrink-0">B</span>
                                <span class="text-[11px] md:text-xs font-semibold text-zinc-600">ボール (<span id="ball-count">1</span>)</span>
                            </div>
                            <div class="flex items-center gap-1">
                                <button onclick="removeBall()" class="w-6 h-6 rounded-md bg-zinc-100 hover:bg-zinc-200 text-zinc-600 flex items-center justify-center transition">
                                    <i data-lucide="minus" class="w-3 h-3"></i>
                                </button>
                                <button onclick="addBall()" class="w-6 h-6 rounded-md bg-amber-400 hover:bg-amber-500 text-white flex items-center justify-center transition">
                                    <i data-lucide="plus" class="w-3 h-3"></i>
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- 作戦メモ（残り高さをすべて使用） -->
                    <div class="bg-white rounded-xl border border-zinc-200/80 p-2 shadow-sm flex-1 flex flex-col min-h-0">
                        <label for="tactic-memo" class="text-[10px] font-semibold text-zinc-400 uppercase tracking-wider mb-1 flex items-center gap-1 shrink-0">
                            <i data-lucide="file-text" class="w-3 h-3"></i> 作戦メモ
                        </label>
                        <textarea id="tactic-memo" placeholder="動きのポイントや指示をメモ..." class="w-full flex-1 text-xs text-zinc-700 placeholder-zinc-400 bg-zinc-50/70 rounded-lg p-2 border border-zinc-200/70 focus:outline-none focus:border-zinc-300 resize-none"></textarea>
                    </div>

                </div>

            </section>

        </main>
    </div>

    <script>
        // アイコン初期化
        lucide.createIcons();

        /* ==========================================================================
           スマホ縦持ち時の自動横画面回転判定ヘルパー
        ========================================================================== */
        function isForcedLandscape() {
            return window.innerWidth <= 767 && window.innerHeight > window.innerWidth;
        }

        // 回転状態に応じて論理的な「上下スワイプ量（上方向がプラス）」を取得
        function getLogicalSwipeUpDelta(startClientX, startClientY, currentClientX, currentClientY) {
            if (isForcedLandscape()) {
                // 90度時計回りに回転しているため、画面上の「上」は物理端末の「右（clientX増加方向）」
                return currentClientX - startClientX;
            }
            return startClientY - currentClientY;
        }

        // 回転状態に応じてコンテナ内の正規化座標(0〜1)を取得
        function getNormalizedCoordsInContainer(clientX, clientY, rect) {
            if (isForcedLandscape()) {
                // 90度時計回り回転時：rect.widthは物理X幅(論理高さ)、rect.heightは物理Y高さ(論理幅)
                const normX = (clientY - rect.top) / rect.height;
                const normY = (rect.right - clientX) / rect.width;
                return { x: normX, y: normY };
            }
            return {
                x: (clientX - rect.left) / rect.width,
                y: (clientY - rect.top) / rect.height
            };
        }

        /* ==========================================================================
           ブザー音（Web Audio API）
        ========================================================================== */
        function playBuzzer() {
            try {
                const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(440, audioCtx.currentTime);
                gain.gain.setValueAtTime(0.3, audioCtx.currentTime);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start();
                osc.stop(audioCtx.currentTime + 0.8);
            } catch (e) {
                console.log('Audio playback prevented or not supported', e);
            }
        }

        /* ==========================================================================
           タブ切り替えロジック
        ========================================================================== */
        function switchTab(tab) {
            const timerView = document.getElementById('view-timer');
            const boardView = document.getElementById('view-board');
            const tabTimer = document.getElementById('tab-timer');
            const tabBoard = document.getElementById('tab-board');

            if (tab === 'timer') {
                timerView.classList.remove('hidden');
                boardView.classList.add('hidden');
                tabTimer.className = 'px-3 md:px-5 py-1 rounded-md text-xs md:text-sm font-semibold transition-all bg-white text-zinc-800 shadow-sm';
                tabBoard.className = 'px-3 md:px-5 py-1 rounded-md text-xs md:text-sm font-semibold transition-all text-zinc-400 hover:text-zinc-700';
            } else {
                timerView.classList.add('hidden');
                boardView.classList.remove('hidden');
                tabBoard.className = 'px-3 md:px-5 py-1 rounded-md text-xs md:text-sm font-semibold transition-all bg-white text-zinc-800 shadow-sm';
                tabTimer.className = 'px-3 md:px-5 py-1 rounded-md text-xs md:text-sm font-semibold transition-all text-zinc-400 hover:text-zinc-700';
                setTimeout(resizeCanvas, 20);
            }
        }

        /* ==========================================================================
           スコア背景色（12色：目に優しいソフトトーン）＆ 自動コントラスト調整ロジック
        ========================================================================== */
        const SCORE_COLORS = [
            { name: 'ホワイト',       hex: '#FFFFFF', isDark: false },
            { name: 'ソフトチャコール', hex: '#52525B', isDark: true },
            { name: 'ソフトレッド',   hex: '#F87171', isDark: true },
            { name: 'ソフトブルー',   hex: '#60A5FA', isDark: true },
            { name: 'ミントグリーン', hex: '#4ADE80', isDark: false },
            { name: 'パステルイエロー', hex: '#FEF08A', isDark: false },
            { name: 'ソフトオレンジ', hex: '#FB923C', isDark: true },
            { name: 'ラベンダー',     hex: '#A78BFA', isDark: true },
            { name: 'ソフトピンク',   hex: '#F472B6', isDark: true },
            { name: 'ペールスカイ',   hex: '#BAE6FD', isDark: false },
            { name: 'スレートブルー', hex: '#64748B', isDark: true },
            { name: 'ライトグレー',   hex: '#E4E4E7', isDark: false }
        ];

        function initColorPickers() {
            ['home', 'guest'].forEach(team => {
                const container = document.getElementById(`color-picker-${team}`);
                container.innerHTML = '';
                SCORE_COLORS.forEach(c => {
                    const btn = document.createElement('button');
                    btn.type = 'button';
                    btn.title = c.name;
                    btn.style.backgroundColor = c.hex;
                    btn.className = 'w-6 h-6 rounded-full border border-zinc-200 shadow-sm hover:scale-110 transition active:scale-95';
                    btn.onclick = (e) => {
                        e.stopPropagation();
                        applyScoreCardColor(team, c);
                        container.classList.add('hidden');
                    };
                    container.appendChild(btn);
                });
            });
        }

        function toggleColorPicker(event, team) {
            event.stopPropagation();
            const otherTeam = team === 'home' ? 'guest' : 'home';
            document.getElementById(`color-picker-${otherTeam}`).classList.add('hidden');
            const target = document.getElementById(`color-picker-${team}`);
            target.classList.toggle('hidden');
        }

        function applyScoreCardColor(team, colorObj) {
            const card = document.getElementById(`score-area-${team}`);
            const inputBox = document.getElementById(`team-input-box-${team}`);
            teamColors[team] = colorObj.hex;
            card.style.backgroundColor = colorObj.hex;
            card.style.color = colorObj.isDark ? '#FFFFFF' : '#3F3F46';
            card.style.borderColor = colorObj.hex === '#FFFFFF' ? '#E4E4E7' : colorObj.hex;

            if (colorObj.isDark) {
                inputBox.classList.remove('bg-black/[0.04]', 'hover:bg-black/[0.08]');
                inputBox.classList.add('bg-white/20', 'hover:bg-white/30');
            } else {
                inputBox.classList.remove('bg-white/20', 'hover:bg-white/30');
                inputBox.classList.add('bg-black/[0.04]', 'hover:bg-black/[0.08]');
            }
            updatePossessionDisplay();
        }

        // 画面のどこかをクリックしたらカラーパレットを閉じる
        window.addEventListener('click', () => {
            document.getElementById('color-picker-home')?.classList.add('hidden');
            document.getElementById('color-picker-guest')?.classList.add('hidden');
        });

        /* ==========================================================================
           タイマー ＆ スコアボード ロジック
        ========================================================================== */
        let mainSeconds = 300; // 初期設定 5分
        let isMainRunning = false;
        let mainInterval = null;

        let shotSeconds = 24;
        let isShotRunning = false;
        let shotInterval = null;

        const periods = ['Q1', 'Q2', 'Q3', 'Q4', 'OT'];
        let currentPeriodIndex = 0;

        // ポゼッションアロー状態: 'right' (右側GUESTチーム), 'left' (左側HOMEチーム)
        let possessionDirection = 'right';
        let teamColors = { home: '#FFFFFF', guest: '#FFFFFF' };

        let scores = { home: 0, guest: 0 };

        function updatePeriodDisplay() {
            document.getElementById('period-display').textContent = periods[currentPeriodIndex];
        }

        // 少し薄いグレー背景（#71717A）上で視認しやすい矢印色を取得
        function getArrowColorForTeam(team) {
            const hex = teamColors[team] || '#FFFFFF';
            // 近いグレー系（チャコール・スレート）は同化しやすいため明るめ・白に補正
            if (hex === '#52525B' || hex === '#64748B') return '#F4F4F5';
            return hex;
        }

        function updatePossessionDisplay() {
            const container = document.getElementById('possession-display');
            if (possessionDirection === 'right') {
                const color = getArrowColorForTeam('guest');
                container.innerHTML = `<i data-lucide="arrow-right" style="color: ${color};" class="w-7 h-7 md:w-8 md:h-8 stroke-[2.5]"></i>`;
            } else {
                const color = getArrowColorForTeam('home');
                container.innerHTML = `<i data-lucide="arrow-left" style="color: ${color};" class="w-7 h-7 md:w-8 md:h-8 stroke-[2.5]"></i>`;
            }
            lucide.createIcons();
        }

        function togglePossession() {
            possessionDirection = possessionDirection === 'right' ? 'left' : 'right';
            updatePossessionDisplay();
        }

        function setPossession(dir) {
            possessionDirection = dir;
            updatePossessionDisplay();
        }

        function changePeriod(delta) {
            currentPeriodIndex = (currentPeriodIndex + delta + periods.length) % periods.length;
            updatePeriodDisplay();
        }

        function nextPeriod() {
            changePeriod(1);
        }

        function updateMainTimerDisplay() {
            const mins = Math.floor(mainSeconds / 60);
            const secs = mainSeconds % 60;
            document.getElementById('main-timer-display').textContent = 
                `${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
        }

        function updateShotClockDisplay() {
            const el = document.getElementById('shot-clock-display');
            el.textContent = String(shotSeconds).padStart(2, '0');
            el.classList.toggle('text-red-400', shotSeconds <= 5);
            el.classList.toggle('text-amber-400', shotSeconds > 5);
        }

        function toggleMainTimer() {
            const badge = document.getElementById('timer-status-badge');
            if (isMainRunning) {
                clearInterval(mainInterval);
                isMainRunning = false;
                badge.textContent = 'STOPPED';
                badge.className = 'px-2 py-0.5 rounded-full bg-zinc-600 text-zinc-200 text-[9px] md:text-xs';
            } else {
                if (mainSeconds <= 0) return;
                isMainRunning = true;
                badge.textContent = 'RUNNING';
                badge.className = 'px-2 py-0.5 rounded-full bg-emerald-400 text-zinc-900 text-[9px] md:text-xs font-bold';
                mainInterval = setInterval(() => {
                    if (mainSeconds > 0) {
                        mainSeconds--;
                        updateMainTimerDisplay();
                        if (mainSeconds === 0) {
                            playBuzzer();
                            toggleMainTimer();
                        }
                    } else {
                        toggleMainTimer();
                    }
                }, 1000);
            }
        }

        function addOneMinute() {
            mainSeconds += 60;
            updateMainTimerDisplay();
        }

        function subOneMinute() {
            mainSeconds = Math.max(0, mainSeconds - 60);
            updateMainTimerDisplay();
        }

        function resetAllGame() {
            // メインタイマーのリセット
            if (isMainRunning) toggleMainTimer();
            mainSeconds = 300;
            updateMainTimerDisplay();

            // 24秒ショットクロックのリセット
            if (isShotRunning) toggleShotClock();
            shotSeconds = 24;
            updateShotClockDisplay();

            // ピリオドのリセット
            currentPeriodIndex = 0;
            updatePeriodDisplay();

            // 両チーム得点のリセット
            scores.home = 0;
            scores.guest = 0;
            document.getElementById('score-display-home').textContent = '0';
            document.getElementById('score-display-guest').textContent = '0';
        }

        function toggleShotClock() {
            const badge = document.getElementById('shot-status-badge');
            if (isShotRunning) {
                clearInterval(shotInterval);
                isShotRunning = false;
                badge.textContent = 'STOPPED';
                badge.className = 'px-2 py-0.5 rounded-full bg-zinc-600 text-zinc-200 text-[9px] md:text-xs shrink-0';
            } else {
                if (shotSeconds <= 0) return;
                isShotRunning = true;
                badge.textContent = 'RUNNING';
                badge.className = 'px-2 py-0.5 rounded-full bg-amber-400 text-zinc-900 text-[9px] md:text-xs font-bold shrink-0';
                shotInterval = setInterval(() => {
                    if (shotSeconds > 0) {
                        shotSeconds--;
                        updateShotClockDisplay();
                        if (shotSeconds === 0) {
                            playBuzzer();
                            toggleShotClock();
                        }
                    } else {
                        toggleShotClock();
                    }
                }, 1000);
            }
        }

        function resetShotClock(sec) {
            shotSeconds = sec;
            updateShotClockDisplay();
        }

        function changeScore(team, delta) {
            scores[team] = Math.max(0, scores[team] + delta);
            const display = document.getElementById(`score-display-${team}`);
            display.textContent = scores[team];
            display.style.transform = delta > 0 ? 'translateY(-4px)' : 'translateY(4px)';
            setTimeout(() => display.style.transform = 'translateY(0)', 120);
        }

        /* ==========================================================================
           スワイプ＆キーボード ジェスチャー制御（確実な1点増減）
        ========================================================================== */
        function setupSwipeGesture(element, { onTap, onSwipeUp, onSwipeDown, continuous = false }) {
            let startX = 0;
            let startY = 0;
            let isSwiping = false;
            let hasTriggered = false;
            let lastTriggerTime = 0;
            const threshold = 22;

            element.addEventListener('touchstart', (e) => {
                startX = e.touches[0].clientX;
                startY = e.touches[0].clientY;
                isSwiping = false;
                hasTriggered = false;
            }, { passive: true });

            element.addEventListener('touchmove', (e) => {
                const currentX = e.touches[0].clientX;
                const currentY = e.touches[0].clientY;
                const diff = getLogicalSwipeUpDelta(startX, startY, currentX, currentY);
                const now = Date.now();
                
                if (Math.abs(diff) > threshold) {
                    isSwiping = true;
                    if (continuous) {
                        if (now - lastTriggerTime > 150) {
                            diff > 0 ? (onSwipeUp && onSwipeUp()) : (onSwipeDown && onSwipeDown());
                            startX = currentX;
                            startY = currentY;
                            lastTriggerTime = now;
                        }
                    } else if (!hasTriggered) {
                        hasTriggered = true;
                        diff > 0 ? (onSwipeUp && onSwipeUp()) : (onSwipeDown && onSwipeDown());
                    }
                }
            }, { passive: true });

            element.addEventListener('touchend', (e) => {
                if (!isSwiping && onTap) {
                    e.preventDefault();
                    onTap();
                }
            });

            let isMouseDown = false;
            element.addEventListener('mousedown', (e) => {
                if (e.target.tagName === 'INPUT' || e.target.closest('button')) return;
                isMouseDown = true;
                startX = e.clientX;
                startY = e.clientY;
                isSwiping = false;
                hasTriggered = false;
            });

            window.addEventListener('mousemove', (e) => {
                if (!isMouseDown) return;
                const diff = getLogicalSwipeUpDelta(startX, startY, e.clientX, e.clientY);
                const now = Date.now();
                if (Math.abs(diff) > threshold) {
                    isSwiping = true;
                    if (continuous) {
                        if (now - lastTriggerTime > 150) {
                            diff > 0 ? (onSwipeUp && onSwipeUp()) : (onSwipeDown && onSwipeDown());
                            startX = e.clientX;
                            startY = e.clientY;
                            lastTriggerTime = now;
                        }
                    } else if (!hasTriggered) {
                        hasTriggered = true;
                        diff > 0 ? (onSwipeUp && onSwipeUp()) : (onSwipeDown && onSwipeDown());
                    }
                }
            });

            window.addEventListener('mouseup', () => {
                if (isMouseDown) {
                    if (!isSwiping && onTap) {
                        onTap();
                    }
                    isMouseDown = false;
                }
            });
        }

        const mainTimerArea = document.getElementById('main-timer-area');
        setupSwipeGesture(mainTimerArea, {
            continuous: true,
            onTap: () => toggleMainTimer(),
            onSwipeUp: () => {
                if (!isMainRunning) {
                    mainSeconds++;
                    updateMainTimerDisplay();
                }
            },
            onSwipeDown: () => {
                if (!isMainRunning && mainSeconds > 0) {
                    mainSeconds--;
                    updateMainTimerDisplay();
                }
            }
        });

        const shotClockArea = document.getElementById('shot-clock-area');
        setupSwipeGesture(shotClockArea, {
            continuous: true,
            onTap: () => toggleShotClock(),
            onSwipeUp: () => {
                if (!isShotRunning) {
                    shotSeconds++;
                    updateShotClockDisplay();
                }
            },
            onSwipeDown: () => {
                if (!isShotRunning && shotSeconds > 0) {
                    shotSeconds--;
                    updateShotClockDisplay();
                }
            }
        });

        const periodArea = document.getElementById('period-area');
        setupSwipeGesture(periodArea, {
            continuous: false,
            onSwipeUp: () => changePeriod(1),
            onSwipeDown: () => changePeriod(-1)
        });

        // ポゼッションエリアのタップ・クリックイベント（スワイプと干渉しないよう独立制御）
        const possessionArea = document.getElementById('possession-area');
        possessionArea.addEventListener('touchstart', (e) => {
            e.stopPropagation();
        }, { passive: true });
        possessionArea.addEventListener('mousedown', (e) => {
            e.stopPropagation();
        });

        periodArea.addEventListener('keydown', (e) => {
            if (e.repeat) return;
            if (e.key === 'ArrowUp') {
                e.preventDefault();
                e.stopPropagation();
                changePeriod(1);
            } else if (e.key === 'ArrowDown') {
                e.preventDefault();
                e.stopPropagation();
                changePeriod(-1);
            }
        });

        ['home', 'guest'].forEach(team => {
            const area = document.getElementById(`score-area-${team}`);
            setupSwipeGesture(area, {
                continuous: false,
                onSwipeUp: () => changeScore(team, 1),
                onSwipeDown: () => changeScore(team, -1)
            });

            area.addEventListener('keydown', (e) => {
                if (e.repeat) return;
                if (document.activeElement.tagName === 'INPUT') return;
                if (e.key === 'ArrowUp') {
                    e.preventDefault();
                    e.stopPropagation();
                    changeScore(team, 1);
                } else if (e.key === 'ArrowDown') {
                    e.preventDefault();
                    e.stopPropagation();
                    changeScore(team, -1);
                }
            });
        });

        let hoveredElement = null;
        document.getElementById('score-area-home').addEventListener('mouseenter', () => hoveredElement = 'home');
        document.getElementById('score-area-home').addEventListener('mouseleave', () => hoveredElement = null);
        document.getElementById('score-area-guest').addEventListener('mouseenter', () => hoveredElement = 'guest');
        document.getElementById('score-area-guest').addEventListener('mouseleave', () => hoveredElement = null);
        mainTimerArea.addEventListener('mouseenter', () => hoveredElement = 'timer');
        mainTimerArea.addEventListener('mouseleave', () => hoveredElement = null);
        shotClockArea.addEventListener('mouseenter', () => hoveredElement = 'shot');
        shotClockArea.addEventListener('mouseleave', () => hoveredElement = null);
        periodArea.addEventListener('mouseenter', () => hoveredElement = 'period');
        periodArea.addEventListener('mouseleave', () => hoveredElement = null);

        window.addEventListener('keydown', (e) => {
            if (e.repeat) return;
            if (document.activeElement.tagName === 'INPUT' || document.activeElement.tagName === 'TEXTAREA') return;
            if (document.activeElement.id === 'score-area-home' || document.activeElement.id === 'score-area-guest' || document.activeElement.id === 'period-area') return;
            
            if (e.key === 'ArrowUp' || e.key === 'ArrowDown') {
                const delta = e.key === 'ArrowUp' ? 1 : -1;
                if (hoveredElement === 'home') {
                    e.preventDefault();
                    changeScore('home', delta);
                } else if (hoveredElement === 'guest') {
                    e.preventDefault();
                    changeScore('guest', delta);
                } else if (hoveredElement === 'period') {
                    e.preventDefault();
                    changePeriod(delta);
                } else if (hoveredElement === 'timer' && !isMainRunning) {
                    e.preventDefault();
                    mainSeconds = Math.max(0, mainSeconds + delta);
                    updateMainTimerDisplay();
                } else if (hoveredElement === 'shot' && !isShotRunning) {
                    e.preventDefault();
                    shotSeconds = Math.max(0, shotSeconds + delta);
                    updateShotClockDisplay();
                }
            }
        });

        /* ==========================================================================
           作戦盤 ロジック（ご提示コート画像生成・選手配置・手書き描画）
        ========================================================================== */
        let currentTool = 'move';
        let players = [];
        let playerIdCounter = 1;

        const courtContainer = document.getElementById('court-container');
        const playersLayer = document.getElementById('players-layer');
        const canvas = document.getElementById('drawing-canvas');
        const ctx = canvas.getContext('2d');

        // ご提示いただいた「コート理想_3.jpeg」と全く同じレイアウト・少し淡く優しい木目背景の画像を生成
        function generateIdealCourtImage() {
            const c = document.createElement('canvas');
            const W = 1252;
            const H = 800;
            c.width = W;
            c.height = H;
            const g = c.getContext('2d');

            const plankCount = 13;
            const plankH = H / plankCount;
            const plankColors = [
                '#E5BE92', '#DFB688', '#ECC79C', '#D9B082', '#E8C195',
                '#E1B88A', '#ECC79C', '#E4BD90', '#DCB385', '#ECC79C',
                '#D5AA7B', '#E6BE92', '#DFB688'
            ];
            for (let i = 0; i < plankCount; i++) {
                g.fillStyle = plankColors[i % plankColors.length];
                g.fillRect(0, i * plankH, W, plankH + 1);
                g.fillStyle = 'rgba(140, 90, 40, 0.11)';
                g.fillRect(0, i * plankH, W, 1.5);
                g.fillStyle = 'rgba(140, 90, 40, 0.05)';
                for (let j = 0; j < 6; j++) {
                    const rx = ((i * 197 + j * 311) % (W - 180));
                    const rw = 80 + ((i * 53 + j * 97) % 140);
                    const ry = i * plankH + ((j * 13) % (plankH - 6));
                    g.fillRect(rx, ry, rw, 2);
                }
            }

            g.strokeStyle = '#FFFFFF';
            g.lineWidth = 5;
            g.lineCap = 'butt';
            g.lineJoin = 'miter';

            const marginX = 52;
            const marginY = 48;
            const courtW = W - marginX * 2;
            const courtH = H - marginY * 2;
            const midX = W / 2;
            const midY = H / 2;

            g.strokeRect(marginX, marginY, courtW, courtH);

            g.beginPath();
            g.moveTo(midX, marginY);
            g.lineTo(midX, H - marginY);
            g.stroke();

            const centerR = 92;
            g.beginPath();
            g.arc(midX, midY, centerR, 0, Math.PI * 2);
            g.stroke();

            const tickPositions = [midX - 182, midX, midX + 182];
            tickPositions.forEach(tx => {
                g.beginPath();
                g.moveTo(tx, marginY - 12);
                g.lineTo(tx, marginY + 12);
                g.moveTo(tx, H - marginY - 12);
                g.lineTo(tx, H - marginY + 12);
                g.stroke();
            });

            function drawHalfCourt(isLeft) {
                const dir = isLeft ? 1 : -1;
                const baseX = isLeft ? marginX : W - marginX;

                // 3ポイントライン
                const threeStraightLen = 115;
                const threeCornerY = 74;
                const threeTopY = marginY + threeCornerY;
                const threeBotY = H - marginY - threeCornerY;
                const arcStartX = baseX + dir * threeStraightLen;
                const arcCenterX = baseX + dir * 100;
                const arcR = 278;
                const startAngle = Math.asin((threeTopY - midY) / arcR);
                const endAngle = Math.asin((threeBotY - midY) / arcR);

                g.beginPath();
                g.moveTo(baseX, threeTopY);
                g.lineTo(arcStartX, threeTopY);
                if (isLeft) {
                    g.arc(arcCenterX, midY, arcR, startAngle, endAngle, false);
                } else {
                    g.arc(arcCenterX, midY, arcR, Math.PI - startAngle, Math.PI - endAngle, true);
                }
                g.lineTo(baseX, threeBotY);
                g.stroke();

                // 制限区域（台形ペイントエリア）
                const keyLen = 262;
                const ftLineX = baseX + dir * keyLen;
                const keyBaseHalfH = 108;
                const keyTopHalfH = 88;

                g.beginPath();
                g.moveTo(baseX, midY - keyBaseHalfH);
                g.lineTo(ftLineX, midY - keyTopHalfH);
                g.lineTo(ftLineX, midY + keyTopHalfH);
                g.lineTo(baseX, midY + keyBaseHalfH);
                g.stroke();

                // ペイント外のブロック目盛り
                [0.34, 0.50, 0.66, 0.82].forEach(t => {
                    const bx = baseX + dir * (keyLen * t);
                    const byTop = midY - (keyBaseHalfH - (keyBaseHalfH - keyTopHalfH) * t);
                    const byBot = midY + (keyBaseHalfH - (keyBaseHalfH - keyTopHalfH) * t);
                    g.beginPath();
                    g.moveTo(bx, byTop);
                    g.lineTo(bx, byTop - 10);
                    g.moveTo(bx, byBot);
                    g.lineTo(bx, byBot + 10);
                    g.stroke();
                });

                // フリースローサークル
                const ftR = keyTopHalfH;
                g.beginPath();
                if (isLeft) {
                    g.arc(ftLineX, midY, ftR, -Math.PI / 2, Math.PI / 2, false);
                } else {
                    g.arc(ftLineX, midY, ftR, Math.PI / 2, -Math.PI / 2, false);
                }
                g.stroke();

                g.save();
                g.setLineDash([12, 12]);
                g.beginPath();
                if (isLeft) {
                    g.arc(ftLineX, midY, ftR, Math.PI / 2, -Math.PI / 2, false);
                } else {
                    g.arc(ftLineX, midY, ftR, -Math.PI / 2, Math.PI / 2, false);
                }
                g.stroke();
                g.restore();

                // バックボード ＆ リング
                const boardX = baseX + dir * 36;
                const boardHalfH = 34;
                g.beginPath();
                g.moveTo(boardX, midY - boardHalfH);
                g.lineTo(boardX, midY + boardHalfH);
                g.stroke();

                const rimR = 20;
                const rimCenterX = boardX + dir * (rimR + 8);
                g.beginPath();
                g.moveTo(boardX, midY);
                g.lineTo(boardX + dir * 8, midY);
                g.stroke();
                g.beginPath();
                g.arc(rimCenterX, midY, rimR, 0, Math.PI * 2);
                g.stroke();
            }

            drawHalfCourt(true);
            drawHalfCourt(false);

            courtContainer.style.backgroundImage = `url('${c.toDataURL('image/png')}')`;
        }

        function initPlayers() {
            const initialPositions = [
                { type: 'offense', label: '1', x: 35, y: 50 },
                { type: 'offense', label: '2', x: 25, y: 20 },
                { type: 'offense', label: '3', x: 25, y: 80 },
                { type: 'offense', label: '4', x: 15, y: 32 },
                { type: 'offense', label: '5', x: 15, y: 68 },
                { type: 'defense', label: '1', x: 30, y: 50 },
                { type: 'defense', label: '2', x: 21, y: 25 },
                { type: 'defense', label: '3', x: 21, y: 75 },
                { type: 'defense', label: '4', x: 12, y: 36 },
                { type: 'defense', label: '5', x: 12, y: 64 },
                { type: 'ball', label: 'B', x: 37.5, y: 47 }
            ];
            initialPositions.forEach(p => {
                players.push({ id: playerIdCounter++, ...p });
            });
            renderPlayers();
        }

        function addPlayer(type) {
            const sameType = players.filter(p => p.type === type);
            if (sameType.length >= 10) return;
            const nextNum = sameType.length + 1;
            players.push({
                id: playerIdCounter++,
                type: type,
                label: String(nextNum),
                x: type === 'offense' ? 46 : 54,
                y: 50
            });
            renderPlayers();
        }

        function removePlayer(type) {
            const sameType = players.filter(p => p.type === type);
            if (sameType.length === 0) return;
            const last = sameType[sameType.length - 1];
            players = players.filter(p => p.id !== last.id);
            renderPlayers();
        }

        function addBall() {
            const balls = players.filter(p => p.type === 'ball');
            if (balls.length >= 5) return;
            players.push({
                id: playerIdCounter++,
                type: 'ball',
                label: 'B',
                x: 50,
                y: 50
            });
            renderPlayers();
        }

        function removeBall() {
            const balls = players.filter(p => p.type === 'ball');
            if (balls.length === 0) return;
            const last = balls[balls.length - 1];
            players = players.filter(p => p.id !== last.id);
            renderPlayers();
        }

        function renderPlayers() {
            playersLayer.innerHTML = '';
            let offCount = 0;
            let defCount = 0;
            let ballCount = 0;

            players.forEach(p => {
                if (p.type === 'offense') offCount++;
                else if (p.type === 'defense') defCount++;
                else if (p.type === 'ball') ballCount++;

                const el = document.createElement('div');
                el.style.left = `${p.x}%`;
                el.style.top = `${p.y}%`;
                el.style.transform = 'translate(-50%, -50%)';
                el.style.pointerEvents = currentTool === 'move' ? 'auto' : 'none';

                if (p.type === 'ball') {
                    el.className = 'player-token absolute w-6 h-6 md:w-8 md:h-8 rounded-full bg-amber-400 text-white border-2 border-white flex items-center justify-center font-bold text-[10px] md:text-xs shadow-md';
                    el.textContent = 'B';
                } else {
                    el.className = `player-token absolute w-7 h-7 md:w-10 md:h-10 rounded-full flex items-center justify-center font-bold text-xs md:text-base shadow-md ${
                        p.type === 'offense' 
                            ? 'bg-zinc-700 text-white border-2 border-white' 
                            : 'bg-white text-red-500 border-2 border-red-400'
                    }`;
                    el.textContent = p.label;
                }

                makeDraggable(el, p);
                playersLayer.appendChild(el);
            });

            document.getElementById('offense-count').textContent = offCount;
            document.getElementById('defense-count').textContent = defCount;
            document.getElementById('ball-count').textContent = ballCount;
        }

        function makeDraggable(el, playerObj) {
            let isDragging = false;

            const onStart = (e) => {
                if (currentTool !== 'move') return;
                e.stopPropagation();
                isDragging = true;
            };

            const onMove = (e) => {
                if (!isDragging) return;
                const clientX = e.touches ? e.touches[0].clientX : e.clientX;
                const clientY = e.touches ? e.touches[0].clientY : e.clientY;
                const rect = courtContainer.getBoundingClientRect();
                const norm = getNormalizedCoordsInContainer(clientX, clientY, rect);

                let xPercent = norm.x * 100;
                let yPercent = norm.y * 100;

                xPercent = Math.max(2, Math.min(98, xPercent));
                yPercent = Math.max(3, Math.min(97, yPercent));

                playerObj.x = xPercent;
                playerObj.y = yPercent;
                el.style.left = `${xPercent}%`;
                el.style.top = `${yPercent}%`;
            };

            const onEnd = () => {
                isDragging = false;
            };

            el.addEventListener('mousedown', onStart);
            window.addEventListener('mousemove', onMove);
            window.addEventListener('mouseup', onEnd);

            el.addEventListener('touchstart', onStart, { passive: false });
            window.addEventListener('touchmove', onMove, { passive: false });
            window.addEventListener('touchend', onEnd);
        }

        /* ==========================================================================
           手書きキャンバス（ペン ＆ 消しゴム）
        ========================================================================== */
        let isDrawing = false;
        let lastX = 0;
        let lastY = 0;
        let currentPenColor = '#3F3F46'; // デフォルトは少し柔らかなチャコール

        function setPenColor(color) {
            currentPenColor = color;
            const btnBlack = document.getElementById('pen-color-black');
            const btnRed = document.getElementById('pen-color-red');
            if (color === '#3F3F46') {
                btnBlack.classList.add('ring-2', 'ring-offset-1', 'ring-zinc-300');
                btnBlack.classList.remove('ring-1', 'ring-zinc-200');
                btnRed.classList.remove('ring-2', 'ring-offset-1', 'ring-red-300');
                btnRed.classList.add('ring-1', 'ring-zinc-200');
            } else {
                btnRed.classList.add('ring-2', 'ring-offset-1', 'ring-red-300');
                btnRed.classList.remove('ring-1', 'ring-zinc-200');
                btnBlack.classList.remove('ring-2', 'ring-offset-1', 'ring-zinc-300');
                btnBlack.classList.add('ring-1', 'ring-zinc-200');
            }
        }

        function setBoardTool(tool) {
            currentTool = tool;
            ['move', 'pen', 'eraser'].forEach(t => {
                const btn = document.getElementById(`tool-${t}`);
                if (t === tool) {
                    btn.className = 'flex-1 py-1 px-1.5 rounded-md text-[11px] md:text-xs font-medium bg-white text-zinc-800 shadow-sm flex items-center justify-center gap-1';
                } else {
                    btn.className = 'flex-1 py-1 px-1.5 rounded-md text-[11px] md:text-xs font-medium text-zinc-500 hover:text-zinc-800 flex items-center justify-center gap-1';
                }
            });

            canvas.style.cursor = tool === 'move' ? 'default' : (tool === 'pen' ? 'crosshair' : 'cell');
            renderPlayers();
        }

        function resizeCanvas() {
            const logicalW = courtContainer.clientWidth;
            const logicalH = courtContainer.clientHeight;
            if (logicalW === 0 || logicalH === 0) return;

            const tempCanvas = document.createElement('canvas');
            tempCanvas.width = canvas.width;
            tempCanvas.height = canvas.height;
            if (canvas.width > 0 && canvas.height > 0) {
                tempCanvas.getContext('2d').drawImage(canvas, 0, 0);
            }

            canvas.width = logicalW;
            canvas.height = logicalH;

            if (tempCanvas.width > 0 && tempCanvas.height > 0) {
                ctx.drawImage(tempCanvas, 0, 0, tempCanvas.width, tempCanvas.height, 0, 0, canvas.width, canvas.height);
            }
        }

        window.addEventListener('resize', () => {
            if (!document.getElementById('view-board').classList.contains('hidden')) {
                resizeCanvas();
            }
        });

        function getCanvasCoords(e) {
            const rect = canvas.getBoundingClientRect();
            const clientX = e.touches ? e.touches[0].clientX : e.clientX;
            const clientY = e.touches ? e.touches[0].clientY : e.clientY;
            const norm = getNormalizedCoordsInContainer(clientX, clientY, rect);
            return {
                x: norm.x * canvas.width,
                y: norm.y * canvas.height
            };
        }

        function startDrawing(e) {
            if (currentTool === 'move') return;
            isDrawing = true;
            const coords = getCanvasCoords(e);
            lastX = coords.x;
            lastY = coords.y;
        }

        function draw(e) {
            if (!isDrawing || currentTool === 'move') return;
            e.preventDefault();
            const coords = getCanvasCoords(e);

            ctx.lineCap = 'round';
            ctx.lineJoin = 'round';

            if (currentTool === 'pen') {
                ctx.globalCompositeOperation = 'source-over';
                ctx.strokeStyle = currentPenColor;
                ctx.lineWidth = 3;
            } else if (currentTool === 'eraser') {
                ctx.globalCompositeOperation = 'destination-out';
                ctx.lineWidth = 22;
            }

            ctx.beginPath();
            ctx.moveTo(lastX, lastY);
            ctx.lineTo(coords.x, coords.y);
            ctx.stroke();

            lastX = coords.x;
            lastY = coords.y;
        }

        function stopDrawing() {
            isDrawing = false;
        }

        function clearLines() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
        }

        canvas.addEventListener('mousedown', startDrawing);
        canvas.addEventListener('mousemove', draw);
        canvas.addEventListener('mouseup', stopDrawing);
        canvas.addEventListener('mouseout', stopDrawing);

        canvas.addEventListener('touchstart', startDrawing, { passive: false });
        canvas.addEventListener('touchmove', draw, { passive: false });
        canvas.addEventListener('touchend', stopDrawing);

        // 初期セットアップ
        window.addEventListener('DOMContentLoaded', () => {
            initColorPickers();
            generateIdealCourtImage();
            initPlayers();
            resizeCanvas();
            updatePossessionDisplay();

            // 可能なブラウザでは横画面ロックを試行
            if (screen.orientation && screen.orientation.lock) {
                screen.orientation.lock('landscape').catch(() => {});
            }
        });

        // 画面の向き変更時にキャンバスサイズを再計算
        window.addEventListener('orientationchange', () => {
            setTimeout(() => {
                if (!document.getElementById('view-board').classList.contains('hidden')) {
                    resizeCanvas();
                }
            }, 200);
        });
    </script>
</body>
</html>
