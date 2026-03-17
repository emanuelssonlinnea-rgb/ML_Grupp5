# Marketplace Safety - Prioritering av misstänkta annonser och meddelanden

Ett maskininlärningsprojekt som bygger ett beslutsstöd för att hjälpa ett Trust & Safety-team att prioritera granskning av misstänkta annonser och meddelanden på en marknadsplats-app.

Plattformen drabbas varje vecka av ett mindre antal problematiska aktiviteter (bluffannonser, spam och misstänkta konton) som Trust & Safety-teamet inte hinner granska manuellt. 

Målet är att bygga en klassificeringsmodell som hjälper teamet prioritera vad som granskas först. 

## Kravkort

**Stakeholder:** Fredrik, COO/Finance

Fredrik vill ha ett beslutsunderlag, inte en teknisk show. Han ser två kostnader: granskningstid och missade bedrägerier. Han accepterar att ni inte kan få allt, men han
kräver att ni visar konsekvenserna av era val och väljer en tydlig kompromiss. Om ni bara säger “vi tog den som gav högst score” kommer han inte köpa det.

## Strategi

Vi inledde arbetet med att undersöka datan för att skapa oss en tydlig bild av dess karaktär och egenskaper, vilket lade grunden för välgrundade beslut i de efterföljande stegen.

Därefter delades datan upp i tränings- och testset med en fördelning på 80/20. För att säkerställa en säker och smidig hantering av prediktioner valde vi att arbeta med pipelines.

Vi jämförde tre modeller – en baseline modell, Logistic Regression och Random Forest – vilka utvärderades med 5-fold cross-validation och F1-score som prestationsmått.

En av modellerna valdes sedan ut för vidare optimering med hjälp av GridSearchCV. Valet av hyperparametrar baserades på kravspecifikationen, med målet att uppnå en balanserad avvägning mellan kostnad och risk, samt mellan falskt positiva och falskt negativa utfall.

Vi valde även att justera beslutströskeln (threshold) och jämförde detta med ett Top-N-angreppssätt, i syfte att uppnå en rimlig balans mellan kostnad och risk. Vid fastställandet av threshold utgick vi från tre olika scenarier och landade i en lägre nivå än standardvärdet (0.35). Detta gjordes för att uppnå en hanterbar arbetsbelastning i kombination med en kontrollerad risknivå.

Avslutningsvis genomförde vi ett sluttest för att få en uppfattning om hur väl modellen kan förväntas prestera i en verklig tillämpning.

## Arbetsfördelning

| Student | Ansvarsområde |
|---|---|
| Isabel | Data & EDA |
| Irene | Pipeline & preprocessing |
| Nora | Modelljämförelse |
| Ummulbanin | Optimering |
| Abdullahi | Threshold & prioritering |
| Linnéa | Pitch & risker |


## Installation

Klona repot och installera beroenden:  
`git clone https://github.com/emanuelssonlinnea-rgb/ML_Grupp5.git`

Skapa och aktivera virtuell miljö:  
`python -m venv .venv`

Windows PowerShell:  
`.venv\Scripts\Activate`

macOS/Linux:  
`source .venv/bin/activate`

installera beroenden:  
`cd ML_Grupp5 python -m pip install -r requirements.txt`


## Användning 

Öppna och kör följande notebook:  

1. `report.ipynb` — Innehåller EDA, preprocessing och pipeline


## Miljö

Python: 3.13.7  
Paket: Numpy, Pandas, Matplotlib, Jupyter, scikit-learn (se requirements.txt)  