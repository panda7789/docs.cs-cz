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
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="f6780-103">Kurz: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)</span><span class="sxs-lookup"><span data-stu-id="f6780-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="f6780-104">Toto téma označuje ML.NET, který je aktuálně ve verzi Preview, a materiálů, mohou se měnit.</span><span class="sxs-lookup"><span data-stu-id="f6780-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f6780-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f6780-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f6780-106">Tento kurz ukazuje, jak používat ML.NET pro vytváření [regresní model](../resources/glossary.md#regression) pro predikci tarify taxíkem New Yorku.</span><span class="sxs-lookup"><span data-stu-id="f6780-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="f6780-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="f6780-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f6780-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="f6780-108">Understand the problem</span></span>
> * <span data-ttu-id="f6780-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="f6780-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="f6780-110">Příprava a pochopit vaše data</span><span class="sxs-lookup"><span data-stu-id="f6780-110">Prepare and understand your data</span></span>
> * <span data-ttu-id="f6780-111">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="f6780-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="f6780-112">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="f6780-112">Load and transform your data</span></span>
> * <span data-ttu-id="f6780-113">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="f6780-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="f6780-114">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="f6780-114">Train the model</span></span>
> * <span data-ttu-id="f6780-115">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="f6780-115">Evaluate the model</span></span>
> * <span data-ttu-id="f6780-116">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="f6780-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6780-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6780-117">Prerequisites</span></span>

