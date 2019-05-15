---
title: 'Kurz: Analýza webu komentáře – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z webu komentářů a provede příslušnou akci. Používá klasifikátor binární mínění C# v sadě Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e145e65e22c955bd547b67de545b883fb0fb3bc2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593412"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="b0424-104">Kurz: Analýza sentimentu komentářů k webu pomocí binární klasifikace ML.NET</span><span class="sxs-lookup"><span data-stu-id="b0424-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="b0424-105">V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z webu komentářů a provede příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="b0424-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="b0424-106">Používá klasifikátor binární mínění C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b0424-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="b0424-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b0424-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b0424-108">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="b0424-108">Create a console application</span></span>
> * <span data-ttu-id="b0424-109">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b0424-109">Prepare data</span></span>
> * <span data-ttu-id="b0424-110">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b0424-110">Load the data</span></span>
> * <span data-ttu-id="b0424-111">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-111">Build and train the model</span></span>
> * <span data-ttu-id="b0424-112">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-112">Evaluate the model</span></span>
> * <span data-ttu-id="b0424-113">Použití modelu vytvoří předpověď</span><span class="sxs-lookup"><span data-stu-id="b0424-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="b0424-114">Zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="b0424-114">See the results</span></span>

<span data-ttu-id="b0424-115">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="b0424-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0424-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0424-116">Prerequisites</span></span>

* <span data-ttu-id="b0424-117">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s úlohou "Vývoj pro různé platformy .NET Core" nainstalovaná</span><span class="sxs-lookup"><span data-stu-id="b0424-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="b0424-118">[Datová sada UCI subjektivního hodnocení s popiskem věty](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)</span><span class="sxs-lookup"><span data-stu-id="b0424-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b0424-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="b0424-119">Create a console application</span></span>

1. <span data-ttu-id="b0424-120">Vytvoření **konzolovou aplikaci .NET Core** nazývá "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="b0424-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="b0424-121">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady.</span><span class="sxs-lookup"><span data-stu-id="b0424-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="b0424-122">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b0424-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b0424-123">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b0424-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b0424-124">Zvolte možnost "nuget.org" jako zdroj balíčku a pak vyberte **Procházet** kartu. Vyhledejte **Microsoft.ML**, vyberte balíček a pak vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b0424-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="b0424-125">Pokračovat v instalaci souhlasí s licenční podmínky pro balíček, který si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="b0424-125">Proceed with the installation by agreeing to the the license terms for the package you choose.</span></span> <span data-ttu-id="b0424-126">Totéž proveďte pro **Microsoft.ML.FastTree** balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0424-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="b0424-127">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b0424-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="b0424-128">Datové sady pro účely tohoto kurzu jsou ze "From skupiny na jednotlivé popisky pomocí podrobné funkce" Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="b0424-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="b0424-129">al,.</span><span class="sxs-lookup"><span data-stu-id="b0424-129">al,.</span></span> <span data-ttu-id="b0424-130">Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="b0424-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="b0424-131">UCI strojového učení úložiště [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="b0424-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="b0424-132">Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.</span><span class="sxs-lookup"><span data-stu-id="b0424-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="b0424-133">Stáhněte si [soubor ZIP datové sady UCI subjektivního hodnocení s popiskem věty](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="b0424-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="b0424-134">Kopírovat `yelp_labelled.txt` soubor do *Data* adresáře, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="b0424-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="b0424-135">V Průzkumníku řešení klikněte pravým tlačítkem myši `yelp_labeled.txt` a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b0424-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="b0424-136">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="b0424-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="b0424-137">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="b0424-137">Create classes and define paths</span></span>

