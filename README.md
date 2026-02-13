<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>House of CB - Spin to Win</title>
    <style>
        /* --- Fonts --- */
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Lato:wght@400;700;900&display=swap');

        /* --- Reset & Base --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: 'Lato', sans-serif;
            background-color: #5e0b0b; /* Deep Burgundy Base */
            color: #d8b98b; /* Gold/Beige Text */
            overflow-x: hidden;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            /* Subtle floral pattern simulation using gradients */
            background-image: 
                radial-gradient(circle at 20% 30%, #4a0505 0%, transparent 20%),
                radial-gradient(circle at 80% 70%, #4a0505 0%, transparent 20%),
                radial-gradient(circle at 50% 50%, #690e0e 0%, #5e0b0b 100%);
            background-blend-mode: multiply;
        }

        /* --- Top Banner --- */
        .top-banner {
            background-color: #faddde; /* Light Pink */
            color: #5e0b0b;
            text-align: center;
            padding: 10px;
            font-size: 13px;
            font-family: 'Playfair Display', serif;
            letter-spacing: 0.5px;
        }
        .top-banner a {
            color: #5e0b0b;
            text-decoration: underline;
        }

        /* --- Navigation --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 20px;
            position: relative;
            z-index: 10;
        }

        .menu-text {
            font-size: 12px;
            letter-spacing: 1px;
            font-weight: 700;
            text-transform: uppercase;
        }

        .logo {
            text-align: center;
            flex-grow: 1;
        }
        .logo h1 {
            font-family: 'Playfair Display', serif;
            font-size: 26px;
            font-weight: 500;
            letter-spacing: 0px;
            line-height: 1;
        }
        .logo span {
            font-style: italic;
            font-size: 18px;
        }
        .logo .subtitle {
            font-family: 'Lato', sans-serif;
            font-size: 8px;
            letter-spacing: 2px;
            margin-top: 5px;
            text-transform: uppercase;
            color: #d8b98b;
        }

        .nav-icons {
            display: flex;
            gap: 15px;
        }
        .nav-icons svg {
            width: 18px;
            height: 18px;
            fill: none;
            stroke: #d8b98b;
            stroke-width: 1.5;
        }

        /* --- Main Content (Wheel) --- */
        main {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
            padding-bottom: 60px; /* Space for footer text */
            overflow: hidden;
        }

        .wheel-container {
            position: relative;
            width: 320px;
            height: 320px;
            margin: 20px auto;
        }

        /* The spinning part */
        .wheel {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 4px solid #d8b98b;
            position: relative;
            transition: transform 4s cubic-bezier(0.25, 0.1, 0.25, 1);
            /* Background color of the wheel itself */
            background-color: #5e0b0b; 
        }

        /* Wheel Segments (Lines) */
        .segment-line {
            position: absolute;
            top: 0;
            left: 50%;
            width: 2px;
            height: 50%;
            background-color: #d8b98b;
            transform-origin: bottom center;
        }
        
        /* Wheel Dots on Rim */
        .rim-dot {
            position: absolute;
            top: -3px; /* Offset for border */
            left: 50%;
            width: 6px;
            height: 6px;
            background-color: #5e0b0b;
            border: 2px solid #d8b98b;
            border-radius: 50%;
            transform-origin: center 163px; /* Half width + border adjustments */
            z-index: 2;
        }

        /* Segment Text */
        .segment-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform-origin: 0 0;
            text-align: center;
            color: #d8b98b;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 1px;
            width: 130px; /* Length of text from center */
            padding-left: 30px; /* Push text away from center */
            line-height: 1.2;
        }

        /* Specific styling for the 'Free Item' text which is longer */
        .segment-text span {
            display: block;
            font-size: 10px;
            font-weight: 400;
        }

        /* Center Button */
        .center-btn {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 70px;
            height: 70px;
            background-color: #f3e5d0; /* Off-white/Cream */
            border-radius: 50%;
            z-index: 5;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 0 10px rgba(0,0,0,0.3);
        }
        
        .center-logo {
            font-family: 'Playfair Display', serif;
            color: #3e0505;
            font-size: 28px;
            line-height: 0.8;
            text-align: center;
        }
        .center-logo span {
            display: block;
        }

        /* Pointer */
        .pointer {
            position: absolute;
            top: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 30px;
            height: 40px;
            z-index: 6;
            filter: drop-shadow(0 2px 2px rgba(0,0,0,0.3));
        }
        .pointer svg {
            fill: #d8b98b;
        }

        /* --- Footer / Legal Text --- */
        .legal-text {
            text-align: center;
            font-family: 'Playfair Display', serif;
            font-style: italic;
            font-size: 10px;
            color: #d8b98b;
            opacity: 0.8;
            padding: 0 20px;
            line-height: 1.4;
            margin-bottom: 20px;
            max-width: 600px;
        }

        /* --- Floating Icons --- */
        .chat-icon {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background-color: #fff;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            z-index: 20;
            border: 1px solid #ddd;
        }
        .chat-logo {
            font-family: 'Playfair Display', serif;
            color: #000;
            font-size: 20px;
            line-height: 0.8;
            text-align: center;
        }
        /* Tiny text around chat logo */
        .chat-ring-text {
            position: absolute;
            width: 100%;
            height: 100%;
            animation: spin-slow 10s linear infinite;
            background: url("data:image/svg+xml,%3Csvg viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath id='circlePath' d='M 50, 50 m -37, 0 a 37,37 0 1,1 74,0 a 37,37 0 1,1 -74,0' fill='none' /%3E%3Ctext font-size='8' font-family='Arial' letter-spacing='2'%3E%3CtextPath href='%23circlePath'%3EHOUSE OF CB LONDON HOUSE OF CB%3C/textPath%3E%3C/text%3E%3C/svg%3E") no-repeat center center;
            background-size: 85%;
            opacity: 0.5;
        }

        .accessibility-icon {
            position: fixed;
            bottom: 20px;
            right: 90px; /* Left of chat icon */
            background-color: #000;
            width: 30px;
            height: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 4px;
            z-index: 19;
        }
        .accessibility-icon svg {
            fill: #fff;
            width: 20px;
        }

        @keyframes spin-slow {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

    </style>
</head>
<body>

    <div class="top-banner">
        Better in person. <a href="#">Visit our stores.</a>
    </div>

    <nav>
        <div class="menu-text">MENU</div>
        
        <div class="logo">
            <h1>house <span>of</span> cb</h1>
            <div class="subtitle">DESIGNED IN LONDON</div>
        </div>

        <div class="nav-icons">
            <svg viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
            <svg viewBox="0 0 24 24"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>
            <svg viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></svg>
            <svg viewBox="0 0 24 24"><path d="M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"></path><line x1="3" y1="6" x2="21" y2="6"></line><path d="M16 10a4 4 0 0 1-8 0"></path></svg>
        </div>
    </nav>

    <main>
        <div class="wheel-container">
            <div class="pointer">
                <svg viewBox="0 0 30 40">
                    <path d="M15 40 C15 40 30 25 30 15 A15 15 0 0 0 0 15 C0 25 15 40 15 40 Z" />
                </svg>
            </div>

            <div class="wheel" id="wheel">
                <div class="segment-line" style="transform: rotate(0deg);"></div>
                <div class="rim-dot" style="transform: rotate(0deg);"></div>

                <div class="segment-line" style="transform: rotate(45deg);"></div>
                <div class="rim-dot" style="transform: rotate(45deg);"></div>

                <div class="segment-line" style="transform: rotate(90deg);"></div>
                <div class="rim-dot" style="transform: rotate(90deg);"></div>

                <div class="segment-line" style="transform: rotate(135deg);"></div>
                <div class="rim-dot" style="transform: rotate(135deg);"></div>

                <div class="segment-line" style="transform: rotate(180deg);"></div>
                <div class="rim-dot" style="transform: rotate(180deg);"></div>

                <div class="segment-line" style="transform: rotate(225deg);"></div>
                <div class="rim-dot" style="transform: rotate(225deg);"></div>

                <div class="segment-line" style="transform: rotate(270deg);"></div>
                <div class="rim-dot" style="transform: rotate(270deg);"></div>

                <div class="segment-line" style="transform: rotate(315deg);"></div>
                <div class="rim-dot" style="transform: rotate(315deg);"></div>

                <div class="segment-text" style="transform: rotate(22.5deg) translate(0, -50%) rotate(0deg);">
                    $15 OFF
                </div>

                <div class="segment-text" style="transform: rotate(67.5deg) translate(0, -50%) rotate(0deg);">
                    $25 OFF
                </div>

                <div class="segment-text" style="transform: rotate(112.5deg) translate(0, -50%) rotate(0deg);">
                    $50 OFF
                </div>

                <div class="segment-text" style="transform: rotate(157.5deg) translate(0, -50%) rotate(0deg);">
                    FREE ITEM<br><span>UP TO $300</span>
                </div>

                <div class="segment-text" style="transform: rotate(202.5deg) translate(0, -50%) rotate(0deg);">
                    $15 OFF
                </div>

                <div class="segment-text" style="transform: rotate(247.5deg) translate(0, -50%) rotate(0deg);">
                    $25 OFF
                </div>

                <div class="segment-text" style="transform: rotate(292.5deg) translate(0, -50%) rotate(0deg);">
                    $50 OFF
                </div>

                <div class="segment-text" style="transform: rotate(337.5deg) translate(0, -50%) rotate(0deg);">
                    $15 OFF
                </div>

            </div>

            <div class="center-btn" onclick="spinWheel()">
                <div class="center-logo">
                    ho<br>cb
                </div>
            </div>
        </div>
    </main>

    <div class="legal-text">
        Spin to win ends 12.00 AM (UK time) on the 7th of February. All prizes and promotional rewards are valid and must be redeemed by 12.00 AM (UK time) on the 11th of February. Prizes cannot redeemed on Sale items, must be used against purchases totalling to a minimum value of USD180 and Gift Cards cannot be used as a payment method.
    </div>

    <div class="accessibility-icon">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="4" r="2"></circle><path d="M19 13v-2c-1.54.02-3.09-.75-4.07-1.83l-1.29-1.43c-.17-.19-.38-.34-.61-.45-.01 0-.01-.01-.02-.01H9.95c-.35.07-.69.26-.96.54L4.9 11.85c-.32.33-.5.77-.5 1.22 0 .61.34 1.15.86 1.41.25.13.53.19.8.19.53 0 1.04-.24 1.38-.64l1.62-1.89.65 3.23c-.16.71-.4 1.94-.96 4.67-.16.8.36 1.58 1.16 1.74.11.02.22.03.32.03.68 0 1.28-.48 1.42-1.18l.85-4.14 1.15 4.13c.17.62.72 1.04 1.36 1.04.13 0 .26-.02.39-.05.79-.2 1.27-1.01 1.07-1.8l-1.16-4.6c-.05-.2-.11-.46-.22-.72l.45-2.22c.98.54 2.11.83 3.3.83h.06c.83 0 1.5-.67 1.5-1.5S19.83 13 19 13z"></path></svg>
    </div>

    <div class="chat-icon">
        <div class="chat-ring-text"></div>
        <div class="chat-logo">ho<br>cb</div>
    </div>

    <script>
        let hasSpun = false;

        function spinWheel() {
        if (hasSpun) return; 
        hasSpun = true;

        const wheel = document.getElementById('wheel');
        
        // 1. Target Calculation:
        // The "FREE ITEM" segment is centered at 157.5 degrees.
        // To bring 157.5 to the top (0 degrees), we rotate the wheel -157.5 degrees.
        const targetDegrees = 247.5; 
        const fullSpins = 360 * 8; // 8 rotations for excitement
        
        const totalRotation = fullSpins + targetDegrees;

        // Apply the transform
        // We use negative so the wheel spins clockwise visually
        wheel.style.transform = `rotate(-${totalRotation}deg)`;
        
        // Optional: Alert the user after the 4s transition ends
        setTimeout(() => {
            alert("Congratulations! You won a FREE ITEM (Up to $300)!");
        }, 4500); 
	}
    </script>
</body>
</html>
