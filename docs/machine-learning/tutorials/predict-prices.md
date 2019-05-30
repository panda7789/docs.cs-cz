---
title: 'Kurz: Předvídání cen prostřednictvím regrese'
description: Tento kurz ukazuje, jak sestavit regresní model využívající ML.NET k předvídání cen, konkrétně tarify taxislužby města New York City.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 40f70b6d89bf19ae0b20cb00d56e9f7dceb48f61
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377793"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Kurz: Předvídání cen prostřednictvím regrese s ML.NET

Tento kurz ukazuje, jak sestavit [regresní model](../resources/glossary.md#regression) pomocí ML.NET k předvídání cen, konkrétně tarify taxislužby města New York City.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Příprava a pochopení dat
> * Načíst a transformovat data
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použít model pro předpovědi

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvoření **konzolovou aplikaci .NET Core** nazývá "TaxiFarePrediction".

1. Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu.

1. Nainstalujte **Microsoft.ML** balíček NuGet:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte balíček, v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené. Totéž proveďte pro **Microsoft.ML.FastTree** balíček Nuget.

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxislužby. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) dat nastaví a uloží je do *Data* složky, které jste vytvořili v předchozím kroku. Používáme tyto datové sady pro trénování modelu strojového učení a pak vyhodnotit, jak přesný je model. Tyto datové sady jsou původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

1. Otevřít **taxislužby. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všech sloupcích. Vysvětlení dat a rozhodnout, které sloupce budou **funkce** a který je **popisek**.

`label` Je sloupec, který chcete předpovědět. Identifikovanou `Features`jsou vstupy, poskytují model k predikci `Label`.

Zadaná datová sada obsahuje následující sloupce:

* **vendor_id:** ID dodavatele taxislužby je funkce.
* **rate_code:** Typ kursu cesty taxíkem je funkce.
* **passenger_count:** Počet cestujících na cestě je funkce.
* **trip_time_in_secs:** Dobu trvání cesty. Chcete předpovědět tarif cesty před dokončením cesty. V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách. Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.
* **trip_distance:** Vzdálenost cesty je funkce.
* **payment_type:** Způsob platby (hotovosti nebo kreditní karta) je funkce.
* **fare_amount:** Celkový počet taxislužby tarif placené je popisek.

## <a name="create-data-classes"></a>Vytvoření datových tříd

Vytvoření třídy pro vstupní data a předpovědí:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TaxiTrip.cs*. Vyberte **přidat** tlačítko.
1. Přidejte následující `using` direktivy do nového souboru:

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je třída vstupní data a obsahuje definice pro všechny sloupce datové sady. Použití <xref:Microsoft.ML.Data.LoadColumnAttribute> atributy indexů zdrojových sloupců v datové sadě.

`TaxiTripFarePrediction` Třída reprezentuje předpokládané výsledky. Obsahuje pole jednou čárkou `FareAmount`, s `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> atribut. V případě úloh regrese **skóre** sloupec obsahuje hodnoty předpovězené popisků.

> [!NOTE]
> Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.

### <a name="define-data-and-model-paths"></a>Definovat cesty k datům a model

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Je potřeba vytvořit tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu:

* `_trainDataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.
* `_testDataPath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.

Přidejte následující kód přímo nad `Main` metoda zadat tyto cesty a `_textLoader` proměnné:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Všechny operace ML.NET spustit v [MLContext třídy](xref:Microsoft.ML.MLContext). Inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně `DBContext` v Entity Framework.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Nahradit `Console.WriteLine("Hello World!")` řádku v `Main` metoda následujícím kódem, jak deklarovat a inicializovat `mlContext` proměnné:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Přidejte následující položky jako další řádek kódu v `Main` metoda se má volat `Train` metody:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train()` Metoda spustí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Trénovat modelu.
* Vrátí hodnotu modelu.

`Train` Metoda trénovat modelu. Vytvoření metody hned pod `Main`, pomocí následujícího kódu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Načítání a transformace dat.

