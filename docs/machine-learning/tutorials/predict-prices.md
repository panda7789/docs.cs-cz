---
title: 'Kurz: předpověď cen pomocí regrese'
description: V tomto kurzu se naučíte, jak vytvořit regresní model s využitím ML.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: beb48c9252b83cd693c351d39882b7ac9d08d882
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309713"
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

## <a name="prerequisites"></a>Požadavky

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".

1. Vytvořte v projektu adresář s názvem *data* pro uložení sady dat a souborů modelu.

1. Nainstalujte balíček NuGet **Microsoft.ml** a **Microsoft. ml. FastTree** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** . Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhněte [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) datových sad a uložte je do složky *dat* , kterou jste vytvořili v předchozím kroku. Tyto sady dat používáme ke studiu modelu strojového učení a vyhodnocení toho, jak je model přesný. Tyto sady dat jsou původně ze [sady NYC TLC taxislužby Trip data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. V **Průzkumník řešení**klikněte pravým tlačítkem na každý ze \* souborů. csv a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

1. Otevřete sadu dat **taxi-fare-train.csv** a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všechny sloupce. Pochopte data a rozhodněte, které sloupce jsou **funkce** a které jsou **označeny**.

`label`Je sloupec, který chcete předpovědět. Identifikované `Features` jsou vstupy, které modelu poskytnete pro předpověď `Label` .

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

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TaxiTrip.cs*. Pak vyberte tlačítko **Přidat** .
1. `using`Do nového souboru přidejte následující direktivy:

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction` , do souboru *TaxiTrip.cs* :

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`je vstupní datová třída a má definice pro každý sloupec sady dat. Použijte <xref:Microsoft.ML.Data.LoadColumnAttribute> atribut k určení indexů zdrojových sloupců v sadě dat.

`TaxiTripFarePrediction`Třída představuje předpovězené výsledky. Má jedno pole s plovoucí desetinnou čárkou, `FareAmount` s `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> použitým atributem. V případě regresní úlohy obsahuje sloupec **skóre** předpovězené hodnoty popisku.

> [!NOTE]
> Použijte `float` typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách.

### <a name="define-data-and-model-paths"></a>Definování cest k datům a modelům

`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

Je potřeba vytvořit tři pole, která budou uchovávat cesty k souborům s datovými sadami a soubor pro uložení modelu:

* `_trainDataPath`obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.
* `_testDataPath`obsahuje cestu k souboru s datovou sadou použitou k vyhodnocení modelu.
* `_modelPath`obsahuje cestu k souboru, ve kterém je uložený model trained.

Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest a `_textLoader` proměnné:

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

Všechny operace ML.NET začínají ve [třídě MLContext](xref:Microsoft.ML.MLContext). Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

Nahraďte `Console.WriteLine("Hello World!")` řádek v `Main` metodě následujícím kódem pro deklaraci a inicializaci `mlContext` proměnné:

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

Přidejte následující jako další řádek kódu v `Main` metodě pro volání `Train` metody:

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

`Train()`Metoda provádí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Navlakuje model.
* Vrátí model.

`Train`Metoda navlakuje model. Vytvořte tuto metodu hned níže `Main` pomocí následujícího kódu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Načtení a transformace dat

ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data. `IDataView`může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu). Do prvního řádku metody přidejte následující kód `Train()` :

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

