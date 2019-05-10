---
title: Použijte v případě detekce anomálií prodejní ML.NET
description: Zjistěte, jak pochopit, jak analyzovat data špiček anomálií a body přijmout vhodná opatření změny pomocí ML.NET v případě detekce anomálií prodejní produktu.
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b0dbd8793e2be3973c37f0f78bc0ddd61b6bfea7
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066190"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a><span data-ttu-id="88c58-103">Kurz: Použití ML.NET pro detekci anomálií prodejní produktu</span><span class="sxs-lookup"><span data-stu-id="88c58-103">Tutorial: Use ML.NET for product sales anomaly detection</span></span> 

<span data-ttu-id="88c58-104">Tento ukázkový kurz ukazuje použití ML.NET zjišťovat anomálie v produktu daty z prodeje přijmout vhodná opatření prostřednictvím aplikace konzoly .NET Core using C# v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="88c58-104">This sample tutorial illustrates using ML.NET to detect anomalies in product sales data to take the appropriate action via a .NET Core console application using C# in Visual Studio 2019.</span></span> 

<span data-ttu-id="88c58-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="88c58-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="88c58-106">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="88c58-106">Load the data</span></span>
> * <span data-ttu-id="88c58-107">Trénování modelu pro detekci anomálií ve špičce</span><span class="sxs-lookup"><span data-stu-id="88c58-107">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="88c58-108">Detekovat anomálie ve špičce pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="88c58-108">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="88c58-109">Trénování modelu pro změnu bodu pro detekci anomálií</span><span class="sxs-lookup"><span data-stu-id="88c58-109">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="88c58-110">Detekovat anomálie bodu změnu s trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="88c58-110">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="88c58-111">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) úložiště.</span><span class="sxs-lookup"><span data-stu-id="88c58-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88c58-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88c58-112">Prerequisites</span></span>

* <span data-ttu-id="88c58-113">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="88c58-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="88c58-114">Datová sada sales.csv produktu</span><span class="sxs-lookup"><span data-stu-id="88c58-114">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="88c58-115">Formátování dat v `product-sales.csv` je založena na této datové sadě "Šampón prodej přes tří let" původně zdrojem je DataMarket a k dispozici podle času řady dat knihovny (TSDL), Autor Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="88c58-115">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="88c58-116">Datová sada "Šampón prodeje za období tří let" licencovaného v rámci programu Open License DataMarket výchozí.</span><span class="sxs-lookup"><span data-stu-id="88c58-116">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="88c58-117">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="88c58-117">Create a console application</span></span>

1. <span data-ttu-id="88c58-118">Vytvoření **konzolovou aplikaci .NET Core** nazývá "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="88c58-118">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="88c58-119">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady.</span><span class="sxs-lookup"><span data-stu-id="88c58-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="88c58-120">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="88c58-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="88c58-121">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="88c58-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="88c58-122">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte **v1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="88c58-122">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="88c58-123">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="88c58-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="88c58-124">Opakujte tyto kroky pro **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="88c58-124">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="88c58-125">Přidejte následující `using` příkazů v horní části vašeho *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="88c58-125">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="88c58-126">Stáhněte si vaše data</span><span class="sxs-lookup"><span data-stu-id="88c58-126">Download your data</span></span>

