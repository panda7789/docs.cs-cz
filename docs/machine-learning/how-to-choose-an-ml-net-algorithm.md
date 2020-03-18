---
title: Jak si vybrat ML.NET algoritmus
description: Přečtěte si, jak vybrat algoritmus ML.NET pro model strojového učení
ms.topic: overview
ms.date: 06/05/2019
ms.openlocfilehash: 0fed33203c02303e37e47f548e08ec131eeb1c77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75739992"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>Jak si vybrat ML.NET algoritmus

Pro každý [ML.NET úkol](resources/tasks.md), existuje více školení algoritmy na výběr. Který z nich zvolit závisí na problému, který se pokoušíte vyřešit, charakteristiky dat a výpočetní prostředky a prostředky úložiště, které máte k dispozici. Je důležité si uvědomit, že školení modelu strojového učení je iterativní proces. Možná budete muset vyzkoušet více algoritmů najít ten, který funguje nejlépe.

Algoritmy pracují na **funkcích**. Funkce jsou číselné hodnoty vypočítané ze vstupních dat. Jsou to optimální vstupy pro algoritmy strojového učení. Nezpracovaná vstupní data můžete transformovat do funkcí pomocí jedné nebo více [transformací dat](resources/transforms.md). Například textová data se transformují do sady počtu slov a kombinace slov. Jakmile byly funkce extrahovány z nezpracovaného datového typu pomocí transformace dat, jsou označovány jako **featurized**. Například featurized text nebo featurized obrazová data.

## <a name="trainer--algorithm--task"></a>Trenér = Algoritmus + Úkol

Algoritmus je matematika, která se provádí k vytvoření **modelu**. Různé algoritmy vytvářejí modely s různými charakteristikami.

U ML.NET lze stejný algoritmus použít pro různé úkoly. Například Stochastic dual coordinated ascent lze použít pro binární klasifikace, vícetřídní klasifikace a regrese. Rozdíl je v tom, jak je interpretován výstup algoritmu tak, aby odpovídal úkolu.

Pro každou kombinaci algoritmu s úkolem ML.NET poskytuje komponentu, která provede algoritmus školení a provede interpretaci. Tyto komponenty se nazývají školitelů. Například <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> používá **Algoritmus StochasticDualCoordinatedAscent** aplikovaný na úlohu **Regrese.**

## <a name="linear-algorithms"></a>Lineární algoritmy

Lineární algoritmy vytvářejí model, který vypočítá **skóre** z lineární kombinace vstupních dat a sady **závaží**. Závaží jsou parametry modelu odhadované během tréninku.

Lineární algoritmy fungují dobře pro prvky, které jsou [lineárně oddělitelné](https://en.wikipedia.org/wiki/Linear_separability).

Před tréninkem s lineárním algoritmem by měly být funkce normalizovány. Tím se zabrání jeden prvek má větší vliv na výsledek než ostatní.

Obecně lineární algoritmy jsou škálovatelné a rychlé, levné trénovat, levné předpovědět. Jejich měřítko podle počtu funkcí a přibližně podle velikosti trénovací datové sady.

Lineární algoritmy provést více průchodů přes trénovací data. Pokud vaše datová sada zapadá do paměti, pak přidání [kontrolního bodu mezipaměti](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) do kanálu ML.NET před připojením trenér, bude školení běžet rychleji.

**Lineární trenažérky**

|Algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Průměrný perceptron|Nejlepší pro klasifikaci textu|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stochastický duální koordinovaný výstup|Ladění není nutné pro dobrý výchozí výkon|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Používá se v případě, že počet funkcí je velký. Vytváří statistiky logistického regrese školení, ale neškáluje stejně jako AveragedPerceptronTrainer|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Symbolický sestup stochastického gradientu|Nejrychlejší a nejpřesnější lineární binární klasifikace trenér. Dobře se škáluje s počtem procesorů|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Algoritmy rozhodovacího stromu

Rozhodovací strom algoritmy vytvořit model, který obsahuje řadu rozhodnutí: efektivně vývojový diagram prostřednictvím datových hodnot.

Funkce není nutné lineárně oddělitelné používat tento typ algoritmu. A funkce nemusí být normalizovány, protože jednotlivé hodnoty ve vektoru prvku se používají nezávisle v rozhodovacím procesu.

Rozhodovací strom algoritmy jsou obecně velmi přesné.

S výjimkou generalizovaných aditivních modelů (GAM) mohou stromové modely postrádat vysvětlitelnost, když je velký počet funkcí.

Rozhodovací strom algoritmy trvat více prostředků a nejsou škálovat, stejně jako lineární ty dělat. Dělají dobře na datové sady, které se vejdou do paměti.

Posílené rozhodovací stromy jsou soubormalých stromů, kde každý strom skóre vstupní data a předává skóre na další strom produkovat lepší skóre, a tak dále, kde každý strom v souboru zlepšuje na předchozí.

**Rozhodovací strom školitelů**

|Algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Světlo gradient posílena stroj|Nejrychlejší a nejpřesnější z binární klasifikace stromu školitelů. Vysoce laditelný|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Rychlý strom|Slouží k featurized obrazových dat. Odolný vůči nevyváženým datům. Vysoce laditelný | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Rychlý les|Funguje dobře s hlučnými daty|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Generalizovaný aditivní model (GAM)|Nejlepší pro problémy, které fungují dobře s algoritmy stromu, ale kde je prioritou vysvětlitelnost|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Faktorizace matice

|Vlastnosti|Školitelé|
|----------|--------|
|Nejlepší pro řídká kategorická data s velkými datovými sadami|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algoritmy

Tyto trenéři vytvořit multi-class trenér z binárního trenéra. Používejte <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>s <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>, , , , .

|Algoritmus|Vlastnosti|Školitelé|
|---------|----------|--------|
|Jeden versus všechny|Tento vícetřídní třídění trénuje jeden binární třídění pro každou třídu, která odlišuje tuto třídu od všech ostatních tříd. Je omezen v měřítku počtem tříd kategorizovat|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Párová spojka|Tento klasifikátor více tříd trénuje binární klasifikační algoritmus na každé dvojici tříd. Je omezen v měřítku počtem tříd, jako každá kombinace dvou tříd musí být vyškoleni.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-prostředky

|Vlastnosti|Školitelé|
|----------|--------|
|Použití pro clustering|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Analýza hlavních součástí

|Vlastnosti|Školitelé|
|----------|--------|
|Použití pro detekci anomálií|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Naivní Bayesovy klasifikátory

|Vlastnosti|Školitelé|
|----------|--------|
|Tento vícetřídní kurzovací kanál použijte, pokud jsou funkce nezávislé a datová sada školení je malá.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Předchozí trenér

|Vlastnosti|Školitelé|
|----------|--------|
|Použijte tento binární klasifikace trenér na směrný plán výkonu jiných školitelů. Aby byly účinné, metriky ostatních trenérů by měly být lepší než předchozí trenér. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
