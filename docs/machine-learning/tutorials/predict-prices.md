---
title: 'Kurz: Předvídání cen pomocí regrese'
description: Tento kurz ukazuje, jak vytvořit regresní model pomocí ML.NET předpovědět ceny, konkrétně new york city taxi tarify.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 91429383341cf718d38e636bd1d71dc25d30d20d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607968"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Kurz: Předvídejte ceny pomocí regrese s ML.NET

Tento kurz ukazuje, jak vytvořit [regresní model](../resources/glossary.md#regression) pomocí ML.NET předpovědět ceny, konkrétně new york city taxi tarify.

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

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **aplikaci .NET Core Console s** názvem "TaxiFarePrediction".

1. Vytvořte adresář s názvem *Data* v projektu pro uložení datové sady a souborů modelu.

1. Nainstalujte **balíček nuget Microsoft.ML:**

    V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet,** vyhledejte **Microsoft.ML**, vyberte balíček v seznamu a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky. Proveďte totéž pro balíček **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhněte si datové sady [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) a uložte je do složky *Data,* kterou jste vytvořili v předchozím kroku. Tyto datové sady používáme k trénování modelu strojového učení a následnému vyhodnocení, jak přesný je model. Tyto datové sady jsou původně z [NYC TLC Taxi Trip datové sady](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. V **Průzkumníku řešení**klepněte \*pravým tlačítkem myši na jednotlivé soubory CSV a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

1. Otevřete datovou sadu **taxi-fare-train.csv** a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na každý sloupec. Porozumějte datům a rozhodněte, které sloupce jsou **prvky** a které jsou **popiskem**.

Je `label` sloupec, který chcete předpovědět. Identifikované `Features`jsou vstupy, které poskytnete `Label`modelu předpovědět .

Zadaný soubor dat obsahuje následující sloupce:

* **vendor_id:** ID dodavatele taxi služby je funkce.
* **rate_code:** Typ sazby taxi cesty je funkce.
* **passenger_count:** Počet cestujících na cestě je funkce.
* **trip_time_in_secs:** Doba, po kterou cesta trvala. Chcete předpovědět jízdné cesty před dokončením cesty. V tu chvíli nevíte, jak dlouho by cesta zabrala. Doba jízdy tedy není funkcí a tento sloupec z modelu vyloučíte.
* **trip_distance:** Vzdálenost cesty je funkce.
* **payment_type:** Platební metoda (v hotovosti nebo kreditní kartou) je funkce.
* **fare_amount:** Celková zaplacená taxi služba je štítek.

## <a name="create-data-classes"></a>Vytvoření tříd dat

Vytvořte třídy pro vstupní data a předpovědi:

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *TaxiTrip.cs*. Potom vyberte tlačítko **Přidat.**
1. Do nového souboru přidejte následující `using` direktivy:

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, do souboru *TaxiTrip.cs:*

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`je třída vstupních dat a obsahuje definice pro každý sloupec sady dat. Pomocí <xref:Microsoft.ML.Data.LoadColumnAttribute> atributu můžete určit indexy zdrojových sloupců v sadě dat.

Třída `TaxiTripFarePrediction` představuje předpokládané výsledky. Má jedno plovoucí pole `FareAmount`, `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> s aplikovaným atributem. V případě regresní úlohy obsahuje sloupec **Skóre** předpokládané hodnoty popisků.

> [!NOTE]
> Použijte `float` typ k reprezentaci hodnot s plovoucí desetinnou desetinnou třídou vstupních dat a predikcí.

### <a name="define-data-and-model-paths"></a>Definování dat a cest modelu

Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

Chcete-li uložit model, musíte vytvořit tři pole, která uchovává cesty k souborům se sadami dat a souborem:

* `_trainDataPath`obsahuje cestu k souboru se sadou dat použitou k trénování modelu.
* `_testDataPath`obsahuje cestu k souboru se sadou dat použitou k vyhodnocení modelu.
* `_modelPath`obsahuje cestu k souboru, kde je uložen trénovaný model.

Přidejte následující kód `Main` přímo nad metodu k `_textLoader` určení těchto cest a pro proměnnou:

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

Všechny operace ML.NET spustit ve [třídě MLContext](xref:Microsoft.ML.MLContext). Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v hlavní

Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro `mlContext` deklarování a inicializaci proměnné:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

Přidejte následující jako další řádek `Main` kódu v `Train` metodě pro volání metody:

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

Metoda `Train()` provádí následující úkoly:

* Načte data.
* Extrahuje a transformuje data.
* Trénuje model.
* Vrátí model.

Metoda `Train` trénuje model. Vytvořte tuto `Main`metodu těsně pod , pomocí následujícího kódu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Načítání a transformace dat

ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisu číselných nebo textových tabulkových dat. `IDataView`můžete načíst textové soubory nebo v reálném čase (například SQL database nebo log files). Jako první řádek `Train()` metody přidejte následující kód:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

Jak chcete předpovědět taxi výlet jízdného, `FareAmount` `Label` sloupec je, že budete předvídat (výstup modelu). Použijte `CopyColumnsEstimator` třídu transformace `FareAmount`ke kopírování a přidejte následující kód:

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Algoritmus, který trénuje model, vyžaduje **číselné** funkce,`VendorId`takže `RateCode`je `PaymentType`třeba transformovat`VendorIdEncoded`hodnoty `RateCodeEncoded`kategorických dat ( , , a ) na čísla ( , , a `PaymentTypeEncoded`). Chcete-li to provést, použijte třídu transformace [OneHotEncodingTransformer,](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) která přiřadí různé číselné hodnoty klíče různým hodnotám v každém sloupci, a přidejte následující kód:

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Poslední krok v přípravě dat kombinuje všechny **Features** sloupce funkce `mlContext.Transforms.Concatenate` do sloupce Funkce pomocí třídy transformace. Ve výchozím nastavení algoritmus učení zpracovává pouze funkce ze sloupce **Funkce.** Přidejte následující kód:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Výběr algoritmu učení

Tento problém je o předpovídání taxi výlet jízdného v New Yorku. Na první pohled se může zdát, že závisí pouze na ujeté vzdálenosti. Prodejci taxi služeb v New Yorku však účtují různé částky za další faktory, jako jsou další cestující nebo placení kreditní kartou místo hotovosti. Chcete předpovědět hodnotu ceny, což je reálná hodnota, na základě dalších faktorů v datové sadě. Chcete-li to provést, můžete zvolit úlohu [regrese](../resources/glossary.md#regression) strojového učení.

Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) k definicím transformace dat přidáním následujícího jako následující řádek kódu v aplikaci `Train()`:

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Připevněte model `dataview` do tréninku a vraťte trénovaný `Train()` model přidáním následujícího řádku kódu v metodě:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

[Metoda Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trénuje váš model transformací datové sady a použitím školení.

Vrátit trénovaný model s následujícím `Train()` řádkem kódu v metodě:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Dále vyhodnoťte výkon modelu pomocí testovacích dat pro zajištění kvality a ověření. Vytvořte `Evaluate()` metodu, `Train()`těsně po , s následujícím kódem:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

Metoda `Evaluate` provádí následující úkoly:

* Načte testovací datovou sadu.
* Vytvoří regresní vyhodnocení.
* Vyhodnotí model a vytvoří metriky.
* Zobrazí metriky.

Přidejte volání nové metody `Main` z metody, `Train` přímo pod volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile().](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) Vyhodnoťte model pomocí této datové sady `Evaluate` jako kontrolu kvality přidáním následujícího kódu v metodě:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

Dále transformujte `Test` data přidáním následujícího kódu do `Evaluate()`aplikace :

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) Metoda umožňuje předpovědi pro vstupní řádky testovací datové sady.

Metoda `RegressionContext.Evaluate` vypočítá metriky kvality pro `PredictionModel` použití zadané datové sady. Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkové metriky vypočítané regresními vyhodnoceními.

Chcete-li zobrazit tyto určit kvalitu modelu, musíte nejprve získat metriky. Jako další řádek `Evaluate` metody přidejte následující kód:

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

Jakmile máte předpověď nastavit, [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metoda vyhodnotí model, který porovnává předpovídané hodnoty s aktuální `Labels` v testovací datové sady a vrátí metriky o tom, jak model funguje.

Přidejte následující kód k vyhodnocení modelu a vytvoření metriky hodnocení:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) je další hodnotící metrika regresních modelů. RSquared trvá hodnoty mezi 0 a 1. Čím blíže je jeho hodnota 1, tím lepší je model. Přidejte do metody `Evaluate` následující kód pro zobrazení hodnoty RSquared:

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) je jednou z hodnotících metrik regresního modelu. Čím nižší je, tím lepší je model. Přidejte do metody `Evaluate` následující kód pro zobrazení hodnoty služby RMS:

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Použití modelu pro předpovědi