* <span data-ttu-id="f6780-118">[Visual Studio 2017 15,6 nebo novější](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.</span><span class="sxs-lookup"><span data-stu-id="f6780-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="f6780-119">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="f6780-119">Understand the problem</span></span>

<span data-ttu-id="f6780-120">Tento problém je zaměřená na **predikci tarif služby taxíkem dojít v New Yorku**.</span><span class="sxs-lookup"><span data-stu-id="f6780-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="f6780-121">Na první pohled se zdá se, že jednoduše na vzdálenost, kterou urazit závisí.</span><span class="sxs-lookup"><span data-stu-id="f6780-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="f6780-122">Dodavatelé taxíkem v New Yorku však účtují různých objemy pro dalších faktorech, například další cestujících nebo platícího platební kartou místo peněžních.</span><span class="sxs-lookup"><span data-stu-id="f6780-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="f6780-123">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="f6780-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="f6780-124">K předvídání taxíkem tarif, nejprve vyberte úlohu odpovídající machine learning.</span><span class="sxs-lookup"><span data-stu-id="f6780-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="f6780-125">Hledáte k předvídání skutečná hodnota (dvojitou hodnotu představující cena) založená na jiných faktorech v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="f6780-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="f6780-126">Můžete vybrat [ **regrese** ](../resources/glossary.md#regression) úloh.</span><span class="sxs-lookup"><span data-stu-id="f6780-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

<span data-ttu-id="f6780-127">Proces tréninku modelu identifikuje předpověď ceny konečné tarif jsou nejvíce vliv faktory, které v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="f6780-127">The process of training the model identifies which factors in the dataset are most influential when predicting the final fare price.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f6780-128">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="f6780-128">Create a console application</span></span>

1. <span data-ttu-id="f6780-129">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f6780-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="f6780-130">Vyberte **soubor** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="f6780-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="f6780-131">V **nový projekt** dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="f6780-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="f6780-132">Vyberte **konzolové aplikace (.NET Core)** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="f6780-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="f6780-133">V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f6780-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="f6780-134">Vytvořte adresář s názvem *Data* ve vašem projektu a uložte si své soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="f6780-134">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="f6780-135">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="f6780-135">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f6780-136">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="f6780-136">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="f6780-137">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="f6780-137">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f6780-138">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f6780-138">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f6780-139">Zvolte "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, vyhledávat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f6780-139">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="f6780-140">Vyberte **OK** tlačítko **zobrazení náhledu změn** dialogové okno a potom vyberte **souhlasím** na tlačítko **přijetí licence** dialogové okno Pokud jste souhlas s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="f6780-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-and-understand-your-data"></a><span data-ttu-id="f6780-141">Příprava a pochopit vaše data</span><span class="sxs-lookup"><span data-stu-id="f6780-141">Prepare and understand your data</span></span>

1. <span data-ttu-id="f6780-142">Stáhnout [taxíkem. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxíkem. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data nastaví a uložte je do *Data* složku dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="f6780-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="f6780-143">Sada dat taxíkem cestě nastaví model strojového učení a slouží k vyhodnocení, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="f6780-143">The Taxi Trip data set trains the machine learning model and can be used to evaluate how accurate your model is.</span></span> <span data-ttu-id="f6780-144">Tyto sady dat se původně z [NYC TLC taxíkem cestě datové sady](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="f6780-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="f6780-145">V Průzkumníku řešení klikněte pravým tlačítkem na každý z \*soubory .csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f6780-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="f6780-146">V části **Upřesnit**, změňte hodnotu **kopírovat do výstupního adresáře** k **vždy**.</span><span class="sxs-lookup"><span data-stu-id="f6780-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="f6780-147">Otevřete **taxíkem. tarif train.csv** data nastavují v editoru kódu a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="f6780-147">Open the **taxi-fare-train.csv** data set in the code editor and look at column headers in the first row.</span></span> <span data-ttu-id="f6780-148">Podívejte se na všechny sloupce.</span><span class="sxs-lookup"><span data-stu-id="f6780-148">Take a look at each of the columns.</span></span> <span data-ttu-id="f6780-149">Pochopení dat a rozhodněte, které sloupce jsou **funkce** a který je **popisek**.</span><span class="sxs-lookup"><span data-stu-id="f6780-149">Understand the data and decide which columns are **features** and which is the **label**.</span></span>

<span data-ttu-id="f6780-150">**Popisek** je identifikátor sloupce, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="f6780-150">The **label** is the identifier of the column you are trying to predict.</span></span> <span data-ttu-id="f6780-151">Identifikovanou **funkce** se používají k předvídání popisku.</span><span class="sxs-lookup"><span data-stu-id="f6780-151">The identified **features** are used to predict the label.</span></span>

* <span data-ttu-id="f6780-152">**vendor_id:** ID dodavatele, taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="f6780-153">**rate_code:** typ míry taxíkem cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="f6780-154">**passenger_count:** počet cestujících na cestu je funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="f6780-155">**trip_time_in_secs:** trvalo množství času, cestu.</span><span class="sxs-lookup"><span data-stu-id="f6780-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="f6780-156">Nebude vědět, jak dlouho bude cesta trvá až po jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="f6780-156">You won't know how long the trip takes until after it is completed.</span></span> <span data-ttu-id="f6780-157">V tomto sloupci vyloučíte z modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-157">You exclude this column from the model.</span></span>
* <span data-ttu-id="f6780-158">**trip_distance:** vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="f6780-159">**payment_type:** platby (peněžních nebo platební karty) je funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="f6780-160">**fare_amount:** tarif celkový taxíkem placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="f6780-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f6780-161">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="f6780-161">Create classes and define paths</span></span>

<span data-ttu-id="f6780-162">Přidejte následující další `using` příkazů do horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="f6780-162">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="f6780-163">Potřebujete vytvořit tři globální proměnné pro uložení cest k naposledy stažené soubory a uložte modelu:</span><span class="sxs-lookup"><span data-stu-id="f6780-163">You need to create three global variables to hold the paths to the recently downloaded files and to save the model:</span></span>

* <span data-ttu-id="f6780-164">`_datapath` obsahuje cestu k datům používá pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-164">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="f6780-165">`_testdatapath` obsahuje cestu k datům používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-165">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="f6780-166">`_modelpath` má cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-166">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="f6780-167">Přidejte následující kód řádku vpravo nahoře `Main` k určení naposledy stažené soubory:</span><span class="sxs-lookup"><span data-stu-id="f6780-167">Add the following code to the line right above `Main` to specify the recently downloaded files:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="f6780-168">Dále vytvořte třídy pro vstupní data a jsou předpovědi:</span><span class="sxs-lookup"><span data-stu-id="f6780-168">Next, create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="f6780-169">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f6780-169">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f6780-170">V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="f6780-170">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="f6780-171">Pak vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f6780-171">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="f6780-172">Přidejte následující `using` příkazy na nový soubor:</span><span class="sxs-lookup"><span data-stu-id="f6780-172">Add the following `using` statements to the new file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="f6780-173">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, na *TaxiTrip.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="f6780-173">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="f6780-174">`TaxiTrip` je třída vstupní datové sady a obsahuje definice pro každý z datové sady sloupců.</span><span class="sxs-lookup"><span data-stu-id="f6780-174">`TaxiTrip` is the input data set class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="f6780-175">`TaxiTripFarePrediction` Třída se používá pro předpověď po modelu má cvičena.</span><span class="sxs-lookup"><span data-stu-id="f6780-175">The `TaxiTripFarePrediction` class is used for prediction after the model has been trained.</span></span> <span data-ttu-id="f6780-176">Má jednou čárkou (`FareAmount`) a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut použitý.</span><span class="sxs-lookup"><span data-stu-id="f6780-176">It has a single float (`FareAmount`) and a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span>

<span data-ttu-id="f6780-177">Nyní přejděte zpět **Program.cs** souboru.</span><span class="sxs-lookup"><span data-stu-id="f6780-177">Now go back to the **Program.cs** file.</span></span> <span data-ttu-id="f6780-178">V `Main`, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="f6780-178">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="f6780-179">`Train` Metoda soupravy modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-179">The `Train` method trains your model.</span></span> <span data-ttu-id="f6780-180">Vytvoření této funkce právě níže `Main`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="f6780-180">Create that function just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="f6780-181">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="f6780-181">Create a learning pipeline</span></span>

<span data-ttu-id="f6780-182">Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-182">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="f6780-183">Přidejte následující kód do `Train()` metoda:</span><span class="sxs-lookup"><span data-stu-id="f6780-183">Add the following code into the `Train()` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a><span data-ttu-id="f6780-184">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="f6780-184">Load and transform your data</span></span>

<span data-ttu-id="f6780-185">V dalším kroku načtěte data do kanálu.</span><span class="sxs-lookup"><span data-stu-id="f6780-185">Next, load your data into the pipeline.</span></span> <span data-ttu-id="f6780-186">Přejděte `_datapath` původně vytvořili, a určete oddělovač souboru CSV (,).</span><span class="sxs-lookup"><span data-stu-id="f6780-186">Point to the `_datapath` created initially and specify the delimiter of the .csv file (,).</span></span> <span data-ttu-id="f6780-187">Přidejte následující kód do `Train()` pod poslední krok:</span><span class="sxs-lookup"><span data-stu-id="f6780-187">Add the following code into the `Train()` method underneath the last step:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

<span data-ttu-id="f6780-188">Budete odkazovat na sloupce bez podtržítka v kódu, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="f6780-188">You'll refer to the columns without the underscores in the code you're creating.</span></span> <span data-ttu-id="f6780-189">Kopírování `FareAmount` sloupce do nového sloupce názvem "Popis" pomocí `ColumnCopier()` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-189">Copy the `FareAmount` column into a new column called "Label" using the `ColumnCopier()` function.</span></span> <span data-ttu-id="f6780-190">Je tento sloupec **popisek**.</span><span class="sxs-lookup"><span data-stu-id="f6780-190">This column is the **Label**.</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="f6780-191">Provedení některých **konstruování** pro transformaci dat, aby se můžete efektivně použít pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="f6780-191">Conduct some **feature engineering** to transform the data so that it can be used effectively for machine learning.</span></span> <span data-ttu-id="f6780-192">Algoritmus, která provede modelu vyžaduje **číselné** funkce transformace kategorizovaná data (`VendorId`, `RateCode`, a `PaymentType`) do čísla.</span><span class="sxs-lookup"><span data-stu-id="f6780-192">The algorithm that trains the model requires **numeric** features, you transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) into numbers.</span></span> <span data-ttu-id="f6780-193">`CategoricalOneHotVectorizer()` Funkce přiřadí číselné klíče na hodnoty v jednotlivých sloupců.</span><span class="sxs-lookup"><span data-stu-id="f6780-193">The `CategoricalOneHotVectorizer()` function assigns a numeric key to the values in each of these columns.</span></span> <span data-ttu-id="f6780-194">Transformace dat tak, že přidáte tento kód:</span><span class="sxs-lookup"><span data-stu-id="f6780-194">Transform your data by adding this code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="f6780-195">Poslední krok v rámci přípravy dat kombinuje všechny vaše **funkce** do jednoho pomocí vektoru `ColumnConcatenator()` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-195">The last step in data preparation combines all of your **features** into one vector using the `ColumnConcatenator()` function.</span></span> <span data-ttu-id="f6780-196">Tento krok nezbytné vám pomůže snadno zpracovat vaše funkce algoritmus.</span><span class="sxs-lookup"><span data-stu-id="f6780-196">This necessary step helps the algorithm easily process your features.</span></span> <span data-ttu-id="f6780-197">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f6780-197">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="f6780-198">Všimněte si, že `trip_time_in_secs` sloupec není součástí.</span><span class="sxs-lookup"><span data-stu-id="f6780-198">Notice that the `trip_time_in_secs` column isn't included.</span></span> <span data-ttu-id="f6780-199">Již je třeba určit, že to není funkce užitečné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="f6780-199">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="f6780-200">Tyto kroky je nutné přidat do kanálu v pořadí určeném výše pro úspěšné provedení.</span><span class="sxs-lookup"><span data-stu-id="f6780-200">These steps must be added to Pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="f6780-201">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="f6780-201">Choose a learning algorithm</span></span>

<span data-ttu-id="f6780-202">Po přidání dat do kanálu a transformace na správný formát vstupu, vyberte algoritmus učení (**Student**).</span><span class="sxs-lookup"><span data-stu-id="f6780-202">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="f6780-203">Algoritmus učení soupravy modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-203">The learning algorithm trains the model.</span></span> <span data-ttu-id="f6780-204">Jste si zvolili **regrese úloh** pro tento problém, takže přidáte student názvem `FastTreeRegressor()` do kanálu, který využívá **přechodu zvyšovat skóre**.</span><span class="sxs-lookup"><span data-stu-id="f6780-204">You chose a **regression task** for this problem, so you add a learner called `FastTreeRegressor()` to the pipeline that utilizes **gradient boosting**.</span></span>

<span data-ttu-id="f6780-205">Přechodu zvyšovat skóre je machine learning technika pro regresní problémy.</span><span class="sxs-lookup"><span data-stu-id="f6780-205">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="f6780-206">Sestavuje každém stromu regrese step-wise způsobem.</span><span class="sxs-lookup"><span data-stu-id="f6780-206">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="f6780-207">Předem definované ztrátě funkce používá k měření chyby v jednotlivých kroků a opravte ho v dalším.</span><span class="sxs-lookup"><span data-stu-id="f6780-207">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="f6780-208">Výsledkem je předpovědi model, který je ve skutečnosti kompletu slabší předpovědi modelů.</span><span class="sxs-lookup"><span data-stu-id="f6780-208">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="f6780-209">Další informace o přechodu zvyšovat skóre najdete v tématu [Boosted rozhodovací strom regrese](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="f6780-209">For more information about gradient boosting, see [Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="f6780-210">Přidejte následující kód do `Train()` metoda po zpracování dat kódu přidali v posledním kroku:</span><span class="sxs-lookup"><span data-stu-id="f6780-210">Add the following code into the `Train()` method following the data processing code added in the last step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="f6780-211">Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale C# má syntaxi inicializace užitečný kolekce, která usnadňuje vytváření a inicializace kanálu.</span><span class="sxs-lookup"><span data-stu-id="f6780-211">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="f6780-212">Nahraďte kód, který jste přidali, pokud na `Train()` metoda následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="f6780-212">Replace the code you added so far to the `Train()` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="f6780-213">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="f6780-213">Train the model</span></span>

<span data-ttu-id="f6780-214">Posledním krokem je pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-214">The final step is to train the model.</span></span> <span data-ttu-id="f6780-215">Dokud nebude tento bod byl proveden nic v kanálu.</span><span class="sxs-lookup"><span data-stu-id="f6780-215">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="f6780-216">`pipeline.Train<T_Input, T_Output>()` Funkce přebírá předem definované `TaxiTrip` typu třídy a výstupy `TaxiTripFarePrediction` typu.</span><span class="sxs-lookup"><span data-stu-id="f6780-216">The `pipeline.Train<T_Input, T_Output>()` function takes in the pre-defined `TaxiTrip` class type and outputs a `TaxiTripFarePrediction` type.</span></span> <span data-ttu-id="f6780-217">Přidejte tento poslední část kódu do `Train()` funkce:</span><span class="sxs-lookup"><span data-stu-id="f6780-217">Add this final piece of code into the `Train()` function:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="f6780-218">A je to!</span><span class="sxs-lookup"><span data-stu-id="f6780-218">And that's it!</span></span> <span data-ttu-id="f6780-219">Úspěšně jste Trénink machine learning model, který může předpovídat taxíkem tarify v NYC.</span><span class="sxs-lookup"><span data-stu-id="f6780-219">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="f6780-220">Nyní si je můžete prohlédnout pochopit, jak přesný je váš model a zjistěte, jak ho zpracovat.</span><span class="sxs-lookup"><span data-stu-id="f6780-220">Now take a look to understand how accurate your model is and learn how to consume it.</span></span>

## <a name="save-the-model"></a><span data-ttu-id="f6780-221">Uložit model</span><span class="sxs-lookup"><span data-stu-id="f6780-221">Save the model</span></span>

<span data-ttu-id="f6780-222">Než přejdete na další krok, uložte modelu do souboru ZIP a přidáním následující kód na konci vaší `Train()` funkce:</span><span class="sxs-lookup"><span data-stu-id="f6780-222">Before you go onto the next step, save your model to a .zip file by adding the following code at the end of your `Train()` function:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="f6780-223">Přidávání `await` příkaz, který má `model.WriteAsync()` volání znamená, že `Train()` metoda musí změnit tak, aby asynchronní metody, která vrací `Task`.</span><span class="sxs-lookup"><span data-stu-id="f6780-223">Adding the `await` statement to the `model.WriteAsync()` call means that the `Train()` method must be changed to an async method that returns a `Task`.</span></span> <span data-ttu-id="f6780-224">Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f6780-224">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="f6780-225">Změna návratový typ `Train` metoda znamená, že budete muset přidat `await` na kód, který volá `Train` v `Main` metoda, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f6780-225">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="f6780-226">Přidání `await` ve vaší `Main` metoda znamená `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:</span><span class="sxs-lookup"><span data-stu-id="f6780-226">Adding an `await` in your `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="f6780-227">Také je nutné přidat následující pomocí příkazu v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="f6780-227">You also need to add the following using statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="f6780-228">Protože `async Main` metoda je nová funkce v C# 7.1 a je výchozí jazykovou verzi projektu C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f6780-228">Because the `async Main` method is a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="f6780-229">To lze provést, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f6780-229">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="f6780-230">Vyberte **sestavení** a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f6780-230">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="f6780-231">V rozevírací nabídce, a vyberte **C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="f6780-231">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="f6780-232">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f6780-232">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="f6780-233">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="f6780-233">Evaluate the model</span></span>

<span data-ttu-id="f6780-234">Vyhodnocení je proces kontroly, jak dobře model funguje.</span><span class="sxs-lookup"><span data-stu-id="f6780-234">Evaluation is the process of checking how well the model works.</span></span> <span data-ttu-id="f6780-235">Je důležité, že váš model vytváří dobrý předpovědi na data, která nepoužili, když byla cvičení.</span><span class="sxs-lookup"><span data-stu-id="f6780-235">It's important that your model makes good predictions on data that it didn't use when it was trained.</span></span> <span data-ttu-id="f6780-236">Jeden ze způsobů, jak provést toto je rozdělením data do vlaku a testovací datové sady, jako jste to udělali v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="f6780-236">One way to do this is by splitting the data into train and test datasets, as you did in this tutorial.</span></span> <span data-ttu-id="f6780-237">Teď, když jsme natrénovali model na základě dat train, se zobrazí její výkon na testovací data.</span><span class="sxs-lookup"><span data-stu-id="f6780-237">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="f6780-238">Přejděte zpět na vaše `Main` funkce a přidejte následující kód pod voláním `Train()`metoda:</span><span class="sxs-lookup"><span data-stu-id="f6780-238">Go back to your `Main` function and add the following code beneath the call to the `Train()`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="f6780-239">`Evaluate()` Funkce vyhodnotí modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-239">The `Evaluate()` function evaluates your model.</span></span> <span data-ttu-id="f6780-240">Vytvoření této funkce níže `Train()`.</span><span class="sxs-lookup"><span data-stu-id="f6780-240">Create that function below `Train()`.</span></span> <span data-ttu-id="f6780-241">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f6780-241">Add the following code:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="f6780-242">Načtení dat pomocí testu `TextLoader()` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-242">Load the test data using the `TextLoader()` function.</span></span> <span data-ttu-id="f6780-243">Přidejte následující kód do `Evaluate()` metoda:</span><span class="sxs-lookup"><span data-stu-id="f6780-243">Add the following code into the `Evaluate()` method:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="f6780-244">Přidejte následující kód k vyhodnocení modelu a vytvoření metriky pro ni:</span><span class="sxs-lookup"><span data-stu-id="f6780-244">Add the following code to evaluate the model and produce the metrics for it:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="f6780-245">RMS je jedna Metrika pro vyhodnocení regrese problémy.</span><span class="sxs-lookup"><span data-stu-id="f6780-245">RMS is one metric for evaluating regression problems.</span></span> <span data-ttu-id="f6780-246">Čím nižší je, tím lépe modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-246">The lower it is, the better your model.</span></span> <span data-ttu-id="f6780-247">Přidejte následující kód do `Evaluate()` funkce Tisknout služby RMS pro váš model.</span><span class="sxs-lookup"><span data-stu-id="f6780-247">Add the following code into the `Evaluate()` function to print the RMS for your model.</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="f6780-248">RSquared je jiné metriky pro vyhodnocení regrese problémy.</span><span class="sxs-lookup"><span data-stu-id="f6780-248">RSquared is another metric for evaluating regression problems.</span></span> <span data-ttu-id="f6780-249">RSquared bude mít hodnotu mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="f6780-249">RSquared will be a value between 0 and 1.</span></span> <span data-ttu-id="f6780-250">Čím bližší jste hodnotu 1, tím lépe modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-250">The closer you are to 1, the better your model.</span></span> <span data-ttu-id="f6780-251">Přidejte následující kód do `Evaluate()` funkce Tisknout RSquared hodnota modelu.</span><span class="sxs-lookup"><span data-stu-id="f6780-251">Add the following code into the `Evaluate()` function to print the RSquared value for your model.</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="f6780-252">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="f6780-252">Use the model for predictions</span></span>

<span data-ttu-id="f6780-253">Dále vytvořte třídu úklidové testovací scénářů, které můžete použít a ujistěte se, že váš model pracuje správně:</span><span class="sxs-lookup"><span data-stu-id="f6780-253">Next, create a class to house test scenarios that you can use to make sure your model is working correctly:</span></span>

1. <span data-ttu-id="f6780-254">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f6780-254">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f6780-255">V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="f6780-255">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="f6780-256">Pak vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f6780-256">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="f6780-257">Upravte třídy, která má být statické jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f6780-257">Modify the class to be static like in the following example:</span></span>

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="f6780-258">Tento kurz používá jeden testovací cesty v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="f6780-258">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="f6780-259">Později můžete přidat další scénáře a experimentovat s této ukázce.</span><span class="sxs-lookup"><span data-stu-id="f6780-259">Later you can add other scenarios to experiment with this sample.</span></span> <span data-ttu-id="f6780-260">Přidejte následující kód do `TestTrips` třídy:</span><span class="sxs-lookup"><span data-stu-id="f6780-260">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="f6780-261">Tuto cestu skutečné tarif je 29.5, ale jako zástupný znak, použijte hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="f6780-261">This trip's actual fare is 29.5, but use 0 as a placeholder.</span></span> <span data-ttu-id="f6780-262">Algoritmu strojového učení se předvídání tarif.</span><span class="sxs-lookup"><span data-stu-id="f6780-262">The machine learning algorithm will predict the fare.</span></span>

<span data-ttu-id="f6780-263">Přidejte následující kód ve vaší `Main` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6780-263">Add the following code in your `Main` function.</span></span> <span data-ttu-id="f6780-264">Testuje se váš model pomocí `TestTrip` dat:</span><span class="sxs-lookup"><span data-stu-id="f6780-264">It tests out your model using the `TestTrip` data:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="f6780-265">Spusťte program zobrazíte předpokládaných taxíkem tarif pro testovacího případu.</span><span class="sxs-lookup"><span data-stu-id="f6780-265">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="f6780-266">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="f6780-266">Congratulations!</span></span> <span data-ttu-id="f6780-267">Jste teď úspěšně sestaven model machine learning pro predikci taxíkem tarify, vyhodnotit jeho přesnost a otestovat ho.</span><span class="sxs-lookup"><span data-stu-id="f6780-267">You've now successfully built a machine learning model for predicting taxi fares, evaluated its accuracy, and tested it.</span></span> <span data-ttu-id="f6780-268">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště.</span><span class="sxs-lookup"><span data-stu-id="f6780-268">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f6780-269">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f6780-269">Next steps</span></span>

<span data-ttu-id="f6780-270">V tomto kurzu jste se dozvěděli, jak:</span><span class="sxs-lookup"><span data-stu-id="f6780-270">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f6780-271">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="f6780-271">Understand the problem</span></span>
> * <span data-ttu-id="f6780-272">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="f6780-272">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="f6780-273">Příprava a pochopit vaše data</span><span class="sxs-lookup"><span data-stu-id="f6780-273">Prepare and understand your data</span></span>
> * <span data-ttu-id="f6780-274">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="f6780-274">Create a learning pipeline</span></span>
> * <span data-ttu-id="f6780-275">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="f6780-275">Load and transform your data</span></span>
> * <span data-ttu-id="f6780-276">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="f6780-276">Choose a learning algorithm</span></span>
> * <span data-ttu-id="f6780-277">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="f6780-277">Train the model</span></span>
> * <span data-ttu-id="f6780-278">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="f6780-278">Evaluate the model</span></span>
> * <span data-ttu-id="f6780-279">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="f6780-279">Use the model for predictions</span></span>

<span data-ttu-id="f6780-280">Podívejte se na našem úložišti GitHub a pokračujte ve čtení najít další ukázky.</span><span class="sxs-lookup"><span data-stu-id="f6780-280">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f6780-281">úložiště GitHub DotNet/machinelearning</span><span class="sxs-lookup"><span data-stu-id="f6780-281">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
