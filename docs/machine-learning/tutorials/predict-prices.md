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
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="13161-103">Kurz: předpověď cen pomocí regrese s ML.NET</span><span class="sxs-lookup"><span data-stu-id="13161-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="13161-104">V tomto kurzu se naučíte, jak vytvořit [regresní model](../resources/glossary.md#regression) s využitím ml.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.</span><span class="sxs-lookup"><span data-stu-id="13161-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="13161-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="13161-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="13161-106">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="13161-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="13161-107">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="13161-107">Load and transform the data</span></span>
> * <span data-ttu-id="13161-108">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="13161-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="13161-109">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="13161-109">Train the model</span></span>
> * <span data-ttu-id="13161-110">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="13161-110">Evaluate the model</span></span>
> * <span data-ttu-id="13161-111">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="13161-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13161-112">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="13161-112">Prerequisites</span></span>

* <span data-ttu-id="13161-113">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="13161-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="13161-114">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="13161-114">Create a console application</span></span>

1. <span data-ttu-id="13161-115">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="13161-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="13161-116">Vytvořte v projektu adresář s názvem *data* pro uložení sady dat a souborů modelu.</span><span class="sxs-lookup"><span data-stu-id="13161-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="13161-117">Nainstalujte balíček NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="13161-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="13161-118">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="13161-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="13161-119">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="13161-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="13161-120">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="13161-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="13161-121">Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="13161-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="13161-122">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="13161-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="13161-123">Stáhněte si sady dat [taxi-Fare-Train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-Fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) a uložte je do složky *dat* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="13161-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="13161-124">Tyto sady dat používáme ke studiu modelu strojového učení a vyhodnocení toho, jak je model přesný.</span><span class="sxs-lookup"><span data-stu-id="13161-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="13161-125">Tyto sady dat jsou původně ze [sady NYC TLC taxislužby Trip data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span><span class="sxs-lookup"><span data-stu-id="13161-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="13161-126">V **Průzkumník řešení**klikněte pravým tlačítkem na každý ze \*souborů. csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="13161-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="13161-127">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="13161-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="13161-128">Otevřete sadu dat **taxi-Fare-Train. csv** a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="13161-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="13161-129">Podívejte se na všechny sloupce.</span><span class="sxs-lookup"><span data-stu-id="13161-129">Take a look at each of the columns.</span></span> <span data-ttu-id="13161-130">Pochopte data a rozhodněte, které sloupce jsou **funkce** a které jsou **označeny**.</span><span class="sxs-lookup"><span data-stu-id="13161-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="13161-131">`label` je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="13161-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="13161-132">Identifikované `Features`jsou vstupy, které modelu udělíte pro předpověď `Label`.</span><span class="sxs-lookup"><span data-stu-id="13161-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="13161-133">Poskytnutá datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="13161-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="13161-134">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="13161-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="13161-135">**rate_code:** Typ rychlosti taxislužby Trip je funkce.</span><span class="sxs-lookup"><span data-stu-id="13161-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="13161-136">**passenger_count:** Počet cestujících na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="13161-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="13161-137">**trip_time_in_secs:** Doba, po kterou cesta trvala.</span><span class="sxs-lookup"><span data-stu-id="13161-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="13161-138">Chcete předpovědět jízdné za cestu před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="13161-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="13161-139">V tuto chvíli nevíte, jak dlouho bude trvat.</span><span class="sxs-lookup"><span data-stu-id="13161-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="13161-140">Doba odezvy tedy není funkcí a tento sloupec z modelu vyloučíte.</span><span class="sxs-lookup"><span data-stu-id="13161-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="13161-141">**trip_distance:** Vzdálenost na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="13161-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="13161-142">**payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="13161-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="13161-143">**fare_amount:** Celková částka taxislužby jízdné je štítek.</span><span class="sxs-lookup"><span data-stu-id="13161-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="13161-144">Vytváření datových tříd</span><span class="sxs-lookup"><span data-stu-id="13161-144">Create data classes</span></span>

<span data-ttu-id="13161-145">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="13161-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="13161-146">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="13161-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="13161-147">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="13161-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="13161-148">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="13161-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="13161-149">Do nového souboru přidejte následující direktivy `using`:</span><span class="sxs-lookup"><span data-stu-id="13161-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="13161-150">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, do souboru *TaxiTrip.cs* :</span><span class="sxs-lookup"><span data-stu-id="13161-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="13161-151">`TaxiTrip` je vstupní datová třída a má definice pro každý sloupec sady dat.</span><span class="sxs-lookup"><span data-stu-id="13161-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="13161-152">Pomocí atributu <xref:Microsoft.ML.Data.LoadColumnAttribute> určete indexy zdrojových sloupců v sadě dat.</span><span class="sxs-lookup"><span data-stu-id="13161-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="13161-153">Třída `TaxiTripFarePrediction` představuje předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="13161-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="13161-154">Má jedno pole s plovoucí desetinnou čárkou, `FareAmount`s použitým atributem `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>.</span><span class="sxs-lookup"><span data-stu-id="13161-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="13161-155">V případě regresní úlohy obsahuje sloupec **skóre** předpovězené hodnoty popisku.</span><span class="sxs-lookup"><span data-stu-id="13161-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="13161-156">Použijte `float` typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupní a předpovědi třídy dat.</span><span class="sxs-lookup"><span data-stu-id="13161-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="13161-157">Definování cest k datům a modelům</span><span class="sxs-lookup"><span data-stu-id="13161-157">Define data and model paths</span></span>

<span data-ttu-id="13161-158">Do horní části souboru *program.cs* přidejte následující další příkazy `using`:</span><span class="sxs-lookup"><span data-stu-id="13161-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="13161-159">Je potřeba vytvořit tři pole, která budou uchovávat cesty k souborům s datovými sadami a soubor pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="13161-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="13161-160">`_trainDataPath` obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="13161-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="13161-161">`_testDataPath` obsahuje cestu k souboru s datovou sadou, která se používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="13161-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="13161-162">`_modelPath` obsahuje cestu k souboru, ve kterém je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="13161-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="13161-163">Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest a pro `_textLoader` proměnnou:</span><span class="sxs-lookup"><span data-stu-id="13161-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="13161-164">Všechny operace ML.NET začínají ve [třídě MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="13161-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="13161-165">Inicializuje se `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="13161-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="13161-166">Je podobný a koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="13161-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="13161-167">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="13161-167">Initialize variables in Main</span></span>

<span data-ttu-id="13161-168">Nahraďte `Console.WriteLine("Hello World!")` řádek v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="13161-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="13161-169">Přidejte následující jako další řádek kódu v metodě `Main` pro volání metody `Train`:</span><span class="sxs-lookup"><span data-stu-id="13161-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="13161-170">Metoda `Train()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="13161-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="13161-171">Načte data.</span><span class="sxs-lookup"><span data-stu-id="13161-171">Loads the data.</span></span>
* <span data-ttu-id="13161-172">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="13161-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="13161-173">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="13161-173">Trains the model.</span></span>
* <span data-ttu-id="13161-174">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="13161-174">Returns the model.</span></span>

<span data-ttu-id="13161-175">Metoda `Train` navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="13161-175">The `Train` method trains the model.</span></span> <span data-ttu-id="13161-176">Vytvořte tuto metodu hned pod `Main`, a to pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="13161-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="13161-177">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="13161-177">Load and transform data</span></span>

<span data-ttu-id="13161-178">ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data.</span><span class="sxs-lookup"><span data-stu-id="13161-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="13161-179">`IDataView` může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu).</span><span class="sxs-lookup"><span data-stu-id="13161-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="13161-180">Do prvního řádku `Train()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="13161-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="13161-181">Jak chcete předpovědět tarif taxislužby TRIPS, `FareAmount` sloupec je `Label`, který budete předpovědět (výstup modelu).</span><span class="sxs-lookup"><span data-stu-id="13161-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="13161-182">Použijte třídu transformace `CopyColumnsEstimator` ke zkopírování `FareAmount`a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="13161-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="13161-183">Algoritmus, který vlaky nastavil, vyžaduje **číselné** funkce, takže je nutné transformovat hodnoty kategorií dat (`VendorId`, `RateCode`a `PaymentType`) na čísla (`VendorIdEncoded`, `RateCodeEncoded`a `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="13161-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="13161-184">K tomu použijte transformační třídu [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , která přiřadí různé hodnoty číselného klíče k různým hodnotám každého sloupce a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="13161-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="13161-185">Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí třídy `mlContext.Transforms.Concatenate` transformace.</span><span class="sxs-lookup"><span data-stu-id="13161-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="13161-186">Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** .</span><span class="sxs-lookup"><span data-stu-id="13161-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="13161-187">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="13161-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="13161-188">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="13161-188">Choose a learning algorithm</span></span>

<span data-ttu-id="13161-189">Tento problém se týká předpovědi tarifů taxislužby na cestách v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="13161-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="13161-190">Na první pohled se může zdát, že bude záviset na ujeté vzdálenosti.</span><span class="sxs-lookup"><span data-stu-id="13161-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="13161-191">Taxislužby dodavatelé v New Yorku ale účtují různé částky pro jiné faktory, jako jsou další cestující nebo platby prostřednictvím platební karty místo hotovostního úvěru.</span><span class="sxs-lookup"><span data-stu-id="13161-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="13161-192">Chcete odhadnout hodnotu ceny, což je skutečná hodnota, která je založená na dalších faktorech v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="13161-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="13161-193">Uděláte to tak, že zvolíte úlohu [regrese](../resources/glossary.md#regression) strojového učení.</span><span class="sxs-lookup"><span data-stu-id="13161-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="13161-194">Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definic transformace dat tak, že jako další řádek kódu v `Train()`přidáte následující.</span><span class="sxs-lookup"><span data-stu-id="13161-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="13161-195">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="13161-195">Train the model</span></span>

<span data-ttu-id="13161-196">Přizpůsobit model na školicí `dataview` a vrátit vyškolený model přidáním následujícího řádku kódu do metody `Train()`:</span><span class="sxs-lookup"><span data-stu-id="13161-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="13161-197">Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.</span><span class="sxs-lookup"><span data-stu-id="13161-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="13161-198">Vraťte školený model s následujícím řádkem kódu v metodě `Train()`:</span><span class="sxs-lookup"><span data-stu-id="13161-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="13161-199">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="13161-199">Evaluate the model</span></span>

<span data-ttu-id="13161-200">Dále vyhodnoťte výkon vašeho modelu s testovacími daty pro zajištění a ověření kvality.</span><span class="sxs-lookup"><span data-stu-id="13161-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="13161-201">Vytvořte metodu `Evaluate()` hned po `Train()`s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="13161-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="13161-202">Metoda `Evaluate` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="13161-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="13161-203">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="13161-203">Loads the test dataset.</span></span>
* <span data-ttu-id="13161-204">Vytvoří vyhodnocovací filtr regrese.</span><span class="sxs-lookup"><span data-stu-id="13161-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="13161-205">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="13161-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="13161-206">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="13161-206">Displays the metrics.</span></span>

<span data-ttu-id="13161-207">Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `Train`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="13161-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="13161-208">Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) .</span><span class="sxs-lookup"><span data-stu-id="13161-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="13161-209">Vyhodnotit model pomocí této datové sady jako kontroly kvality přidáním následujícího kódu do metody `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="13161-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="13161-210">Dále Transformujte data `Test` přidáním následujícího kódu do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="13161-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="13161-211">Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro vstupní řádky sady testů.</span><span class="sxs-lookup"><span data-stu-id="13161-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="13161-212">Metoda `RegressionContext.Evaluate` vypočítá metriky kvality pro `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="13161-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="13161-213">Vrátí objekt <xref:Microsoft.ML.Data.RegressionMetrics>, který obsahuje celkové metriky vypočítané hodnotiteli regrese.</span><span class="sxs-lookup"><span data-stu-id="13161-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="13161-214">Aby bylo možné zjistit kvalitu modelu, je třeba nejprve získat metriky.</span><span class="sxs-lookup"><span data-stu-id="13161-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="13161-215">Přidejte následující kód jako další řádek v metodě `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="13161-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="13161-216">Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.</span><span class="sxs-lookup"><span data-stu-id="13161-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="13161-217">Přidejte následující kód pro vyhodnocení modelu a vytvořte metriky vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="13161-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="13161-218">[RSquared](../resources/glossary.md#coefficient-of-determination) je další metrika hodnocení regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="13161-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="13161-219">RSquared přebírá hodnoty mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="13161-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="13161-220">Bližší hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="13161-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="13161-221">Přidejte následující kód do metody `Evaluate` pro zobrazení hodnoty RSquared:</span><span class="sxs-lookup"><span data-stu-id="13161-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="13161-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) je jednou ze zkušebních metrik modelu regrese.</span><span class="sxs-lookup"><span data-stu-id="13161-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="13161-223">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="13161-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="13161-224">Přidejte následující kód do metody `Evaluate` k zobrazení hodnoty RMS:</span><span class="sxs-lookup"><span data-stu-id="13161-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="13161-225">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="13161-225">Use the model for predictions</span></span>

<span data-ttu-id="13161-226">Vytvořte metodu `TestSinglePrediction` hned za metodou `Evaluate` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="13161-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="13161-227">Metoda `TestSinglePrediction` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="13161-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="13161-228">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="13161-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="13161-229">Odhadne částku tarifu na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="13161-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="13161-230">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="13161-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="13161-231">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="13161-231">Displays the predicted results.</span></span>

<span data-ttu-id="13161-232">Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `Evaluate`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="13161-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="13161-233">Pomocí `PredictionEngine` můžete odhadnout tarif přidáním následujícího kódu do `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="13161-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="13161-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="13161-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="13161-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="13161-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="13161-236">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="13161-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="13161-237">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="13161-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="13161-238">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="13161-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="13161-239">rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="13161-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="13161-240">V tomto kurzu se používá jedna zkušební cesta v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="13161-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="13161-241">Později můžete přidat další scénáře pro experimentování s modelem.</span><span class="sxs-lookup"><span data-stu-id="13161-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="13161-242">Přidejte cestu k otestování předpovědi nákladů vyškolených modelů v metodě `TestSinglePrediction()` vytvořením instance `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="13161-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="13161-243">Dále předpovídat tarify na základě jedné instance dat taxislužby a předejte je do `PredictionEngine` přidáním následujícího jako další řádky kódu v metodě `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="13161-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="13161-244">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provádí předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="13161-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="13161-245">Chcete-li zobrazit předpovězené tarify zadané cesty, přidejte do metody `TestSinglePrediction` následující kód:</span><span class="sxs-lookup"><span data-stu-id="13161-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="13161-246">Spusťte program, abyste viděli předpovězené taxislužby jízdné za váš testovací případ.</span><span class="sxs-lookup"><span data-stu-id="13161-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="13161-247">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="13161-247">Congratulations!</span></span> <span data-ttu-id="13161-248">Teď jste úspěšně vytvořili model strojového učení pro předvídání tarifů taxislužby Trip, vyhodnotili jste jeho přesnost a použili ho k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="13161-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="13161-249">Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.</span><span class="sxs-lookup"><span data-stu-id="13161-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13161-250">Další kroky</span><span class="sxs-lookup"><span data-stu-id="13161-250">Next steps</span></span>

<span data-ttu-id="13161-251">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="13161-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="13161-252">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="13161-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="13161-253">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="13161-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="13161-254">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="13161-254">Load and transform the data</span></span>
> * <span data-ttu-id="13161-255">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="13161-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="13161-256">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="13161-256">Train the model</span></span>
> * <span data-ttu-id="13161-257">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="13161-257">Evaluate the model</span></span>
> * <span data-ttu-id="13161-258">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="13161-258">Use the model for predictions</span></span>

<span data-ttu-id="13161-259">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="13161-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="13161-260">Iris clustering</span><span class="sxs-lookup"><span data-stu-id="13161-260">Iris clustering</span></span>](iris-clustering.md)
