---
title: Úkoly strojového učení
description: Prozkoumejte různé úlohy strojového učení a související úlohy, které jsou podporované v ML.NET.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: d0634ce8a0559ab3cdb5bf27fc5406ab02af8df6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977245"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Úlohy strojového učení v ML.NET

Při sestavování modelu strojového učení nejdřív musíte definovat, co se vám doufá že k dosažení vašich dat. Díky tomu můžete zvolit správnou úlohu strojového učení pro vaši situaci. V následujícím seznamu jsou popsány různé úlohy strojového učení, ze kterých si můžete vybrat, a některé běžné případy použití. Další informace o výběru úlohy, která je vhodná pro váš scénář, najdete v tématu [algoritmy](../how-to-choose-an-ml-net-algorithm.md).

Jakmile se rozhodnete, který úkol pro váš scénář funguje, musíte zvolit nejlepší algoritmus pro vyučování modelu. Dostupné algoritmy jsou uvedené v části pro každý úkol.

## <a name="binary-classification"></a>binární klasifikace

Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovídání dvou tříd (kategorií), do kterých patří instance dat. Vstup klasifikačního algoritmu je sada popisných příkladů, kde je každý popisek celé číslo 0 nebo 1. Výstup binárního klasifikačního algoritmu je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí. Mezi příklady scénářů binární klasifikace patří:

