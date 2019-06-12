---
title: 'Kurz: Zjišťovat anomálie v produktu prodeje'
description: Zjistěte, jak sestavit aplikaci detekce anomálií na prodejní data produktu. Tento kurz vytvoří aplikace konzoly .NET Core using C# v aplikaci Visual Studio 2019.
ms.date: 06/11/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 6ea5adf79a17bb10ddea676eaea483c2cf627d82
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026046"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="138d3-104">Kurz: Zjišťovat anomálie v prodejích s ML.NET</span><span class="sxs-lookup"><span data-stu-id="138d3-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="138d3-105">Zjistěte, jak sestavit aplikaci detekce anomálií na prodejní data produktu.</span><span class="sxs-lookup"><span data-stu-id="138d3-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="138d3-106">Tento kurz vytvoří aplikace konzoly .NET Core using C# v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="138d3-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="138d3-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="138d3-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="138d3-108">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="138d3-108">Load the data</span></span>
> * <span data-ttu-id="138d3-109">Trénování modelu pro detekci anomálií ve špičce</span><span class="sxs-lookup"><span data-stu-id="138d3-109">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="138d3-110">Detekovat anomálie ve špičce pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="138d3-110">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="138d3-111">Trénování modelu pro změnu bodu pro detekci anomálií</span><span class="sxs-lookup"><span data-stu-id="138d3-111">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="138d3-112">Detekovat anomálie bodu změnu s trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="138d3-112">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="138d3-113">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) úložiště.</span><span class="sxs-lookup"><span data-stu-id="138d3-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="138d3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="138d3-114">Prerequisites</span></span>

* <span data-ttu-id="138d3-115">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="138d3-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="138d3-116">Datová sada sales.csv produktu</span><span class="sxs-lookup"><span data-stu-id="138d3-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="138d3-117">Formátování dat v `product-sales.csv` je založena na této datové sadě "Šampón prodej přes tří let" původně zdrojem je DataMarket a k dispozici podle času řady dat knihovny (TSDL), Autor Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="138d3-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="138d3-118">Datová sada "Šampón prodeje za období tří let" licencovaného v rámci programu Open License DataMarket výchozí.</span><span class="sxs-lookup"><span data-stu-id="138d3-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="138d3-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="138d3-119">Create a console application</span></span>

1. <span data-ttu-id="138d3-120">Vytvoření **konzolovou aplikaci .NET Core** nazývá "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="138d3-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="138d3-121">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady.</span><span class="sxs-lookup"><span data-stu-id="138d3-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="138d3-122">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="138d3-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="138d3-123">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="138d3-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="138d3-124">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte **v1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="138d3-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="138d3-125">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="138d3-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="138d3-126">Opakujte tyto kroky pro **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="138d3-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="138d3-127">Přidejte následující `using` příkazů v horní části vašeho *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="138d3-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="138d3-128">Stáhněte si vaše data</span><span class="sxs-lookup"><span data-stu-id="138d3-128">Download your data</span></span>