Vytvořte `TestSinglePrediction` metodu, `Evaluate` hned za metodou, pomocí následujícího kódu:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Metoda `TestSinglePrediction` provádí následující úkoly:

* Vytvoří jeden komentář testovacích dat.
* Předpovídá částku jízdného na základě testovacích dat.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí předpokládané výsledky.

Přidejte volání nové metody `Main` z metody, `Evaluate` přímo pod volání metody, pomocí následujícího kódu:

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Použijte `PredictionEngine` předpovědět jízdné přidáním následujícího `TestSinglePrediction()`kódu:

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

Tento kurz používá jednu zkušební cestu v rámci této třídy. Později můžete přidat další scénáře experimentovat s modelem. Přidejte výlet a otestujte predikci `TestSinglePrediction()` nákladů trénovaného `TaxiTrip`modelu v metodě vytvořením instance :

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

Dále předpovědět jízdné na základě jedné instance taxi data cesty `PredictionEngine` a předat ji tím, že přidá `TestSinglePrediction()` následující jako další řádky kódu v metodě:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jednu instanci dat.

Chcete-li zobrazit předpokládané jízdné zadané cesty, přidejte `TestSinglePrediction` do metody následující kód:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

Spusťte program a podívejte se na předpokládané jízdné taxi pro váš testovací případ.

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro předpovídání jízdného na taxi, vyhodnotili jste jeho přesnost a použili jste ho k předpovědím. Zdrojový kód pro tento kurz najdete v úložišti [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction)

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

Přejdete k dalšímu kurzu, abyste se dozvěděli více.

> [!div class="nextstepaction"]
> [Iris clustering](iris-clustering.md)
