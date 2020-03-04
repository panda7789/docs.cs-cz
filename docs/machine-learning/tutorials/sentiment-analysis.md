---
title: 'Kurz: analýza komentářů webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241127"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="56568-104">Kurz: analýza mínění komentářů k webu pomocí binární klasifikace v ML.NET</span><span class="sxs-lookup"><span data-stu-id="56568-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="56568-105">V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="56568-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="56568-106">Mínění třídění binárních souborů používá C# v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="56568-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="56568-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="56568-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="56568-108">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="56568-108">Create a console application</span></span>
> - <span data-ttu-id="56568-109">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="56568-109">Prepare data</span></span>
> - <span data-ttu-id="56568-110">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="56568-110">Load the data</span></span>
> - <span data-ttu-id="56568-111">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="56568-111">Build and train the model</span></span>
> - <span data-ttu-id="56568-112">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="56568-112">Evaluate the model</span></span>
> - <span data-ttu-id="56568-113">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="56568-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="56568-114">Zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="56568-114">See the results</span></span>

<span data-ttu-id="56568-115">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="56568-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56568-116">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="56568-116">Prerequisites</span></span>

- <span data-ttu-id="56568-117">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="56568-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="56568-118">[Mínění – datová sada vět s popisky](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)</span><span class="sxs-lookup"><span data-stu-id="56568-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="56568-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="56568-119">Create a console application</span></span>

1. <span data-ttu-id="56568-120">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="56568-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="56568-121">Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.</span><span class="sxs-lookup"><span data-stu-id="56568-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="56568-122">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="56568-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="56568-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="56568-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="56568-124">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="56568-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="56568-125">Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček.</span><span class="sxs-lookup"><span data-stu-id="56568-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="56568-126">Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="56568-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="56568-127">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="56568-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="56568-128">Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="56568-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="56568-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="56568-129">al,.</span></span> <span data-ttu-id="56568-130">KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="56568-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="56568-131">UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="56568-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="56568-132">Irvine, CA: University of California, školní informace a počítačové vědy.</span><span class="sxs-lookup"><span data-stu-id="56568-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="56568-133">Stáhněte [soubor zip datové sady mínění s popiskem](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="56568-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="56568-134">Zkopírujte soubor `yelp_labelled.txt` do adresáře *dat* , který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="56568-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="56568-135">V Průzkumník řešení klikněte pravým tlačítkem na soubor `yelp_labeled.txt` a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="56568-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="56568-136">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="56568-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="56568-137">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="56568-137">Create classes and define paths</span></span>

1. <span data-ttu-id="56568-138">Do horní části souboru *program.cs* přidejte následující další příkazy `using`:</span><span class="sxs-lookup"><span data-stu-id="56568-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="56568-139">Přidejte následující kód na řádek vpravo nad `Main` metodou, chcete-li vytvořit pole pro uchování nedávno stažené cesty souboru datové sady:</span><span class="sxs-lookup"><span data-stu-id="56568-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="56568-140">Dále vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="56568-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="56568-141">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="56568-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="56568-142">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="56568-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="56568-143">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="56568-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="56568-144">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="56568-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="56568-145">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="56568-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="56568-146">Do horní části *SentimentData.cs*přidejte následující příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="56568-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="56568-147">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do souboru *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="56568-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="56568-148">Způsob přípravy dat</span><span class="sxs-lookup"><span data-stu-id="56568-148">How the data was prepared</span></span>

<span data-ttu-id="56568-149">Vstupní datová třída, `SentimentData`, má `string` pro komentáře uživatele (`SentimentText`) a hodnotu `bool` (`Sentiment`) pro hodnotu 1 (kladné) nebo 0 (negativní) pro mínění.</span><span class="sxs-lookup"><span data-stu-id="56568-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="56568-150">Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="56568-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="56568-151">Kromě toho vlastnost `Sentiment` má atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) k označení jako pole `Label`.</span><span class="sxs-lookup"><span data-stu-id="56568-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="56568-152">Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="56568-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="56568-153">SentimentText</span><span class="sxs-lookup"><span data-stu-id="56568-153">SentimentText</span></span>                         |<span data-ttu-id="56568-154">Mínění (popisek)</span><span class="sxs-lookup"><span data-stu-id="56568-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="56568-155">Waitress bylo v provozu trochu pomalé.</span><span class="sxs-lookup"><span data-stu-id="56568-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="56568-156">0</span><span class="sxs-lookup"><span data-stu-id="56568-156">0</span></span>     |
|<span data-ttu-id="56568-157">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="56568-157">Crust is not good.</span></span>                    |    <span data-ttu-id="56568-158">0</span><span class="sxs-lookup"><span data-stu-id="56568-158">0</span></span>     |
|<span data-ttu-id="56568-159">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="56568-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="56568-160">1</span><span class="sxs-lookup"><span data-stu-id="56568-160">1</span></span>     |
|<span data-ttu-id="56568-161">Služba byla velmi výzvou.</span><span class="sxs-lookup"><span data-stu-id="56568-161">Service was very prompt.</span></span>              |    <span data-ttu-id="56568-162">1</span><span class="sxs-lookup"><span data-stu-id="56568-162">1</span></span>     |