1. <span data-ttu-id="138d3-129">Stáhnout datovou sadu a uložit ho. tím *Data* dříve vytvořená složka:</span><span class="sxs-lookup"><span data-stu-id="138d3-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="138d3-130">Klikněte pravým tlačítkem na [ *produktu sales.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."</span><span class="sxs-lookup"><span data-stu-id="138d3-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="138d3-131">Ujistěte se, že buď uložit \*soubor .csv *Data* složky, nebo poté, co jste jej uložili jinde, přesunout \*soubor .csv *Data* složky.</span><span class="sxs-lookup"><span data-stu-id="138d3-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="138d3-132">V Průzkumníku řešení klikněte pravým tlačítkem myši \*soubor .csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="138d3-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="138d3-133">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="138d3-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="138d3-134">V následující tabulce je náhled dat z vašich \*souboru CSV:</span><span class="sxs-lookup"><span data-stu-id="138d3-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="138d3-135">Měsíc</span><span class="sxs-lookup"><span data-stu-id="138d3-135">Month</span></span>  |<span data-ttu-id="138d3-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="138d3-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="138d3-137">1. leden</span><span class="sxs-lookup"><span data-stu-id="138d3-137">1-Jan</span></span>  |    <span data-ttu-id="138d3-138">271</span><span class="sxs-lookup"><span data-stu-id="138d3-138">271</span></span>      |
|<span data-ttu-id="138d3-139">2 – leden</span><span class="sxs-lookup"><span data-stu-id="138d3-139">2-Jan</span></span>  |    <span data-ttu-id="138d3-140">150.9</span><span class="sxs-lookup"><span data-stu-id="138d3-140">150.9</span></span>    |
|<span data-ttu-id="138d3-141">.....</span><span class="sxs-lookup"><span data-stu-id="138d3-141">.....</span></span>  |    <span data-ttu-id="138d3-142">.....</span><span class="sxs-lookup"><span data-stu-id="138d3-142">.....</span></span>    |
|<span data-ttu-id="138d3-143">1 – únor</span><span class="sxs-lookup"><span data-stu-id="138d3-143">1-Feb</span></span>  |    <span data-ttu-id="138d3-144">199.3</span><span class="sxs-lookup"><span data-stu-id="138d3-144">199.3</span></span>    |
|<span data-ttu-id="138d3-145">.....</span><span class="sxs-lookup"><span data-stu-id="138d3-145">.....</span></span>  |    <span data-ttu-id="138d3-146">.....</span><span class="sxs-lookup"><span data-stu-id="138d3-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="138d3-147">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="138d3-147">Create classes and define paths</span></span>

<span data-ttu-id="138d3-148">Dále definujte vstupní třídy datovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="138d3-148">Next, define your input class data structure.</span></span>

<span data-ttu-id="138d3-149">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="138d3-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="138d3-150">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="138d3-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="138d3-151">V **dialogové okno Přidat novou položku**vyberte **třídy** a změnit **název** pole *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="138d3-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="138d3-152">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="138d3-152">Then, select the **Add** button.</span></span>

<span data-ttu-id="138d3-153">*ProductSalesData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="138d3-153">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="138d3-154">Přidejte následující `using` příkaz do horní části *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="138d3-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="138d3-155">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, možnosti *ProductSalesData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="138d3-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="138d3-156">`ProductSalesData` Určuje třídu vstupní data.</span><span class="sxs-lookup"><span data-stu-id="138d3-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="138d3-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atribut určuje, jaké sloupce (podle index sloupce) v datové sadě se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="138d3-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="138d3-158">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="138d3-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="138d3-159">Je potřeba vytvořit dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:</span><span class="sxs-lookup"><span data-stu-id="138d3-159">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="138d3-160">`_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="138d3-160">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="138d3-161">`_docsize` soubor datové sady obsahuje několik záznamů.</span><span class="sxs-lookup"><span data-stu-id="138d3-161">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="138d3-162">Budete využit k výpočtu `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="138d3-162">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="138d3-163">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="138d3-163">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="138d3-164">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="138d3-164">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="138d3-165">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="138d3-165">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="138d3-166">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="138d3-166">Initialize variables in Main</span></span>

<span data-ttu-id="138d3-167">Nahradit `Console.WriteLine("Hello World!")` řádku v `Main` metoda následujícím kódem, jak deklarovat a inicializovat `mlContext` proměnné:</span><span class="sxs-lookup"><span data-stu-id="138d3-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="138d3-168">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="138d3-168">Load the data</span></span>