Používá ML.NET [IDataView třídy](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob, jak popisují číselné nebo text tabulková data. `IDataView` můžete načíst buď textové soubory nebo v reálném čase (například SQL databázi nebo soubory protokolů). Přidejte následující kód jako první řádek `Train()` metody:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Jak chcete předpovědět tarif cesty taxíkem, `FareAmount` sloupec je `Label` , že bude předpovídat (výstup modelu) použijte `CopyColumnsEstimator` třídy transformace kopírování `FareAmount`a přidejte následující kód: 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla (`VendorIdEncoded`, `RateCodeEncoded`, a `PaymentTypeEncoded`). Chcete-li to mohli udělat, použijte [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) třídy transformace, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `mlContext.Transforms.Concatenate` třídy transformace. Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce. Přidejte následující kód:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Tento problém je o předpověď tarif cesty taxíkem v New Yorku. Na první pohled to nemusí závisí jednoduše na vzdálenost přesunul. Ale taxislužby dodavatelů v New Yorku poplatky různá množství dalších faktorů, jako je například další cestujících nebo placení pomocí platební karty místo platební. Chcete předpovídat cenu hodnotu, která je skutečná hodnota, na základě dalších faktorů v datové sadě. Chcete-li to mohli udělat, klikněte [regrese](../resources/glossary.md#regression) machine learning úloh.

Připojte [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) na definice transformace dat přidáním následujícího kódu jako další řádek kódu v machine learning úlohy `Train()`:

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Přizpůsobit modelu, který má na školení `dataview` a vrátit tak, že přidáte následující řádek kódu v trénovaného modelu `Train()` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda trénovat modelu transformace datové sady a aplikováním školení.

Vrátí trénovaného modelu s následujícím řádkem kódu `Train()` metody:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Zhodnotit svůj výkon modelu pomocí zkušebních dat kontroly kvality a ověřování. Vytvořte `Evaluate()` metoda, hned za `Train()`, následujícím kódem:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` Metoda spustí následující úlohy:

* Načte datovou sadu testů.
* Chyba při vyhodnocování regrese vytvoří.
* Vyhodnotí modelu a vytvoří metriky.
* Zobrazuje metriky.

Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Načíst testovací datové sady pomocí [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody. Vyhodnocení modelu s použitím tohoto objektu dataset jako kontrola kvality tak, že přidáte následující kód `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

V dalším kroku transformovat `Test` data přidáním následujícího kódu do `EvaluateModel()`:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda řádky vstupní datovou sadu vytváří předpovědi pro test.

`RegressionContext.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení regrese. 

Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první. Přidejte následující kód jako další řádek `Evaluate` metody:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Až budete mít předpovědi nastavená, [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` v testovací datové sady a vrátí metriky na jaký je výkon modelu.

Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů. RSquared trvá hodnoty v rozmezí 0 až 1. Čím blíž její hodnota je 1, tím lepší je model. Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model. Čím nižší je, tím lepší je model. Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Použít model pro předpovědi

Vytvořte `TestSinglePrediction` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction` Metoda spustí následující úlohy:

* Vytvoří jeden komentář testovací data.
* Předpovídá tarif velikost na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Použití `PredictionEngine` k předpovědi tarif přidáním následujícího kódu `TestSinglePrediction()`:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které vám umožní předat jedna instance data a pak na něm provést predikcí.

Tento kurz používá jeden test latence v rámci této třídy. Později můžete přidat další scénáře můžete experimentovat s modelem. Přidat cestu k otestování předpovědi trénovaného modelu nákladů `TestSinglePrediction()` metodu tak, že vytvoříte instanci `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

V dalším kroku předpovědět tarif založené na jednu instanci data o jízdách taxislužby města a předejte ji do `PredictionEngine` přidáním následujícího kódu jako další řádky kódu ve `TestSinglePrediction()` metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce díky predikcí na jednu instanci data.

K zobrazení předpokládané tarif zadané cesty, přidejte následující kód do `TestSinglePrediction` metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.

Blahopřejeme! Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště GitHub.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:

> [!div class="checklist"]
> * Příprava a pochopení dat
> * Vytvoření kanálu učení
> * Načíst a transformovat data
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použít model pro předpovědi

Přejděte k dalšímu kurzu, kde Další informace.

> [!div class="nextstepaction"]
> [Iris clustering](iris-clustering.md)
