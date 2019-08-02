---
title: Úkoly strojového učení
description: Prozkoumejte různé úlohy strojového učení a související úlohy, které jsou podporované v ML.NET.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: bcd967c11156ca9b837631560e78722b13fc7ae0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630053"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="0cef3-103">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="0cef3-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="0cef3-104">Při sestavování modelu strojového učení nejdřív musíte definovat, co se vám doufá že k dosažení vašich dat.</span><span class="sxs-lookup"><span data-stu-id="0cef3-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="0cef3-105">Díky tomu můžete zvolit správnou úlohu strojového učení pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="0cef3-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="0cef3-106">V následujícím seznamu jsou popsány různé úlohy strojového učení, ze kterých si můžete vybrat, a některé běžné případy použití.</span><span class="sxs-lookup"><span data-stu-id="0cef3-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="0cef3-107">Jakmile se rozhodnete, který úkol pro váš scénář funguje, musíte zvolit nejlepší algoritmus pro vyučování modelu.</span><span class="sxs-lookup"><span data-stu-id="0cef3-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="0cef3-108">Dostupné algoritmy jsou uvedené v části pro každý úkol.</span><span class="sxs-lookup"><span data-stu-id="0cef3-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="0cef3-109">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="0cef3-109">Binary classification</span></span>

