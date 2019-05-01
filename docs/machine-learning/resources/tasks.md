---
title: Úlohy strojového učení – ML.NET
description: Prozkoumejte různé strojového učení úkoly a přidružené úlohy, které jsou podporovány v ML.NET.
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019098"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="65089-103">Úlohy strojového učení v ML.NET</span><span class="sxs-lookup"><span data-stu-id="65089-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="65089-104">Při sestavování model strojového učení, musíte nejprve definovat jsou doufá dosáhnout s vašimi daty.</span><span class="sxs-lookup"><span data-stu-id="65089-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="65089-105">To umožňuje zvolit správný strojového učení úkol pro konkrétní situaci.</span><span class="sxs-lookup"><span data-stu-id="65089-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="65089-106">Následující seznam popisuje různé strojového učení úlohy, které můžete vybrat z a některé běžné případy použití.</span><span class="sxs-lookup"><span data-stu-id="65089-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="65089-107">Až si ověříte, které úloha se dá použít pro váš scénář, pak musíte zvolit nejlepší algoritmus k natrénování modelu.</span><span class="sxs-lookup"><span data-stu-id="65089-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="65089-108">K dispozici algoritmy jsou uvedené v části pro každý úkol.</span><span class="sxs-lookup"><span data-stu-id="65089-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="65089-109">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="65089-109">Binary classification</span></span>

<span data-ttu-id="65089-110">A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi, které instance dat patří do dvou tříd (kategorie).</span><span class="sxs-lookup"><span data-stu-id="65089-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="65089-111">Vstup klasifikační algoritmus je sada s popiskem příklady, kde každý popisek je celé číslo 0 nebo 1.</span><span class="sxs-lookup"><span data-stu-id="65089-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="65089-112">Výstupní binární klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku.</span><span class="sxs-lookup"><span data-stu-id="65089-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="65089-113">Příklady scénářů binární klasifikace:</span><span class="sxs-lookup"><span data-stu-id="65089-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="65089-114">[Principy mínění Twitteru, komentářů](../tutorials/sentiment-analysis.md) jako "kladné" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="65089-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="65089-115">Diagnostika zda pacienta má určitá stádiu, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="65089-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="65089-116">Rozhodování k označení e-mailu jako "nevyžádanou poštu" nebo ne.</span><span class="sxs-lookup"><span data-stu-id="65089-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="65089-117">Určení, zda obsahuje fotografii dog nebo výsledku.</span><span class="sxs-lookup"><span data-stu-id="65089-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="65089-118">Další informace najdete v tématu [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) článku na wikipedii.</span><span class="sxs-lookup"><span data-stu-id="65089-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-training-algorithms"></a><span data-ttu-id="65089-119">Binární klasifikace trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="65089-119">Binary Classification Training Algorithms</span></span>

<span data-ttu-id="65089-120">Trénovat binární klasifikační model pomocí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="65089-120">You can train a binary classification model using the following algorithms:</span></span>

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

## <a name="multiclass-classification"></a><span data-ttu-id="65089-121">Klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="65089-121">Multiclass classification</span></span>

