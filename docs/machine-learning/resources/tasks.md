---
title: Úlohy strojového učení – ML.NET
description: Prozkoumejte různé strojového učení úkoly a přidružené inteligentních algoritmů, které jsou podporovány v ML.NET.
ms.custom: seodec18
ms.date: 01/14/2019
author: jralexander
ms.openlocfilehash: 32a785a28a02b936ab92f6b3a3c4c5abbbf73315
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307406"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Úlohy strojového učení v ML.NET

Při sestavování model strojového učení, musíte nejprve definovat jsou doufá dosáhnout s vašimi daty. Později můžete si vybrat úlohu učení správné počítače pro vaši situaci. Následující seznam popisuje různé strojového učení úlohy, které můžete vybrat z a některé běžné případy použití.

> [!NOTE]
> ML.NET je aktuálně ve verzi Preview. Ne všechny úlohy strojového učení se aktuálně nepodporuje. Chcete-li odeslat žádost o určitý úkol, otevřete problém ve službě [úložišti dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues).

## <a name="binary-classification"></a>Binární klasifikace

A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi, které instance dat patří do dvou tříd (kategorie). Vstup klasifikační algoritmus je sada s popiskem příklady, kde každý popisek je celé číslo 0 nebo 1. Výstupní binární klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku. Příklady scénářů binární klasifikace:

