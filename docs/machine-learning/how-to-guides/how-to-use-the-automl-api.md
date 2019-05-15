---
title: Jak používat ML.NET automatizované ML API
description: Automatizované ML API ML.NET automatizuje proces vytváření modelu a generuje modelu připravené na nasazení. Další možnosti, které můžete použít ke konfiguraci automatické strojového učení úlohy.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b05b6ed7c66062b28aaf634913a9598602b62498
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557875"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="eb566-104">Jak používat ML.NET automatizované machine learning API</span><span class="sxs-lookup"><span data-stu-id="eb566-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="eb566-105">Automatizované strojového učení (AutoML) automatizuje proces použití machine learningu data.</span><span class="sxs-lookup"><span data-stu-id="eb566-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="eb566-106">Zadané datové sady, můžete spustit AutoML **experimentovat** k iteraci přes různé datové featurizations, machine learning algoritmy a vybrat nejlepší model hyperparameters.</span><span class="sxs-lookup"><span data-stu-id="eb566-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="eb566-107">Toto téma odkazuje na automatické machine learning API pro ML.NET, která je aktuálně ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="eb566-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="eb566-108">Materiál může být mohou změnit.</span><span class="sxs-lookup"><span data-stu-id="eb566-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="eb566-109">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="eb566-109">Load data</span></span>