* [Princip mínění komentářů na Twitteru](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".
* Diagnostikuje, jestli má pacient určitou chorobu nebo ne.
* Rozhodování o označení e-mailu jako "spam" nebo ne.
* Určení, jestli fotka obsahuje určitou položku, například pes nebo ovoce.

Další informace najdete v článku o [binární klasifikaci](https://en.wikipedia.org/wiki/Binary_classification) v Wikipedii.

### <a name="binary-classification-trainers"></a>Školitele binární klasifikace

Model binární klasifikace můžete proškolit pomocí těchto algoritmů:

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

### <a name="binary-classification-inputs-and-outputs"></a>Binární vstupy a výstupy klasifikace

Pro dosažení nejlepších výsledků s binární klasifikací musí být školicí data vyvážená (tj. stejná čísla kladných a záporných školicích dat). Před školením by měly být zpracovány chybějící hodnoty.

Data sloupce vstupního popisku musí být <xref:System.Boolean>.
Data ve sloupci vstupní funkce musí být vektorem s pevnou velikostí <xref:System.Single>.

Výstup učitelů má následující sloupce:

| Název výstupního sloupce | Typ sloupce | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nezpracované skóre, které bylo vypočítáno modelem|
| `PredictedLabel` | <xref:System.Boolean> | Předpokládaný popisek, založený na znaménku skóre. Záporné skóre se mapuje na `false` a kladné skóre se mapuje na `true`.|

## <a name="multiclass-classification"></a>klasifikace s více třídami

Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předvídání třídy dat instance. Vstup algoritmu klasifikace je sada příkladů s popisky. Každý popisek normálně začíná jako text. Pak se spustí přes TermTransform, který ho převede na klíč (číselný) typ. Výstup algoritmu klasifikace je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí. Mezi příklady scénářů klasifikace s více třídami patří:

* Určení plemene psa jako "Siberian Husky", "zlatý spuštění metody Retriever", "Poodle" atd.
* Pochopíte recenze filmů jako "pozitivní", "neutrální" nebo "negativní".
* Kategorizace hodnocení hotelu jako "umístění", "cena", "čistota" atd.

Další informace naleznete v článku o třídě s více [třídami](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.

>[!NOTE]
>Jedna sada vs všechno upgraduje libovolný [postup binární klasifikace](#binary-classification) , aby fungovala u datových sad s více třídami. Další informace o [Wikipedii] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-trainers"></a>Školitel klasifikace s více třídami

Model klasifikace s více třídami můžete proškolit pomocí následujících školicích algoritmů:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a>Vstupy a výstupy s více třídami klasifikace

Data sloupce vstupního popisku musí být typu [Key](xref:Microsoft.ML.Data.KeyDataViewType) .
Sloupec funkce musí být vektorem pevné velikosti <xref:System.Single>.

Tento Trainer má následující výstup:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | vektor <xref:System.Single> | Skóre všech tříd. Vyšší hodnota znamená vyšší pravděpodobnost pro přechod do přidružené třídy. Pokud má i-th největší hodnotu, index předpokládaného popisku by byl i. Všimněte si, že je index založený na nule. |
| `PredictedLabel` | typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType) | Index předpokládaného popisku. Pokud je jeho hodnota, vlastní popisek bude i-th kategorie v typu vstupního popisku s hodnotou klíče. |

## <a name="regression"></a>Nevýhody

Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovědi hodnoty popisku ze sady souvisejících funkcí. Popisek může být jakékoli reálné hodnoty a nepochází z konečné sady hodnot jako v rámci úloh klasifikace. Regresní algoritmy modelují závislost popisku na jeho souvisejících funkcích, aby určili, jak se popisek změní, protože hodnoty funkcí se mění. Vstup regresního algoritmu je sada příkladů s popisky známých hodnot. Výstupem regresního algoritmu je funkce, kterou můžete použít k předpovědi hodnoty popisku pro všechny nové sady vstupních funkcí. Mezi příklady scénářů regrese patří:

* Předvídání cen domu na základě atributů na pracovišti, jako je počet ložnicemi, umístění nebo velikost.
* Předvídání budoucích cen za ceny na základě historických dat a současných vývojů na trhu.
* Předvídání prodeje produktů na základě reklamních rozpočtů.

### <a name="regression-trainers"></a>Regresní školitele

Regresní model můžete naučit pomocí těchto algoritmů:

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Regrese – vstupy a výstupy

Data sloupce vstupního popisku musí být <xref:System.Single>.

Školitel pro tento úkol má následující výstup:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nezpracované skóre, které model předpovídá |

## <a name="clustering"></a>Clustering

Úkol [strojového učení, který není pod dohledem](glossary.md#unsupervised-machine-learning) , který se používá k seskupení instancí dat do clusterů, které obsahují podobné charakteristiky. Clustering lze také použít k identifikaci relací v datové sadě, které nemůžete logicky odvodit pomocí procházení nebo jednoduchého sledování. Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodologii. Můžete provést distribuci, těžiště, připojení nebo přístup na základě hustoty. ML.NET aktuálně podporuje přístup založený na těžiště pomocí K-znamená clustering. Mezi příklady scénářů clusteringu patří:

* Porozumění segmentům hostů v hotelovém typu na základě zvyklostí a vlastností možností hotelu.
* Identifikujte segmenty zákazníků a demografické údaje, které vám pomůžou vytvářet cílené reklamní kampaně.
* Kategorizace inventáře na základě výrobních metrik.

### <a name="clustering-trainer"></a>Clustering Trainer

Model clusteringu můžete proškolit pomocí následujícího algoritmu:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a>Vstupy a výstupy clusteringu

Data funkcí input musí být <xref:System.Single>. Nejsou nutné žádné popisky.

Tento Trainer má následující výstup:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | vektor <xref:System.Single> | Vzdálenosti daného datového bodu ke všem clusterům ' centriods |
| `PredictedLabel` | typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType) | Index nejbližšího clusteru předpokládaný modelem. |

## <a name="anomaly-detection"></a>Detekce anomálií

Tato úloha vytvoří model detekce anomálií pomocí hlavní komponenty pro analýzu (DPS). Detekce anomálií založená na DPS vám pomůže sestavit model ve scénářích, kdy je snadné získat školicí data z jedné třídy, jako jsou platné transakce, ale obtížně získat dostatečné vzorky cílových anomálií.

V rámci strojového učení se často používá příhlas POMOCNÍKa při analýze dat, protože odhalí vnitřní strukturu dat a vysvětluje odchylku dat. Funkce DPS funguje při analýze dat, která obsahují více proměnných. Vyhledá korelaci mezi proměnnými a určí kombinaci hodnot, které nejlépe zachytí rozdíly ve výsledcích. Tyto kombinované hodnoty funkcí slouží k vytvoření kompaktnějšího prostoru funkcí označovaného jako hlavní komponenty.

Detekce anomálií zahrnuje mnoho důležitých úloh ve strojovém učení:

* Identifikujte transakce, které jsou potenciálně podvodné.
* Výukové modely indikující, že došlo k narušení sítě.
* Hledání neobvyklých clusterů pacientů.
* Kontrola hodnot zadaných do systému.

Vzhledem k tomu, že anomálie jsou vzácné události podle definice, může být obtížné shromáždit reprezentativní vzorek dat, který se má použít pro modelování. Algoritmy zahrnuté v této kategorii byly obzvláště navržené pro řešení základních výzev k sestavování a školení modelů pomocí nevyvážených datových sad.

### <a name="anomaly-detection-trainer"></a>Trainer detekce anomálií

Model detekce anomálií můžete vyškolit pomocí následujícího algoritmu:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Vstupy a výstupy detekce anomálií

Vstupní funkce musí být vektor <xref:System.Single>pevné velikosti.

Tento Trainer má následující výstup:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nezáporné, neohraničené skóre, které bylo vypočítáno modelem detekce anomálií |

## <a name="ranking"></a>Pořadí

Úkol hodnocení sestaví seřazení ze sady popisných příkladů. Tato ukázková sada se skládá ze skupin instancí, jejichž skóre se dá vyhodnotit pomocí daných kritérií. Popisky hodnocení jsou pro každou instanci {0, 1, 2, 3, 4}.  Klasifikátor je vyškolen pro řazení nových skupin instancí s neznámým skóre pro každou instanci. Seznámení s ML.NETm řazením [počítačů se seznámili podle hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) .

### <a name="ranking-training-algorithms"></a>Hodnocení školicích algoritmů

Model hodnocení můžete proškolit s následujícími algoritmy:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a>Řazení vstupů a výstupů

Vstupní datový typ popisku musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) nebo <xref:System.Single>. Hodnota popisku určuje relevanci, kde vyšší hodnoty označují vyšší relevanci. Pokud je popisek typem [klíče](xref:Microsoft.ML.Data.KeyDataViewType) , pak je index klíče hodnota významnosti, kde nejmenší index je nejméně relevantní. Pokud je popisek <xref:System.Single>, větší hodnoty znamenají vyšší relevance.

Data funkce musí být vektorem pevné velikosti <xref:System.Single> a sloupec vstupní skupiny řádků musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) .

Tento Trainer má následující výstup:

| Název výstupu | Typ | Popis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Neohraničené skóre, které bylo vypočítáno modelem k určení předpovědi |

## <a name="recommendation"></a>Základě

Úkol doporučení umožňuje vytvořit seznam doporučených produktů nebo služeb. ML.NET používá pro doporučení algoritmus pro [filtrování](https://en.wikipedia.org/wiki/Collaborative_filtering) a vytváření [matic (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), pokud máte historická data hodnocení produktu ve vašem katalogu. Máte například historická data o hodnocení filmu pro vaše uživatele a chcete doporučit další filmy, které se budou pravděpodobně sledovat.

### <a name="recommendation-training-algorithms"></a>Algoritmy školení pro doporučení

Model doporučení můžete vyškolit pomocí následujícího algoritmu:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
