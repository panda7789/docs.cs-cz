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
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Jak používat rozhraní API pro automatické strojové učení ML.NET

Automatizované strojové učení (AutoML) automatizuje proces aplikace strojového učení na data. Vzhledem k tomu, datové sady, můžete spustit **experiment** AutoML iterovat přes různé výkony dat, algoritmy strojového učení a hyperparametry vybrat nejlepší model.

> [!NOTE]
> Toto téma odkazuje na automatizované rozhraní API pro strojové učení pro ML.NET, které je aktuálně ve verzi Preview. Materiál se může změnit.

## <a name="load-data"></a>Načtení dat

Automatizované strojové učení podporuje načítání datové sady do [iDataView](xref:Microsoft.ML.IDataView). Data mohou být ve formě souborů s hodnotou oddělených tabulátory (TSV) a souborů csv oddělených čárkami.

Příklad:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Výběr typu úlohy strojového učení

Před vytvořením experimentu určete druh problému strojového učení, který chcete vyřešit. Automatizované strojové učení podporuje následující úlohy ml:

* Binární klasifikace
* Klasifikace více tříd
* Regrese
* Doporučení

## <a name="create-experiment-settings"></a>Vytvoření nastavení experimentu

Vytvořte nastavení experimentu pro určený typ úlohy ML:

* Binární klasifikace

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Klasifikace více tříd

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

## <a name="configure-experiment-settings"></a>Konfigurace nastavení experimentu

Experimenty jsou vysoce konfigurovatelné. Úplný seznam nastavení konfigurace najdete v [dokumentech rozhraní API automatického mlsní.](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview)

Možné příklady:

1. Zadejte maximální dobu, po kterou může experiment spustit.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Pomocí tokenu zrušení zrušit experiment před jeho dokončením.

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

1. Toto `CacheDirectory` nastavení je ukazatelem na adresář, kde budou uloženy všechny modely trénované během úlohy Automatické mlm. Pokud `CacheDirectory` je nastavena na hodnotu null, modely budou uchovávány v paměti namísto zapsány na disk.

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Dejte automatickému ML pokyn, aby nepoužíval určité trenažér.

    Výchozí seznam školitelů pro optimalizaci jsou prozkoumány na úkol. Tento seznam lze upravit pro každý experiment. Například školitelů, které běží pomalu na datové sadě lze odebrat ze seznamu. Chcete-li optimalizovat na `experimentSettings.Trainers.Clear()`jeden konkrétní trenér volání , pak přidejte trenér, který chcete použít.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

Seznam podporovaných školitelů na úlohu ML naleznete na příslušném odkazu níže:

* [Podporované binární klasifikační algoritmy](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Podporované klasifikační algoritmy více tříd](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Podporované regresní algoritmy](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [Podporované algoritmy doporučení](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a>Optimalizace metriky

Metrika optimalizace, jak je znázorněno ve výše uvedeném příkladu, určuje metriku, která má být optimalizována během tréninku modelu. Metrika optimalizace, kterou můžete vybrat, je určena vybraným typem úkolu. Níže je uveden seznam dostupných metrik.

|[Binární klasifikace](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Klasifikace více tříd](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Doporučení pro regresi &](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|Přesnost| Ztráta protokolu | RSquared
|Area UnderPrecisionRecallCurve | LogLossReduction | MeanAbsoluteError
|AreaUnderRocCurve | Přesnost maker | MeanSquaredError
|F1Skóre | Mikropřesnost | Chyba RootMeanSquaredError
|NegativníPřesnost | TopKPřesnost
|NegativníRecall |
|PozitivníPřesnost
|PozitivníOdvolání

## <a name="data-pre-processing-and-featurization"></a>Předběžné zpracování a featurizace dat

> [!NOTE]
> Sloupec funkce podporuje pouze <xref:System.Boolean> <xref:System.Single>typy <xref:System.String>, a .

Předběžné zpracování dat probíhá ve výchozím nastavení a automaticky se provádějí následující kroky:

1. Drop funkce bez užitečných informací

    Drop funkce bez užitečných informací z školení a sady ověření. Patří mezi ně funkce se všemi chybějícími hodnotami, stejnou hodnotou ve všech řádcích nebo s extrémně vysokou mohutností (např. hodnoty hash, ID nebo GUID).

1. Chybějící označení hodnoty a imputace

    Vyplňte chybějící buňky hodnot výchozí hodnotou pro datový typ. Připojit indikátor funkce se stejným počtem slotů jako vstupní sloupec. Hodnota v připojených funkcích `1` indikátoru je, pokud hodnota `0` ve vstupním sloupci chybí a jinak.

1. Generovat další funkce

    Pro textové funkce: Funkce sáčku s použitím unigramů a tříznakových gramů.

    Pro kategorické funkce: Jednohorké kódování pro funkce nízké mohutnosti a kódování hash jedním hotem pro kategorické funkce s vysokou mohutností.

1. Transformace a kódování

    Textové prvky s velmi málo jedinečnými hodnotami, které jsou transformovány do kategorických prvků. V závislosti na mohutnosti kategorických funkcí proveďte kódování jedním horkým nebo jedním horkým kódováním hash.

## <a name="exit-criteria"></a>Kritéria ukončení

Definujte kritéria pro dokončení úkolu:

1. Ukončit po delší době `MaxExperimentTimeInSeconds` – Pomocí nastavení experimentu můžete definovat, jak dlouho v sekundách, že úloha by měla pokračovat v běhu.

1. Ukončit na token zrušení - Můžete použít token zrušení, který vám umožní zrušit úkol před jeho dokončením.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Vytvoření experimentu

Po konfiguraci nastavení experimentu jste připraveni experiment vytvořit.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Spusťte experiment.

Spuštění experimentu aktivuje předběžné zpracování dat, výběr algoritmu učení a hyperparametrické ladění. AutoML bude nadále generovat kombinace featurization, učení algoritmy a `MaxExperimentTimeInSeconds` hyperparameters, dokud je dosaženo nebo experiment je ukončen.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Prozkoumejte další `Execute()` přetížení, pokud chcete předat ověřovací data, informace o sloupci označující účel sloupce nebo prefeaturizers.

## <a name="training-modes"></a>Tréninkové režimy

### <a name="training-dataset"></a>Trénovací datová sada

AutoML poskytuje přetížený experiment spustit metodu, která umožňuje poskytnout trénovací data. Internally, automated ML rozděluje data do rozdělení ověření vlaku.

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a>Vlastní datová sada ověření

Vlastní ověřovací datovou sadu použijte, pokud náhodné rozdělení není přijatelné, jako je tomu obvykle u dat časových řad. Můžete zadat vlastní datovou sadu ověření. Model bude vyhodnocen podle ověřovací datové sady zadané namísto jedné nebo více náhodných datových sad.

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a>Prozkoumejte metriky modelu

Po každé iteraci experimentu ML jsou uloženy metriky vztahující se k této úloze.

Například můžeme získat přístup k metrikám ověření z nejlepšího spuštění:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Následují všechny dostupné metriky na úlohu ML:

* [Binární klasifikace metriky](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Metriky klasifikace více tříd](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Metriky doporučení regresní &](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Viz také

Úplné ukázky kódu a další najdete [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub úložiště.
