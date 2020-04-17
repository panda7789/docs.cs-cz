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
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="887e0-103">Kurz: Předvídejte ceny pomocí regrese s ML.NET</span><span class="sxs-lookup"><span data-stu-id="887e0-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="887e0-104">Tento kurz ukazuje, jak vytvořit [regresní model](../resources/glossary.md#regression) pomocí ML.NET předpovědět ceny, konkrétně new york city taxi tarify.</span><span class="sxs-lookup"><span data-stu-id="887e0-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="887e0-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="887e0-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="887e0-106">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="887e0-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="887e0-107">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="887e0-107">Load and transform the data</span></span>
> * <span data-ttu-id="887e0-108">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="887e0-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="887e0-109">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-109">Train the model</span></span>
> * <span data-ttu-id="887e0-110">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-110">Evaluate the model</span></span>
> * <span data-ttu-id="887e0-111">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="887e0-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="887e0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="887e0-112">Prerequisites</span></span>

* <span data-ttu-id="887e0-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="887e0-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="887e0-114">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="887e0-114">Create a console application</span></span>

1. <span data-ttu-id="887e0-115">Vytvořte **aplikaci .NET Core Console s** názvem "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="887e0-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="887e0-116">Vytvořte adresář s názvem *Data* v projektu pro uložení datové sady a souborů modelu.</span><span class="sxs-lookup"><span data-stu-id="887e0-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="887e0-117">Nainstalujte **balíček nuget Microsoft.ML:**</span><span class="sxs-lookup"><span data-stu-id="887e0-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="887e0-118">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="887e0-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="887e0-119">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet,** vyhledejte **Microsoft.ML**, vyberte balíček v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="887e0-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="887e0-120">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="887e0-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="887e0-121">Proveďte totéž pro balíček **Microsoft.ML.FastTree** NuGet.</span><span class="sxs-lookup"><span data-stu-id="887e0-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="887e0-122">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="887e0-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="887e0-123">Stáhněte si datové sady [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) a uložte je do složky *Data,* kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="887e0-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="887e0-124">Tyto datové sady používáme k trénování modelu strojového učení a následnému vyhodnocení, jak přesný je model.</span><span class="sxs-lookup"><span data-stu-id="887e0-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="887e0-125">Tyto datové sady jsou původně z [NYC TLC Taxi Trip datové sady](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span><span class="sxs-lookup"><span data-stu-id="887e0-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="887e0-126">V **Průzkumníku řešení**klepněte \*pravým tlačítkem myši na jednotlivé soubory CSV a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="887e0-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="887e0-127">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="887e0-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="887e0-128">Otevřete datovou sadu **taxi-fare-train.csv** a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="887e0-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="887e0-129">Podívejte se na každý sloupec.</span><span class="sxs-lookup"><span data-stu-id="887e0-129">Take a look at each of the columns.</span></span> <span data-ttu-id="887e0-130">Porozumějte datům a rozhodněte, které sloupce jsou **prvky** a které jsou **popiskem**.</span><span class="sxs-lookup"><span data-stu-id="887e0-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="887e0-131">Je `label` sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="887e0-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="887e0-132">Identifikované `Features`jsou vstupy, které poskytnete `Label`modelu předpovědět .</span><span class="sxs-lookup"><span data-stu-id="887e0-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="887e0-133">Zadaný soubor dat obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="887e0-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="887e0-134">**vendor_id:** ID dodavatele taxi služby je funkce.</span><span class="sxs-lookup"><span data-stu-id="887e0-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="887e0-135">**rate_code:** Typ sazby taxi cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="887e0-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="887e0-136">**passenger_count:** Počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="887e0-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="887e0-137">**trip_time_in_secs:** Doba, po kterou cesta trvala.</span><span class="sxs-lookup"><span data-stu-id="887e0-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="887e0-138">Chcete předpovědět jízdné cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="887e0-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="887e0-139">V tu chvíli nevíte, jak dlouho by cesta zabrala.</span><span class="sxs-lookup"><span data-stu-id="887e0-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="887e0-140">Doba jízdy tedy není funkcí a tento sloupec z modelu vyloučíte.</span><span class="sxs-lookup"><span data-stu-id="887e0-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="887e0-141">**trip_distance:** Vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="887e0-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="887e0-142">**payment_type:** Platební metoda (v hotovosti nebo kreditní kartou) je funkce.</span><span class="sxs-lookup"><span data-stu-id="887e0-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="887e0-143">**fare_amount:** Celková zaplacená taxi služba je štítek.</span><span class="sxs-lookup"><span data-stu-id="887e0-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="887e0-144">Vytvoření tříd dat</span><span class="sxs-lookup"><span data-stu-id="887e0-144">Create data classes</span></span>