<span data-ttu-id="eb566-110">Automatizované strojového učení podporuje načítání datovou sadu do [IDataView](https://docs.microsoft.com/dotnet/api/microsoft.ml.idataview?view=ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="eb566-110">Automated machine learning supports loading a dataset into an [IDataView](https://docs.microsoft.com/dotnet/api/microsoft.ml.idataview?view=ml-dotnet).</span></span> <span data-ttu-id="eb566-111">Data můžou být ve formě souborů hodnoty oddělené tabulátorem (TSV) a soubory oddělených čárkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="eb566-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="eb566-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="eb566-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="eb566-113">Vyberte strojového učení typ úlohy</span><span class="sxs-lookup"><span data-stu-id="eb566-113">Select the machine learning task type</span></span>
<span data-ttu-id="eb566-114">Před vytvořením experiment, určete druh problém machine learning, který chcete vyřešit.</span><span class="sxs-lookup"><span data-stu-id="eb566-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="eb566-115">Automatizované machine learning podporuje následující ML úlohy:</span><span class="sxs-lookup"><span data-stu-id="eb566-115">Automated machine learning supports the following ML tasks:</span></span>
* <span data-ttu-id="eb566-116">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="eb566-116">Binary Classification</span></span>
* <span data-ttu-id="eb566-117">Klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="eb566-117">Multiclass Classification</span></span>
* <span data-ttu-id="eb566-118">Regrese</span><span class="sxs-lookup"><span data-stu-id="eb566-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="eb566-119">Vytvoření nastavení testu</span><span class="sxs-lookup"><span data-stu-id="eb566-119">Create experiment settings</span></span>

<span data-ttu-id="eb566-120">Vytvořte nastavení testu pro typ úlohy určené ML:</span><span class="sxs-lookup"><span data-stu-id="eb566-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="eb566-121">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="eb566-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="eb566-122">Klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="eb566-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="eb566-123">Regrese</span><span class="sxs-lookup"><span data-stu-id="eb566-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="eb566-124">Konfigurace nastavení testu</span><span class="sxs-lookup"><span data-stu-id="eb566-124">Configure experiment settings</span></span>

<span data-ttu-id="eb566-125">Experimenty jsou vysoce konfigurovatelné.</span><span class="sxs-lookup"><span data-stu-id="eb566-125">Experiments are highly configurable.</span></span> <span data-ttu-id="eb566-126">Zobrazit [dokumenty k rozhraní API AutoML](https://docs.microsoft.com/dotnet/api/microsoft.ml.auto?view=ml-dotnet) úplný seznam nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="eb566-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.auto?view=ml-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="eb566-127">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="eb566-127">Some examples include:</span></span>

1. <span data-ttu-id="eb566-128">Zadejte maximální dobu, po spuštění testu je povoleno.</span><span class="sxs-lookup"><span data-stu-id="eb566-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="eb566-129">Použijte token zrušení pro zrušení testu předtím, než je naplánováno na dokončení.</span><span class="sxs-lookup"><span data-stu-id="eb566-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="eb566-130">Zadejte jinou metriku optimalizace.</span><span class="sxs-lookup"><span data-stu-id="eb566-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="eb566-131">`CacheDirectory` Nastavení je ukazatel na adresář uložení všech modelů trénovaných během AutoML úloh.</span><span class="sxs-lookup"><span data-stu-id="eb566-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="eb566-132">Pokud `CacheDirectory` je nastavena na hodnotu null, modely zůstanou zachovaná v paměti, nikoli zapsané na disk.</span><span class="sxs-lookup"><span data-stu-id="eb566-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="eb566-133">Dáte pokyn, aby automatizované ML nepoužívat určité školitelé.</span><span class="sxs-lookup"><span data-stu-id="eb566-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="eb566-134">Výchozí seznam školitelé optimalizovat jsou probírány na jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="eb566-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="eb566-135">Tento seznam je upravit pro každého pokusu.</span><span class="sxs-lookup"><span data-stu-id="eb566-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="eb566-136">Například školitelé, na kterých běží pomalu datové sady můžete odebrat ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="eb566-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="eb566-137">K optimalizaci na jedno volání konkrétní trainer `experimentSettings.Trainers.Clear()`, přidáte školitele, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="eb566-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="eb566-138">Seznam podporovaných školitelé na jeden úkol ML najdete na příslušný odkaz níže:</span><span class="sxs-lookup"><span data-stu-id="eb566-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>
* [<span data-ttu-id="eb566-139">Podporované algoritmy binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="eb566-139">Supported Binary Classification Algorithms</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationtrainer?view=automl-dotnet)
* [<span data-ttu-id="eb566-140">Podporované algoritmy klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="eb566-140">Supported Multiclass Classification Algorithms</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationtrainer?view=automl-dotnet)
* [<span data-ttu-id="eb566-141">Regrese podporovaných algoritmů</span><span class="sxs-lookup"><span data-stu-id="eb566-141">Supported Regression Algorithms</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressiontrainer?view=automl-dotnet)

## <a name="optimizing-metric"></a><span data-ttu-id="eb566-142">Optimalizace metrika</span><span class="sxs-lookup"><span data-stu-id="eb566-142">Optimizing metric</span></span>

<span data-ttu-id="eb566-143">Optimalizace metriku, jak je znázorněno v příkladu výše, určuje metrika optimalizovat během cvičení modelu.</span><span class="sxs-lookup"><span data-stu-id="eb566-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="eb566-144">Optimalizace metriky, které můžete vybrat se určuje podle typu úkolu, který zvolíte.</span><span class="sxs-lookup"><span data-stu-id="eb566-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="eb566-145">Níže je seznam dostupných metrik.</span><span class="sxs-lookup"><span data-stu-id="eb566-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="eb566-146">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="eb566-146">Binary Classification</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet) | [<span data-ttu-id="eb566-147">Klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="eb566-147">Multiclass Classification</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet) | [<span data-ttu-id="eb566-148">Regrese</span><span class="sxs-lookup"><span data-stu-id="eb566-148">Regression</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet)
|-- |-- |--
|<span data-ttu-id="eb566-149">Přesnost</span><span class="sxs-lookup"><span data-stu-id="eb566-149">Accuracy</span></span>| <span data-ttu-id="eb566-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="eb566-150">LogLoss</span></span> | <span data-ttu-id="eb566-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="eb566-151">RSquared</span></span>
|<span data-ttu-id="eb566-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="eb566-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="eb566-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="eb566-153">LogLossReduction</span></span> | <span data-ttu-id="eb566-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="eb566-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="eb566-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="eb566-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="eb566-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="eb566-156">MacroAccuracy</span></span> | <span data-ttu-id="eb566-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="eb566-157">MeanSquaredError</span></span>
|<span data-ttu-id="eb566-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="eb566-158">F1Score</span></span> | <span data-ttu-id="eb566-159">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="eb566-159">MicroAccuracy</span></span> | <span data-ttu-id="eb566-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="eb566-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="eb566-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="eb566-161">NegativePrecision</span></span> | <span data-ttu-id="eb566-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="eb566-162">TopKAccuracy</span></span>
|<span data-ttu-id="eb566-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="eb566-163">NegativeRecall</span></span> |
|<span data-ttu-id="eb566-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="eb566-164">PositivePrecision</span></span>
|<span data-ttu-id="eb566-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="eb566-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="eb566-166">Předběžné zpracování dat a snadné</span><span class="sxs-lookup"><span data-stu-id="eb566-166">Data pre-processing and featurization</span></span>

<span data-ttu-id="eb566-167">Ve výchozím nastavení se stane předběžného zpracování dat a následující kroky se provádějí automaticky za vás:</span><span class="sxs-lookup"><span data-stu-id="eb566-167">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="eb566-168">Přetažení funkce s žádnou užitečnou informaci</span><span class="sxs-lookup"><span data-stu-id="eb566-168">Drop features with no useful information</span></span>

    <span data-ttu-id="eb566-169">Vyřaďte ze sady pro trénování a ověření funkce s žádnou užitečnou informaci.</span><span class="sxs-lookup"><span data-stu-id="eb566-169">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="eb566-170">Patří mezi funkce s všechny hodnoty, které chybí, stejnou hodnotu napříč všemi řádky nebo s velmi vysokou kardinalitu (například hodnoty hash ID nebo identifikátory GUID).</span><span class="sxs-lookup"><span data-stu-id="eb566-170">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="eb566-171">Chybějící hodnota označení a shodný podíl</span><span class="sxs-lookup"><span data-stu-id="eb566-171">Missing value indication and imputation</span></span>

    <span data-ttu-id="eb566-172">Vyplníte výchozí hodnota pro datový typ chybí hodnota buňky.</span><span class="sxs-lookup"><span data-stu-id="eb566-172">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="eb566-173">Připojte ukazatel funkce se stejným číslem sloty jako vstupní sloupec.</span><span class="sxs-lookup"><span data-stu-id="eb566-173">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="eb566-174">Hodnota v připojených ukazatele funkce je `1` Pokud chybí hodnota ve vstupním sloupci a `0` jinak.</span><span class="sxs-lookup"><span data-stu-id="eb566-174">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="eb566-175">Generovat další funkce</span><span class="sxs-lookup"><span data-stu-id="eb566-175">Generate additional features</span></span>
    
    <span data-ttu-id="eb566-176">Pro textové funkce: Kontejner objektů a dat z aplikace word funkcí s použitím unigrams a tri znak g.</span><span class="sxs-lookup"><span data-stu-id="eb566-176">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="eb566-177">Pro funkce zařazené do kategorií: Jedna hot kódování pro funkce s nízkou Kardinalita a jeden horkou hash kódování funkcí zařazené do kategorií vysoká Kardinalita.</span><span class="sxs-lookup"><span data-stu-id="eb566-177">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="eb566-178">Transformace a kódování</span><span class="sxs-lookup"><span data-stu-id="eb566-178">Transformations and encodings</span></span>

    <span data-ttu-id="eb566-179">Funkce text s velmi malým počtem jedinečných hodnot transformována do kategorií funkce.</span><span class="sxs-lookup"><span data-stu-id="eb566-179">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="eb566-180">V závislosti na mohutnosti zařazené do kategorií funkcí proveďte jednu hot kódování nebo horkou jedna hodnota hash kódování.</span><span class="sxs-lookup"><span data-stu-id="eb566-180">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="eb566-181">Výstupní kritéria</span><span class="sxs-lookup"><span data-stu-id="eb566-181">Exit criteria</span></span>

<span data-ttu-id="eb566-182">Definujte kritéria pro dokončení úlohy:</span><span class="sxs-lookup"><span data-stu-id="eb566-182">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="eb566-183">Ukončit po dobu - pomocí `MaxExperimentTimeInSeconds` v nastaveních testu můžete definovat dobu v sekundách, které by měly být nadále úlohu spustit.</span><span class="sxs-lookup"><span data-stu-id="eb566-183">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="eb566-184">Ukončení na token zrušení – můžete použít token zrušení, který umožňuje zrušit úlohu předtím, než je naplánováno na dokončení.</span><span class="sxs-lookup"><span data-stu-id="eb566-184">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="eb566-185">Vytvoření experimentu</span><span class="sxs-lookup"><span data-stu-id="eb566-185">Create an experiment</span></span>

<span data-ttu-id="eb566-186">Po nakonfigurování nastavení testu, budete chtít vytvořit experiment.</span><span class="sxs-lookup"><span data-stu-id="eb566-186">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="eb566-187">Spusťte experiment.</span><span class="sxs-lookup"><span data-stu-id="eb566-187">Run the experiment</span></span>

<span data-ttu-id="eb566-188">Běží data aktivační události experiment předběžného zpracování, učení algoritmus pro výběr a hyperparametrů.</span><span class="sxs-lookup"><span data-stu-id="eb566-188">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="eb566-189">AutoML budou i nadále generovat kombinace snadné, algoritmů učení a hyperparameters až `MaxExperimentTimeInSeconds` je dosaženo nebo experimentu je ukončen.</span><span class="sxs-lookup"><span data-stu-id="eb566-189">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="eb566-190">Prozkoumejte další přetížení pro `Execute()` Pokud budete chtít předávat data pro ověření, označuje sloupec účel nebo prefeaturizers informace o sloupci.</span><span class="sxs-lookup"><span data-stu-id="eb566-190">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="eb566-191">Režimy školení</span><span class="sxs-lookup"><span data-stu-id="eb566-191">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="eb566-192">Trénovací datové sady</span><span class="sxs-lookup"><span data-stu-id="eb566-192">Training dataset</span></span>

<span data-ttu-id="eb566-193">Poskytuje přetížený AutoML experiment spustit metodu, která umožňuje poskytovat trénovací data.</span><span class="sxs-lookup"><span data-stu-id="eb566-193">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="eb566-194">Interně jsou automatizované ML rozdělí data train-validate rozdělení.</span><span class="sxs-lookup"><span data-stu-id="eb566-194">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="eb566-195">Vlastní ověření datové sady</span><span class="sxs-lookup"><span data-stu-id="eb566-195">Custom validation dataset</span></span>

<span data-ttu-id="eb566-196">Použití vlastního ověřovacího datová sada Pokud náhodného dělení není přijatelná, jako je obvykle v případě dat časových řad.</span><span class="sxs-lookup"><span data-stu-id="eb566-196">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="eb566-197">Můžete zadat vlastní ověření datové sady.</span><span class="sxs-lookup"><span data-stu-id="eb566-197">You can specify your own validation dataset.</span></span> <span data-ttu-id="eb566-198">Ověření datové sadě zadán místo jednoho nebo více náhodných datových sad se vyhodnotí modelu.</span><span class="sxs-lookup"><span data-stu-id="eb566-198">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="eb566-199">Zkoumání metrik model</span><span class="sxs-lookup"><span data-stu-id="eb566-199">Explore model metrics</span></span>

<span data-ttu-id="eb566-200">Po každé iteraci experimentu ML jsou uloženy metriky týkající se tohoto úkolu.</span><span class="sxs-lookup"><span data-stu-id="eb566-200">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="eb566-201">Například můžeme mají přístup k ověření metriky z nejlepší spuštění:</span><span class="sxs-lookup"><span data-stu-id="eb566-201">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="eb566-202">Tady jsou všechny dostupné metriky za ML úloh:</span><span class="sxs-lookup"><span data-stu-id="eb566-202">The following are all the available metrics per ML task:</span></span>
* [<span data-ttu-id="eb566-203">Binární klasifikace metriky</span><span class="sxs-lookup"><span data-stu-id="eb566-203">Binary classification metrics</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet
)
* [<span data-ttu-id="eb566-204">Klasifikace víc tříd metriky</span><span class="sxs-lookup"><span data-stu-id="eb566-204">Multiclass classification metrics</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet
)
* [<span data-ttu-id="eb566-205">Regrese metriky</span><span class="sxs-lookup"><span data-stu-id="eb566-205">Regression metrics</span></span>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet
)

## <a name="see-also"></a><span data-ttu-id="eb566-206">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb566-206">See also</span></span>

<span data-ttu-id="eb566-207">Úplné ukázky a další najdete [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="eb566-207">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
