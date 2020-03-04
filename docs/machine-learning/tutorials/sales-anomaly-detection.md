---
title: 'Kurz: zjištění anomálií v prodeji produktu'
description: Naučte se, jak vytvořit aplikaci pro detekci anomálií pro prodejní data produktu. Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí C# sady Visual Studio 2019.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239986"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="18829-104">Kurz: zjištění anomálií v prodeji produktů pomocí ML.NET</span><span class="sxs-lookup"><span data-stu-id="18829-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="18829-105">Naučte se, jak vytvořit aplikaci pro detekci anomálií pro prodejní data produktu.</span><span class="sxs-lookup"><span data-stu-id="18829-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="18829-106">Tento kurz vytvoří konzolovou aplikaci .NET Core pomocí C# sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="18829-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="18829-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="18829-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="18829-108">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="18829-108">Load the data</span></span>
> * <span data-ttu-id="18829-109">Vytvoření transformace pro detekci anomálií špičky</span><span class="sxs-lookup"><span data-stu-id="18829-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="18829-110">Zjištění anomálií špičky pomocí transformace</span><span class="sxs-lookup"><span data-stu-id="18829-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="18829-111">Vytvoření transformace pro detekci anomálií bodu změny</span><span class="sxs-lookup"><span data-stu-id="18829-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="18829-112">Detekovat anomálie změn bodů pomocí transformace</span><span class="sxs-lookup"><span data-stu-id="18829-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="18829-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .</span><span class="sxs-lookup"><span data-stu-id="18829-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18829-114">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="18829-114">Prerequisites</span></span>

* <span data-ttu-id="18829-115">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="18829-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="18829-116">Datová sada Product-Sales. csv</span><span class="sxs-lookup"><span data-stu-id="18829-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="18829-117">Formát dat v `product-sales.csv` vychází z datové sady "šampon Sales" za tříleté období "původně vytvořeného z datového trhu a poskytovaného službou Time Series data Library (TSDL), kterou vytvořila Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="18829-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="18829-118">"Nemožnost prodeje za tři roky v rámci" datové sady ", která je licencovaná na základě výchozího Open License pro datamarketo.</span><span class="sxs-lookup"><span data-stu-id="18829-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="18829-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="18829-119">Create a console application</span></span>

1. <span data-ttu-id="18829-120">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="18829-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="18829-121">Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.</span><span class="sxs-lookup"><span data-stu-id="18829-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="18829-122">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="18829-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="18829-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="18829-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="18829-124">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml** a vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="18829-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="18829-125">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="18829-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="18829-126">Opakujte tento postup pro **Microsoft. ml. časové řady**.</span><span class="sxs-lookup"><span data-stu-id="18829-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="18829-127">Do horní části souboru *program.cs* přidejte následující příkazy `using`:</span><span class="sxs-lookup"><span data-stu-id="18829-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="18829-128">Stažení dat</span><span class="sxs-lookup"><span data-stu-id="18829-128">Download your data</span></span>

1. <span data-ttu-id="18829-129">Stáhněte si datovou sadu a uložte ji do složky *dat* , kterou jste vytvořili dříve:</span><span class="sxs-lookup"><span data-stu-id="18829-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="18829-130">Klikněte pravým tlačítkem na [*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte Uložit odkaz (nebo cíl) jako...</span><span class="sxs-lookup"><span data-stu-id="18829-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="18829-131">Ujistěte se, že soubor \*. csv buď uložíte do složky *dat* , nebo když ho uložíte jinam, přesuňte soubor \*. CSV do složky *data* .</span><span class="sxs-lookup"><span data-stu-id="18829-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="18829-132">V Průzkumník řešení klikněte pravým tlačítkem na soubor \*. csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="18829-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="18829-133">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="18829-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="18829-134">Následující tabulka je náhled dat ze souboru \*. CSV:</span><span class="sxs-lookup"><span data-stu-id="18829-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="18829-135">Měsíc</span><span class="sxs-lookup"><span data-stu-id="18829-135">Month</span></span>  |<span data-ttu-id="18829-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="18829-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="18829-137">1 – leden</span><span class="sxs-lookup"><span data-stu-id="18829-137">1-Jan</span></span>  |    <span data-ttu-id="18829-138">271</span><span class="sxs-lookup"><span data-stu-id="18829-138">271</span></span>      |
|<span data-ttu-id="18829-139">2 – leden</span><span class="sxs-lookup"><span data-stu-id="18829-139">2-Jan</span></span>  |    <span data-ttu-id="18829-140">150,9</span><span class="sxs-lookup"><span data-stu-id="18829-140">150.9</span></span>    |
|<span data-ttu-id="18829-141">.....</span><span class="sxs-lookup"><span data-stu-id="18829-141">.....</span></span>  |    <span data-ttu-id="18829-142">.....</span><span class="sxs-lookup"><span data-stu-id="18829-142">.....</span></span>    |
|<span data-ttu-id="18829-143">1 – únor</span><span class="sxs-lookup"><span data-stu-id="18829-143">1-Feb</span></span>  |    <span data-ttu-id="18829-144">199,3</span><span class="sxs-lookup"><span data-stu-id="18829-144">199.3</span></span>    |
|<span data-ttu-id="18829-145">.....</span><span class="sxs-lookup"><span data-stu-id="18829-145">.....</span></span>  |    <span data-ttu-id="18829-146">.....</span><span class="sxs-lookup"><span data-stu-id="18829-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="18829-147">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="18829-147">Create classes and define paths</span></span>

