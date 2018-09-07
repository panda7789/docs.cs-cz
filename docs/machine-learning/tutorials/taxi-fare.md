---
title: ML.NET používají k vytváření prognóz tarify taxislužby města New York (regrese)
description: Další informace o použití ML.NET ve scénáři regrese.
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 133b7ad17a98e4eea510f1704555b690b98e9091
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079799"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Kurz: Použití ML.NET předpovědět tarify taxislužby města New York (regrese)

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz ukazuje, jak použít ML.NET k sestavení [regresní model](../resources/glossary.md#regression) pro predikci tarify taxislužby města New York City.

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

* **vendor_id:** ID dodavatele, taxi je funkce.
* **rate_code:** typ kursu cesty taxíkem je funkce.
* **passenger_count:** počet cestujících na cestě je funkce.
* **trip_time_in_secs:** trvalo cesty časového intervalu. Chcete předpovědět tarif cesty před dokončením cesty. V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách. Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.
* **trip_distance:** vzdálenost cesty je funkce.
* **payment_type:** platby (hotovosti nebo kreditní karta) je funkce.
* **fare_amount:** tarif celkový taxislužby placené je popisek.

## <a name="create-data-classes"></a>Vytvoření datových tříd

Vytvoření třídy pro vstupní data a předpovědí:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TaxiTrip.cs*. Vyberte **přidat** tlačítko.
1. Přidejte následující `using` direktivy do nového souboru:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` je třída vstupní data a obsahuje definice pro všechny sloupce datové sady. Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atributy indexů zdrojových sloupců v datové sadě.

`TaxiTripFarePrediction` Třída reprezentuje předpokládané výsledky. Obsahuje pole jednou čárkou `FareAmount`, s `Score` [Názevsloupce](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut. V případě úloh regrese **skóre** sloupec obsahuje hodnoty předpovězené popisků.

> [!NOTE]
> Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.

## <a name="define-data-and-model-paths"></a>Definovat cesty k datům a model

Přejděte zpět *Program.cs* a přidejte tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu:

* `_datapath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.
* `_testdatapath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.
* `_modelpath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.

Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>Vytvoření kanálu učení

Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

V `Main` metoda, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Metoda trénovat modelu. Vytvoření metody hned pod `Main`, pomocí následujícího kódu:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu. Přidejte následující kód do `Train` metody:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Načítání a transformace dat.

Prvním krokem k provedení je k načtení dat z trénovací datové sady. V našem případě trénovací datové sady se ukládají v textovém souboru s cestu definovanou `_datapath` pole. Tento soubor má záhlaví s názvy sloupců, takže první řádek by měl ignorovat při načítání dat. Sloupce v souboru jsou oddělené čárkou (","). Přidejte následující kód do `Train` metody:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

V dalších krocích budeme odkazovat na sloupce pomocí názvy definované v `TaxiTrip` třídy.

Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat. Protože chceme předpovědět tarif cesty taxíkem, zkopírujte `FareAmount` sloupec **popisek** sloupec. K tomuto účelu použijte <xref:Microsoft.ML.Transforms.ColumnCopier> a přidejte následující kód:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla. K tomuto účelu použijte <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Transforms.ColumnConcatenator> třídy transformace. Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce. Přidejte následující kód:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Všimněte si, že `TripTime` sloupec, který odpovídá `trip_time_in_secs` sloupec v souboru datové sady není zahrnut. Už jste zjistili, že to není užitečné předpovědi funkce.

> [!NOTE]
> Tyto kroky je nutné přidat do kanálu v pořadí určeném výše pro úspěšné provedení.

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vyberte algoritmus učení (**learner**). Learner trénovat modelu. Jste si zvolili **regrese** úkol pro tento problém, proto použijete <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, což je jedna studentů regrese poskytované ML.NET.

<xref:Microsoft.ML.Trainers.FastTreeRegressor> learner využívá přechodu zvýšení skóre. Přechodu zvýšení skóre je strojové učení techniku pro regresní problémy. Sestaví každém stromu regrese způsobem podle jednotlivých kroků. Předdefinované ztráta funkce používá k měření chyb v každém kroku a opravit ho v dalším. Výsledkem je, který je ve skutečnosti kompletu sady slabší prediktivní modely prediktivní model. Další informace o přechodu zvýšení skóre, naleznete v tématu [Boosted regrese rozhodovacího stromu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Přidejte následující kód do `Train` metoda po zpracování dat kód přidaný v předchozím kroku:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale jazyka C# má syntaxe inicializace kolekce po ruce, který usnadňuje vytváření a inicializace kanálu. Nahraďte kód přidaný zatím na `Train` metodu s následujícím kódem:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Trénování modelu

Posledním krokem je pro trénování modelu. Až do této chvíle byl proveden nic v kanálu. `pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přijímá instanci `TInput` zadejte a vypíše instance `TOutput` typu. Přidejte následující kód do `Train` metody:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

A to je všechno! Úspěšně jste trénuje model, který může předpovídat tarify taxislužby města v NYC strojového učení. Nyní Pojďme podívat, abyste pochopili, jak přesný je model a zjistěte, jak ho použít k předpovědi hodnot tarif taxislužby.

### <a name="save-the-model"></a>Uložit model

V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET. Chcete-li uložit model do souboru .zip, přidejte následující kód na konci `Train` metody:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Přidávání `await` příkazu `model.WriteAsync` volání znamená, že `Train` metoda musí být změněna na asynchronní metoda vracející úlohu. Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Změna návratového typu `Train` metoda znamená, že chcete přidat `await` kódu, který volá `Train` v `Main` způsob, jak je znázorněno v následujícím kódu:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Pomocí `await` v `Main` znamená, že metoda `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Budete také muset přidat následující `using` direktiv v horní části souboru:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Vzhledem k tomu, `async Main` metoda je funkce přidané v jazyce C# 7.1 a výchozí jazyková verze projektu je C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější. Chcete-li to mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**. Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze). Vyberte **OK** tlačítko.

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Hodnocení je proces kontroly, jak dobře model předpovídá hodnoty popisků. Je důležité, že model vytváří dobré předpovědi na data, která nebyla použita pro trénování modelu. Jedním ze způsobů k tomu je rozdělení dat na trénovací a testovací datové sady, jak je tomu v tomto kurzu. Teď, když jsme natrénovali model na trénovací data, zobrazí se, jak dobře funguje na testovací data.

Přejděte zpět `Main` metoda a přidejte následující kód pod volání `Train`– metoda:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` Metoda vyhodnocuje modelu. Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metody:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Přidejte následující kód do `Evaluate` metodu pro nastavení načítání testovacích dat:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model. Čím nižší je, tím lepší je model. Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů. RSquared trvá hodnoty v rozmezí 0 až 1. Čím blíž její hodnota je 1, tím lepší je model. Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Použít model pro předpovědi

Vytvoření třídy, která porušuje testovací data instancí:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.
1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestTrips.cs*. Vyberte **přidat** tlačítko.
1. Upravte třídu pro statické stejně jako v následujícím příkladu:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Tento kurz používá jeden test latence v rámci této třídy. Později můžete přidat další scénáře můžete experimentovat s modelem. Přidejte následující kód do `TestTrips` třídy:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Tuto cestu skutečné tarif je 29,5. Model bude předpovídat tarif, použijte jako zástupný znak, 0.

Pokud chcete předpovědět tarif zadané cesty, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.

Blahopřejeme! Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště GitHub.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak:
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
