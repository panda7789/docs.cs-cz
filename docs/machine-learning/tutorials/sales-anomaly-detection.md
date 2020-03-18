---
title: 'Kurz: Detekce anomálií v prodeji produktů'
description: Zjistěte, jak vytvořit aplikaci pro detekci anomálií pro data o prodeji produktů. Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí jazyka C# v sadě Visual Studio 2019.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239986"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="7c82d-104">Kurz: Detekce anomálií v prodeji produktů s ML.NET</span><span class="sxs-lookup"><span data-stu-id="7c82d-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="7c82d-105">Zjistěte, jak vytvořit aplikaci pro detekci anomálií pro data o prodeji produktů.</span><span class="sxs-lookup"><span data-stu-id="7c82d-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="7c82d-106">Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí jazyka C# v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7c82d-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="7c82d-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="7c82d-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7c82d-108">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="7c82d-108">Load the data</span></span>
> * <span data-ttu-id="7c82d-109">Vytvoření transformace pro detekci anomálií špičky</span><span class="sxs-lookup"><span data-stu-id="7c82d-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="7c82d-110">Detekce spikač anomálie s transformací</span><span class="sxs-lookup"><span data-stu-id="7c82d-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="7c82d-111">Vytvoření transformace pro detekci anomálií bodů změny</span><span class="sxs-lookup"><span data-stu-id="7c82d-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="7c82d-112">Detekce anomálií bodů změny pomocí transformace</span><span class="sxs-lookup"><span data-stu-id="7c82d-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="7c82d-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)</span><span class="sxs-lookup"><span data-stu-id="7c82d-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c82d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c82d-114">Prerequisites</span></span>

