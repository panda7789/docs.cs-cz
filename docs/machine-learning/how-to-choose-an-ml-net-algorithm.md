---
title: Jak zvolit ML.NET algoritmus
description: Naučte se zvolit ML.NET algoritmus pro model služby Machine Learning.
ms.topic: overview
ms.date: 06/05/2019
ms.openlocfilehash: 0fed33203c02303e37e47f548e08ec131eeb1c77
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739992"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>Jak zvolit ML.NET algoritmus

Pro každý [úkol ml.NET](resources/tasks.md)existuje několik školicích algoritmů, ze kterých si můžete vybrat. Kterou si zvolíte, záleží na problému, který se snažíte vyřešit, charakteristiky vašich dat a výpočetní prostředky a prostředky úložiště, které máte k dispozici. Je důležité si uvědomit, že školení modelu Machine Learning je iterativní proces. Možná budete muset vyzkoušet několik algoritmů, abyste našli ten, který nejlépe vyhovuje.

Algoritmy fungují na **funkcích**. Funkce jsou číselné hodnoty vypočítané ze vstupních dat. Jsou to optimální vstupy pro algoritmy strojového učení. Nezpracované vstupní data můžete transformovat na funkce pomocí jedné nebo více transformací [dat](resources/transforms.md). Například textová data jsou transformovaná na sadu slov počty slov a počet kombinací slov. Po extrakci funkcí z nezpracovaných datových typů pomocí transformací dat se označují jako **natrénuje**. Například natrénuje text nebo natrénuje data obrázku.

## <a name="trainer--algorithm--task"></a>Trainer = Algorithm + úloha

Algoritmus je matematický, který se spouští k vytvoření **modelu**. Různé algoritmy vytváří modely s různými charakteristikami.

Pomocí ML.NET je možné použít stejný algoritmus pro různé úlohy. Například stochastického Dual koordinované stoupání lze použít pro binární klasifikaci, více tříd a regresi. Rozdíl je ve způsobu, jakým je výstup algoritmu interpretován tak, aby odpovídal úkolu.

Pro každou kombinaci algoritmu a úlohy ML.NET poskytuje komponentu, která spustí školicí algoritmus a provede výklad. Tyto komponenty se nazývají školitele. <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> například používá algoritmus **StochasticDualCoordinatedAscent** použitý pro **regresní** úlohu.

## <a name="linear-algorithms"></a>Lineární algoritmy

Lineární algoritmy vytvoří model, který vypočítá **skóre** z lineární kombinace vstupních dat a sady **vah**. Váhy jsou parametry modelu odhadované během školení.

Lineární algoritmy fungují dobře pro funkce, které jsou [lineárně oddělitelné](https://en.wikipedia.org/wiki/Linear_separability).

Před školením pomocí lineárního algoritmu by měly být tyto funkce normalizovány. To brání tomu, aby jedna funkce měla větší vliv na výsledek než jiné.

V obecných lineárních algoritmech jsou škálovatelné a rychlé a levné na vlaky až po předpověď. Škálují se podle počtu funkcí a přibližně podle velikosti sady školicích dat.

Lineární algoritmy umožňují více průchodů školicích dat. Pokud se vaše datová sada vejde do paměti, pak před připojením Trainer přidejte [kontrolní bod mezipaměti](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) do kanálu ml.NET, aby se školení spouštělo rychleji.

**Lineární školitel**

|Algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Průměrná Perceptron|Nejlepší pro klasifikaci textu|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stochastického Dual koordinovaný stoupání|Ladění není nutné pro dobrý výchozí výkon.|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Použijte, pokud je počet funkcí velký. Vytvoří logistické regresní statistiky, ale nemění škálu a také AveragedPerceptronTrainer.|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Symbol klesání na symbolický stochastického|Nejrychlejší a nejpřesnější lineární binární klasifikace Trainer. Škálujte dobře pomocí počtu procesorů.|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Algoritmy rozhodovacího stromu

Algoritmy rozhodovacího stromu vytvoří model, který obsahuje řadu rozhodnutí: efektivní tok grafu prostřednictvím hodnot dat.

Pro použití tohoto typu algoritmu nemusíte lineárně dělit funkce. Funkce a nemusí být normalizovány, protože jednotlivé hodnoty ve vektoru funkce jsou používány nezávisle v rámci rozhodovacího procesu.

Algoritmy rozhodovacího stromu jsou všeobecně velmi přesné.

S výjimkou Generalizických přídatných modelů (GAMs) mohou stromové modely při velkém počtu funkcí chybět vysvětlení.

Algoritmy rozhodovacího stromu přijímají více prostředků a neškálují se i lineární. U datových sad, které se dají umístit do paměti, se dobře plní.

Posílené rozhodovací stromy jsou množinou malých stromů, kde každý z nich vyhodnotí vstupní data a předá skóre do dalšího stromu, aby se vytvořilo lepší skóre, a tak dále, kde se jednotlivé stromové struktury v kompletu zlepšují na předchozí.

**Školitele rozhodovacího stromu**

|Algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Světlý nárůst přechodu na počítač|Nejrychlejší a nejpřesnější v binárním stromu klasifikace. Vysoce přizpůsobitelné|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Rychlý strom|Používá se pro natrénuje obrazová data. Odolná vůči nevyváženým datům. Vysoce přizpůsobitelné | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Rychlá doménová struktura|Dobře funguje s daty o hlučnosti|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Model generalizované doplňkové látky (GAM)|Nejvhodnější pro problémy, které se dobře provádějí s algoritmy stromu, ale pokud je tato světlá priorita|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Faktoring pro vytváření matic

|Vlastnosti|Školitelé|
|----------|--------|
|Nejlepší pro zhuštěná kategorií data s velkými datovými sadami|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algoritmy

Tyto školitele vytvoří Trainer s více třídami z binárního Trainer. Použijte s <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.

|Algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Jedna oproti všem|Tato třída třídění s více třídami navlakuje jeden binární klasifikátor pro každou třídu, který rozlišuje tuto třídu od všech ostatních tříd. Má omezené škálování podle počtu tříd pro kategorizaci.|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Párový párování|Tento klasifikační klasifikátory navlakují binární klasifikační algoritmus na každou dvojici tříd. Má omezené škálování podle počtu tříd, protože každá kombinace dvou tříd musí být vyškolená.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-znamená

|Vlastnosti|Školitelé|
|----------|--------|
|Použít pro clusteringu|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Analýza hlavní komponenty

|Vlastnosti|Školitelé|
|----------|--------|
|Použít pro detekci anomálií|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Naive Bayes

|Vlastnosti|Školitelé|
|----------|--------|
|Použijte tuto Trainer klasifikaci s více třídami, pokud jsou funkce nezávislé a datová sada pro školení je malá.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Předchozí Trainer

|Vlastnosti|Školitelé|
|----------|--------|
|Pomocí této binární klasifikace Trainer můžete podle směrného plánu vyhodnotit výkon jiné školitele. Aby bylo možné platit, metriky druhé školitele by měly být lepší než předchozí Trainer. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