<span data-ttu-id="887e0-145">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="887e0-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="887e0-146">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="887e0-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="887e0-147">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="887e0-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="887e0-148">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="887e0-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="887e0-149">Do nového souboru přidejte následující `using` direktivy:</span><span class="sxs-lookup"><span data-stu-id="887e0-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="887e0-150">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, do souboru *TaxiTrip.cs:*</span><span class="sxs-lookup"><span data-stu-id="887e0-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="887e0-151">`TaxiTrip`je třída vstupních dat a obsahuje definice pro každý sloupec sady dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="887e0-152">Pomocí <xref:Microsoft.ML.Data.LoadColumnAttribute> atributu můžete určit indexy zdrojových sloupců v sadě dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="887e0-153">Třída `TaxiTripFarePrediction` představuje předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="887e0-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="887e0-154">Má jedno plovoucí pole `FareAmount`, `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> s aplikovaným atributem.</span><span class="sxs-lookup"><span data-stu-id="887e0-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="887e0-155">V případě regresní úlohy obsahuje sloupec **Skóre** předpokládané hodnoty popisků.</span><span class="sxs-lookup"><span data-stu-id="887e0-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="887e0-156">Použijte `float` typ k reprezentaci hodnot s plovoucí desetinnou desetinnou třídou vstupních dat a predikcí.</span><span class="sxs-lookup"><span data-stu-id="887e0-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="887e0-157">Definování dat a cest modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-157">Define data and model paths</span></span>