* <span data-ttu-id="7c82d-115">[Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".</span><span class="sxs-lookup"><span data-stu-id="7c82d-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="7c82d-116">Datová sada product-sales.csv</span><span class="sxs-lookup"><span data-stu-id="7c82d-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="7c82d-117">Formát dat `product-sales.csv` v je založen na datové sadě "Shampoo Sales Over a Three Year Period" původně pořízené z DataMarketu a poskytované Datovou knihovnou Time Series (TSDL), kterou vytvořil Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="7c82d-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="7c82d-118">Dataset "Shampoo Sales Over a Three Year Period" s licencí pod výchozí otevřenou licencí DataMarket.</span><span class="sxs-lookup"><span data-stu-id="7c82d-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7c82d-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="7c82d-119">Create a console application</span></span>

1. <span data-ttu-id="7c82d-120">Vytvořte **aplikaci .NET Core Console** s názvem ProductSalesAnomalyDetection.</span><span class="sxs-lookup"><span data-stu-id="7c82d-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="7c82d-121">Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.</span><span class="sxs-lookup"><span data-stu-id="7c82d-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="7c82d-122">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="7c82d-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="7c82d-123">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7c82d-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7c82d-124">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML** a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="7c82d-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="7c82d-125">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="7c82d-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="7c82d-126">Opakujte tento postup pro **Microsoft.ML.TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="7c82d-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="7c82d-127">V horní `using` části *Program.cs* souboru přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="7c82d-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="7c82d-128">Stažení dat</span><span class="sxs-lookup"><span data-stu-id="7c82d-128">Download your data</span></span>

1. <span data-ttu-id="7c82d-129">Stáhněte si datovou sadu a uložte ji do dříve vytvořené *datové* složky:</span><span class="sxs-lookup"><span data-stu-id="7c82d-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="7c82d-130">Klikněte pravým tlačítkem myši na [*produkt-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte "Uložit odkaz (nebo cíl) Jako ..."</span><span class="sxs-lookup"><span data-stu-id="7c82d-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="7c82d-131">Ujistěte se, \*že soubor .csv uložíte do složky *Data,* nebo jej po uložení jinde přesuňte \*do složky *Data.*</span><span class="sxs-lookup"><span data-stu-id="7c82d-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="7c82d-132">V Průzkumníku řešení klepněte pravým tlačítkem \*myši na soubor .csv a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7c82d-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="7c82d-133">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="7c82d-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="7c82d-134">Následující tabulka obsahuje náhled dat \*ze souboru .csv:</span><span class="sxs-lookup"><span data-stu-id="7c82d-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="7c82d-135">Month</span><span class="sxs-lookup"><span data-stu-id="7c82d-135">Month</span></span>  |<span data-ttu-id="7c82d-136">Prodej produktů</span><span class="sxs-lookup"><span data-stu-id="7c82d-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="7c82d-137">1-Jan</span><span class="sxs-lookup"><span data-stu-id="7c82d-137">1-Jan</span></span>  |    <span data-ttu-id="7c82d-138">271</span><span class="sxs-lookup"><span data-stu-id="7c82d-138">271</span></span>      |
|<span data-ttu-id="7c82d-139">2-Jan</span><span class="sxs-lookup"><span data-stu-id="7c82d-139">2-Jan</span></span>  |    <span data-ttu-id="7c82d-140">150.9</span><span class="sxs-lookup"><span data-stu-id="7c82d-140">150.9</span></span>    |
|<span data-ttu-id="7c82d-141">.....</span><span class="sxs-lookup"><span data-stu-id="7c82d-141">.....</span></span>  |    <span data-ttu-id="7c82d-142">.....</span><span class="sxs-lookup"><span data-stu-id="7c82d-142">.....</span></span>    |
|<span data-ttu-id="7c82d-143">1-Únor</span><span class="sxs-lookup"><span data-stu-id="7c82d-143">1-Feb</span></span>  |    <span data-ttu-id="7c82d-144">199.3</span><span class="sxs-lookup"><span data-stu-id="7c82d-144">199.3</span></span>    |
|<span data-ttu-id="7c82d-145">.....</span><span class="sxs-lookup"><span data-stu-id="7c82d-145">.....</span></span>  |    <span data-ttu-id="7c82d-146">.....</span><span class="sxs-lookup"><span data-stu-id="7c82d-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="7c82d-147">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="7c82d-147">Create classes and define paths</span></span>

<span data-ttu-id="7c82d-148">Dále definujte struktury dat vstupní a předpověď třídy.</span><span class="sxs-lookup"><span data-stu-id="7c82d-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="7c82d-149">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="7c82d-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="7c82d-150">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a potom vyberte **přidat > novou položku**.</span><span class="sxs-lookup"><span data-stu-id="7c82d-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="7c82d-151">V **dialogovém okně Přidat novou položku**vyberte **Třídu** a změňte pole **Název** na *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="7c82d-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="7c82d-152">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="7c82d-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="7c82d-153">V editoru kódu se otevře *soubor ProductSalesData.cs.*</span><span class="sxs-lookup"><span data-stu-id="7c82d-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="7c82d-154">Na začátek `using` *ProductSalesData.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="7c82d-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="7c82d-155">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, do souboru *ProductSalesData.cs:*</span><span class="sxs-lookup"><span data-stu-id="7c82d-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="7c82d-156">`ProductSalesData`určuje třídu vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="7c82d-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="7c82d-157">Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny.</span><span class="sxs-lookup"><span data-stu-id="7c82d-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="7c82d-158">`ProductSalesPrediction`určuje třídu dat předpověď.</span><span class="sxs-lookup"><span data-stu-id="7c82d-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="7c82d-159">Pro detekci anomálií předpověď se skládá z výstrahy k označení, zda je anomálie, nezpracované skóre a p-hodnota.</span><span class="sxs-lookup"><span data-stu-id="7c82d-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="7c82d-160">Čím blíže je hodnota p 0, tím je pravděpodobnější, že došlo k anomálii.</span><span class="sxs-lookup"><span data-stu-id="7c82d-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="7c82d-161">Vytvořte dvě globální pole pro uložení cesty k nedávno stažené datové sadě a cesty k uloženému souboru modelu:</span><span class="sxs-lookup"><span data-stu-id="7c82d-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="7c82d-162">`_dataPath`má cestu k datové sadě použité k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="7c82d-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="7c82d-163">`_docsize`má počet záznamů v souboru datové sady.</span><span class="sxs-lookup"><span data-stu-id="7c82d-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="7c82d-164">Budete používat `_docSize` k `pvalueHistoryLength`výpočtu .</span><span class="sxs-lookup"><span data-stu-id="7c82d-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="7c82d-165">Přidejte následující kód na řádek `Main` přímo nad metodou a určete tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="7c82d-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="7c82d-166">Inicializovat proměnné v hlavní</span><span class="sxs-lookup"><span data-stu-id="7c82d-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="7c82d-167">Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro `mlContext` deklarování a inicializaci proměnné:</span><span class="sxs-lookup"><span data-stu-id="7c82d-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="7c82d-168">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="7c82d-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7c82d-169">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="7c82d-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="7c82d-170">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="7c82d-170">Load the data</span></span>

<span data-ttu-id="7c82d-171">Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="7c82d-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7c82d-172">`IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových).</span><span class="sxs-lookup"><span data-stu-id="7c82d-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="7c82d-173">Data lze načíst z textového souboru nebo z jiných zdrojů (například databáze SQL nebo souborů protokolu) do objektu. `IDataView`</span><span class="sxs-lookup"><span data-stu-id="7c82d-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="7c82d-174">Jako další řádek `Main()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7c82d-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="7c82d-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru.</span><span class="sxs-lookup"><span data-stu-id="7c82d-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="7c82d-176">Přebírá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="7c82d-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="7c82d-177">Detekce anomálií časových řad</span><span class="sxs-lookup"><span data-stu-id="7c82d-177">Time series anomaly detection</span></span>

<span data-ttu-id="7c82d-178">Detekce anomálií příznaky neočekávané nebo neobvyklé události nebo chování.</span><span class="sxs-lookup"><span data-stu-id="7c82d-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="7c82d-179">To dává vodítka, kde hledat problémy a pomůže vám odpovědět na otázku "Je to divné?".</span><span class="sxs-lookup"><span data-stu-id="7c82d-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Příklad detekce anomálií "Je to divné".](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="7c82d-181">Detekce anomálií je proces detekce odlehlých časových řad; body na dané vstupní časové řady, kde chování není to, co bylo očekáváno, nebo "divný".</span><span class="sxs-lookup"><span data-stu-id="7c82d-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="7c82d-182">Detekce anomálií může být užitečná mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="7c82d-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="7c82d-183">Například:</span><span class="sxs-lookup"><span data-stu-id="7c82d-183">For instance:</span></span>

<span data-ttu-id="7c82d-184">Pokud máte auto, možná budete chtít vědět: Je to olejoměr čtení normální, nebo mám únik?</span><span class="sxs-lookup"><span data-stu-id="7c82d-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="7c82d-185">Pokud sledujete spotřebu energie, chtěli byste vědět: Existuje výpadek?</span><span class="sxs-lookup"><span data-stu-id="7c82d-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="7c82d-186">Existují dva typy anomálií časových řad, které lze zjistit:</span><span class="sxs-lookup"><span data-stu-id="7c82d-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="7c82d-187">**Hroty** označují dočasné výbuchy anomálníchování v systému.</span><span class="sxs-lookup"><span data-stu-id="7c82d-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="7c82d-188">**Body změny** označují začátek trvalých změn v průběhu času v systému.</span><span class="sxs-lookup"><span data-stu-id="7c82d-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="7c82d-189">V ML.NET jsou algoritmy detekce špičky IID nebo iid change point vhodné pro [nezávislé a identicky distribuované datové sady](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="7c82d-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="7c82d-190">Na rozdíl od modelů v jiných kurzech transformace detektoru anomálií časové řady pracují přímo na vstupních datech.</span><span class="sxs-lookup"><span data-stu-id="7c82d-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="7c82d-191">Metoda `IEstimator.Fit()` nepotřebuje trénovací data k vytvoření transformace.</span><span class="sxs-lookup"><span data-stu-id="7c82d-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="7c82d-192">Je třeba schéma dat i když, který je poskytován zobrazení dat generované z `ProductSalesData`prázdného seznamu .</span><span class="sxs-lookup"><span data-stu-id="7c82d-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="7c82d-193">Budete analyzovat stejná data o prodeji produktů, abyste zjistili špičky a body změny.</span><span class="sxs-lookup"><span data-stu-id="7c82d-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="7c82d-194">Proces modelu budovy a školení je stejný pro detekci špičky a detekci bodů změny; hlavním rozdílem je specifický detekční algoritmus.</span><span class="sxs-lookup"><span data-stu-id="7c82d-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="7c82d-195">Detekce špičky</span><span class="sxs-lookup"><span data-stu-id="7c82d-195">Spike detection</span></span>

<span data-ttu-id="7c82d-196">Cílem detekce špičky je identifikovat náhlé, ale dočasné shluky, které se výrazně liší od většiny hodnot dat časových řad.</span><span class="sxs-lookup"><span data-stu-id="7c82d-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="7c82d-197">Je důležité zjistit tyto podezřelé vzácné položky, události nebo pozorování včas minimalizovat.</span><span class="sxs-lookup"><span data-stu-id="7c82d-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="7c82d-198">Následující přístup lze použít k detekci různých anomálií, jako jsou: výpadky, kybernetické útoky nebo virální webový obsah.</span><span class="sxs-lookup"><span data-stu-id="7c82d-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="7c82d-199">Následující obrázek je příkladem špičky v datové sadě časové řady:</span><span class="sxs-lookup"><span data-stu-id="7c82d-199">The following image is an example of spikes in a time series dataset:</span></span>

![Snímek obrazovky, který zobrazuje dvě detekce špičky.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="7c82d-201">Přidejte metodu CreateEmptyDataView().</span><span class="sxs-lookup"><span data-stu-id="7c82d-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="7c82d-202">Do této metody `Program.cs`přidejte následující metodu :</span><span class="sxs-lookup"><span data-stu-id="7c82d-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="7c82d-203">Vytvoří `CreateEmptyDataView()` prázdný objekt zobrazení dat se správným schématem, které má `IEstimator.Fit()` být použito jako vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="7c82d-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="7c82d-204">Vytvořit metodu DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="7c82d-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="7c82d-205">Metoda: `DetectSpike()`</span><span class="sxs-lookup"><span data-stu-id="7c82d-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="7c82d-206">Vytvoří transformaci z odhadu.</span><span class="sxs-lookup"><span data-stu-id="7c82d-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="7c82d-207">Detekuje špičky na základě historických dat prodeje.</span><span class="sxs-lookup"><span data-stu-id="7c82d-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="7c82d-208">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="7c82d-208">Displays the results.</span></span>

1. <span data-ttu-id="7c82d-209">Vytvořte `DetectSpike()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7c82d-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="7c82d-210">Použijte [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) trénovat model pro detekci špičky.</span><span class="sxs-lookup"><span data-stu-id="7c82d-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="7c82d-211">Přidejte ji `DetectSpike()` do metody s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7c82d-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="7c82d-212">Vytvořte transformaci detekce špičky přidáním následujícího `DetectSpike()` jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="7c82d-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="7c82d-213">Přidejte následující řádek kódu `productSales` pro transformaci dat jako `DetectSpike()` další řádek v metodě:</span><span class="sxs-lookup"><span data-stu-id="7c82d-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="7c82d-214">Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda, aby předpovědi pro více vstupních řádků datové sady.</span><span class="sxs-lookup"><span data-stu-id="7c82d-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="7c82d-215">Převeďte svůj `transformedData` na silně `IEnumerable` zadaný pro snadnější zobrazení pomocí [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metoda s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7c82d-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="7c82d-216">Vytvořte řádek záhlaví zobrazení <xref:System.Console.WriteLine?displayProperty=nameWithType> pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7c82d-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="7c82d-217">Ve výsledcích detekce špičky se zobrazí následující informace:</span><span class="sxs-lookup"><span data-stu-id="7c82d-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="7c82d-218">`Alert`označuje upozornění na špičku pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="7c82d-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="7c82d-219">`Score`je `ProductSales` hodnota pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="7c82d-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="7c82d-220">`P-Value`"P" znamená pravděpodobnost.</span><span class="sxs-lookup"><span data-stu-id="7c82d-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="7c82d-221">Čím blíže je hodnota p na hodnotu 0, tím je pravděpodobnější, že datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="7c82d-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="7c82d-222">Použijte následující kód k iterátu `predictions` `IEnumerable` prostřednictvím a zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="7c82d-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="7c82d-223">Přidejte volání `DetectSpike()`metody v `Main()` metodě:</span><span class="sxs-lookup"><span data-stu-id="7c82d-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="7c82d-224">Výsledky detekce špičky</span><span class="sxs-lookup"><span data-stu-id="7c82d-224">Spike detection results</span></span>

<span data-ttu-id="7c82d-225">Vaše výsledky by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="7c82d-225">Your results should be similar to the following.</span></span> <span data-ttu-id="7c82d-226">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7c82d-226">During processing, messages are displayed.</span></span> <span data-ttu-id="7c82d-227">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7c82d-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="7c82d-228">Některé zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="7c82d-228">Some of the messages have been removed from the following results for clarity.</span></span>

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a><span data-ttu-id="7c82d-229">Detekce bodu změny</span><span class="sxs-lookup"><span data-stu-id="7c82d-229">Change point detection</span></span>

<span data-ttu-id="7c82d-230">`Change points`jsou trvalé změny v rozdělení datových proudů událostí časové řady hodnot, jako jsou změny úrovně a trendy.</span><span class="sxs-lookup"><span data-stu-id="7c82d-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="7c82d-231">Tyto trvalé změny trvají `spikes` mnohem déle než katastrofické události.</span><span class="sxs-lookup"><span data-stu-id="7c82d-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="7c82d-232">`Change points`nejsou obvykle viditelné pouhým okem, ale mohou být detekovány ve vašich datech pomocí přístupů, například v následující metodě.</span><span class="sxs-lookup"><span data-stu-id="7c82d-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="7c82d-233">Následující obrázek je příkladem detekce bodu změny:</span><span class="sxs-lookup"><span data-stu-id="7c82d-233">The following image is an example of a change point detection:</span></span>

![Snímek obrazovky, který zobrazuje detekci bodu změny.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="7c82d-235">Vytvoření metody DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="7c82d-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="7c82d-236">Metoda `DetectChangepoint()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="7c82d-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="7c82d-237">Vytvoří transformaci z odhadu.</span><span class="sxs-lookup"><span data-stu-id="7c82d-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="7c82d-238">Detekuje body změn na základě historických dat o prodeji.</span><span class="sxs-lookup"><span data-stu-id="7c82d-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="7c82d-239">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="7c82d-239">Displays the results.</span></span>

1. <span data-ttu-id="7c82d-240">Vytvořte `DetectChangepoint()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7c82d-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="7c82d-241">Vytvořte [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) `DetectChangepoint()` v metodě s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7c82d-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="7c82d-242">Stejně jako dříve vytvořte transformaci z odhadu přidáním následujícího řádku kódu do `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="7c82d-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="7c82d-243">Pomocí `Transform()` metody transformujte data přidáním následujícího kódu do `DetectChangePoint()`aplikace :</span><span class="sxs-lookup"><span data-stu-id="7c82d-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="7c82d-244">Stejně jako dříve `transformedData` převeďte svůj na `IEnumerable` silně zadaný `CreateEnumerable()`pro snadnější zobrazení pomocí metody s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7c82d-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="7c82d-245">Vytvořte záhlaví zobrazení s následujícím kódem `DetectChangePoint()` jako další řádek v metodě:</span><span class="sxs-lookup"><span data-stu-id="7c82d-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="7c82d-246">Ve výsledcích zjišťování bodů změny se zobrazí následující informace:</span><span class="sxs-lookup"><span data-stu-id="7c82d-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="7c82d-247">`Alert`označuje výstrahu bodu změny pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="7c82d-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="7c82d-248">`Score`je `ProductSales` hodnota pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="7c82d-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="7c82d-249">`P-Value`"P" znamená pravděpodobnost.</span><span class="sxs-lookup"><span data-stu-id="7c82d-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="7c82d-250">Čím blíže je hodnota P na hodnotu 0, tím je pravděpodobnější, že datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="7c82d-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="7c82d-251">`Martingale value`se používá k identifikaci, jak "divný" datový bod je, na základě sekvence P-hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7c82d-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="7c82d-252">Iterate prostřednictvím `predictions` `IEnumerable` a zobrazit výsledky s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7c82d-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="7c82d-253">Přidejte do `DetectChangepoint()`metody v `Main()` metodě následující volání:</span><span class="sxs-lookup"><span data-stu-id="7c82d-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="7c82d-254">Výsledky zjišťování bodu změny</span><span class="sxs-lookup"><span data-stu-id="7c82d-254">Change point detection results</span></span>

<span data-ttu-id="7c82d-255">Vaše výsledky by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="7c82d-255">Your results should be similar to the following.</span></span> <span data-ttu-id="7c82d-256">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7c82d-256">During processing, messages are displayed.</span></span> <span data-ttu-id="7c82d-257">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7c82d-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="7c82d-258">Některé zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="7c82d-258">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

<span data-ttu-id="7c82d-259">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="7c82d-259">Congratulations!</span></span> <span data-ttu-id="7c82d-260">Nyní jste úspěšně vytvořili modely strojového učení pro detekci špiček a anomálií bodů změny v prodejních datech.</span><span class="sxs-lookup"><span data-stu-id="7c82d-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="7c82d-261">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)</span><span class="sxs-lookup"><span data-stu-id="7c82d-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="7c82d-262">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="7c82d-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7c82d-263">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="7c82d-263">Load the data</span></span>
> * <span data-ttu-id="7c82d-264">Trénování modelu pro detekci anomálií špičky</span><span class="sxs-lookup"><span data-stu-id="7c82d-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="7c82d-265">Detekce spikač anomálie s trénovaný model</span><span class="sxs-lookup"><span data-stu-id="7c82d-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="7c82d-266">Trénování modelu pro detekci anomálií bodu změny</span><span class="sxs-lookup"><span data-stu-id="7c82d-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="7c82d-267">Detekce anomálií bodů změny pomocí trénovaného režimu</span><span class="sxs-lookup"><span data-stu-id="7c82d-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c82d-268">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7c82d-268">Next steps</span></span>

<span data-ttu-id="7c82d-269">Podívejte se na ukázky machine learningu úložiště GitHub a prozkoumejte ukázku detekce anomálií spotřeby spotřeby.</span><span class="sxs-lookup"><span data-stu-id="7c82d-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7c82d-270">úložiště GitHub u dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="7c82d-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
