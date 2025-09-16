# Entero_math_ElkinArteaga.html
Conceptualización de números enteros en operaciones combinadas
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>👑 Reino de los Números - Aventura Matemática</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .screen {
            display: none;
            min-height: 100vh;
            position: relative;
        }
        
        .screen.active { display: block; }
        
        /* PANTALLA DE INICIO */
        .inicio-screen {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
        }
        
        .inicio-card {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            border: 2px solid rgba(255,255,255,0.2);
        }
        
        .titulo-principal {
            font-size: 3em;
            color: #FFD700;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            margin-bottom: 20px;
        }
        
        .personaje-inicio {
            font-size: 8em;
            margin: 20px 0;
            animation: flotar 2s infinite ease-in-out;
        }
        
        @keyframes flotar {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        .btn-principal {
            background: linear-gradient(45deg, #FF6B6B, #4ECDC4);
            border: none;
            color: white;
            padding: 15px 30px;
            font-size: 1.2em;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            margin: 10px;
        }
        
        .btn-principal:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }
        
        /* MAPA DE MUNDOS */
        .mapa-screen {
            padding: 20px;
            text-align: center;
        }
        
        .titulo-mapa {
            color: #FFD700;
            font-size: 2.5em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            margin-bottom: 30px;
        }
        
        .mundos-container {
            display: flex;
            justify-content: center;
            gap: 50px;
            flex-wrap: wrap;
            margin-bottom: 30px;
        }
        
        .mundo-card {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            border: 2px solid rgba(255,255,255,0.2);
            cursor: pointer;
            transition: all 0.3s;
            max-width: 300px;
        }
        
        .mundo-card:hover {
            transform: scale(1.05);
            box-shadow: 0 15px 30px rgba(0,0,0,0.3);
        }
        
        .mundo-icono {
            font-size: 4em;
            margin-bottom: 15px;
        }
        
        .mundo-titulo {
            color: white;
            font-size: 1.5em;
            margin-bottom: 10px;
        }
        
        .mundo-descripcion {
            color: rgba(255,255,255,0.8);
            font-size: 1em;
        }
        
        /* MAPA DE NIVELES */
        .niveles-screen {
            padding: 20px;
        }
        
        .niveles-header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .mundo-actual {
            color: #FFD700;
            font-size: 2em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
        
        .niveles-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            max-width: 1000px;
            margin: 0 auto;
        }
        
        .nivel-card {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 25px;
            border: 2px solid rgba(255,255,255,0.2);
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        
        .nivel-card:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }
        
        .nivel-monstruo {
            font-size: 4em;
            margin-bottom: 15px;
            display: block;
        }
        
        .nivel-nombre {
            color: white;
            font-size: 1.3em;
            margin-bottom: 10px;
            font-weight: bold;
        }
        
        .nivel-descripcion {
            color: rgba(255,255,255,0.8);
            font-size: 0.9em;
        }
        
        .btn-volver {
            background: rgba(255,255,255,0.2);
            border: 1px solid rgba(255,255,255,0.3);
            color: white;
            padding: 10px 20px;
            border-radius: 15px;
            cursor: pointer;
            margin: 20px;
            font-size: 1em;
        }
        
        .btn-volver:hover {
            background: rgba(255,255,255,0.3);
        }
        
        /* BATALLA */
        .batalla-screen {
            padding: 20px;
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            min-height: 100vh;
        }
        
        .batalla-header {
            text-align: center;
            margin-bottom: 20px;
        }
        
        .monstruo-nombre {
            color: #e74c3c;
            font-size: 2em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            margin-bottom: 10px;
        }
        
        .campo-batalla {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 30px 0;
            min-height: 200px;
        }
        
        .mago, .monstruo {
            text-align: center;
            flex: 1;
        }
        
        .mago-sprite, .monstruo-sprite {
            font-size: 6em;
            margin: 10px;
            transition: all 0.5s;
        }
        
        .personaje-nombre {
            color: white;
            font-size: 1.2em;
            margin-bottom: 10px;
        }
        
        .barra-vida {
            background: rgba(255,255,255,0.2);
            border-radius: 10px;
            height: 20px;
            margin: 10px auto;
            max-width: 200px;
            overflow: hidden;
        }
        
        .vida-actual {
            height: 100%;
            border-radius: 10px;
            transition: width 0.5s;
        }
        
        .vida-mago { background: linear-gradient(45deg, #3498db, #2980b9); }
        .vida-monstruo { background: linear-gradient(45deg, #e74c3c, #c0392b); }
        
        .ejercicio-panel {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            margin: 20px auto;
            max-width: 600px;
            border: 2px solid rgba(255,255,255,0.2);
        }
        
        .ejercicio-texto {
            color: white;
            font-size: 2em;
            margin-bottom: 20px;
            font-weight: bold;
        }
        
        .progreso-batalla {
            color: rgba(255,255,255,0.8);
            margin-bottom: 20px;
        }
        
        .respuesta-contenedor {
            display: flex;
            gap: 20px;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
        }
        
        .input-respuesta {
            padding: 15px 20px;
            font-size: 1.5em;
            border: none;
            border-radius: 10px;
            text-align: center;
            background: rgba(255,255,255,0.9);
            max-width: 150px;
        }
        
        .btn-lanzar-hechizo {
            background: linear-gradient(45deg, #FF6B6B, #4ECDC4);
            border: none;
            color: white;
            padding: 15px 25px;
            font-size: 1.2em;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
        }
        
        .btn-lanzar-hechizo:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }
        
        /* EFECTOS Y ANIMACIONES */
        .ataque-mago {
            animation: ataqueAnimacion 1s;
        }
        
        .dano-monstruo {
            animation: danoAnimacion 1s;
            filter: brightness(0.5);
        }
        
        .contraataque-monstruo {
            animation: contraataqueAnimacion 1s;
        }
        
        .dano-mago {
            animation: danoAnimacion 1s;
            filter: brightness(0.5);
        }
        
        @keyframes ataqueAnimacion {
            0% { transform: scale(1) rotate(0deg); }
            25% { transform: scale(1.2) rotate(5deg); }
            50% { transform: scale(1.1) rotate(-5deg); }
            75% { transform: scale(1.2) rotate(5deg); }
            100% { transform: scale(1) rotate(0deg); }
        }
        
        @keyframes danoAnimacion {
            0% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            50% { transform: translateX(10px); }
            75% { transform: translateX(-5px); }
            100% { transform: translateX(0); }
        }
        
        @keyframes contraataqueAnimacion {
            0% { transform: scale(1); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }
        
        .hechizo-proyectil {
            position: absolute;
            font-size: 2.5em;
            animation: volarHechizo 1s linear;
            pointer-events: none;
            z-index: 100;
        }
        
        .proyectil-fuego {
            animation: volarFuego 1s linear;
        }
        
        .proyectil-viento {
            animation: volarViento 1s linear;
        }
        
        @keyframes volarFuego {
            0% {
                left: 20%;
                top: 40%;
                transform: scale(1) rotate(0deg);
                filter: brightness(1);
            }
            50% {
                filter: brightness(1.5);
                transform: scale(1.3) rotate(180deg);
            }
            100% {
                left: 75%;
                top: 40%;
                transform: scale(1.8) rotate(360deg);
                filter: brightness(2);
            }
        }
        
        @keyframes volarViento {
            0% {
                left: 20%;
                top: 40%;
                transform: scale(1);
                opacity: 1;
            }
            30% {
                transform: scale(1.2);
                opacity: 0.8;
            }
            70% {
                left: 60%;
                transform: scale(0.8);
                opacity: 0.4;
            }
            100% {
                left: 75%;
                top: 40%;
                transform: scale(0.3);
                opacity: 0;
            }
        }
        
        .explosion {
            position: absolute;
            font-size: 3em;
            animation: explotar 0.8s;
            pointer-events: none;
            z-index: 100;
        }
        
        @keyframes explotar {
            0% {
                transform: scale(0);
                opacity: 1;
            }
            50% {
                transform: scale(1.5);
                opacity: 1;
            }
            100% {
                transform: scale(2);
                opacity: 0;
            }
        }
        
        .particulas-magicas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .particula {
            position: absolute;
            width: 8px;
            height: 8px;
            background: #FFD700;
            border-radius: 50%;
            animation: floatMagic 4s infinite;
        }
        
        @keyframes floatMagic {
            0% {
                transform: translateY(100vh) translateX(0) rotate(0deg);
                opacity: 0;
            }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% {
                transform: translateY(-100px) translateX(100px) rotate(360deg);
                opacity: 0;
            }
        }
        
        .mensaje-final {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0,0,0,0.95);
            color: white;
            padding: 40px;
            border-radius: 25px;
            text-align: center;
            z-index: 300;
            border: 4px solid #FFD700;
            animation: aparecerFinal 1s ease-out;
        }
        
        @keyframes aparecerFinal {
            0% { 
                transform: translate(-50%, -50%) scale(0); 
                opacity: 0; 
            }
            100% { 
                transform: translate(-50%, -50%) scale(1); 
                opacity: 1; 
            }
        }
        
        .oculto { display: none !important; }
        
        /* RESPONSIVE */
        @media (max-width: 768px) {
            .titulo-principal { font-size: 2em; }
            .personaje-inicio { font-size: 6em; }
            .mundos-container { flex-direction: column; align-items: center; }
            .campo-batalla {
                flex-direction: column;
                justify-content: space-around;
                min-height: 300px;
            }
            .mago-sprite, .monstruo-sprite { font-size: 4em; }
            .ejercicio-texto { font-size: 1.5em; }
            .respuesta-contenedor { flex-direction: column; gap: 15px; }
            .input-respuesta { max-width: 200px; }
        }
    </style>
</head>
<body>
    <!-- Partículas mágicas -->
    <div class="particulas-magicas" id="particulasMagicas"></div>

    <!-- Pantalla de Inicio -->
    <div id="inicio" class="screen active inicio-screen">
        <div class="inicio-card">
            <h1 class="titulo-principal">👑 REINO DE LOS NÚMEROS</h1>
            <div class="personaje-inicio">🧙‍♂️</div>
            <h2 style="color: #FFD700; margin-bottom: 30px;">La Gran Aventura Matemática</h2>
            <p style="font-size: 1.2em; margin-bottom: 30px; color: white;">
                ¡Embárcate en una épica aventura para salvar el Reino de los Números!<br>
                Usa la magia de las matemáticas para derrotar a los monstruos del caos.
            </p>
            <button class="btn-principal" onclick="iniciarJuego()">🚀 COMENZAR AVENTURA</button>
            <button class="btn-principal" onclick="mostrarInstrucciones()">📜 INSTRUCCIONES</button>
        </div>
    </div>

    <!-- Pantalla de Mapa de Mundos -->
    <div id="mapaMundos" class="screen mapa-screen">
        <h1 class="titulo-mapa">🗺️ ELIGE TU DESTINO</h1>
        
        <div class="mundos-container">
            <div class="mundo-card" onclick="irAMundo(1)">
                <div class="mundo-icono">🌟</div>
                <div class="mundo-titulo">Mundo 1: Valle Místico</div>
                <div class="mundo-descripcion">
                    Operaciones básicas con números enteros<br>
                    Niveles 1-4: Sumas, restas y primeras batallas
                </div>
            </div>
            
            <div class="mundo-card" onclick="irAMundo(2)">
                <div class="mundo-icono">🌙</div>
                <div class="mundo-titulo">Mundo 2: Reino Sombrío</div>
                <div class="mundo-descripcion">
                    Operaciones avanzadas con números enteros<br>
                    Niveles 5-8: Multiplicaciones, divisiones y combos
                </div>
            </div>
        </div>
        
        <button class="btn-volver" onclick="volverInicio()">🏠 Volver al Inicio</button>
    </div>

    <!-- Pantalla de Mapa de Niveles -->
    <div id="mapaNiveles" class="screen niveles-screen">
        <div class="niveles-header">
            <h1 id="mundoActual" class="mundo-actual">🌟 VALLE MÍSTICO</h1>
            <p style="color: white; font-size: 1.2em;">Todos los niveles están disponibles - ¡Elige tu reto!</p>
        </div>
        
        <div class="niveles-grid" id="nivelesGrid">
            <!-- Los niveles se cargan dinámicamente -->
        </div>
        
        <div style="text-align: center; margin-top: 30px;">
            <button class="btn-volver" onclick="volverMapa()">🗺️ Cambiar Mundo</button>
        </div>
    </div>

    <!-- Pantalla de Batalla -->
    <div id="batalla" class="screen batalla-screen">
        <div class="batalla-header">
            <h1 id="monstruoNombre" class="monstruo-nombre">🐺 LOBO DEL CAOS</h1>
            <div class="progreso-batalla" id="progresoBatalla">
                Aciertos: 0/15 | Intentos: 0/20
            </div>
        </div>
        
        <div class="campo-batalla">
            <div class="mago">
                <div class="personaje-nombre">🧙‍♂️ Mago</div>
                <div id="magoSprite" class="mago-sprite">🧙‍♂️</div>
                <div class="barra-vida">
                    <div id="vidaMago" class="vida-actual vida-mago" style="width: 100%"></div>
                </div>
            </div>
            
            <div class="monstruo">
                <div class="personaje-nombre" id="nombreMonstruo">🐺 Lobo del Caos</div>
                <div id="monstruoSprite" class="monstruo-sprite">🐺</div>
                <div class="barra-vida">
                    <div id="vidaMonstruo" class="vida-actual vida-monstruo" style="width: 100%"></div>
                </div>
            </div>
        </div>
        
        <div class="ejercicio-panel">
            <div id="ejercicioTexto" class="ejercicio-texto">(-5) + 8 = ?</div>
            
            <div class="respuesta-contenedor">
                <input type="number" id="respuestaInput" class="input-respuesta" 
                       placeholder="?" onkeypress="if(event.key==='Enter') lanzarHechizo()">
                <button id="btnLanzarHechizo" class="btn-lanzar-hechizo" onclick="lanzarHechizo()">
                    ⚡ LANZAR HECHIZO
                </button>
            </div>
        </div>
        
        <div style="text-align: center; margin-top: 20px;">
            <button class="btn-volver" onclick="abandonarBatalla()">🏃‍♂️ Abandonar Batalla</button>
        </div>
    </div>

    <script>
        // Variables globales del juego SIMPLIFICADAS
        let mundoActual = 1;
        let batalla = {
            aciertos: 0,
            intentos: 0,
            ejercicioActual: 0,
            vidaMago: 100,
            vidaMonstruo: 100,
            monstruoActual: null,
            ejercicios: [],
            enBatalla: false
        };

        // Datos de monstruos por nivel
        const monstruos = {
            1: { nombre: "Lobo del Caos", sprite: "🐺", descripcion: "Suma y resta básica" },
            2: { nombre: "Búho Corrupto", sprite: "🦉", descripcion: "Suma y resta intermedia" },
            3: { nombre: "Fantasma de Números", sprite: "👻", descripcion: "Suma y resta avanzada" },
            4: { nombre: "Dragón Menor", sprite: "🐲", descripcion: "Combinación de operaciones" },
            5: { nombre: "Yeti Helado", sprite: "🥶", descripcion: "Multiplicación básica" },
            6: { nombre: "Robot Defectuoso", sprite: "🤖", descripcion: "División básica" },
            7: { nombre: "Comandante Espacial", sprite: "🚀", descripcion: "Operaciones combinadas" },
            8: { nombre: "Emperador Final", sprite: "👹", descripcion: "Máximo desafío" }
        };

        // Generador de ejercicios por nivel - NÚMEROS ENTEROS
        function generarEjercicios(nivel) {
            const ejercicios = [];
            
            switch(nivel) {
                case 1: // Sumas básicas con enteros
                    ejercicios.push(
                        { texto: "(-5) + 8 = ?", respuesta: 3 },
                        { texto: "12 + (-7) = ?", respuesta: 5 },
                        { texto: "(-9) + (-4) = ?", respuesta: -13 },
                        { texto: "15 + (-6) = ?", respuesta: 9 },
                        { texto: "(-8) + 13 = ?", respuesta: 5 },
                        { texto: "7 + (-12) = ?", respuesta: -5 },
                        { texto: "(-3) + (-9) = ?", respuesta: -12 },
                        { texto: "18 + (-5) = ?", respuesta: 13 },
                        { texto: "(-14) + 6 = ?", respuesta: -8 },
                        { texto: "4 + (-11) = ?", respuesta: -7 },
                        { texto: "(-7) + (-8) = ?", respuesta: -15 },
                        { texto: "20 + (-9) = ?", respuesta: 11 },
                        { texto: "(-12) + 15 = ?", respuesta: 3 },
                        { texto: "8 + (-8) = ?", respuesta: 0 },
                        { texto: "(-6) + (-7) = ?", respuesta: -13 },
                        { texto: "17 + (-4) = ?", respuesta: 13 },
                        { texto: "(-13) + 9 = ?", respuesta: -4 },
                        { texto: "5 + (-14) = ?", respuesta: -9 },
                        { texto: "(-10) + (-3) = ?", respuesta: -13 },
                        { texto: "16 + (-7) = ?", respuesta: 9 }
                    );
                    break;
                    
                case 3: // Sumas y restas combinadas
                    ejercicios.push(
                        { texto: "(-8) + 12 - 5 = ?", respuesta: -1 },
                        { texto: "15 - (-6) + 3 = ?", respuesta: 24 },
                        { texto: "(-12) + 7 - (-4) = ?", respuesta: -1 },
                        { texto: "9 - 14 + (-3) = ?", respuesta: -8 },
                        { texto: "(-7) + (-5) + 13 = ?", respuesta: 1 },
                        { texto: "18 - (-9) - 6 = ?", respuesta: 21 },
                        { texto: "(-11) + 15 - 8 = ?", respuesta: -4 },
                        { texto: "6 - (-12) + (-7) = ?", respuesta: 11 },
                        { texto: "(-9) - 4 + 16 = ?", respuesta: 3 },
                        { texto: "13 + (-8) - (-5) = ?", respuesta: 10 },
                        { texto: "(-14) + 9 + 7 = ?", respuesta: 2 },
                        { texto: "10 - (-3) - 8 = ?", respuesta: 5 },
                        { texto: "(-6) + (-9) + 18 = ?", respuesta: 3 },
                        { texto: "7 - 12 + (-4) = ?", respuesta: -9 },
                        { texto: "(-13) + 8 - (-6) = ?", respuesta: 1 },
                        { texto: "14 + (-7) - 9 = ?", respuesta: -2 },
                        { texto: "(-5) - (-11) + 3 = ?", respuesta: 9 },
                        { texto: "8 - 15 + (-2) = ?", respuesta: -9 },
                        { texto: "(-10) + 14 - 6 = ?", respuesta: -2 },
                        { texto: "12 - (-4) + (-8) = ?", respuesta: 8 }
                    );
                    break;
                    
                case 4: // Operaciones mixtas básicas
                    ejercicios.push(
                        { texto: "(-3) × 4 = ?", respuesta: -12 },
                        { texto: "15 ÷ (-3) = ?", respuesta: -5 },
                        { texto: "(-8) × (-2) = ?", respuesta: 16 },
                        { texto: "(-24) ÷ 6 = ?", respuesta: -4 },
                        { texto: "7 × (-5) = ?", respuesta: -35 },
                        { texto: "(-18) ÷ (-3) = ?", respuesta: 6 },
                        { texto: "(-6) × 9 = ?", respuesta: -54 },
                        { texto: "28 ÷ (-7) = ?", respuesta: -4 },
                        { texto: "(-4) × (-8) = ?", respuesta: 32 },
                        { texto: "(-35) ÷ 5 = ?", respuesta: -7 },
                        { texto: "12 × (-3) = ?", respuesta: -36 },
                        { texto: "(-42) ÷ (-6) = ?", respuesta: 7 },
                        { texto: "(-9) × 7 = ?", respuesta: -63 },
                        { texto: "45 ÷ (-9) = ?", respuesta: -5 },
                        { texto: "(-5) × (-6) = ?", respuesta: 30 },
                        { texto: "(-30) ÷ 10 = ?", respuesta: -3 },
                        { texto: "8 × (-4) = ?", respuesta: -32 },
                        { texto: "(-21) ÷ (-7) = ?", respuesta: 3 },
                        { texto: "(-11) × 3 = ?", respuesta: -33 },
                        { texto: "36 ÷ (-4) = ?", respuesta: -9 }
                    );
                    break;
                    
                case 5: // Multiplicaciones avanzadas
                    ejercicios.push(
                        { texto: "(-7) × (-8) = ?", respuesta: 56 },
                        { texto: "13 × (-4) = ?", respuesta: -52 },
                        { texto: "(-12) × 5 = ?", respuesta: -60 },
                        { texto: "(-9) × (-11) = ?", respuesta: 99 },
                        { texto: "15 × (-6) = ?", respuesta: -90 },
                        { texto: "(-14) × 7 = ?", respuesta: -98 },
                        { texto: "(-8) × (-9) = ?", respuesta: 72 },
                        { texto: "16 × (-5) = ?", respuesta: -80 },
                        { texto: "(-13) × 6 = ?", respuesta: -78 },
                        { texto: "(-10) × (-12) = ?", respuesta: 120 },
                        { texto: "18 × (-3) = ?", respuesta: -54 },
                        { texto: "(-15) × 4 = ?", respuesta: -60 },
                        { texto: "(-7) × (-13) = ?", respuesta: 91 },
                        { texto: "14 × (-8) = ?", respuesta: -112 },
                        { texto: "(-11) × 9 = ?", respuesta: -99 },
                        { texto: "(-6) × (-15) = ?", respuesta: 90 },
                        { texto: "17 × (-4) = ?", respuesta: -68 },
                        { texto: "(-16) × 3 = ?", respuesta: -48 },
                        { texto: "(-9) × (-14) = ?", respuesta: 126 },
                        { texto: "19 × (-5) = ?", respuesta: -95 }
                    );
                    break;
                    
                case 6: // Divisiones avanzadas
                    ejercicios.push(
                        { texto: "(-84) ÷ 12 = ?", respuesta: -7 },
                        { texto: "96 ÷ (-8) = ?", respuesta: -12 },
                        { texto: "(-72) ÷ (-9) = ?", respuesta: 8 },
                        { texto: "108 ÷ (-6) = ?", respuesta: -18 },
                        { texto: "(-91) ÷ 7 = ?", respuesta: -13 },
                        { texto: "(-126) ÷ (-14) = ?", respuesta: 9 },
                        { texto: "144 ÷ (-12) = ?", respuesta: -12 },
                        { texto: "(-105) ÷ 15 = ?", respuesta: -7 },
                        { texto: "(-132) ÷ (-11) = ?", respuesta: 12 },
                        { texto: "156 ÷ (-13) = ?", respuesta: -12 },
                        { texto: "(-117) ÷ 9 = ?", respuesta: -13 },
                        { texto: "(-168) ÷ (-8) = ?", respuesta: 21 },
                        { texto: "180 ÷ (-15) = ?", respuesta: -12 },
                        { texto: "(-154) ÷ 14 = ?", respuesta: -11 },
                        { texto: "(-196) ÷ (-7) = ?", respuesta: 28 },
                        { texto: "225 ÷ (-9) = ?", respuesta: -25 },
                        { texto: "(-192) ÷ 16 = ?", respuesta: -12 },
                        { texto: "(-210) ÷ (-10) = ?", respuesta: 21 },
                        { texto: "240 ÷ (-12) = ?", respuesta: -20 },
                        { texto: "(-273) ÷ 13 = ?", respuesta: -21 }
                    );
                    break;
                    
                case 7: // Operaciones combinadas complejas
                    ejercicios.push(
                        { texto: "(-6) × 4 + 15 = ?", respuesta: -9 },
                        { texto: "18 - (-3) × 5 = ?", respuesta: 33 },
                        { texto: "(-12) ÷ 3 + 8 = ?", respuesta: 4 },
                        { texto: "7 × (-4) - (-6) = ?", respuesta: -22 },
                        { texto: "(-20) ÷ (-5) + 12 = ?", respuesta: 16 },
                        { texto: "15 + (-8) × 3 = ?", respuesta: -9 },
                        { texto: "(-24) ÷ 6 - 9 = ?", respuesta: -13 },
                        { texto: "9 - (-5) × 4 = ?", respuesta: 29 },
                        { texto: "(-7) × (-3) + 4 = ?", respuesta: 25 },
                        { texto: "36 ÷ (-4) + 15 = ?", respuesta: 6 },
                        { texto: "(-8) + 6 × (-2) = ?", respuesta: -20 },
                        { texto: "14 × (-2) + 30 = ?", respuesta: 2 },
                        { texto: "(-45) ÷ 9 + 18 = ?", respuesta: 13 },
                        { texto: "12 - (-4) × 6 = ?", respuesta: 36 },
                        { texto: "(-9) × 5 - (-7) = ?", respuesta: -38 },
                        { texto: "48 ÷ (-8) + 25 = ?", respuesta: 19 },
                        { texto: "(-13) + 7 × (-3) = ?", respuesta: -34 },
                        { texto: "16 × (-3) + 42 = ?", respuesta: -6 },
                        { texto: "(-63) ÷ (-7) - 4 = ?", respuesta: 5 },
                        { texto: "11 - (-6) × 4 = ?", respuesta: 35 }
                    );
                    break;
                    
                case 8: // Desafío final - máxima complejidad
                    ejercicios.push(
                        { texto: "(-8) × 3 + (-4) × 5 = ?", respuesta: -44 },
                        { texto: "72 ÷ (-9) - 6 × 2 = ?", respuesta: -20 },
                        { texto: "(-15) + (-7) × (-4) = ?", respuesta: 13 },
                        { texto: "48 ÷ (-6) + (-9) × 3 = ?", respuesta: -35 },
                        { texto: "(-12) × (-5) - 8 × 7 = ?", respuesta: 4 },
                        { texto: "84 ÷ (-7) + (-3) × (-8) = ?", respuesta: 12 },
                        { texto: "(-9) × 6 + 63 ÷ (-9) = ?", respuesta: -61 },
                        { texto: "(-56) ÷ 8 - (-4) × 5 = ?", respuesta: 13 },
                        { texto: "11 × (-6) + (-45) ÷ 5 = ?", respuesta: -75 },
                        { texto: "(-36) ÷ (-4) + 7 × (-3) = ?", respuesta: -12 },
                        { texto: "(-13) × 4 - (-28) ÷ 7 = ?", respuesta: -48 },
                        { texto: "90 ÷ (-10) + (-8) × (-6) = ?", respuesta: 39 },
                        { texto: "(-14) × (-3) - 54 ÷ 9 = ?", respuesta: 36 },
                        { texto: "(-77) ÷ 11 + 15 × (-2) = ?", respuesta: -37 },
                        { texto: "12 × (-7) + (-96) ÷ (-8) = ?", respuesta: -72 },
                        { texto: "(-18) × 5 - (-42) ÷ 6 = ?", respuesta: -83 },
                        { texto: "120 ÷ (-15) + (-9) × (-7) = ?", respuesta: 55 },
                        { texto: "(-16) × (-4) + 75 ÷ (-5) = ?", respuesta: 49 },
                        { texto: "(-11) × 8 - (-132) ÷ 12 = ?", respuesta: -77 },
                        { texto: "144 ÷ (-12) + (-13) × (-6) = ?", respuesta: 66 }
                    );
                    break;
            }
            
            // Barajar ejercicios para variedad
            return ejercicios.sort(() => Math.random() - 0.5);
        }

        // Funciones de navegación
        function iniciarJuego() {
            crearParticulasMagicas();
            mostrarPantalla('mapaMundos');
        }

        function mostrarInstrucciones() {
            alert(`🎮 INSTRUCCIONES DEL JUEGO:

📚 OBJETIVO: Derrotar a 8 poderosos monstruos usando matemáticas

⚔️ COMBATE:
• Resuelve ejercicios de números enteros
• Necesitas 15 aciertos de máximo 20 intentos
• Respuesta correcta: 🔥 Bola de fuego daña al monstruo
• Respuesta incorrecta: 💨 Bola de viento, el monstruo contraataca

🎯 NIVELES:
• Nivel 1-3: Sumas y restas básicas
• Nivel 4: Operaciones mixtas básicas  
• Nivel 5-6: Multiplicaciones y divisiones
• Nivel 7-8: Operaciones combinadas complejas

🏆 TODOS LOS NIVELES ESTÁN DESBLOQUEADOS
¡Puedes elegir cualquier desafío!

¡Que comience la aventura! 🧙‍♂️✨`);
        }

        function volverInicio() {
            mostrarPantalla('inicio');
        }

        function irAMundo(mundo) {
            mundoActual = mundo;
            cargarNiveles(mundo);
            mostrarPantalla('mapaNiveles');
        }

        function volverMapa() {
            mostrarPantalla('mapaMundos');
        }

        function mostrarPantalla(idPantalla) {
            document.querySelectorAll('.screen').forEach(screen => {
                screen.classList.remove('active');
            });
            document.getElementById(idPantalla).classList.add('active');
        }

        // Cargar niveles por mundo
        function cargarNiveles(mundo) {
            const mundoTitulos = {
                1: "🌟 VALLE MÍSTICO",
                2: "🌙 REINO SOMBRÍO"
            };
            
            document.getElementById('mundoActual').textContent = mundoTitulos[mundo];
            
            const nivelesGrid = document.getElementById('nivelesGrid');
            nivelesGrid.innerHTML = '';
            
            const nivelesDelMundo = mundo === 1 ? [1,2,3,4] : [5,6,7,8];
            
            nivelesDelMundo.forEach(nivel => {
                const monstruo = monstruos[nivel];
                const nivelCard = document.createElement('div');
                nivelCard.className = 'nivel-card';
                nivelCard.onclick = () => iniciarBatalla(nivel);
                
                nivelCard.innerHTML = `
                    <div class="nivel-monstruo">${monstruo.sprite}</div>
                    <div class="nivel-nombre">Nivel ${nivel}: ${monstruo.nombre}</div>
                    <div class="nivel-descripcion">${monstruo.descripcion}</div>
                `;
                
                nivelesGrid.appendChild(nivelCard);
            });
        }

        // Iniciar batalla
        function iniciarBatalla(nivel) {
            // Resetear estado de batalla completamente
            batalla = {
                aciertos: 0,
                intentos: 0,
                ejercicioActual: 0,
                vidaMago: 100,
                vidaMonstruo: 100,
                monstruoActual: monstruos[nivel],
                ejercicios: generarEjercicios(nivel),
                enBatalla: true
            };
            
            // Configurar interfaz de batalla
            const monstruo = batalla.monstruoActual;
            document.getElementById('monstruoNombre').textContent = `${monstruo.sprite} ${monstruo.nombre}`;
            document.getElementById('nombreMonstruo').textContent = `${monstruo.sprite} ${monstruo.nombre}`;
            document.getElementById('monstruoSprite').textContent = monstruo.sprite;
            
            // Resetear barras de vida
            document.getElementById('vidaMago').style.width = '100%';
            document.getElementById('vidaMonstruo').style.width = '100%';
            
            // Mostrar primer ejercicio
            mostrarSiguienteEjercicio();
            
            // Ir a pantalla de batalla
            mostrarPantalla('batalla');
            
            // Enfocar input
            setTimeout(() => {
                document.getElementById('respuestaInput').focus();
            }, 100);
        }

        // Mostrar siguiente ejercicio
        function mostrarSiguienteEjercicio() {
            if (batalla.ejercicioActual < batalla.ejercicios.length) {
                const ejercicio = batalla.ejercicios[batalla.ejercicioActual];
                document.getElementById('ejercicioTexto').textContent = ejercicio.texto;
                batalla.ejercicioActual++;
                
                if (batalla.ejercicioActual >= batalla.ejercicios.length) {
                    // Regenerar ejercicios si se agotaron
                    const nivelActual = Object.keys(monstruos).find(key => 
                        monstruos[key] === batalla.monstruoActual
                    );
                    batalla.ejercicios = generarEjercicios(parseInt(nivelActual));
                    batalla.ejercicioActual = 0;
                }
            }
        }

        // Efectos de combate
        function ataqueExitoso() {
            // Daño al monstruo
            batalla.vidaMonstruo = Math.max(0, batalla.vidaMonstruo - (100/15));
            document.getElementById('vidaMonstruo').style.width = batalla.vidaMonstruo + '%';
            
            // Animación de daño al monstruo
            const monstruoSprite = document.getElementById('monstruoSprite');
            monstruoSprite.classList.add('dano-monstruo');
            
            setTimeout(() => {
                monstruoSprite.classList.remove('dano-monstruo');
                mostrarSiguienteEjercicio();
            }, 1500);
        }

        function ataqueContraproducente() {
            // Contraataque del monstruo
            batalla.vidaMago = Math.max(0, batalla.vidaMago - 16.67);
            document.getElementById('vidaMago').style.width = batalla.vidaMago + '%';
            
            // Animaciones
            const monstruoSprite = document.getElementById('monstruoSprite');
            const magoSprite = document.getElementById('magoSprite');
            
            monstruoSprite.classList.add('contraataque-monstruo');
            
            setTimeout(() => {
                magoSprite.classList.add('dano-mago');
                
                setTimeout(() => {
                    monstruoSprite.classList.remove('contraataque-monstruo');
                    magoSprite.classList.remove('dano-mago');
                    mostrarSiguienteEjercicio();
                }, 1000);
            }, 500);
        }

        // Verificar fin de batalla
        function verificarFinBatalla() {
            if (batalla.aciertos >= 15) {
                // VICTORIA
                setTimeout(() => {
                    mostrarVictoria();
                }, 500);
            } else if (batalla.intentos >= 20) {
                // DERROTA
                setTimeout(() => {
                    mostrarDerrota();
                }, 500);
            }
        }

        function mostrarVictoria() {
            const mensaje = document.createElement('div');
            mensaje.className = 'mensaje-final';
            mensaje.innerHTML = `
                <h2>🎉 ¡VICTORIA ÉPICA! 🎉</h2>
                <p style="font-size: 1.5em; margin: 20px 0;">${batalla.monstruoActual.sprite}</p>
                <p><strong>${batalla.monstruoActual.nombre}</strong> ha sido derrotado!</p>
                <p>Aciertos: ${batalla.aciertos}/15</p>
                <p>Intentos: ${batalla.intentos}/20</p>
                <button class="btn-principal" onclick="cerrarMensaje()">✨ ¡Continuar Aventura! ✨</button>
            `;
            document.body.appendChild(mensaje);
        }

        function mostrarDerrota() {
            const mensaje = document.createElement('div');
            mensaje.className = 'mensaje-final';
            mensaje.innerHTML = `
                <h2>😔 Derrota Temporal</h2>
                <p style="font-size: 1.5em; margin: 20px 0;">${batalla.monstruoActual.sprite}</p>
                <p><strong>${batalla.monstruoActual.nombre}</strong> fue demasiado poderoso esta vez...</p>
                <p>Aciertos: ${batalla.aciertos}/15</p>
                <p>Intentos: ${batalla.intentos}/20</p>
                <p style="color: #FFD700; margin-top: 20px;">¡Pero puedes intentarlo de nuevo!</p>
                <button class="btn-principal" onclick="cerrarMensaje()">🔄 ¡Reintentar!</button>
            `;
            document.body.appendChild(mensaje);
        }

        function cerrarMensaje() {
            const mensaje = document.querySelector('.mensaje-final');
            if (mensaje) {
                document.body.removeChild(mensaje);
            }
            volverMapa();
        }

        function abandonarBatalla() {
            batalla.enBatalla = false;
            volverMapa();
        }

        // Crear explosiones
        function crearExplosion(emoji, left, top) {
            const explosion = document.createElement('div');
            explosion.textContent = emoji;
            explosion.className = 'explosion';
            explosion.style.left = left;
            explosion.style.top = top;
            
            document.body.appendChild(explosion);
            
            setTimeout(() => {
                document.body.removeChild(explosion);
            }, 800);
        }

        // Crear partículas mágicas de fondo
        function crearParticulasMagicas() {
            const contenedor = document.getElementById('particulasMagicas');
            
            setInterval(() => {
                const particula = document.createElement('div');
                particula.className = 'particula';
                particula.style.left = Math.random() * 100 + '%';
                particula.style.animationDuration = (Math.random() * 3 + 2) + 's';
                particula.style.animationDelay = (Math.random() * 2) + 's';
                
                contenedor.appendChild(particula);
                
                setTimeout(() => {
                    if (contenedor.contains(particula)) {
                        contenedor.removeChild(particula);
                    }
                }, 5000);
            }, 500);
        }
        
        // Inicializar juego cuando carga la página
        window.addEventListener('load', function() {
            crearParticulasMagicas();
        });
    </script>
</body>
</html>
                    
                case 2: // Restas básicas con enteros
                    ejercicios.push(
                        { texto: "8 - (-5) = ?", respuesta: 13 },
                        { texto: "(-12) - 7 = ?", respuesta: -19 },
                        { texto: "15 - (-8) = ?", respuesta: 23 },
                        { texto: "(-9) - (-4) = ?", respuesta: -5 },
                        { texto: "6 - (-11) = ?", respuesta: 17 },
                        { texto: "(-14) - 3 = ?", respuesta: -17 },
                        { texto: "10 - (-6) = ?", respuesta: 16 },
                        { texto: "(-7) - (-9) = ?", respuesta: 2 },
                        { texto: "13 - (-4) = ?", respuesta: 17 },
                        { texto: "(-18) - 5 = ?", respuesta: -23 },
                        { texto: "9 - (-7) = ?", respuesta: 16 },
                        { texto: "(-11) - (-8) = ?", respuesta: -3 },
                        { texto: "14 - (-3) = ?", respuesta: 17 },
                        { texto: "(-6) - 9 = ?", respuesta: -15 },
                        { texto: "7 - (-12) = ?", respuesta: 19 },
                        { texto: "(-15) - (-6) = ?", respuesta: -9 },
                        { texto: "12 - (-5) = ?", respuesta: 17 },
                        { texto: "(-8) - 4 = ?", respuesta: -12 },
                        { texto: "11 - (-9) = ?", respuesta: 20 },
                        { texto: "(-13) - (-7) = ?", respuesta: -6 }
                    );
                    break;
                    
                case 3: // Sumas y restas combinadas
                    ejercicios.push(
                        { texto: "(-8) + 12 - 5 = ?", respuesta: -1 },
                        { texto: "15