<span data-ttu-id="887e0-158">Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:</span><span class="sxs-lookup"><span data-stu-id="887e0-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="887e0-159">Chcete-li uložit model, musíte vytvořit tři pole, která uchovává cesty k souborům se sadami dat a souborem:</span><span class="sxs-lookup"><span data-stu-id="887e0-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="887e0-160">`_trainDataPath`obsahuje cestu k souboru se sadou dat použitou k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="887e0-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="887e0-161">`_testDataPath`obsahuje cestu k souboru se sadou dat použitou k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="887e0-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="887e0-162">`_modelPath`obsahuje cestu k souboru, kde je uložen trénovaný model.</span><span class="sxs-lookup"><span data-stu-id="887e0-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="887e0-163">Přidejte následující kód `Main` přímo nad metodu k `_textLoader` určení těchto cest a pro proměnnou:</span><span class="sxs-lookup"><span data-stu-id="887e0-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="887e0-164">Všechny operace ML.NET spustit ve [třídě MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="887e0-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="887e0-165">Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="887e0-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="887e0-166">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="887e0-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="887e0-167">Inicializovat proměnné v hlavní</span><span class="sxs-lookup"><span data-stu-id="887e0-167">Initialize variables in Main</span></span>

<span data-ttu-id="887e0-168">Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro `mlContext` deklarování a inicializaci proměnné:</span><span class="sxs-lookup"><span data-stu-id="887e0-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="887e0-169">Přidejte následující jako další řádek `Main` kódu v `Train` metodě pro volání metody:</span><span class="sxs-lookup"><span data-stu-id="887e0-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="887e0-170">Metoda `Train()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="887e0-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="887e0-171">Načte data.</span><span class="sxs-lookup"><span data-stu-id="887e0-171">Loads the data.</span></span>
* <span data-ttu-id="887e0-172">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="887e0-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="887e0-173">Trénuje model.</span><span class="sxs-lookup"><span data-stu-id="887e0-173">Trains the model.</span></span>
* <span data-ttu-id="887e0-174">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="887e0-174">Returns the model.</span></span>

<span data-ttu-id="887e0-175">Metoda `Train` trénuje model.</span><span class="sxs-lookup"><span data-stu-id="887e0-175">The `Train` method trains the model.</span></span> <span data-ttu-id="887e0-176">Vytvořte tuto `Main`metodu těsně pod , pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="887e0-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="887e0-177">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="887e0-177">Load and transform data</span></span>

<span data-ttu-id="887e0-178">ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisu číselných nebo textových tabulkových dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="887e0-179">`IDataView`můžete načíst textové soubory nebo v reálném čase (například SQL database nebo log files).</span><span class="sxs-lookup"><span data-stu-id="887e0-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="887e0-180">Jako první řádek `Train()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="887e0-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="887e0-181">Jak chcete předpovědět taxi výlet jízdného, `FareAmount` `Label` sloupec je, že budete předvídat (výstup modelu).</span><span class="sxs-lookup"><span data-stu-id="887e0-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="887e0-182">Použijte `CopyColumnsEstimator` třídu transformace `FareAmount`ke kopírování a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="887e0-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="887e0-183">Algoritmus, který trénuje model, vyžaduje **číselné** funkce,`VendorId`takže `RateCode`je `PaymentType`třeba transformovat`VendorIdEncoded`hodnoty `RateCodeEncoded`kategorických dat ( , , a ) na čísla ( , , a `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="887e0-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="887e0-184">Chcete-li to provést, použijte třídu transformace [OneHotEncodingTransformer,](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) která přiřadí různé číselné hodnoty klíče různým hodnotám v každém sloupci, a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="887e0-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="887e0-185">Poslední krok v přípravě dat kombinuje všechny **Features** sloupce funkce `mlContext.Transforms.Concatenate` do sloupce Funkce pomocí třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="887e0-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="887e0-186">Ve výchozím nastavení algoritmus učení zpracovává pouze funkce ze sloupce **Funkce.**</span><span class="sxs-lookup"><span data-stu-id="887e0-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="887e0-187">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="887e0-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="887e0-188">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="887e0-188">Choose a learning algorithm</span></span>

<span data-ttu-id="887e0-189">Tento problém je o předpovídání taxi výlet jízdného v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="887e0-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="887e0-190">Na první pohled se může zdát, že závisí pouze na ujeté vzdálenosti.</span><span class="sxs-lookup"><span data-stu-id="887e0-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="887e0-191">Prodejci taxi služeb v New Yorku však účtují různé částky za další faktory, jako jsou další cestující nebo placení kreditní kartou místo hotovosti.</span><span class="sxs-lookup"><span data-stu-id="887e0-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="887e0-192">Chcete předpovědět hodnotu ceny, což je reálná hodnota, na základě dalších faktorů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="887e0-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="887e0-193">Chcete-li to provést, můžete zvolit úlohu [regrese](../resources/glossary.md#regression) strojového učení.</span><span class="sxs-lookup"><span data-stu-id="887e0-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="887e0-194">Přidejte úlohu strojového učení [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) k definicím transformace dat přidáním následujícího jako následující řádek kódu v aplikaci `Train()`:</span><span class="sxs-lookup"><span data-stu-id="887e0-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="887e0-195">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-195">Train the model</span></span>

<span data-ttu-id="887e0-196">Připevněte model `dataview` do tréninku a vraťte trénovaný `Train()` model přidáním následujícího řádku kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="887e0-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="887e0-197">[Metoda Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trénuje váš model transformací datové sady a použitím školení.</span><span class="sxs-lookup"><span data-stu-id="887e0-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="887e0-198">Vrátit trénovaný model s následujícím `Train()` řádkem kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="887e0-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="887e0-199">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-199">Evaluate the model</span></span>

<span data-ttu-id="887e0-200">Dále vyhodnoťte výkon modelu pomocí testovacích dat pro zajištění kvality a ověření.</span><span class="sxs-lookup"><span data-stu-id="887e0-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="887e0-201">Vytvořte `Evaluate()` metodu, `Train()`těsně po , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="887e0-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="887e0-202">Metoda `Evaluate` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="887e0-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="887e0-203">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="887e0-203">Loads the test dataset.</span></span>
* <span data-ttu-id="887e0-204">Vytvoří regresní vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="887e0-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="887e0-205">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="887e0-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="887e0-206">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="887e0-206">Displays the metrics.</span></span>

<span data-ttu-id="887e0-207">Přidejte volání nové metody `Main` z metody, `Train` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="887e0-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="887e0-208">Načtěte testovací datovou sadu pomocí metody [LoadFromTextFile().](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A)</span><span class="sxs-lookup"><span data-stu-id="887e0-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="887e0-209">Vyhodnoťte model pomocí této datové sady `Evaluate` jako kontrolu kvality přidáním následujícího kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="887e0-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="887e0-210">Dále transformujte `Test` data přidáním následujícího kódu do `Evaluate()`aplikace :</span><span class="sxs-lookup"><span data-stu-id="887e0-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="887e0-211">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) Metoda umožňuje předpovědi pro vstupní řádky testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="887e0-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="887e0-212">Metoda `RegressionContext.Evaluate` vypočítá metriky kvality pro `PredictionModel` použití zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="887e0-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="887e0-213">Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkové metriky vypočítané regresními vyhodnoceními.</span><span class="sxs-lookup"><span data-stu-id="887e0-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="887e0-214">Chcete-li zobrazit tyto určit kvalitu modelu, musíte nejprve získat metriky.</span><span class="sxs-lookup"><span data-stu-id="887e0-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="887e0-215">Jako další řádek `Evaluate` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="887e0-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="887e0-216">Jakmile máte předpověď nastavit, [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metoda vyhodnotí model, který porovnává předpovídané hodnoty s aktuální `Labels` v testovací datové sady a vrátí metriky o tom, jak model funguje.</span><span class="sxs-lookup"><span data-stu-id="887e0-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="887e0-217">Přidejte následující kód k vyhodnocení modelu a vytvoření metriky hodnocení:</span><span class="sxs-lookup"><span data-stu-id="887e0-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="887e0-218">[RSquared](../resources/glossary.md#coefficient-of-determination) je další hodnotící metrika regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="887e0-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="887e0-219">RSquared trvá hodnoty mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="887e0-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="887e0-220">Čím blíže je jeho hodnota 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="887e0-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="887e0-221">Přidejte do metody `Evaluate` následující kód pro zobrazení hodnoty RSquared:</span><span class="sxs-lookup"><span data-stu-id="887e0-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="887e0-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) je jednou z hodnotících metrik regresního modelu.</span><span class="sxs-lookup"><span data-stu-id="887e0-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="887e0-223">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="887e0-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="887e0-224">Přidejte do metody `Evaluate` následující kód pro zobrazení hodnoty služby RMS:</span><span class="sxs-lookup"><span data-stu-id="887e0-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="887e0-225">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="887e0-225">Use the model for predictions</span></span>