<span data-ttu-id="18829-148">Dále definujte vstupní a předpovědní datové struktury třídy.</span><span class="sxs-lookup"><span data-stu-id="18829-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="18829-149">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="18829-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="18829-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="18829-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="18829-151">V **dialogovém okně Přidat novou položku**vyberte **třída** a změňte pole **název** na *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="18829-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="18829-152">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="18829-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="18829-153">V editoru kódu se otevře soubor *ProductSalesData.cs* .</span><span class="sxs-lookup"><span data-stu-id="18829-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="18829-154">Do horní části *ProductSalesData.cs*přidejte následující příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="18829-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="18829-155">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, do souboru *ProductSalesData.cs* :</span><span class="sxs-lookup"><span data-stu-id="18829-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="18829-156">`ProductSalesData` určuje vstupní datovou třídu.</span><span class="sxs-lookup"><span data-stu-id="18829-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="18829-157">Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny.</span><span class="sxs-lookup"><span data-stu-id="18829-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="18829-158">`ProductSalesPrediction` určuje třídu dat předpovědi.</span><span class="sxs-lookup"><span data-stu-id="18829-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="18829-159">Pro detekci anomálií se předpověď skládá z výstrahy, která indikuje, jestli existuje anomálie, hrubá skóre a hodnota p-.</span><span class="sxs-lookup"><span data-stu-id="18829-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="18829-160">Bližší hodnota p je 0, pravděpodobnější je, že došlo k anomálii.</span><span class="sxs-lookup"><span data-stu-id="18829-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="18829-161">Vytvořte dvě globální pole, která budou uchovávat nedávno staženou cestu k souboru datové sady a uloženou cestu k souboru modelu:</span><span class="sxs-lookup"><span data-stu-id="18829-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="18829-162">`_dataPath` má cestu k datové sadě, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="18829-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="18829-163">`_docsize` má počet záznamů v souboru DataSet.</span><span class="sxs-lookup"><span data-stu-id="18829-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="18829-164">K výpočtu `pvalueHistoryLength`použijete `_docSize`.</span><span class="sxs-lookup"><span data-stu-id="18829-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="18829-165">Přidejte následující kód na řádek vpravo nad `Main` metodou pro určení těchto cest:</span><span class="sxs-lookup"><span data-stu-id="18829-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="18829-166">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="18829-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="18829-167">Nahraďte `Console.WriteLine("Hello World!")` řádek v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="18829-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="18829-168">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="18829-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="18829-169">Je podobný a koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="18829-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="18829-170">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="18829-170">Load the data</span></span>

