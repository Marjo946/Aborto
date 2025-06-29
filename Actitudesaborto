"""
Análisis de actitudes según variables socio-demográficas
Autor: [Tu Nombre]
Descripción: Este script carga una base de datos tipo Likert y grafica los promedios
de actitud en función de sexo, escolaridad, estado civil y religión.
"""

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# === 1. Cargar datos ===
FILE_PATH = 'Base de Likert(Sheet1).csv'

# Intentar diferentes codificaciones
try:
    df = pd.read_csv(FILE_PATH, encoding='utf-8')
except UnicodeDecodeError:
    df = pd.read_csv(FILE_PATH, encoding='ISO-8859-1')

# === 2. Procesamiento ===
# Calcular promedio de actitud por persona (R1 a R25)
df['Promedio_Actitud'] = df[[f'R{i}' for i in range(1, 26)]].mean(axis=1)

# Mapas de codificación
mapas = {
    'Sexo': {1: 'Mujer', 2: 'Hombre'},
    'Escolaridad': {
        1: 'Primaria', 2: 'Secundaria', 3: 'Técnico',
        4: 'Preparatoria', 5: 'Licenciatura', 6: 'Maestría', 7: 'Doctorado'
    },
    'Estado civil': {
        1: 'Soltero', 2: 'Noviazgo', 3: 'Casado', 4: 'Unión libre'
    },
    'Religión': {
        1: 'Católica', 2: 'Cristiana', 3: 'Testigo de Jehová', 4: 'No tengo'
    }
}

# Aplicar etiquetas legibles
for col, mapa in mapas.items():
    df[col] = df[col].map(mapa)

# === 3. Visualización ===
sns.set(style="whitegrid")
fig, axs = plt.subplots(2, 2, figsize=(16, 10))

# Gráficos
sns.barplot(data=df, x='Sexo', y='Promedio_Actitud', ax=axs[0, 0])
axs[0, 0].set_title('Promedio de actitud por Sexo')

sns.barplot(data=df, x='Escolaridad', y='Promedio_Actitud', ax=axs[0, 1])
axs[0, 1].set_title('Promedio de actitud por Escolaridad')
axs[0, 1].tick_params(axis='x', rotation=45)

sns.barplot(data=df, x='Estado civil', y='Promedio_Actitud', ax=axs[1, 0])
axs[1, 0].set_title('Promedio de actitud por Estado civil')

sns.barplot(data=df, x='Religión', y='Promedio_Actitud', ax=axs[1, 1])
axs[1, 1].set_title('Promedio de actitud por Religión')
axs[1, 1].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.savefig("promedios_actitud.png")
plt.show()

# === Fin del script ===
