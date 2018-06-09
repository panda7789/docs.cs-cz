---
title: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)
description: Další informace o použití ML.NET ve scénáři regrese.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "35017278"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Kurz: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)

> [!NOTE]
> Toto téma označuje ML.NET, který je aktuálně ve verzi Preview, a materiálů, mohou se měnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz ukazuje, jak používat ML.NET pro vytváření [regresní model](../resources/glossary.md#regression) pro predikci tarify taxíkem New Yorku.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava a pochopit vaše data
> * Vytvoření kanálu učení
> * Načítání a transformace dat
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použití modelu předpovědi

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,6 nebo novější](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.

## <a name="understand-the-problem"></a>Pochopení problému

Tento problém je zaměřená na **predikci tarif služby taxíkem dojít v New Yorku**. Na první pohled se zdá se, že jednoduše na vzdálenost, kterou urazit závisí. Dodavatelé taxíkem v New Yorku však účtují různých objemy pro dalších faktorech, například další cestujících nebo platícího platební kartou místo peněžních.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

K předvídání taxíkem tarif, nejprve vyberte úlohu odpovídající machine learning. Hledáte k předvídání skutečná hodnota (dvojitou hodnotu představující cena) založená na jiných faktorech v datové sadě. Můžete vybrat [ **regrese** ](../resources/glossary.md#regression) úloh.

Proces tréninku modelu identifikuje předpověď ceny konečné tarif jsou nejvíce vliv faktory, které v datové sadě.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **soubor** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu. Vyberte **konzolové aplikace (.NET Core)** šablona projektu. V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář s názvem *Data* ve vašem projektu a uložte si své soubory datové sady:

    V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, vyhledávat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **zobrazení náhledu změn** dialogové okno a potom vyberte **souhlasím** na tlačítko **přijetí licence** dialogové okno Pokud jste souhlas s licenčními podmínkami pro balíčky uvedené.

### <a name="prepare-and-understand-your-data"></a>Příprava a pochopit vaše data

1. Stáhnout [taxíkem. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxíkem. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data nastaví a uložte je do *Data* složku dříve vytvořili. Sada dat taxíkem cestě nastaví model strojového učení a slouží k vyhodnocení, jak přesný je váš model. Tyto sady dat se původně z [NYC TLC taxíkem cestě datové sady](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. V Průzkumníku řešení klikněte pravým tlačítkem na každý z \*soubory .csv a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu **kopírovat do výstupního adresáře** k **vždy**.

3. Otevřete **taxíkem. tarif train.csv** data nastavují v editoru kódu a podívejte se na záhlaví sloupců v prvním řádku. Podívejte se na všechny sloupce. Pochopení dat a rozhodněte, které sloupce jsou **funkce** a který je **popisek**.

**Popisek** je identifikátor sloupce, který chcete předpovědět. Identifikovanou **funkce** se používají k předvídání popisku.

* **vendor_id:** ID dodavatele, taxíkem je funkce.
* **rate_code:** typ míry taxíkem cesty je funkce.
* **passenger_count:** počet cestujících na cestu je funkce.
* **trip_time_in_secs:** trvalo množství času, cestu. Nebude vědět, jak dlouho bude cesta trvá až po jeho dokončení. V tomto sloupci vyloučíte z modelu.
* **trip_distance:** vzdálenost cesty je funkce.
* **payment_type:** platby (peněžních nebo platební karty) je funkce.
* **fare_amount:** tarif celkový taxíkem placené je popisek.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazů do horní části *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Potřebujete vytvořit tři globální proměnné pro uložení cest k naposledy stažené soubory a uložte modelu:

* `_datapath` obsahuje cestu k datům používá pro trénování modelu.
* `_testdatapath` obsahuje cestu k datům používá k vyhodnocení modelu.
* `_modelpath` má cestu k uložení naučeného modelu.

Přidejte následující kód řádku vpravo nahoře `Main` k určení naposledy stažené soubory:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Dále vytvořte třídy pro vstupní data a jsou předpovědi:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.
1. V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TaxiTrip.cs*. Pak vyberte **přidat** tlačítko.
1. Přidejte následující `using` příkazy na nový soubor:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, na *TaxiTrip.cs* souboru:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je třída vstupní datové sady a obsahuje definice pro každý z datové sady sloupců. `TaxiTripFarePrediction` Třída se používá pro předpověď po modelu má cvičena. Má jednou čárkou (`FareAmount`) a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut použitý.

Nyní přejděte zpět **Program.cs** souboru. V `Main`, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Metoda soupravy modelu. Vytvoření této funkce právě níže `Main`, pomocí následujícího kódu:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a>Vytvoření kanálu učení

Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu. Přidejte následující kód do `Train()` metoda:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a>Načítání a transformace dat

V dalším kroku načtěte data do kanálu. Přejděte `_datapath` původně vytvořili, a určete oddělovač souboru CSV (,). Přidejte následující kód do `Train()` pod poslední krok:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

Budete odkazovat na sloupce bez podtržítka v kódu, kterou vytváříte. Kopírování `FareAmount` sloupce do nového sloupce názvem "Popis" pomocí `ColumnCopier()` funkce. Je tento sloupec **popisek**.

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Provedení některých **konstruování** pro transformaci dat, aby se můžete efektivně použít pro machine learning. Algoritmus, která provede modelu vyžaduje **číselné** funkce transformace kategorizovaná data (`VendorId`, `RateCode`, a `PaymentType`) do čísla. `CategoricalOneHotVectorizer()` Funkce přiřadí číselné klíče na hodnoty v jednotlivých sloupců. Transformace dat tak, že přidáte tento kód:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Poslední krok v rámci přípravy dat kombinuje všechny vaše **funkce** do jednoho pomocí vektoru `ColumnConcatenator()` funkce. Tento krok nezbytné vám pomůže snadno zpracovat vaše funkce algoritmus. Přidejte následující kód:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Všimněte si, že `trip_time_in_secs` sloupec není součástí. Již je třeba určit, že to není funkce užitečné předpovědi.

> [!NOTE]
> Tyto kroky je nutné přidat do kanálu v pořadí určeném výše pro úspěšné provedení.

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Po přidání dat do kanálu a transformace na správný formát vstupu, vyberte algoritmus učení (**Student**). Algoritmus učení soupravy modelu. Jste si zvolili **regrese úloh** pro tento problém, takže přidáte student názvem `FastTreeRegressor()` do kanálu, který využívá **přechodu zvyšovat skóre**.

Přechodu zvyšovat skóre je machine learning technika pro regresní problémy. Sestavuje každém stromu regrese step-wise způsobem. Předem definované ztrátě funkce používá k měření chyby v jednotlivých kroků a opravte ho v dalším. Výsledkem je předpovědi model, který je ve skutečnosti kompletu slabší předpovědi modelů. Další informace o přechodu zvyšovat skóre najdete v tématu [Boosted rozhodovací strom regrese](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Přidejte následující kód do `Train()` metoda po zpracování dat kódu přidali v posledním kroku:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale C# má syntaxi inicializace užitečný kolekce, která usnadňuje vytváření a inicializace kanálu. Nahraďte kód, který jste přidali, pokud na `Train()` metoda následujícím kódem:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Trénování modelu

Posledním krokem je pro trénování modelu. Dokud nebude tento bod byl proveden nic v kanálu. `pipeline.Train<T_Input, T_Output>()` Funkce přebírá předem definované `TaxiTrip` typu třídy a výstupy `TaxiTripFarePrediction` typu. Přidejte tento poslední část kódu do `Train()` funkce:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

A je to! Úspěšně jste Trénink machine learning model, který může předpovídat taxíkem tarify v NYC. Nyní si je můžete prohlédnout pochopit, jak přesný je váš model a zjistěte, jak ho zpracovat.

## <a name="save-the-model"></a>Uložit model

Než přejdete na další krok, uložte modelu do souboru ZIP a přidáním následující kód na konci vaší `Train()` funkce:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Přidávání `await` příkaz, který má `model.WriteAsync()` volání znamená, že `Train()` metoda musí změnit tak, aby asynchronní metody, která vrací `Task`. Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Změna návratový typ `Train` metoda znamená, že budete muset přidat `await` na kód, který volá `Train` v `Main` metoda, jak je znázorněno v následujícím kódu:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Přidání `await` ve vaší `Main` metoda znamená `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Také je nutné přidat následující pomocí příkazu v horní části souboru:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Protože `async Main` metoda je nová funkce v C# 7.1 a je výchozí jazykovou verzi projektu C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.
To lze provést, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**. Vyberte **sestavení** a vyberte **Upřesnit** tlačítko. V rozevírací nabídce, a vyberte **C# 7.1** (nebo vyšší verze). Vyberte **OK** tlačítko.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Vyhodnocení je proces kontroly, jak dobře model funguje. Je důležité, že váš model vytváří dobrý předpovědi na data, která nepoužili, když byla cvičení. Jeden ze způsobů, jak provést toto je rozdělením data do vlaku a testovací datové sady, jako jste to udělali v tomto kurzu. Teď, když jsme natrénovali model na základě dat train, se zobrazí její výkon na testovací data.

Přejděte zpět na vaše `Main` funkce a přidejte následující kód pod voláním `Train()`metoda:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate()` Funkce vyhodnotí modelu. Vytvoření této funkce níže `Train()`. Přidejte následující kód:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Načtení dat pomocí testu `TextLoader()` funkce. Přidejte následující kód do `Evaluate()` metoda:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Přidejte následující kód k vyhodnocení modelu a vytvoření metriky pro ni:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

RMS je jedna Metrika pro vyhodnocení regrese problémy. Čím nižší je, tím lépe modelu. Přidejte následující kód do `Evaluate()` funkce Tisknout služby RMS pro váš model.

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

RSquared je jiné metriky pro vyhodnocení regrese problémy. RSquared bude mít hodnotu mezi 0 a 1. Čím bližší jste hodnotu 1, tím lépe modelu. Přidejte následující kód do `Evaluate()` funkce Tisknout RSquared hodnota modelu.

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Použití modelu předpovědi

Dále vytvořte třídu úklidové testovací scénářů, které můžete použít a ujistěte se, že váš model pracuje správně:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.
1. V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TestTrips.cs*. Pak vyberte **přidat** tlačítko.
1. Upravte třídy, která má být statické jako v následujícím příkladu:

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Tento kurz používá jeden testovací cesty v rámci této třídy. Později můžete přidat další scénáře a experimentovat s této ukázce. Přidejte následující kód do `TestTrips` třídy:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Tuto cestu skutečné tarif je 29.5, ale jako zástupný znak, použijte hodnotu 0. Algoritmu strojového učení se předvídání tarif.

Přidejte následující kód ve vaší `Main` funkce. Testuje se váš model pomocí `TestTrip` dat:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Spusťte program zobrazíte předpokládaných taxíkem tarif pro testovacího případu.

Blahopřejeme! Jste teď úspěšně sestaven model machine learning pro predikci taxíkem tarify, vyhodnotit jeho přesnost a otestovat ho. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se dozvěděli, jak:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava a pochopit vaše data
> * Vytvoření kanálu učení
> * Načítání a transformace dat
> * Vyberte algoritmus učení
> * Trénování modelu
> * Vyhodnocení modelu
> * Použití modelu předpovědi

Podívejte se na našem úložišti GitHub a pokračujte ve čtení najít další ukázky.
> [!div class="nextstepaction"]
> [úložiště GitHub DotNet/machinelearning](https://github.com/dotnet/machinelearning/)