<span data-ttu-id="56568-163">`SentimentPrediction` je třída předpovědi, která se používá po školení modelu.</span><span class="sxs-lookup"><span data-stu-id="56568-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="56568-164">Dědí z `SentimentData` tak, aby se vstupní `SentimentText` mohl zobrazit společně s předpovědí výstupu.</span><span class="sxs-lookup"><span data-stu-id="56568-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="56568-165">`Prediction` Boolean je hodnota, kterou model předpovídá, pokud je zadán s novým vstupním `SentimentText`.</span><span class="sxs-lookup"><span data-stu-id="56568-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="56568-166">Výstupní třída `SentimentPrediction` obsahuje dvě další vlastnosti, které jsou vypočítány modelem: `Score`-nezpracované skóre počítané modelem a `Probability` – skóre kalibrované na pravděpodobnost textu, který má kladný mínění.</span><span class="sxs-lookup"><span data-stu-id="56568-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="56568-167">V tomto kurzu je nejdůležitější vlastností `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="56568-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="56568-168">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="56568-168">Load the data</span></span>

<span data-ttu-id="56568-169">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="56568-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="56568-170">`IDataView` je flexibilní a efektivní způsob popisující tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="56568-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="56568-171">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="56568-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="56568-172">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET.</span><span class="sxs-lookup"><span data-stu-id="56568-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="56568-173">Inicializuje se `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="56568-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="56568-174">Je podobný a koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="56568-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="56568-175">Aplikaci připravíte a pak načtěte data:</span><span class="sxs-lookup"><span data-stu-id="56568-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="56568-176">Nahraďte `Console.WriteLine("Hello World!")` řádek v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné mlContext:</span><span class="sxs-lookup"><span data-stu-id="56568-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="56568-177">Jako další řádek kódu v metodě `Main()` přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="56568-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="56568-178">Vytvořte metodu `LoadData()` hned za metodou `Main()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="56568-179">Metoda `LoadData()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="56568-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="56568-180">Načte data.</span><span class="sxs-lookup"><span data-stu-id="56568-180">Loads the data.</span></span>
    - <span data-ttu-id="56568-181">Rozdělí načtenou datovou sadu do sady výukových a testovacích datových sad.</span><span class="sxs-lookup"><span data-stu-id="56568-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="56568-182">Vrátí rozdělený vlak a testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="56568-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="56568-183">Do prvního řádku `LoadData()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="56568-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="56568-184">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="56568-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="56568-185">Převezme proměnné cesty k datům a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="56568-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="56568-186">Rozdělení datové sady pro školení modelů a testování</span><span class="sxs-lookup"><span data-stu-id="56568-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="56568-187">Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="56568-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="56568-188">Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v metodě `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="56568-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="56568-189">Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení do třídy [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) .</span><span class="sxs-lookup"><span data-stu-id="56568-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="56568-190">Zadejte procento testovací sady dat s parametrem `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="56568-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="56568-191">Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.</span><span class="sxs-lookup"><span data-stu-id="56568-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="56568-192">Vraťte `splitDataView` na konci `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="56568-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="56568-193">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="56568-193">Build and train the model</span></span>

1. <span data-ttu-id="56568-194">Přidejte následující volání metody `BuildAndTrainModel`jako další řádek kódu v metodě `Main()`:</span><span class="sxs-lookup"><span data-stu-id="56568-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="56568-195">Metoda `BuildAndTrainModel()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="56568-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="56568-196">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="56568-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="56568-197">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="56568-197">Trains the model.</span></span>
    - <span data-ttu-id="56568-198">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="56568-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="56568-199">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="56568-199">Returns the model.</span></span>

