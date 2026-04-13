# **Ejercicios del Trabajo Práctico N°2: Evaluación in silico de propiedades ADMET y filtros de selección de candidatos a fármaco**
## **Ejercicio 1**
### a. Selección de compuestos: Ingresar a PubChem (https://pubchem.ncbi.nlm.nih.gov). Utilizar la barra de búsqueda, para encontrar información de los siguientes compuesto: aspirin, paracetamol y caffeine. Obtener el “Canonical SMILES” del compuesto para los pasos anteriores

Aspirin: CC(=O)OC1=CC=CC=C1C(=O)O

Paracetamol: CC(=O)NC1=CC=C(C=C1)O

Caffeine: CN1C=NC2=C1C(=O)N(C(=O)N2C)C

### b. Seleccionar 3 fármacos conocidos y 2 experimentales utilizando las palabras clave: anticancer candidate, natural product, experimental drug.

## Fármacos conocidos

- **Imatinib**  
  SMILES: `CC1=C(C=C(C=C1)NC(=O)C2=CC=C(C=C2)CN3CCN(CC3)C)NC4=NC=CC(=N4)C5=CN=CC=C5`  
  Inhibidor de quinasas que revolucionó el tratamiento de la leucemia mieloide crónica (LMC).  
  Aprobado por la FDA en 2001 y por la EMA el 7 de noviembre de 2001.  
  PubChem: 5291

- **Temozolomide**  
  SMILES: `CN1C(=O)N2C=NC(=C2N=N1)C(=O)N`  
  Agente alquilante oral de referencia para el glioblastoma multiforme y el astrocitoma anaplásico refractario.  
  Aprobada por la FDA en 1999. Comercializada como TEMODAR® por Merck.  
  PubChem: 5394

- **5-Fluorouracil**  
  SMILES: `C1=C(C(=O)NC(=O)N1)F`  
  Análogo de pirimidina antineoplásico utilizado en tumores sólidos: colon, recto, mama, estómago, páncreas, ovario, vejiga e hígado.  
  Aprobado el 30 de septiembre de 1998.  
  PubChem: 3385

## Fármacos experimentales

- **Resveratrol**  
  SMILES: `C1=CC(=CC=C1/C=C/C2=CC(=CC(=C2)O)O)O`  
  Polifenol natural de las uvas rojas investigado para hiperlipidemia, hígado graso, diabetes y aterosclerosis.  
  Ha alcanzado ensayos de fase 3, sin aprobación definitiva aún.  
  PubChem: 445154

- **Curcumin**  
  SMILES: `COC1=C(C=CC(=C1)/C=C/C(=O)CC(=O)/C=C/C2=CC(=C(C=C2)O)OC)O`  
  Polifenol de la cúrcuma con actividades antibacteriana, antiinflamatoria, antioxidante y antimicrobiana.  
  Investigada en cáncer de mama, mieloma múltiple, depresión y deterioro cognitivo leve.  
  Limitada por su baja biodisponibilidad oral.  
  PubChem: 969516

## **Ejercicio 2**
### Realizar la predicción de propiedades fisicoquímicas de las moléculas obtenidas en el punto 1.a, mediante el uso de la herramienta SwissADME (http://www.swissadme.ch). Utilizando los SMILES obtenidos en el punto anterior, obtener de ambos fármacos: 

### Aspirin
- Peso molecular: 180.16 g/mol  
- LogP (índice de lipofilicidad): 1.28  
- H-bond acceptors: 4  
- H-bond donors: 1  
- TPSA (Superficie polar): 63.60 Å²  
- Rotatable bonds: 3  

### Paracetamol
- Peso molecular: 151.16 g/mol  
- LogP (índice de lipofilicidad): 0.93  
- H-bond acceptors: 2  
- H-bond donors: 2  
- TPSA (Superficie polar): 49.33 Å²  
- Rotatable bonds: 2  

### Caffeine
- Peso molecular: 194.19 g/mol  
- LogP (índice de lipofilicidad): 0.08  
- H-bond acceptors: 3  
- H-bond donors: 0  
- TPSA (Superficie polar): 61.82 Å²  
- Rotatable bonds: 0  

También para los fármacos elegidos en el punto 1.b:
### Imatinib
- Peso molecular: 493.60 g/mol  
- LogP (índice de lipofilicidad): 3.38  
- H-bond acceptors: 6  
- H-bond donors: 2  
- TPSA (Superficie polar): 86.28 Å²  
- Rotatable bonds: 8  

### Temozolomide
- Peso molecular: 194.15 g/mol  
- LogP (índice de lipofilicidad): -0.92  
- H-bond acceptors: 5  
- H-bond donors: 1  
- TPSA (Superficie polar): 108.17 Å²  
- Rotatable bonds: 1  

