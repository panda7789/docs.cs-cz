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
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Jak používat automatizované rozhraní API pro strojové učení ML.NET

Automatizované Machine Learning (AutoML) automatizuje proces použití strojového učení na data. S ohledem na datovou sadu můžete spustit **experiment** AutoML a iterovat přes různé datové featurizations, algoritmy strojového učení a základní parametry a vybrat nejlepší model.

> [!NOTE]
> Toto téma odkazuje na automatizované rozhraní API služby Machine Learning pro ML.NET, které je momentálně ve verzi Preview. Materiál může být změněn.

## <a name="load-data"></a>Načtení dat

Automatizované Machine Learning podporuje načtení datové sady do [IDataView](xref:Microsoft.ML.IDataView). Data mohou být ve formě souborů hodnot oddělených tabulátorem (TSV) a souborů s hodnotami oddělenými čárkou (CSV).

Příklad:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Vyberte typ úlohy Machine Learning.

Než začnete vytvářet experiment, určete druh problému strojového učení, který chcete vyřešit. Automatizované Machine Learning podporuje následující úlohy ML:

* Binární klasifikace
* Klasifikace s více třídami
* Regrese
* Doporučení

## <a name="create-experiment-settings"></a>Vytvořit nastavení experimentu

Vytvořit nastavení experimentu pro stanovený typ úkolu ML:

* Binární klasifikace

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Klasifikace s více třídami

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* Regrese

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* Doporučení

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a>Konfigurovat nastavení experimentu

Experimenty jsou vysoce konfigurovatelné. Úplný seznam nastavení konfigurace najdete v [dokumentaci k rozhraní AutoML API](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) .

Možné příklady:

1. Zadejte maximální dobu, po kterou může experiment běžet.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Použijte token zrušení, chcete-li experiment zrušit před dokončením plánování.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Zadejte jinou optimalizaci metriky.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. Nastavení `CacheDirectory` je ukazatel na adresář, do kterého se uloží všechny modely školené během AutoML úlohy. Pokud je `CacheDirectory` nastavená na hodnotu null, budou se modely uchovávat v paměti místo zápisu na disk.

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Požádejte o automatizovanou ML, aby nepoužívali určitou školitele.

    Výchozí seznam školitelů, které se mají optimalizovat, se prozkoumá na úkol. Tento seznam je možné upravit pro každý experiment. Například školitele, které běží pomalu na vaší datové sadě, můžete ze seznamu odebrat. Chcete-li provést optimalizaci na jednom konkrétním Trainer volání `experimentSettings.Trainers.Clear()`, přidejte Trainer, který chcete použít.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

Seznam podporovaných školitelů na úlohu ML najdete na odpovídajícím odkazu níže:

* [Podporované binární algoritmy klasifikace](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Podporované algoritmy klasifikace s více třídami](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Podporované algoritmy regrese](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [Podporované algoritmy doporučení](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a>Optimalizace metriky

Optimalizace metriky, jak je znázorněno v příkladu výše, Určuje metriku, která má být optimalizována během školení modelu. Optimalizace metriky, kterou můžete vybrat, je určená typem úlohy, kterou zvolíte. Níže je uveden seznam dostupných metrik.

|[Binární klasifikace](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Klasifikace s více třídami](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Regrese & doporučení](xref:Microsoft.ML.AutoML.RegressionMetric)
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

> [!NOTE]
> Sloupec funkce podporuje pouze typy <xref:System.Boolean>, <xref:System.Single>a <xref:System.String>.

Předběžné zpracování dat probíhá ve výchozím nastavení a k provedení následujících kroků dojde automaticky:

1. Vyřadit funkce bez užitečných informací

    Vyřaďte ze sady pro trénování a ověření funkce s žádnou užitečnou informaci. Patří mezi funkce s všechny hodnoty, které chybí, stejnou hodnotu napříč všemi řádky nebo s velmi vysokou kardinalitu (například hodnoty hash ID nebo identifikátory GUID).

1. Chybí indikace hodnoty a imputace.

    Vyplňte chybějící buňky s hodnotou výchozí hodnotou pro datový typ. Přidejte funkce indikátoru se stejným počtem slotů jako vstupní sloupec. Hodnota ve funkcích s připojeným indikátorem je `1`, pokud hodnota ve sloupci Input chybí a `0` jinak.

1. Generovat další funkce

    Pro funkce textu: funkce typu penalta v aplikaci Word s využitím unigrams a Tri-Character-gramů.

    Pro funkce kategorií: jedno horké kódování pro funkce s nízkou mohutnost a kódování One-Hot-hash pro funkce High mohutnosti kategorií.

1. Transformace a kódování

    Funkce textu s velmi malým počtem jedinečných hodnot, které jsou transformovány do funkcí kategorií. V závislosti na mohutnosti funkcí kategorií proveďte kódování s jedním horkou nebo kódováním hash s jedním horkou hodnotou.

## <a name="exit-criteria"></a>Výstupní kritéria

Zadejte kritéria pro dokončení úlohy:

1. Po uplynutí časového intervalu použijte `MaxExperimentTimeInSeconds` v nastavení experimentu můžete definovat dobu v sekundách, po kterou by úloha měla běžet.

1. Ukončit na tokenu zrušení – můžete použít token zrušení, který vám umožní zrušit úlohu před tím, než se naplánuje na dokončení.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Vytvoření experimentu

Jakmile nakonfigurujete nastavení experimentu, budete připraveni vytvořit experiment.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Spusťte experiment.

Spuštění experimentu aktivuje předběžné zpracování dat, výběr výukového algoritmu a ladění předaných parametrů. AutoML bude nadále generovat kombinace featurization, výukových algoritmů a parametrů, dokud není dosaženo `MaxExperimentTimeInSeconds` nebo je experiment ukončen.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Prozkoumejte další přetížení pro `Execute()`, pokud chcete předat ověřovací data, informace o sloupci, které označují účel sloupce nebo prefeaturizers.

## <a name="training-modes"></a>Školicí režimy

### <a name="training-dataset"></a>Datová sada školení

AutoML poskytuje přetíženou metodu spuštění experimentu, která umožňuje poskytovat školicí data. Interně automatizované ML rozděluje data do přístrojově ověřovaného rozdělení.

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a>Vlastní ověření datové sady

Použijte vlastní ověřovací datovou sadu, pokud není přijatelné náhodné rozdělení, což je obvykle případ s daty časových řad. Můžete zadat vlastní ověření datové sady. Model bude vyhodnocen proti zadané datové sadě ověřování místo jedné nebo více náhodných datových sad.

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a>Zkoumání metrik model

Po každé iteraci experimentu ML se budou ukládat metriky související s touto úlohou.

Můžete například získat přístup k metrikám ověření z nejlepšího běhu:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Níže jsou uvedené všechny dostupné metriky na ML:

* [Binární metriky klasifikace](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Metriky klasifikace s více třídami](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Regrese & metriky doporučení](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Viz také:

Úplné ukázky kódu a další informace najdete v úložišti GitHubu [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) .
