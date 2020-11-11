# Cores no terminal em Python 👨‍💻

Python é realmente uma liguagem de programação bastante poderosa, claro, 
simples ao mesmo tempo também. Essa liguagem é muito utilizada em:

- Data science;
- CLI (Command Line Interfaces);
- Apps Android (Sim apps Android);
- Programas desktop;
- APIs Rest.

Claro que há muito mais usos e estes são um dos vários que existem.

# Como instalar o Python ? 

### Windows

#### Pelo site

Accesse este <a href="https://www.python.org/downloads/windows/">link</a>.

#### Via chocolatey

````sh
choco install python
````

### MacOS

````sh
brew install python
````
Ou
````sh
brew install python3
````
# Como escolher cores, estilos e fundo no Python?

As cores no terminal são escolhidas por meio da tabela ANSI. 
O Python trabalha muito bem com o formato <b>\033[m</b>. Mas o que 
são estes simbolos doidos? Basicamente é como iniciaremos
a nossa brincadeira com as cores. 

A estrutura funciona da seguinte forma:

```
\033[m{estilo_fonte};{cor_fonte};{cor_fundo} Hello World \033[m
```

Para escolher o estilo basta seguir esta lista:

 - none (sem estilo) - 0
 - bold - 1
 - underline - 4
 - negative (inverter cores) - 7

Para escolher as cores de texto basta seguir esta lista:

 - white - 30
 - red - 31
 - green - 32
 - yellow - 33
 - blue - 34
 - purple - 35
 - cyan - 36
 - gray - 37
 
Para o fundo basta seguir a esta lista:

 - white - 40
 - red - 41
 - green - 42
 - yellow - 43
 - blue - 44
 - purple - 45
 - cyan - 46
 - gray - 47
 
Exemplo de print com cor:
 
```python
print('\033[0;30;0m Hello World!!! \033[m')
```
 Neste exemplo tiramos os estilos e o fundo, dando uma cor somente para o texto, ou seja:
 
 - 0 : sem estilo;
 - 30 : texto branco;
 - 0 : sem cor de fundo.
 
# Meu arquivo "main.py"

Para facilitar sua vida criei um método que você pode usar em seus trabalhos
para facilitar sua vida.

Ele se chama "c_print":
 
```python

def c_print(
        text="",
        text_color="white",
        text_style="none",
        background_color="none"):
    style_text_dictionary = {
        "bold": "1",
        "underline": "4",
        "negative": "7"
    }
    colors_dictionary = {
        "text_colors": {
            "white": "30",
            "red": "31",
            "green": "32",
            "yellow": "33",
            "blue": "34",
            "purple": "35",
            "cyan": "36",
            "gray": "37"
        },
        "background_colors": {
            "white": "40",
            "red": "41",
            "green": "42",
            "yellow": "43",
            "blue": "44",
            "purple": "45",
            "cyan": "46",
            "gray": "47"
        }
    }

    data = []
    output = ''
    if text_color in colors_dictionary["text_colors"]:
        data.append(f'{colors_dictionary["text_colors"][text_color]}')
    if text_style in style_text_dictionary:
        data.append(f'{style_text_dictionary[text_style]}')
    if background_color in colors_dictionary["background_colors"]:
        data.append(f'{colors_dictionary["background_colors"][background_color]}')

    if len(data) == 3:
        output = f'\033[{data[1]};{data[0]};{data[2]}m{text}\033[m'
    if len(data) == 2:
        output = f'\033[{data[1]};{data[0]}m{text}\033[m'
    if len(data) == 1:
        output = f'\033[{data[0]}m{text}\033[m'
    if len(data) == 0:
        output = text
    print(output)

```
Ele rece um texto, cor, estilo e fundo

# Fotos com alguns exemplos & respectivos comandos

```python
# com corpo colorido
c_print(f"Hello World {year}!!!", "yellow", "bold", "blue")
c_print(f"Hello World {year}!!!", "blue", "bold", "green")
c_print(f"Hello World {year}!!!", "yellow", "bold", "red")
c_print(f"Hello World {year}!!!", "white", "bold", "purple")
# com estilo e cor de texto
c_print(f"Hello World {year}!!!", "blue", "bold")
c_print(f"Hello World {year}!!!", "yellow", "underline")
c_print(f"Hello World {year}!!!", "white", "negative")
```

<img src="https://lh5.googleusercontent.com/f8GMIo6wCVlfZTCPO_bHohfX6Vx47EU-amBknOEpnq7u6tNOcq6a5H0NpGnGlTUPna7lGyHPRmR4Lq6WzuSq=w952-h704-rw" />