### 5-Fluorouracil
- Peso molecular: 130.08 g/mol  
- LogP (índice de lipofilicidad): 0.13  
- H-bond acceptors: 3  
- H-bond donors: 2  
- TPSA (Superficie polar): 65.72 Å²  
- Rotatable bonds: 0  

### Resveratrol
- Peso molecular: 228.24 g/mol  
- LogP (índice de lipofilicidad): 2.48  
- H-bond acceptors: 3  
- H-bond donors: 3  
- TPSA (Superficie polar): 60.69 Å²  
- Rotatable bonds: 2  

### Curcumin
- Peso molecular: 368.38 g/mol  
- LogP (índice de lipofilicidad): 3.03  
- H-bond acceptors: 6  
- H-bond donors: 2  
- TPSA (Superficie polar): 93.06 Å²  
- Rotatable bonds: 8  


## **Ejercicio 3**
### Identificar subestructuras indeseables de los compuestos del punto 1.a y 1.b usando el siguiente módulo de python creado para tal fin siguiendo el tutorial. 
```bash
$ pip install rdkit-pypi molvs requests pandas numpy matplotlib seaborn
$ pip install deepchem
$ python
```
```python
from admet_module import analisis_completo

mis_moleculas = {'molecula': 'COc1ccccc1C=O'}

resultados = analisis_completo(mis_moleculas)

print(resultados.keys())
print(resultados['propiedades'])
```
Se obtuvo el siguiente resultado para las moléculas analizadas:
## Propiedades calculadas (sin SMILES)

| Name            | MW (g/mol) | LogP    | HBA | HBD | TPSA (Å²) | Rotatable Bonds | Lipinski Violations |
|-----------------|-----------:|--------:|----:|----:|----------:|----------------:|--------------------:|
| aspirin         | 180.159    | 1.31010 | 3   | 1   | 63.60     | 2               | 0 |
| paracetamol     | 151.165    | 1.35060 | 2   | 2   | 49.33     | 1               | 0 |
| caffeine        | 194.194    | -1.02930| 6   | 0   | 61.82     | 0               | 0 |
| imatinib        | 493.615    | 4.59032 | 7   | 2   | 86.28     | 7               | 0 |
| temozolomide    | 194.154    | -2.07810| 7   | 1   | 108.17    | 1               | 0 |
| 5-fluorouracil  | 130.078    | -0.79770| 2   | 2   | 65.72     | 0               | 0 |
| resveratrol     | 228.247    | 2.97380 | 3   | 3   | 60.69     | 2               | 0 |
| curcumin        | 368.385    | 3.36990 | 6   | 2   | 93.06     | 8               | 0 |

A su vez, se calculó la presencia de subestructuras indeseables (PAINS):
## Evaluación de subestructuras indeseables (PAINS)

| Name            | PAINS Alerts | PAINS Details |
|-----------------|-------------:|---------------|
| aspirin         | 0            | []            |
| paracetamol     | 0            | []            |
| caffeine        | 0            | []            |
| imatinib        | 0            | []            |
| temozolomide    | 0            | []            |
| 5-fluorouracil  | 0            | []            |
| resveratrol     | 0            | []            |
| curcumin        | 0            | []            |

No se detectó ninguna en ninguno de los casos. Se incluyen otros datos que aporta el código:

## Predicción ADMET

| Name           | Absorption | BBB Penetration | Plasma Binding | CYP Inhibition | Renal Clearance |
|----------------|-----------|-----------------|----------------|----------------|-----------------|
| aspirin        | High      | Yes             | Medium         | Low            | Low             |
| paracetamol    | High      | Yes             | Medium         | Low            | Low             |
| caffeine       | High      | Yes             | Low            | Low            | High            |
| imatinib       | High      | No              | High           | Low            | Low             |
| temozolomide   | High      | No              | Low            | Low            | High            |
| 5-fluorouracil | High      | Yes             | Low            | Low            | High            |
| resveratrol    | High      | No              | Medium         | Low            | Low             |
| curcumin       | High      | No              | High           | Low            | Low             |

## Predicción de toxicidad

| Name           | Toxicity Alerts | Toxic Fragments | Predicted Toxicity | Estimated LD50 |
|----------------|----------------:|-----------------|--------------------|----------------|
| aspirin        | 0               | —               | Low                | >5000 mg/kg    |
| paracetamol    | 0               | —               | Low                | >5000 mg/kg    |
| caffeine       | 0               | —               | Low                | >5000 mg/kg    |
| imatinib       | 0               | —               | Low                | >5000 mg/kg    |
| temozolomide   | 0               | —               | Low                | >5000 mg/kg    |
| 5-fluorouracil | 0               | —               | Low                | >5000 mg/kg    |
| resveratrol    | 0               | —               | Low                | >5000 mg/kg    |
| curcumin       | 0               | —               | Low                | >5000 mg/kg    |

