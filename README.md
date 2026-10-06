# Cubo Tic Tac Toe

Un cubo Rubik blanco en 3D en el que dos jugadores juegan al tres en raya. Después de cada turno, el cubo gira una capa al azar, como si alguien lo estuviera mezclando mientras se juega. Las marcas se mueven con las piezas, así que la jugada que parecía segura puede romperse, o armarse sola.

## Cómo ejecutarlo

Abre `cubo-tictactoe.html` con doble clic en cualquier navegador moderno. Es un único archivo: lleva dentro Three.js y el código del juego, y no necesita internet ni instalación.

## Cómo se juega

1. El **Jugador 1** pone **X** (rojo) y el **Jugador 2** pone **O** (azul).
2. En tu turno, toca una casilla libre de cualquiera de las 54 del cubo (9 por cada una de las 6 caras).
3. Cuando marcas, una capa al azar (izquierda, central, derecha, superior, etc.) gira 90° en una dirección aleatoria. Las marcas viajan con las piezas.
4. Gana quien consiga **3 en línea dentro de una misma cara**: fila, columna o diagonal.

### Reglas de desempate

| Situación | Resultado |
|---|---|
| Tu marca forma línea | Ganas |
| El giro aleatorio forma línea solo para tu rival | Gana tu rival |
| El giro forma línea para los dos a la vez | Empate |
| Las 54 casillas están llenas sin línea | Empate |

## Controles

- **Clic o toque** sobre una casilla: marcar.
- **Arrastrar el fondo o el cubo**: girar la vista.
- **Rueda del ratón**: zoom.
- **Giros por turno** (1, 2 o 3): cuántas capas giran tras cada jugada.
- **Reiniciar**: nueva partida.

## Cómo funciona por dentro

- **Render:** Three.js. Hay 27 cubitos y 54 casillas, cada una con su propio material.
- **Marcas:** son texturas dibujadas con canvas. Cada una pertenece a su casilla, por eso se mueve con el cubito.
- **Giros:** animación interpolada de una capa (eje, capa y sentido aleatorios) que termina redondeando posiciones para no acumular error. Nunca deshace justo el giro anterior.
- **Detección de líneas:** tras cada jugada y cada giro se calcula la posición y la normal de cada casilla en coordenadas del cubo, se agrupan por cara en una cuadrícula de 3×3 y se comprueban las 8 líneas de cada cara.

## Estructura

```
Cubo/
├── cubo-tictactoe.html   # el juego completo (Three.js + lógica incluidos)
└── README.md
```
