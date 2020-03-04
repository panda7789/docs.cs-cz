---
title: 'Kurz: předpověď cen pomocí regrese'
description: V tomto kurzu se naučíte, jak vytvořit regresní model s využitím ML.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 51cef97178c2dbc6a5b572a7045bdad4bc382ba0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240984"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Kurz: předpověď cen pomocí regrese s ML.NET

V tomto kurzu se naučíte, jak vytvořit [regresní model](../resources/glossary.md#regression) s využitím ml.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Příprava a pochopení dat
> * Načtení a transformace dat
> * Výběr algoritmu učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použití modelu pro předpovědi

## <a name="prerequisites"></a>Předpoklady

* [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".

1. Vytvořte v projektu adresář s názvem *data* pro uložení sady dat a souborů modelu.

1. Nainstalujte balíček NuGet **Microsoft.ml** :

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** . Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhněte si sady dat [taxi-Fare-Train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-Fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) a uložte je do složky *dat* , kterou jste vytvořili v předchozím kroku. Tyto sady dat používáme ke studiu modelu strojového učení a vyhodnocení toho, jak je model přesný. Tyto sady dat jsou původně ze [sady NYC TLC taxislužby Trip data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. V **Průzkumník řešení**klikněte pravým tlačítkem na každý ze \*souborů. csv a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

1. Otevřete sadu dat **taxi-Fare-Train. csv** a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všechny sloupce. Pochopte data a rozhodněte, které sloupce jsou **funkce** a které jsou **označeny**.

`label` je sloupec, který chcete předpovědět. Identifikované `Features`jsou vstupy, které modelu udělíte pro předpověď `Label`.

Poskytnutá datová sada obsahuje následující sloupce:

* **vendor_id:** ID dodavatele taxislužby je funkce.
* **rate_code:** Typ rychlosti taxislužby Trip je funkce.
* **passenger_count:** Počet cestujících na cestách je funkce.
* **trip_time_in_secs:** Doba, po kterou cesta trvala. Chcete předpovědět jízdné za cestu před dokončením cesty. V tuto chvíli nevíte, jak dlouho bude trvat. Doba odezvy tedy není funkcí a tento sloupec z modelu vyloučíte.
* **trip_distance:** Vzdálenost na cestách je funkce.
* **payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.
* **fare_amount:** Celková částka taxislužby jízdné je štítek.

## <a name="create-data-classes"></a>Vytváření datových tříd

Vytvořte třídy pro vstupní data a předpovědi:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TaxiTrip.cs*. Pak vyberte tlačítko **Přidat** .
1. Do nového souboru přidejte následující direktivy `using`:

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, do souboru *TaxiTrip.cs* :

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je vstupní datová třída a má definice pro každý sloupec sady dat. Pomocí atributu <xref:Microsoft.ML.Data.LoadColumnAttribute> určete indexy zdrojových sloupců v sadě dat.

Třída `TaxiTripFarePrediction` představuje předpovězené výsledky. Má jedno pole s plovoucí desetinnou čárkou, `FareAmount`s použitým atributem `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>. V případě regresní úlohy obsahuje sloupec **skóre** předpovězené hodnoty popisku.

> [!NOTE]
> Použijte `float` typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupní a předpovědi třídy dat.

### <a name="define-data-and-model-paths"></a>Definování cest k datům a modelům

Do horní části souboru *program.cs* přidejte následující další příkazy `using`:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

Je potřeba vytvořit tři pole, která budou uchovávat cesty k souborům s datovými sadami a soubor pro uložení modelu:

* `_trainDataPath` obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.
* `_testDataPath` obsahuje cestu k souboru s datovou sadou, která se používá k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k souboru, ve kterém je uložený model trained.

Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest a pro `_textLoader` proměnnou:

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

Všechny operace ML.NET začínají ve [třídě MLContext](xref:Microsoft.ML.MLContext). Inicializuje se `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů. Je podobný a koncepčně `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

Nahraďte `Console.WriteLine("Hello World!")` řádek v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné `mlContext`:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

Přidejte následující jako další řádek kódu v metodě `Main` pro volání metody `Train`:

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

Metoda `Train()` provádí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Navlakuje model.
* Vrátí model.

Metoda `Train` navlakuje model. Vytvořte tuto metodu hned pod `Main`, a to pomocí následujícího kódu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Načtení a transformace dat

ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data. `IDataView` může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu). Do prvního řádku `Train()` metody přidejte následující kód:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

Jak chcete předpovědět tarif taxislužby TRIPS, `FareAmount` sloupec je `Label`, který budete předpovědět (výstup modelu). Použijte třídu transformace `CopyColumnsEstimator` ke zkopírování `FareAmount`a přidejte následující kód:

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Algoritmus, který vlaky nastavil, vyžaduje **číselné** funkce, takže je nutné transformovat hodnoty kategorií dat (`VendorId`, `RateCode`a `PaymentType`) na čísla (`VendorIdEncoded`, `RateCodeEncoded`a `PaymentTypeEncoded`). K tomu použijte transformační třídu [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , která přiřadí různé hodnoty číselného klíče k různým hodnotám každého sloupce a přidejte následující kód:

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí třídy `mlContext.Transforms.Concatenate` transformace. Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** . Přidejte následující kód:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Výběr algoritmu učení

Tento problém se týká předpovědi tarifů taxislužby na cestách v New Yorku. Na první pohled se může zdát, že bude záviset na ujeté vzdálenosti. Taxislužby dodavatelé v New Yorku ale účtují různé částky pro jiné faktory, jako jsou další cestující nebo platby prostřednictvím platební karty místo hotovostního úvěru. Chcete odhadnout hodnotu ceny, což je skutečná hodnota, která je založená na dalších faktorech v datové sadě. Uděláte to tak, že zvolíte úlohu [regrese](../resources/glossary.md#regression) strojového učení.

Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definic transformace dat tak, že jako další řádek kódu v `Train()`přidáte následující.

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Přizpůsobit model na školicí `dataview` a vrátit vyškolený model přidáním následujícího řádku kódu do metody `Train()`:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

Vraťte školený model s následujícím řádkem kódu v metodě `Train()`:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Dále vyhodnoťte výkon vašeho modelu s testovacími daty pro zajištění a ověření kvality. Vytvořte metodu `Evaluate()` hned po `Train()`s následujícím kódem:

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

Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `Train`, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) . Vyhodnotit model pomocí této datové sady jako kontroly kvality přidáním následujícího kódu do metody `Evaluate`:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

Dále Transformujte data `Test` přidáním následujícího kódu do `Evaluate()`:

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro vstupní řádky sady testů.

Metoda `RegressionContext.Evaluate` vypočítá metriky kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí objekt <xref:Microsoft.ML.Data.RegressionMetrics>, který obsahuje celkové metriky vypočítané hodnotiteli regrese.

Aby bylo možné zjistit kvalitu modelu, je třeba nejprve získat metriky. Přidejte následující kód jako další řádek v metodě `Evaluate`:

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.

Přidejte následující kód pro vyhodnocení modelu a vytvořte metriky vyhodnocení:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) je další metrika hodnocení regresních modelů. RSquared přebírá hodnoty mezi 0 a 1. Bližší hodnota je 1, tím lepší je model. Přidejte následující kód do metody `Evaluate` pro zobrazení hodnoty RSquared:

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) je jednou ze zkušebních metrik modelu regrese. Čím nižší je, tím lepší je model. Přidejte následující kód do metody `Evaluate` k zobrazení hodnoty RMS:

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

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

Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `Evaluate`, pomocí následujícího kódu:

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Pomocí `PredictionEngine` můžete odhadnout tarif přidáním následujícího kódu do `TestSinglePrediction()`:

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.

V tomto kurzu se používá jedna zkušební cesta v rámci této třídy. Později můžete přidat další scénáře pro experimentování s modelem. Přidejte cestu k otestování předpovědi nákladů vyškolených modelů v metodě `TestSinglePrediction()` vytvořením instance `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

Dále předpovídat tarify na základě jedné instance dat taxislužby a předejte je do `PredictionEngine` přidáním následujícího jako další řádky kódu v metodě `TestSinglePrediction()`:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provádí předpovědi pro jednu instanci dat.

Chcete-li zobrazit předpovězené tarify zadané cesty, přidejte do metody `TestSinglePrediction` následující kód:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

Spusťte program, abyste viděli předpovězené taxislužby jízdné za váš testovací případ.

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro předvídání tarifů taxislužby Trip, vyhodnotili jste jeho přesnost a použili ho k vytvoření předpovědi. Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:

> [!div class="checklist"]
>
> * Příprava a pochopení dat
> * Vytvoření výukového kanálu
> * Načtení a transformace dat
> * Výběr algoritmu učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použití modelu pro předpovědi

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Iris clustering](iris-clustering.md)