## **Ejercicio 4**
### Realizar la predicción de toxicidad in silico utilizando ProTox-II (https://tox-new.charite.de/protox_II/). Utilizando los SMILES de moléculas del punto 1.a y 1.b, obtener: a. Predicted LD50 (mg/kg) y clase de toxicidad (I–VI). b. Riesgo de hepatotoxicidad, mutagenicidad, carcinogenicidad. ¿Cuál de las moléculas seleccionadas muestra menor toxicidad según ProTox-II?

## Predicción de toxicidad in silico mediante ProTox-II

Se realizó la predicción de toxicidad in silico de las moléculas seleccionadas utilizando ProTox-II, a partir de sus respectivos SMILES. Se obtuvieron los valores de LD50, la clase de toxicidad (I–VI) y la predicción de hepatotoxicidad, mutagenicidad y carcinogenicidad.

### Resultados

| Compuesto        | LD50 (mg/kg) | Clase | Hepatotoxicidad | Carcinogenicidad | Mutagenicidad |
|------------------|-------------:|:-----:|-----------------|------------------|---------------|
| Aspirin          | 250          | III   | Inactiva (0.51) | Inactiva (0.86)  | Inactiva (0.97) |
| Caffeine         | 127          | III   | Inactiva (0.97) | Inactiva (0.93)  | Inactiva (0.94) |
| Paracetamol      | 338          | IV    | Activa (0.74)   | Inactiva (0.51)  | Inactiva (0.90) |
| Imatinib         | 100          | III   | Activa (0.71)   | Inactiva (0.67)  | Inactiva (0.73) |
| Temozolomide     | 498          | IV    | Inactiva (0.58) | Inactiva (0.50)  | Inactiva (0.61) |
| 5-fluorouracil   | 1923         | IV    | Inactiva (0.78) | Activa (0.85)    | Inactiva (0.88) |
| Resveratrol      | 1560         | IV    | Inactiva (0.74) | Inactiva (0.71)  | Inactiva (0.92) |
| Curcumin         | 2000         | IV    | Inactiva (0.61) | Inactiva (0.84)  | Inactiva (0.88) |



En términos de toxicidad aguda, un valor de **LD50** más alto indica menor toxicidad. A su vez, las moléculas de **clase IV** presentan menor toxicidad aguda que las de **clase III**.

Entre los compuestos analizados, **curcumin** fue la molécula que mostró **menor toxicidad aguda**, ya que presentó el **LD50 más alto (2000 mg/kg)** dentro del grupo y perteneció a la **clase IV**. Le siguieron **5-fluorouracil** con un LD50 de 1923 mg/kg y **resveratrol** con 1560 mg/kg, ambos también en clase IV.

En cuanto a los riesgos toxicológicos específicos, la mayoría de las moléculas presentaron predicción **inactiva** para carcinogenicidad y mutagenicidad. Sin embargo, se observaron algunas alertas puntuales:
- **Paracetamol** e **imatinib** mostraron **hepatotoxicidad activa**.
- **5-fluorouracil** mostró **carcinogenicidad activa**.
- El resto de las moléculas presentaron predicción inactiva para hepatotoxicidad, carcinogenicidad y mutagenicidad.

Considerando los resultados de ProTox-II, la molécula que mostró **menor toxicidad global según la toxicidad aguda** fue **curcumin**, debido a su **LD50 de 2000 mg/kg** y su clasificación en **clase IV**, además de no presentar alertas activas de hepatotoxicidad, mutagenicidad ni carcinogenicidad. Por lo tanto, dentro del conjunto analizado, **curcumin** fue el compuesto con el perfil toxicológico más favorable.

## **Ejercicio 5**
### Construir una ficha técnica de cada compuesto que considere las respuestas a las siguientes preguntas: ¿Qué compuestos cumplen mejor con los filtros de Lipinski y Veber? ¿Aparecieron moléculas con alertas PAINS? ¿Cuál es su toxicidad?

A partir de los resultados obtenidos con SwissADME, el análisis de alertas PAINS y la predicción de toxicidad con ProTox-II, se construyó una ficha técnica comparativa para cada compuesto.

### Criterios considerados
- **Filtros de Lipinski y Veber:** todos los compuestos analizados cumplen con estos filtros, por lo que presentan un perfil fisicoquímico compatible con características de drug-likeness y biodisponibilidad oral.
- **Alertas PAINS:** no se detectaron alertas PAINS en ninguno de los compuestos, lo que indica ausencia de subestructuras típicamente asociadas a interferencias en ensayos biológicos.
- **Toxicidad:** la diferenciación entre compuestos se realizó principalmente en base a la predicción de toxicidad aguda (LD50 y clase de toxicidad) y a la presencia o ausencia de alertas específicas de hepatotoxicidad, carcinogenicidad y mutagenicidad.

