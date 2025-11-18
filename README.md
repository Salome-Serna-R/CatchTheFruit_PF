# 🎮 Catch The Fruit – Nand2Tetris Game

**HECHO POR:** Salomé Serna Restrepo, Juan David Velásquez Restrepo y Luciana Hoyos Pérez.

**Catch The Fruit** es un juego sencillo desarrollado completamente en **Jack**, el lenguaje de alto nivel del curso **Nand2Tetris**.
El jugador controla una canasta que se mueve horizontalmente en la parte inferior de la pantalla y debe atrapar frutas para sumar puntos…
¡Pero cuidado con las bombas! 💣

---

## 🧩 Características del juego

### ✔️ Objetos que caen (Falling)

* Dos tipos de objetos:

  * **Fruta (tipo 0)** → tamaño 12×12, velocidad lenta.
  * **Bomba (tipo 1)** → tamaño 16×16, velocidad rápida, dañan al jugador.
* Caen desde una posición X aleatoria.
* Al llegar al fondo de la pantalla:

  * La **fruta perdida** resta una vida.
  * La **bomba** simplemente desaparece.
* Si son atrapados por el jugador:

  * **Fruta** → +1 punto
  * **Bomba** → -1 vida

---

## 🕹️ Controles del jugador

El jugador controla una canasta:

* **Flecha izquierda (130)** → mover a la izquierda
* **Flecha derecha (132)** → mover a la derecha
* **Tecla ESC (140)** → salir del juego

La canasta:

* mide 40 px de ancho,
* se posiciona inicialmente en el centro inferior de la pantalla,
* está limitada a los bordes (clamp).

---

## 💥 Mecánicas principales

### 🎯 Spawn de objetos

* Posición X pseudoaleatoria usando un generador congruencial.
* Evita repetir el mismo spawn consecutivo (pequeño desplazamiento).
* Probabilidad de bomba: **1 de cada 3 objetos**.

### ❤️ Vidas y Game Over

* El jugador inicia con **3 vidas**.
* Una fruta perdida o una bomba atrapada resta una vida.
* Cuando las vidas llegan a 0:

  * La pantalla se limpia.
  * Se muestra **GAME OVER** y el puntaje final.
  * El juego termina.

### 🧮 HUD

Siempre visible en la parte superior:

```
Score: X Lives: Y
```

---

## 📁 Estructura del proyecto

```
CATCHTHEFRUIT_PF/
│
├── Falling.jack   # Lógica y renderizado de frutas/bombas
├── Game.jack      # Bucle principal y lógica del juego
├── Player.jack    # Control del jugador (canasta)
├── Main.jack      # Punto de entrada
│
├── Falling.vm     # Archivos compilados
├── Game.vm
├── Main.vm
└── Player.vm
```

---

## 🧠 Descripción de cada módulo

### 🟧 **Falling.jack**

* Representa un objeto que cae.
* Maneja tamaño, velocidad, tipo, dibujo, borrado y colisión con jugador.
* Implementa:

  * `fall()`
  * `isCaught()`
  * `reset()`
  * `draw()` y `erase()`

### 🟦 **Player.jack**

* Controla la canasta del jugador.
* Administra movimiento y renderizado.
* Métodos importantes:

  * `move()`
  * `getX()`, `getY()`, `getWidth()`
  * `dispose()`

### 🟩 **Game.jack**

* Controlador del juego.
* Se encarga de:

  * spawn aleatorio,
  * puntaje,
  * vidas,
  * HUD,
  * ciclo principal.
* Contiene el generador pseudoaleatorio `rand()`.

### 🟪 **Main.jack**

* Inicializa el juego.
* Limpia la pantalla y llama `game.run()`.

---

## ▶️ Cómo ejecutar

1. Instala la extensión de Nand2Tetris
2. Abrir la terminal en la carpeta del proyecto. La terminal debe estar en:
```bash
...\nand2tetris\projects\12\CatchTheFruit
```
3. Abre un Command Prompt o PowerShell y sitúate en esa carpeta:
```bash
cd C:\ruta\a\nand2tetris\projects\12\CatchTheFruit

```
4. Compilar los archivos .jack a código VM
* Usa la herramienta JackCompiler que trae el paquete nand2tetris (hay un script .bat/.sh o un .jar).
* Objetivo: que se generen archivos .vm (p. ej. Main.vm, Game.vm, etc.) en la misma carpeta. Confirma que aparezcan esos .vm.
5. Abrir el VM Emulator
* Ejecuta la herramienta VM Emulator del paquete nand2tetris (en Windows suele haber VMEmulator.bat o VMEmulator.sh en la carpeta tools).
* También puedes abrir el ejecutable desde la interfaz gráfica
6. Cargar los archivos .vm en el emulador
* En la ventana del VM Emulator: File -> Open (o similar) y selecciona el archivo .vm principal (habitualmente Main.vm) o abre la carpeta con todos los .vm.
* Asegúrate de que el emulador apunte a la carpeta del proyecto (no a otra carpeta).
7. Ejecutar el programa en el emulador
* En el emulator: Run -> Run o presiona el botón de Play.
* Observa la ventana gráfica (el juego) y el panel de RAM / stacks del emulador.
8. ¡Juega!
---

## Video
[https://youtu.be/XNJ3COolrno](https://youtu.be/XNJ3COolrno)
