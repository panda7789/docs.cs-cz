---
title: Úkoly strojového učení
description: Prozkoumejte různé úlohy strojového učení a související úlohy, které jsou podporované v ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745098"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="09d76-103">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="09d76-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="09d76-104">Úloha strojového učení je typ předpovědi nebo odvození, na základě problému nebo otázky, na které se žádá, a dostupných dat.</span><span class="sxs-lookup"><span data-stu-id="09d76-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="09d76-105">Například úloha klasifikace přiřadí data do kategorií a úloha clusteringu seskupuje data podle podobnosti.</span><span class="sxs-lookup"><span data-stu-id="09d76-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="09d76-106">Úlohy strojového učení využívají vzory v datech, a ne explicitně naprogramované.</span><span class="sxs-lookup"><span data-stu-id="09d76-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="09d76-107">Tento článek popisuje různé úlohy strojového učení, ze kterých si můžete vybrat v ML.NET a některých běžných případech použití.</span><span class="sxs-lookup"><span data-stu-id="09d76-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="09d76-108">Jakmile se rozhodnete, který úkol pro váš scénář funguje, musíte zvolit nejlepší algoritmus pro vyučování modelu.</span><span class="sxs-lookup"><span data-stu-id="09d76-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="09d76-109">Dostupné algoritmy jsou uvedené v části pro každý úkol.</span><span class="sxs-lookup"><span data-stu-id="09d76-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="09d76-110">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="09d76-110">Binary classification</span></span>