1. <span data-ttu-id="b0424-138">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b0424-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="b0424-139">Vytvořte dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:</span><span class="sxs-lookup"><span data-stu-id="b0424-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="b0424-140">`_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="b0424-141">`_modelPath` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="b0424-142">Přidejte následující kód na řádku vpravo nahoře `Main` metodu pro zadání cesty:</span><span class="sxs-lookup"><span data-stu-id="b0424-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="b0424-143">Dále vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b0424-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="b0424-144">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="b0424-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="b0424-145">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="b0424-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="b0424-146">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b0424-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="b0424-147">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b0424-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="b0424-148">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b0424-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b0424-149">Přidejte následující `using` příkaz do horní části *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b0424-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="b0424-150">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b0424-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="b0424-151">Jak se připravit data</span><span class="sxs-lookup"><span data-stu-id="b0424-151">How the data was prepared</span></span>
<span data-ttu-id="b0424-152">Třída vstupní datová sada `SentimentData`, má `string` pro komentáře uživatelů (`SentimentText`) a `bool` (`Sentiment`) hodnotu 1 (pozitivní) nebo 0 (negativní) mínění.</span><span class="sxs-lookup"><span data-stu-id="b0424-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="b0424-153">Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy připojené k nim, který popisuje soubor pořadí dat u každého pole.</span><span class="sxs-lookup"><span data-stu-id="b0424-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="b0424-154">Kromě toho `Sentiment` má vlastnost [Názevsloupce](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atribut nastavit jako `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="b0424-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="b0424-155">Následující příklad souboru nemá řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="b0424-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="b0424-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="b0424-156">SentimentText</span></span>                         |<span data-ttu-id="b0424-157">Mínění (popisek)</span><span class="sxs-lookup"><span data-stu-id="b0424-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="b0424-158">Waitress pomalý trochu ve službě.</span><span class="sxs-lookup"><span data-stu-id="b0424-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="b0424-159">0</span><span class="sxs-lookup"><span data-stu-id="b0424-159">0</span></span>     |
|<span data-ttu-id="b0424-160">Povrch ovšem není vhodné.</span><span class="sxs-lookup"><span data-stu-id="b0424-160">Crust is not good.</span></span>                    |    <span data-ttu-id="b0424-161">0</span><span class="sxs-lookup"><span data-stu-id="b0424-161">0</span></span>     |
|<span data-ttu-id="b0424-162">WOW... Miluju toto místo.</span><span class="sxs-lookup"><span data-stu-id="b0424-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="b0424-163">1</span><span class="sxs-lookup"><span data-stu-id="b0424-163">1</span></span>     |
|<span data-ttu-id="b0424-164">Služba se velmi výzvy.</span><span class="sxs-lookup"><span data-stu-id="b0424-164">Service was very prompt.</span></span>              |    <span data-ttu-id="b0424-165">1</span><span class="sxs-lookup"><span data-stu-id="b0424-165">1</span></span>     |

<span data-ttu-id="b0424-166">`SentimentPrediction` je třída předpovědi používá po cvičení modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-166">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="b0424-167">Dědí z `SentimentData` pro zobrazení `SentimentText` s předpovědí.</span><span class="sxs-lookup"><span data-stu-id="b0424-167">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="b0424-168">`SentimentPrediction` má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="b0424-168">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="b0424-169">`Label` Slouží k vytvoření a trénování modelu a jeho rozdělení na testovací datové použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-169">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="b0424-170">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b0424-170">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="b0424-171">Pro vyhodnocení se používají trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="b0424-171">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="b0424-172">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b0424-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="b0424-173">Inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="b0424-174">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b0424-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b0424-175">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b0424-175">Load the data</span></span>
<span data-ttu-id="b0424-176">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="b0424-176">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="b0424-177">`IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="b0424-177">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="b0424-178">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="b0424-178">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="b0424-179">Příprava aplikace a pak načíst data:</span><span class="sxs-lookup"><span data-stu-id="b0424-179">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="b0424-180">Nahraďte `Console.WriteLine("Hello World!")` řádku v `Main` metodu, jak deklarovat a inicializovat proměnnou mlContext následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b0424-180">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="b0424-181">Přidejte následující položky jako další řádek kódu `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-181">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="b0424-182">Vytvořte `LoadData()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="b0424-183">`LoadData()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b0424-183">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="b0424-184">Načte data.</span><span class="sxs-lookup"><span data-stu-id="b0424-184">Loads the data.</span></span>
    * <span data-ttu-id="b0424-185">Rozdělí načíst datovou sadu na trénování a testování datových sad.</span><span class="sxs-lookup"><span data-stu-id="b0424-185">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="b0424-186">Vrátí hodnotu rozdělení trénují a testují datové sady.</span><span class="sxs-lookup"><span data-stu-id="b0424-186">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="b0424-187">Přidejte následující kód jako první řádek `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-187">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="b0424-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru.</span><span class="sxs-lookup"><span data-stu-id="b0424-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="b0424-189">Přijímá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="b0424-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="b0424-190">Rozdělení datové sady pro trénování a testování modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="b0424-191">Při přípravě na model, použijte část datové sady pro trénování a část datové sady, testování přesnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-191">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="b0424-192">Načtená data rozdělením potřebné datové sady, přidejte následující kód jako další řádek `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="b0424-193">Předchozí kód používá [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metodu rozdělit načíst datovou sadu na trénování a testování datových sad a vrátit je do [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) třídy.</span><span class="sxs-lookup"><span data-stu-id="b0424-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="b0424-194">Zadejte procento dat pomocí nastavení testu `testFraction`parametru.</span><span class="sxs-lookup"><span data-stu-id="b0424-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="b0424-195">Výchozí hodnota je 10 %, v tomto případě je použít 20 % k vyhodnocení další data.</span><span class="sxs-lookup"><span data-stu-id="b0424-195">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="b0424-196">Vrátit `splitDataView` na konci `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="b0424-197">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-197">Build and train the model</span></span>

1. <span data-ttu-id="b0424-198">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="b0424-199">`BuildAndTrainModel()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b0424-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="b0424-200">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="b0424-200">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="b0424-201">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-201">Trains the model.</span></span>
    * <span data-ttu-id="b0424-202">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="b0424-202">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="b0424-203">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-203">Returns the model.</span></span>

2. <span data-ttu-id="b0424-204">Vytvořte `BuildAndTrainModel()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="b0424-205">Extrahovat a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="b0424-205">Extract and transform the data</span></span>

1. <span data-ttu-id="b0424-206">Volání `FeaturizeText` jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-206">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="b0424-207">`FeaturizeText()` Metoda v předchozím kódu převede textový sloupec (`SentimentText`) na číselný typ klíče `Features` sloupec používá algoritmu strojového učení a přidá ho jakou novou datovou sadu sloupce:</span><span class="sxs-lookup"><span data-stu-id="b0424-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="b0424-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="b0424-208">SentimentText</span></span>                         |<span data-ttu-id="b0424-209">Mínění</span><span class="sxs-lookup"><span data-stu-id="b0424-209">Sentiment</span></span> |<span data-ttu-id="b0424-210">Funkce</span><span class="sxs-lookup"><span data-stu-id="b0424-210">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="b0424-211">Waitress pomalý trochu ve službě.</span><span class="sxs-lookup"><span data-stu-id="b0424-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="b0424-212">0</span><span class="sxs-lookup"><span data-stu-id="b0424-212">0</span></span>     |<span data-ttu-id="b0424-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="b0424-213">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="b0424-214">Povrch ovšem není vhodné.</span><span class="sxs-lookup"><span data-stu-id="b0424-214">Crust is not good.</span></span>                    |    <span data-ttu-id="b0424-215">0</span><span class="sxs-lookup"><span data-stu-id="b0424-215">0</span></span>     |<span data-ttu-id="b0424-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="b0424-216">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="b0424-217">WOW... Miluju toto místo.</span><span class="sxs-lookup"><span data-stu-id="b0424-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="b0424-218">1</span><span class="sxs-lookup"><span data-stu-id="b0424-218">1</span></span>     |<span data-ttu-id="b0424-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="b0424-219">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="b0424-220">Služba se velmi výzvy.</span><span class="sxs-lookup"><span data-stu-id="b0424-220">Service was very prompt.</span></span>              |    <span data-ttu-id="b0424-221">1</span><span class="sxs-lookup"><span data-stu-id="b0424-221">1</span></span>     |<span data-ttu-id="b0424-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="b0424-222">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="b0424-223">Přidat algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="b0424-223">Add a learning algorithm</span></span>

<span data-ttu-id="b0424-224">Tato aplikace používá klasifikační algoritmus, který slouží ke kategorizaci položky nebo řádky s daty.</span><span class="sxs-lookup"><span data-stu-id="b0424-224">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="b0424-225">Aplikace slouží ke kategorizaci komentáře webu jako kladné nebo záporné, takže pomocí binární klasifikace úlohy.</span><span class="sxs-lookup"><span data-stu-id="b0424-225">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="b0424-226">Přidat úlohy strojového učení do definice transformace dat přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="b0424-226">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="b0424-227">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je vaše klasifikace cvičení algoritmu.</span><span class="sxs-lookup"><span data-stu-id="b0424-227">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="b0424-228">To se připojí `estimator` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="b0424-228">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="b0424-229">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-229">Train the model</span></span>

<span data-ttu-id="b0424-230">Přizpůsobit modelu, který má `splitTrainSet` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-230">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="b0424-231">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="b0424-231">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="b0424-232">Vrátí že model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="b0424-232">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="b0424-233">Model na konci vrátit `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-233">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="b0424-234">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-234">Evaluate the model</span></span>

<span data-ttu-id="b0424-235">Poté, co váš model se trénuje, použijte test ověřit data výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-235">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="b0424-236">Vytvořte `Evaluate()` metoda, hned za `BuildAndTrainModel()`, následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b0424-236">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="b0424-237">`Evaluate()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b0424-237">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="b0424-238">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="b0424-238">Loads the test dataset.</span></span>
    * <span data-ttu-id="b0424-239">Chyba při vyhodnocování BinaryClassification vytvoří.</span><span class="sxs-lookup"><span data-stu-id="b0424-239">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="b0424-240">Vyhodnotí modelu a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="b0424-240">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="b0424-241">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="b0424-241">Displays the metrics.</span></span>

2. <span data-ttu-id="b0424-242">Přidejte volání do nové metody z `Main()` metody, v rámci `BuildAndTrainModel()` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-242">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="b0424-243">Transformace `splitTestSet` data přidáním následujícího kódu do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="b0424-243">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="b0424-244">Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda k následné predikci pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="b0424-244">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="b0424-245">Přidáním následujícího kódu jako další řádek kódu ve vyhodnocení modelu `Evaluate()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-245">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="b0424-246">Jakmile budete mít do predikce. Nastavte (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` datovou sadu testů a vrátí [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objektu, na jaký je výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="b0424-246">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="b0424-247">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-247">Displaying the metrics for model validation</span></span>

<span data-ttu-id="b0424-248">Použijte následující kód k zobrazení metriky:</span><span class="sxs-lookup"><span data-stu-id="b0424-248">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="b0424-249">`Accuracy` Metrika získá přesnost modelu, který je poměr správné predikce v testovací sadě.</span><span class="sxs-lookup"><span data-stu-id="b0424-249">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="b0424-250">`AreaUnderRocCurve` Metrika vyjadřuje důvěru modelu je správně klasifikace třídy kladné a záporné.</span><span class="sxs-lookup"><span data-stu-id="b0424-250">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="b0424-251">Chcete, aby `AreaUnderRocCurve` bude blízko jeden nejvíce.</span><span class="sxs-lookup"><span data-stu-id="b0424-251">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="b0424-252">`F1Score` Metrika získá modelu F1 skóre, které je míra rovnováhu mezi [přesnost](../resources/glossary.md#precision) a [spojené s vracením](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="b0424-252">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="b0424-253">Chcete, aby `F1Score` bude blízko jeden nejvíce.</span><span class="sxs-lookup"><span data-stu-id="b0424-253">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="b0424-254">Předpověď data výsledek testu</span><span class="sxs-lookup"><span data-stu-id="b0424-254">Predict the test data outcome</span></span>

1. <span data-ttu-id="b0424-255">Vytvořte `UseModelWithSingleItem()` metoda, hned za `Evaluate()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-255">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="b0424-256">`UseModelWithSingleItem()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b0424-256">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="b0424-257">Vytvoří jeden komentář testovací data.</span><span class="sxs-lookup"><span data-stu-id="b0424-257">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="b0424-258">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="b0424-258">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="b0424-259">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="b0424-259">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="b0424-260">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="b0424-260">Displays the predicted results.</span></span>

2. <span data-ttu-id="b0424-261">Přidejte volání do nové metody z `Main()` metody, v rámci `Evaluate()` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-261">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="b0424-262">Přidejte následující kód k vytvoření jako první řádek `Predict()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-262">Add the following code to create as the first line in the `Predict()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="b0424-263">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je vhodné rozhraní API, což vám umožní předat a pak proveďte predikcí na jednu instanci data.</span><span class="sxs-lookup"><span data-stu-id="b0424-263">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="b0424-264">Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict()` metodu tak, že vytvoříte instanci `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="b0424-264">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="b0424-265">Předání dat komentář test `Prediction Engine` přidáním následujícího kódu jako další řádky kódu ve `UseModelWithSingleItem()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-265">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="b0424-266">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) predikcí na jednom řádku dat díky funkce.</span><span class="sxs-lookup"><span data-stu-id="b0424-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="b0424-267">Zobrazení `SentimentText` a odpovídající předpovědí mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="b0424-268">Použití modelu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="b0424-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="b0424-269">Nasazení a předvídání položky služby batch</span><span class="sxs-lookup"><span data-stu-id="b0424-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="b0424-270">Vytvořte `UseModelWithBatchItems()` metoda, hned za `UseModelWithSingleItem()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="b0424-271">`UseModelWithBatchItems()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b0424-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="b0424-272">Vytvoří služby batch testovací data.</span><span class="sxs-lookup"><span data-stu-id="b0424-272">Creates batch test data.</span></span>
    * <span data-ttu-id="b0424-273">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="b0424-273">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="b0424-274">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="b0424-274">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="b0424-275">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="b0424-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="b0424-276">Přidejte volání do nové metody z `Main` metody, v rámci `UseModelWithSingleItem()` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="b0424-277">Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `UseModelWithBatchItems()` metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="b0424-278">Předpověď mínění komentář</span><span class="sxs-lookup"><span data-stu-id="b0424-278">Predict comment sentiment</span></span>

<span data-ttu-id="b0424-279">Použít model k predikci komentář data subjektivního hodnocení s využitím [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="b0424-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="b0424-280">Spojit a zobrazit předpovědi</span><span class="sxs-lookup"><span data-stu-id="b0424-280">Combine and display the predictions</span></span>

<span data-ttu-id="b0424-281">Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="b0424-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="b0424-282">Protože `SentimentPrediction` je zděděno od `SentimentData`, `Transform()` metoda vyplní `SentimentText` s předpokládanou pole.</span><span class="sxs-lookup"><span data-stu-id="b0424-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="b0424-283">Procesu ML.NET zpracovává, jednotlivé komponenty přidá sloupce, a to usnadňuje zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="b0424-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="b0424-284">Výsledky</span><span class="sxs-lookup"><span data-stu-id="b0424-284">Results</span></span>

<span data-ttu-id="b0424-285">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="b0424-285">Your results should be similar to the following.</span></span> <span data-ttu-id="b0424-286">Během zpracování zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="b0424-286">During processing, messages are displayed.</span></span> <span data-ttu-id="b0424-287">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="b0424-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="b0424-288">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="b0424-288">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="b0424-289">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="b0424-289">Congratulations!</span></span> <span data-ttu-id="b0424-290">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění.</span><span class="sxs-lookup"><span data-stu-id="b0424-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="b0424-291">Vytváření modelů po úspěšné je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="b0424-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="b0424-292">Tento model má nižší počáteční kvalita jako kurz používá malé datové sady poskytují rychlý model školení.</span><span class="sxs-lookup"><span data-stu-id="b0424-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="b0424-293">Pokud si nejste spokojeni s kvalitou modelu, můžete zkusit ho vylepšit tím, že poskytuje větší cvičných datových sad nebo výběrem jiné trénování algoritmů s různými [hyperparametry](../resources/glossary.md##hyperparameter) pro jednotlivé algoritmy.</span><span class="sxs-lookup"><span data-stu-id="b0424-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="b0424-294">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="b0424-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b0424-295">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b0424-295">Next steps</span></span>

<span data-ttu-id="b0424-296">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="b0424-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b0424-297">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="b0424-297">Create a console application</span></span>
> * <span data-ttu-id="b0424-298">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b0424-298">Prepare data</span></span>
> * <span data-ttu-id="b0424-299">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b0424-299">Load the data</span></span>
> * <span data-ttu-id="b0424-300">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-300">Build and train the model</span></span>
> * <span data-ttu-id="b0424-301">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b0424-301">Evaluate the model</span></span>
> * <span data-ttu-id="b0424-302">Použití modelu vytvoří předpověď</span><span class="sxs-lookup"><span data-stu-id="b0424-302">Use the model to make a prediction</span></span>
> * <span data-ttu-id="b0424-303">Zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="b0424-303">See the results</span></span>

<span data-ttu-id="b0424-304">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="b0424-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b0424-305">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="b0424-305">Issue Classification</span></span>](github-issue-classification.md)