---

## Ranking global de seguridad toxicológica

1. **Curcumin**
2. **Resveratrol**
3. **Temozolomide**
4. **Caffeine**
5. **Aspirin**
6. **Paracetamol**
7. **Imatinib**
8. **5-fluorouracil**

---

## Fichas técnicas por compuesto

### Curcumin
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** inactiva (0.61)
- **Carcinogenicidad:** inactiva (0.84)
- **Mutagenicidad:** inactiva (0.88)
- **Clase de toxicidad:** IV
- **LD50:** 2000 mg/kg

Es el compuesto con el perfil más favorable. No presenta alertas toxicológicas activas, pertenece a clase IV y muestra el LD50 más alto del conjunto, por lo que se considera el de **menor toxicidad global**.

---

### Resveratrol
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** inactiva (0.74)
- **Carcinogenicidad:** inactiva (0.71)
- **Mutagenicidad:** inactiva (0.92)
- **Clase de toxicidad:** IV
- **LD50:** 1560 mg/kg

Presenta un perfil toxicológico muy favorable, sin alertas activas y con buen LD50. Queda apenas por debajo de curcumin por tener menor LD50.

---

### Temozolomide
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** inactiva (0.58)
- **Carcinogenicidad:** inactiva (0.50)
- **Mutagenicidad:** inactiva (0.61)
- **Clase de toxicidad:** IV
- **LD50:** 498 mg/kg

No presenta alertas activas, lo cual le da una ventaja importante. Sin embargo, queda por debajo de curcumin y resveratrol porque su LD50 es bastante menor y las probabilidades de inactividad en toxicidades específicas son más débiles.

---

### Caffeine
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** inactiva (0.97)
- **Carcinogenicidad:** inactiva (0.93)
- **Mutagenicidad:** inactiva (0.94)
- **Clase de toxicidad:** III
- **LD50:** 127 mg/kg

Tiene el perfil específico más limpio y confiable de todos, ya que todas las alertas resultan inactivas con probabilidades altas. Sin embargo, queda relegada por su clase III y su LD50 bajo, lo que indica mayor toxicidad aguda que los compuestos ubicados por encima.

---

### Aspirin
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** inactiva (0.51)
- **Carcinogenicidad:** inactiva (0.86)
- **Mutagenicidad:** inactiva (0.97)
- **Clase de toxicidad:** III
- **LD50:** 250 mg/kg

No presenta alertas activas, pero la predicción de hepatotoxicidad inactiva es débil (0.51). Por eso queda muy pareja con caffeine, aunque algo por debajo si se prioriza la claridad del perfil toxicológico específico.

---

### Paracetamol
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** activa (0.74)
- **Carcinogenicidad:** inactiva (0.51)
- **Mutagenicidad:** inactiva (0.90)
- **Clase de toxicidad:** IV
- **LD50:** 338 mg/kg

Aunque pertenece a clase IV, cae en el ranking por presentar una alerta activa de hepatotoxicidad con probabilidad relativamente alta. Esa señal penaliza significativamente su perfil de seguridad.

---

### Imatinib
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** activa (0.71)
- **Carcinogenicidad:** inactiva (0.67)
- **Mutagenicidad:** inactiva (0.73)
- **Clase de toxicidad:** III
- **LD50:** 100 mg/kg
 
Presenta hepatotoxicidad activa y, además, combina clase III con uno de los LD50 más bajos del grupo. Esto lo ubica entre los compuestos menos favorables desde el punto de vista toxicológico.

---

### 5-fluorouracil
- **Lipinski:** cumple
- **Veber:** cumple
- **PAINS:** 0 alertas
- **Hepatotoxicidad:** inactiva (0.78)
- **Carcinogenicidad:** activa (0.85)
- **Mutagenicidad:** inactiva (0.88)
- **Clase de toxicidad:** IV
- **LD50:** 1923 mg/kg

A pesar de presentar una clase de toxicidad favorable y un LD50 alto, queda en último lugar por la presencia de una alerta activa de carcinogenicidad con probabilidad elevada (0.85), lo que penaliza fuertemente su perfil global de seguridad.

---

## Conclusión general

Todos los compuestos analizados cumplen con los filtros de **Lipinski** y **Veber**, y ninguno presenta **alertas PAINS**, por lo que desde el punto de vista estructural y fisicoquímico todos muestran un perfil adecuado.

La principal diferencia entre ellos aparece al evaluar la **toxicidad predicha**. En este análisis, **curcumin** y **resveratrol** se destacan como los compuestos con mejor perfil global de seguridad, mientras que **5-fluorouracil**, **imatinib** y **paracetamol** resultan más desfavorables debido a la presencia de alertas toxicológicas activas.