<span data-ttu-id="138d3-169">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="138d3-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="138d3-170">`IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="138d3-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="138d3-171">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="138d3-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="138d3-172">Přidejte následující kód jako další řádek `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-172">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="138d3-173">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru.</span><span class="sxs-lookup"><span data-stu-id="138d3-173">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="138d3-174">Přijímá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="138d3-174">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="138d3-175">Úloha ML – čas detekce anomálií řady</span><span class="sxs-lookup"><span data-stu-id="138d3-175">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="138d3-176">Detekce anomálií příznaky neočekávaná nebo neobvyklá událostí nebo chování.</span><span class="sxs-lookup"><span data-stu-id="138d3-176">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="138d3-177">Poskytuje možné místo pro vyhledání problémů a pomáhá odpovědět na otázku "Je tato divně?".</span><span class="sxs-lookup"><span data-stu-id="138d3-177">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Je to divné](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="138d3-179">Detekce anomálií je proces zjišťování dat časových řad odlehlé hodnoty; odkazuje na daný vstupní časovou řadu, kde chování není očekávaným, nebo "divné".</span><span class="sxs-lookup"><span data-stu-id="138d3-179">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="138d3-180">To může být užitečné v mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="138d3-180">This can be useful in lots of ways.</span></span> <span data-ttu-id="138d3-181">Příklad:</span><span class="sxs-lookup"><span data-stu-id="138d3-181">For instance:</span></span>

<span data-ttu-id="138d3-182">Pokud máte automobilu, můžete chtít vědět: Je tento olej měřidla čtení normální nebo mít nevracení?</span><span class="sxs-lookup"><span data-stu-id="138d3-182">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="138d3-183">Pokud monitorujete spotřebu energie, byste měli vědět: Je k dispozici kvůli výpadku?</span><span class="sxs-lookup"><span data-stu-id="138d3-183">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="138d3-184">Existují dva typy anomálií řady čas, které lze zjistit:</span><span class="sxs-lookup"><span data-stu-id="138d3-184">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="138d3-185">**Špičky** označují dočasné nárůstům neobvyklé chování v systému.</span><span class="sxs-lookup"><span data-stu-id="138d3-185">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="138d3-186">**Body změny** označuje začátek trvalé změny časem v systému.</span><span class="sxs-lookup"><span data-stu-id="138d3-186">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="138d3-187">V ML.NET, identifikátor IID zásobníku zjišťování nebo detekce změn bodu IID algoritmy jsou vhodné pro [nezávislé a stejně jako distribuovaných datových sad](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="138d3-187">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="138d3-188">Budete analyzuje stejný produkt prodejní data, zjistit provozní špičky a změnit body.</span><span class="sxs-lookup"><span data-stu-id="138d3-188">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="138d3-189">Model procesu sestavovat a vzdělávání je stejný pro zjišťování zásobníku a detekce změn bod; Hlavní rozdíl je použitý algoritmus konkrétní zjišťování.</span><span class="sxs-lookup"><span data-stu-id="138d3-189">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="138d3-190">Detekce zásobníku</span><span class="sxs-lookup"><span data-stu-id="138d3-190">Spike detection</span></span> 

<span data-ttu-id="138d3-191">Cílem zásobníku detekce je k identifikaci i s náhlými ještě dočasné nárůsty zatížení, které výrazně se liší od většinou časových řad dat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="138d3-191">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="138d3-192">Je důležité pro detekci těchto výjimečných podezřelé položky, události nebo pozorování minimalizaci včas.</span><span class="sxs-lookup"><span data-stu-id="138d3-192">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="138d3-193">Následující postup slouží ke zjištění různých anomálie, jako: výpadky, kybernetických útoků nebo virální webového obsahu.</span><span class="sxs-lookup"><span data-stu-id="138d3-193">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="138d3-194">Na následujícím obrázku je příklad špičky v datové sadě řady čas:</span><span class="sxs-lookup"><span data-stu-id="138d3-194">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="138d3-196">Vytvoření DetectSpike() – metoda</span><span class="sxs-lookup"><span data-stu-id="138d3-196">Create the DetectSpike() method</span></span>

<span data-ttu-id="138d3-197">Přidejte následující volání `DetectSpike()`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-197">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="138d3-198">`DetectSpike()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="138d3-198">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="138d3-199">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="138d3-199">Trains the model.</span></span>
* <span data-ttu-id="138d3-200">Detekuje na základě na historická data o prodeji provozní špičky.</span><span class="sxs-lookup"><span data-stu-id="138d3-200">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="138d3-201">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="138d3-201">Displays the results.</span></span>

<span data-ttu-id="138d3-202">Vytvořte `DetectSpike()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="138d3-202">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="138d3-203">Použití [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pro trénování modelu pro zjišťování (špičky).</span><span class="sxs-lookup"><span data-stu-id="138d3-203">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="138d3-204">Přidejte ji tak `DetectChangepoint()` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="138d3-204">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="138d3-205">Přizpůsobení modelu, který má `productSales` data přidáním následujícího kódu jako další řádek kódu v `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-205">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="138d3-206">[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="138d3-206">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="138d3-207">Přidejte následující řádek kódu, který umožňuje transformovat `productSales` data jako další řádek v `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-207">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="138d3-208">Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda k následné predikci pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="138d3-208">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="138d3-209">Převést vaše `transformedData` do silného typu `IEnumerable` pro snadnější zobrazení pomocí [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="138d3-209">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="138d3-210">Vytvořit řádek záhlaví zobrazení pomocí následující <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="138d3-210">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="138d3-211">Ve výsledcích zjišťování zásobníku budete zobrazovat následující informace:</span><span class="sxs-lookup"><span data-stu-id="138d3-211">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="138d3-212">`Alert` označuje zásobníku upozornění pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="138d3-212">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="138d3-213">`Score` je `ProductSales` hodnotu pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="138d3-213">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="138d3-214">`P-Value` "P" jsou zahrnovaného pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="138d3-214">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="138d3-215">To znamená, jaká je pravděpodobnost tento datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="138d3-215">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="138d3-216">Použijte následující kód k iteraci v rámci `predictions` `IEnumerable` a zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="138d3-216">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="138d3-217">Výsledky vyhledávání (špičky)</span><span class="sxs-lookup"><span data-stu-id="138d3-217">Spike detection results</span></span>

<span data-ttu-id="138d3-218">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="138d3-218">Your results should be similar to the following.</span></span> <span data-ttu-id="138d3-219">Během zpracování zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="138d3-219">During processing, messages are displayed.</span></span> <span data-ttu-id="138d3-220">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="138d3-220">You may see warnings, or processing messages.</span></span> <span data-ttu-id="138d3-221">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="138d3-221">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="138d3-222">Změna bodu zjišťování</span><span class="sxs-lookup"><span data-stu-id="138d3-222">Change point detection</span></span>

<span data-ttu-id="138d3-223">`Change points` jsou trvalé změny v řady čas události datového proudu distribuci hodnot, jako jsou změny na úrovni a trendy.</span><span class="sxs-lookup"><span data-stu-id="138d3-223">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="138d3-224">Trvalé změny naposledy mnohem delší než `spikes` a může znamenat katastrofické události.</span><span class="sxs-lookup"><span data-stu-id="138d3-224">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="138d3-225">`Change points` se obvykle nezobrazí pouhým okem, ale můžete zjistit ve vašich datech pomocí přístupů například následující metodu.</span><span class="sxs-lookup"><span data-stu-id="138d3-225">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="138d3-226">Na následujícím obrázku je příklad bodu detekce změn:</span><span class="sxs-lookup"><span data-stu-id="138d3-226">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="138d3-228">Vytvoření DetectChangepoint() – metoda</span><span class="sxs-lookup"><span data-stu-id="138d3-228">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="138d3-229">Přidejte následující volání `DetectChangepoint()`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-229">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="138d3-230">`DetectChangepoint()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="138d3-230">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="138d3-231">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="138d3-231">Trains the model.</span></span>
* <span data-ttu-id="138d3-232">Zjistí změnu body na základě historických dat prodeje.</span><span class="sxs-lookup"><span data-stu-id="138d3-232">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="138d3-233">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="138d3-233">Displays the results.</span></span>

<span data-ttu-id="138d3-234">Vytvořte `DetectChangepoint()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="138d3-234">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="138d3-235">[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) se používá pro trénování modelu pro změnu bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="138d3-235">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="138d3-236">Přidejte ji tak `DetectChangepoint()` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="138d3-236">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="138d3-237">Stejně jako dříve, podle modelu, který má `productSales` data přidáním následujícího kódu jako další řádek kódu v `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-237">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="138d3-238">Použití `Transform()` metody k transformaci `Training` data přidáním následujícího kódu do `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="138d3-238">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="138d3-239">Stejně jako dříve, převést vaše `transformedData` do silného typu `IEnumerable` pro snadnější zobrazení pomocí `CreateEnumerable()`metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="138d3-239">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="138d3-240">Vytvořit záhlaví zobrazení jako na další řádek v následujícím kódem `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="138d3-240">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="138d3-241">Ve výsledcích zjišťování změn bodu budete zobrazovat následující informace:</span><span class="sxs-lookup"><span data-stu-id="138d3-241">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="138d3-242">`Alert` označuje změnit bod oznámení pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="138d3-242">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="138d3-243">`Score` je `ProductSales` hodnotu pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="138d3-243">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="138d3-244">`P-Value` "P" jsou zahrnovaného pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="138d3-244">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="138d3-245">To znamená, jaká je pravděpodobnost tento datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="138d3-245">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="138d3-246">`Martingale value` se používá k identifikaci, jak je "divně" datový bod, v závislosti na sekvenci hodnot P.</span><span class="sxs-lookup"><span data-stu-id="138d3-246">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="138d3-247">Iterovat přes `predictions` `IEnumerable` a zobrazit výsledky s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="138d3-247">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="138d3-248">Změna bodu zjišťování výsledky</span><span class="sxs-lookup"><span data-stu-id="138d3-248">Change point detection results</span></span>

<span data-ttu-id="138d3-249">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="138d3-249">Your results should be similar to the following.</span></span> <span data-ttu-id="138d3-250">Během zpracování zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="138d3-250">During processing, messages are displayed.</span></span> <span data-ttu-id="138d3-251">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="138d3-251">You may see warnings, or processing messages.</span></span> <span data-ttu-id="138d3-252">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="138d3-252">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="138d3-253">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="138d3-253">Congratulations!</span></span> <span data-ttu-id="138d3-254">Jste teď úspěšně sestaven modelů strojového učení pro zjišťování provozní špičky a změnit bod anomálie v prodejní data.</span><span class="sxs-lookup"><span data-stu-id="138d3-254">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="138d3-255">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) úložiště.</span><span class="sxs-lookup"><span data-stu-id="138d3-255">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="138d3-256">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="138d3-256">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="138d3-257">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="138d3-257">Load the data</span></span>
> * <span data-ttu-id="138d3-258">Trénování modelu pro detekci anomálií ve špičce</span><span class="sxs-lookup"><span data-stu-id="138d3-258">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="138d3-259">Detekovat anomálie ve špičce pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="138d3-259">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="138d3-260">Trénování modelu pro změnu bodu pro detekci anomálií</span><span class="sxs-lookup"><span data-stu-id="138d3-260">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="138d3-261">Detekovat anomálie bodu změnu s režimem trénovaného</span><span class="sxs-lookup"><span data-stu-id="138d3-261">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="138d3-262">Další kroky</span><span class="sxs-lookup"><span data-stu-id="138d3-262">Next steps</span></span>

<span data-ttu-id="138d3-263">Projděte si úložišti GitHub s ukázkami Machine Learning a prozkoumejte ukázkový spotřebu energie pro detekci anomálií.</span><span class="sxs-lookup"><span data-stu-id="138d3-263">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="138d3-264">úložiště GitHub DotNet/machinelearning – ukázky</span><span class="sxs-lookup"><span data-stu-id="138d3-264">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
