---
title: Jak používat ML.NET automatizované rozhraní ML API
description: Automatizované rozhraní ML API ML.NET automatizuje proces vytváření modelu a generuje model připravený k nasazení. Seznamte se s možnostmi, které můžete použít ke konfiguraci úloh automatizovaného strojového učení.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b322c484282d025033d747d2093f7b5b4d216fde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75636559"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="1c932-104">Jak používat rozhraní API pro automatické strojové učení ML.NET</span><span class="sxs-lookup"><span data-stu-id="1c932-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="1c932-105">Automatizované strojové učení (AutoML) automatizuje proces aplikace strojového učení na data.</span><span class="sxs-lookup"><span data-stu-id="1c932-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="1c932-106">Vzhledem k tomu, datové sady, můžete spustit **experiment** AutoML iterovat přes různé výkony dat, algoritmy strojového učení a hyperparametry vybrat nejlepší model.</span><span class="sxs-lookup"><span data-stu-id="1c932-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="1c932-107">Toto téma odkazuje na automatizované rozhraní API pro strojové učení pro ML.NET, které je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="1c932-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="1c932-108">Materiál se může změnit.</span><span class="sxs-lookup"><span data-stu-id="1c932-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="1c932-109">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="1c932-109">Load data</span></span>

<span data-ttu-id="1c932-110">Automatizované strojové učení podporuje načítání datové sady do [iDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="1c932-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="1c932-111">Data mohou být ve formě souborů s hodnotou oddělených tabulátory (TSV) a souborů csv oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="1c932-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="1c932-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1c932-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="1c932-113">Výběr typu úlohy strojového učení</span><span class="sxs-lookup"><span data-stu-id="1c932-113">Select the machine learning task type</span></span>

<span data-ttu-id="1c932-114">Před vytvořením experimentu určete druh problému strojového učení, který chcete vyřešit.</span><span class="sxs-lookup"><span data-stu-id="1c932-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="1c932-115">Automatizované strojové učení podporuje následující úlohy ml:</span><span class="sxs-lookup"><span data-stu-id="1c932-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="1c932-116">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="1c932-116">Binary Classification</span></span>
* <span data-ttu-id="1c932-117">Klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="1c932-117">Multiclass Classification</span></span>
* <span data-ttu-id="1c932-118">Regrese</span><span class="sxs-lookup"><span data-stu-id="1c932-118">Regression</span></span>
* <span data-ttu-id="1c932-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="1c932-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="1c932-120">Vytvoření nastavení experimentu</span><span class="sxs-lookup"><span data-stu-id="1c932-120">Create experiment settings</span></span>

<span data-ttu-id="1c932-121">Vytvořte nastavení experimentu pro určený typ úlohy ML:</span><span class="sxs-lookup"><span data-stu-id="1c932-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="1c932-122">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="1c932-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="1c932-123">Klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="1c932-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="1c932-124">Regrese</span><span class="sxs-lookup"><span data-stu-id="1c932-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="1c932-125">Doporučení</span><span class="sxs-lookup"><span data-stu-id="1c932-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="1c932-126">Konfigurace nastavení experimentu</span><span class="sxs-lookup"><span data-stu-id="1c932-126">Configure experiment settings</span></span>

<span data-ttu-id="1c932-127">Experimenty jsou vysoce konfigurovatelné.</span><span class="sxs-lookup"><span data-stu-id="1c932-127">Experiments are highly configurable.</span></span> <span data-ttu-id="1c932-128">Úplný seznam nastavení konfigurace najdete v [dokumentech rozhraní API automatického mlsní.](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview)</span><span class="sxs-lookup"><span data-stu-id="1c932-128">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="1c932-129">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="1c932-129">Some examples include:</span></span>

1. <span data-ttu-id="1c932-130">Zadejte maximální dobu, po kterou může experiment spustit.</span><span class="sxs-lookup"><span data-stu-id="1c932-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="1c932-131">Pomocí tokenu zrušení zrušit experiment před jeho dokončením.</span><span class="sxs-lookup"><span data-stu-id="1c932-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="1c932-132">Zadejte jinou metriku optimalizace.</span><span class="sxs-lookup"><span data-stu-id="1c932-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="1c932-133">Toto `CacheDirectory` nastavení je ukazatelem na adresář, kde budou uloženy všechny modely trénované během úlohy Automatické mlm.</span><span class="sxs-lookup"><span data-stu-id="1c932-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="1c932-134">Pokud `CacheDirectory` je nastavena na hodnotu null, modely budou uchovávány v paměti namísto zapsány na disk.</span><span class="sxs-lookup"><span data-stu-id="1c932-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="1c932-135">Dejte automatickému ML pokyn, aby nepoužíval určité trenažér.</span><span class="sxs-lookup"><span data-stu-id="1c932-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="1c932-136">Výchozí seznam školitelů pro optimalizaci jsou prozkoumány na úkol.</span><span class="sxs-lookup"><span data-stu-id="1c932-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="1c932-137">Tento seznam lze upravit pro každý experiment.</span><span class="sxs-lookup"><span data-stu-id="1c932-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="1c932-138">Například školitelů, které běží pomalu na datové sadě lze odebrat ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="1c932-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="1c932-139">Chcete-li optimalizovat na `experimentSettings.Trainers.Clear()`jeden konkrétní trenér volání , pak přidejte trenér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1c932-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="1c932-140">Seznam podporovaných školitelů na úlohu ML naleznete na příslušném odkazu níže:</span><span class="sxs-lookup"><span data-stu-id="1c932-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="1c932-141">Podporované binární klasifikační algoritmy</span><span class="sxs-lookup"><span data-stu-id="1c932-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="1c932-142">Podporované klasifikační algoritmy více tříd</span><span class="sxs-lookup"><span data-stu-id="1c932-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="1c932-143">Podporované regresní algoritmy</span><span class="sxs-lookup"><span data-stu-id="1c932-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="1c932-144">Podporované algoritmy doporučení</span><span class="sxs-lookup"><span data-stu-id="1c932-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="1c932-145">Optimalizace metriky</span><span class="sxs-lookup"><span data-stu-id="1c932-145">Optimizing metric</span></span>

<span data-ttu-id="1c932-146">Metrika optimalizace, jak je znázorněno ve výše uvedeném příkladu, určuje metriku, která má být optimalizována během tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="1c932-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="1c932-147">Metrika optimalizace, kterou můžete vybrat, je určena vybraným typem úkolu.</span><span class="sxs-lookup"><span data-stu-id="1c932-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="1c932-148">Níže je uveden seznam dostupných metrik.</span><span class="sxs-lookup"><span data-stu-id="1c932-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="1c932-149">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="1c932-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="1c932-150">Klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="1c932-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="1c932-151">Doporučení pro regresi &</span><span class="sxs-lookup"><span data-stu-id="1c932-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="1c932-152">Přesnost</span><span class="sxs-lookup"><span data-stu-id="1c932-152">Accuracy</span></span>| <span data-ttu-id="1c932-153">Ztráta protokolu</span><span class="sxs-lookup"><span data-stu-id="1c932-153">LogLoss</span></span> | <span data-ttu-id="1c932-154">RSquared</span><span class="sxs-lookup"><span data-stu-id="1c932-154">RSquared</span></span>
|<span data-ttu-id="1c932-155">Area UnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="1c932-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="1c932-156">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="1c932-156">LogLossReduction</span></span> | <span data-ttu-id="1c932-157">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="1c932-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="1c932-158">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="1c932-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="1c932-159">Přesnost maker</span><span class="sxs-lookup"><span data-stu-id="1c932-159">MacroAccuracy</span></span> | <span data-ttu-id="1c932-160">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="1c932-160">MeanSquaredError</span></span>
|<span data-ttu-id="1c932-161">F1Skóre</span><span class="sxs-lookup"><span data-stu-id="1c932-161">F1Score</span></span> | <span data-ttu-id="1c932-162">Mikropřesnost</span><span class="sxs-lookup"><span data-stu-id="1c932-162">MicroAccuracy</span></span> | <span data-ttu-id="1c932-163">Chyba RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="1c932-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="1c932-164">NegativníPřesnost</span><span class="sxs-lookup"><span data-stu-id="1c932-164">NegativePrecision</span></span> | <span data-ttu-id="1c932-165">TopKPřesnost</span><span class="sxs-lookup"><span data-stu-id="1c932-165">TopKAccuracy</span></span>
|<span data-ttu-id="1c932-166">NegativníRecall</span><span class="sxs-lookup"><span data-stu-id="1c932-166">NegativeRecall</span></span> |
|<span data-ttu-id="1c932-167">PozitivníPřesnost</span><span class="sxs-lookup"><span data-stu-id="1c932-167">PositivePrecision</span></span>
|<span data-ttu-id="1c932-168">PozitivníOdvolání</span><span class="sxs-lookup"><span data-stu-id="1c932-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="1c932-169">Předběžné zpracování a featurizace dat</span><span class="sxs-lookup"><span data-stu-id="1c932-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="1c932-170">Sloupec funkce podporuje pouze <xref:System.Boolean> <xref:System.Single>typy <xref:System.String>, a .</span><span class="sxs-lookup"><span data-stu-id="1c932-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="1c932-171">Předběžné zpracování dat probíhá ve výchozím nastavení a automaticky se provádějí následující kroky:</span><span class="sxs-lookup"><span data-stu-id="1c932-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="1c932-172">Drop funkce bez užitečných informací</span><span class="sxs-lookup"><span data-stu-id="1c932-172">Drop features with no useful information</span></span>

    <span data-ttu-id="1c932-173">Drop funkce bez užitečných informací z školení a sady ověření.</span><span class="sxs-lookup"><span data-stu-id="1c932-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="1c932-174">Patří mezi ně funkce se všemi chybějícími hodnotami, stejnou hodnotou ve všech řádcích nebo s extrémně vysokou mohutností (např. hodnoty hash, ID nebo GUID).</span><span class="sxs-lookup"><span data-stu-id="1c932-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="1c932-175">Chybějící označení hodnoty a imputace</span><span class="sxs-lookup"><span data-stu-id="1c932-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="1c932-176">Vyplňte chybějící buňky hodnot výchozí hodnotou pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="1c932-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="1c932-177">Připojit indikátor funkce se stejným počtem slotů jako vstupní sloupec.</span><span class="sxs-lookup"><span data-stu-id="1c932-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="1c932-178">Hodnota v připojených funkcích `1` indikátoru je, pokud hodnota `0` ve vstupním sloupci chybí a jinak.</span><span class="sxs-lookup"><span data-stu-id="1c932-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="1c932-179">Generovat další funkce</span><span class="sxs-lookup"><span data-stu-id="1c932-179">Generate additional features</span></span>

    <span data-ttu-id="1c932-180">Pro textové funkce: Funkce sáčku s použitím unigramů a tříznakových gramů.</span><span class="sxs-lookup"><span data-stu-id="1c932-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="1c932-181">Pro kategorické funkce: Jednohorké kódování pro funkce nízké mohutnosti a kódování hash jedním hotem pro kategorické funkce s vysokou mohutností.</span><span class="sxs-lookup"><span data-stu-id="1c932-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="1c932-182">Transformace a kódování</span><span class="sxs-lookup"><span data-stu-id="1c932-182">Transformations and encodings</span></span>

    <span data-ttu-id="1c932-183">Textové prvky s velmi málo jedinečnými hodnotami, které jsou transformovány do kategorických prvků.</span><span class="sxs-lookup"><span data-stu-id="1c932-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="1c932-184">V závislosti na mohutnosti kategorických funkcí proveďte kódování jedním horkým nebo jedním horkým kódováním hash.</span><span class="sxs-lookup"><span data-stu-id="1c932-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="1c932-185">Kritéria ukončení</span><span class="sxs-lookup"><span data-stu-id="1c932-185">Exit criteria</span></span>

<span data-ttu-id="1c932-186">Definujte kritéria pro dokončení úkolu:</span><span class="sxs-lookup"><span data-stu-id="1c932-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="1c932-187">Ukončit po delší době `MaxExperimentTimeInSeconds` – Pomocí nastavení experimentu můžete definovat, jak dlouho v sekundách, že úloha by měla pokračovat v běhu.</span><span class="sxs-lookup"><span data-stu-id="1c932-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="1c932-188">Ukončit na token zrušení - Můžete použít token zrušení, který vám umožní zrušit úkol před jeho dokončením.</span><span class="sxs-lookup"><span data-stu-id="1c932-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="1c932-189">Vytvoření experimentu</span><span class="sxs-lookup"><span data-stu-id="1c932-189">Create an experiment</span></span>

<span data-ttu-id="1c932-190">Po konfiguraci nastavení experimentu jste připraveni experiment vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1c932-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="1c932-191">Spusťte experiment.</span><span class="sxs-lookup"><span data-stu-id="1c932-191">Run the experiment</span></span>

<span data-ttu-id="1c932-192">Spuštění experimentu aktivuje předběžné zpracování dat, výběr algoritmu učení a hyperparametrické ladění.</span><span class="sxs-lookup"><span data-stu-id="1c932-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="1c932-193">AutoML bude nadále generovat kombinace featurization, učení algoritmy a `MaxExperimentTimeInSeconds` hyperparameters, dokud je dosaženo nebo experiment je ukončen.</span><span class="sxs-lookup"><span data-stu-id="1c932-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="1c932-194">Prozkoumejte další `Execute()` přetížení, pokud chcete předat ověřovací data, informace o sloupci označující účel sloupce nebo prefeaturizers.</span><span class="sxs-lookup"><span data-stu-id="1c932-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="1c932-195">Tréninkové režimy</span><span class="sxs-lookup"><span data-stu-id="1c932-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="1c932-196">Trénovací datová sada</span><span class="sxs-lookup"><span data-stu-id="1c932-196">Training dataset</span></span>

<span data-ttu-id="1c932-197">AutoML poskytuje přetížený experiment spustit metodu, která umožňuje poskytnout trénovací data.</span><span class="sxs-lookup"><span data-stu-id="1c932-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="1c932-198">Internally, automated ML rozděluje data do rozdělení ověření vlaku.</span><span class="sxs-lookup"><span data-stu-id="1c932-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="1c932-199">Vlastní datová sada ověření</span><span class="sxs-lookup"><span data-stu-id="1c932-199">Custom validation dataset</span></span>

<span data-ttu-id="1c932-200">Vlastní ověřovací datovou sadu použijte, pokud náhodné rozdělení není přijatelné, jako je tomu obvykle u dat časových řad.</span><span class="sxs-lookup"><span data-stu-id="1c932-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="1c932-201">Můžete zadat vlastní datovou sadu ověření.</span><span class="sxs-lookup"><span data-stu-id="1c932-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="1c932-202">Model bude vyhodnocen podle ověřovací datové sady zadané namísto jedné nebo více náhodných datových sad.</span><span class="sxs-lookup"><span data-stu-id="1c932-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="1c932-203">Prozkoumejte metriky modelu</span><span class="sxs-lookup"><span data-stu-id="1c932-203">Explore model metrics</span></span>

<span data-ttu-id="1c932-204">Po každé iteraci experimentu ML jsou uloženy metriky vztahující se k této úloze.</span><span class="sxs-lookup"><span data-stu-id="1c932-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="1c932-205">Například můžeme získat přístup k metrikám ověření z nejlepšího spuštění:</span><span class="sxs-lookup"><span data-stu-id="1c932-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="1c932-206">Následují všechny dostupné metriky na úlohu ML:</span><span class="sxs-lookup"><span data-stu-id="1c932-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="1c932-207">Binární klasifikace metriky</span><span class="sxs-lookup"><span data-stu-id="1c932-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="1c932-208">Metriky klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="1c932-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="1c932-209">Metriky doporučení regresní &</span><span class="sxs-lookup"><span data-stu-id="1c932-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="1c932-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c932-210">See also</span></span>

<span data-ttu-id="1c932-211">Úplné ukázky kódu a další najdete [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub úložiště.</span><span class="sxs-lookup"><span data-stu-id="1c932-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