2. <span data-ttu-id="56568-200">Vytvořte metodu `BuildAndTrainModel()` hned za metodou `Main()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="56568-201">Extrakce a transformace dat</span><span class="sxs-lookup"><span data-stu-id="56568-201">Extract and transform the data</span></span>

1. <span data-ttu-id="56568-202">Zavolejte `FeaturizeText` jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="56568-203">Metoda `FeaturizeText()` v předchozím kódu převede textový sloupec (`SentimentText`) na typ číselného klíče `Features` sloupec používaný algoritmem strojového učení a přidá ho jako sloupec nové datové sady:</span><span class="sxs-lookup"><span data-stu-id="56568-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="56568-204">SentimentText</span><span class="sxs-lookup"><span data-stu-id="56568-204">SentimentText</span></span>                         |<span data-ttu-id="56568-205">Mínění</span><span class="sxs-lookup"><span data-stu-id="56568-205">Sentiment</span></span> |<span data-ttu-id="56568-206">Funkce</span><span class="sxs-lookup"><span data-stu-id="56568-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="56568-207">Waitress bylo v provozu trochu pomalé.</span><span class="sxs-lookup"><span data-stu-id="56568-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="56568-208">0</span><span class="sxs-lookup"><span data-stu-id="56568-208">0</span></span>     |<span data-ttu-id="56568-209">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="56568-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="56568-210">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="56568-210">Crust is not good.</span></span>                    |    <span data-ttu-id="56568-211">0</span><span class="sxs-lookup"><span data-stu-id="56568-211">0</span></span>     |<span data-ttu-id="56568-212">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="56568-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="56568-213">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="56568-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="56568-214">1</span><span class="sxs-lookup"><span data-stu-id="56568-214">1</span></span>     |<span data-ttu-id="56568-215">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="56568-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="56568-216">Služba byla velmi výzvou.</span><span class="sxs-lookup"><span data-stu-id="56568-216">Service was very prompt.</span></span>              |    <span data-ttu-id="56568-217">1</span><span class="sxs-lookup"><span data-stu-id="56568-217">1</span></span>     |<span data-ttu-id="56568-218">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="56568-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="56568-219">Přidání sledovacího algoritmu</span><span class="sxs-lookup"><span data-stu-id="56568-219">Add a learning algorithm</span></span>

<span data-ttu-id="56568-220">Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat.</span><span class="sxs-lookup"><span data-stu-id="56568-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="56568-221">Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="56568-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="56568-222">Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="56568-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="56568-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="56568-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="56568-224">Tento údaj je připojen k `estimator` a přijímá natrénuje `SentimentText` (`Features`) a vstupní parametry `Label` pro další informace z historických dat.</span><span class="sxs-lookup"><span data-stu-id="56568-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="56568-225">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="56568-225">Train the model</span></span>

<span data-ttu-id="56568-226">Přizpůsobit model na `splitTrainSet`á data a vrátit vyškolený model přidáním následujícího jako další řádek kódu v metodě `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="56568-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="56568-227">Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.</span><span class="sxs-lookup"><span data-stu-id="56568-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="56568-228">Vrátí vyškolený model, který se má použít pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="56568-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="56568-229">Vrátí model na konci `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="56568-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="56568-230">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="56568-230">Evaluate the model</span></span>

