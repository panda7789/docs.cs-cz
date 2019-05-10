---
title: Jak používat ML.NET automatizované ML API
description: Automatizované ML API ML.NET automatizuje proces vytváření modelu a generuje modelu připravené na nasazení. Další možnosti, které můžete použít ke konfiguraci automatické strojového učení úlohy.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 23410a11f94ab6052ab64bd8968f0ed127441898
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066178"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Jak používat ML.NET automatizované machine learning API

Automatizované strojového učení (AutoML) automatizuje proces použití machine learningu data. Zadané datové sady, můžete spustit AutoML **experimentovat** k iteraci přes různé datové featurizations, machine learning algoritmy a vybrat nejlepší model hyperparameters.

> [!NOTE]
> Toto téma odkazuje na automatické machine learning API pro ML.NET, která je aktuálně ve verzi preview. Materiál může být mohou změnit.

## <a name="load-data"></a>Načtení dat

Automatizované strojového učení podporuje načítání datovou sadu do [IDataView](https://docs.microsoft.com/dotnet/api/microsoft.ml.idataview?view=ml-dotnet). Data můžou být ve formě souborů hodnoty oddělené tabulátorem (TSV) a soubory oddělených čárkami (CSV).

Příklad:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Vyberte strojového učení typ úlohy
Před vytvořením experiment, určete druh problém machine learning, který chcete vyřešit. Automatizované machine learning podporuje následující ML úlohy:
* Binární klasifikace
* Klasifikace víc tříd
* Regrese

## <a name="create-experiment-settings"></a>Vytvoření nastavení testu

Vytvořte nastavení testu pro typ úlohy určené ML:

* Binární klasifikace
```csharp
var experimentSettings = new BinaryExperimentSettings();
```
* Klasifikace víc tříd
```csharp
var experimentSettings = new MulticlassExperimentSettings();
```
* Regrese
```csharp
var experimentSettings = new RegressionExperimentSettings();
```

## <a name="configure-experiment-settings"></a>Konfigurace nastavení testu

Experimenty jsou vysoce konfigurovatelné. Zobrazit [dokumenty k rozhraní API AutoML](https://docs.microsoft.com/dotnet/api/microsoft.ml.auto?view=ml-dotnet) úplný seznam nastavení konfigurace.

Možné příklady:

1. Zadejte maximální dobu, po spuštění testu je povoleno.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Použijte token zrušení pro zrušení testu předtím, než je naplánováno na dokončení.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Zadejte jinou metriku optimalizace.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. `CacheDirectory` Nastavení je ukazatel na adresář uložení všech modelů trénovaných během AutoML úloh. Pokud `CacheDirectory` je nastavena na hodnotu null, modely zůstanou zachovaná v paměti, nikoli zapsané na disk.
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Dáte pokyn, aby automatizované ML nepoužívat určité školitelé.

    Výchozí seznam školitelé optimalizovat jsou probírány na jeden úkol. Tento seznam je upravit pro každého pokusu. Například školitelé, na kterých běží pomalu datové sady můžete odebrat ze seznamu. K optimalizaci na jedno volání konkrétní trainer `experimentSettings.Trainers.Clear()`, přidáte školitele, kterou chcete použít.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

Seznam podporovaných školitelé na jeden úkol ML najdete na příslušný odkaz níže:
* [Podporované algoritmy binární klasifikace](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationtrainer?view=automl-dotnet)
* [Podporované algoritmy klasifikace víc tříd](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationtrainer?view=automl-dotnet)
* [Regrese podporovaných algoritmů](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressiontrainer?view=automl-dotnet)

## <a name="optimizing-metric"></a>Optimalizace metrika

Optimalizace metriku, jak je znázorněno v příkladu výše, určuje metrika optimalizovat během cvičení modelu. Optimalizace metriky, které můžete vybrat se určuje podle typu úkolu, který zvolíte. Níže je seznam dostupných metrik.

|[Binární klasifikace](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet) | [Klasifikace víc tříd](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet) | [Regrese](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet)
|-- |-- |--
|Přesnost| LogLoss | RSquared
|AreaUnderPrecisionRecallCurve | LogLossReduction | MeanAbsoluteError
|AreaUnderRocCurve | MacroAccuracy | MeanSquaredError
|F1Score | MicroAccuracy | RootMeanSquaredError
|NegativePrecision | TopKAccuracy
|NegativeRecall |
|PositivePrecision
|PositiveRecall

## <a name="data-pre-processing-and-featurization"></a>Předběžné zpracování dat a snadné

Ve výchozím nastavení se stane předběžného zpracování dat a následující kroky se provádějí automaticky za vás:

1. Přetažení funkce s žádnou užitečnou informaci

    Vyřaďte ze sady pro trénování a ověření funkce s žádnou užitečnou informaci. Patří mezi funkce s všechny hodnoty, které chybí, stejnou hodnotu napříč všemi řádky nebo s velmi vysokou kardinalitu (například hodnoty hash ID nebo identifikátory GUID).

1. Chybějící hodnota označení a shodný podíl

    Vyplníte výchozí hodnota pro datový typ chybí hodnota buňky. Připojte ukazatel funkce se stejným číslem sloty jako vstupní sloupec. Hodnota v připojených ukazatele funkce je `1` Pokud chybí hodnota ve vstupním sloupci a `0` jinak.

1. Generovat další funkce
    
    Pro textové funkce: Kontejner objektů a dat z aplikace word funkcí s použitím unigrams a tri znak g.
    
    Pro funkce zařazené do kategorií: Jedna hot kódování pro funkce s nízkou Kardinalita a jeden horkou hash kódování funkcí zařazené do kategorií vysoká Kardinalita.

1. Transformace a kódování

    Funkce text s velmi malým počtem jedinečných hodnot transformována do kategorií funkce. V závislosti na mohutnosti zařazené do kategorií funkcí proveďte jednu hot kódování nebo horkou jedna hodnota hash kódování.

## <a name="exit-criteria"></a>Výstupní kritéria

Definujte kritéria pro dokončení úlohy:

1. Ukončit po dobu - pomocí `MaxExperimentTimeInSeconds` v nastaveních testu můžete definovat dobu v sekundách, které by měly být nadále úlohu spustit.

1. Ukončení na token zrušení – můžete použít token zrušení, který umožňuje zrušit úlohu předtím, než je naplánováno na dokončení.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Vytvoření experimentu

Po nakonfigurování nastavení testu, budete chtít vytvořit experiment.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Spusťte experiment.

Běží data aktivační události experiment předběžného zpracování, učení algoritmus pro výběr a hyperparametrů. AutoML budou i nadále generovat kombinace snadné, algoritmů učení a hyperparameters až `MaxExperimentTimeInSeconds` je dosaženo nebo experimentu je ukončen.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Prozkoumejte další přetížení pro `Execute()` Pokud budete chtít předávat data pro ověření, označuje sloupec účel nebo prefeaturizers informace o sloupci.

## <a name="training-modes"></a>Režimy školení

### <a name="training-dataset"></a>Trénovací datové sady

Poskytuje přetížený AutoML experiment spustit metodu, která umožňuje poskytovat trénovací data. Interně jsou automatizované ML rozdělí data train-validate rozdělení.

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a>Vlastní ověření datové sady

Použití vlastního ověřovacího datová sada Pokud náhodného dělení není přijatelná, jako je obvykle v případě dat časových řad. Můžete zadat vlastní ověření datové sady. Ověření datové sadě zadán místo jednoho nebo více náhodných datových sad se vyhodnotí modelu.

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a>Zkoumání metrik model

Po každé iteraci experimentu ML jsou uloženy metriky týkající se tohoto úkolu.

Například můžeme mají přístup k ověření metriky z nejlepší spuštění:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Tady jsou všechny dostupné metriky za ML úloh:
* [Binární klasifikace metriky](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet
)
* [Klasifikace víc tříd metriky](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet
)
* [Regrese metriky](https://docs.microsoft.com/en-us/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet
)

## <a name="see-also"></a>Viz také:

Úplné ukázky a další najdete [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) úložiště GitHub.