Jak chcete předpovědět tarif taxislužby TRIPS, je ve `FareAmount` sloupci `Label` , který budete předpovídat (výstup modelu). Použijte `CopyColumnsEstimator` třídu transformace ke zkopírování `FareAmount` a přidejte následující kód:

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Algoritmus, který vlaky nastavil, vyžaduje **číselné** funkce, takže je nutné transformovat hodnoty kategorií dat ( `VendorId` , `RateCode` a `PaymentType` ) na čísla ( `VendorIdEncoded` , a `RateCodeEncoded` `PaymentTypeEncoded` ). K tomu použijte transformační třídu [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , která přiřadí různé hodnoty číselného klíče k různým hodnotám každého sloupce a přidejte následující kód:

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí `mlContext.Transforms.Concatenate` třídy transformace. Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** . Přidejte následující kód:

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Výběr algoritmu učení

Tento problém se týká předpovědi tarifů taxislužby na cestách v New Yorku. Na první pohled se může zdát, že bude záviset na ujeté vzdálenosti. Taxislužby dodavatelé v New Yorku ale účtují různé částky pro jiné faktory, jako jsou další cestující nebo platby prostřednictvím platební karty místo hotovostního úvěru. Chcete odhadnout hodnotu ceny, což je skutečná hodnota, která je založená na dalších faktorech v datové sadě. Uděláte to tak, že zvolíte úlohu [regrese](../resources/glossary.md#regression) strojového učení.

Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) k definicím transformace dat, a to přidáním následujícího jako další řádek kódu v `Train()` :

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Přizpůsobit model školením `dataview` a vrátit školicí model přidáním následujícího řádku kódu do `Train()` metody:

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

Vraťte vyškolený model s následujícím řádkem kódu v `Train()` metodě:

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Dále vyhodnoťte výkon vašeho modelu s testovacími daty pro zajištění a ověření kvality. Vytvořte `Evaluate()` metodu, hned po `Train()` , s následujícím kódem:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate`Metoda provádí následující úlohy:

* Načte testovací datovou sadu.
* Vytvoří vyhodnocovací filtr regrese.
* Vyhodnotí model a vytvoří metriky.
* Zobrazí metriky.

Přidejte volání do metody New z `Main` metody přímo pod `Train` voláním metody pomocí následujícího kódu:

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) . Vyhodnotit model pomocí této datové sady jako kontroly kvality přidáním následujícího kódu do `Evaluate` metody:

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

Dále Transformujte `Test` data přidáním následujícího kódu do `Evaluate()` :

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro vstupní řádky sady testů.

`RegressionContext.Evaluate`Metoda vypočítá metriky kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkové metriky vypočítané hodnotiteli regrese.

Aby bylo možné zjistit kvalitu modelu, je třeba nejprve získat metriky. Přidejte následující kód jako další řádek v `Evaluate` metodě:

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.

Přidejte následující kód pro vyhodnocení modelu a vytvořte metriky vyhodnocení:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) je další metrika hodnocení regresních modelů. RSquared přebírá hodnoty mezi 0 a 1. Bližší hodnota je 1, tím lepší je model. Do metody přidejte následující kód, `Evaluate` aby se zobrazila hodnota RSquared:

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) je jednou ze zkušebních metrik modelu regrese. Čím nižší je, tím lepší je model. Do metody přidejte následující kód `Evaluate` pro zobrazení hodnoty RMS:

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Použití modelu pro předpovědi

Vytvořte `TestSinglePrediction` metodu hned za `Evaluate` metodou pomocí následujícího kódu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction`Metoda provádí následující úlohy:

* Vytvoří jeden komentář testovacích dat.
* Odhadne částku tarifu na základě testovacích dat.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí předpovězené výsledky.

Přidejte volání do metody New z `Main` metody přímo pod `Evaluate` voláním metody pomocí následujícího kódu:

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Použijte `PredictionEngine` k předpovědi tarifu přidáním následujícího kódu do `TestSinglePrediction()` :

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.

V tomto kurzu se používá jedna zkušební cesta v rámci této třídy. Později můžete přidat další scénáře pro experimentování s modelem. Přidejte cestu k otestování předpovědi nákladů vyškolených modelů v `TestSinglePrediction()` metodě vytvořením instance `TaxiTrip` :

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

Dále předpovídat tarify na základě jedné instance dat taxislužby a předejte je do rozhraní `PredictionEngine` přidáním následujícího jako další řádky kódu v `TestSinglePrediction()` metodě:

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provádí předpovědi pro jednu instanci dat.

Chcete-li zobrazit předpovězené tarify zadané cesty, přidejte do metody následující kód `TestSinglePrediction` :

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

Spusťte program, abyste viděli předpovězené taxislužby jízdné za váš testovací případ.

Blahopřejeme. Teď jste úspěšně vytvořili model strojového učení pro předvídání tarifů taxislužby Trip, vyhodnotili jste jeho přesnost a použili ho k vytvoření předpovědi. Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.

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