<span data-ttu-id="09d76-111">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovídání dvou tříd (kategorií), do kterých patří instance dat.</span><span class="sxs-lookup"><span data-stu-id="09d76-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="09d76-112">Vstup klasifikačního algoritmu je sada popisných příkladů, kde je každý popisek celé číslo 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="09d76-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="09d76-113">Výstup binárního klasifikačního algoritmu je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí.</span><span class="sxs-lookup"><span data-stu-id="09d76-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="09d76-114">Mezi příklady scénářů binární klasifikace patří:</span><span class="sxs-lookup"><span data-stu-id="09d76-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="09d76-115">[Princip mínění komentářů na Twitteru](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="09d76-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="09d76-116">Diagnostikuje, jestli má pacient určitou chorobu nebo ne.</span><span class="sxs-lookup"><span data-stu-id="09d76-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="09d76-117">Rozhodování o označení e-mailu jako "spam" nebo ne.</span><span class="sxs-lookup"><span data-stu-id="09d76-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="09d76-118">Určení, jestli fotka obsahuje určitou položku, například pes nebo ovoce.</span><span class="sxs-lookup"><span data-stu-id="09d76-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="09d76-119">Další informace najdete v článku o [binární klasifikaci](https://en.wikipedia.org/wiki/Binary_classification) v Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="09d76-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="09d76-120">Školitele binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="09d76-120">Binary classification trainers</span></span>

<span data-ttu-id="09d76-121">Model binární klasifikace můžete proškolit pomocí těchto algoritmů:</span><span class="sxs-lookup"><span data-stu-id="09d76-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="09d76-122">Binární vstupy a výstupy klasifikace</span><span class="sxs-lookup"><span data-stu-id="09d76-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="09d76-123">Pro dosažení nejlepších výsledků s binární klasifikací musí být školicí data vyvážená (tj. stejná čísla kladných a záporných školicích dat).</span><span class="sxs-lookup"><span data-stu-id="09d76-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="09d76-124">Před školením by měly být zpracovány chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="09d76-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="09d76-125">Data sloupce vstupního popisku musí být <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="09d76-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="09d76-126">Data ve sloupci vstupní funkce musí být vektorem s pevnou velikostí <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="09d76-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="09d76-127">Výstup učitelů má následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="09d76-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="09d76-128">Název výstupního sloupce</span><span class="sxs-lookup"><span data-stu-id="09d76-128">Output Column Name</span></span> | <span data-ttu-id="09d76-129">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="09d76-129">Column Type</span></span> | <span data-ttu-id="09d76-130">Popis</span><span class="sxs-lookup"><span data-stu-id="09d76-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="09d76-131">Nezpracované skóre, které bylo vypočítáno modelem</span><span class="sxs-lookup"><span data-stu-id="09d76-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="09d76-132">Předpokládaný popisek, založený na znaménku skóre.</span><span class="sxs-lookup"><span data-stu-id="09d76-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="09d76-133">Záporné skóre se mapuje na `false` a kladné skóre se mapuje na `true`.</span><span class="sxs-lookup"><span data-stu-id="09d76-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="09d76-134">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="09d76-134">Multiclass classification</span></span>

<span data-ttu-id="09d76-135">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předvídání třídy dat instance.</span><span class="sxs-lookup"><span data-stu-id="09d76-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="09d76-136">Vstup algoritmu klasifikace je sada příkladů s popisky.</span><span class="sxs-lookup"><span data-stu-id="09d76-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="09d76-137">Každý popisek normálně začíná jako text.</span><span class="sxs-lookup"><span data-stu-id="09d76-137">Each label normally starts as text.</span></span> <span data-ttu-id="09d76-138">Pak se spustí přes TermTransform, který ho převede na klíč (číselný) typ.</span><span class="sxs-lookup"><span data-stu-id="09d76-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="09d76-139">Výstup algoritmu klasifikace je klasifikátor, který můžete použít k předpovědi třídy nových neoznačených instancí.</span><span class="sxs-lookup"><span data-stu-id="09d76-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="09d76-140">Mezi příklady scénářů klasifikace s více třídami patří:</span><span class="sxs-lookup"><span data-stu-id="09d76-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="09d76-141">Určení plemene psa jako "Siberian Husky", "zlatý spuštění metody Retriever", "Poodle" atd.</span><span class="sxs-lookup"><span data-stu-id="09d76-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="09d76-142">Pochopíte recenze filmů jako "pozitivní", "neutrální" nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="09d76-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="09d76-143">Kategorizace hodnocení hotelu jako "umístění", "cena", "čistota" atd.</span><span class="sxs-lookup"><span data-stu-id="09d76-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="09d76-144">Další informace naleznete v článku o třídě s více [třídami](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="09d76-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="09d76-145">Jedna sada vs všechno upgraduje libovolný [postup binární klasifikace](#binary-classification) , aby fungovala u datových sad s více třídami.</span><span class="sxs-lookup"><span data-stu-id="09d76-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="09d76-146">Další informace o [Wikipedii] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="09d76-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="09d76-147">Školitel klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="09d76-147">Multiclass classification trainers</span></span>

<span data-ttu-id="09d76-148">Model klasifikace s více třídami můžete proškolit pomocí následujících školicích algoritmů:</span><span class="sxs-lookup"><span data-stu-id="09d76-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="09d76-149">Vstupy a výstupy s více třídami klasifikace</span><span class="sxs-lookup"><span data-stu-id="09d76-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="09d76-150">Data sloupce vstupního popisku musí být typu [Key](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="09d76-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="09d76-151">Sloupec funkce musí být vektorem pevné velikosti <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="09d76-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="09d76-152">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="09d76-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="09d76-153">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="09d76-153">Output Name</span></span> | <span data-ttu-id="09d76-154">Typ</span><span class="sxs-lookup"><span data-stu-id="09d76-154">Type</span></span> | <span data-ttu-id="09d76-155">Popis</span><span class="sxs-lookup"><span data-stu-id="09d76-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="09d76-156">vektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="09d76-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="09d76-157">Skóre všech tříd.</span><span class="sxs-lookup"><span data-stu-id="09d76-157">The scores of all classes.</span></span> <span data-ttu-id="09d76-158">Vyšší hodnota znamená vyšší pravděpodobnost pro přechod do přidružené třídy.</span><span class="sxs-lookup"><span data-stu-id="09d76-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="09d76-159">Pokud má i-th největší hodnotu, index předpokládaného popisku by byl i.</span><span class="sxs-lookup"><span data-stu-id="09d76-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="09d76-160">Všimněte si, že je index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="09d76-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="09d76-161">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="09d76-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="09d76-162">Index předpokládaného popisku.</span><span class="sxs-lookup"><span data-stu-id="09d76-162">The predicted label's index.</span></span> <span data-ttu-id="09d76-163">Pokud je jeho hodnota, vlastní popisek bude i-th kategorie v typu vstupního popisku s hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="09d76-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="09d76-164">Regrese</span><span class="sxs-lookup"><span data-stu-id="09d76-164">Regression</span></span>

<span data-ttu-id="09d76-165">Úkol [strojového učení pod dohledem](glossary.md#supervised-machine-learning) , který se používá k předpovědi hodnoty popisku ze sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="09d76-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="09d76-166">Popisek může být jakékoli reálné hodnoty a nepochází z konečné sady hodnot jako v rámci úloh klasifikace.</span><span class="sxs-lookup"><span data-stu-id="09d76-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="09d76-167">Regresní algoritmy modelují závislost popisku na jeho souvisejících funkcích, aby určili, jak se popisek změní, protože hodnoty funkcí se mění.</span><span class="sxs-lookup"><span data-stu-id="09d76-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="09d76-168">Vstup regresního algoritmu je sada příkladů s popisky známých hodnot.</span><span class="sxs-lookup"><span data-stu-id="09d76-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="09d76-169">Výstupem regresního algoritmu je funkce, kterou můžete použít k předpovědi hodnoty popisku pro všechny nové sady vstupních funkcí.</span><span class="sxs-lookup"><span data-stu-id="09d76-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="09d76-170">Mezi příklady scénářů regrese patří:</span><span class="sxs-lookup"><span data-stu-id="09d76-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="09d76-171">Předvídání cen domu na základě atributů na pracovišti, jako je počet ložnicemi, umístění nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="09d76-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="09d76-172">Předvídání budoucích cen za ceny na základě historických dat a současných vývojů na trhu.</span><span class="sxs-lookup"><span data-stu-id="09d76-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="09d76-173">Předvídání prodeje produktů na základě reklamních rozpočtů.</span><span class="sxs-lookup"><span data-stu-id="09d76-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="09d76-174">Regresní školitele</span><span class="sxs-lookup"><span data-stu-id="09d76-174">Regression trainers</span></span>

<span data-ttu-id="09d76-175">Regresní model můžete naučit pomocí těchto algoritmů:</span><span class="sxs-lookup"><span data-stu-id="09d76-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="09d76-176">Regrese – vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="09d76-176">Regression inputs and outputs</span></span>

<span data-ttu-id="09d76-177">Data sloupce vstupního popisku musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="09d76-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="09d76-178">Školitel pro tento úkol má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="09d76-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="09d76-179">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="09d76-179">Output Name</span></span> | <span data-ttu-id="09d76-180">Typ</span><span class="sxs-lookup"><span data-stu-id="09d76-180">Type</span></span> | <span data-ttu-id="09d76-181">Popis</span><span class="sxs-lookup"><span data-stu-id="09d76-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="09d76-182">Nezpracované skóre, které model předpovídá</span><span class="sxs-lookup"><span data-stu-id="09d76-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="09d76-183">Clustering</span><span class="sxs-lookup"><span data-stu-id="09d76-183">Clustering</span></span>

<span data-ttu-id="09d76-184">Úkol [strojového učení, který není pod dohledem](glossary.md#unsupervised-machine-learning) , který se používá k seskupení instancí dat do clusterů, které obsahují podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="09d76-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="09d76-185">Clustering lze také použít k identifikaci relací v datové sadě, které nemůžete logicky odvodit pomocí procházení nebo jednoduchého sledování.</span><span class="sxs-lookup"><span data-stu-id="09d76-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="09d76-186">Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodologii.</span><span class="sxs-lookup"><span data-stu-id="09d76-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="09d76-187">Můžete provést distribuci, těžiště, připojení nebo přístup na základě hustoty.</span><span class="sxs-lookup"><span data-stu-id="09d76-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="09d76-188">ML.NET aktuálně podporuje přístup založený na těžiště pomocí K-znamená clustering.</span><span class="sxs-lookup"><span data-stu-id="09d76-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="09d76-189">Mezi příklady scénářů clusteringu patří:</span><span class="sxs-lookup"><span data-stu-id="09d76-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="09d76-190">Porozumění segmentům hostů v hotelovém typu na základě zvyklostí a vlastností možností hotelu.</span><span class="sxs-lookup"><span data-stu-id="09d76-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="09d76-191">Identifikujte segmenty zákazníků a demografické údaje, které vám pomůžou vytvářet cílené reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="09d76-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="09d76-192">Kategorizace inventáře na základě výrobních metrik.</span><span class="sxs-lookup"><span data-stu-id="09d76-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="09d76-193">Clustering Trainer</span><span class="sxs-lookup"><span data-stu-id="09d76-193">Clustering trainer</span></span>

<span data-ttu-id="09d76-194">Model clusteringu můžete proškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="09d76-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="09d76-195">Vstupy a výstupy clusteringu</span><span class="sxs-lookup"><span data-stu-id="09d76-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="09d76-196">Data funkcí input musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="09d76-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="09d76-197">Nejsou nutné žádné popisky.</span><span class="sxs-lookup"><span data-stu-id="09d76-197">No labels are needed.</span></span>

<span data-ttu-id="09d76-198">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="09d76-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="09d76-199">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="09d76-199">Output Name</span></span> | <span data-ttu-id="09d76-200">Typ</span><span class="sxs-lookup"><span data-stu-id="09d76-200">Type</span></span> | <span data-ttu-id="09d76-201">Popis</span><span class="sxs-lookup"><span data-stu-id="09d76-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="09d76-202">vektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="09d76-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="09d76-203">Vzdálenosti daného datového bodu ke všem clusterům ' centriods</span><span class="sxs-lookup"><span data-stu-id="09d76-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="09d76-204">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="09d76-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="09d76-205">Index nejbližšího clusteru předpokládaný modelem.</span><span class="sxs-lookup"><span data-stu-id="09d76-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="09d76-206">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="09d76-206">Anomaly detection</span></span>

<span data-ttu-id="09d76-207">Tato úloha vytvoří model detekce anomálií pomocí hlavní komponenty pro analýzu (DPS).</span><span class="sxs-lookup"><span data-stu-id="09d76-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="09d76-208">Detekce anomálií založená na DPS vám pomůže sestavit model ve scénářích, kdy je snadné získat školicí data z jedné třídy, jako jsou platné transakce, ale obtížně získat dostatečné vzorky cílových anomálií.</span><span class="sxs-lookup"><span data-stu-id="09d76-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="09d76-209">V rámci strojového učení se často používá příhlas POMOCNÍKa při analýze dat, protože odhalí vnitřní strukturu dat a vysvětluje odchylku dat.</span><span class="sxs-lookup"><span data-stu-id="09d76-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="09d76-210">Funkce DPS funguje při analýze dat, která obsahují více proměnných.</span><span class="sxs-lookup"><span data-stu-id="09d76-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="09d76-211">Vyhledá korelaci mezi proměnnými a určí kombinaci hodnot, které nejlépe zachytí rozdíly ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="09d76-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="09d76-212">Tyto kombinované hodnoty funkcí slouží k vytvoření kompaktnějšího prostoru funkcí označovaného jako hlavní komponenty.</span><span class="sxs-lookup"><span data-stu-id="09d76-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="09d76-213">Detekce anomálií zahrnuje mnoho důležitých úloh ve strojovém učení:</span><span class="sxs-lookup"><span data-stu-id="09d76-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="09d76-214">Identifikujte transakce, které jsou potenciálně podvodné.</span><span class="sxs-lookup"><span data-stu-id="09d76-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="09d76-215">Výukové modely indikující, že došlo k narušení sítě.</span><span class="sxs-lookup"><span data-stu-id="09d76-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="09d76-216">Hledání neobvyklých clusterů pacientů.</span><span class="sxs-lookup"><span data-stu-id="09d76-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="09d76-217">Kontrola hodnot zadaných do systému.</span><span class="sxs-lookup"><span data-stu-id="09d76-217">Checking values entered into a system.</span></span>

<span data-ttu-id="09d76-218">Vzhledem k tomu, že anomálie jsou vzácné události podle definice, může být obtížné shromáždit reprezentativní vzorek dat, který se má použít pro modelování.</span><span class="sxs-lookup"><span data-stu-id="09d76-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="09d76-219">Algoritmy zahrnuté v této kategorii byly obzvláště navržené pro řešení základních výzev k sestavování a školení modelů pomocí nevyvážených datových sad.</span><span class="sxs-lookup"><span data-stu-id="09d76-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="09d76-220">Trainer detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="09d76-220">Anomaly detection trainer</span></span>

<span data-ttu-id="09d76-221">Model detekce anomálií můžete vyškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="09d76-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="09d76-222">Vstupy a výstupy detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="09d76-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="09d76-223">Vstupní funkce musí být vektor <xref:System.Single>pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="09d76-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="09d76-224">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="09d76-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="09d76-225">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="09d76-225">Output Name</span></span> | <span data-ttu-id="09d76-226">Typ</span><span class="sxs-lookup"><span data-stu-id="09d76-226">Type</span></span> | <span data-ttu-id="09d76-227">Popis</span><span class="sxs-lookup"><span data-stu-id="09d76-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="09d76-228">Nezáporné, neohraničené skóre, které bylo vypočítáno modelem detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="09d76-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="09d76-229">Hodnota true nebo false, která představuje, zda je vstup anomálií (PredictedLabel = true) nebo ne (PredictedLabel = false)</span><span class="sxs-lookup"><span data-stu-id="09d76-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="09d76-230">Pořadí</span><span class="sxs-lookup"><span data-stu-id="09d76-230">Ranking</span></span>

<span data-ttu-id="09d76-231">Úkol hodnocení sestaví seřazení ze sady popisných příkladů.</span><span class="sxs-lookup"><span data-stu-id="09d76-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="09d76-232">Tato ukázková sada se skládá ze skupin instancí, jejichž skóre se dá vyhodnotit pomocí daných kritérií.</span><span class="sxs-lookup"><span data-stu-id="09d76-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="09d76-233">Popisky hodnocení jsou pro každou instanci {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="09d76-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="09d76-234">Klasifikátor je vyškolen pro řazení nových skupin instancí s neznámým skóre pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="09d76-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="09d76-235">Seznámení s ML.NETm řazením [počítačů se seznámili podle hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) .</span><span class="sxs-lookup"><span data-stu-id="09d76-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="09d76-236">Hodnocení školicích algoritmů</span><span class="sxs-lookup"><span data-stu-id="09d76-236">Ranking training algorithms</span></span>

<span data-ttu-id="09d76-237">Model hodnocení můžete proškolit s následujícími algoritmy:</span><span class="sxs-lookup"><span data-stu-id="09d76-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="09d76-238">Řazení vstupů a výstupů</span><span class="sxs-lookup"><span data-stu-id="09d76-238">Ranking input and outputs</span></span>

<span data-ttu-id="09d76-239">Vstupní datový typ popisku musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) nebo <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="09d76-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="09d76-240">Hodnota popisku určuje relevanci, kde vyšší hodnoty označují vyšší relevanci.</span><span class="sxs-lookup"><span data-stu-id="09d76-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="09d76-241">Pokud je popisek typem [klíče](xref:Microsoft.ML.Data.KeyDataViewType) , pak je index klíče hodnota významnosti, kde nejmenší index je nejméně relevantní.</span><span class="sxs-lookup"><span data-stu-id="09d76-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="09d76-242">Pokud je popisek <xref:System.Single>, větší hodnoty znamenají vyšší relevance.</span><span class="sxs-lookup"><span data-stu-id="09d76-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="09d76-243">Data funkce musí být vektorem pevné velikosti <xref:System.Single> a sloupec vstupní skupiny řádků musí být typ [Key](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="09d76-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="09d76-244">Tento Trainer má následující výstup:</span><span class="sxs-lookup"><span data-stu-id="09d76-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="09d76-245">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="09d76-245">Output Name</span></span> | <span data-ttu-id="09d76-246">Typ</span><span class="sxs-lookup"><span data-stu-id="09d76-246">Type</span></span> | <span data-ttu-id="09d76-247">Popis</span><span class="sxs-lookup"><span data-stu-id="09d76-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="09d76-248">Neohraničené skóre, které bylo vypočítáno modelem k určení předpovědi</span><span class="sxs-lookup"><span data-stu-id="09d76-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="09d76-249">Doporučení</span><span class="sxs-lookup"><span data-stu-id="09d76-249">Recommendation</span></span>

<span data-ttu-id="09d76-250">Úkol doporučení umožňuje vytvořit seznam doporučených produktů nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="09d76-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="09d76-251">ML.NET používá pro doporučení algoritmus pro [filtrování](https://en.wikipedia.org/wiki/Collaborative_filtering) a vytváření [matic (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), pokud máte historická data hodnocení produktu ve vašem katalogu.</span><span class="sxs-lookup"><span data-stu-id="09d76-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="09d76-252">Máte například historická data o hodnocení filmu pro vaše uživatele a chcete doporučit další filmy, které se budou pravděpodobně sledovat.</span><span class="sxs-lookup"><span data-stu-id="09d76-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="09d76-253">Algoritmy školení pro doporučení</span><span class="sxs-lookup"><span data-stu-id="09d76-253">Recommendation training algorithms</span></span>

<span data-ttu-id="09d76-254">Model doporučení můžete vyškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="09d76-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="09d76-255">Prognózování</span><span class="sxs-lookup"><span data-stu-id="09d76-255">Forecasting</span></span>

<span data-ttu-id="09d76-256">Úkol prognózy používá data v minulosti v rámci časových řad k předpovědií o budoucím chování.</span><span class="sxs-lookup"><span data-stu-id="09d76-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="09d76-257">Scénáře, které se týkají předpovědi, zahrnují předpověď počasí, sezónní prodej předpovědi a prediktivní údržba.</span><span class="sxs-lookup"><span data-stu-id="09d76-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="09d76-258">Předpověď školitelů</span><span class="sxs-lookup"><span data-stu-id="09d76-258">Forecasting trainers</span></span>

<span data-ttu-id="09d76-259">Prognózový model můžete proškolit pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="09d76-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