<span data-ttu-id="0cef3-110">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovídání dvou tříd (kategorií), do kterých patří instance dat.</span><span class="sxs-lookup"><span data-stu-id="0cef3-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="0cef3-111">Vstup klasifikačního algoritmu je sada popisných příkladů, kde je každý popisek celé číslo 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="0cef3-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="0cef3-112">Výstup binárního klasifikačního algoritmu je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí.</span><span class="sxs-lookup"><span data-stu-id="0cef3-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="0cef3-113">Mezi příklady scénářů binární klasifikace patří:</span><span class="sxs-lookup"><span data-stu-id="0cef3-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="0cef3-114">[Princip mínění komentářů](../tutorials/sentiment-analysis.md) na Twitteru jako "kladné" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="0cef3-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="0cef3-115">Diagnostikuje, jestli má pacient určitou chorobu nebo ne.</span><span class="sxs-lookup"><span data-stu-id="0cef3-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="0cef3-116">Rozhodování o označení e-mailu jako "spam" nebo ne.</span><span class="sxs-lookup"><span data-stu-id="0cef3-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="0cef3-117">Určení, jestli fotografie obsahuje pes nebo ovoce</span><span class="sxs-lookup"><span data-stu-id="0cef3-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="0cef3-118">Další informace najdete v článku o [binární klasifikaci](https://en.wikipedia.org/wiki/Binary_classification) v Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="0cef3-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="0cef3-119">Školitele binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="0cef3-119">Binary classification trainers</span></span>

<span data-ttu-id="0cef3-120">Model binární klasifikace můžete proškolit pomocí těchto algoritmů:</span><span class="sxs-lookup"><span data-stu-id="0cef3-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="0cef3-121">Binární vstupy a výstupy klasifikace</span><span class="sxs-lookup"><span data-stu-id="0cef3-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="0cef3-122">Pro dosažení nejlepších výsledků s binární klasifikací musí být školicí data vyvážená (tj. stejná čísla kladných a záporných školicích dat).</span><span class="sxs-lookup"><span data-stu-id="0cef3-122">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="0cef3-123">Před školením by měly být zpracovány chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0cef3-123">Missing values should be handled before training.</span></span>

<span data-ttu-id="0cef3-124">Data sloupce vstupního popisku musí být <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="0cef3-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="0cef3-125">Data ve sloupci vstupní funkce musí být vektorem <xref:System.Single>pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="0cef3-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="0cef3-126">Tato školitele vypíše následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="0cef3-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="0cef3-127">Název výstupního sloupce</span><span class="sxs-lookup"><span data-stu-id="0cef3-127">Output Column Name</span></span> | <span data-ttu-id="0cef3-128">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="0cef3-128">Column Type</span></span> | <span data-ttu-id="0cef3-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0cef3-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="0cef3-130">Nezpracované skóre, které bylo vypočítáno modelem</span><span class="sxs-lookup"><span data-stu-id="0cef3-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="0cef3-131">Předpokládaný popisek, založený na znaménku skóre.</span><span class="sxs-lookup"><span data-stu-id="0cef3-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="0cef3-132">Záporné skóre se mapuje na `false` a kladné skóre se mapuje na `true`.</span><span class="sxs-lookup"><span data-stu-id="0cef3-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="0cef3-133">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="0cef3-133">Multiclass classification</span></span>

<span data-ttu-id="0cef3-134">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předvídání třídy dat instance.</span><span class="sxs-lookup"><span data-stu-id="0cef3-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="0cef3-135">Vstup algoritmu klasifikace je sada příkladů s popisky.</span><span class="sxs-lookup"><span data-stu-id="0cef3-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="0cef3-136">Každý popisek normálně začíná jako text.</span><span class="sxs-lookup"><span data-stu-id="0cef3-136">Each label normally starts as text.</span></span> <span data-ttu-id="0cef3-137">Pak se spustí přes TermTransform, který ho převede na klíč (číselný) typ.</span><span class="sxs-lookup"><span data-stu-id="0cef3-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="0cef3-138">Výstup algoritmu klasifikace je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí.</span><span class="sxs-lookup"><span data-stu-id="0cef3-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="0cef3-139">Mezi příklady scénářů klasifikace s více třídami patří:</span><span class="sxs-lookup"><span data-stu-id="0cef3-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="0cef3-140">Určení plemene psa jako "Siberian Husky", "zlatý spuštění metody Retriever", "Poodle" atd.</span><span class="sxs-lookup"><span data-stu-id="0cef3-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="0cef3-141">Pochopíte recenze filmů jako "pozitivní", "neutrální" nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="0cef3-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="0cef3-142">Kategorizace hodnocení hotelu jako "umístění", "cena", "čistota" atd.</span><span class="sxs-lookup"><span data-stu-id="0cef3-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="0cef3-143">Další informace naleznete v článku o [](https://en.wikipedia.org/wiki/Multiclass_classification) třídě s více třídami na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="0cef3-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="0cef3-144">Jedna sada vs všechno upgraduje libovolný [postup binární klasifikace](#binary-classification) , aby fungovala u datových sad s více třídami.</span><span class="sxs-lookup"><span data-stu-id="0cef3-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="0cef3-145">Další informace o [Wikipedii] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="0cef3-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="0cef3-146">Školitel klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="0cef3-146">Multiclass classification trainers</span></span>

<span data-ttu-id="0cef3-147">Model klasifikace s více třídami můžete proškolit pomocí následujících školicích algoritmů:</span><span class="sxs-lookup"><span data-stu-id="0cef3-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="0cef3-148">Vstupy a výstupy s více třídami klasifikace</span><span class="sxs-lookup"><span data-stu-id="0cef3-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="0cef3-149">Data sloupce vstupního popisku musí být typu [Key](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="0cef3-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="0cef3-150">Sloupec funkce musí být vektorem <xref:System.Single>pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="0cef3-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="0cef3-151">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0cef3-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="0cef3-152">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="0cef3-152">Output Name</span></span> | <span data-ttu-id="0cef3-153">type</span><span class="sxs-lookup"><span data-stu-id="0cef3-153">Type</span></span> | <span data-ttu-id="0cef3-154">Popis</span><span class="sxs-lookup"><span data-stu-id="0cef3-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="0cef3-155">Vektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="0cef3-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="0cef3-156">Skóre všech tříd.</span><span class="sxs-lookup"><span data-stu-id="0cef3-156">The scores of all classes.</span></span> <span data-ttu-id="0cef3-157">Vyšší hodnota znamená vyšší pravděpodobnost pro přechod do přidružené třídy.</span><span class="sxs-lookup"><span data-stu-id="0cef3-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="0cef3-158">Pokud má i-th největší hodnotu, index předpokládaného popisku by byl i.</span><span class="sxs-lookup"><span data-stu-id="0cef3-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="0cef3-159">Všimněte si, že je index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="0cef3-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="0cef3-160">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="0cef3-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="0cef3-161">Index předpokládaného popisku.</span><span class="sxs-lookup"><span data-stu-id="0cef3-161">The predicted label's index.</span></span> <span data-ttu-id="0cef3-162">Pokud je jeho hodnota, vlastní popisek bude i-th kategorie v typu vstupního popisku s hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="0cef3-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="0cef3-163">Regrese</span><span class="sxs-lookup"><span data-stu-id="0cef3-163">Regression</span></span>

<span data-ttu-id="0cef3-164">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovědi hodnoty popisku ze sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="0cef3-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="0cef3-165">Popisek může být jakékoli reálné hodnoty a nepochází z konečné sady hodnot jako v rámci úloh klasifikace.</span><span class="sxs-lookup"><span data-stu-id="0cef3-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="0cef3-166">Regresní algoritmy modelují závislost popisku na jeho souvisejících funkcích, aby určili, jak se popisek změní, protože hodnoty funkcí se mění.</span><span class="sxs-lookup"><span data-stu-id="0cef3-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="0cef3-167">Vstup regresního algoritmu je sada příkladů s popisky známých hodnot.</span><span class="sxs-lookup"><span data-stu-id="0cef3-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="0cef3-168">Výstupem regresního algoritmu je funkce, kterou můžete použít k předpovědi hodnoty popisku pro všechny nové sady vstupních funkcí.</span><span class="sxs-lookup"><span data-stu-id="0cef3-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="0cef3-169">Mezi příklady scénářů regrese patří:</span><span class="sxs-lookup"><span data-stu-id="0cef3-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="0cef3-170">Předvídání cen domu na základě atributů na pracovišti, jako je počet ložnicemi, umístění nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="0cef3-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="0cef3-171">Předvídání budoucích cen za ceny na základě historických dat a současných vývojů na trhu.</span><span class="sxs-lookup"><span data-stu-id="0cef3-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="0cef3-172">Předvídání prodeje produktů na základě reklamních rozpočtů.</span><span class="sxs-lookup"><span data-stu-id="0cef3-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="0cef3-173">Regresní školitele</span><span class="sxs-lookup"><span data-stu-id="0cef3-173">Regression trainers</span></span>

<span data-ttu-id="0cef3-174">Regresní model můžete naučit pomocí těchto algoritmů:</span><span class="sxs-lookup"><span data-stu-id="0cef3-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="0cef3-175">Regrese – vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="0cef3-175">Regression inputs and outputs</span></span>

<span data-ttu-id="0cef3-176">Data sloupce vstupního popisku musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="0cef3-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="0cef3-177">Školitel pro tento úkol má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0cef3-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="0cef3-178">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="0cef3-178">Output Name</span></span> | <span data-ttu-id="0cef3-179">type</span><span class="sxs-lookup"><span data-stu-id="0cef3-179">Type</span></span> | <span data-ttu-id="0cef3-180">Popis</span><span class="sxs-lookup"><span data-stu-id="0cef3-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="0cef3-181">Nezpracované skóre, které model předpovídá</span><span class="sxs-lookup"><span data-stu-id="0cef3-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="0cef3-182">Clustering</span><span class="sxs-lookup"><span data-stu-id="0cef3-182">Clustering</span></span>

<span data-ttu-id="0cef3-183">Úkol [strojového učení](glossary.md#unsupervised-machine-learning) , který není pod dohledem, který se používá k seskupení instancí dat do clusterů, které obsahují podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="0cef3-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="0cef3-184">Clustering lze také použít k identifikaci relací v datové sadě, které nemůžete logicky odvodit pomocí procházení nebo jednoduchého sledování.</span><span class="sxs-lookup"><span data-stu-id="0cef3-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="0cef3-185">Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodologii.</span><span class="sxs-lookup"><span data-stu-id="0cef3-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="0cef3-186">Můžete provést distribuci, těžiště, připojení nebo přístup na základě hustoty.</span><span class="sxs-lookup"><span data-stu-id="0cef3-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="0cef3-187">ML.NET aktuálně podporuje přístup založený na těžiště pomocí K-znamená clustering.</span><span class="sxs-lookup"><span data-stu-id="0cef3-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="0cef3-188">Mezi příklady scénářů clusteringu patří:</span><span class="sxs-lookup"><span data-stu-id="0cef3-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="0cef3-189">Porozumění segmentům hostů v hotelovém typu na základě zvyklostí a vlastností možností hotelu.</span><span class="sxs-lookup"><span data-stu-id="0cef3-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="0cef3-190">Identifikujte segmenty zákazníků a demografické údaje, které vám pomůžou vytvářet cílené reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="0cef3-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="0cef3-191">Kategorizace inventáře na základě výrobních metrik.</span><span class="sxs-lookup"><span data-stu-id="0cef3-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="0cef3-192">Clustering Trainer</span><span class="sxs-lookup"><span data-stu-id="0cef3-192">Clustering trainer</span></span>

<span data-ttu-id="0cef3-193">Model clusteringu můžete proškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="0cef3-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="0cef3-194">Vstupy a výstupy clusteringu</span><span class="sxs-lookup"><span data-stu-id="0cef3-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="0cef3-195">Data funkcí input musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="0cef3-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="0cef3-196">Nejsou nutné žádné popisky.</span><span class="sxs-lookup"><span data-stu-id="0cef3-196">No labels are needed.</span></span>

<span data-ttu-id="0cef3-197">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0cef3-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="0cef3-198">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="0cef3-198">Output Name</span></span> | <span data-ttu-id="0cef3-199">type</span><span class="sxs-lookup"><span data-stu-id="0cef3-199">Type</span></span> | <span data-ttu-id="0cef3-200">Popis</span><span class="sxs-lookup"><span data-stu-id="0cef3-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="0cef3-201">vektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="0cef3-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="0cef3-202">Vzdálenosti daného datového bodu ke všem clusterům ' centriods</span><span class="sxs-lookup"><span data-stu-id="0cef3-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="0cef3-203">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="0cef3-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="0cef3-204">Index nejbližšího clusteru předpokládaný modelem.</span><span class="sxs-lookup"><span data-stu-id="0cef3-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="0cef3-205">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="0cef3-205">Anomaly detection</span></span>

<span data-ttu-id="0cef3-206">Tato úloha vytvoří model detekce anomálií pomocí hlavní komponenty pro analýzu (DPS).</span><span class="sxs-lookup"><span data-stu-id="0cef3-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="0cef3-207">Detekce anomálií založená na DPS vám pomůže sestavit model ve scénářích, kdy je snadné získat školicí data z jedné třídy, jako jsou platné transakce, ale obtížně získat dostatečné vzorky cílových anomálií.</span><span class="sxs-lookup"><span data-stu-id="0cef3-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="0cef3-208">V rámci strojového učení se často používá příhlas POMOCNÍKa při analýze dat, protože odhalí vnitřní strukturu dat a vysvětluje odchylku dat.</span><span class="sxs-lookup"><span data-stu-id="0cef3-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="0cef3-209">Funkce DPS funguje při analýze dat, která obsahují více proměnných.</span><span class="sxs-lookup"><span data-stu-id="0cef3-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="0cef3-210">Vyhledá korelaci mezi proměnnými a určí kombinaci hodnot, které nejlépe zachytí rozdíly ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="0cef3-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="0cef3-211">Tyto kombinované hodnoty funkcí slouží k vytvoření kompaktnějšího prostoru funkcí označovaného jako hlavní komponenty.</span><span class="sxs-lookup"><span data-stu-id="0cef3-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="0cef3-212">Detekce anomálií zahrnuje mnoho důležitých úloh ve strojovém učení:</span><span class="sxs-lookup"><span data-stu-id="0cef3-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="0cef3-213">Identifikujte transakce, které jsou potenciálně podvodné.</span><span class="sxs-lookup"><span data-stu-id="0cef3-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="0cef3-214">Výukové modely indikující, že došlo k narušení sítě.</span><span class="sxs-lookup"><span data-stu-id="0cef3-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="0cef3-215">Hledání neobvyklých clusterů pacientů.</span><span class="sxs-lookup"><span data-stu-id="0cef3-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="0cef3-216">Kontrola hodnot zadaných do systému.</span><span class="sxs-lookup"><span data-stu-id="0cef3-216">Checking values entered into a system.</span></span>

<span data-ttu-id="0cef3-217">Vzhledem k tomu, že anomálie jsou vzácné události podle definice, může být obtížné shromáždit reprezentativní vzorek dat, který se má použít pro modelování.</span><span class="sxs-lookup"><span data-stu-id="0cef3-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="0cef3-218">Algoritmy zahrnuté v této kategorii byly obzvláště navržené pro řešení základních výzev k sestavování a školení modelů pomocí nevyvážených datových sad.</span><span class="sxs-lookup"><span data-stu-id="0cef3-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="0cef3-219">Trainer detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="0cef3-219">Anomaly detection trainer</span></span>

<span data-ttu-id="0cef3-220">Model detekce anomálií můžete vyškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="0cef3-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="0cef3-221">Vstupy a výstupy detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="0cef3-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="0cef3-222">Vstupní funkce musí být vektorem <xref:System.Single>pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="0cef3-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="0cef3-223">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0cef3-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="0cef3-224">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="0cef3-224">Output Name</span></span> | <span data-ttu-id="0cef3-225">type</span><span class="sxs-lookup"><span data-stu-id="0cef3-225">Type</span></span> | <span data-ttu-id="0cef3-226">Popis</span><span class="sxs-lookup"><span data-stu-id="0cef3-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="0cef3-227">Nezáporné, neohraničené skóre, které bylo vypočítáno modelem detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="0cef3-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="0cef3-228">Pořadí</span><span class="sxs-lookup"><span data-stu-id="0cef3-228">Ranking</span></span>

<span data-ttu-id="0cef3-229">Úkol hodnocení sestaví seřazení ze sady popisných příkladů.</span><span class="sxs-lookup"><span data-stu-id="0cef3-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="0cef3-230">Tato ukázková sada se skládá ze skupin instancí, jejichž skóre se dá vyhodnotit pomocí daných kritérií.</span><span class="sxs-lookup"><span data-stu-id="0cef3-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="0cef3-231">Popisky hodnocení jsou pro každou instanci {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="0cef3-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="0cef3-232">Klasifikátor je vyškolen pro řazení nových skupin instancí s neznámým skóre pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="0cef3-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="0cef3-233">Seznámení s ML.NETm řazením počítačů se seznámili podle [hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) .</span><span class="sxs-lookup"><span data-stu-id="0cef3-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="0cef3-234">Hodnocení školicích algoritmů</span><span class="sxs-lookup"><span data-stu-id="0cef3-234">Ranking training algorithms</span></span>

<span data-ttu-id="0cef3-235">Model hodnocení můžete proškolit s následujícími algoritmy:</span><span class="sxs-lookup"><span data-stu-id="0cef3-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="0cef3-236">Řazení vstupů a výstupů</span><span class="sxs-lookup"><span data-stu-id="0cef3-236">Ranking input and outputs</span></span>

<span data-ttu-id="0cef3-237">Vstupní datový typ popisku musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) nebo <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="0cef3-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="0cef3-238">Hodnota popisku určuje relevanci, kde vyšší hodnoty označují vyšší relevanci.</span><span class="sxs-lookup"><span data-stu-id="0cef3-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="0cef3-239">Pokud je popisek typem [klíče](xref:Microsoft.ML.Data.KeyDataViewType) , pak je index klíče hodnota významnosti, kde nejmenší index je nejméně relevantní.</span><span class="sxs-lookup"><span data-stu-id="0cef3-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="0cef3-240">Pokud je popisek a <xref:System.Single>, větší hodnota znamená vyšší relevance.</span><span class="sxs-lookup"><span data-stu-id="0cef3-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="0cef3-241">Data funkce musí být vektorem <xref:System.Single> pevné velikosti a sloupec vstupní řádky musí být typu [Key](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="0cef3-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="0cef3-242">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0cef3-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="0cef3-243">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="0cef3-243">Output Name</span></span> | <span data-ttu-id="0cef3-244">type</span><span class="sxs-lookup"><span data-stu-id="0cef3-244">Type</span></span> | <span data-ttu-id="0cef3-245">Popis</span><span class="sxs-lookup"><span data-stu-id="0cef3-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="0cef3-246">Neohraničené skóre, které bylo vypočítáno modelem k určení předpovědi</span><span class="sxs-lookup"><span data-stu-id="0cef3-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="0cef3-247">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0cef3-247">Recommendation</span></span>

<span data-ttu-id="0cef3-248">Úkol doporučení umožňuje vytvořit seznam doporučených produktů nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="0cef3-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="0cef3-249">ML.NET používá pro doporučení algoritmus pro [filtrování](https://en.wikipedia.org/wiki/Collaborative_filtering) a vytváření [matic (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), pokud máte historická data hodnocení produktu ve vašem katalogu.</span><span class="sxs-lookup"><span data-stu-id="0cef3-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="0cef3-250">Máte například historická data o hodnocení filmu pro vaše uživatele a chcete doporučit další filmy, které se budou pravděpodobně sledovat.</span><span class="sxs-lookup"><span data-stu-id="0cef3-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="0cef3-251">Algoritmy školení pro doporučení</span><span class="sxs-lookup"><span data-stu-id="0cef3-251">Recommendation training algorithms</span></span>

<span data-ttu-id="0cef3-252">Model doporučení můžete vyškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="0cef3-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
