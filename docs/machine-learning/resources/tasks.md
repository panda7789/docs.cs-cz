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
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="154aa-103">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="154aa-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="154aa-104">Při sestavování modelu strojového učení nejdřív musíte definovat, co se vám doufá že k dosažení vašich dat.</span><span class="sxs-lookup"><span data-stu-id="154aa-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="154aa-105">Díky tomu můžete zvolit správnou úlohu strojového učení pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="154aa-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="154aa-106">V následujícím seznamu jsou popsány různé úlohy strojového učení, ze kterých si můžete vybrat, a některé běžné případy použití.</span><span class="sxs-lookup"><span data-stu-id="154aa-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span> <span data-ttu-id="154aa-107">Další informace o výběru úlohy, která je vhodná pro váš scénář, najdete v tématu [algoritmy](../how-to-choose-an-ml-net-algorithm.md).</span><span class="sxs-lookup"><span data-stu-id="154aa-107">For more information about choosing the task that is appropriate for your scenario, see [Algorithms](../how-to-choose-an-ml-net-algorithm.md).</span></span>

<span data-ttu-id="154aa-108">Jakmile se rozhodnete, který úkol pro váš scénář funguje, musíte zvolit nejlepší algoritmus pro vyučování modelu.</span><span class="sxs-lookup"><span data-stu-id="154aa-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="154aa-109">Dostupné algoritmy jsou uvedené v části pro každý úkol.</span><span class="sxs-lookup"><span data-stu-id="154aa-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="154aa-110">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="154aa-110">Binary classification</span></span>

