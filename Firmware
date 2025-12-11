# StudyPad - Firmware para macropad de 4 teclas
# Este firmware é para um projeto académico que junta Pomodoro + Notas rápidas.
# Feito para correr em KMK/CircuitPython num RP2040.

import board

from kmk.kmk_keyboard import KMKKeyboard
from kmk.scanners.keypad import KeysScanner
from kmk.keys import KC
from kmk.modules.macros import Macros, Press, Release, Tap

# Instância principal do teclado
keyboard = KMKKeyboard()

# Módulo de macros (necessário para enviar sequências)
macros = Macros()
keyboard.modules.append(macros)

# Estes são os pinos que planeei usar na PCB (pode ser alterado se necessário)
PINS = [
    board.D3,  # tecla 1
    board.D4,  # tecla 2
    board.D2,  # tecla 3
    board.D1,  # tecla 4
]

# Definição dos 4 botões sem matriz (1 pin = 1 tecla)
keyboard.matrix = KeysScanner(
    pins=PINS,
    value_when_pressed=False,
)

# --------------------------
# MACROS DO STUDYPAD
# --------------------------

# Iniciar Pomodoro (abre Spotlight e escreve o comando)
def macro_start_pomodoro():
    return [
        Press(KC.LCMD),
        Tap(KC.SPACE),
        Release(KC.LCMD),
        "pomodoro start",
        KC.ENTER,
    ]

# Parar Pomodoro
def macro_stop_pomodoro():
    return [
        Press(KC.LCMD),
        Tap(KC.SPACE),
        Release(KC.LCMD),
        "pomodoro stop",
        KC.ENTER,
    ]

# Criar uma nota rápida
def macro_quick_note():
    return [
        Press(KC.LCMD),
        Tap(KC.SPACE),
        Release(KC.LCMD),
        "quick note",
        KC.ENTER,
    ]

# Abrir a aplicação de Notas do sistema
def macro_open_notes_app():
    return [
        Press(KC.LCMD),
        Tap(KC.SPACE),
        Release(KC.LCMD),
        "notes",
        KC.ENTER,
    ]

# --------------------------
# KEYMAP FINAL DO MACROPAD
# --------------------------

keyboard.keymap = [
    [
        KC.MACRO(macro_start_pomodoro()),  # tecla 1
        KC.MACRO(macro_stop_pomodoro()),   # tecla 2
        KC.MACRO(macro_quick_note()),      # tecla 3
        KC.MACRO(macro_open_notes_app()),  # tecla 4
    ]
]

# Inicia o loop principal do KMK
if __name__ == "__main__":
    keyboard.go()