* [Principy mínění Twitteru, komentářů](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".
* Diagnostika zda pacienta má určitá stádiu, nebo ne.
* Rozhodování k označení e-mailu jako "nevyžádanou poštu" nebo ne.
* Určení, zda obsahuje fotografii dog nebo výsledku.

Další informace najdete v tématu [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) článku na wikipedii.

Doporučené inteligentních algoritmů pro binární klasifikace:

* AveragedPerceptronTrainer
* StochasticGradientDescentClassificationTrainer
* LightGbmBinaryTrainer
* FastTreeBinaryClassificationTrainer
* SymSgdClassificationTrainer

### <a name="binary-classification-learners"></a>Binární klasifikace studentů

Následující inteligentních algoritmů jsou k dispozici pro úlohy binární klasifikace:

* [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.Online.AveragedPerceptronTrainer)
* [BinaryClassificationGamTrainer](xref:Microsoft.ML.Trainers.FastTree.BinaryClassificationGamTrainer)
* [FastForestClassification](xref:Microsoft.ML.Trainers.FastTree.FastForestClassification)
* [FastTreeBinaryClassificationTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer)
* [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.FactorizationMachine.FieldAwareFactorizationMachineTrainer)
* [LightGbmBinaryTrainer](xref:Microsoft.ML.LightGBM.LightGbmBinaryTrainer)
* [LinearSvm](xref:Microsoft.ML.Trainers.Online.LinearSvm)
* [PriorTrainer](xref:Microsoft.ML.Trainers.PriorTrainer)
* [RandomTrainer](xref:Microsoft.ML.Trainers.RandomTrainer)
* [StochasticGradientDescentClassificationTrainer](xref:Microsoft.ML.Trainers.StochasticGradientDescentClassificationTrainer)
* [SymSgdClassificationTrainer](xref:Microsoft.ML.Trainers.SymSgd.SymSgdClassificationTrainer)

## <a name="multiclass-classification"></a>Klasifikace víc tříd

A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi třídu instance data (kategorie). Vstup klasifikační algoritmus je sada s popiskem příklady. Každý popisek normálně spustí jako text. Následně se spustí prostřednictvím TermTransform, který převádí na typ klíče (číselné). Výstup klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku. Příklady scénářů roc klasifikace:

* Určení emulátorem pes jako "Siberian Husky", "Golden načítací", "Co", atd.
* Principy film revize jako "kladné", "neutrální" nebo "záporné".
* Kategorizace hotelu revize jako "umístění", "price", "čistota" atd.

Další informace najdete v tématu [klasifikace víc tříd](https://en.wikipedia.org/wiki/Multiclass_classification) článku na wikipedii.

Doporučené inteligentních algoritmů pro více třídu:

* OVA-AveragedPerceptronTrainer
* SdcaMultiClassTrainer
* LightGbmMulticlassTrainer
* OVA-FastTreeBinaryClassificationTrainer

>[!NOTE]
>Soubory OVA a PKPD upgraduje všechny [binární klasifikace learner](#binary-classification) k práci s více třídami datové sady. Další informace o [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-learners"></a>Klasifikace víc tříd studentů

Pro úlohy klasifikace víc tříd k dispozici jsou následující inteligentních algoritmů:

* [LightGbmMulticlassTrainer](xref:Microsoft.ML.LightGBM.LightGbmMulticlassTrainer)
* [MetaMulticlassTrainer < TTransformer, TModel >](xref:Microsoft.ML.Learners.MetaMulticlassTrainer%602)
* [MultiClassClassificationTrainers](xref:Microsoft.ML.Trainers.MultiClassClassificationTrainers)
* [MultiClassNaiveBayesTrainer](xref:Microsoft.ML.Trainers.MultiClassNaiveBayesTrainer)
* [Ova](xref:Microsoft.ML.Trainers.Ova)
* [Pkpd](xref:Microsoft.ML.Trainers.Pkpd)
* [SdcaMultiClassTrainer](xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer)

## <a name="regression"></a>Regrese

A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi hodnota popisku na základě sady souvisejících funkcí. Popisek může být libovolné skutečné hodnoty a je neumožňují omezenou sadu hodnot jako úlohy klasifikace. Regresní model algoritmy závislost popisek na jeho související funkce, chcete-li zjistit, jak se změní popisek jako hodnoty funkcí se lišily. Vstup regresního algoritmu je sada příklady s popisky známé hodnoty. Výstup tohoto regresního algoritmu je funkce, které můžete použít k predikci hodnoty popisku pro všechny nové sady vstupní funkce. Příklady scénářů regrese:

* Odhad ceny Domů na základě atributů house například počtu ložnic, umístění a velikosti.
* Předpovídání budoucích cenami akcií na základě historických dat a aktuální trendy na trhu.
* Předpověď prodeje podle inzerování rozpočty produktu.

Doporučené inteligentních algoritmů pro regresní:

* FastTreeTweedieTrainer 
* LightGbmRegressorTrainer 
* SdcaRegressionTrainer 
* FastTreeRegressionTrainer

### <a name="regression-learners"></a>Regrese studentů

Následující inteligentních algoritmů jsou k dispozici pro regresní úlohy:

* [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer)
* [FastTreeRegressionFastTreeTrainer](xref:Microsoft.ML.Runtime.FastTreeRegressionFastTreeTrainer)
* [FastTreeTweedieTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer)
* [LightGbmRegressorTrainer](xref:Microsoft.ML.LightGBM.LightGbmRegressorTrainer)
* [LogisticRegression](xref:Microsoft.ML.Learners.LogisticRegression)
* [OlsLinearRegressionTrainer](xref:Microsoft.ML.Trainers.HalLearners.OlsLinearRegressionTrainer)
* [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.Online.OnlineGradientDescentTrainer)
* [PoissonRegression](xref:Microsoft.ML.Trainers.PoissonRegression)
* [RegressionGamTrainer](xref:Microsoft.ML.Trainers.FastTree.RegressionGamTrainer)
* [SdcaRegressionTrainer](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)
* [FastTree.SingleTrainer](xref:Microsoft.ML.Trainers.FastTree.SingleTrainer)
* [LightGBM.SingleTrainer](xref:Microsoft.ML.LightGBM.SingleTrainer)

## <a name="clustering"></a>Vytváření clusterů

[Nastavenou možnost bez dohledu strojového učení](glossary.md#unsupervised-machine-learning) úlohu, která se používá k skupiny instancí data do clusterů obsahující podobné charakteristiky. Clustering lze také identifikovat relací v datové sadě, která nemusí být odvozena logicky sledováním procházení nebo jednoduché. Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodě. Můžete provést distribuci, těžiště, připojení nebo přístup založený na hustotě. ML.NET v současné době podporuje přístup na základě těžiště pomocí K-Means clustering. Příklady scénáře clusteringu:

* Principy segmenty hotelu hostů na základě zvyklosti a charakteristiky hotelu voleb.
* Identifikace segmenty uživatelů a demografických údajů, které vám pomůžou vytvářet cílené reklamní kampaně.
* Kategorizace podle výrobní metriky inventáře.

### <a name="clustering-learners"></a>Clustering inteligentních algoritmů

Následující inteligentních algoritmů jsou k dispozici pro clustering s úkoly:

* [KMeansPlusPlusTrainer](xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer)

## <a name="anomaly-detection"></a>Detekce anomálií

Tato úloha vytváří model detekce anomálií pomocí analýzy hlavní součásti (DPS). Detekce anomálií založená na PCA umožňuje sestavit model ve scénářích, kde je snadné získat trénovací data z jedné třídy, jako jsou platné transakce, ale obtížné dostatečná ukázky cílové anomálie.

Zavedený postup ve službě machine learning, DPS se často používá na analýzu dat průzkumného testování, protože odhalí vnitřní strukturu dat a vysvětluje variance v datech. DPS funguje díky analýze dat, která obsahuje více proměnných. Hledá korelace mezi proměnné a určuje kombinace hodnot, které nejlépe zachycuje rozdíly ve výsledcích. Tyto funkce kombinované hodnoty slouží k vytvoření kompaktnějším místo funkce nazývané jako hlavní komponenty.

Detekce anomálií zahrnuje mnoho důležitých úloh ve službě machine learning:

* Identifikace transakcí, které jsou potenciálně podvodný.
* Učení vzorce, které naznačují, že došlo k napadení sítě.
* Hledání neobvyklé clustery pacientů.
* Kontrola hodnoty zadané do systému.

Vzhledem k tomu anomálie výjimečné události podle definice, může být obtížné ke shromažďování dat pro modelování reprezentativní vzorek. Algoritmy zahrnuté v této kategorii jsou obzvláště navržené pro řeší problémy základní stavební a trénování modelů s použitím imbalanced datových sad.

### <a name="anomaly-detection-learners"></a>Detekce anomálií inteligentních algoritmů

Následující inteligentních algoritmů jsou k dispozici pro úlohy zjišťování anomálií:

* [RandomizedPcaTrainer](xref:Microsoft.ML.Trainers.PCA.RandomizedPcaTrainer)

## <a name="ranking"></a>Hodnocení

Pořadí úkolů vytvoří klasifikátor ze sady s popiskem příklady. Tato sada příklad se skládá ze skupiny instancí, které mohou být upraveny pomocí zadaných kritérií. Hodnocení popisky jsou pro každou instanci {0, 1, 2, 3, 4}.  Klasifikátor je vyškolit tak, aby pořadí nové instance skupiny s Neznámý skóre, které se pro každou instanci. Inteligentních algoritmů ML.NET hodnocení jsou [počítače se dozvěděli, hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) založené.

### <a name="ranking-learners"></a>Hodnocení inteligentních algoritmů

Pro pořadí úloh k dispozici jsou následující inteligentních algoritmů:

* [FastTreeRankingTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer)
* [LightGbmRankingTrainer](xref:Microsoft.ML.LightGBM.LightGbmRankingTrainer)

## <a name="recommendation"></a>Doporučení

Doporučení úloh umožňuje vytváření seznam doporučených produktů nebo služeb. Používá ML.NET [factorization matice (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrování založeného na spolupráci](https://en.wikipedia.org/wiki/Collaborative_filtering) algoritmus doporučení, když máte data hodnocení historických produktu ve vašem katalogu. Například máte data o filmech historických hodnocení pro vaše uživatele a chcete doporučit další filmů, ve které je pravděpodobně podívejte se na další.

### <a name="recommendation-learners"></a>Doporučení studentů

Následující inteligentních algoritmů jsou k dispozici pro úlohy doporučení:

* [MatrixFactorizationTrainer](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer)
* [MatrixFactorizationPredictionTransformer](xref:Microsoft.ML.Trainers.Recommender.MatrixFactorizationPredictionTransformer)