<span data-ttu-id="887e0-226">Vytvořte `TestSinglePrediction` metodu, `Evaluate` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="887e0-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="887e0-227">Metoda `TestSinglePrediction` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="887e0-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="887e0-228">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="887e0-229">Předpovídá částku jízdného na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="887e0-230">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="887e0-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="887e0-231">Zobrazí předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="887e0-231">Displays the predicted results.</span></span>

<span data-ttu-id="887e0-232">Přidejte volání nové metody `Main` z metody, `Evaluate` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="887e0-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="887e0-233">Použijte `PredictionEngine` předpovědět jízdné přidáním následujícího `TestSinglePrediction()`kódu:</span><span class="sxs-lookup"><span data-stu-id="887e0-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="887e0-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="887e0-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="887e0-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="887e0-236">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="887e0-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="887e0-237">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="887e0-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="887e0-238">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="887e0-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="887e0-239">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="887e0-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="887e0-240">Tento kurz používá jednu zkušební cestu v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="887e0-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="887e0-241">Později můžete přidat další scénáře experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="887e0-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="887e0-242">Přidejte výlet a otestujte predikci `TestSinglePrediction()` nákladů trénovaného `TaxiTrip`modelu v metodě vytvořením instance :</span><span class="sxs-lookup"><span data-stu-id="887e0-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="887e0-243">Dále předpovědět jízdné na základě jedné instance taxi data cesty `PredictionEngine` a předat ji tím, že přidá `TestSinglePrediction()` následující jako další řádky kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="887e0-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="887e0-244">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="887e0-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="887e0-245">Chcete-li zobrazit předpokládané jízdné zadané cesty, přidejte `TestSinglePrediction` do metody následující kód:</span><span class="sxs-lookup"><span data-stu-id="887e0-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="887e0-246">Spusťte program a podívejte se na předpokládané jízdné taxi pro váš testovací případ.</span><span class="sxs-lookup"><span data-stu-id="887e0-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="887e0-247">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="887e0-247">Congratulations!</span></span> <span data-ttu-id="887e0-248">Nyní jste úspěšně vytvořili model strojového učení pro předpovídání jízdného na taxi, vyhodnotili jste jeho přesnost a použili jste ho k předpovědím.</span><span class="sxs-lookup"><span data-stu-id="887e0-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="887e0-249">Zdrojový kód pro tento kurz najdete v úložišti [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction)</span><span class="sxs-lookup"><span data-stu-id="887e0-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="887e0-250">Další kroky</span><span class="sxs-lookup"><span data-stu-id="887e0-250">Next steps</span></span>

<span data-ttu-id="887e0-251">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="887e0-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="887e0-252">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="887e0-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="887e0-253">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="887e0-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="887e0-254">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="887e0-254">Load and transform the data</span></span>
> * <span data-ttu-id="887e0-255">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="887e0-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="887e0-256">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-256">Train the model</span></span>
> * <span data-ttu-id="887e0-257">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="887e0-257">Evaluate the model</span></span>
> * <span data-ttu-id="887e0-258">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="887e0-258">Use the model for predictions</span></span>

<span data-ttu-id="887e0-259">Přejdete k dalšímu kurzu, abyste se dozvěděli více.</span><span class="sxs-lookup"><span data-stu-id="887e0-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="887e0-260">Iris clustering</span><span class="sxs-lookup"><span data-stu-id="887e0-260">Iris clustering</span></span>](iris-clustering.md)
