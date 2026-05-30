<div align="center">

# Script simplificado que automatiza webscraping de correos electrónicos

</div>

---

## 1. ¿Qué hace este script?
Tú copias el contenido del correo directamente (Ctrl + A → Ctrl + C).

Pegas ese texto tal cual en un archivo .txt (por ejemplo: correo.txt).

El script lee ese texto, detecta todos los correos y los exporta a Excel.

---


## Paso 1: Copiar el correo (sin inspeccionar código)
Desde el navegador Brave:

Abre el correo en Outlook Web.

Presiona Ctrl + A → Ctrl + C (copias todo el contenido visible).

Abre un editor de texto como Bloc de Notas.

Pega el contenido (Ctrl + V) y guárdalo como correo.txt.

---


 ## Paso 2: Código Python para extraer y exportar
- Instala primero (si no tienes):

  ```bash
  pip install pandas openpyxl
  ```

- Luego ejecuta este script en Jupyter o Python:

```python
import pandas as pd
import re
```

# 1. Cargar el texto copiado desde el navegador

```
with open("correo.txt", encoding="utf-8") as file:
    contenido = file.read()
```

# 2. Buscar correos con expresión regular

```
correos = re.findall(r"[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+", contenido)
```

# 3. Eliminar duplicados y ordenar
```
correos_unicos = sorted(set(correos))
```

# 4. Crear un DataFrame y exportar

```
df = pd.DataFrame(correos_unicos, columns=["Correo Electrónico"])
df.to_excel("correos_extraidos.xlsx", index=False)

print(f"✅ Se extrajeron {len(df)} correos únicos y se guardaron en 'correos_extraidos.xlsx'")
```

# 3. Resultado
Solo necesitas copiar y pegar el correo a un .txt

El script hace el resto: extrae los correos y los guarda en un archivo Excel.

