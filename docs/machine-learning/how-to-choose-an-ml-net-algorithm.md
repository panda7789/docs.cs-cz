---
title: Jak vybrat algoritmus ML.NET
description: Zjistěte, jak vybrat algoritmus ML.NET pro váš model strojového učení
author: natke
ms.topic: overview
ms.date: 04/20/1029
ms.openlocfilehash: d1c637437a7b285f2b66b597d616fcf39248697f
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557786"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>Jak vybrat algoritmus ML.NET

Pro každou [ML.NET úloh](resources/tasks.md), existuje více školení algoritmy lze vybírat. Jak vybírat závisí na problému, který se snažíte vyřešit, charakteristiky vašich dat a výpočetních a úložných kapacit, které máte k dispozici. Je důležité si uvědomit, že trénování modelu strojového učení je iterativní proces. Můžete potřebovat vyzkoušet několik algoritmů, abyste našli ten nejvhodnější.

Algoritmy provádět **funkce**. Funkce jsou číselné hodnoty vypočítané ze vstupní data. Jsou optimální vstupy pro algoritmů strojového učení. Transformujte nezpracovaná vstupní data na funkce využívající jednu nebo více [transformací dat](resources/transforms.md). Například textová data se transformuje na sadu počty slov a počty kombinace slov. Jakmile se funkce byly extrahovány ze nezpracovaná data typu pomocí transformace dat, jsou označovány jako **natrénuje**. Například natrénuje text nebo natrénuje obrazová data.

## <a name="trainer--algorithm--task"></a>Trainer = algoritmus + úloh

Algoritmus je matematický výraz, který se spustí k vytvoření **modelu**. Různé algoritmy vytvářet modely s různými charakteristikami. 

S ML.NET můžete použít stejný algoritmus pro různé úkoly. Například pomocí Stochastického sestup koordinované Ascent slouží pro binární klasifikaci, Multiclass klasifikace a regrese. Rozdíl je v jak výstupu algoritmu je interpretován tak, aby odpovídaly úkolu. 

Pro každou kombinaci algoritmů nebo úlohou ML.NET obsahuje komponenty, která spustí cvičení algoritmu a provádí vyhodnocení. Tyto součásti se nazývají školitelé. Například <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> používá **StochasticDualCoordinatedAscent** algoritmus použitý k **regrese** úloh.

## <a name="linear-algorithms"></a>Lineární algoritmy

Lineární algoritmy vytvořit model, který vypočítá **skóre** z kombinace lineární vstupní data a sadu **váhy**. Váhy jsou parametry odhadované během cvičení modelu.

Lineární algoritmy fungovat dobře pro funkce, které jsou [lineárně oddělitelné](https://en.wikipedia.org/wiki/Linear_separability).

Před školení pomocí lineárního algoritmu, by měly být normalizovány funkce. Tím se předchází jedna funkce s více vliv výsledek než jiné.

Obecně lineární algoritmy jsou škálovatelné a rychle, levné tak moct trénovat, levné předpovědět. Jejich škálování řadu funkcí a přibližně velikost trénovací datové sady.

Lineární algoritmy provést několik průchodů za trénovací data. Pokud vaše datová sada se vejde do paměti, přidáte [kontrolního bodu mezipaměti](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) do kanálu ML.NET před připojením školitele, bude urychlit školení spuštění.

**Lineární školitelé**

|algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|průměrné perceptron|Nejvhodnější pro klasifikace textu|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Koordinované ascent stochastického sestup|Ladění není nutný pro dobré výchozí výkonu|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Použijte, když je velký počet funkcí. Vytvoří statistiku školení logistické regrese, ale neškáluje a také AveragedPerceptronTrainer|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Symbolické stochastického sestupu|Nejrychlejší a co nejvíce zpřesnili lineární binární klasifikace trainer. Škálování s počet procesorů|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Algoritmy rozhodovacího stromu

Algoritmy rozhodovacího stromu s vytvořit model, který obsahuje řadu rozhodnutí: efektivně vývojový diagram prostřednictvím datových hodnot.

Funkce není potřeba lineárně oddělitelné použití tohoto typu algoritmu. A funkce nemusí být normalizovány, vzhledem k tomu, že jednotlivé hodnoty ve vektoru funkce jsou nezávisle na sobě použít v rozhodovací proces.

Algoritmy rozhodovacího stromu jsou obecně velmi přesné.

S výjimkou zobecněný Additive modely (GAMs) můžete stromu modely nedostatku explainability, když je velký počet funkcí.

Algoritmy rozhodovacího stromu s využít další prostředky a není škálování i ty lineární udělat. Fungují dobře u datových sad, která se vejde do paměti.

Posílený rozhodovací stromy jsou kompletu malé stromové struktury, ve kterém každý stromu stanoví skóre vstupní data a předá do další stromu k vytvoření lepší skóre skóre a tak dále, kde každý stromu v skupiny stromů zlepšuje na předchozí.

**Rozhodovací strom školitelé**

|algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Světle přechodu Posílený počítače|Nejrychlejší a co nejvíce zpřesnili učitelů stromu binární klasifikace. Vysoce přizpůsobitelné|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Rychlé stromu|Používá se pro natrénuje obrazová data. Odolné vůči nevyváženou data. Vysoce přizpůsobitelné | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Rychlé doménové struktury|Funguje dobře s daty hlučného|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Model zobecněný sčítání (GAM)|Nejvhodnější pro problémy, které provádějí s algoritmy stromu, ale pokud explainability je prioritou|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Matice factorization

|Vlastnosti|Školitelé|
|----------|--------|
|Nejvhodnější pro zhuštěné zařazené do kategorií dat, s velkými datovými sadami|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algoritmy

Tyto školitelé vytvořit roc trainer binární trainer. Použití s <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.

|algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Jeden oproti vše|Tato víc tříd klasifikátor trénovat jeden binární třídění pro každou třídu, která odlišuje tuto třídu z jiné třídy. Má zobrazení omezenou škálování podle počtu tříd do kategorií|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Ukládání párování|Tato víc tříd klasifikátor trénovat binární klasifikační algoritmus na každý pár třídy. Je omezená škále počet tříd, protože každá kombinace dvou tříd musí být školení.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-Means

|Vlastnosti|Školitelé|
|----------|--------|
|Použití pro clustering|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Analýza hlavních komponentách

|Vlastnosti|Školitelé|
|----------|--------|
|Použijte k detekci anomálií|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Naive Bayes

|Vlastnosti|Školitelé|
|----------|--------|
|Tato klasifikace roc trainer použijte v případě funkce jsou nezávislé a trénovací datové sady je malý.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Předchozí Trainer

|Vlastnosti|Školitelé|
|----------|--------|
|Použijte tento binární klasifikační trainer do standardních hodnot výkonu jiných školitelé. Aby byla účinná, by měl být lepší než předchozí trainer metriky školitelé. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
