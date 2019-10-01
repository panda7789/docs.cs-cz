---
title: 'Kurz: předpověď cen pomocí regrese'
description: V tomto kurzu se naučíte, jak vytvořit regresní model s využitím ML.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 8db6b0c9ae1fd98724eda285423960546be8bac6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700948"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Kurz: předpověď cen pomocí regrese s ML.NET

V tomto kurzu se naučíte, jak vytvořit [regresní model](../resources/glossary.md#regression) s využitím ml.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Příprava a pochopení dat
> * Načtení a transformace dat
> * Výběr algoritmu učení
> * Výuka modelu
> * Vyhodnocení modelu
> * Použití modelu pro předpovědi

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".

1. Vytvořte v projektu adresář s názvem *data* pro uložení sady dat a souborů modelu.

1. Nainstalujte balíček NuGet **Microsoft.ml** :

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** . Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhněte si sady dat [taxi-Fare-Train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-Fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) a uložte je do složky *dat* , kterou jste vytvořili v předchozím kroku. Tyto sady dat používáme ke studiu modelu strojového učení a vyhodnocení toho, jak je model přesný. Tyto sady dat jsou původně ze [sady NYC TLC taxislužby Trip data](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. V **Průzkumník řešení**klikněte pravým tlačítkem na všechny soubory @no__t -1. csv a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

1. Otevřete sadu dat **taxi-Fare-Train. csv** a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všechny sloupce. Pochopte data a rozhodněte, které sloupce jsou **funkce** a které jsou **označeny**.

@No__t-0 je sloupec, který chcete předpovědět. Identifikované @no__t – 0are vstupy, které model udělíte, aby předpovídat `Label`.

Poskytnutá datová sada obsahuje následující sloupce:

* **vendor_id:** ID dodavatele taxislužby je funkce.
* **rate_code:** Typ rychlosti taxislužby Trip je funkce.
* **passenger_count:** Počet cestujících na cestách je funkce.
* **trip_time_in_secs:** Doba, po kterou cesta trvala. Chcete předpovědět jízdné za cestu před dokončením cesty. V tuto chvíli nevíte, jak dlouho trvá služební cyklus. Doba odezvy tedy není funkcí a tento sloupec z modelu vyloučíte.
* **trip_distance:** Vzdálenost na cestách je funkce.
* **payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.
* **fare_amount:** Celková částka taxislužby jízdné je štítek.

## <a name="create-data-classes"></a>Vytváření datových tříd

Vytvořte třídy pro vstupní data a předpovědi:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TaxiTrip.cs*. Pak vyberte tlačítko **Přidat** .
1. Do nového souboru přidejte následující direktivy `using`:

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, do souboru *TaxiTrip.cs* :

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je vstupní datová třída a má definice pro každý sloupec sady dat. Pomocí atributu <xref:Microsoft.ML.Data.LoadColumnAttribute> určete indexy zdrojových sloupců v sadě dat.

Třída `TaxiTripFarePrediction` představuje předpovězené výsledky. Má jedno pole s plovoucí desetinnou čárkou, `FareAmount` s použitým atributem `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>. V případě regresní úlohy obsahuje sloupec **skóre** předpovězené hodnoty popisku.

> [!NOTE]
> K reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách použijte typ `float`.

### <a name="define-data-and-model-paths"></a>Definování cest k datům a modelům

Do horní části souboru *program.cs* přidejte následující dodatečné příkazy `using`:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Je potřeba vytvořit tři pole, která budou uchovávat cesty k souborům s datovými sadami a soubor pro uložení modelu:

* `_trainDataPath` obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.
* `_testDataPath` obsahuje cestu k souboru s datovou sadou použitou k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k souboru, ve kterém je uložený model trained.

Přidejte následující kód přímo nad metodu `Main` pro určení těchto cest a pro proměnnou `_textLoader`:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Všechny operace ML.NET začínají ve [třídě MLContext](xref:Microsoft.ML.MLContext). Inicializace `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu vytváření modelů. Je podobné, koncepčně, `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

Nahraďte řádek `Console.WriteLine("Hello World!")` v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné `mlContext`:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Přidejte následující jako další řádek kódu do metody `Main` pro volání metody `Train`:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

Metoda `Train()` provádí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Navlakuje model.
* Vrátí model.

Metoda `Train` navlakuje model. Vytvořte tuto metodu hned pod `Main` pomocí následujícího kódu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Načtení a transformace dat

ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data. `IDataView` může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu). Do prvního řádku metody `Train()` přidejte následující kód:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Jak chcete předpovědět tarif taxislužby TRIPS, sloupec `FareAmount` je `Label`, který budete předpovědět (výstup modelu) použijte ke kopírování `FareAmount` třídu transformace `CopyColumnsEstimator` a přidejte následující kód: 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Algoritmus, který předává model, vyžaduje **číselné** funkce, takže je nutné transformovat hodnoty dat kategorií (`VendorId`, `RateCode` a `PaymentType`) na čísla (`VendorIdEncoded`, `RateCodeEncoded` a `PaymentTypeEncoded`). K tomu použijte transformační třídu [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , která přiřadí různé hodnoty číselného klíče k různým hodnotám každého sloupce a přidejte následující kód:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí transformační třídy `mlContext.Transforms.Concatenate`. Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** . Přidejte následující kód:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Výběr algoritmu učení

Tento problém se týká předpovědi tarifů taxislužby na cestách v New Yorku. Na první pohled se může zdát, že bude záviset na ujeté vzdálenosti. Taxislužby dodavatelé v New Yorku ale účtují různé částky pro jiné faktory, jako jsou další cestující nebo platby prostřednictvím platební karty místo hotovostního úvěru. Chcete odhadnout hodnotu ceny, což je skutečná hodnota, která je založená na dalších faktorech v datové sadě. Uděláte to tak, že zvolíte úlohu [regrese](../resources/glossary.md#regression) strojového učení.

Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definic transformace dat tak, že jako další řádek kódu v `Train()` přidáte následující.

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Výuka modelu

Přizpůsobit model školením `dataview` a vrátit vyškolený model přidáním následujícího řádku kódu do metody `Train()`:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

Vraťte vyškolený model s následujícím řádkem kódu v metodě `Train()`:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Dále vyhodnoťte výkon vašeho modelu s testovacími daty pro zajištění a ověření kvality. Vytvořte metodu `Evaluate()` hned za `Train()` s následujícím kódem:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

Metoda `Evaluate` provádí následující úlohy:

* Načte testovací datovou sadu.
* Vytvoří vyhodnocovací filtr regrese.
* Vyhodnotí model a vytvoří metriky.
* Zobrazí metriky.

Přidejte volání do nové metody z metody `Main` přímo pod voláním metody `Train` pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) . Vyhodnotit model pomocí této datové sady jako kontroly kvality přidáním následujícího kódu do metody `Evaluate`:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Dále Transformujte data `Test` přidáním následujícího kódu do `EvaluateModel()`:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro vstupní řádky sady testů.

Metoda `RegressionContext.Evaluate` počítá metriky kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí objekt <xref:Microsoft.ML.Data.RegressionMetrics>, který obsahuje celkové metriky vypočítané pomocí regresních vyhodnocení. 

Aby bylo možné zjistit kvalitu modelu, je třeba nejprve získat metriky. Přidejte následující kód jako další řádek v metodě `Evaluate`:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.

Přidejte následující kód pro vyhodnocení modelu a vytvořte metriky vyhodnocení:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) je další metrika hodnocení regresních modelů. RSquared přebírá hodnoty mezi 0 a 1. Bližší hodnota je 1, tím lepší je model. Přidejte následující kód do metody `Evaluate`, aby se zobrazila hodnota RSquared:

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jednou ze zkušebních metrik modelu regrese. Čím nižší je, tím lepší je model. Přidejte následující kód do metody `Evaluate` pro zobrazení hodnoty RMS:

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Použití modelu pro předpovědi

Vytvořte metodu `TestSinglePrediction` hned za metodou `Evaluate` pomocí následujícího kódu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Metoda `TestSinglePrediction` provádí následující úlohy:

* Vytvoří jeden komentář testovacích dat.
* Odhadne částku tarifu na základě testovacích dat.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí předpovězené výsledky.

Přidejte volání do nové metody z metody `Main` přímo pod voláním metody `Evaluate` pomocí následujícího kódu:

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Pomocí `PredictionEngine` můžete odhadnout tarif přidáním následujícího kódu do `TestSinglePrediction()`:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci. V této příručce najdete informace o [použití `PredictionEnginePool` v ASP.NET Core webovém rozhraní API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) .

> [!NOTE]
> rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.

V tomto kurzu se používá jedna zkušební cesta v rámci této třídy. Později můžete přidat další scénáře pro experimentování s modelem. Přidejte cestu k otestování předpovědi nákladů vyškolených modelů v metodě `TestSinglePrediction()` vytvořením instance `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

Dále předpovídat tarify na základě jedné instance dat taxislužby a předejte ji do `PredictionEngine` přidáním následujícího jako další řádky kódu v metodě `TestSinglePrediction()`:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provádí předpovědi pro jednu instanci dat.

Chcete-li zobrazit předpovězené tarify zadané cesty, přidejte následující kód do metody `TestSinglePrediction`:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Spusťte program, abyste viděli předpovězené taxislužby jízdné za váš testovací případ.

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro předvídání tarifů taxislužby Trip, vyhodnotili jste jeho přesnost a použili ho k vytvoření předpovědi. Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak:

> [!div class="checklist"]
>
> * Příprava a pochopení dat
> * Vytvoření výukového kanálu
> * Načtení a transformace dat
> * Výběr algoritmu učení
> * Výuka modelu
> * Vyhodnocení modelu
> * Použití modelu pro předpovědi

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Iris clustering](iris-clustering.md)
