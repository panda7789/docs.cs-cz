---
title: Jak používat automatizované rozhraní API pro ML.NET
description: Rozhraní ML.NET Automated ML API automatizuje proces vytváření modelů a vygeneruje model připravený pro nasazení. Seznamte se s možnostmi, které můžete použít ke konfiguraci automatizovaných úloh strojového učení.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b322c484282d025033d747d2093f7b5b4d216fde
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636559"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="9626d-104">Jak používat automatizované rozhraní API pro strojové učení ML.NET</span><span class="sxs-lookup"><span data-stu-id="9626d-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="9626d-105">Automatizované Machine Learning (AutoML) automatizuje proces použití strojového učení na data.</span><span class="sxs-lookup"><span data-stu-id="9626d-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="9626d-106">S ohledem na datovou sadu můžete spustit **experiment** AutoML a iterovat přes různé datové featurizations, algoritmy strojového učení a základní parametry a vybrat nejlepší model.</span><span class="sxs-lookup"><span data-stu-id="9626d-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="9626d-107">Toto téma odkazuje na automatizované rozhraní API služby Machine Learning pro ML.NET, které je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="9626d-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="9626d-108">Materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="9626d-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="9626d-109">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="9626d-109">Load data</span></span>

<span data-ttu-id="9626d-110">Automatizované Machine Learning podporuje načtení datové sady do [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="9626d-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="9626d-111">Data mohou být ve formě souborů hodnot oddělených tabulátorem (TSV) a souborů s hodnotami oddělenými čárkou (CSV).</span><span class="sxs-lookup"><span data-stu-id="9626d-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="9626d-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9626d-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="9626d-113">Vyberte typ úlohy Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="9626d-113">Select the machine learning task type</span></span>

<span data-ttu-id="9626d-114">Než začnete vytvářet experiment, určete druh problému strojového učení, který chcete vyřešit.</span><span class="sxs-lookup"><span data-stu-id="9626d-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="9626d-115">Automatizované Machine Learning podporuje následující úlohy ML:</span><span class="sxs-lookup"><span data-stu-id="9626d-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="9626d-116">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="9626d-116">Binary Classification</span></span>
* <span data-ttu-id="9626d-117">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="9626d-117">Multiclass Classification</span></span>
* <span data-ttu-id="9626d-118">Regrese</span><span class="sxs-lookup"><span data-stu-id="9626d-118">Regression</span></span>
* <span data-ttu-id="9626d-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9626d-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="9626d-120">Vytvořit nastavení experimentu</span><span class="sxs-lookup"><span data-stu-id="9626d-120">Create experiment settings</span></span>

<span data-ttu-id="9626d-121">Vytvořit nastavení experimentu pro stanovený typ úkolu ML:</span><span class="sxs-lookup"><span data-stu-id="9626d-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="9626d-122">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="9626d-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="9626d-123">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="9626d-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="9626d-124">Regrese</span><span class="sxs-lookup"><span data-stu-id="9626d-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="9626d-125">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9626d-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="9626d-126">Konfigurovat nastavení experimentu</span><span class="sxs-lookup"><span data-stu-id="9626d-126">Configure experiment settings</span></span>

<span data-ttu-id="9626d-127">Experimenty jsou vysoce konfigurovatelné.</span><span class="sxs-lookup"><span data-stu-id="9626d-127">Experiments are highly configurable.</span></span> <span data-ttu-id="9626d-128">Úplný seznam nastavení konfigurace najdete v [dokumentaci k rozhraní AutoML API](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) .</span><span class="sxs-lookup"><span data-stu-id="9626d-128">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="9626d-129">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="9626d-129">Some examples include:</span></span>

1. <span data-ttu-id="9626d-130">Zadejte maximální dobu, po kterou může experiment běžet.</span><span class="sxs-lookup"><span data-stu-id="9626d-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="9626d-131">Použijte token zrušení, chcete-li experiment zrušit před dokončením plánování.</span><span class="sxs-lookup"><span data-stu-id="9626d-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="9626d-132">Zadejte jinou optimalizaci metriky.</span><span class="sxs-lookup"><span data-stu-id="9626d-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="9626d-133">Nastavení `CacheDirectory` je ukazatel na adresář, do kterého se uloží všechny modely školené během AutoML úlohy.</span><span class="sxs-lookup"><span data-stu-id="9626d-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="9626d-134">Pokud je `CacheDirectory` nastavená na hodnotu null, budou se modely uchovávat v paměti místo zápisu na disk.</span><span class="sxs-lookup"><span data-stu-id="9626d-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="9626d-135">Požádejte o automatizovanou ML, aby nepoužívali určitou školitele.</span><span class="sxs-lookup"><span data-stu-id="9626d-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="9626d-136">Výchozí seznam školitelů, které se mají optimalizovat, se prozkoumá na úkol.</span><span class="sxs-lookup"><span data-stu-id="9626d-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="9626d-137">Tento seznam je možné upravit pro každý experiment.</span><span class="sxs-lookup"><span data-stu-id="9626d-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="9626d-138">Například školitele, které běží pomalu na vaší datové sadě, můžete ze seznamu odebrat.</span><span class="sxs-lookup"><span data-stu-id="9626d-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="9626d-139">Chcete-li provést optimalizaci na jednom konkrétním Trainer volání `experimentSettings.Trainers.Clear()`, přidejte Trainer, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="9626d-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="9626d-140">Seznam podporovaných školitelů na úlohu ML najdete na odpovídajícím odkazu níže:</span><span class="sxs-lookup"><span data-stu-id="9626d-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="9626d-141">Podporované binární algoritmy klasifikace</span><span class="sxs-lookup"><span data-stu-id="9626d-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="9626d-142">Podporované algoritmy klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="9626d-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="9626d-143">Podporované algoritmy regrese</span><span class="sxs-lookup"><span data-stu-id="9626d-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="9626d-144">Podporované algoritmy doporučení</span><span class="sxs-lookup"><span data-stu-id="9626d-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="9626d-145">Optimalizace metriky</span><span class="sxs-lookup"><span data-stu-id="9626d-145">Optimizing metric</span></span>

<span data-ttu-id="9626d-146">Optimalizace metriky, jak je znázorněno v příkladu výše, Určuje metriku, která má být optimalizována během školení modelu.</span><span class="sxs-lookup"><span data-stu-id="9626d-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="9626d-147">Optimalizace metriky, kterou můžete vybrat, je určená typem úlohy, kterou zvolíte.</span><span class="sxs-lookup"><span data-stu-id="9626d-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="9626d-148">Níže je uveden seznam dostupných metrik.</span><span class="sxs-lookup"><span data-stu-id="9626d-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="9626d-149">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="9626d-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="9626d-150">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="9626d-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="9626d-151">Regrese & doporučení</span><span class="sxs-lookup"><span data-stu-id="9626d-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="9626d-152">Přesnost</span><span class="sxs-lookup"><span data-stu-id="9626d-152">Accuracy</span></span>| <span data-ttu-id="9626d-153">LogLoss</span><span class="sxs-lookup"><span data-stu-id="9626d-153">LogLoss</span></span> | <span data-ttu-id="9626d-154">RSquared</span><span class="sxs-lookup"><span data-stu-id="9626d-154">RSquared</span></span>
|<span data-ttu-id="9626d-155">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="9626d-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="9626d-156">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="9626d-156">LogLossReduction</span></span> | <span data-ttu-id="9626d-157">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="9626d-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="9626d-158">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="9626d-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="9626d-159">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="9626d-159">MacroAccuracy</span></span> | <span data-ttu-id="9626d-160">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="9626d-160">MeanSquaredError</span></span>
|<span data-ttu-id="9626d-161">F1Score</span><span class="sxs-lookup"><span data-stu-id="9626d-161">F1Score</span></span> | <span data-ttu-id="9626d-162">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="9626d-162">MicroAccuracy</span></span> | <span data-ttu-id="9626d-163">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="9626d-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="9626d-164">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="9626d-164">NegativePrecision</span></span> | <span data-ttu-id="9626d-165">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="9626d-165">TopKAccuracy</span></span>
|<span data-ttu-id="9626d-166">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="9626d-166">NegativeRecall</span></span> |
|<span data-ttu-id="9626d-167">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="9626d-167">PositivePrecision</span></span>
|<span data-ttu-id="9626d-168">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="9626d-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="9626d-169">Předběžné zpracování dat a snadné</span><span class="sxs-lookup"><span data-stu-id="9626d-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="9626d-170">Sloupec funkce podporuje pouze typy <xref:System.Boolean>, <xref:System.Single>a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="9626d-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="9626d-171">Předběžné zpracování dat probíhá ve výchozím nastavení a k provedení následujících kroků dojde automaticky:</span><span class="sxs-lookup"><span data-stu-id="9626d-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="9626d-172">Vyřadit funkce bez užitečných informací</span><span class="sxs-lookup"><span data-stu-id="9626d-172">Drop features with no useful information</span></span>

    <span data-ttu-id="9626d-173">Vyřaďte ze sady pro trénování a ověření funkce s žádnou užitečnou informaci.</span><span class="sxs-lookup"><span data-stu-id="9626d-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="9626d-174">Patří mezi funkce s všechny hodnoty, které chybí, stejnou hodnotu napříč všemi řádky nebo s velmi vysokou kardinalitu (například hodnoty hash ID nebo identifikátory GUID).</span><span class="sxs-lookup"><span data-stu-id="9626d-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="9626d-175">Chybí indikace hodnoty a imputace.</span><span class="sxs-lookup"><span data-stu-id="9626d-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="9626d-176">Vyplňte chybějící buňky s hodnotou výchozí hodnotou pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="9626d-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="9626d-177">Přidejte funkce indikátoru se stejným počtem slotů jako vstupní sloupec.</span><span class="sxs-lookup"><span data-stu-id="9626d-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="9626d-178">Hodnota ve funkcích s připojeným indikátorem je `1`, pokud hodnota ve sloupci Input chybí a `0` jinak.</span><span class="sxs-lookup"><span data-stu-id="9626d-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="9626d-179">Generovat další funkce</span><span class="sxs-lookup"><span data-stu-id="9626d-179">Generate additional features</span></span>

    <span data-ttu-id="9626d-180">Pro funkce textu: funkce typu penalta v aplikaci Word s využitím unigrams a Tri-Character-gramů.</span><span class="sxs-lookup"><span data-stu-id="9626d-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="9626d-181">Pro funkce kategorií: jedno horké kódování pro funkce s nízkou mohutnost a kódování One-Hot-hash pro funkce High mohutnosti kategorií.</span><span class="sxs-lookup"><span data-stu-id="9626d-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="9626d-182">Transformace a kódování</span><span class="sxs-lookup"><span data-stu-id="9626d-182">Transformations and encodings</span></span>

    <span data-ttu-id="9626d-183">Funkce textu s velmi malým počtem jedinečných hodnot, které jsou transformovány do funkcí kategorií.</span><span class="sxs-lookup"><span data-stu-id="9626d-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="9626d-184">V závislosti na mohutnosti funkcí kategorií proveďte kódování s jedním horkou nebo kódováním hash s jedním horkou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9626d-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="9626d-185">Výstupní kritéria</span><span class="sxs-lookup"><span data-stu-id="9626d-185">Exit criteria</span></span>

<span data-ttu-id="9626d-186">Zadejte kritéria pro dokončení úlohy:</span><span class="sxs-lookup"><span data-stu-id="9626d-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="9626d-187">Po uplynutí časového intervalu použijte `MaxExperimentTimeInSeconds` v nastavení experimentu můžete definovat dobu v sekundách, po kterou by úloha měla běžet.</span><span class="sxs-lookup"><span data-stu-id="9626d-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="9626d-188">Ukončit na tokenu zrušení – můžete použít token zrušení, který vám umožní zrušit úlohu před tím, než se naplánuje na dokončení.</span><span class="sxs-lookup"><span data-stu-id="9626d-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="9626d-189">Vytvoření experimentu</span><span class="sxs-lookup"><span data-stu-id="9626d-189">Create an experiment</span></span>

<span data-ttu-id="9626d-190">Jakmile nakonfigurujete nastavení experimentu, budete připraveni vytvořit experiment.</span><span class="sxs-lookup"><span data-stu-id="9626d-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="9626d-191">Spusťte experiment.</span><span class="sxs-lookup"><span data-stu-id="9626d-191">Run the experiment</span></span>

<span data-ttu-id="9626d-192">Spuštění experimentu aktivuje předběžné zpracování dat, výběr výukového algoritmu a ladění předaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="9626d-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="9626d-193">AutoML bude nadále generovat kombinace featurization, výukových algoritmů a parametrů, dokud není dosaženo `MaxExperimentTimeInSeconds` nebo je experiment ukončen.</span><span class="sxs-lookup"><span data-stu-id="9626d-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="9626d-194">Prozkoumejte další přetížení pro `Execute()`, pokud chcete předat ověřovací data, informace o sloupci, které označují účel sloupce nebo prefeaturizers.</span><span class="sxs-lookup"><span data-stu-id="9626d-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="9626d-195">Školicí režimy</span><span class="sxs-lookup"><span data-stu-id="9626d-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="9626d-196">Datová sada školení</span><span class="sxs-lookup"><span data-stu-id="9626d-196">Training dataset</span></span>

<span data-ttu-id="9626d-197">AutoML poskytuje přetíženou metodu spuštění experimentu, která umožňuje poskytovat školicí data.</span><span class="sxs-lookup"><span data-stu-id="9626d-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="9626d-198">Interně automatizované ML rozděluje data do přístrojově ověřovaného rozdělení.</span><span class="sxs-lookup"><span data-stu-id="9626d-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="9626d-199">Vlastní ověření datové sady</span><span class="sxs-lookup"><span data-stu-id="9626d-199">Custom validation dataset</span></span>

<span data-ttu-id="9626d-200">Použijte vlastní ověřovací datovou sadu, pokud není přijatelné náhodné rozdělení, což je obvykle případ s daty časových řad.</span><span class="sxs-lookup"><span data-stu-id="9626d-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="9626d-201">Můžete zadat vlastní ověření datové sady.</span><span class="sxs-lookup"><span data-stu-id="9626d-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="9626d-202">Model bude vyhodnocen proti zadané datové sadě ověřování místo jedné nebo více náhodných datových sad.</span><span class="sxs-lookup"><span data-stu-id="9626d-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="9626d-203">Zkoumání metrik model</span><span class="sxs-lookup"><span data-stu-id="9626d-203">Explore model metrics</span></span>

<span data-ttu-id="9626d-204">Po každé iteraci experimentu ML se budou ukládat metriky související s touto úlohou.</span><span class="sxs-lookup"><span data-stu-id="9626d-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="9626d-205">Můžete například získat přístup k metrikám ověření z nejlepšího běhu:</span><span class="sxs-lookup"><span data-stu-id="9626d-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="9626d-206">Níže jsou uvedené všechny dostupné metriky na ML:</span><span class="sxs-lookup"><span data-stu-id="9626d-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="9626d-207">Binární metriky klasifikace</span><span class="sxs-lookup"><span data-stu-id="9626d-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="9626d-208">Metriky klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="9626d-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="9626d-209">Regrese & metriky doporučení</span><span class="sxs-lookup"><span data-stu-id="9626d-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="9626d-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9626d-210">See also</span></span>

<span data-ttu-id="9626d-211">Úplné ukázky kódu a další informace najdete v úložišti GitHubu [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) .</span><span class="sxs-lookup"><span data-stu-id="9626d-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