<span data-ttu-id="65089-122">A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi třídu instance data (kategorie).</span><span class="sxs-lookup"><span data-stu-id="65089-122">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="65089-123">Vstup klasifikační algoritmus je sada s popiskem příklady.</span><span class="sxs-lookup"><span data-stu-id="65089-123">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="65089-124">Každý popisek normálně spustí jako text.</span><span class="sxs-lookup"><span data-stu-id="65089-124">Each label normally starts as text.</span></span> <span data-ttu-id="65089-125">Následně se spustí prostřednictvím TermTransform, který převádí na typ klíče (číselné).</span><span class="sxs-lookup"><span data-stu-id="65089-125">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="65089-126">Výstup klasifikační algoritmus je klasifikátor, který můžete použít k predikci třídy nové instance bez popisku.</span><span class="sxs-lookup"><span data-stu-id="65089-126">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="65089-127">Příklady scénářů roc klasifikace:</span><span class="sxs-lookup"><span data-stu-id="65089-127">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="65089-128">Určení emulátorem pes jako "Siberian Husky", "Golden načítací", "Co", atd.</span><span class="sxs-lookup"><span data-stu-id="65089-128">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="65089-129">Principy film revize jako "kladné", "neutrální" nebo "záporné".</span><span class="sxs-lookup"><span data-stu-id="65089-129">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="65089-130">Kategorizace hotelu revize jako "umístění", "price", "čistota" atd.</span><span class="sxs-lookup"><span data-stu-id="65089-130">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="65089-131">Další informace najdete v tématu [klasifikace víc tříd](https://en.wikipedia.org/wiki/Multiclass_classification) článku na wikipedii.</span><span class="sxs-lookup"><span data-stu-id="65089-131">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="65089-132">Jeden vs všechny upgraduje všechny [binární klasifikace learner](#binary-classification) k práci s více třídami datové sady.</span><span class="sxs-lookup"><span data-stu-id="65089-132">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="65089-133">Další informace o [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="65089-133">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-training-algorithms"></a><span data-ttu-id="65089-134">Víc tříd klasifikace trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="65089-134">Multiclass Classification training algorithms</span></span>

<span data-ttu-id="65089-135">Trénovat klasifikace víc tříd modelu pomocí následujících trénování algoritmů:</span><span class="sxs-lookup"><span data-stu-id="65089-135">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a><span data-ttu-id="65089-136">Regrese</span><span class="sxs-lookup"><span data-stu-id="65089-136">Regression</span></span>

<span data-ttu-id="65089-137">A [pod dohledem strojového učení](glossary.md#supervised-machine-learning) úlohu, která se používá k předpovědi hodnota popisku na základě sady souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="65089-137">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="65089-138">Popisek může být libovolné skutečné hodnoty a je neumožňují omezenou sadu hodnot jako úlohy klasifikace.</span><span class="sxs-lookup"><span data-stu-id="65089-138">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="65089-139">Regresní model algoritmy závislost popisek na jeho související funkce, chcete-li zjistit, jak se změní popisek jako hodnoty funkcí se lišily.</span><span class="sxs-lookup"><span data-stu-id="65089-139">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="65089-140">Vstup regresního algoritmu je sada příklady s popisky známé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65089-140">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="65089-141">Výstup tohoto regresního algoritmu je funkce, které můžete použít k predikci hodnoty popisku pro všechny nové sady vstupní funkce.</span><span class="sxs-lookup"><span data-stu-id="65089-141">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="65089-142">Příklady scénářů regrese:</span><span class="sxs-lookup"><span data-stu-id="65089-142">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="65089-143">Odhad ceny Domů na základě atributů house například počtu ložnic, umístění a velikosti.</span><span class="sxs-lookup"><span data-stu-id="65089-143">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="65089-144">Předpovídání budoucích cenami akcií na základě historických dat a aktuální trendy na trhu.</span><span class="sxs-lookup"><span data-stu-id="65089-144">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="65089-145">Předpověď prodeje podle inzerování rozpočty produktu.</span><span class="sxs-lookup"><span data-stu-id="65089-145">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-training-algorithms"></a><span data-ttu-id="65089-146">Regrese trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="65089-146">Regression training algorithms</span></span>

<span data-ttu-id="65089-147">Trénovat regresního modelu pomocí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="65089-147">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a><span data-ttu-id="65089-148">Vytváření clusterů</span><span class="sxs-lookup"><span data-stu-id="65089-148">Clustering</span></span>

<span data-ttu-id="65089-149">[Nastavenou možnost bez dohledu strojového učení](glossary.md#unsupervised-machine-learning) úlohu, která se používá k skupiny instancí data do clusterů obsahující podobné charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="65089-149">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="65089-150">Clustering lze také identifikovat relací v datové sadě, která nemusí být odvozena logicky sledováním procházení nebo jednoduché.</span><span class="sxs-lookup"><span data-stu-id="65089-150">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="65089-151">Vstupy a výstupy algoritmu clusteringu závisí na zvolené metodě.</span><span class="sxs-lookup"><span data-stu-id="65089-151">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="65089-152">Můžete provést distribuci, těžiště, připojení nebo přístup založený na hustotě.</span><span class="sxs-lookup"><span data-stu-id="65089-152">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="65089-153">ML.NET v současné době podporuje přístup na základě těžiště pomocí K-Means clustering.</span><span class="sxs-lookup"><span data-stu-id="65089-153">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="65089-154">Příklady scénáře clusteringu:</span><span class="sxs-lookup"><span data-stu-id="65089-154">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="65089-155">Principy segmenty hotelu hostů na základě zvyklosti a charakteristiky hotelu voleb.</span><span class="sxs-lookup"><span data-stu-id="65089-155">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="65089-156">Identifikace segmenty uživatelů a demografických údajů, které vám pomůžou vytvářet cílené reklamní kampaně.</span><span class="sxs-lookup"><span data-stu-id="65089-156">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="65089-157">Kategorizace podle výrobní metriky inventáře.</span><span class="sxs-lookup"><span data-stu-id="65089-157">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-training-algorithms"></a><span data-ttu-id="65089-158">Clustering trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="65089-158">Clustering training algorithms</span></span>

<span data-ttu-id="65089-159">Trénovat model clusteringu pomocí následující požadovaný algoritmus:</span><span class="sxs-lookup"><span data-stu-id="65089-159">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a><span data-ttu-id="65089-160">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="65089-160">Anomaly detection</span></span>

<span data-ttu-id="65089-161">Tato úloha vytváří model detekce anomálií pomocí analýzy hlavní součásti (DPS).</span><span class="sxs-lookup"><span data-stu-id="65089-161">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="65089-162">Detekce anomálií založená na PCA umožňuje sestavit model ve scénářích, kde je snadné získat trénovací data z jedné třídy, jako jsou platné transakce, ale obtížné dostatečná ukázky cílové anomálie.</span><span class="sxs-lookup"><span data-stu-id="65089-162">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="65089-163">Zavedený postup ve službě machine learning, DPS se často používá na analýzu dat průzkumného testování, protože odhalí vnitřní strukturu dat a vysvětluje variance v datech.</span><span class="sxs-lookup"><span data-stu-id="65089-163">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="65089-164">DPS funguje díky analýze dat, která obsahuje více proměnných.</span><span class="sxs-lookup"><span data-stu-id="65089-164">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="65089-165">Hledá korelace mezi proměnné a určuje kombinace hodnot, které nejlépe zachycuje rozdíly ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="65089-165">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="65089-166">Tyto funkce kombinované hodnoty slouží k vytvoření kompaktnějším místo funkce nazývané jako hlavní komponenty.</span><span class="sxs-lookup"><span data-stu-id="65089-166">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="65089-167">Detekce anomálií zahrnuje mnoho důležitých úloh ve službě machine learning:</span><span class="sxs-lookup"><span data-stu-id="65089-167">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="65089-168">Identifikace transakcí, které jsou potenciálně podvodný.</span><span class="sxs-lookup"><span data-stu-id="65089-168">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="65089-169">Učení vzorce, které naznačují, že došlo k napadení sítě.</span><span class="sxs-lookup"><span data-stu-id="65089-169">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="65089-170">Hledání neobvyklé clustery pacientů.</span><span class="sxs-lookup"><span data-stu-id="65089-170">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="65089-171">Kontrola hodnoty zadané do systému.</span><span class="sxs-lookup"><span data-stu-id="65089-171">Checking values entered into a system.</span></span>

<span data-ttu-id="65089-172">Vzhledem k tomu anomálie výjimečné události podle definice, může být obtížné ke shromažďování dat pro modelování reprezentativní vzorek.</span><span class="sxs-lookup"><span data-stu-id="65089-172">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="65089-173">Algoritmy zahrnuté v této kategorii jsou obzvláště navržené pro řeší problémy základní stavební a trénování modelů s použitím imbalanced datových sad.</span><span class="sxs-lookup"><span data-stu-id="65089-173">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-training-algorithms"></a><span data-ttu-id="65089-174">Algoritmy školení detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="65089-174">Anomaly detection training algorithms</span></span>

<span data-ttu-id="65089-175">Můžete trénování modelu detekce anomálií pomocí následující požadovaný algoritmus:</span><span class="sxs-lookup"><span data-stu-id="65089-175">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a><span data-ttu-id="65089-176">Hodnocení</span><span class="sxs-lookup"><span data-stu-id="65089-176">Ranking</span></span>

<span data-ttu-id="65089-177">Pořadí úkolů vytvoří klasifikátor ze sady s popiskem příklady.</span><span class="sxs-lookup"><span data-stu-id="65089-177">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="65089-178">Tato sada příklad se skládá ze skupiny instancí, které mohou být upraveny pomocí zadaných kritérií.</span><span class="sxs-lookup"><span data-stu-id="65089-178">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="65089-179">Hodnocení popisky jsou pro každou instanci {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="65089-179">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="65089-180">Klasifikátor je vyškolit tak, aby pořadí nové instance skupiny s Neznámý skóre, které se pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="65089-180">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="65089-181">Inteligentních algoritmů ML.NET hodnocení jsou [počítače se dozvěděli, hodnocení](https://en.wikipedia.org/wiki/Learning_to_rank) založené.</span><span class="sxs-lookup"><span data-stu-id="65089-181">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="65089-182">Hodnocení trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="65089-182">Ranking training algorithms</span></span>

<span data-ttu-id="65089-183">Můžete vyškolíme model pořadí pomocí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="65089-183">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a><span data-ttu-id="65089-184">Doporučení</span><span class="sxs-lookup"><span data-stu-id="65089-184">Recommendation</span></span>

<span data-ttu-id="65089-185">Doporučení úloh umožňuje vytváření seznam doporučených produktů nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="65089-185">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="65089-186">Používá ML.NET [factorization matice (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrování založeného na spolupráci](https://en.wikipedia.org/wiki/Collaborative_filtering) algoritmus doporučení, když máte data hodnocení historických produktu ve vašem katalogu.</span><span class="sxs-lookup"><span data-stu-id="65089-186">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="65089-187">Například máte data o filmech historických hodnocení pro vaše uživatele a chcete doporučit další filmů, ve které je pravděpodobně podívejte se na další.</span><span class="sxs-lookup"><span data-stu-id="65089-187">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="65089-188">Doporučení trénování algoritmů</span><span class="sxs-lookup"><span data-stu-id="65089-188">Recommendation training algorithms</span></span>

<span data-ttu-id="65089-189">Můžete vyškolíme model doporučení pomocí následující požadovaný algoritmus:</span><span class="sxs-lookup"><span data-stu-id="65089-189">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
