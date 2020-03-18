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
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="fe253-103">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe253-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="fe253-104">Úloha strojového učení je typ predikce nebo odvození, které se provádí, na základě problému nebo otázky, která je kladena, a dostupných dat.</span><span class="sxs-lookup"><span data-stu-id="fe253-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="fe253-105">Například úkol klasifikace přiřazuje data kategoriím a clustering úkoly seskupí data podle podobnosti.</span><span class="sxs-lookup"><span data-stu-id="fe253-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="fe253-106">Úlohy strojového učení spoléhají na vzory v datech, nikoli na explicitně naprogramované.</span><span class="sxs-lookup"><span data-stu-id="fe253-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="fe253-107">Tento článek popisuje různé úkoly strojového učení, ze kterých si můžete vybrat v ML.NET a některé běžné případy použití.</span><span class="sxs-lookup"><span data-stu-id="fe253-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="fe253-108">Jakmile jste se rozhodli, který úkol funguje pro váš scénář, musíte zvolit nejlepší algoritmus pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="fe253-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="fe253-109">Dostupné algoritmy jsou uvedeny v části pro každý úkol.</span><span class="sxs-lookup"><span data-stu-id="fe253-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="fe253-110">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="fe253-110">Binary classification</span></span>

<span data-ttu-id="fe253-111">Úkol [strojového učení pod dohledem,](glossary.md#supervised-machine-learning) který se používá k předvídání, do kterých dvou tříd (kategorií) patří instance dat.</span><span class="sxs-lookup"><span data-stu-id="fe253-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="fe253-112">Vstup klasifikační algoritmus je sada popisek příklady, kde každý popisek je celé číslo buď 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="fe253-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="fe253-113">Výstup binární klasifikační algoritmus je třídění, které můžete použít k předpovědět třídu nových instancí bez popisku.</span><span class="sxs-lookup"><span data-stu-id="fe253-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="fe253-114">Příklady binárních scénářů klasifikace zahrnují:</span><span class="sxs-lookup"><span data-stu-id="fe253-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="fe253-115">[Pochopení sentimentu komentářů Twitter](../tutorials/sentiment-analysis.md) jako "pozitivní" nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="fe253-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="fe253-116">Diagnostika, zda má pacient určitou nemoc nebo ne.</span><span class="sxs-lookup"><span data-stu-id="fe253-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="fe253-117">Rozhodování o označení e-mailu jako "spam", nebo ne.</span><span class="sxs-lookup"><span data-stu-id="fe253-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="fe253-118">Určení, zda fotografie obsahuje určitou položku nebo ne, například psa nebo ovoce.</span><span class="sxs-lookup"><span data-stu-id="fe253-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="fe253-119">Další informace naleznete v článku [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="fe253-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="fe253-120">Binární klasifikace školitelů</span><span class="sxs-lookup"><span data-stu-id="fe253-120">Binary classification trainers</span></span>

<span data-ttu-id="fe253-121">Binární klasifikační model můžete trénovat pomocí následujících algoritmů:</span><span class="sxs-lookup"><span data-stu-id="fe253-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="fe253-122">Binární klasifikační vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="fe253-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="fe253-123">Pro dosažení nejlepších výsledků s binární klasifikací by měla být vyvážená data školení (to znamená stejný počet pozitivních a záporných trénovacích dat).</span><span class="sxs-lookup"><span data-stu-id="fe253-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="fe253-124">Chybějící hodnoty by měly být zpracovány před tréninkem.</span><span class="sxs-lookup"><span data-stu-id="fe253-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="fe253-125">Data sloupce vstupního <xref:System.Boolean>popisku musí být .</span><span class="sxs-lookup"><span data-stu-id="fe253-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="fe253-126">Data sloupce vstupnífunkce musí být vektor <xref:System.Single>pevné velikosti .</span><span class="sxs-lookup"><span data-stu-id="fe253-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="fe253-127">Tyto školicí prvky výstup následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="fe253-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="fe253-128">Název výstupního sloupce</span><span class="sxs-lookup"><span data-stu-id="fe253-128">Output Column Name</span></span> | <span data-ttu-id="fe253-129">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="fe253-129">Column Type</span></span> | <span data-ttu-id="fe253-130">Popis</span><span class="sxs-lookup"><span data-stu-id="fe253-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="fe253-131">Hrubé skóre, které bylo vypočteno modelem</span><span class="sxs-lookup"><span data-stu-id="fe253-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="fe253-132">Předpovídaný popisek, na základě znaménko skóre.</span><span class="sxs-lookup"><span data-stu-id="fe253-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="fe253-133">Negativní skóre mapuje a `false` pozitivní `true`skóre mapuje na .</span><span class="sxs-lookup"><span data-stu-id="fe253-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="fe253-134">Klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="fe253-134">Multiclass classification</span></span>

<span data-ttu-id="fe253-135">Úkol [strojového učení pod dohledem,](glossary.md#supervised-machine-learning) který se používá k předvídání třídy (kategorie) instance dat.</span><span class="sxs-lookup"><span data-stu-id="fe253-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="fe253-136">Vstup klasifikačníalgoritmus je sada popisek příklady.</span><span class="sxs-lookup"><span data-stu-id="fe253-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="fe253-137">Každý popisek obvykle začíná jako text.</span><span class="sxs-lookup"><span data-stu-id="fe253-137">Each label normally starts as text.</span></span> <span data-ttu-id="fe253-138">Potom je spuštěn prostřednictvím TermTransform, který převádí na klíč (číselný) typ.</span><span class="sxs-lookup"><span data-stu-id="fe253-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="fe253-139">Výstup klasifikačního algoritmu je třídění, které můžete použít k předvídání třídy nových instancí bez popisku.</span><span class="sxs-lookup"><span data-stu-id="fe253-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="fe253-140">Příklady scénářů klasifikace více tříd:</span><span class="sxs-lookup"><span data-stu-id="fe253-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="fe253-141">Určení plemene psa jako "sibiřského Huskyho", "Zlatého retrívra", "Pudla" atd.</span><span class="sxs-lookup"><span data-stu-id="fe253-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="fe253-142">Pochopení filmové recenze jako "pozitivní", "neutrální", nebo "negativní".</span><span class="sxs-lookup"><span data-stu-id="fe253-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="fe253-143">Kategorizace recenzí hotelů jako "umístění", "cena", "čistota" atd.</span><span class="sxs-lookup"><span data-stu-id="fe253-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="fe253-144">Další informace naleznete v článku [klasifikace více tříd](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="fe253-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="fe253-145">Jeden vs všechny upgrady jakékoli [binární klasifikace studenta](#binary-classification) jednat o vícetřídových datových sad.</span><span class="sxs-lookup"><span data-stu-id="fe253-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="fe253-146">Více informací o [Wikipedii] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="fe253-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="fe253-147">Vícetřídní klasifikační trenažér</span><span class="sxs-lookup"><span data-stu-id="fe253-147">Multiclass classification trainers</span></span>

<span data-ttu-id="fe253-148">Můžete trénovat vícetřídní klasifikační model pomocí následujících trénovacích algoritmů:</span><span class="sxs-lookup"><span data-stu-id="fe253-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="fe253-149">Vícetřídní klasifikační vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="fe253-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="fe253-150">Data sloupce vstupního popisku musí být typ [klíče.](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="fe253-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="fe253-151">Sloupec prvku musí být vektor <xref:System.Single>pevné velikosti .</span><span class="sxs-lookup"><span data-stu-id="fe253-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="fe253-152">Tento trenažér výstupy následující:</span><span class="sxs-lookup"><span data-stu-id="fe253-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="fe253-153">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="fe253-153">Output Name</span></span> | <span data-ttu-id="fe253-154">Typ</span><span class="sxs-lookup"><span data-stu-id="fe253-154">Type</span></span> | <span data-ttu-id="fe253-155">Popis</span><span class="sxs-lookup"><span data-stu-id="fe253-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="fe253-156">Vektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="fe253-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="fe253-157">Skóre všech tříd.</span><span class="sxs-lookup"><span data-stu-id="fe253-157">The scores of all classes.</span></span> <span data-ttu-id="fe253-158">Vyšší hodnota znamená vyšší pravděpodobnost, že spadají do přidružené třídy.</span><span class="sxs-lookup"><span data-stu-id="fe253-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="fe253-159">Pokud i-th element má největší hodnotu, by byl index předpovídaný popisek i.</span><span class="sxs-lookup"><span data-stu-id="fe253-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="fe253-160">Všimněte si, že i je nula-založené index.</span><span class="sxs-lookup"><span data-stu-id="fe253-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="fe253-161">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="fe253-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="fe253-162">Index předpovídaného popisku.</span><span class="sxs-lookup"><span data-stu-id="fe253-162">The predicted label's index.</span></span> <span data-ttu-id="fe253-163">Pokud je jeho hodnota i, skutečný popisek by byla i-th kategorie v typu vstupní popisek s hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="fe253-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="fe253-164">Regrese</span><span class="sxs-lookup"><span data-stu-id="fe253-164">Regression</span></span>

<span data-ttu-id="fe253-165">Úkol [strojového učení pod dohledem,](glossary.md#supervised-machine-learning) který se používá k předvídání hodnoty popisku ze sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="fe253-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="fe253-166">Popisek může mít libovolnou reálnou hodnotu a nepochází z omezené sady hodnot jako v úkolech klasifikace.</span><span class="sxs-lookup"><span data-stu-id="fe253-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="fe253-167">Regresní algoritmy modelují závislost popisku na souvisejících funkcích, aby určily, jak se popisek bude měnit, protože hodnoty prvků se mění.</span><span class="sxs-lookup"><span data-stu-id="fe253-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="fe253-168">Vstup regresníalgoritmus je sada příkladů s popisky známých hodnot.</span><span class="sxs-lookup"><span data-stu-id="fe253-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="fe253-169">Výstup regresníalgoritmus je funkce, kterou můžete použít k předpovědět hodnotu popisku pro všechny nové sady vstupních funkcí.</span><span class="sxs-lookup"><span data-stu-id="fe253-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="fe253-170">Příklady regresních scénářů:</span><span class="sxs-lookup"><span data-stu-id="fe253-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="fe253-171">Předpovídání cen domů na základě atributů domu, jako je počet ložnic, umístění nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="fe253-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="fe253-172">Předpovídání budoucích cen akcií na základě historických údajů a současných tržních trendů.</span><span class="sxs-lookup"><span data-stu-id="fe253-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="fe253-173">Předvídání prodeje produktu na základě rozpočtů na reklamu.</span><span class="sxs-lookup"><span data-stu-id="fe253-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="fe253-174">Regresní trenéři</span><span class="sxs-lookup"><span data-stu-id="fe253-174">Regression trainers</span></span>

<span data-ttu-id="fe253-175">Regresní model můžete trénovat pomocí následujících algoritmů:</span><span class="sxs-lookup"><span data-stu-id="fe253-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="fe253-176">Regresní vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="fe253-176">Regression inputs and outputs</span></span>

<span data-ttu-id="fe253-177">Data sloupce vstupního <xref:System.Single>popisku musí být .</span><span class="sxs-lookup"><span data-stu-id="fe253-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="fe253-178">Školitelů pro tento úkol výstup následující:</span><span class="sxs-lookup"><span data-stu-id="fe253-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="fe253-179">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="fe253-179">Output Name</span></span> | <span data-ttu-id="fe253-180">Typ</span><span class="sxs-lookup"><span data-stu-id="fe253-180">Type</span></span> | <span data-ttu-id="fe253-181">Popis</span><span class="sxs-lookup"><span data-stu-id="fe253-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="fe253-182">Hrubé skóre, které bylo předpovězeno modelem</span><span class="sxs-lookup"><span data-stu-id="fe253-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="fe253-183">Clustering</span><span class="sxs-lookup"><span data-stu-id="fe253-183">Clustering</span></span>

<span data-ttu-id="fe253-184">Úloha [strojového učení bez dozoru,](glossary.md#unsupervised-machine-learning) která se používá k seskupení instancí dat do clusterů, které obsahují podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="fe253-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="fe253-185">Clustering lze také použít k identifikaci vztahů v datové sadě, které nemusí logicky odvodit procházením nebo jednoduchým pozorováním.</span><span class="sxs-lookup"><span data-stu-id="fe253-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="fe253-186">Vstupy a výstupy clustering algoritmu závisí na zvolené metodice.</span><span class="sxs-lookup"><span data-stu-id="fe253-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="fe253-187">Můžete provést přístup založený na distribuci, centroidu, připojení nebo hustotě.</span><span class="sxs-lookup"><span data-stu-id="fe253-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="fe253-188">ML.NET v současné době podporuje přístup založený na centroidu pomocí clusteringu K-Means.</span><span class="sxs-lookup"><span data-stu-id="fe253-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="fe253-189">Příklady scénářů clusteringu:</span><span class="sxs-lookup"><span data-stu-id="fe253-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="fe253-190">Pochopení segmentů hotelových hostů na základě návyků a charakteristik hotelové volby.</span><span class="sxs-lookup"><span data-stu-id="fe253-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="fe253-191">Identifikace zákaznických segmentů a demografických údajů s cílem pomoci vytvářet cílené reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="fe253-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="fe253-192">Kategorizace zásob na základě výrobních metrik.</span><span class="sxs-lookup"><span data-stu-id="fe253-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="fe253-193">Shlukovací trenér</span><span class="sxs-lookup"><span data-stu-id="fe253-193">Clustering trainer</span></span>

<span data-ttu-id="fe253-194">Model clusteringu můžete trénovat pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="fe253-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="fe253-195">Clustering vstupů a výstupů</span><span class="sxs-lookup"><span data-stu-id="fe253-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="fe253-196">Vstupní funkce data <xref:System.Single>musí být .</span><span class="sxs-lookup"><span data-stu-id="fe253-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="fe253-197">Nejsou potřeba žádné štítky.</span><span class="sxs-lookup"><span data-stu-id="fe253-197">No labels are needed.</span></span>

<span data-ttu-id="fe253-198">Tento trenažér výstupy následující:</span><span class="sxs-lookup"><span data-stu-id="fe253-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="fe253-199">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="fe253-199">Output Name</span></span> | <span data-ttu-id="fe253-200">Typ</span><span class="sxs-lookup"><span data-stu-id="fe253-200">Type</span></span> | <span data-ttu-id="fe253-201">Popis</span><span class="sxs-lookup"><span data-stu-id="fe253-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="fe253-202">vektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="fe253-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="fe253-203">Vzdálenosti daného datového bodu k centriodům všech klastrů</span><span class="sxs-lookup"><span data-stu-id="fe253-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="fe253-204">typ [klíče](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="fe253-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="fe253-205">Nejbližší index clusteru předpověděl model.</span><span class="sxs-lookup"><span data-stu-id="fe253-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="fe253-206">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="fe253-206">Anomaly detection</span></span>

<span data-ttu-id="fe253-207">Tato úloha vytvoří model detekce anomálií pomocí analýzy primární chř složky (PCA).</span><span class="sxs-lookup"><span data-stu-id="fe253-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="fe253-208">Detekce anomálií na základě PCA pomáhá vytvořit model ve scénářích, kde je snadné získat trénovací data z jedné třídy, jako jsou platné transakce, ale obtížné získat dostatečné vzorky cílené anomálie.</span><span class="sxs-lookup"><span data-stu-id="fe253-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="fe253-209">Zavedená technika ve strojovém učení, PCA se často používá v analýzě průzkumných dat, protože odhaluje vnitřní strukturu dat a vysvětluje odchylku v datech.</span><span class="sxs-lookup"><span data-stu-id="fe253-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="fe253-210">PCA funguje tak, že analyzuje data, která obsahují více proměnných.</span><span class="sxs-lookup"><span data-stu-id="fe253-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="fe253-211">Hledá korelace mezi proměnnými a určuje kombinaci hodnot, které nejlépe zachycuje rozdíly ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="fe253-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="fe253-212">Tyto kombinované hodnoty prvků se používají k vytvoření kompaktnějšího prostoru prvku nazývaného hlavní součásti.</span><span class="sxs-lookup"><span data-stu-id="fe253-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="fe253-213">Detekce anomálií zahrnuje mnoho důležitých úkolů ve strojovém učení:</span><span class="sxs-lookup"><span data-stu-id="fe253-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="fe253-214">Identifikace transakcí, které jsou potenciálně podvodné.</span><span class="sxs-lookup"><span data-stu-id="fe253-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="fe253-215">Vzory učení, které označují, že došlo k narušení sítě.</span><span class="sxs-lookup"><span data-stu-id="fe253-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="fe253-216">Hledání abnormálních shluků pacientů.</span><span class="sxs-lookup"><span data-stu-id="fe253-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="fe253-217">Kontrola hodnot zadaných do systému.</span><span class="sxs-lookup"><span data-stu-id="fe253-217">Checking values entered into a system.</span></span>

<span data-ttu-id="fe253-218">Vzhledem k tomu, že anomálie jsou vzácné události podle definice, může být obtížné shromáždit reprezentativní vzorek dat pro modelování.</span><span class="sxs-lookup"><span data-stu-id="fe253-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="fe253-219">Algoritmy zahrnuté v této kategorii byly speciálně navrženy tak, aby řešily hlavní problémy vytváření a školení pomocí nevyvážených datových sad.</span><span class="sxs-lookup"><span data-stu-id="fe253-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="fe253-220">Trenažér detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="fe253-220">Anomaly detection trainer</span></span>

<span data-ttu-id="fe253-221">Model detekce anomálií můžete trénovat pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="fe253-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="fe253-222">Vstupy a výstupy detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="fe253-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="fe253-223">Vstupní prvky musí být vektor pevné <xref:System.Single>velikosti .</span><span class="sxs-lookup"><span data-stu-id="fe253-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="fe253-224">Tento trenažér výstupy následující:</span><span class="sxs-lookup"><span data-stu-id="fe253-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="fe253-225">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="fe253-225">Output Name</span></span> | <span data-ttu-id="fe253-226">Typ</span><span class="sxs-lookup"><span data-stu-id="fe253-226">Type</span></span> | <span data-ttu-id="fe253-227">Popis</span><span class="sxs-lookup"><span data-stu-id="fe253-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="fe253-228">Nezáporné, neomezené skóre, které bylo vypočteno modelem detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="fe253-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="fe253-229">True/false hodnota představující, zda vstup je anomálie (PredictedLabel = true) nebo ne (PredictedLabel = false)</span><span class="sxs-lookup"><span data-stu-id="fe253-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="fe253-230">Pořadí</span><span class="sxs-lookup"><span data-stu-id="fe253-230">Ranking</span></span>

<span data-ttu-id="fe253-231">Úkol hodnocení vytvoří ranker ze sady popisek příklady.</span><span class="sxs-lookup"><span data-stu-id="fe253-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="fe253-232">Tato ukázková sada se skládá ze skupin instancí, které mohou být hodnoceny s danými kritérii.</span><span class="sxs-lookup"><span data-stu-id="fe253-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="fe253-233">Popisky hodnocení jsou { 0, 1, 2, 3, 4 } pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="fe253-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="fe253-234">Ranker je trénován tak, aby seřadil nové skupiny instancí s neznámým skóre pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="fe253-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="fe253-235">ML.NET žebříčků jsou [strojově naučené hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) založené.</span><span class="sxs-lookup"><span data-stu-id="fe253-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="fe253-236">Algoritmy hodnocení</span><span class="sxs-lookup"><span data-stu-id="fe253-236">Ranking training algorithms</span></span>

<span data-ttu-id="fe253-237">Můžete trénovat model hodnocení s následujícími algoritmy:</span><span class="sxs-lookup"><span data-stu-id="fe253-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="fe253-238">Pořadí vstupů a výstupů</span><span class="sxs-lookup"><span data-stu-id="fe253-238">Ranking input and outputs</span></span>

<span data-ttu-id="fe253-239">Datový typ vstupního [key](xref:Microsoft.ML.Data.KeyDataViewType) popisku <xref:System.Single>musí být typ klíče nebo .</span><span class="sxs-lookup"><span data-stu-id="fe253-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="fe253-240">Hodnota popisku určuje relevanci, kde vyšší hodnoty označují vyšší relevanci.</span><span class="sxs-lookup"><span data-stu-id="fe253-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="fe253-241">Pokud je popisek typ [klíče,](xref:Microsoft.ML.Data.KeyDataViewType) pak index klíče je hodnota relevance, kde nejmenší index je nejméně relevantní.</span><span class="sxs-lookup"><span data-stu-id="fe253-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="fe253-242">Pokud je popisek <xref:System.Single>, větší hodnoty označují vyšší relevanci.</span><span class="sxs-lookup"><span data-stu-id="fe253-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="fe253-243">Data prvku musí být vektor <xref:System.Single> pevné velikosti a sloupec skupiny vstupních řádků musí být typ [klíče.](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="fe253-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="fe253-244">Tento trenažér výstupy následující:</span><span class="sxs-lookup"><span data-stu-id="fe253-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="fe253-245">Název výstupu</span><span class="sxs-lookup"><span data-stu-id="fe253-245">Output Name</span></span> | <span data-ttu-id="fe253-246">Typ</span><span class="sxs-lookup"><span data-stu-id="fe253-246">Type</span></span> | <span data-ttu-id="fe253-247">Popis</span><span class="sxs-lookup"><span data-stu-id="fe253-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="fe253-248">Neomezené skóre, které bylo vypočteno modelem k určení předpovědi</span><span class="sxs-lookup"><span data-stu-id="fe253-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="fe253-249">Doporučení</span><span class="sxs-lookup"><span data-stu-id="fe253-249">Recommendation</span></span>

<span data-ttu-id="fe253-250">Úloha doporučení umožňuje vytvoření seznamu doporučených produktů nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="fe253-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="fe253-251">ML.NET používá [maticovou faktorizaci (MF),](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)algoritmus [kolaborativního filtrování](https://en.wikipedia.org/wiki/Collaborative_filtering) pro doporučení, pokud máte v katalogu historická data hodnocení produktu.</span><span class="sxs-lookup"><span data-stu-id="fe253-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="fe253-252">Máte například historická data hodnocení filmů pro uživatele a chcete doporučit další filmy, které budou pravděpodobně sledovat příště.</span><span class="sxs-lookup"><span data-stu-id="fe253-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="fe253-253">Algoritmy pro školení doporučení</span><span class="sxs-lookup"><span data-stu-id="fe253-253">Recommendation training algorithms</span></span>

<span data-ttu-id="fe253-254">Model doporučení můžete trénovat pomocí následujícího algoritmu:</span><span class="sxs-lookup"><span data-stu-id="fe253-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="fe253-255">Prognózování</span><span class="sxs-lookup"><span data-stu-id="fe253-255">Forecasting</span></span>

<span data-ttu-id="fe253-256">Prognostické úkol použít minulé časové řady data, aby předpovědi o budoucím chování.</span><span class="sxs-lookup"><span data-stu-id="fe253-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="fe253-257">Scénáře použitelné pro předpověď zahrnují předpověď počasí, předpovědi sezónních prodejů a prediktivní údržbu,</span><span class="sxs-lookup"><span data-stu-id="fe253-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="fe253-258">Předvídání školitelů</span><span class="sxs-lookup"><span data-stu-id="fe253-258">Forecasting trainers</span></span>

<span data-ttu-id="fe253-259">Můžete trénovat model prognózy s následujícím algoritmem:</span><span class="sxs-lookup"><span data-stu-id="fe253-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
