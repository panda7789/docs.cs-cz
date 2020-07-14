---
title: 'Kurz: předpověď cen pomocí regrese'
description: V tomto kurzu se naučíte, jak vytvořit regresní model s využitím ML.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 27054e28f9a4fa628f0d7348d45528b690d7da83
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281768"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="04c5b-103">Kurz: předpověď cen pomocí regrese s ML.NET</span><span class="sxs-lookup"><span data-stu-id="04c5b-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="04c5b-104">V tomto kurzu se naučíte, jak vytvořit [regresní model](../resources/glossary.md#regression) s využitím ml.NET k předvídání cen, konkrétně v New Yorku City taxislužby tarifs.</span><span class="sxs-lookup"><span data-stu-id="04c5b-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="04c5b-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="04c5b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="04c5b-106">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="04c5b-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="04c5b-107">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="04c5b-107">Load and transform the data</span></span>
> * <span data-ttu-id="04c5b-108">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="04c5b-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="04c5b-109">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="04c5b-109">Train the model</span></span>
> * <span data-ttu-id="04c5b-110">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="04c5b-110">Evaluate the model</span></span>
> * <span data-ttu-id="04c5b-111">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="04c5b-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04c5b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04c5b-112">Prerequisites</span></span>

* <span data-ttu-id="04c5b-113">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="04c5b-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="04c5b-114">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="04c5b-114">Create a console application</span></span>

1. <span data-ttu-id="04c5b-115">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="04c5b-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="04c5b-116">Vytvořte v projektu adresář s názvem *data* pro uložení sady dat a souborů modelu.</span><span class="sxs-lookup"><span data-stu-id="04c5b-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="04c5b-117">Nainstalujte balíček NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="04c5b-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="04c5b-118">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="04c5b-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="04c5b-119">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="04c5b-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="04c5b-120">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="04c5b-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="04c5b-121">Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="04c5b-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="04c5b-122">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="04c5b-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="04c5b-123">Stáhněte [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) datových sad a uložte je do složky *dat* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="04c5b-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="04c5b-124">Tyto sady dat používáme ke studiu modelu strojového učení a vyhodnocení toho, jak je model přesný.</span><span class="sxs-lookup"><span data-stu-id="04c5b-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="04c5b-125">Tyto sady dat jsou původně ze [sady NYC TLC taxislužby Trip data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span><span class="sxs-lookup"><span data-stu-id="04c5b-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="04c5b-126">V **Průzkumník řešení**klikněte pravým tlačítkem na každý ze \* souborů. csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="04c5b-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="04c5b-127">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="04c5b-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="04c5b-128">Otevřete sadu dat **taxi-fare-train.csv** a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="04c5b-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="04c5b-129">Podívejte se na všechny sloupce.</span><span class="sxs-lookup"><span data-stu-id="04c5b-129">Take a look at each of the columns.</span></span> <span data-ttu-id="04c5b-130">Pochopte data a rozhodněte, které sloupce jsou **funkce** a které jsou **označeny**.</span><span class="sxs-lookup"><span data-stu-id="04c5b-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="04c5b-131">`label`Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="04c5b-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="04c5b-132">Identifikované `Features` jsou vstupy, které modelu poskytnete pro předpověď `Label` .</span><span class="sxs-lookup"><span data-stu-id="04c5b-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="04c5b-133">Poskytnutá datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="04c5b-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="04c5b-134">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="04c5b-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="04c5b-135">**rate_code:** Typ rychlosti taxislužby Trip je funkce.</span><span class="sxs-lookup"><span data-stu-id="04c5b-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="04c5b-136">**passenger_count:** Počet cestujících na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="04c5b-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="04c5b-137">**trip_time_in_secs:** Doba, po kterou cesta trvala.</span><span class="sxs-lookup"><span data-stu-id="04c5b-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="04c5b-138">Chcete předpovědět jízdné za cestu před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="04c5b-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="04c5b-139">V tuto chvíli nevíte, jak dlouho bude trvat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="04c5b-140">Doba odezvy tedy není funkcí a tento sloupec z modelu vyloučíte.</span><span class="sxs-lookup"><span data-stu-id="04c5b-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="04c5b-141">**trip_distance:** Vzdálenost na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="04c5b-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="04c5b-142">**payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="04c5b-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="04c5b-143">**fare_amount:** Celková částka taxislužby jízdné je štítek.</span><span class="sxs-lookup"><span data-stu-id="04c5b-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="04c5b-144">Vytváření datových tříd</span><span class="sxs-lookup"><span data-stu-id="04c5b-144">Create data classes</span></span>

<span data-ttu-id="04c5b-145">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="04c5b-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="04c5b-146">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="04c5b-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="04c5b-147">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="04c5b-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="04c5b-148">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="04c5b-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="04c5b-149">`using`Do nového souboru přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="04c5b-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="04c5b-150">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction` , do souboru *TaxiTrip.cs* :</span><span class="sxs-lookup"><span data-stu-id="04c5b-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="04c5b-151">`TaxiTrip`je vstupní datová třída a má definice pro každý sloupec sady dat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="04c5b-152">Použijte <xref:Microsoft.ML.Data.LoadColumnAttribute> atribut k určení indexů zdrojových sloupců v sadě dat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="04c5b-153">`TaxiTripFarePrediction`Třída představuje předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="04c5b-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="04c5b-154">Má jedno pole s plovoucí desetinnou čárkou, `FareAmount` s `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> použitým atributem.</span><span class="sxs-lookup"><span data-stu-id="04c5b-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="04c5b-155">V případě regresní úlohy obsahuje sloupec **skóre** předpovězené hodnoty popisku.</span><span class="sxs-lookup"><span data-stu-id="04c5b-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="04c5b-156">Použijte `float` typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách.</span><span class="sxs-lookup"><span data-stu-id="04c5b-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="04c5b-157">Definování cest k datům a modelům</span><span class="sxs-lookup"><span data-stu-id="04c5b-157">Define data and model paths</span></span>

<span data-ttu-id="04c5b-158">`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="04c5b-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="04c5b-159">Je potřeba vytvořit tři pole, která budou uchovávat cesty k souborům s datovými sadami a soubor pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="04c5b-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="04c5b-160">`_trainDataPath`obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="04c5b-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="04c5b-161">`_testDataPath`obsahuje cestu k souboru s datovou sadou použitou k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="04c5b-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="04c5b-162">`_modelPath`obsahuje cestu k souboru, ve kterém je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="04c5b-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="04c5b-163">Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest a `_textLoader` proměnné:</span><span class="sxs-lookup"><span data-stu-id="04c5b-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="04c5b-164">Všechny operace ML.NET začínají ve [třídě MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="04c5b-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="04c5b-165">Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="04c5b-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="04c5b-166">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="04c5b-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="04c5b-167">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="04c5b-167">Initialize variables in Main</span></span>

<span data-ttu-id="04c5b-168">Nahraďte `Console.WriteLine("Hello World!")` řádek v `Main` metodě následujícím kódem pro deklaraci a inicializaci `mlContext` proměnné:</span><span class="sxs-lookup"><span data-stu-id="04c5b-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="04c5b-169">Přidejte následující jako další řádek kódu v `Main` metodě pro volání `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="04c5b-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="04c5b-170">`Train()`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="04c5b-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="04c5b-171">Načte data.</span><span class="sxs-lookup"><span data-stu-id="04c5b-171">Loads the data.</span></span>
* <span data-ttu-id="04c5b-172">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="04c5b-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="04c5b-173">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="04c5b-173">Trains the model.</span></span>
* <span data-ttu-id="04c5b-174">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="04c5b-174">Returns the model.</span></span>

<span data-ttu-id="04c5b-175">`Train`Metoda navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="04c5b-175">The `Train` method trains the model.</span></span> <span data-ttu-id="04c5b-176">Vytvořte tuto metodu hned níže `Main` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="04c5b-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="04c5b-177">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="04c5b-177">Load and transform data</span></span>

<span data-ttu-id="04c5b-178">ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data.</span><span class="sxs-lookup"><span data-stu-id="04c5b-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="04c5b-179">`IDataView`může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu).</span><span class="sxs-lookup"><span data-stu-id="04c5b-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="04c5b-180">Do prvního řádku metody přidejte následující kód `Train()` :</span><span class="sxs-lookup"><span data-stu-id="04c5b-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="04c5b-181">Jak chcete předpovědět tarif taxislužby TRIPS, je ve `FareAmount` sloupci `Label` , který budete předpovídat (výstup modelu).</span><span class="sxs-lookup"><span data-stu-id="04c5b-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="04c5b-182">Použijte `CopyColumnsEstimator` třídu transformace ke zkopírování `FareAmount` a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="04c5b-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="04c5b-183">Algoritmus, který vlaky nastavil, vyžaduje **číselné** funkce, takže je nutné transformovat hodnoty kategorií dat ( `VendorId` , `RateCode` a `PaymentType` ) na čísla ( `VendorIdEncoded` , a `RateCodeEncoded` `PaymentTypeEncoded` ).</span><span class="sxs-lookup"><span data-stu-id="04c5b-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="04c5b-184">K tomu použijte transformační třídu [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , která přiřadí různé hodnoty číselného klíče k různým hodnotám každého sloupce a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="04c5b-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="04c5b-185">Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí `mlContext.Transforms.Concatenate` třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="04c5b-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="04c5b-186">Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** .</span><span class="sxs-lookup"><span data-stu-id="04c5b-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="04c5b-187">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="04c5b-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="04c5b-188">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="04c5b-188">Choose a learning algorithm</span></span>

<span data-ttu-id="04c5b-189">Tento problém se týká předpovědi tarifů taxislužby na cestách v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="04c5b-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="04c5b-190">Na první pohled se může zdát, že bude záviset na ujeté vzdálenosti.</span><span class="sxs-lookup"><span data-stu-id="04c5b-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="04c5b-191">Taxislužby dodavatelé v New Yorku ale účtují různé částky pro jiné faktory, jako jsou další cestující nebo platby prostřednictvím platební karty místo hotovostního úvěru.</span><span class="sxs-lookup"><span data-stu-id="04c5b-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="04c5b-192">Chcete odhadnout hodnotu ceny, což je skutečná hodnota, která je založená na dalších faktorech v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="04c5b-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="04c5b-193">Uděláte to tak, že zvolíte úlohu [regrese](../resources/glossary.md#regression) strojového učení.</span><span class="sxs-lookup"><span data-stu-id="04c5b-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="04c5b-194">Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) k definicím transformace dat, a to přidáním následujícího jako další řádek kódu v `Train()` :</span><span class="sxs-lookup"><span data-stu-id="04c5b-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="04c5b-195">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="04c5b-195">Train the model</span></span>

<span data-ttu-id="04c5b-196">Přizpůsobit model školením `dataview` a vrátit školicí model přidáním následujícího řádku kódu do `Train()` metody:</span><span class="sxs-lookup"><span data-stu-id="04c5b-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="04c5b-197">Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.</span><span class="sxs-lookup"><span data-stu-id="04c5b-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="04c5b-198">Vraťte vyškolený model s následujícím řádkem kódu v `Train()` metodě:</span><span class="sxs-lookup"><span data-stu-id="04c5b-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="04c5b-199">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="04c5b-199">Evaluate the model</span></span>

<span data-ttu-id="04c5b-200">Dále vyhodnoťte výkon vašeho modelu s testovacími daty pro zajištění a ověření kvality.</span><span class="sxs-lookup"><span data-stu-id="04c5b-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="04c5b-201">Vytvořte `Evaluate()` metodu, hned po `Train()` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="04c5b-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="04c5b-202">`Evaluate`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="04c5b-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="04c5b-203">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="04c5b-203">Loads the test dataset.</span></span>
* <span data-ttu-id="04c5b-204">Vytvoří vyhodnocovací filtr regrese.</span><span class="sxs-lookup"><span data-stu-id="04c5b-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="04c5b-205">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="04c5b-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="04c5b-206">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="04c5b-206">Displays the metrics.</span></span>

<span data-ttu-id="04c5b-207">Přidejte volání do metody New z `Main` metody přímo pod `Train` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="04c5b-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="04c5b-208">Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) .</span><span class="sxs-lookup"><span data-stu-id="04c5b-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="04c5b-209">Vyhodnotit model pomocí této datové sady jako kontroly kvality přidáním následujícího kódu do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="04c5b-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="04c5b-210">Dále Transformujte `Test` data přidáním následujícího kódu do `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="04c5b-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="04c5b-211">Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro vstupní řádky sady testů.</span><span class="sxs-lookup"><span data-stu-id="04c5b-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="04c5b-212">`RegressionContext.Evaluate`Metoda vypočítá metriky kvality pro `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="04c5b-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="04c5b-213">Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkové metriky vypočítané hodnotiteli regrese.</span><span class="sxs-lookup"><span data-stu-id="04c5b-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="04c5b-214">Aby bylo možné zjistit kvalitu modelu, je třeba nejprve získat metriky.</span><span class="sxs-lookup"><span data-stu-id="04c5b-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="04c5b-215">Přidejte následující kód jako další řádek v `Evaluate` metodě:</span><span class="sxs-lookup"><span data-stu-id="04c5b-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="04c5b-216">Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.</span><span class="sxs-lookup"><span data-stu-id="04c5b-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="04c5b-217">Přidejte následující kód pro vyhodnocení modelu a vytvořte metriky vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="04c5b-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="04c5b-218">[RSquared](../resources/glossary.md#coefficient-of-determination) je další metrika hodnocení regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="04c5b-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="04c5b-219">RSquared přebírá hodnoty mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="04c5b-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="04c5b-220">Bližší hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="04c5b-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="04c5b-221">Do metody přidejte následující kód, `Evaluate` aby se zobrazila hodnota RSquared:</span><span class="sxs-lookup"><span data-stu-id="04c5b-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="04c5b-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) je jednou ze zkušebních metrik modelu regrese.</span><span class="sxs-lookup"><span data-stu-id="04c5b-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="04c5b-223">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="04c5b-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="04c5b-224">Do metody přidejte následující kód `Evaluate` pro zobrazení hodnoty RMS:</span><span class="sxs-lookup"><span data-stu-id="04c5b-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="04c5b-225">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="04c5b-225">Use the model for predictions</span></span>

<span data-ttu-id="04c5b-226">Vytvořte `TestSinglePrediction` metodu hned za `Evaluate` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="04c5b-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="04c5b-227">`TestSinglePrediction`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="04c5b-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="04c5b-228">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="04c5b-229">Odhadne částku tarifu na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="04c5b-230">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="04c5b-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="04c5b-231">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="04c5b-231">Displays the predicted results.</span></span>

<span data-ttu-id="04c5b-232">Přidejte volání do metody New z `Main` metody přímo pod `Evaluate` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="04c5b-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="04c5b-233">Použijte `PredictionEngine` k předpovědi tarifu přidáním následujícího kódu do `TestSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="04c5b-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="04c5b-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="04c5b-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="04c5b-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="04c5b-236">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="04c5b-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="04c5b-237">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="04c5b-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="04c5b-238">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="04c5b-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="04c5b-239">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="04c5b-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="04c5b-240">V tomto kurzu se používá jedna zkušební cesta v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="04c5b-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="04c5b-241">Později můžete přidat další scénáře pro experimentování s modelem.</span><span class="sxs-lookup"><span data-stu-id="04c5b-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="04c5b-242">Přidejte cestu k otestování předpovědi nákladů vyškolených modelů v `TestSinglePrediction()` metodě vytvořením instance `TaxiTrip` :</span><span class="sxs-lookup"><span data-stu-id="04c5b-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="04c5b-243">Dále předpovídat tarify na základě jedné instance dat taxislužby a předejte je do rozhraní `PredictionEngine` přidáním následujícího jako další řádky kódu v `TestSinglePrediction()` metodě:</span><span class="sxs-lookup"><span data-stu-id="04c5b-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="04c5b-244">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provádí předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="04c5b-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="04c5b-245">Chcete-li zobrazit předpovězené tarify zadané cesty, přidejte do metody následující kód `TestSinglePrediction` :</span><span class="sxs-lookup"><span data-stu-id="04c5b-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="04c5b-246">Spusťte program, abyste viděli předpovězené taxislužby jízdné za váš testovací případ.</span><span class="sxs-lookup"><span data-stu-id="04c5b-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="04c5b-247">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="04c5b-247">Congratulations!</span></span> <span data-ttu-id="04c5b-248">Teď jste úspěšně vytvořili model strojového učení pro předvídání tarifů taxislužby Trip, vyhodnotili jste jeho přesnost a použili ho k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="04c5b-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="04c5b-249">Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.</span><span class="sxs-lookup"><span data-stu-id="04c5b-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="04c5b-250">Další kroky</span><span class="sxs-lookup"><span data-stu-id="04c5b-250">Next steps</span></span>

<span data-ttu-id="04c5b-251">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="04c5b-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="04c5b-252">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="04c5b-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="04c5b-253">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="04c5b-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="04c5b-254">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="04c5b-254">Load and transform the data</span></span>
> * <span data-ttu-id="04c5b-255">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="04c5b-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="04c5b-256">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="04c5b-256">Train the model</span></span>
> * <span data-ttu-id="04c5b-257">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="04c5b-257">Evaluate the model</span></span>
> * <span data-ttu-id="04c5b-258">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="04c5b-258">Use the model for predictions</span></span>

<span data-ttu-id="04c5b-259">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="04c5b-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04c5b-260">Iris clustering</span><span class="sxs-lookup"><span data-stu-id="04c5b-260">Iris clustering</span></span>](iris-clustering.md)
