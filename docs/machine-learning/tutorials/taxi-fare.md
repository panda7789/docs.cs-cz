---
title: Předvídání cen pomocí learner regrese ML.NET
description: Předvídání cen pomocí ML.NET learner regrese.
author: aditidugar
ms.author: johalex
ms.date: 02/08/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d9c87c4f4a81c02979259a47e8c4167d80f06377
ms.sourcegitcommit: a532e8314c3a4b5b039656567fedff9787a31957
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251089"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a>Kurz: Předvídání cen pomocí learner regrese ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz ukazuje, jak použít ML.NET k sestavení [regresní model](../resources/glossary.md#regression) pro odhad ceny, konkrétně, tarify taxislužby města New York City.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava a pochopení dat
> * Vytvoření kanálu učení
> * Načíst a transformovat data
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použít model pro předpovědi

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

## <a name="understand-the-problem"></a>Pochopení problému

Tento problém je o predikci tarif cesty taxíkem v New Yorku. Na první pohled to nemusí závisí jednoduše na vzdálenost přesunul. Ale taxislužby dodavatelů v New Yorku poplatky různá množství dalších faktorů, jako je například další cestujících nebo placení pomocí platební karty místo platební.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

Chcete předpovídat cenu hodnotu, která je skutečná hodnota, na základě dalších faktorů v datové sadě. Udělat, abyste zvolili [regrese](../resources/glossary.md#regression) machine learning úloh.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.

1. Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

1. Nainstalujte **Microsoft.ML** balíček NuGet:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxislužby. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) dat nastaví a uloží je do *Data* složky, které jste vytvořili v předchozím kroku. Používáme tyto datové sady pro trénování modelu strojového učení a pak vyhodnotit, jak přesný je model. Tyto datové sady jsou původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

1. Otevřít **taxislužby. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všech sloupcích. Vysvětlení dat a rozhodnout, které sloupce budou **funkce** a který je **popisek**.

**Popisek** je identifikátor sloupce, který chcete předpovědět. Identifikovanou **funkce** se používají k předpovědi popisek.

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

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je třída vstupní data a obsahuje definice pro všechny sloupce datové sady. Použití <xref:Microsoft.ML.Data.ColumnAttribute> atributy indexů zdrojových sloupců v datové sadě.

`TaxiTripFarePrediction` Třída reprezentuje předpokládané výsledky. Obsahuje pole jednou čárkou `FareAmount`, s `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> atribut. V případě úloh regrese **skóre** sloupec obsahuje hodnoty předpovězené popisků.

> [!NOTE]
> Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.

## <a name="define-data-and-model-paths"></a>Definovat cesty k datům a model

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Je potřeba vytvořit tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu a globální proměnné pro `TextLoader`:

* `_trainDataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.
* `_testDataPath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.
* `_textLoader` je <xref:Microsoft.ML.Data.TextLoader> lze načíst a transformovat datové sady.

Přidejte následující kód přímo nad `Main` metoda zadat tyto cesty a `_textLoader` proměnné:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Při vytváření modelu s ML.NET spustíte tak, že vytvoříte objekt Context ML. Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework. Prostředí poskytuje kontext pro úlohu machine learning, který lze použít pro sledování a protokolování výjimek.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Vytvořte proměnnou s názvem `mlContext` a inicializujte novou instanci třídy `MLContext`.  Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Další nastavení pro načítání inicializace dat `_textLoader` globální proměnné, aby bylo možné znovu použít. Při vytváření `TextLoader`, předáte v souvislosti potřebné a <xref:Microsoft.ML.Data.TextLoader.Arguments> třída, která umožňuje přizpůsobení. Zadejte schéma dat předáním pole <xref:Microsoft.ML.Data.TextLoader.Column> objektů `TextLoader` obsahující všechny názvy sloupců a jejich typy. Jsme dříve definovali schéma dat když jsme vytvořili naši `TaxiTrip` třídy.

`TextLoader` Třídy vrátí plně inicializován <xref:Microsoft.ML.Data.TextLoader>  

Inicializovat `_textLoader` globální proměnné, aby bylo možné znovu použít pro potřeby datové sady, přidejte následující kód za `mlContext` inicializace:

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Initialize the TextLoader")]

Přidejte následující položky jako další řádek kódu v `Main` metoda se má volat `Train` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train` Metoda spustí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Trénovat modelu.
* Model se uloží jako soubor ZIP.
* Vrátí hodnotu modelu.

`Train` Metoda trénovat modelu. Vytvoření metody hned pod `Main`, pomocí následujícího kódu:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Jsme prochází dva parametry do `Train` metoda; `MLContext` kontextu (`mlContext`) a řetězec pro cestu k datové sadě (`dataPath`). Chceme znovu použít tuto metodu pro načtení datové sady.

## <a name="load-and-transform-data"></a>Načítání a transformace dat.

Budete načteme data s využitím `_textLoader` globální proměnné `dataPath` parametru. Vrátí <xref:Microsoft.Data.DataView.IDataView>. Jako vstup a výstup transformace `IDataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.

Data jsou v ML.NET, podobně jako zobrazení SQL. Je laxně Vyhodnocená schematizovanými a heterogenní. Objekt představuje první část kanálu a načte data. Pro účely tohoto kurzu načte datovou sadu s informacemi o jízdách taxislužby užitečné k předpovědi tarify. Slouží k vytvoření modelu a jeho trénování.

 Přidejte následující kód jako první řádek `Train` metody:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

V dalších krocích budeme odkazovat na sloupce pomocí názvy definované v `TaxiTrip` třídy.

Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat. Protože chceme předpovědět tarif cesty taxíkem, zkopírujte `FareAmount` sloupec **popisek** sloupec. Chcete-li to mohli udělat, použijte `CopyColumnsEstimator` transformace třídu a přidejte následující kód:

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla. Chcete-li to mohli udělat, použijte `OneHotEncodingEstimator` třídy transformace, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `ColumnConcatenatingEstimator` třídy transformace. Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce. Přidejte následující kód:

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vybereme algoritmu učení (**learner**). Learner trénovat modelu. Rozhodli jsme se **regrese** úkol pro tento problém, takže použijeme `FastTreeRegressionTrainer` learner, což je jedna studentů regrese poskytované ML.NET.

`FastTreeRegressionTrainer` Learner využívá přechodu zvýšení skóre. Přechodu zvýšení skóre je strojové učení techniku pro regresní problémy. Sestaví každém stromu regrese způsobem podle jednotlivých kroků. Předdefinované ztráta funkce používá k měření chyb v každém kroku a opravit ho v dalším. Výsledkem je, který je ve skutečnosti kompletu sady slabší prediktivní modely prediktivní model. Další informace o přechodu zvýšení skóre, naleznete v tématu [Boosted regrese rozhodovacího stromu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Přidejte následující kód do `Train` způsob, jak přidat `FastTreeRegressionTrainer` na zpracování dat kód přidaný v předchozím kroku:

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Posledním krokem je pro trénování modelu. Model trénujeme <xref:Microsoft.ML.Data.TransformerChain>založená na datovou sadu, která má načíst a transformovat. Po definování odhadu trénujeme pomocí modelu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> současně už načtený trénovací data. Vrátí model pro předpovědi. `pipeline.Fit()` trénovat kanálu a vrátí `Transformer` na základě `DataView` předán. Experiment není spuštěn, dokud k tomu dojde.

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

A to je všechno! Úspěšně jste trénuje model, který může předpovídat tarify taxislužby města v NYC strojového učení. Nyní Pojďme podívat, abyste pochopili, jak přesný je model a zjistěte, jak ho použít k předpovědi hodnot tarif taxislužby.

### <a name="save-the-model"></a>Uložit model

V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain> , který je možné integrovat do všech existujících nebo nových aplikací .NET. Chcete-li uložit model do souboru .zip, přidejte následující kód na konci `Train` metody:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>Model uložit jako soubor ZIP

Vytvořte `SaveModelAsFile` metoda, hned za `Train` metodu, pomocí následujícího kódu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda spustí následující úlohy:

* Uloží modelu ve formě souboru .zip.

Potřebujeme vytvořit metodu ke uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích. `ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>. Protože chceme uložit jako soubor zip, vytvoříme `FileStream` bezprostředně před volání `SaveTo` metody. Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

Také jsme může zobrazit, kde soubor byl zapsán napsáním zprávu konzoly s `_modelPath`, pomocí následujícího kódu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Hodnocení je proces kontroly, jak dobře model předpovídá hodnoty popisků. Je důležité, že model vytváří dobré předpovědi na data, která nebyla použita pro trénování modelu. Jedním ze způsobů k tomu je rozdělení dat na trénovací a testovací datové sady, jak je tomu v tomto kurzu. Teď, když jsme natrénovali model na trénovací data, zobrazí se, jak dobře funguje na testovací data.

`Evaluate` Metoda vyhodnocuje modelu. Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metody:

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

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Zobrazí se nám načíst testovací datové sady, pomocí dříve inicializován `_textLoader` globální proměnné `_testDataPath` globální pole. Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality. Přidejte následující kód, který `Evaluate` metody:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

V dalším kroku použijeme strojového učení `model` parametr (transformace) pro vstup funkce a vrátí předpovědi. Přidejte následující kód, který `Evaluate` metody jako další řádek:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

`RegressionContext.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení regrese. Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první. Přidejte následující kód jako další řádek `Evaluate` metody:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů. RSquared trvá hodnoty v rozmezí 0 až 1. Čím blíž její hodnota je 1, tím lepší je model. Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model. Čím nižší je, tím lepší je model. Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Použít model pro předpovědi


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>Předpověď data výsledek testu s modelem a jednoho komentáře

Vytvořte `TestSinglePrediction` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

`TestSinglePrediction` Metoda spustí následující úlohy:

* Vytvoří jeden komentář testovací data.
* Předpovídá tarif velikost na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Protože chceme, aby načíst model ze souboru zip jsme předtím uložili, a My vytvoříme `FileStream` bezprostředně před volání `Load` metody. Přidejte následující kód, který `TestSinglePrediction` metody jako další řádek:

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí. <xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody. Přidejte následující kód k vytvoření `PredictionEngine` jako další řádek `TestSinglePrediction` metody:

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
Tento kurz používá jeden test latence v rámci této třídy. Později můžete přidat další scénáře můžete experimentovat s modelem. Přidat cestu k otestování předpovědi trénovaného modelu nákladů `TestSinglePrediction` metodu tak, že vytvoříte instanci `TaxiTrip`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 Který můžeme použít k predikci tarif založené na jednu instanci data o jízdách taxislužby. Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data. Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

K zobrazení předpokládané tarif zadané cesty, přidejte následující kód do `TestSinglePrediction` metody:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.

Blahopřejeme! Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště GitHub.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
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