<span data-ttu-id="18829-171">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="18829-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="18829-172">`IDataView` je flexibilní a efektivní způsob popisující tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="18829-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="18829-173">Data je možné načíst z textového souboru nebo z jiných zdrojů (například databáze SQL nebo souborů protokolu) do objektu `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="18829-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="18829-174">Přidejte následující kód jako další řádek metody `Main()`:</span><span class="sxs-lookup"><span data-stu-id="18829-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="18829-175">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="18829-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="18829-176">Převezme proměnné cesty k datům a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="18829-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="18829-177">Detekce anomálií časové řady</span><span class="sxs-lookup"><span data-stu-id="18829-177">Time series anomaly detection</span></span>

<span data-ttu-id="18829-178">Detekce anomálií příznaky neočekávaná nebo neobvyklá událostí nebo chování.</span><span class="sxs-lookup"><span data-stu-id="18829-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="18829-179">Dává v tom, kde hledat problémy a pomáhá zodpovědět otázku "je to divné?".</span><span class="sxs-lookup"><span data-stu-id="18829-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Příklad detekce anomálií "je tímto divné".](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="18829-181">Detekce anomálií je proces zjišťování nezaložených dat časových řad. body v dané vstupní časové řadě, kde chování není očekávané, nebo "divné".</span><span class="sxs-lookup"><span data-stu-id="18829-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="18829-182">Detekce anomálií může být užitečná v mnoha různých ohledech.</span><span class="sxs-lookup"><span data-stu-id="18829-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="18829-183">Příklad:</span><span class="sxs-lookup"><span data-stu-id="18829-183">For instance:</span></span>

<span data-ttu-id="18829-184">Pokud máte auto, možná budete chtít vědět, že je tento měřič ropy čten běžným způsobem nebo mám netěsnost?</span><span class="sxs-lookup"><span data-stu-id="18829-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="18829-185">Pokud sledujete spotřebu energie, měli byste si být vědomi, že dochází k výpadku.</span><span class="sxs-lookup"><span data-stu-id="18829-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="18829-186">Existují dva typy anomálií časových řad, které je možné zjistit:</span><span class="sxs-lookup"><span data-stu-id="18829-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="18829-187">**Špičky** označují dočasné shluky chování neobvyklé v systému.</span><span class="sxs-lookup"><span data-stu-id="18829-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="18829-188">**Body změny** označují začátek trvalých změn v průběhu času v systému.</span><span class="sxs-lookup"><span data-stu-id="18829-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="18829-189">V ML.NET jsou algoritmy detekce špičky IID nebo identifikátory identifikátoru IID pro [nezávislou a identickou distribuovanou](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)datovou sadu vhodné.</span><span class="sxs-lookup"><span data-stu-id="18829-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="18829-190">Na rozdíl od modelů v ostatních kurzech transformace detektoru časové řady transformují provoz přímo na vstupní data.</span><span class="sxs-lookup"><span data-stu-id="18829-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="18829-191">Metoda `IEstimator.Fit()` nepotřebuje k tvorbě transformace data školení.</span><span class="sxs-lookup"><span data-stu-id="18829-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="18829-192">K tomu potřebuje schéma dat, které je k dispozici v zobrazení dat vygenerovaném z prázdného seznamu `ProductSalesData`.</span><span class="sxs-lookup"><span data-stu-id="18829-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="18829-193">Budete analyzovat stejná prodejní data produktu za účelem detekce Špičk a změn bodů.</span><span class="sxs-lookup"><span data-stu-id="18829-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="18829-194">Proces vytváření a školicích modelů je stejný pro detekci špičky a detekci bodu změny; Hlavním rozdílem je konkrétní použitý algoritmus detekce.</span><span class="sxs-lookup"><span data-stu-id="18829-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="18829-195">Detekce špičky</span><span class="sxs-lookup"><span data-stu-id="18829-195">Spike detection</span></span>

<span data-ttu-id="18829-196">Cílem detekce špičky je identifikovat náhlé ještě dočasné shluky, které se významně liší od většiny hodnot dat časových řad.</span><span class="sxs-lookup"><span data-stu-id="18829-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="18829-197">Je důležité detekovat tyto podezřelé výjimečné položky, události nebo pozorování včas, aby byly minimalizovány.</span><span class="sxs-lookup"><span data-stu-id="18829-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="18829-198">K detekci nejrůznějších anomálií, jako jsou výpadky, internetoví útoky nebo virové webovému obsahu, se dá použít následující přístup.</span><span class="sxs-lookup"><span data-stu-id="18829-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="18829-199">Následující obrázek je příkladem špičky v datové sadě časových řad:</span><span class="sxs-lookup"><span data-stu-id="18829-199">The following image is an example of spikes in a time series dataset:</span></span>

![Snímek obrazovky, který zobrazuje dvě detekce špičky.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="18829-201">Přidání metody CreateEmptyDataView ()</span><span class="sxs-lookup"><span data-stu-id="18829-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="18829-202">Přidejte následující metodu pro `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="18829-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="18829-203">`CreateEmptyDataView()` vytvoří prázdný objekt zobrazení dat se správným schématem, který se použije jako vstup do metody `IEstimator.Fit()`.</span><span class="sxs-lookup"><span data-stu-id="18829-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="18829-204">Vytvoření metody DetectSpike ()</span><span class="sxs-lookup"><span data-stu-id="18829-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="18829-205">Metoda `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="18829-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="18829-206">Vytvoří transformaci z Estimator.</span><span class="sxs-lookup"><span data-stu-id="18829-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="18829-207">Detekuje špičky na základě historických dat o prodeji.</span><span class="sxs-lookup"><span data-stu-id="18829-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="18829-208">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="18829-208">Displays the results.</span></span>

