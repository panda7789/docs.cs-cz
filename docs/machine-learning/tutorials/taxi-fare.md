---
title: 'Kurz: Předvídání cen pomocí regresního algoritmu'
description: Tento kurz ukazuje, jak sestavit regresní model využívající ML.NET k předvídání cen, konkrétně tarify taxislužby města New York City.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a61b0eb316f61e888933aefa2c91a9f76c6e1c53
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641196"
---
# <a name="tutorial-predict-prices-using-a-regression-model-with-mlnet"></a><span data-ttu-id="bb63a-103">Kurz: Předvídání cen pomocí regresní model ML.NET</span><span class="sxs-lookup"><span data-stu-id="bb63a-103">Tutorial: Predict prices using a regression model with ML.NET</span></span>

<span data-ttu-id="bb63a-104">Tento kurz ukazuje, jak sestavit [regresní model](../resources/glossary.md#regression) pomocí ML.NET k předvídání cen, konkrétně tarify taxislužby města New York City.</span><span class="sxs-lookup"><span data-stu-id="bb63a-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="bb63a-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="bb63a-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bb63a-106">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="bb63a-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="bb63a-107">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="bb63a-107">Load and transform the data</span></span>
> * <span data-ttu-id="bb63a-108">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="bb63a-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="bb63a-109">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="bb63a-109">Train the model</span></span>
> * <span data-ttu-id="bb63a-110">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bb63a-110">Evaluate the model</span></span>
> * <span data-ttu-id="bb63a-111">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="bb63a-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb63a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb63a-112">Prerequisites</span></span>

* <span data-ttu-id="bb63a-113">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="bb63a-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="bb63a-114">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="bb63a-114">Create a console application</span></span>

1. <span data-ttu-id="bb63a-115">Vytvoření **konzolovou aplikaci .NET Core** nazývá "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="bb63a-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="bb63a-116">Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="bb63a-117">Nainstalujte **Microsoft.ML** balíček NuGet:</span><span class="sxs-lookup"><span data-stu-id="bb63a-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="bb63a-118">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="bb63a-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="bb63a-119">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte balíček, v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bb63a-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="bb63a-120">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="bb63a-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="bb63a-121">Totéž proveďte pro **Microsoft.ML.FastTree** balíček Nuget.</span><span class="sxs-lookup"><span data-stu-id="bb63a-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="bb63a-122">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="bb63a-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="bb63a-123">Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxislužby. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) dat nastaví a uloží je do *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="bb63a-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="bb63a-124">Používáme tyto datové sady pro trénování modelu strojového učení a pak vyhodnotit, jak přesný je model.</span><span class="sxs-lookup"><span data-stu-id="bb63a-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="bb63a-125">Tyto datové sady jsou původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="bb63a-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="bb63a-126">V **Průzkumníka řešení**, klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="bb63a-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="bb63a-127">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="bb63a-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="bb63a-128">Otevřít **taxislužby. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="bb63a-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="bb63a-129">Podívejte se na všech sloupcích.</span><span class="sxs-lookup"><span data-stu-id="bb63a-129">Take a look at each of the columns.</span></span> <span data-ttu-id="bb63a-130">Vysvětlení dat a rozhodnout, které sloupce budou **funkce** a který je **popisek**.</span><span class="sxs-lookup"><span data-stu-id="bb63a-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="bb63a-131">`label` Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="bb63a-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="bb63a-132">Identifikovanou `Features`jsou vstupy, poskytují model k predikci `Label`.</span><span class="sxs-lookup"><span data-stu-id="bb63a-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="bb63a-133">Zadaná datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="bb63a-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="bb63a-134">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="bb63a-135">**rate_code:** Typ kursu cesty taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="bb63a-136">**passenger_count:** Počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="bb63a-137">**trip_time_in_secs:** Dobu trvání cesty.</span><span class="sxs-lookup"><span data-stu-id="bb63a-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="bb63a-138">Chcete předpovědět tarif cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="bb63a-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="bb63a-139">V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách.</span><span class="sxs-lookup"><span data-stu-id="bb63a-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="bb63a-140">Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="bb63a-141">**trip_distance:** Vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="bb63a-142">**payment_type:** Způsob platby (hotovosti nebo kreditní karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="bb63a-143">**fare_amount:** Celkový počet taxislužby tarif placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="bb63a-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="bb63a-144">Vytvoření datových tříd</span><span class="sxs-lookup"><span data-stu-id="bb63a-144">Create data classes</span></span>

<span data-ttu-id="bb63a-145">Vytvoření třídy pro vstupní data a předpovědí:</span><span class="sxs-lookup"><span data-stu-id="bb63a-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="bb63a-146">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="bb63a-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="bb63a-147">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="bb63a-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="bb63a-148">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bb63a-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="bb63a-149">Přidejte následující `using` direktivy do nového souboru:</span><span class="sxs-lookup"><span data-stu-id="bb63a-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="bb63a-150">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="bb63a-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="bb63a-151">`TaxiTrip` je třída vstupní data a obsahuje definice pro všechny sloupce datové sady.</span><span class="sxs-lookup"><span data-stu-id="bb63a-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="bb63a-152">Použití <xref:Microsoft.ML.Data.LoadColumnAttribute> atributy indexů zdrojových sloupců v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="bb63a-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="bb63a-153">`TaxiTripFarePrediction` Třída reprezentuje předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="bb63a-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="bb63a-154">Obsahuje pole jednou čárkou `FareAmount`, s `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bb63a-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="bb63a-155">V případě úloh regrese **skóre** sloupec obsahuje hodnoty předpovězené popisků.</span><span class="sxs-lookup"><span data-stu-id="bb63a-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="bb63a-156">Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.</span><span class="sxs-lookup"><span data-stu-id="bb63a-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="bb63a-157">Definovat cesty k datům a model</span><span class="sxs-lookup"><span data-stu-id="bb63a-157">Define data and model paths</span></span>

<span data-ttu-id="bb63a-158">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="bb63a-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="bb63a-159">Je potřeba vytvořit tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu:</span><span class="sxs-lookup"><span data-stu-id="bb63a-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="bb63a-160">`_trainDataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="bb63a-161">`_testDataPath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="bb63a-162">`_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="bb63a-163">Přidejte následující kód přímo nad `Main` metoda zadat tyto cesty a `_textLoader` proměnné:</span><span class="sxs-lookup"><span data-stu-id="bb63a-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="bb63a-164">Všechny operace ML.NET spustit v [MLContext třídy](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="bb63a-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="bb63a-165">Inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="bb63a-166">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bb63a-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="bb63a-167">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="bb63a-167">Initialize variables in Main</span></span>

<span data-ttu-id="bb63a-168">Nahradit `Console.WriteLine("Hello World!")` řádku v `Main` metoda následujícím kódem, jak deklarovat a inicializovat `mlContext` proměnné:</span><span class="sxs-lookup"><span data-stu-id="bb63a-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="bb63a-169">Přidejte následující položky jako další řádek kódu v `Main` metoda se má volat `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="bb63a-170">`Train()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="bb63a-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="bb63a-171">Načte data.</span><span class="sxs-lookup"><span data-stu-id="bb63a-171">Loads the data.</span></span>
* <span data-ttu-id="bb63a-172">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="bb63a-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="bb63a-173">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-173">Trains the model.</span></span>
* <span data-ttu-id="bb63a-174">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-174">Returns the model.</span></span>

<span data-ttu-id="bb63a-175">`Train` Metoda trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-175">The `Train` method trains the model.</span></span> <span data-ttu-id="bb63a-176">Vytvoření metody hned pod `Main`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bb63a-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="bb63a-177">Načítání a transformace dat.</span><span class="sxs-lookup"><span data-stu-id="bb63a-177">Load and transform data</span></span>

<span data-ttu-id="bb63a-178">Používá ML.NET [IDataView třídy](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob, jak popisují číselné nebo text tabulková data.</span><span class="sxs-lookup"><span data-stu-id="bb63a-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="bb63a-179">`IDataView` můžete načíst buď textové soubory nebo v reálném čase (například SQL databázi nebo soubory protokolů).</span><span class="sxs-lookup"><span data-stu-id="bb63a-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="bb63a-180">Přidejte následující kód jako první řádek `Train()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="bb63a-181">Jak chcete předpovědět tarif cesty taxíkem, `FareAmount` sloupec je `Label` , že bude předpovídat (výstup modelu) použijte `CopyColumnsEstimator` třídy transformace kopírování `FareAmount`a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bb63a-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="bb63a-182">Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla (`VendorIdEncoded`, `RateCodeEncoded`, a `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="bb63a-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="bb63a-183">Chcete-li to mohli udělat, použijte [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) třídy transformace, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bb63a-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="bb63a-184">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `mlContext.Transforms.Concatenate` třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="bb63a-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="bb63a-185">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="bb63a-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="bb63a-186">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bb63a-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="bb63a-187">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="bb63a-187">Choose a learning algorithm</span></span>

<span data-ttu-id="bb63a-188">Tento problém je o předpověď tarif cesty taxíkem v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="bb63a-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="bb63a-189">Na první pohled to nemusí závisí jednoduše na vzdálenost přesunul.</span><span class="sxs-lookup"><span data-stu-id="bb63a-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="bb63a-190">Ale taxislužby dodavatelů v New Yorku poplatky různá množství dalších faktorů, jako je například další cestujících nebo placení pomocí platební karty místo platební.</span><span class="sxs-lookup"><span data-stu-id="bb63a-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="bb63a-191">Chcete předpovídat cenu hodnotu, která je skutečná hodnota, na základě dalších faktorů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="bb63a-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="bb63a-192">Chcete-li to mohli udělat, klikněte [regrese](../resources/glossary.md#regression) machine learning úloh.</span><span class="sxs-lookup"><span data-stu-id="bb63a-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="bb63a-193">Připojte [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) na definice transformace dat přidáním následujícího kódu jako další řádek kódu v machine learning úlohy `Train()`:</span><span class="sxs-lookup"><span data-stu-id="bb63a-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="bb63a-194">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="bb63a-194">Train the model</span></span>

<span data-ttu-id="bb63a-195">Přizpůsobit modelu, který má na školení `dataview` a vrátit tak, že přidáte následující řádek kódu v trénovaného modelu `Train()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="bb63a-196">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="bb63a-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="bb63a-197">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bb63a-197">Evaluate the model</span></span>

<span data-ttu-id="bb63a-198">Zhodnotit svůj výkon modelu pomocí zkušebních dat kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="bb63a-198">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="bb63a-199">Vytvořte `Evaluate()` metoda, hned za `Train()`, následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="bb63a-199">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="bb63a-200">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="bb63a-200">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="bb63a-201">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="bb63a-201">Loads the test dataset.</span></span>
* <span data-ttu-id="bb63a-202">Chyba při vyhodnocování regrese vytvoří.</span><span class="sxs-lookup"><span data-stu-id="bb63a-202">Creates the regression evaluator.</span></span>
* <span data-ttu-id="bb63a-203">Vyhodnotí modelu a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="bb63a-203">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="bb63a-204">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="bb63a-204">Displays the metrics.</span></span>

<span data-ttu-id="bb63a-205">Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bb63a-205">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="bb63a-206">Načíst testovací datové sady pomocí [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="bb63a-206">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="bb63a-207">Vyhodnocení modelu s použitím tohoto objektu dataset jako kontrola kvality tak, že přidáte následující kód `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-207">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="bb63a-208">V dalším kroku transformovat `Test` data přidáním následujícího kódu do `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="bb63a-208">Next, transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="bb63a-209">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda řádky vstupní datovou sadu vytváří předpovědi pro test.</span><span class="sxs-lookup"><span data-stu-id="bb63a-209">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="bb63a-210">`RegressionContext.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="bb63a-210">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="bb63a-211">Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení regrese.</span><span class="sxs-lookup"><span data-stu-id="bb63a-211">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="bb63a-212">Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="bb63a-212">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="bb63a-213">Přidejte následující kód jako další řádek `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-213">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="bb63a-214">Až budete mít předpovědi nastavená, [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` v testovací datové sady a vrátí metriky na jaký je výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-214">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="bb63a-215">Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="bb63a-215">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="bb63a-216">[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="bb63a-216">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="bb63a-217">RSquared trvá hodnoty v rozmezí 0 až 1.</span><span class="sxs-lookup"><span data-stu-id="bb63a-217">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="bb63a-218">Čím blíž její hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="bb63a-218">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="bb63a-219">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:</span><span class="sxs-lookup"><span data-stu-id="bb63a-219">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="bb63a-220">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model.</span><span class="sxs-lookup"><span data-stu-id="bb63a-220">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="bb63a-221">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="bb63a-221">The lower it is, the better the model is.</span></span> <span data-ttu-id="bb63a-222">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:</span><span class="sxs-lookup"><span data-stu-id="bb63a-222">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="bb63a-223">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="bb63a-223">Use the model for predictions</span></span>

<span data-ttu-id="bb63a-224">Vytvořte `TestSinglePrediction` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bb63a-224">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="bb63a-225">`TestSinglePrediction` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="bb63a-225">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="bb63a-226">Vytvoří jeden komentář testovací data.</span><span class="sxs-lookup"><span data-stu-id="bb63a-226">Creates a single comment of test data.</span></span>
* <span data-ttu-id="bb63a-227">Předpovídá tarif velikost na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="bb63a-227">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="bb63a-228">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="bb63a-228">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="bb63a-229">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="bb63a-229">Displays the predicted results.</span></span>

<span data-ttu-id="bb63a-230">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bb63a-230">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="bb63a-231">Použití `PredictionEngine` k předpovědi tarif přidáním následujícího kódu `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="bb63a-231">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="bb63a-232">[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které vám umožní předat jedna instance data a pak na něm provést predikcí.</span><span class="sxs-lookup"><span data-stu-id="bb63a-232">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on it.</span></span>

<span data-ttu-id="bb63a-233">Tento kurz používá jeden test latence v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="bb63a-233">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="bb63a-234">Později můžete přidat další scénáře můžete experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="bb63a-234">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="bb63a-235">Přidat cestu k otestování předpovědi trénovaného modelu nákladů `TestSinglePrediction()` metodu tak, že vytvoříte instanci `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="bb63a-235">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="bb63a-236">V dalším kroku předpovědět tarif založené na jednu instanci data o jízdách taxislužby města a předejte ji do `PredictionEngine` přidáním následujícího kódu jako další řádky kódu ve `TestSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-236">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="bb63a-237">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce díky predikcí na jednu instanci data.</span><span class="sxs-lookup"><span data-stu-id="bb63a-237">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="bb63a-238">K zobrazení předpokládané tarif zadané cesty, přidejte následující kód do `TestSinglePrediction` metody:</span><span class="sxs-lookup"><span data-stu-id="bb63a-238">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="bb63a-239">Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="bb63a-239">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="bb63a-240">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="bb63a-240">Congratulations!</span></span> <span data-ttu-id="bb63a-241">Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="bb63a-241">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="bb63a-242">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="bb63a-242">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb63a-243">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bb63a-243">Next steps</span></span>

<span data-ttu-id="bb63a-244">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="bb63a-244">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="bb63a-245">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="bb63a-245">Prepare and understand the data</span></span>
> * <span data-ttu-id="bb63a-246">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="bb63a-246">Create a learning pipeline</span></span>
> * <span data-ttu-id="bb63a-247">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="bb63a-247">Load and transform the data</span></span>
> * <span data-ttu-id="bb63a-248">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="bb63a-248">Choose a learning algorithm</span></span>
> * <span data-ttu-id="bb63a-249">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="bb63a-249">Train the model</span></span>
> * <span data-ttu-id="bb63a-250">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bb63a-250">Evaluate the model</span></span>
> * <span data-ttu-id="bb63a-251">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="bb63a-251">Use the model for predictions</span></span>

<span data-ttu-id="bb63a-252">Přejděte k dalšímu kurzu, kde Další informace.</span><span class="sxs-lookup"><span data-stu-id="bb63a-252">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb63a-253">Iris clustering</span><span class="sxs-lookup"><span data-stu-id="bb63a-253">Iris clustering</span></span>](iris-clustering.md)
