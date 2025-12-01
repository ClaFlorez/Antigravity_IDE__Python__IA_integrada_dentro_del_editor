# 📘 Tutorial Completo – Antigravity IDE + Python + IA  
*Documento de soporte para tu repositorio (carpeta `docs/`).*

Este tutorial explica paso a paso cómo:

- Configurar Antigravity IDE por primera vez  
- Probar Python con el módulo secreto `antigravity`  
- Usar el Antigravity Agent para crear código  
- Construir una pequeña demo interactiva (`ai_demo.py`)  
- Manejar errores reales que aparecieron durante el proceso  

---

## 1. Requisitos previos

- Windows 10/11  
- Python 3.x instalado  
- Antigravity IDE instalado  
- Cuenta de Google (opcional, para autenticación)

Verificar Python:

```bash
python --version
```

---

## 2. Configuración inicial del IDE

1. Abrir Antigravity IDE por primera vez.  
2. En la pantalla de inicio de configuración elegir:

   - **Start fresh** (configuración limpia).

3. En la parte del **Antigravity Agent**, usar:

   - Modo: **Custom configuration**  
   - Terminal execution policy: `Auto`  
   - Review policy: `Request Review` ✔  
   - JavaScript execution: `Always Ask` ✔  

4. En la parte del editor:

   - Keybindings: **Normal**  
   - Instalar extensiones recomendadas (por ejemplo: *Install 7 Extensions*).

5. Si lo deseas, iniciar sesión con **Google** para activar funciones extra del IDE.  
   Cuando veas el mensaje *“You have successfully authenticated”*, volver al IDE y aceptar los términos de uso.

6. Cuando el IDE pregunte:

   > Do you trust the authors of the files in this folder?

   seleccionar **Yes, I trust the authors** para activar todas las funciones.

7. Si aparece el botón **Reload Window**, pulsarlo.  
   Esto solo recarga el editor, no reinicia Windows.

---

## 3. Crear el proyecto `antigravity_test`

1. En el IDE, ir a **Open Folder**.  
2. Crear una carpeta nueva, por ejemplo:

   ```text
   antigravity_test
   ```

3. Abrir esa carpeta con el IDE.  
4. Si vuelve a aparecer la pregunta de confianza, elegir otra vez:

   - **Yes, I trust the authors**

---

## 4. Probar Python con `import antigravity`

Dentro de la carpeta del proyecto:

1. Crear un archivo llamado:

   ```text
   test_antigravity.py
   ```

2. Escribir:

   ```python
   import antigravity
   ```

3. Ejecutar:

   - Botón **Run Python File**, o  
   - Menú **Run → Run Without Debugging**

Si todo está bien configurado, se abrirá en el navegador el famoso cómic de XKCD sobre Python (id #353).  
Eso confirma que Python y el entorno del IDE están funcionando correctamente.

---

## 5. Usar el Antigravity Agent para crear una demo de IA

Antigravity incluye un panel de agente de IA que puede crear y modificar archivos.

### 5.1 Abrir el panel del agente

1. En el lado derecho del IDE, abrir la pestaña del **Agent**.  
2. Allí verás un campo que dice algo como:

   ```text
   Ask anything (Ctrl+L)
   ```

3. Si aparece un aviso para seleccionar modelo, basta con cerrarlo o elegir un modelo por defecto.

---

### 5.2 Prompt utilizado para generar `ai_demo.py`

En el campo de texto del agente, escribir (o pegar):

```text
Create a new Python file in this workspace called ai_demo.py.

The script should:
1. Ask the user for their name.
2. Ask how many times to repeat the greeting.
3. Validate that the number is a positive integer.
4. Print: "Hola <nombre>, la IA y tú son un gran equipo 🚀" that many times.

Use comments in Spanish.
Only use the Python standard library.
```

Después de presionar Enter:

- El agente analiza la petición  
- Propone crear un archivo `ai_demo.py`  
- Muestra el contenido sugerido del archivo  
- Y, como está configurado con **Request Review**, pide permiso antes de ejecutar cualquier comando.

---

### 5.3 Código final de `ai_demo.py`

Este es un ejemplo de cómo queda el archivo:

```python
def main():
    # Pedir el nombre al usuario
    nombre = input("Por favor, introduce tu nombre: ")

    # Pedir cuántas veces repetir el saludo y validar que sea entero positivo
    while True:
        entrada = input("¿Cuántas veces quieres repetir el saludo? ")
        try:
            cantidad = int(entrada)
            if cantidad > 0:
                break
            else:
                print("Por favor, introduce un número entero positivo mayor que cero.")
        except ValueError:
            print("Eso no es un número válido. Inténtalo de nuevo.")

    # Imprimir el saludo la cantidad de veces solicitada
    for _ in range(cantidad):
        print(f"Hola {nombre}, la IA y tú son un gran equipo 🚀")


if __name__ == "__main__":
    main()
```

---

## 6. Ejecutar la demo `ai_demo.py`

Para ejecutar la demo de IA:

1. Abrir la terminal integrada en el IDE (PowerShell / CMD).  
2. Asegurarse de estar en la carpeta del proyecto (`antigravity_test`).  
3. Ejecutar:

   ```bash
   python ai_demo.py
   ```

Ejemplo de interacción:

```text
Por favor, introduce tu nombre: claudia
¿Cuántas veces quieres repetir el saludo? 3

Hola claudia, la IA y tú son un gran equipo 🚀
Hola claudia, la IA y tú son un gran equipo 🚀
Hola claudia, la IA y tú son un gran equipo 🚀
```

Con esto comprobamos que:

- El agente generó un script correcto  
- El entorno de Python funciona  
- El programa hace interacción por consola

---

## 7. Errores reales y cómo se solucionaron

Durante el proceso aparecieron algunos errores que son normales cuando se combina IA + consola de Windows.

### 7.1 `Agent terminated due to error`

A veces, el agente intentó ejecutar un comando automático (por ejemplo, utilizando `Write-Output` en PowerShell) y terminó con un error.

**Solución:**

- Cerrar la notificación del agente (Dismiss)  
- Ejecutar el archivo manualmente en la terminal con:

  ```bash
  python ai_demo.py
  ```

### 7.2 `UnicodeEncodeError` por el emoji 🚀

En algunas configuraciones de consola de Windows, los emojis no se muestran bien y apareció un error de codificación de caracteres.

**Soluciones posibles:**

1. Cambiar la página de códigos a UTF-8 antes de ejecutar:

   ```bat
   chcp 65001
   python ai_demo.py
   ```

2. O simplemente ejecutar desde la terminal integrada del IDE, que a menudo maneja mejor el Unicode.

En nuestro caso, el programa funcionó correctamente al ejecutarlo manualmente.

---

## 8. Imágenes reales del proceso

En esta carpeta (`docs/img/`) se guardan capturas reales de la configuración y uso del IDE.  
Puedes referenciarlas desde otros documentos o desde tu README principal.

Ejemplo de uso en Markdown:

```markdown
![Captura de ejemplo](../img/0602b1a7-0a44-4bba-8a30-956ca7b846cc.png)
```