1. <span data-ttu-id="88c58-127">Stáhnout datovou sadu a uložit ho. tím *Data* dříve vytvořená složka:</span><span class="sxs-lookup"><span data-stu-id="88c58-127">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="88c58-128">Klikněte pravým tlačítkem na [ *produktu sales.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."</span><span class="sxs-lookup"><span data-stu-id="88c58-128">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="88c58-129">Ujistěte se, že buď uložit \*soubor .csv *Data* složky, nebo poté, co jste jej uložili jinde, přesunout \*soubor .csv *Data* složky.</span><span class="sxs-lookup"><span data-stu-id="88c58-129">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="88c58-130">V Průzkumníku řešení klikněte pravým tlačítkem myši \*soubor .csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="88c58-130">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="88c58-131">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="88c58-131">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="88c58-132">V následující tabulce je náhled dat z vašich \*souboru CSV:</span><span class="sxs-lookup"><span data-stu-id="88c58-132">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="88c58-133">Měsíc</span><span class="sxs-lookup"><span data-stu-id="88c58-133">Month</span></span>  |<span data-ttu-id="88c58-134">ProductSales</span><span class="sxs-lookup"><span data-stu-id="88c58-134">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="88c58-135">1. leden</span><span class="sxs-lookup"><span data-stu-id="88c58-135">1-Jan</span></span>  |    <span data-ttu-id="88c58-136">271</span><span class="sxs-lookup"><span data-stu-id="88c58-136">271</span></span>      |
|<span data-ttu-id="88c58-137">2 – leden</span><span class="sxs-lookup"><span data-stu-id="88c58-137">2-Jan</span></span>  |    <span data-ttu-id="88c58-138">150.9</span><span class="sxs-lookup"><span data-stu-id="88c58-138">150.9</span></span>    |
|<span data-ttu-id="88c58-139">.....</span><span class="sxs-lookup"><span data-stu-id="88c58-139">.....</span></span>  |    <span data-ttu-id="88c58-140">.....</span><span class="sxs-lookup"><span data-stu-id="88c58-140">.....</span></span>    |
|<span data-ttu-id="88c58-141">1 – únor</span><span class="sxs-lookup"><span data-stu-id="88c58-141">1-Feb</span></span>  |    <span data-ttu-id="88c58-142">199.3</span><span class="sxs-lookup"><span data-stu-id="88c58-142">199.3</span></span>    |
|<span data-ttu-id="88c58-143">.....</span><span class="sxs-lookup"><span data-stu-id="88c58-143">.....</span></span>  |    <span data-ttu-id="88c58-144">.....</span><span class="sxs-lookup"><span data-stu-id="88c58-144">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="88c58-145">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="88c58-145">Create classes and define paths</span></span>

<span data-ttu-id="88c58-146">Dále definujte vstupní třídy datovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="88c58-146">Next, define your input class data structure.</span></span>

<span data-ttu-id="88c58-147">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="88c58-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="88c58-148">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="88c58-148">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="88c58-149">V **dialogové okno Přidat novou položku**vyberte **třídy** a změnit **název** pole *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="88c58-149">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="88c58-150">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="88c58-150">Then, select the **Add** button.</span></span>

<span data-ttu-id="88c58-151">*ProductSalesData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="88c58-151">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="88c58-152">Přidejte následující `using` příkaz do horní části *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="88c58-152">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="88c58-153">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `ProductSalesData` a `ProductSalesPrediction`, možnosti *ProductSalesData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="88c58-153">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="88c58-154">`ProductSalesData` Určuje třídu vstupní data.</span><span class="sxs-lookup"><span data-stu-id="88c58-154">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="88c58-155">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atribut určuje, jaké sloupce (podle index sloupce) v datové sadě se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="88c58-155">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="88c58-156">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="88c58-156">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="88c58-157">Je potřeba vytvořit dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:</span><span class="sxs-lookup"><span data-stu-id="88c58-157">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="88c58-158">`_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="88c58-158">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="88c58-159">`_docsize` soubor datové sady obsahuje několik záznamů.</span><span class="sxs-lookup"><span data-stu-id="88c58-159">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="88c58-160">Budete využit k výpočtu `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="88c58-160">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="88c58-161">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="88c58-161">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="88c58-162">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="88c58-162">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="88c58-163">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="88c58-163">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="88c58-164">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="88c58-164">Initialize variables in Main</span></span>

<span data-ttu-id="88c58-165">Nahradit `Console.WriteLine("Hello World!")` řádku v `Main` metoda následujícím kódem, jak deklarovat a inicializovat `mlContext` proměnné:</span><span class="sxs-lookup"><span data-stu-id="88c58-165">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="88c58-166">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="88c58-166">Load the data</span></span>

<span data-ttu-id="88c58-167">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="88c58-167">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="88c58-168">`IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="88c58-168">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="88c58-169">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="88c58-169">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="88c58-170">Přidejte následující kód jako další řádek `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-170">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="88c58-171">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru.</span><span class="sxs-lookup"><span data-stu-id="88c58-171">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="88c58-172">Přijímá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="88c58-172">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="88c58-173">Úloha ML – čas detekce anomálií řady</span><span class="sxs-lookup"><span data-stu-id="88c58-173">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="88c58-174">Detekce anomálií příznaky neočekávaná nebo neobvyklá událostí nebo chování.</span><span class="sxs-lookup"><span data-stu-id="88c58-174">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="88c58-175">Poskytuje možné místo pro vyhledání problémů a pomáhá odpovědět na otázku "Je tato divně?".</span><span class="sxs-lookup"><span data-stu-id="88c58-175">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Je to divné](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="88c58-177">Detekce anomálií je proces zjišťování dat časových řad odlehlé hodnoty; odkazuje na daný vstupní časovou řadu, kde chování není očekávaným, nebo "divné".</span><span class="sxs-lookup"><span data-stu-id="88c58-177">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="88c58-178">To může být užitečné v mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="88c58-178">This can be useful in lots of ways.</span></span> <span data-ttu-id="88c58-179">Příklad:</span><span class="sxs-lookup"><span data-stu-id="88c58-179">For instance:</span></span>

<span data-ttu-id="88c58-180">Pokud máte automobilu, můžete chtít vědět: Je tento olej měřidla čtení normální nebo mít nevracení?</span><span class="sxs-lookup"><span data-stu-id="88c58-180">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="88c58-181">Pokud monitorujete spotřebu energie, byste měli vědět: Je k dispozici kvůli výpadku?</span><span class="sxs-lookup"><span data-stu-id="88c58-181">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="88c58-182">Existují dva typy anomálií řady čas, které lze zjistit:</span><span class="sxs-lookup"><span data-stu-id="88c58-182">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="88c58-183">**Špičky** označují dočasné nárůstům neobvyklé chování v systému.</span><span class="sxs-lookup"><span data-stu-id="88c58-183">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="88c58-184">**Body změny** označuje začátek trvalé změny časem v systému.</span><span class="sxs-lookup"><span data-stu-id="88c58-184">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="88c58-185">V ML.NET, identifikátor IID zásobníku zjišťování nebo detekce změn bodu IID algoritmy jsou vhodné pro [nezávislé a stejně jako distribuovaných datových sad](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="88c58-185">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="88c58-186">Budete analyzuje stejný produkt prodejní data, zjistit provozní špičky a změnit body.</span><span class="sxs-lookup"><span data-stu-id="88c58-186">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="88c58-187">Model procesu sestavovat a vzdělávání je stejný pro zjišťování zásobníku a detekce změn bod; Hlavní rozdíl je použitý algoritmus konkrétní zjišťování.</span><span class="sxs-lookup"><span data-stu-id="88c58-187">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="88c58-188">Detekce zásobníku</span><span class="sxs-lookup"><span data-stu-id="88c58-188">Spike detection</span></span> 

<span data-ttu-id="88c58-189">Cílem zásobníku detekce je k identifikaci i s náhlými ještě dočasné nárůsty zatížení, které výrazně se liší od většinou časových řad dat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88c58-189">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="88c58-190">Je důležité pro detekci těchto výjimečných podezřelé položky, události nebo pozorování minimalizaci včas.</span><span class="sxs-lookup"><span data-stu-id="88c58-190">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="88c58-191">Následující postup slouží ke zjištění různých anomálie, jako: výpadky, kybernetických útoků nebo virální webového obsahu.</span><span class="sxs-lookup"><span data-stu-id="88c58-191">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="88c58-192">Na následujícím obrázku je příklad špičky v datové sadě řady čas:</span><span class="sxs-lookup"><span data-stu-id="88c58-192">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="88c58-194">Vytvoření DetectSpike() – metoda</span><span class="sxs-lookup"><span data-stu-id="88c58-194">Create the DetectSpike() method</span></span>

<span data-ttu-id="88c58-195">Přidejte následující volání `DetectSpike()`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-195">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="88c58-196">`DetectSpike()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="88c58-196">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="88c58-197">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="88c58-197">Trains the model.</span></span>
* <span data-ttu-id="88c58-198">Detekuje na základě na historická data o prodeji provozní špičky.</span><span class="sxs-lookup"><span data-stu-id="88c58-198">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="88c58-199">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="88c58-199">Displays the results.</span></span>

<span data-ttu-id="88c58-200">Vytvořte `DetectSpike()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="88c58-200">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="88c58-201">Použití [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pro trénování modelu pro zjišťování (špičky).</span><span class="sxs-lookup"><span data-stu-id="88c58-201">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="88c58-202">Přidejte ji tak `DetectChangepoint()` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="88c58-202">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="88c58-203">Přizpůsobit modelu, který má `productSales` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-203">Fit the model to the `productSales` data and return the trained model by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="88c58-204">[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="88c58-204">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="88c58-205">Přidejte následující řádek kódu, který umožňuje transformovat `productSales` data jako další řádek v `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-205">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="88c58-206">Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda k následné predikci pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="88c58-206">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="88c58-207">Převést vaše `transformedData` do silného typu `IEnumerable` pro snadnější zobrazení pomocí [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="88c58-207">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="88c58-208">Vytvořit řádek záhlaví zobrazení pomocí následující <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="88c58-208">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="88c58-209">Ve výsledcích zjišťování zásobníku budete zobrazovat následující informace:</span><span class="sxs-lookup"><span data-stu-id="88c58-209">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="88c58-210">`Alert` označuje zásobníku upozornění pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="88c58-210">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="88c58-211">`Score` je `ProductSales` hodnotu pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="88c58-211">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="88c58-212">`P-Value` "P" jsou zahrnovaného pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="88c58-212">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="88c58-213">To znamená, jaká je pravděpodobnost tento datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="88c58-213">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="88c58-214">Použijte následující kód k iteraci v rámci `predictions` `IEnumerable` a zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="88c58-214">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="88c58-215">Výsledky vyhledávání (špičky)</span><span class="sxs-lookup"><span data-stu-id="88c58-215">Spike detection results</span></span>

<span data-ttu-id="88c58-216">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="88c58-216">Your results should be similar to the following.</span></span> <span data-ttu-id="88c58-217">Během zpracování zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="88c58-217">During processing, messages are displayed.</span></span> <span data-ttu-id="88c58-218">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="88c58-218">You may see warnings, or processing messages.</span></span> <span data-ttu-id="88c58-219">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="88c58-219">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="88c58-220">Změna bodu zjišťování</span><span class="sxs-lookup"><span data-stu-id="88c58-220">Change point detection</span></span>

<span data-ttu-id="88c58-221">`Change points` jsou trvalé změny v řady čas události datového proudu distribuci hodnot, jako jsou změny na úrovni a trendy.</span><span class="sxs-lookup"><span data-stu-id="88c58-221">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="88c58-222">Trvalé změny naposledy mnohem delší než `spikes` a může znamenat katastrofické události.</span><span class="sxs-lookup"><span data-stu-id="88c58-222">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="88c58-223">`Change points` se obvykle nezobrazí pouhým okem, ale můžete zjistit ve vašich datech pomocí přístupů například následující metodu.</span><span class="sxs-lookup"><span data-stu-id="88c58-223">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="88c58-224">Na následujícím obrázku je příklad bodu detekce změn:</span><span class="sxs-lookup"><span data-stu-id="88c58-224">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="88c58-226">Vytvoření DetectChangepoint() – metoda</span><span class="sxs-lookup"><span data-stu-id="88c58-226">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="88c58-227">Přidejte následující volání `DetectChangepoint()`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-227">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="88c58-228">`DetectChangepoint()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="88c58-228">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="88c58-229">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="88c58-229">Trains the model.</span></span>
* <span data-ttu-id="88c58-230">Zjistí změnu body na základě historických dat prodeje.</span><span class="sxs-lookup"><span data-stu-id="88c58-230">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="88c58-231">Zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="88c58-231">Displays the results.</span></span>

<span data-ttu-id="88c58-232">Vytvořte `DetectChangepoint()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="88c58-232">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="88c58-233">[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) se používá pro trénování modelu pro změnu bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="88c58-233">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="88c58-234">Přidejte ji tak `DetectChangepoint()` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="88c58-234">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="88c58-235">Stejně jako dříve, podle modelu, který má `productSales` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-235">As you did previously, fit the model to the `productSales` data and return the trained model by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="88c58-236">Použití `Transform()` metody k transformaci `Training` data přidáním následujícího kódu do `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="88c58-236">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="88c58-237">Stejně jako dříve, převést vaše `transformedData` do silného typu `IEnumerable` pro snadnější zobrazení pomocí `CreateEnumerable()`metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="88c58-237">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="88c58-238">Vytvořit záhlaví zobrazení jako na další řádek v následujícím kódem `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="88c58-238">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="88c58-239">Ve výsledcích zjišťování změn bodu budete zobrazovat následující informace:</span><span class="sxs-lookup"><span data-stu-id="88c58-239">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="88c58-240">`Alert` označuje změnit bod oznámení pro daný datový bod.</span><span class="sxs-lookup"><span data-stu-id="88c58-240">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="88c58-241">`Score` je `ProductSales` hodnotu pro daný datový bod v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="88c58-241">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="88c58-242">`P-Value` "P" jsou zahrnovaného pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="88c58-242">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="88c58-243">To znamená, jaká je pravděpodobnost tento datový bod je anomálie.</span><span class="sxs-lookup"><span data-stu-id="88c58-243">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="88c58-244">`Martingale value` se používá k identifikaci, jak je "divně" datový bod, v závislosti na sekvenci hodnot P.</span><span class="sxs-lookup"><span data-stu-id="88c58-244">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="88c58-245">Iterovat přes `predictions` `IEnumerable` a zobrazit výsledky s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="88c58-245">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="88c58-246">Změna bodu zjišťování výsledky</span><span class="sxs-lookup"><span data-stu-id="88c58-246">Change point detection results</span></span>

<span data-ttu-id="88c58-247">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="88c58-247">Your results should be similar to the following.</span></span> <span data-ttu-id="88c58-248">Během zpracování zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="88c58-248">During processing, messages are displayed.</span></span> <span data-ttu-id="88c58-249">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="88c58-249">You may see warnings, or processing messages.</span></span> <span data-ttu-id="88c58-250">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="88c58-250">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="88c58-251">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="88c58-251">Congratulations!</span></span> <span data-ttu-id="88c58-252">Jste teď úspěšně sestaven modelů strojového učení pro zjišťování provozní špičky a změnit bod anomálie v prodejní data.</span><span class="sxs-lookup"><span data-stu-id="88c58-252">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="88c58-253">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) úložiště.</span><span class="sxs-lookup"><span data-stu-id="88c58-253">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="88c58-254">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="88c58-254">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="88c58-255">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="88c58-255">Load the data</span></span>
> * <span data-ttu-id="88c58-256">Trénování modelu pro detekci anomálií ve špičce</span><span class="sxs-lookup"><span data-stu-id="88c58-256">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="88c58-257">Detekovat anomálie ve špičce pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="88c58-257">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="88c58-258">Trénování modelu pro změnu bodu pro detekci anomálií</span><span class="sxs-lookup"><span data-stu-id="88c58-258">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="88c58-259">Detekovat anomálie bodu změnu s režimem trénovaného</span><span class="sxs-lookup"><span data-stu-id="88c58-259">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="88c58-260">Další kroky</span><span class="sxs-lookup"><span data-stu-id="88c58-260">Next steps</span></span>

<span data-ttu-id="88c58-261">Projděte si úložišti GitHub s ukázkami Machine Learning a prozkoumejte ukázkový spotřebu energie pro detekci anomálií.</span><span class="sxs-lookup"><span data-stu-id="88c58-261">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="88c58-262">úložiště GitHub DotNet/machinelearning – ukázky</span><span class="sxs-lookup"><span data-stu-id="88c58-262">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection)