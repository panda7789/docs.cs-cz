---
title: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)
description: Další informace o použití ML.NET ve scénáři regrese.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9706dad0a8e32651496e0404be4501c2c70e9d75
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948628"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Kurz: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)

> [!NOTE]
> Toto téma označuje ML.NET, který je aktuálně ve verzi Preview, a materiálů, mohou se měnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz ukazuje, jak používat ML.NET pro vytváření [regresní model](../resources/glossary.md#regression) pro predikci tarify taxíkem New Yorku.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava a pochopení dat
> * Vytvoření kanálu učení
> * Načítání a transformace dat
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použití modelu předpovědi

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.

## <a name="understand-the-problem"></a>Pochopení problému

Tento problém je zaměřená na **predikci tarif služby taxíkem dojít v New Yorku**. Na první pohled se zdá se, že jednoduše na vzdálenost, kterou urazit závisí. Dodavatelé taxíkem v New Yorku však účtují různých objemy pro dalších faktorech, například další cestujících nebo platícího platební kartou místo peněžních.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

K předvídání taxíkem tarif, nejprve vyberte úlohu odpovídající machine learning. Hledáte k předvídání skutečná hodnota (dvojitou hodnotu představující cena) založená na jiných faktorech v datové sadě. Můžete vybrat [ **regrese** ](../resources/glossary.md#regression) úloh.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **soubor** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu. Vyberte **konzolové aplikace (.NET Core)** šablona projektu. V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář s názvem *Data* ve vašem projektu a ukládat soubory datové sady:

    V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Vyberte "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartě, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **zobrazení náhledu změn** dialogové okno a potom vyberte **souhlasím** na tlačítko **přijetí licence** dialogové okno Pokud jste souhlas s licenčními podmínkami pro balíčky uvedené.

## <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

1. Stáhnout [taxíkem. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxíkem. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data nastaví a uložte je do *Data* složky, které jste vytvořili v předchozím kroku. Používáme tyto sady dat a natrénuje strojového učení modelu a pak vyhodnotit, jak přesný je modelu. Tyto sady dat se původně z [NYC TLC taxíkem cestě datové sady](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. V **Průzkumníku řešení**, klikněte pravým tlačítkem na každý z \*soubory .csv a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu **kopírovat do výstupního adresáře** k **vždy**.

3. Otevřete **taxíkem. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všechny sloupce. Pochopení dat a rozhodněte, které sloupce jsou **funkce** a která je **popisek**.

**Popisek** je identifikátor sloupce, který chcete předpovědět. Identifikovanou **funkce** se používají k předvídání popisku.

Zadaná sada dat obsahuje následující sloupce:

* **vendor_id:** ID dodavatele, taxíkem je funkce.
* **rate_code:** typ míry taxíkem cesty je funkce.
* **passenger_count:** počet cestujících na cestu je funkce.
* **trip_time_in_secs:** trvalo množství času, cestu. Chcete předpovědět tarif cesty před dokončením cesty. V daném okamžiku by nevíte, jak dlouho bude cesta chvíli trvat. Proto času není funkce a budete v tomto sloupci vyloučíte z modelu.
* **trip_distance:** vzdálenost cesty je funkce.
* **payment_type:** platby (peněžních nebo platební karty) je funkce.
* **fare_amount:** tarif celkový taxíkem placené je popisek.

## <a name="create-data-classes"></a>Vytvořit datové třídy

Vytvoření třídy pro vstupní data a jsou předpovědi:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.
1. V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TaxiTrip.cs*. Pak vyberte **přidat** tlačítko.
1. Přidejte následující `using` direktivy na nový soubor:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, na *TaxiTrip.cs* souboru:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je třída vstupní data a obsahuje definice pro každý z datové sady sloupců. Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atribut k určení indexy zdrojové sloupce v datové sadě.

`TaxiTripFarePrediction` Třída se používá k reprezentování předpokládaných výsledky. Má jednou čárkou (`FareAmount`) pole s `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut použitý. **Skóre** sloupec je speciální sloupec v ML.NET. Model výstupy předpovězené hodnoty do sloupce.

## <a name="define-data-and-model-paths"></a>Definování dat a model cesty

Přejděte zpět *Program.cs* souboru a přidejte tři pole pro uložení cest k souborům s datových sad a soubor uložte modelu:

* `_datapath` obsahuje cestu k souboru s datovou sadou použity při cvičení modelu.
* `_testdatapath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.
* `_modelpath` obsahuje cestu k souboru, kde je uložený naučeného modelu.

Přidejte následující kód vpravo nahoře `Main` metoda k určení těchto cestách:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Chcete-li předchozí kód kompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>Vytvoření kanálu učení

Přidejte následující další `using` direktivy do horní části *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

V `Main`, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Metoda nastaví model. Vytvoření dané metody právě níže `Main`, pomocí následujícího kódu:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu. Přidejte následující kód do `Train` metoda:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Načítání a transformace dat

První krok, který provádí learning kanálu načítá data z trénovací datové sady. V našem případě trénovací datové sady je uložený v textovém souboru s cestou definované `_datapath` pole. Tento soubor obsahuje záhlaví s názvy sloupců, takže první řádek má ignorovat při načítání dat. Sloupce v souboru oddělených čárkou (","). Přidejte následující kód do `Train` metoda:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

V dalších krocích označujeme sloupce názvy definované v `TaxiTrip` třídy.

Když je model trénují a vyhodnocují, hodnoty **popisek** sloupce jsou považovány za jako správné hodnoty pro předpovědět. Jak chcete předpovídat tarif cestě taxi, zkopírujte `FareAmount` sloupce do **popisek** sloupce. Chcete-li provést, použijte <xref:Microsoft.ML.Transforms.ColumnCopier> a přidejte následující kód:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Algoritmus, která provede modelu vyžaduje **číselné** funkce, takže budete mít k transformaci kategorizovaná data (`VendorId`, `RateCode`, a `PaymentType`) hodnoty do čísla. Chcete-li provést, použijte <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, které přiřadí různé číselné hodnoty pro různé hodnoty v jednotlivých sloupců klíče a přidejte následující kód:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Poslední krok v rámci přípravy dat kombinuje všechny sloupce funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Transforms.ColumnConcatenator> třídy transformace. Tento krok je nezbytný, protože student zpracovává pouze funkce z **funkce** sloupce. Přidejte následující kód:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Všimněte si, že `TripTime` sloupec, který odpovídá `trip_time_in_secs` není zahrnutý sloupec v souboru datové sady. Již je třeba určit, že to není funkce užitečné předpovědi.

> [!NOTE]
> Tyto kroky je nutné přidat do tohoto kanálu v pořadí určeném výše pro úspěšné provedení.

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Po přidání dat do kanálu a transformace na správný formát vstupu, vyberte algoritmus učení (**Student**). Student soupravy modelu. Jste si zvolili **regrese úloh** pro tento problém, takže můžete přidat <xref:Microsoft.ML.Trainers.FastTreeRegressor> student, což je jedna ze regrese inteligentních algoritmů, poskytované ML.NET.

<xref:Microsoft.ML.Trainers.FastTreeRegressor> Student využívá přechodu zvyšovat skóre. Přechodu zvyšovat skóre je machine learning technika pro regresní problémy. Sestavuje každém stromu regrese step-wise způsobem. Předem definované ztrátě funkce používá k měření chyby v jednotlivých kroků a opravte ho v dalším. Výsledkem je předpovědi model, který je ve skutečnosti kompletu slabší předpovědi modelů. Další informace o přechodu zvyšovat skóre najdete v tématu [Boosted rozhodovací strom regrese](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Přidejte následující kód do `Train` metoda po zpracování dat kódu přidali v předchozím kroku:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale C# má syntaxi inicializace užitečný kolekce, která usnadňuje vytváření a inicializace kanálu. Nahraďte kód, který jste přidali, pokud na `Train` metoda následujícím kódem:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Trénování modelu

Posledním krokem je pro trénování modelu. Dokud nebude tento bod byl proveden nic v kanálu. `pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přebírá instanci `TInput` zadejte a výstupy instanci `TOutput` typu. Přidejte následující kód do `Train` metoda:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

A je to! Úspěšně jste Trénink machine learning model, který může předpovídat taxíkem tarify v NYC. Nyní Pojďme prohlédněte pochopit, jak přesný je model a zjistěte, jak ji použít k předpovědi hodnot tarif taxíkem.

### <a name="save-the-model"></a>Uložit model

Než přejdete na další krok, model uložte do souboru ZIP a přidáním následující kód na konci `Train` metoda:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Přidávání `await` příkaz, který má `model.WriteAsync` volání znamená, že `Train` metoda musí změnit tak, aby asynchronní metody, který vrátí úlohu. Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Změna návratový typ `Train` metoda znamená, že budete muset přidat `await` na kód, který volá `Train` v `Main` metoda, jak je znázorněno v následujícím kódu:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Pomocí `await` v `Main` metoda znamená `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Také je nutné přidat následující `using` direktivy v horní části souboru:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Protože `async Main` metoda je funkce přidané v C# 7.1 a je výchozí jazykovou verzi projektu C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější. To lze provést, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**. Vyberte **sestavení** a vyberte **Upřesnit** tlačítko. V rozevírací nabídce, a vyberte **C# 7.1** (nebo vyšší verze). Vyberte **OK** tlačítko.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Vyhodnocení je proces kontroly, jak dobře model předpovídá popisek hodnoty. Je důležité, aby model vytváří dobrý předpovědi na data, která nebyla použita pro trénování modelu. Jeden způsob, jak to udělat je rozdělení dat do vlaku a testování sad dat, jak se provádí v tomto kurzu. Teď, když jsme natrénovali model na základě dat train, se zobrazí její výkon na testovací data.

Přejděte zpět `Main` metoda a přidejte následující kód pod voláním `Train`metoda:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` Metoda vyhodnotí modelu. Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metoda:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Přidejte následující kód do `Evaluate` metodu za účelem instalace načítání testovacích dat:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Přidejte následující kód k vyhodnocení modelu a vytvořit metriku vyhodnocení:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z vyhodnocení metriky regresní model. Čím nižší je, tím lepší je model. Přidejte následující kód do `Evaluate` metodu pro zobrazení hodnota RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrika vyhodnocení modelů regrese. RSquared přijímá hodnoty mezi 0 a 1. Čím bližší její hodnota je 1, tím lepší je model. Přidejte následující kód do `Evaluate` metodu pro zobrazení RSquared hodnotu:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Použití modelu předpovědi

Dále vytvořte třídu úklidové testovací scénářů, které můžete použít a ujistěte se, že model pracuje správně:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.
1. V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TestTrips.cs*. Pak vyberte **přidat** tlačítko.
1. Upravte třídy, která má být statické jako v následujícím příkladu:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Tento kurz používá jeden testovací cesty v rámci této třídy. Později můžete přidat další scénáře a experimentovat s modelem. Přidejte následující kód do `TestTrips` třídy:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Tuto cestu skutečné tarif je 29.5. Model bude předpovídat tarif použijte jako zástupný znak, 0.

K předvídání tarif zadané cesty, přejděte zpět na *Program.cs* souboru a přidejte následující kód do `Main` metoda:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Spusťte program zobrazíte předpokládaných taxíkem tarif pro testovacího případu.

Blahopřejeme! Jste teď úspěšně sestaven model machine learning pro predikci taxíkem cestě tarify, vyhodnotit jeho přesnost a použít k předpovědi. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se dozvěděli, jak:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava a pochopení dat
> * Vytvoření kanálu učení
> * Načítání a transformace dat
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použití modelu předpovědi

Podívejte se na našem úložišti GitHub a pokračujte ve čtení najít další ukázky.
> [!div class="nextstepaction"]
> [úložiště GitHub DotNet/machinelearning](https://github.com/dotnet/machinelearning/)
