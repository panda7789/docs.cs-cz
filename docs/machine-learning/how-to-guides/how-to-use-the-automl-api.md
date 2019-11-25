---
title: Jak používat automatizované rozhraní API pro ML.NET
description: Rozhraní ML.NET Automated ML API automatizuje proces vytváření modelů a vygeneruje model připravený pro nasazení. Seznamte se s možnostmi, které můžete použít ke konfiguraci automatizovaných úloh strojového učení.
ms.date: 11/7/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c1c18decc48bc1499aa55210becff305cdec4a53
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977121"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="c844a-104">Jak používat automatizované rozhraní API pro strojové učení ML.NET</span><span class="sxs-lookup"><span data-stu-id="c844a-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="c844a-105">Automatizované Machine Learning (AutoML) automatizuje proces použití strojového učení na data.</span><span class="sxs-lookup"><span data-stu-id="c844a-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="c844a-106">S ohledem na datovou sadu můžete spustit **experiment** AutoML a iterovat přes různé datové featurizations, algoritmy strojového učení a základní parametry a vybrat nejlepší model.</span><span class="sxs-lookup"><span data-stu-id="c844a-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="c844a-107">Toto téma odkazuje na automatizované rozhraní API služby Machine Learning pro ML.NET, které je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="c844a-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="c844a-108">Materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="c844a-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="c844a-109">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c844a-109">Load data</span></span>

