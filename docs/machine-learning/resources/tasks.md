---
title: Úkoly strojového učení
description: Prozkoumejte různé úkoly strojového učení a související úkoly, které jsou podporovány v ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399201"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Úlohy strojového učení v ML.NET

Úloha strojového učení je typ predikce nebo odvození, které se provádí, na základě problému nebo otázky, která je kladena, a dostupných dat. Například úkol klasifikace přiřazuje data kategoriím a clustering úkoly seskupí data podle podobnosti.

Úlohy strojového učení spoléhají na vzory v datech, nikoli na explicitně naprogramované.

Tento článek popisuje různé úkoly strojového učení, ze kterých si můžete vybrat v ML.NET a některé běžné případy použití.

Jakmile jste se rozhodli, který úkol funguje pro váš scénář, musíte zvolit nejlepší algoritmus pro trénování modelu. Dostupné algoritmy jsou uvedeny v části pro každý úkol.

## <a name="binary-classification"></a>Binární klasifikace

Úkol [strojového učení pod dohledem,](glossary.md#supervised-machine-learning) který se používá k předvídání, do kterých dvou tříd (kategorií) patří instance dat. Vstup klasifikační algoritmus je sada popisek příklady, kde každý popisek je celé číslo buď 0 nebo 1. Výstup binární klasifikační algoritmus je třídění, které můžete použít k předpovědět třídu nových instancí bez popisku. Příklady binárních scénářů klasifikace zahrnují:

* [Pochopení sentimentu komentářů Twitter](../tutorials/sentiment-analysis.md) jako "pozitivní" nebo "negativní".
* Diagnostika, zda má pacient určitou nemoc nebo ne.
* Rozhodování o označení e-mailu jako "spam", nebo ne.
* Určení, zda fotografie obsahuje určitou položku nebo ne, například psa nebo ovoce.

Další informace naleznete v článku [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) na Wikipedii.

### <a name="binary-classification-trainers"></a>Binární klasifikace školitelů

Binární klasifikační model můžete trénovat pomocí následujících algoritmů:

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a>Binární klasifikační vstupy a výstupy

Pro dosažení nejlepších výsledků s binární klasifikací by měla být vyvážená data školení (to znamená stejný počet pozitivních a záporných trénovacích dat). Chybějící hodnoty by měly být zpracovány před tréninkem.

Data sloupce vstupního <xref:System.Boolean>popisku musí být .
Data sloupce vstupnífunkce musí být vektor <xref:System.Single>pevné velikosti .

Tyto školicí prvky výstup následující sloupce:

| Název výstupního sloupce | Typ sloupce | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Hrubé skóre, které bylo vypočteno modelem|
| `PredictedLabel` | <xref:System.Boolean> | Předpovídaný popisek, na základě znaménko skóre. Negativní skóre mapuje a `false` pozitivní `true`skóre mapuje na .|

## <a name="multiclass-classification"></a>Klasifikace více tříd

Úkol [strojového učení pod dohledem,](glossary.md#supervised-machine-learning) který se používá k předvídání třídy (kategorie) instance dat. Vstup klasifikačníalgoritmus je sada popisek příklady. Každý popisek obvykle začíná jako text. Potom je spuštěn prostřednictvím TermTransform, který převádí na klíč (číselný) typ. Výstup klasifikačního algoritmu je třídění, které můžete použít k předvídání třídy nových instancí bez popisku. Příklady scénářů klasifikace více tříd:

* Určení plemene psa jako "sibiřského Huskyho", "Zlatého retrívra", "Pudla" atd.
* Pochopení filmové recenze jako "pozitivní", "neutrální", nebo "negativní".
* Kategorizace recenzí hotelů jako "umístění", "cena", "čistota" atd.

Další informace naleznete v článku [klasifikace více tříd](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.

>[!NOTE]
>Jeden vs všechny upgrady jakékoli [binární klasifikace studenta](#binary-classification) jednat o vícetřídových datových sad. Více informací o [Wikipedii] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-trainers"></a>Vícetřídní klasifikační trenažér

Můžete trénovat vícetřídní klasifikační model pomocí následujících trénovacích algoritmů:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a>Vícetřídní klasifikační vstupy a výstupy

Data sloupce vstupního popisku musí být typ [klíče.](xref:Microsoft.ML.Data.KeyDataViewType)
Sloupec prvku musí být vektor <xref:System.Single>pevné velikosti .

Tento trenažér výstupy následující:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | Vektor<xref:System.Single> | Skóre všech tříd. Vyšší hodnota znamená vyšší pravděpodobnost, že spadají do přidružené třídy. Pokud i-th element má největší hodnotu, by byl index předpovídaný popisek i. Všimněte si, že i je nula-založené index. |
| `PredictedLabel` | typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType) | Index předpovídaného popisku. Pokud je jeho hodnota i, skutečný popisek by byla i-th kategorie v typu vstupní popisek s hodnotou klíče. |

## <a name="regression"></a>Regrese

Úkol [strojového učení pod dohledem,](glossary.md#supervised-machine-learning) který se používá k předvídání hodnoty popisku ze sady souvisejících funkcí. Popisek může mít libovolnou reálnou hodnotu a nepochází z omezené sady hodnot jako v úkolech klasifikace. Regresní algoritmy modelují závislost popisku na souvisejících funkcích, aby určily, jak se popisek bude měnit, protože hodnoty prvků se mění. Vstup regresníalgoritmus je sada příkladů s popisky známých hodnot. Výstup regresníalgoritmus je funkce, kterou můžete použít k předpovědět hodnotu popisku pro všechny nové sady vstupních funkcí. Příklady regresních scénářů:

* Předpovídání cen domů na základě atributů domu, jako je počet ložnic, umístění nebo velikost.
* Předpovídání budoucích cen akcií na základě historických údajů a současných tržních trendů.
* Předvídání prodeje produktu na základě rozpočtů na reklamu.

### <a name="regression-trainers"></a>Regresní trenéři

Regresní model můžete trénovat pomocí následujících algoritmů:

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Regresní vstupy a výstupy

Data sloupce vstupního <xref:System.Single>popisku musí být .

Školitelů pro tento úkol výstup následující:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Hrubé skóre, které bylo předpovězeno modelem |

## <a name="clustering"></a>Clustering

Úloha [strojového učení bez dozoru,](glossary.md#unsupervised-machine-learning) která se používá k seskupení instancí dat do clusterů, které obsahují podobné charakteristiky. Clustering lze také použít k identifikaci vztahů v datové sadě, které nemusí logicky odvodit procházením nebo jednoduchým pozorováním. Vstupy a výstupy clustering algoritmu závisí na zvolené metodice. Můžete provést přístup založený na distribuci, centroidu, připojení nebo hustotě. ML.NET v současné době podporuje přístup založený na centroidu pomocí clusteringu K-Means. Příklady scénářů clusteringu:

* Pochopení segmentů hotelových hostů na základě návyků a charakteristik hotelové volby.
* Identifikace zákaznických segmentů a demografických údajů s cílem pomoci vytvářet cílené reklamní kampaně.
* Kategorizace zásob na základě výrobních metrik.

### <a name="clustering-trainer"></a>Shlukovací trenér

Model clusteringu můžete trénovat pomocí následujícího algoritmu:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a>Clustering vstupů a výstupů

Vstupní funkce data <xref:System.Single>musí být . Nejsou potřeba žádné štítky.

Tento trenažér výstupy následující:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | vektor<xref:System.Single> | Vzdálenosti daného datového bodu k centriodům všech klastrů |
| `PredictedLabel` | typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType) | Nejbližší index clusteru předpověděl model. |

## <a name="anomaly-detection"></a>Detekce anomálií

Tato úloha vytvoří model detekce anomálií pomocí analýzy primární chř složky (PCA). Detekce anomálií na základě PCA pomáhá vytvořit model ve scénářích, kde je snadné získat trénovací data z jedné třídy, jako jsou platné transakce, ale obtížné získat dostatečné vzorky cílené anomálie.

Zavedená technika ve strojovém učení, PCA se často používá v analýzě průzkumných dat, protože odhaluje vnitřní strukturu dat a vysvětluje odchylku v datech. PCA funguje tak, že analyzuje data, která obsahují více proměnných. Hledá korelace mezi proměnnými a určuje kombinaci hodnot, které nejlépe zachycuje rozdíly ve výsledcích. Tyto kombinované hodnoty prvků se používají k vytvoření kompaktnějšího prostoru prvku nazývaného hlavní součásti.

Detekce anomálií zahrnuje mnoho důležitých úkolů ve strojovém učení:

* Identifikace transakcí, které jsou potenciálně podvodné.
* Vzory učení, které označují, že došlo k narušení sítě.
* Hledání abnormálních shluků pacientů.
* Kontrola hodnot zadaných do systému.

Vzhledem k tomu, že anomálie jsou vzácné události podle definice, může být obtížné shromáždit reprezentativní vzorek dat pro modelování. Algoritmy zahrnuté v této kategorii byly speciálně navrženy tak, aby řešily hlavní problémy vytváření a školení pomocí nevyvážených datových sad.

### <a name="anomaly-detection-trainer"></a>Trenažér detekce anomálií

Model detekce anomálií můžete trénovat pomocí následujícího algoritmu:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Vstupy a výstupy detekce anomálií

Vstupní prvky musí být vektor pevné <xref:System.Single>velikosti .

Tento trenažér výstupy následující:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nezáporné, neomezené skóre, které bylo vypočteno modelem detekce anomálií |
| `PredictedLabel` | <xref:System.Boolean> | True/false hodnota představující, zda vstup je anomálie (PredictedLabel = true) nebo ne (PredictedLabel = false) |

## <a name="ranking"></a>Pořadí

Úkol hodnocení vytvoří ranker ze sady popisek příklady. Tato ukázková sada se skládá ze skupin instancí, které mohou být hodnoceny s danými kritérii. Popisky hodnocení jsou { 0, 1, 2, 3, 4 } pro každou instanci.  Ranker je trénován tak, aby seřadil nové skupiny instancí s neznámým skóre pro každou instanci. ML.NET žebříčků jsou [strojově naučené hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) založené.

### <a name="ranking-training-algorithms"></a>Algoritmy hodnocení

Můžete trénovat model hodnocení s následujícími algoritmy:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a>Pořadí vstupů a výstupů

Datový typ vstupního [key](xref:Microsoft.ML.Data.KeyDataViewType) popisku <xref:System.Single>musí být typ klíče nebo . Hodnota popisku určuje relevanci, kde vyšší hodnoty označují vyšší relevanci. Pokud je popisek typ [klíče,](xref:Microsoft.ML.Data.KeyDataViewType) pak index klíče je hodnota relevance, kde nejmenší index je nejméně relevantní. Pokud je popisek <xref:System.Single>, větší hodnoty označují vyšší relevanci.

Data prvku musí být vektor <xref:System.Single> pevné velikosti a sloupec skupiny vstupních řádků musí být typ [klíče.](xref:Microsoft.ML.Data.KeyDataViewType)

Tento trenažér výstupy následující:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Neomezené skóre, které bylo vypočteno modelem k určení předpovědi |

## <a name="recommendation"></a>Doporučení

Úloha doporučení umožňuje vytvoření seznamu doporučených produktů nebo služeb. ML.NET používá [maticovou faktorizaci (MF),](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)algoritmus [kolaborativního filtrování](https://en.wikipedia.org/wiki/Collaborative_filtering) pro doporučení, pokud máte v katalogu historická data hodnocení produktu. Máte například historická data hodnocení filmů pro uživatele a chcete doporučit další filmy, které budou pravděpodobně sledovat příště.

### <a name="recommendation-training-algorithms"></a>Algoritmy pro školení doporučení

Model doporučení můžete trénovat pomocí následujícího algoritmu:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a>Prognózování

Prognostické úkol použít minulé časové řady data, aby předpovědi o budoucím chování. Scénáře použitelné pro předpověď zahrnují předpověď počasí, předpovědi sezónních prodejů a prediktivní údržbu,

### <a name="forecasting-trainers"></a>Předvídání školitelů

Můžete trénovat model prognózy s následujícím algoritmem:

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