1. <span data-ttu-id="18829-209">Vytvořte metodu `DetectSpike()` hned za metodou `Main()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="18829-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="18829-210">Pomocí [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) můžete vyškolit model pro detekci špičky.</span><span class="sxs-lookup"><span data-stu-id="18829-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="18829-211">Přidejte ho do metody `DetectSpike()` s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="18829-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="18829-212">Vytvořte transformaci detekce špičkou přidáním následujícího jako další řádek kódu v metodě `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="18829-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="18829-213">Přidejte následující řádek kódu pro transformaci dat `productSales` jako další řádek v metodě `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="18829-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="18829-214">Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více vstupních řádků datové sady.</span><span class="sxs-lookup"><span data-stu-id="18829-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="18829-215">Převeďte `transformedData` na `IEnumerable` silného typu pro snadnější zobrazení pomocí metody [CreateEnumerable ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="18829-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="18829-216">Pomocí následujícího kódu <xref:System.Console.WriteLine?displayProperty=nameWithType> vytvořte řádek záhlaví zobrazení:</span><span class="sxs-lookup"><span data-stu-id="18829-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="18829-217">Ve výsledcích detekce špičky zobrazíte následující informace:</span><span class="sxs-lookup"><span data-stu-id="18829-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="18829-218">`Alert` označuje upozornění špičky pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="18829-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="18829-219">`Score` je `ProductSales` hodnota pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="18829-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="18829-220">`P-Value` "P" představuje pravděpodobnost.</span><span class="sxs-lookup"><span data-stu-id="18829-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="18829-221">Bližší hodnota p je 0, pravděpodobnější je, že datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="18829-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="18829-222">Použijte následující kód k iterování `IEnumerable` `predictions` a zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="18829-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="18829-223">Přidejte volání do metody `DetectSpike()`v metodě `Main()`:</span><span class="sxs-lookup"><span data-stu-id="18829-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="18829-224">Výsledky detekce špičky</span><span class="sxs-lookup"><span data-stu-id="18829-224">Spike detection results</span></span>

<span data-ttu-id="18829-225">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="18829-225">Your results should be similar to the following.</span></span> <span data-ttu-id="18829-226">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="18829-226">During processing, messages are displayed.</span></span> <span data-ttu-id="18829-227">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="18829-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="18829-228">Některé zprávy byly pro přehlednost odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="18829-228">Some of the messages have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="18829-229">Detekce bodu změny</span><span class="sxs-lookup"><span data-stu-id="18829-229">Change point detection</span></span>

<span data-ttu-id="18829-230">`Change points` jsou trvalé změny v průběhu distribuce hodnot datového proudu událostí, jako jsou například změny úrovně a trendy.</span><span class="sxs-lookup"><span data-stu-id="18829-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="18829-231">Tyto trvalé změny jsou poslední mnohem delší než `spikes` a můžou označovat závažné události.</span><span class="sxs-lookup"><span data-stu-id="18829-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="18829-232">`Change points` nejsou obvykle viditelné pro holé oči, ale lze je zjistit ve vašich datech pomocí přístupů, jako je například v následující metodě.</span><span class="sxs-lookup"><span data-stu-id="18829-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="18829-233">Následující obrázek je příkladem detekce bodu změny:</span><span class="sxs-lookup"><span data-stu-id="18829-233">The following image is an example of a change point detection:</span></span>