<span data-ttu-id="c844a-110">Automatizované Machine Learning podporuje načtení datové sady do [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="c844a-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="c844a-111">Data mohou být ve formě souborů hodnot oddělených tabulátorem (TSV) a souborů s hodnotami oddělenými čárkou (CSV).</span><span class="sxs-lookup"><span data-stu-id="c844a-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="c844a-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c844a-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="c844a-113">Vyberte typ úlohy Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="c844a-113">Select the machine learning task type</span></span>

<span data-ttu-id="c844a-114">Než začnete vytvářet experiment, určete druh problému strojového učení, který chcete vyřešit.</span><span class="sxs-lookup"><span data-stu-id="c844a-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="c844a-115">Automatizované Machine Learning podporuje následující úlohy ML:</span><span class="sxs-lookup"><span data-stu-id="c844a-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="c844a-116">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="c844a-116">Binary Classification</span></span>
* <span data-ttu-id="c844a-117">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="c844a-117">Multiclass Classification</span></span>
* <span data-ttu-id="c844a-118">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="c844a-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="c844a-119">Vytvořit nastavení experimentu</span><span class="sxs-lookup"><span data-stu-id="c844a-119">Create experiment settings</span></span>

<span data-ttu-id="c844a-120">Vytvořit nastavení experimentu pro stanovený typ úkolu ML:</span><span class="sxs-lookup"><span data-stu-id="c844a-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="c844a-121">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="c844a-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="c844a-122">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="c844a-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="c844a-123">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="c844a-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="c844a-124">Konfigurovat nastavení experimentu</span><span class="sxs-lookup"><span data-stu-id="c844a-124">Configure experiment settings</span></span>

<span data-ttu-id="c844a-125">Experimenty jsou vysoce konfigurovatelné.</span><span class="sxs-lookup"><span data-stu-id="c844a-125">Experiments are highly configurable.</span></span> <span data-ttu-id="c844a-126">Úplný seznam nastavení konfigurace najdete v [dokumentaci k rozhraní AutoML API](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) .</span><span class="sxs-lookup"><span data-stu-id="c844a-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="c844a-127">Mezi příklady patří:</span><span class="sxs-lookup"><span data-stu-id="c844a-127">Some examples include:</span></span>

1. <span data-ttu-id="c844a-128">Zadejte maximální dobu, po kterou může experiment běžet.</span><span class="sxs-lookup"><span data-stu-id="c844a-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="c844a-129">Použijte token zrušení, chcete-li experiment zrušit před dokončením plánování.</span><span class="sxs-lookup"><span data-stu-id="c844a-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="c844a-130">Zadejte jinou optimalizaci metriky.</span><span class="sxs-lookup"><span data-stu-id="c844a-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="c844a-131">Nastavení `CacheDirectory` je ukazatel na adresář, do kterého se uloží všechny modely školené během AutoML úlohy.</span><span class="sxs-lookup"><span data-stu-id="c844a-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="c844a-132">Pokud je `CacheDirectory` nastavená na hodnotu null, budou se modely uchovávat v paměti místo zápisu na disk.</span><span class="sxs-lookup"><span data-stu-id="c844a-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="c844a-133">Požádejte o automatizovanou ML, aby nepoužívali určitou školitele.</span><span class="sxs-lookup"><span data-stu-id="c844a-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="c844a-134">Výchozí seznam školitelů, které se mají optimalizovat, se prozkoumá na úkol.</span><span class="sxs-lookup"><span data-stu-id="c844a-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="c844a-135">Tento seznam je možné upravit pro každý experiment.</span><span class="sxs-lookup"><span data-stu-id="c844a-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="c844a-136">Například školitele, které běží pomalu na vaší datové sadě, můžete ze seznamu odebrat.</span><span class="sxs-lookup"><span data-stu-id="c844a-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="c844a-137">Chcete-li provést optimalizaci na jednom konkrétním Trainer volání `experimentSettings.Trainers.Clear()`, přidejte Trainer, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c844a-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="c844a-138">Seznam podporovaných školitelů na úlohu ML najdete na odpovídajícím odkazu níže:</span><span class="sxs-lookup"><span data-stu-id="c844a-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="c844a-139">Podporované binární algoritmy klasifikace</span><span class="sxs-lookup"><span data-stu-id="c844a-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="c844a-140">Podporované algoritmy klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="c844a-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="c844a-141">Podporované algoritmy regrese</span><span class="sxs-lookup"><span data-stu-id="c844a-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="c844a-142">Optimalizace metriky</span><span class="sxs-lookup"><span data-stu-id="c844a-142">Optimizing metric</span></span>

<span data-ttu-id="c844a-143">Optimalizace metriky, jak je znázorněno v příkladu výše, Určuje metriku, která má být optimalizována během školení modelu.</span><span class="sxs-lookup"><span data-stu-id="c844a-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="c844a-144">Optimalizace metriky, kterou můžete vybrat, je určená typem úlohy, kterou zvolíte.</span><span class="sxs-lookup"><span data-stu-id="c844a-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="c844a-145">Níže je uveden seznam dostupných metrik.</span><span class="sxs-lookup"><span data-stu-id="c844a-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="c844a-146">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="c844a-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="c844a-147">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="c844a-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="c844a-148">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="c844a-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="c844a-149">Údajů</span><span class="sxs-lookup"><span data-stu-id="c844a-149">Accuracy</span></span>| <span data-ttu-id="c844a-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="c844a-150">LogLoss</span></span> | <span data-ttu-id="c844a-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="c844a-151">RSquared</span></span>
|<span data-ttu-id="c844a-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="c844a-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="c844a-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="c844a-153">LogLossReduction</span></span> | <span data-ttu-id="c844a-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="c844a-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="c844a-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="c844a-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="c844a-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="c844a-156">MacroAccuracy</span></span> | <span data-ttu-id="c844a-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="c844a-157">MeanSquaredError</span></span>
|<span data-ttu-id="c844a-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="c844a-158">F1Score</span></span> | <span data-ttu-id="c844a-159">Mikropřesnost</span><span class="sxs-lookup"><span data-stu-id="c844a-159">MicroAccuracy</span></span> | <span data-ttu-id="c844a-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="c844a-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="c844a-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="c844a-161">NegativePrecision</span></span> | <span data-ttu-id="c844a-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="c844a-162">TopKAccuracy</span></span>
|<span data-ttu-id="c844a-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="c844a-163">NegativeRecall</span></span> |
|<span data-ttu-id="c844a-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="c844a-164">PositivePrecision</span></span>
|<span data-ttu-id="c844a-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="c844a-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="c844a-166">Předběžné zpracování dat a featurization</span><span class="sxs-lookup"><span data-stu-id="c844a-166">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="c844a-167">Sloupec funkce podporuje pouze typy <xref:System.Boolean>, <xref:System.Single> a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c844a-167">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="c844a-168">Předběžné zpracování dat probíhá ve výchozím nastavení a k provedení následujících kroků dojde automaticky:</span><span class="sxs-lookup"><span data-stu-id="c844a-168">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="c844a-169">Vyřadit funkce bez užitečných informací</span><span class="sxs-lookup"><span data-stu-id="c844a-169">Drop features with no useful information</span></span>

    <span data-ttu-id="c844a-170">Vyřaďte funkce bez užitečných informací ze školicích a ověřovacích sad.</span><span class="sxs-lookup"><span data-stu-id="c844a-170">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="c844a-171">Mezi ně patří funkce se všemi chybějícími hodnotami, stejnou hodnotou ve všech řádcích nebo s velmi vysokou mohutnosti (například hodnoty hash, ID nebo identifikátory GUID).</span><span class="sxs-lookup"><span data-stu-id="c844a-171">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="c844a-172">Chybí indikace hodnoty a imputace.</span><span class="sxs-lookup"><span data-stu-id="c844a-172">Missing value indication and imputation</span></span>

    <span data-ttu-id="c844a-173">Vyplňte chybějící buňky s hodnotou výchozí hodnotou pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="c844a-173">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="c844a-174">Přidejte funkce indikátoru se stejným počtem slotů jako vstupní sloupec.</span><span class="sxs-lookup"><span data-stu-id="c844a-174">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="c844a-175">Hodnota ve funkcích s připojeným indikátorem je `1`, pokud hodnota ve sloupci Input chybí a `0` jinak.</span><span class="sxs-lookup"><span data-stu-id="c844a-175">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="c844a-176">Generování dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="c844a-176">Generate additional features</span></span>

    <span data-ttu-id="c844a-177">Pro funkce textu: funkce typu penalta v aplikaci Word s využitím unigrams a Tri-Character-gramů.</span><span class="sxs-lookup"><span data-stu-id="c844a-177">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="c844a-178">Pro funkce kategorií: jedno horké kódování pro funkce s nízkou mohutnost a kódování One-Hot-hash pro funkce High mohutnosti kategorií.</span><span class="sxs-lookup"><span data-stu-id="c844a-178">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="c844a-179">Transformace a kódování</span><span class="sxs-lookup"><span data-stu-id="c844a-179">Transformations and encodings</span></span>

    <span data-ttu-id="c844a-180">Funkce textu s velmi malým počtem jedinečných hodnot, které jsou transformovány do funkcí kategorií.</span><span class="sxs-lookup"><span data-stu-id="c844a-180">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="c844a-181">V závislosti na mohutnosti funkcí kategorií proveďte kódování s jedním horkou nebo kódováním hash s jedním horkou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="c844a-181">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="c844a-182">Výstupní kritéria</span><span class="sxs-lookup"><span data-stu-id="c844a-182">Exit criteria</span></span>

<span data-ttu-id="c844a-183">Zadejte kritéria pro dokončení úlohy:</span><span class="sxs-lookup"><span data-stu-id="c844a-183">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="c844a-184">Po uplynutí časového intervalu použijte `MaxExperimentTimeInSeconds` v nastavení experimentu můžete definovat dobu v sekundách, po kterou by úloha měla běžet.</span><span class="sxs-lookup"><span data-stu-id="c844a-184">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="c844a-185">Ukončit na tokenu zrušení – můžete použít token zrušení, který vám umožní zrušit úlohu před tím, než se naplánuje na dokončení.</span><span class="sxs-lookup"><span data-stu-id="c844a-185">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="c844a-186">Vytvoření experimentu</span><span class="sxs-lookup"><span data-stu-id="c844a-186">Create an experiment</span></span>

<span data-ttu-id="c844a-187">Jakmile nakonfigurujete nastavení experimentu, budete připraveni vytvořit experiment.</span><span class="sxs-lookup"><span data-stu-id="c844a-187">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="c844a-188">Spuštění experimentu</span><span class="sxs-lookup"><span data-stu-id="c844a-188">Run the experiment</span></span>

<span data-ttu-id="c844a-189">Spuštění experimentu aktivuje předběžné zpracování dat, výběr výukového algoritmu a ladění předaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="c844a-189">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="c844a-190">AutoML bude nadále generovat kombinace featurization, výukových algoritmů a parametrů, dokud není dosaženo `MaxExperimentTimeInSeconds` nebo je experiment ukončen.</span><span class="sxs-lookup"><span data-stu-id="c844a-190">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="c844a-191">Prozkoumejte další přetížení pro `Execute()`, pokud chcete předat ověřovací data, informace o sloupci, které označují účel sloupce nebo prefeaturizers.</span><span class="sxs-lookup"><span data-stu-id="c844a-191">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="c844a-192">Školicí režimy</span><span class="sxs-lookup"><span data-stu-id="c844a-192">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="c844a-193">Datová sada školení</span><span class="sxs-lookup"><span data-stu-id="c844a-193">Training dataset</span></span>

<span data-ttu-id="c844a-194">AutoML poskytuje přetíženou metodu spuštění experimentu, která umožňuje poskytovat školicí data.</span><span class="sxs-lookup"><span data-stu-id="c844a-194">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="c844a-195">Interně automatizované ML rozděluje data do přístrojově ověřovaného rozdělení.</span><span class="sxs-lookup"><span data-stu-id="c844a-195">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="c844a-196">Vlastní ověřovací datová sada</span><span class="sxs-lookup"><span data-stu-id="c844a-196">Custom validation dataset</span></span>

<span data-ttu-id="c844a-197">Použijte vlastní ověřovací datovou sadu, pokud není přijatelné náhodné rozdělení, což je obvykle případ s daty časových řad.</span><span class="sxs-lookup"><span data-stu-id="c844a-197">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="c844a-198">Můžete zadat vlastní ověřovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="c844a-198">You can specify your own validation dataset.</span></span> <span data-ttu-id="c844a-199">Model bude vyhodnocen proti zadané datové sadě ověřování místo jedné nebo více náhodných datových sad.</span><span class="sxs-lookup"><span data-stu-id="c844a-199">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="c844a-200">Prozkoumat metriky modelu</span><span class="sxs-lookup"><span data-stu-id="c844a-200">Explore model metrics</span></span>

<span data-ttu-id="c844a-201">Po každé iteraci experimentu ML se budou ukládat metriky související s touto úlohou.</span><span class="sxs-lookup"><span data-stu-id="c844a-201">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="c844a-202">Můžete například získat přístup k metrikám ověření z nejlepšího běhu:</span><span class="sxs-lookup"><span data-stu-id="c844a-202">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="c844a-203">Níže jsou uvedené všechny dostupné metriky na ML:</span><span class="sxs-lookup"><span data-stu-id="c844a-203">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="c844a-204">Binární metriky klasifikace</span><span class="sxs-lookup"><span data-stu-id="c844a-204">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="c844a-205">Metriky klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="c844a-205">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="c844a-206">Regresní metriky</span><span class="sxs-lookup"><span data-stu-id="c844a-206">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="c844a-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c844a-207">See also</span></span>

<span data-ttu-id="c844a-208">Úplné ukázky kódu a další informace najdete v úložišti GitHubu [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) .</span><span class="sxs-lookup"><span data-stu-id="c844a-208">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