<span data-ttu-id="56568-231">Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="56568-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="56568-232">Vytvořte metodu `Evaluate()` hned po `BuildAndTrainModel()`s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="56568-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="56568-233">Metoda `Evaluate()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="56568-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="56568-234">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="56568-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="56568-235">Vytvoří vyhodnocovací filtr BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="56568-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="56568-236">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="56568-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="56568-237">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="56568-237">Displays the metrics.</span></span>

2. <span data-ttu-id="56568-238">Přidejte volání do nové metody z metody `Main()`, přímo pod voláním metody `BuildAndTrainModel()`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="56568-239">Transformujte data `splitTestSet` přidáním následujícího kódu do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="56568-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="56568-240">Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.</span><span class="sxs-lookup"><span data-stu-id="56568-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="56568-241">Vyhodnoťte model přidáním následujícího jako další řádek kódu v metodě `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="56568-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="56568-242">Jakmile máte sadu předpovědi (`predictions`), metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovná předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrátí objekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) , jak model provádí.</span><span class="sxs-lookup"><span data-stu-id="56568-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="56568-243">Zobrazení metrik pro ověřování modelu</span><span class="sxs-lookup"><span data-stu-id="56568-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="56568-244">K zobrazení metrik použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="56568-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="56568-245">Metrika `Accuracy` získá přesnost modelu, což je poměr správných předpovědi v sadě testů.</span><span class="sxs-lookup"><span data-stu-id="56568-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="56568-246">Metrika `AreaUnderRocCurve` označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy.</span><span class="sxs-lookup"><span data-stu-id="56568-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="56568-247">Chcete, aby `AreaUnderRocCurve` co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="56568-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="56568-248">Metrika `F1Score` získá skóre modelu F1, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="56568-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="56568-249">Chcete, aby `F1Score` co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="56568-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="56568-250">Předpověď výsledku testovacích dat</span><span class="sxs-lookup"><span data-stu-id="56568-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="56568-251">Vytvořte metodu `UseModelWithSingleItem()` hned za metodou `Evaluate()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="56568-252">Metoda `UseModelWithSingleItem()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="56568-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="56568-253">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="56568-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="56568-254">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="56568-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="56568-255">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="56568-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="56568-256">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="56568-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="56568-257">Přidejte volání do nové metody z metody `Main()`, přímo pod voláním metody `Evaluate()`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="56568-258">Přidejte následující kód, který chcete vytvořit jako první řádek v metodě `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="56568-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="56568-259">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="56568-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="56568-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="56568-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="56568-261">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="56568-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="56568-262">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="56568-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="56568-263">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="56568-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="56568-264">rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="56568-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="56568-265">Přidejte komentář k otestování předpovědi vyškolených modelů v metodě `UseModelWithSingleItem()` vytvořením instance `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="56568-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="56568-266">Předání dat testovacích komentářů do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) přidáním následujícího jako další řádky kódu v metodě `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="56568-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="56568-267">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.</span><span class="sxs-lookup"><span data-stu-id="56568-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="56568-268">Zobrazit `SentimentText` a odpovídající předpovědi mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="56568-269">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="56568-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="56568-270">Nasazení a předpověď položek Batch</span><span class="sxs-lookup"><span data-stu-id="56568-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="56568-271">Vytvořte metodu `UseModelWithBatchItems()` hned za metodou `UseModelWithSingleItem()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="56568-272">Metoda `UseModelWithBatchItems()` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="56568-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="56568-273">Vytvoří data dávkového testu.</span><span class="sxs-lookup"><span data-stu-id="56568-273">Creates batch test data.</span></span>
    - <span data-ttu-id="56568-274">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="56568-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="56568-275">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="56568-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="56568-276">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="56568-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="56568-277">Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `UseModelWithSingleItem()`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="56568-278">Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů v metodě `UseModelWithBatchItems()`:</span><span class="sxs-lookup"><span data-stu-id="56568-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="56568-279">Předpověď komentáře mínění</span><span class="sxs-lookup"><span data-stu-id="56568-279">Predict comment sentiment</span></span>

<span data-ttu-id="56568-280">Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="56568-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="56568-281">Kombinování a zobrazení předpovědi</span><span class="sxs-lookup"><span data-stu-id="56568-281">Combine and display the predictions</span></span>

<span data-ttu-id="56568-282">Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="56568-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="56568-283">Vzhledem k tomu, že `SentimentPrediction` dědí z `SentimentData`, `Transform()` metoda naplněná `SentimentText` s předpovězenými poli.</span><span class="sxs-lookup"><span data-stu-id="56568-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="56568-284">Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="56568-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="56568-285">Výsledky</span><span class="sxs-lookup"><span data-stu-id="56568-285">Results</span></span>

<span data-ttu-id="56568-286">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="56568-286">Your results should be similar to the following.</span></span> <span data-ttu-id="56568-287">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="56568-287">During processing, messages are displayed.</span></span> <span data-ttu-id="56568-288">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="56568-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="56568-289">Tyto výsledky byly z důvodu srozumitelnosti odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="56568-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="56568-290">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="56568-290">Congratulations!</span></span> <span data-ttu-id="56568-291">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění.</span><span class="sxs-lookup"><span data-stu-id="56568-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="56568-292">Sestavování úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="56568-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="56568-293">Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady.</span><span class="sxs-lookup"><span data-stu-id="56568-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="56568-294">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými [parametry Hyper-](../resources/glossary.md#hyperparameter) v pro každý algoritmus.</span><span class="sxs-lookup"><span data-stu-id="56568-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="56568-295">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="56568-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="56568-296">Další kroky</span><span class="sxs-lookup"><span data-stu-id="56568-296">Next steps</span></span>

<span data-ttu-id="56568-297">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="56568-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="56568-298">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="56568-298">Create a console application</span></span>
> - <span data-ttu-id="56568-299">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="56568-299">Prepare data</span></span>
> - <span data-ttu-id="56568-300">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="56568-300">Load the data</span></span>
> - <span data-ttu-id="56568-301">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="56568-301">Build and train the model</span></span>
> - <span data-ttu-id="56568-302">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="56568-302">Evaluate the model</span></span>
> - <span data-ttu-id="56568-303">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="56568-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="56568-304">Zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="56568-304">See the results</span></span>

<span data-ttu-id="56568-305">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="56568-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="56568-306">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="56568-306">Issue Classification</span></span>](github-issue-classification.md)
