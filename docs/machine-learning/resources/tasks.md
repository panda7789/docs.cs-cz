---
title: Úkoly strojového učení
description: Prozkoumejte různé strojového učení úkoly a přidružené úlohy, které jsou podporovány v ML.NET.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: ed6361fdcbca11c100ee5cae4ca76e152ddfba11
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063542"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="21d29-103">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="21d29-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="21d29-104">Při sestavování model strojového učení, musíte nejprve definovat jsou doufá dosáhnout s vašimi daty.</span><span class="sxs-lookup"><span data-stu-id="21d29-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="21d29-105">To umožňuje zvolit správný strojového učení úkol pro konkrétní situaci.</span><span class="sxs-lookup"><span data-stu-id="21d29-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="21d29-106">Následující seznam popisuje různé strojového učení úlohy, které můžete vybrat z a některé běžné případy použití.</span><span class="sxs-lookup"><span data-stu-id="21d29-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="21d29-107">Až si ověříte, které úloha se dá použít pro váš scénář, pak musíte zvolit nejlepší algoritmus k natrénování modelu.</span><span class="sxs-lookup"><span data-stu-id="21d29-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="21d29-108">K dispozici algoritmy jsou uvedené v části pro každý úkol.</span><span class="sxs-lookup"><span data-stu-id="21d29-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="21d29-109">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="21d29-109">Binary classification</span></span>

