import time
import os

# Definir el pin donde está conectado el LED (puedes cambiar el número del pin según corresponda)
LED_PIN = 18

# Exportar el pin para hacerlo accesible
if not os.path.exists(f"/sys/class/gpio/gpio{LED_PIN}"):
    with open("/sys/class/gpio/export", "w") as f:
        f.write(str(LED_PIN))

# Configurar el pin como salida
with open(f"/sys/class/gpio/gpio{LED_PIN}/direction", "w") as f:
    f.write("out")

# Encender y apagar el LED
try:
    while True:
        # Encender el LED
        with open(f"/sys/class/gpio/gpio{LED_PIN}/value", "w") as f:
            f.write("1")
        print("LED encendido")
        time.sleep(1)  # Esperar 1 segundo
        
        # Apagar el LED
        with open(f"/sys/class/gpio/gpio{LED_PIN}/value", "w") as f:
            f.write("0")
        print("LED apagado")
        time.sleep(1)  # Esperar 1 segundo

except KeyboardInterrupt:
    print("Programa terminado por el usuario")

    # Liberar el pin GPIO
    with open("/sys/class/gpio/unexport", "w") as f:
        f.write(str(LED_PIN))