![Snímek obrazovky, který ukazuje detekci bodu změny.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="18829-235">Vytvoření metody DetectChangepoint ()</span><span class="sxs-lookup"><span data-stu-id="18829-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="18829-236">Metoda `DetectChangepoint()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="18829-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="18829-237">Vytvoří transformaci z Estimator.</span><span class="sxs-lookup"><span data-stu-id="18829-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="18829-238">Detekuje body změn na základě historických dat o prodeji.</span><span class="sxs-lookup"><span data-stu-id="18829-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="18829-239">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="18829-239">Displays the results.</span></span>

1. <span data-ttu-id="18829-240">Vytvořte metodu `DetectChangepoint()` hned za metodou `Main()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="18829-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="18829-241">Vytvořte [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) pomocí následujícího kódu v metodě `DetectChangepoint()`:</span><span class="sxs-lookup"><span data-stu-id="18829-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="18829-242">Jak jste předtím pracovali, vytvořte transformaci z Estimator přidáním následujícího řádku kódu do metody `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="18829-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="18829-243">Použijte metodu `Transform()` pro transformaci dat přidáním následujícího kódu do `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="18829-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="18829-244">Jak jste předtím pracovali, převeďte `transformedData` na silně typované `IEnumerable` pro snazší zobrazení pomocí metody `CreateEnumerable()`s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="18829-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="18829-245">Vytvořte záhlaví zobrazení s následujícím kódem jako další řádek v metodě `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="18829-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="18829-246">Ve výsledcích detekce bodů změny se zobrazí následující informace:</span><span class="sxs-lookup"><span data-stu-id="18829-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="18829-247">`Alert` označuje upozornění na změnu bodu pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="18829-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="18829-248">`Score` je `ProductSales` hodnota pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="18829-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="18829-249">`P-Value` "P" představuje pravděpodobnost.</span><span class="sxs-lookup"><span data-stu-id="18829-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="18829-250">Bližší hodnota P je 0, pravděpodobnější je, že datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="18829-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="18829-251">`Martingale value` slouží k identifikaci způsobu, jakým je "divné" a datovým bodem, na základě pořadí hodnot P.</span><span class="sxs-lookup"><span data-stu-id="18829-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="18829-252">Iterujte pomocí `predictions` `IEnumerable` a zobrazte výsledky s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="18829-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="18829-253">Do metody `DetectChangepoint()`v metodě `Main()` přidejte následující volání:</span><span class="sxs-lookup"><span data-stu-id="18829-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="18829-254">Výsledky detekce bodu změny</span><span class="sxs-lookup"><span data-stu-id="18829-254">Change point detection results</span></span>

<span data-ttu-id="18829-255">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="18829-255">Your results should be similar to the following.</span></span> <span data-ttu-id="18829-256">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="18829-256">During processing, messages are displayed.</span></span> <span data-ttu-id="18829-257">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="18829-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="18829-258">Některé zprávy byly pro přehlednost odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="18829-258">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="18829-259">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="18829-259">Congratulations!</span></span> <span data-ttu-id="18829-260">Teď jste úspěšně vytvořili modely strojového učení pro zjišťování špiček a anomálií bodů změn v prodejních datech.</span><span class="sxs-lookup"><span data-stu-id="18829-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="18829-261">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .</span><span class="sxs-lookup"><span data-stu-id="18829-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="18829-262">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="18829-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="18829-263">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="18829-263">Load the data</span></span>
> * <span data-ttu-id="18829-264">Vyškolit model pro detekci anomálií špičky</span><span class="sxs-lookup"><span data-stu-id="18829-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="18829-265">Zjištění anomálií špičky pomocí trained model</span><span class="sxs-lookup"><span data-stu-id="18829-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="18829-266">Výuka modelu pro detekci anomálií bodů změn</span><span class="sxs-lookup"><span data-stu-id="18829-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="18829-267">Detekovat anomálie bodů změny v proškolených režimech</span><span class="sxs-lookup"><span data-stu-id="18829-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="18829-268">Další kroky</span><span class="sxs-lookup"><span data-stu-id="18829-268">Next steps</span></span>

<span data-ttu-id="18829-269">Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku detekce anomálií spotřeby energie.</span><span class="sxs-lookup"><span data-stu-id="18829-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="18829-270">dotnet/machinelearning-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="18829-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