<span data-ttu-id="21d29-110">A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi, které instance dat patří do dvou tříd (kategorie).</span><span class="sxs-lookup"><span data-stu-id="21d29-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="21d29-111">Vstup klasifikační algoritmus je sada s popiskem příklady, kde každý popisek je celé číslo 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="21d29-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="21d29-112">Výstupní binární klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku.</span><span class="sxs-lookup"><span data-stu-id="21d29-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="21d29-113">Příklady scénářů binární klasifikace:</span><span class="sxs-lookup"><span data-stu-id="21d29-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="21d29-114">[Principy mínění Twitteru, komentářů](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="21d29-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="21d29-115">Diagnostika zda pacienta má určitá stádiu, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="21d29-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="21d29-116">Rozhodování k označení e-mailu jako "nevyžádanou poštu" nebo ne.</span><span class="sxs-lookup"><span data-stu-id="21d29-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="21d29-117">Určení, zda obsahuje fotografii dog nebo výsledku.</span><span class="sxs-lookup"><span data-stu-id="21d29-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="21d29-118">Další informace najdete v tématu [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) článku na wikipedii.</span><span class="sxs-lookup"><span data-stu-id="21d29-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="21d29-119">Binární klasifikace školitelé</span><span class="sxs-lookup"><span data-stu-id="21d29-119">Binary classification trainers</span></span>

<span data-ttu-id="21d29-120">Trénovat binární klasifikační model pomocí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="21d29-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="21d29-121">Binární klasifikace vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="21d29-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="21d29-122">Pro nejlepší výsledky pomocí binární klasifikace trénovací data, musíte vyvážit (to znamená rovná čísla kladné a záporné trénovacích dat).</span><span class="sxs-lookup"><span data-stu-id="21d29-122">For best results with binary classification, the training data should be balanced (i.e. equal numbers of positive and negative training data).</span></span> <span data-ttu-id="21d29-123">Chybí a hodnoty by měly zpracovat před školení.</span><span class="sxs-lookup"><span data-stu-id="21d29-123">Missing and values should be handled before training.</span></span>

<span data-ttu-id="21d29-124">Popisek vstupní sloupec data musí být <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="21d29-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="21d29-125">Data funkce vstupní sloupce musí být vektor pevné velikosti <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="21d29-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="21d29-126">Tyto školitelé výstupy následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="21d29-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="21d29-127">Název výstupního sloupce</span><span class="sxs-lookup"><span data-stu-id="21d29-127">Output Column Name</span></span> | <span data-ttu-id="21d29-128">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="21d29-128">Column Type</span></span> | <span data-ttu-id="21d29-129">Popis</span><span class="sxs-lookup"><span data-stu-id="21d29-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="21d29-130">Nezpracovaná skóre, které se počítá podle modelu</span><span class="sxs-lookup"><span data-stu-id="21d29-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="21d29-131">Předpokládaná popisku na základě znaménka skóre.</span><span class="sxs-lookup"><span data-stu-id="21d29-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="21d29-132">Záporná skóre se mapuje na `false` a kladné skóre se mapuje na `true`.</span><span class="sxs-lookup"><span data-stu-id="21d29-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="21d29-133">Klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="21d29-133">Multiclass classification</span></span>

<span data-ttu-id="21d29-134">A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi třídu instance data (kategorie).</span><span class="sxs-lookup"><span data-stu-id="21d29-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="21d29-135">Vstup klasifikační algoritmus je sada s popiskem příklady.</span><span class="sxs-lookup"><span data-stu-id="21d29-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="21d29-136">Každý popisek normálně spustí jako text.</span><span class="sxs-lookup"><span data-stu-id="21d29-136">Each label normally starts as text.</span></span> <span data-ttu-id="21d29-137">Následně se spustí prostřednictvím TermTransform, který převádí na typ klíče (číselné).</span><span class="sxs-lookup"><span data-stu-id="21d29-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="21d29-138">Výstup klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku.</span><span class="sxs-lookup"><span data-stu-id="21d29-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="21d29-139">Příklady scénářů roc klasifikace:</span><span class="sxs-lookup"><span data-stu-id="21d29-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="21d29-140">Určení emulátorem pes jako "Siberian Husky", "Golden načítací", "Co", atd.</span><span class="sxs-lookup"><span data-stu-id="21d29-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="21d29-141">Principy film revize jako "kladné", "neutrální" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="21d29-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="21d29-142">Kategorizace hotelu revize jako "umístění", "price", "čistota" atd.</span><span class="sxs-lookup"><span data-stu-id="21d29-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="21d29-143">Další informace najdete v tématu [klasifikace víc tříd](https://en.wikipedia.org/wiki/Multiclass_classification) článku na wikipedii.</span><span class="sxs-lookup"><span data-stu-id="21d29-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="21d29-144">Jeden vs všechny upgraduje všechny [binární klasifikace learner](#binary-classification) k práci s více třídami datové sady.</span><span class="sxs-lookup"><span data-stu-id="21d29-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="21d29-145">Další informace o [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="21d29-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="21d29-146">Školitelé klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="21d29-146">Multiclass classification trainers</span></span>

<span data-ttu-id="21d29-147">Trénovat klasifikace víc tříd modelu pomocí následujících trénování algoritmů:</span><span class="sxs-lookup"><span data-stu-id="21d29-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="21d29-148">Klasifikace víc tříd vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="21d29-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="21d29-149">Popisek vstupní sloupec data musí být [klíč](xref:Microsoft.ML.Data.KeyDataViewType) typu.</span><span class="sxs-lookup"><span data-stu-id="21d29-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="21d29-150">Sloupec funkce musí být vektor pevné velikosti <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="21d29-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="21d29-151">Výstupem této trainer následující:</span><span class="sxs-lookup"><span data-stu-id="21d29-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="21d29-152">Název výstupního</span><span class="sxs-lookup"><span data-stu-id="21d29-152">Output Name</span></span> | <span data-ttu-id="21d29-153">Type</span><span class="sxs-lookup"><span data-stu-id="21d29-153">Type</span></span> | <span data-ttu-id="21d29-154">Popis</span><span class="sxs-lookup"><span data-stu-id="21d29-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="21d29-155">Vektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="21d29-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="21d29-156">Skóre všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="21d29-156">The scores of all classes.</span></span> <span data-ttu-id="21d29-157">Vyšší hodnota znamená vyšší pravděpodobnost spadat do přidružené třídy.</span><span class="sxs-lookup"><span data-stu-id="21d29-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="21d29-158">Pokud i tý prvek má největší hodnota, index předpokládané popisek bude i.</span><span class="sxs-lookup"><span data-stu-id="21d29-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="21d29-159">Všimněte si, že i je index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="21d29-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="21d29-160">[klíč](xref:Microsoft.ML.Data.KeyDataViewType) typu</span><span class="sxs-lookup"><span data-stu-id="21d29-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="21d29-161">Index předpokládané popisek.</span><span class="sxs-lookup"><span data-stu-id="21d29-161">The predicted label's index.</span></span> <span data-ttu-id="21d29-162">Pokud je jeho hodnota i, skutečné popisek by i tý kategorie v typu s hodnotou klíče vstupní popisek.</span><span class="sxs-lookup"><span data-stu-id="21d29-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="21d29-163">Regrese</span><span class="sxs-lookup"><span data-stu-id="21d29-163">Regression</span></span>

<span data-ttu-id="21d29-164">A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi hodnota popisku na základě sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="21d29-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="21d29-165">Popisek může být libovolné skutečné hodnoty a je neumožňují omezenou sadu hodnot jako úlohy klasifikace.</span><span class="sxs-lookup"><span data-stu-id="21d29-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="21d29-166">Regresní model algoritmy závislost popisek na jeho související funkce, chcete-li zjistit, jak se změní popisek jako hodnoty funkcí se lišily.</span><span class="sxs-lookup"><span data-stu-id="21d29-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="21d29-167">Vstup regresního algoritmu je sada příklady s popisky známé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="21d29-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="21d29-168">Výstup tohoto regresního algoritmu je funkce, které můžete použít k predikci hodnoty popisku pro všechny nové sady vstupní funkce.</span><span class="sxs-lookup"><span data-stu-id="21d29-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="21d29-169">Příklady scénářů regrese:</span><span class="sxs-lookup"><span data-stu-id="21d29-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="21d29-170">Odhad ceny Domů na základě atributů house například počtu ložnic, umístění a velikosti.</span><span class="sxs-lookup"><span data-stu-id="21d29-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="21d29-171">Předpovídání budoucích cenami akcií na základě historických dat a aktuální trendy na trhu.</span><span class="sxs-lookup"><span data-stu-id="21d29-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="21d29-172">Předpověď prodeje podle inzerování rozpočty produktu.</span><span class="sxs-lookup"><span data-stu-id="21d29-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="21d29-173">Regrese školitelé</span><span class="sxs-lookup"><span data-stu-id="21d29-173">Regression trainers</span></span>

<span data-ttu-id="21d29-174">Trénovat regresního modelu pomocí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="21d29-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="21d29-175">Regrese vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="21d29-175">Regression inputs and outputs</span></span>

<span data-ttu-id="21d29-176">Popisek vstupní sloupec data musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="21d29-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="21d29-177">Školitelé pro tuto úlohu výstup následující:</span><span class="sxs-lookup"><span data-stu-id="21d29-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="21d29-178">Název výstupního</span><span class="sxs-lookup"><span data-stu-id="21d29-178">Output Name</span></span> | <span data-ttu-id="21d29-179">Type</span><span class="sxs-lookup"><span data-stu-id="21d29-179">Type</span></span> | <span data-ttu-id="21d29-180">Popis</span><span class="sxs-lookup"><span data-stu-id="21d29-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="21d29-181">Nezpracovaná skóre, které se předpovědět modelem</span><span class="sxs-lookup"><span data-stu-id="21d29-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="21d29-182">Vytváření clusterů</span><span class="sxs-lookup"><span data-stu-id="21d29-182">Clustering</span></span>

<span data-ttu-id="21d29-183">[Nastavenou možnost bez dohledu strojového učení](glossary.md#unsupervised-machine-learning) úlohu, která se používá k skupiny instancí data do clusterů obsahující podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="21d29-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="21d29-184">Clustering lze také identifikovat relací v datové sadě, která nemusí být odvozena logicky sledováním procházení nebo jednoduché.</span><span class="sxs-lookup"><span data-stu-id="21d29-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="21d29-185">Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodě.</span><span class="sxs-lookup"><span data-stu-id="21d29-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="21d29-186">Můžete provést distribuci, těžiště, připojení nebo přístup založený na hustotě.</span><span class="sxs-lookup"><span data-stu-id="21d29-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="21d29-187">ML.NET v současné době podporuje přístup na základě těžiště pomocí K-Means clustering.</span><span class="sxs-lookup"><span data-stu-id="21d29-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="21d29-188">Příklady scénáře clusteringu:</span><span class="sxs-lookup"><span data-stu-id="21d29-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="21d29-189">Principy segmenty hotelu hostů na základě zvyklosti a charakteristiky hotelu voleb.</span><span class="sxs-lookup"><span data-stu-id="21d29-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="21d29-190">Identifikace segmenty uživatelů a demografických údajů, které vám pomůžou vytvářet cílené reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="21d29-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="21d29-191">Kategorizace podle výrobní metriky inventáře.</span><span class="sxs-lookup"><span data-stu-id="21d29-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="21d29-192">Clustering trainer</span><span class="sxs-lookup"><span data-stu-id="21d29-192">Clustering trainer</span></span>

<span data-ttu-id="21d29-193">Trénovat model clusteringu pomocí následující požadovaný algoritmus:</span><span class="sxs-lookup"><span data-stu-id="21d29-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="21d29-194">Clustering vstupy a výstupy</span><span class="sxs-lookup"><span data-stu-id="21d29-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="21d29-195">Funkce vstupní data musí být <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="21d29-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="21d29-196">Nejsou potřeba žádné popisky.</span><span class="sxs-lookup"><span data-stu-id="21d29-196">No labels are needed.</span></span>

<span data-ttu-id="21d29-197">Výstupem této trainer následující:</span><span class="sxs-lookup"><span data-stu-id="21d29-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="21d29-198">Název výstupního</span><span class="sxs-lookup"><span data-stu-id="21d29-198">Output Name</span></span> | <span data-ttu-id="21d29-199">Type</span><span class="sxs-lookup"><span data-stu-id="21d29-199">Type</span></span> | <span data-ttu-id="21d29-200">Popis</span><span class="sxs-lookup"><span data-stu-id="21d29-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="21d29-201">vektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="21d29-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="21d29-202">Přejděte na všech clusterech centriods vzdálenosti daná data</span><span class="sxs-lookup"><span data-stu-id="21d29-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="21d29-203">[klíč](xref:Microsoft.ML.Data.KeyDataViewType) typu</span><span class="sxs-lookup"><span data-stu-id="21d29-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="21d29-204">Index nejbližší clusteru předpovědět modelem.</span><span class="sxs-lookup"><span data-stu-id="21d29-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="21d29-205">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="21d29-205">Anomaly detection</span></span>

<span data-ttu-id="21d29-206">Tato úloha vytváří model detekce anomálií pomocí analýzy hlavní součásti (DPS).</span><span class="sxs-lookup"><span data-stu-id="21d29-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="21d29-207">Detekce anomálií založená na PCA umožňuje sestavit model ve scénářích, kde je snadné získat trénovací data z jedné třídy, jako jsou platné transakce, ale obtížné dostatečná ukázky cílové anomálie.</span><span class="sxs-lookup"><span data-stu-id="21d29-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="21d29-208">Zavedený postup ve službě machine learning, DPS se často používá na analýzu dat průzkumného testování, protože odhalí vnitřní strukturu dat a vysvětluje variance v datech.</span><span class="sxs-lookup"><span data-stu-id="21d29-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="21d29-209">DPS funguje díky analýze dat, která obsahuje více proměnných.</span><span class="sxs-lookup"><span data-stu-id="21d29-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="21d29-210">Hledá korelace mezi proměnné a určuje kombinace hodnot, které nejlépe zachycuje rozdíly ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="21d29-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="21d29-211">Tyto funkce kombinované hodnoty slouží k vytvoření kompaktnějším místo funkce nazývané jako hlavní komponenty.</span><span class="sxs-lookup"><span data-stu-id="21d29-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="21d29-212">Detekce anomálií zahrnuje mnoho důležitých úloh ve službě machine learning:</span><span class="sxs-lookup"><span data-stu-id="21d29-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="21d29-213">Identifikace transakcí, které jsou potenciálně podvodný.</span><span class="sxs-lookup"><span data-stu-id="21d29-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="21d29-214">Učení vzorce, které naznačují, že došlo k napadení sítě.</span><span class="sxs-lookup"><span data-stu-id="21d29-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="21d29-215">Hledání neobvyklé clustery pacientů.</span><span class="sxs-lookup"><span data-stu-id="21d29-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="21d29-216">Kontrola hodnoty zadané do systému.</span><span class="sxs-lookup"><span data-stu-id="21d29-216">Checking values entered into a system.</span></span>

<span data-ttu-id="21d29-217">Vzhledem k tomu anomálie výjimečné události podle definice, může být obtížné ke shromažďování dat pro modelování reprezentativní vzorek.</span><span class="sxs-lookup"><span data-stu-id="21d29-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="21d29-218">Algoritmy zahrnuté v této kategorii jsou obzvláště navržené pro řeší problémy základní stavební a trénování modelů s použitím imbalanced datových sad.</span><span class="sxs-lookup"><span data-stu-id="21d29-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="21d29-219">Trainer detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="21d29-219">Anomaly detection trainer</span></span>

<span data-ttu-id="21d29-220">Můžete trénování modelu detekce anomálií pomocí následující požadovaný algoritmus:</span><span class="sxs-lookup"><span data-stu-id="21d29-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="21d29-221">Vstupy detekce anomálií a výstupy</span><span class="sxs-lookup"><span data-stu-id="21d29-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="21d29-222">Vstupní funkce musí být vektor pevnou velikostí <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="21d29-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="21d29-223">Výstupem této trainer následující:</span><span class="sxs-lookup"><span data-stu-id="21d29-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="21d29-224">Název výstupního</span><span class="sxs-lookup"><span data-stu-id="21d29-224">Output Name</span></span> | <span data-ttu-id="21d29-225">Type</span><span class="sxs-lookup"><span data-stu-id="21d29-225">Type</span></span> | <span data-ttu-id="21d29-226">Popis</span><span class="sxs-lookup"><span data-stu-id="21d29-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="21d29-227">Záporná, unbounded skóre, které se počítá podle modelu detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="21d29-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="21d29-228">Hodnocení</span><span class="sxs-lookup"><span data-stu-id="21d29-228">Ranking</span></span>

<span data-ttu-id="21d29-229">Pořadí úkolů vytvoří klasifikátor ze sady s popiskem příklady.</span><span class="sxs-lookup"><span data-stu-id="21d29-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="21d29-230">Tato sada příklad se skládá ze skupiny instancí, které mohou být upraveny pomocí zadaných kritérií.</span><span class="sxs-lookup"><span data-stu-id="21d29-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="21d29-231">Hodnocení popisky jsou pro každou instanci {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="21d29-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="21d29-232">Klasifikátor je vyškolit tak, aby pořadí nové instance skupiny s Neznámý skóre, které se pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="21d29-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="21d29-233">Inteligentních algoritmů ML.NET hodnocení jsou [počítače se dozvěděli, hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) založené.</span><span class="sxs-lookup"><span data-stu-id="21d29-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="21d29-234">Hodnocení trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="21d29-234">Ranking training algorithms</span></span>

<span data-ttu-id="21d29-235">Můžete vyškolíme model pořadí pomocí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="21d29-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="21d29-236">Hodnocení vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="21d29-236">Ranking input and outputs</span></span>

<span data-ttu-id="21d29-237">Datový typ vstupní popisku musí být [klíč](xref:Microsoft.ML.Data.KeyDataViewType) typu nebo <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="21d29-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="21d29-238">Hodnota popisku určuje relevance, kde vyšší hodnoty znamenat vyšší podle relevance.</span><span class="sxs-lookup"><span data-stu-id="21d29-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="21d29-239">Pokud je popisek [klíč](xref:Microsoft.ML.Data.KeyDataViewType) zadejte index klíče je hodnota relevance, kde je nejmenší index nejméně relevantní.</span><span class="sxs-lookup"><span data-stu-id="21d29-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="21d29-240">Pokud je popisek <xref:System.Single>, vyšší hodnoty znamenat vyšší podle relevance.</span><span class="sxs-lookup"><span data-stu-id="21d29-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="21d29-241">Data funkce musí být vektor pevné velikosti <xref:System.Single> a vstupní řádek skupiny sloupec musí být [klíč](xref:Microsoft.ML.Data.KeyDataViewType) typu.</span><span class="sxs-lookup"><span data-stu-id="21d29-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="21d29-242">Výstupem této trainer následující:</span><span class="sxs-lookup"><span data-stu-id="21d29-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="21d29-243">Název výstupního</span><span class="sxs-lookup"><span data-stu-id="21d29-243">Output Name</span></span> | <span data-ttu-id="21d29-244">Type</span><span class="sxs-lookup"><span data-stu-id="21d29-244">Type</span></span> | <span data-ttu-id="21d29-245">Popis</span><span class="sxs-lookup"><span data-stu-id="21d29-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="21d29-246">Bez vazby skóre, které se počítá podle modelu k určení do predikce.</span><span class="sxs-lookup"><span data-stu-id="21d29-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="21d29-247">Doporučení</span><span class="sxs-lookup"><span data-stu-id="21d29-247">Recommendation</span></span>

<span data-ttu-id="21d29-248">Doporučení úloh umožňuje vytváření seznam doporučených produktů nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="21d29-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="21d29-249">Používá ML.NET [factorization matice (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrování založeného na spolupráci](https://en.wikipedia.org/wiki/Collaborative_filtering) algoritmus doporučení, když máte data hodnocení historických produktu ve vašem katalogu.</span><span class="sxs-lookup"><span data-stu-id="21d29-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="21d29-250">Například máte data o filmech historických hodnocení pro vaše uživatele a chcete doporučit další filmů, ve které je pravděpodobně podívejte se na další.</span><span class="sxs-lookup"><span data-stu-id="21d29-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="21d29-251">Doporučení trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="21d29-251">Recommendation training algorithms</span></span>

<span data-ttu-id="21d29-252">Můžete vyškolíme model doporučení pomocí následující požadovaný algoritmus:</span><span class="sxs-lookup"><span data-stu-id="21d29-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