<span data-ttu-id="154aa-111">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovídání dvou tříd (kategorií), do kterých patří instance dat.</span><span class="sxs-lookup"><span data-stu-id="154aa-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="154aa-112">Vstup klasifikačního algoritmu je sada popisných příkladů, kde je každý popisek celé číslo 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="154aa-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="154aa-113">Výstup binárního klasifikačního algoritmu je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí.</span><span class="sxs-lookup"><span data-stu-id="154aa-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="154aa-114">Mezi příklady scénářů binární klasifikace patří:</span><span class="sxs-lookup"><span data-stu-id="154aa-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="154aa-115">[Princip mínění komentářů na Twitteru](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="154aa-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="154aa-116">Diagnostikuje, jestli má pacient určitou chorobu nebo ne.</span><span class="sxs-lookup"><span data-stu-id="154aa-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="154aa-117">Rozhodování o označení e-mailu jako "spam" nebo ne.</span><span class="sxs-lookup"><span data-stu-id="154aa-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="154aa-118">Určení, jestli fotka obsahuje určitou položku, například pes nebo ovoce.</span><span class="sxs-lookup"><span data-stu-id="154aa-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="154aa-119">Další informace najdete v článku o [binární klasifikaci](https://en.wikipedia.org/wiki/Binary_classification) v Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="154aa-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="154aa-120">Školitele binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="154aa-120">Binary classification trainers</span></span>

<span data-ttu-id="154aa-121">Model binární klasifikace můžete proškolit pomocí těchto algoritmů:</span><span class="sxs-lookup"><span data-stu-id="154aa-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="154aa-122">Binární vstupy a výstupy klasifikace</span><span class="sxs-lookup"><span data-stu-id="154aa-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="154aa-123">Pro dosažení nejlepších výsledků s binární klasifikací musí být školicí data vyvážená (tj. stejná čísla kladných a záporných školicích dat).</span><span class="sxs-lookup"><span data-stu-id="154aa-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="154aa-124">Před školením by měly být zpracovány chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="154aa-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="154aa-125">Data sloupce vstupního popisku musí být <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="154aa-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="154aa-126">Data ve sloupci vstupní funkce musí být vektorem s pevnou velikostí <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="154aa-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="154aa-127">Výstup učitelů má následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="154aa-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="154aa-128">Název výstupního sloupce</span><span class="sxs-lookup"><span data-stu-id="154aa-128">Output Column Name</span></span> | <span data-ttu-id="154aa-129">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="154aa-129">Column Type</span></span> | <span data-ttu-id="154aa-130">Popis</span><span class="sxs-lookup"><span data-stu-id="154aa-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="154aa-131">Nezpracované skóre, které bylo vypočítáno modelem</span><span class="sxs-lookup"><span data-stu-id="154aa-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="154aa-132">Předpokládaný popisek, založený na znaménku skóre.</span><span class="sxs-lookup"><span data-stu-id="154aa-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="154aa-133">Záporné skóre se mapuje na `false` a kladné skóre se mapuje na `true`.</span><span class="sxs-lookup"><span data-stu-id="154aa-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="154aa-134">klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="154aa-134">Multiclass classification</span></span>

<span data-ttu-id="154aa-135">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předvídání třídy dat instance.</span><span class="sxs-lookup"><span data-stu-id="154aa-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="154aa-136">Vstup algoritmu klasifikace je sada příkladů s popisky.</span><span class="sxs-lookup"><span data-stu-id="154aa-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="154aa-137">Každý popisek normálně začíná jako text.</span><span class="sxs-lookup"><span data-stu-id="154aa-137">Each label normally starts as text.</span></span> <span data-ttu-id="154aa-138">Pak se spustí přes TermTransform, který ho převede na klíč (číselný) typ.</span><span class="sxs-lookup"><span data-stu-id="154aa-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="154aa-139">Výstup algoritmu klasifikace je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí.</span><span class="sxs-lookup"><span data-stu-id="154aa-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="154aa-140">Mezi příklady scénářů klasifikace s více třídami patří:</span><span class="sxs-lookup"><span data-stu-id="154aa-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="154aa-141">Určení plemene psa jako "Siberian Husky", "zlatý spuštění metody Retriever", "Poodle" atd.</span><span class="sxs-lookup"><span data-stu-id="154aa-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="154aa-142">Pochopíte recenze filmů jako "pozitivní", "neutrální" nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="154aa-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="154aa-143">Kategorizace hodnocení hotelu jako "umístění", "cena", "čistota" atd.</span><span class="sxs-lookup"><span data-stu-id="154aa-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="154aa-144">Další informace naleznete v článku o třídě s více [třídami](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="154aa-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="154aa-145">Jedna sada vs všechno upgraduje libovolný [postup binární klasifikace](#binary-classification) , aby fungovala u datových sad s více třídami.</span><span class="sxs-lookup"><span data-stu-id="154aa-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="154aa-146">Další informace o [Wikipedii] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="154aa-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="154aa-147">Školitel klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="154aa-147">Multiclass classification trainers</span></span>

<span data-ttu-id="154aa-148">Model klasifikace s více třídami můžete proškolit pomocí následujících školicích algoritmů:</span><span class="sxs-lookup"><span data-stu-id="154aa-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="154aa-149">Vstupy a výstupy s více třídami klasifikace</span><span class="sxs-lookup"><span data-stu-id="154aa-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="154aa-150">Data sloupce vstupního popisku musí být typu [Key](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="154aa-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="154aa-151">Sloupec funkce musí být vektorem pevné velikosti <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="154aa-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="154aa-152">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="154aa-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="154aa-153">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="154aa-153">Output Name</span></span> | <span data-ttu-id="154aa-154">Typ</span><span class="sxs-lookup"><span data-stu-id="154aa-154">Type</span></span> | <span data-ttu-id="154aa-155">Popis</span><span class="sxs-lookup"><span data-stu-id="154aa-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="154aa-156">vektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="154aa-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="154aa-157">Skóre všech tříd.</span><span class="sxs-lookup"><span data-stu-id="154aa-157">The scores of all classes.</span></span> <span data-ttu-id="154aa-158">Vyšší hodnota znamená vyšší pravděpodobnost pro přechod do přidružené třídy.</span><span class="sxs-lookup"><span data-stu-id="154aa-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="154aa-159">Pokud má i-th největší hodnotu, index předpokládaného popisku by byl i.</span><span class="sxs-lookup"><span data-stu-id="154aa-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="154aa-160">Všimněte si, že je index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="154aa-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="154aa-161">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="154aa-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="154aa-162">Index předpokládaného popisku.</span><span class="sxs-lookup"><span data-stu-id="154aa-162">The predicted label's index.</span></span> <span data-ttu-id="154aa-163">Pokud je jeho hodnota, vlastní popisek bude i-th kategorie v typu vstupního popisku s hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="154aa-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="154aa-164">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="154aa-164">Regression</span></span>

<span data-ttu-id="154aa-165">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovědi hodnoty popisku ze sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="154aa-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="154aa-166">Popisek může být jakékoli reálné hodnoty a nepochází z konečné sady hodnot jako v rámci úloh klasifikace.</span><span class="sxs-lookup"><span data-stu-id="154aa-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="154aa-167">Regresní algoritmy modelují závislost popisku na jeho souvisejících funkcích, aby určili, jak se popisek změní, protože hodnoty funkcí se mění.</span><span class="sxs-lookup"><span data-stu-id="154aa-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="154aa-168">Vstup regresního algoritmu je sada příkladů s popisky známých hodnot.</span><span class="sxs-lookup"><span data-stu-id="154aa-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="154aa-169">Výstupem regresního algoritmu je funkce, kterou můžete použít k předpovědi hodnoty popisku pro všechny nové sady vstupních funkcí.</span><span class="sxs-lookup"><span data-stu-id="154aa-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="154aa-170">Mezi příklady scénářů regrese patří:</span><span class="sxs-lookup"><span data-stu-id="154aa-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="154aa-171">Předvídání cen domu na základě atributů na pracovišti, jako je počet ložnicemi, umístění nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="154aa-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="154aa-172">Předvídání budoucích cen za ceny na základě historických dat a současných vývojů na trhu.</span><span class="sxs-lookup"><span data-stu-id="154aa-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="154aa-173">Předvídání prodeje produktů na základě reklamních rozpočtů.</span><span class="sxs-lookup"><span data-stu-id="154aa-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="154aa-174">Regresní školitele</span><span class="sxs-lookup"><span data-stu-id="154aa-174">Regression trainers</span></span>

<span data-ttu-id="154aa-175">Regresní model můžete naučit pomocí těchto algoritmů:</span><span class="sxs-lookup"><span data-stu-id="154aa-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="154aa-176">Regrese – vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="154aa-176">Regression inputs and outputs</span></span>

<span data-ttu-id="154aa-177">Data sloupce vstupního popisku musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="154aa-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="154aa-178">Školitel pro tento úkol má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="154aa-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="154aa-179">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="154aa-179">Output Name</span></span> | <span data-ttu-id="154aa-180">Typ</span><span class="sxs-lookup"><span data-stu-id="154aa-180">Type</span></span> | <span data-ttu-id="154aa-181">Popis</span><span class="sxs-lookup"><span data-stu-id="154aa-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="154aa-182">Nezpracované skóre, které model předpovídá</span><span class="sxs-lookup"><span data-stu-id="154aa-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="154aa-183">Clustering</span><span class="sxs-lookup"><span data-stu-id="154aa-183">Clustering</span></span>

<span data-ttu-id="154aa-184">Úkol [strojového učení, který není pod dohledem](glossary.md#unsupervised-machine-learning) , který se používá k seskupení instancí dat do clusterů, které obsahují podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="154aa-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="154aa-185">Clustering lze také použít k identifikaci relací v datové sadě, které nemůžete logicky odvodit pomocí procházení nebo jednoduchého sledování.</span><span class="sxs-lookup"><span data-stu-id="154aa-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="154aa-186">Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodologii.</span><span class="sxs-lookup"><span data-stu-id="154aa-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="154aa-187">Můžete provést distribuci, těžiště, připojení nebo přístup na základě hustoty.</span><span class="sxs-lookup"><span data-stu-id="154aa-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="154aa-188">ML.NET aktuálně podporuje přístup založený na těžiště pomocí K-znamená clustering.</span><span class="sxs-lookup"><span data-stu-id="154aa-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="154aa-189">Mezi příklady scénářů clusteringu patří:</span><span class="sxs-lookup"><span data-stu-id="154aa-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="154aa-190">Porozumění segmentům hostů v hotelovém typu na základě zvyklostí a vlastností možností hotelu.</span><span class="sxs-lookup"><span data-stu-id="154aa-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="154aa-191">Identifikujte segmenty zákazníků a demografické údaje, které vám pomůžou vytvářet cílené reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="154aa-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="154aa-192">Kategorizace inventáře na základě výrobních metrik.</span><span class="sxs-lookup"><span data-stu-id="154aa-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="154aa-193">Clustering Trainer</span><span class="sxs-lookup"><span data-stu-id="154aa-193">Clustering trainer</span></span>

<span data-ttu-id="154aa-194">Model clusteringu můžete proškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="154aa-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="154aa-195">Vstupy a výstupy clusteringu</span><span class="sxs-lookup"><span data-stu-id="154aa-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="154aa-196">Data funkcí input musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="154aa-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="154aa-197">Nejsou nutné žádné popisky.</span><span class="sxs-lookup"><span data-stu-id="154aa-197">No labels are needed.</span></span>

<span data-ttu-id="154aa-198">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="154aa-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="154aa-199">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="154aa-199">Output Name</span></span> | <span data-ttu-id="154aa-200">Typ</span><span class="sxs-lookup"><span data-stu-id="154aa-200">Type</span></span> | <span data-ttu-id="154aa-201">Popis</span><span class="sxs-lookup"><span data-stu-id="154aa-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="154aa-202">vektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="154aa-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="154aa-203">Vzdálenosti daného datového bodu ke všem clusterům ' centriods</span><span class="sxs-lookup"><span data-stu-id="154aa-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="154aa-204">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="154aa-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="154aa-205">Index nejbližšího clusteru předpokládaný modelem.</span><span class="sxs-lookup"><span data-stu-id="154aa-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="154aa-206">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="154aa-206">Anomaly detection</span></span>

<span data-ttu-id="154aa-207">Tato úloha vytvoří model detekce anomálií pomocí hlavní komponenty pro analýzu (DPS).</span><span class="sxs-lookup"><span data-stu-id="154aa-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="154aa-208">Detekce anomálií založená na DPS vám pomůže sestavit model ve scénářích, kdy je snadné získat školicí data z jedné třídy, jako jsou platné transakce, ale obtížně získat dostatečné vzorky cílových anomálií.</span><span class="sxs-lookup"><span data-stu-id="154aa-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="154aa-209">V rámci strojového učení se často používá příhlas POMOCNÍKa při analýze dat, protože odhalí vnitřní strukturu dat a vysvětluje odchylku dat.</span><span class="sxs-lookup"><span data-stu-id="154aa-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="154aa-210">Funkce DPS funguje při analýze dat, která obsahují více proměnných.</span><span class="sxs-lookup"><span data-stu-id="154aa-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="154aa-211">Vyhledá korelaci mezi proměnnými a určí kombinaci hodnot, které nejlépe zachytí rozdíly ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="154aa-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="154aa-212">Tyto kombinované hodnoty funkcí slouží k vytvoření kompaktnějšího prostoru funkcí označovaného jako hlavní komponenty.</span><span class="sxs-lookup"><span data-stu-id="154aa-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="154aa-213">Detekce anomálií zahrnuje mnoho důležitých úloh ve strojovém učení:</span><span class="sxs-lookup"><span data-stu-id="154aa-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="154aa-214">Identifikujte transakce, které jsou potenciálně podvodné.</span><span class="sxs-lookup"><span data-stu-id="154aa-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="154aa-215">Výukové modely indikující, že došlo k narušení sítě.</span><span class="sxs-lookup"><span data-stu-id="154aa-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="154aa-216">Hledání neobvyklých clusterů pacientů.</span><span class="sxs-lookup"><span data-stu-id="154aa-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="154aa-217">Kontrola hodnot zadaných do systému.</span><span class="sxs-lookup"><span data-stu-id="154aa-217">Checking values entered into a system.</span></span>

<span data-ttu-id="154aa-218">Vzhledem k tomu, že anomálie jsou vzácné události podle definice, může být obtížné shromáždit reprezentativní vzorek dat, který se má použít pro modelování.</span><span class="sxs-lookup"><span data-stu-id="154aa-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="154aa-219">Algoritmy zahrnuté v této kategorii byly obzvláště navržené pro řešení základních výzev k sestavování a školení modelů pomocí nevyvážených datových sad.</span><span class="sxs-lookup"><span data-stu-id="154aa-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="154aa-220">Trainer detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="154aa-220">Anomaly detection trainer</span></span>

<span data-ttu-id="154aa-221">Model detekce anomálií můžete vyškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="154aa-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="154aa-222">Vstupy a výstupy detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="154aa-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="154aa-223">Vstupní funkce musí být vektor <xref:System.Single>pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="154aa-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="154aa-224">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="154aa-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="154aa-225">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="154aa-225">Output Name</span></span> | <span data-ttu-id="154aa-226">Typ</span><span class="sxs-lookup"><span data-stu-id="154aa-226">Type</span></span> | <span data-ttu-id="154aa-227">Popis</span><span class="sxs-lookup"><span data-stu-id="154aa-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="154aa-228">Nezáporné, neohraničené skóre, které bylo vypočítáno modelem detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="154aa-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="154aa-229">Pořadí</span><span class="sxs-lookup"><span data-stu-id="154aa-229">Ranking</span></span>

<span data-ttu-id="154aa-230">Úkol hodnocení sestaví seřazení ze sady popisných příkladů.</span><span class="sxs-lookup"><span data-stu-id="154aa-230">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="154aa-231">Tato ukázková sada se skládá ze skupin instancí, jejichž skóre se dá vyhodnotit pomocí daných kritérií.</span><span class="sxs-lookup"><span data-stu-id="154aa-231">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="154aa-232">Popisky hodnocení jsou pro každou instanci {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="154aa-232">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="154aa-233">Klasifikátor je vyškolen pro řazení nových skupin instancí s neznámým skóre pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="154aa-233">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="154aa-234">Seznámení s ML.NETm řazením [počítačů se seznámili podle hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) .</span><span class="sxs-lookup"><span data-stu-id="154aa-234">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="154aa-235">Hodnocení školicích algoritmů</span><span class="sxs-lookup"><span data-stu-id="154aa-235">Ranking training algorithms</span></span>

<span data-ttu-id="154aa-236">Model hodnocení můžete proškolit s následujícími algoritmy:</span><span class="sxs-lookup"><span data-stu-id="154aa-236">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="154aa-237">Řazení vstupů a výstupů</span><span class="sxs-lookup"><span data-stu-id="154aa-237">Ranking input and outputs</span></span>

<span data-ttu-id="154aa-238">Vstupní datový typ popisku musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) nebo <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="154aa-238">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="154aa-239">Hodnota popisku určuje relevanci, kde vyšší hodnoty označují vyšší relevanci.</span><span class="sxs-lookup"><span data-stu-id="154aa-239">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="154aa-240">Pokud je popisek typem [klíče](xref:Microsoft.ML.Data.KeyDataViewType) , pak je index klíče hodnota významnosti, kde nejmenší index je nejméně relevantní.</span><span class="sxs-lookup"><span data-stu-id="154aa-240">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="154aa-241">Pokud je popisek <xref:System.Single>, větší hodnoty znamenají vyšší relevance.</span><span class="sxs-lookup"><span data-stu-id="154aa-241">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="154aa-242">Data funkce musí být vektorem pevné velikosti <xref:System.Single> a sloupec vstupní skupiny řádků musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="154aa-242">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="154aa-243">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="154aa-243">This trainer outputs the following:</span></span>

| <span data-ttu-id="154aa-244">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="154aa-244">Output Name</span></span> | <span data-ttu-id="154aa-245">Typ</span><span class="sxs-lookup"><span data-stu-id="154aa-245">Type</span></span> | <span data-ttu-id="154aa-246">Popis</span><span class="sxs-lookup"><span data-stu-id="154aa-246">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="154aa-247">Neohraničené skóre, které bylo vypočítáno modelem k určení předpovědi</span><span class="sxs-lookup"><span data-stu-id="154aa-247">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="154aa-248">Základě</span><span class="sxs-lookup"><span data-stu-id="154aa-248">Recommendation</span></span>

<span data-ttu-id="154aa-249">Úkol doporučení umožňuje vytvořit seznam doporučených produktů nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="154aa-249">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="154aa-250">ML.NET používá pro doporučení algoritmus pro [filtrování](https://en.wikipedia.org/wiki/Collaborative_filtering) a vytváření [matic (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), pokud máte historická data hodnocení produktu ve vašem katalogu.</span><span class="sxs-lookup"><span data-stu-id="154aa-250">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="154aa-251">Máte například historická data o hodnocení filmu pro vaše uživatele a chcete doporučit další filmy, které se budou pravděpodobně sledovat.</span><span class="sxs-lookup"><span data-stu-id="154aa-251">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="154aa-252">Algoritmy školení pro doporučení</span><span class="sxs-lookup"><span data-stu-id="154aa-252">Recommendation training algorithms</span></span>

<span data-ttu-id="154aa-253">Model doporučení můžete vyškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="154aa-253">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
