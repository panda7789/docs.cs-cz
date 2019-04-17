---
title: Úlohy strojového učení – ML.NET
description: Prozkoumejte různé strojového učení úkoly a přidružené úlohy, které jsou podporovány v ML.NET.
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613158"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Úlohy strojového učení v ML.NET

Při sestavování model strojového učení, musíte nejprve definovat jsou doufá dosáhnout s vašimi daty. To umožňuje zvolit správný strojového učení úkol pro konkrétní situaci. Následující seznam popisuje různé strojového učení úlohy, které můžete vybrat z a některé běžné případy použití.

Až si ověříte, které úloha se dá použít pro váš scénář, pak musíte zvolit nejlepší algoritmus k natrénování modelu. K dispozici algoritmy jsou uvedené v části pro každý úkol.

## <a name="binary-classification"></a>Binární klasifikace

A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi, které instance dat patří do dvou tříd (kategorie). Vstup klasifikační algoritmus je sada s popiskem příklady, kde každý popisek je celé číslo 0 nebo 1. Výstupní binární klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku. Příklady scénářů binární klasifikace:

* [Principy mínění Twitteru, komentářů](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".
* Diagnostika zda pacienta má určitá stádiu, nebo ne.
* Rozhodování k označení e-mailu jako "nevyžádanou poštu" nebo ne.
* Určení, zda obsahuje fotografii dog nebo výsledku.

Další informace najdete v tématu [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) článku na wikipedii.

### <a name="binary-classification-training-algorithms"></a>Binární klasifikace trénování algoritmů

Trénovat binární klasifikační model pomocí tyto algoritmy:

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a>Klasifikace víc tříd

A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi třídu instance data (kategorie). Vstup klasifikační algoritmus je sada s popiskem příklady. Každý popisek normálně spustí jako text. Následně se spustí prostřednictvím TermTransform, který převádí na typ klíče (číselné). Výstup klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku. Příklady scénářů roc klasifikace:

* Určení emulátorem pes jako "Siberian Husky", "Golden načítací", "Co", atd.
* Principy film revize jako "kladné", "neutrální" nebo "záporné".
* Kategorizace hotelu revize jako "umístění", "price", "čistota" atd.

Další informace najdete v tématu [klasifikace víc tříd](https://en.wikipedia.org/wiki/Multiclass_classification) článku na wikipedii.

>[!NOTE]
>Jeden vs všechny upgraduje všechny [binární klasifikace learner](#binary-classification) k práci s více třídami datové sady. Další informace o [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-training-algorithms"></a>Víc tříd klasifikace trénování algoritmů

Trénovat klasifikace víc tříd modelu pomocí následujících trénování algoritmů:

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a>Regrese

A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi hodnota popisku na základě sady souvisejících funkcí. Popisek může být libovolné skutečné hodnoty a je neumožňují omezenou sadu hodnot jako úlohy klasifikace. Regresní model algoritmy závislost popisek na jeho související funkce, chcete-li zjistit, jak se změní popisek jako hodnoty funkcí se lišily. Vstup regresního algoritmu je sada příklady s popisky známé hodnoty. Výstup tohoto regresního algoritmu je funkce, které můžete použít k predikci hodnoty popisku pro všechny nové sady vstupní funkce. Příklady scénářů regrese:

* Odhad ceny Domů na základě atributů house například počtu ložnic, umístění a velikosti.
* Předpovídání budoucích cenami akcií na základě historických dat a aktuální trendy na trhu.
* Předpověď prodeje podle inzerování rozpočty produktu.

### <a name="regression-training-algorithms"></a>Regrese trénování algoritmů

Trénovat regresního modelu pomocí tyto algoritmy:

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a>Vytváření clusterů

[Nastavenou možnost bez dohledu strojového učení](glossary.md#unsupervised-machine-learning) úlohu, která se používá k skupiny instancí data do clusterů obsahující podobné charakteristiky. Clustering lze také identifikovat relací v datové sadě, která nemusí být odvozena logicky sledováním procházení nebo jednoduché. Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodě. Můžete provést distribuci, těžiště, připojení nebo přístup založený na hustotě. ML.NET v současné době podporuje přístup na základě těžiště pomocí K-Means clustering. Příklady scénáře clusteringu:

* Principy segmenty hotelu hostů na základě zvyklosti a charakteristiky hotelu voleb.
* Identifikace segmenty uživatelů a demografických údajů, které vám pomůžou vytvářet cílené reklamní kampaně.
* Kategorizace podle výrobní metriky inventáře.

### <a name="clustering-training-algorithms"></a>Clustering trénování algoritmů

Trénovat model clusteringu pomocí následující požadovaný algoritmus:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a>Detekce anomálií

Tato úloha vytváří model detekce anomálií pomocí analýzy hlavní součásti (DPS). Detekce anomálií založená na PCA umožňuje sestavit model ve scénářích, kde je snadné získat trénovací data z jedné třídy, jako jsou platné transakce, ale obtížné dostatečná ukázky cílové anomálie.

Zavedený postup ve službě machine learning, DPS se často používá na analýzu dat průzkumného testování, protože odhalí vnitřní strukturu dat a vysvětluje variance v datech. DPS funguje díky analýze dat, která obsahuje více proměnných. Hledá korelace mezi proměnné a určuje kombinace hodnot, které nejlépe zachycuje rozdíly ve výsledcích. Tyto funkce kombinované hodnoty slouží k vytvoření kompaktnějším místo funkce nazývané jako hlavní komponenty.

Detekce anomálií zahrnuje mnoho důležitých úloh ve službě machine learning:

* Identifikace transakcí, které jsou potenciálně podvodný.
* Učení vzorce, které naznačují, že došlo k napadení sítě.
* Hledání neobvyklé clustery pacientů.
* Kontrola hodnoty zadané do systému.

Vzhledem k tomu anomálie výjimečné události podle definice, může být obtížné ke shromažďování dat pro modelování reprezentativní vzorek. Algoritmy zahrnuté v této kategorii jsou obzvláště navržené pro řeší problémy základní stavební a trénování modelů s použitím imbalanced datových sad.

### <a name="anomaly-detection-training-algorithms"></a>Algoritmy školení detekce anomálií

Můžete trénování modelu detekce anomálií pomocí následující požadovaný algoritmus:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a>Hodnocení

Pořadí úkolů vytvoří klasifikátor ze sady s popiskem příklady. Tato sada příklad se skládá ze skupiny instancí, které mohou být upraveny pomocí zadaných kritérií. Hodnocení popisky jsou pro každou instanci {0, 1, 2, 3, 4}.  Klasifikátor je vyškolit tak, aby pořadí nové instance skupiny s Neznámý skóre, které se pro každou instanci. Inteligentních algoritmů ML.NET hodnocení jsou [počítače se dozvěděli, hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) založené.

### <a name="ranking-training-algorithms"></a>Hodnocení trénování algoritmů

Můžete vyškolíme model pořadí pomocí tyto algoritmy:

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a>Doporučení

Doporučení úloh umožňuje vytváření seznam doporučených produktů nebo služeb. Používá ML.NET [factorization matice (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrování založeného na spolupráci](https://en.wikipedia.org/wiki/Collaborative_filtering) algoritmus doporučení, když máte data hodnocení historických produktu ve vašem katalogu. Například máte data o filmech historických hodnocení pro vaše uživatele a chcete doporučit další filmů, ve které je pravděpodobně podívejte se na další.

### <a name="recommendation-training-algorithms"></a>Doporučení trénování algoritmů

Můžete vyškolíme model doporučení pomocí následující požadovaný algoritmus:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
