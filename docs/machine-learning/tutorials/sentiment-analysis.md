---
title: 'Kurz: analýza komentářů webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárního prostředí používá jazyk C# v aplikaci Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: de8ea511b3d421e391b182a6de079b854d3f2390
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281750"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="8d83e-104">Kurz: analýza mínění komentářů k webu pomocí binární klasifikace v ML.NET</span><span class="sxs-lookup"><span data-stu-id="8d83e-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="8d83e-105">V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="8d83e-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="8d83e-106">Mínění třídění binárního prostředí používá jazyk C# v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8d83e-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="8d83e-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="8d83e-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8d83e-108">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="8d83e-108">Create a console application</span></span>
> - <span data-ttu-id="8d83e-109">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-109">Prepare data</span></span>
> - <span data-ttu-id="8d83e-110">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-110">Load the data</span></span>
> - <span data-ttu-id="8d83e-111">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-111">Build and train the model</span></span>
> - <span data-ttu-id="8d83e-112">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-112">Evaluate the model</span></span>
> - <span data-ttu-id="8d83e-113">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d83e-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="8d83e-114">Zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="8d83e-114">See the results</span></span>

<span data-ttu-id="8d83e-115">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="8d83e-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d83e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d83e-116">Prerequisites</span></span>

- <span data-ttu-id="8d83e-117">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="8d83e-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="8d83e-118">[Mínění – datová sada vět s popisky](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)</span><span class="sxs-lookup"><span data-stu-id="8d83e-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8d83e-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="8d83e-119">Create a console application</span></span>

1. <span data-ttu-id="8d83e-120">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="8d83e-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="8d83e-121">Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="8d83e-122">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="8d83e-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="8d83e-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8d83e-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8d83e-124">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="8d83e-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="8d83e-125">Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček.</span><span class="sxs-lookup"><span data-stu-id="8d83e-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="8d83e-126">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-126">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="8d83e-127">Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="8d83e-127">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="8d83e-128">Al,.</span><span class="sxs-lookup"><span data-stu-id="8d83e-128">al,.</span></span> <span data-ttu-id="8d83e-129">KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="8d83e-129">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="8d83e-130">UCI Machine Learning úložiště [ http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="8d83e-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="8d83e-131">Irvine, CA: University of California, školní informace a počítačové vědy.</span><span class="sxs-lookup"><span data-stu-id="8d83e-131">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="8d83e-132">Stáhněte [soubor zip datové sady mínění s popiskem](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="8d83e-132">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="8d83e-133">Zkopírujte `yelp_labelled.txt` soubor do adresáře *dat* , který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="8d83e-133">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="8d83e-134">V Průzkumník řešení klikněte pravým tlačítkem na `yelp_labeled.txt` soubor a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8d83e-134">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="8d83e-135">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="8d83e-135">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="8d83e-136">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="8d83e-136">Create classes and define paths</span></span>

1. <span data-ttu-id="8d83e-137">`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="8d83e-137">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="8d83e-138">Přidejte následující kód na řádek vpravo nad `Main` metodou, chcete-li vytvořit pole, které bude uchovávat nedávno staženou cestu k souboru datové sady:</span><span class="sxs-lookup"><span data-stu-id="8d83e-138">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](./snippets/sentiment-analysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="8d83e-139">Dále vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="8d83e-139">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="8d83e-140">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-140">Add a new class to your project:</span></span>

    - <span data-ttu-id="8d83e-141">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="8d83e-141">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="8d83e-142">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="8d83e-142">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="8d83e-143">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="8d83e-143">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="8d83e-144">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="8d83e-144">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8d83e-145">`using`Do horní části *SentimentData.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8d83e-145">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="8d83e-146">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction` , do souboru *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="8d83e-146">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/sentiment-analysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="8d83e-147">Způsob přípravy dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-147">How the data was prepared</span></span>

<span data-ttu-id="8d83e-148">Vstupní třída datové sady, `SentimentData` má `string` hodnotu pro komentáře uživatele ( `SentimentText` ) a `bool` `Sentiment` hodnotu () pro mínění (kladné) nebo 0 (negativní).</span><span class="sxs-lookup"><span data-stu-id="8d83e-148">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="8d83e-149">Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="8d83e-149">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="8d83e-150">Kromě toho `Sentiment` má vlastnost atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) k označení jako `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="8d83e-150">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="8d83e-151">Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8d83e-151">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="8d83e-152">SentimentText</span><span class="sxs-lookup"><span data-stu-id="8d83e-152">SentimentText</span></span>                         |<span data-ttu-id="8d83e-153">Mínění (popisek)</span><span class="sxs-lookup"><span data-stu-id="8d83e-153">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="8d83e-154">Waitress bylo v provozu trochu pomalé.</span><span class="sxs-lookup"><span data-stu-id="8d83e-154">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="8d83e-155">0</span><span class="sxs-lookup"><span data-stu-id="8d83e-155">0</span></span>     |
|<span data-ttu-id="8d83e-156">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="8d83e-156">Crust is not good.</span></span>                    |    <span data-ttu-id="8d83e-157">0</span><span class="sxs-lookup"><span data-stu-id="8d83e-157">0</span></span>     |
|<span data-ttu-id="8d83e-158">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="8d83e-158">Wow... Loved this place.</span></span>              |    <span data-ttu-id="8d83e-159">1</span><span class="sxs-lookup"><span data-stu-id="8d83e-159">1</span></span>     |
|<span data-ttu-id="8d83e-160">Služba byla velmi výzvou.</span><span class="sxs-lookup"><span data-stu-id="8d83e-160">Service was very prompt.</span></span>              |    <span data-ttu-id="8d83e-161">1</span><span class="sxs-lookup"><span data-stu-id="8d83e-161">1</span></span>     |

<span data-ttu-id="8d83e-162">`SentimentPrediction`je třída předpovědi, která se používá po školení modelu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-162">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="8d83e-163">Dědí z `SentimentData` , aby se vstup `SentimentText` mohl zobrazit společně s předpovědí výstupu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-163">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="8d83e-164">`Prediction`Logická hodnota je hodnota, kterou model předpovídá, pokud je zadán s novým vstupem `SentimentText` .</span><span class="sxs-lookup"><span data-stu-id="8d83e-164">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="8d83e-165">Třída Output `SentimentPrediction` obsahuje dvě další vlastnosti, které jsou vypočítány modelem: `Score` – nezpracované skóre počítané modelem a `Probability` – skóre, které se kalibruje na pravděpodobnost textu s kladným míněníem.</span><span class="sxs-lookup"><span data-stu-id="8d83e-165">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="8d83e-166">V tomto kurzu je nejdůležitější vlastností `Prediction` .</span><span class="sxs-lookup"><span data-stu-id="8d83e-166">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="8d83e-167">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-167">Load the data</span></span>

<span data-ttu-id="8d83e-168">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="8d83e-168">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="8d83e-169">`IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="8d83e-169">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="8d83e-170">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-170">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="8d83e-171">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET.</span><span class="sxs-lookup"><span data-stu-id="8d83e-171">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="8d83e-172">Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="8d83e-172">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="8d83e-173">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8d83e-173">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="8d83e-174">Aplikaci připravíte a pak načtěte data:</span><span class="sxs-lookup"><span data-stu-id="8d83e-174">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="8d83e-175">Nahraďte `Console.WriteLine("Hello World!")` řádek v `Main` metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext:</span><span class="sxs-lookup"><span data-stu-id="8d83e-175">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/sentiment-analysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="8d83e-176">Přidejte následující jako další řádek kódu v `Main()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-176">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](./snippets/sentiment-analysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="8d83e-177">Vytvořte `LoadData()` metodu hned za `Main()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-177">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="8d83e-178">`LoadData()`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8d83e-178">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="8d83e-179">Načte data.</span><span class="sxs-lookup"><span data-stu-id="8d83e-179">Loads the data.</span></span>
    - <span data-ttu-id="8d83e-180">Rozdělí načtenou datovou sadu do sady výukových a testovacích datových sad.</span><span class="sxs-lookup"><span data-stu-id="8d83e-180">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="8d83e-181">Vrátí rozdělený vlak a testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="8d83e-181">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="8d83e-182">Do prvního řádku metody přidejte následující kód `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="8d83e-182">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](./snippets/sentiment-analysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="8d83e-183">Metoda [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="8d83e-183">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="8d83e-184">Převezme proměnné cesty k datům a vrátí `IDataView` .</span><span class="sxs-lookup"><span data-stu-id="8d83e-184">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="8d83e-185">Rozdělení datové sady pro školení modelů a testování</span><span class="sxs-lookup"><span data-stu-id="8d83e-185">Split the dataset for model training and testing</span></span>

<span data-ttu-id="8d83e-186">Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-186">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="8d83e-187">Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v `LoadData()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-187">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](./snippets/sentiment-analysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="8d83e-188">Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení ve <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> třídě.</span><span class="sxs-lookup"><span data-stu-id="8d83e-188">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="8d83e-189">Zadejte procento testovací sady dat s `testFraction` parametrem.</span><span class="sxs-lookup"><span data-stu-id="8d83e-189">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="8d83e-190">Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-190">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="8d83e-191">Vraťte se na `splitDataView` konec `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="8d83e-191">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](./snippets/sentiment-analysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="8d83e-192">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-192">Build and train the model</span></span>

1. <span data-ttu-id="8d83e-193">Do metody přidejte následující volání `BuildAndTrainModel` metody jako další řádek kódu v `Main()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-193">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](./snippets/sentiment-analysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="8d83e-194">`BuildAndTrainModel()`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8d83e-194">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="8d83e-195">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="8d83e-195">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="8d83e-196">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="8d83e-196">Trains the model.</span></span>
    - <span data-ttu-id="8d83e-197">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-197">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="8d83e-198">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="8d83e-198">Returns the model.</span></span>

2. <span data-ttu-id="8d83e-199">Vytvořte `BuildAndTrainModel()` metodu hned za `Main()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-199">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="8d83e-200">Extrakce a transformace dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-200">Extract and transform the data</span></span>

1. <span data-ttu-id="8d83e-201">Zavolat `FeaturizeText` jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-201">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](./snippets/sentiment-analysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="8d83e-202">`FeaturizeText()`Metoda v předchozím kódu převede textový sloupec ( `SentimentText` ) na sloupec typu číselného klíče, který `Features` používá algoritmus strojového učení, a přidá ho jako sloupec nové datové sady:</span><span class="sxs-lookup"><span data-stu-id="8d83e-202">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="8d83e-203">SentimentText</span><span class="sxs-lookup"><span data-stu-id="8d83e-203">SentimentText</span></span>                         |<span data-ttu-id="8d83e-204">Mínění</span><span class="sxs-lookup"><span data-stu-id="8d83e-204">Sentiment</span></span> |<span data-ttu-id="8d83e-205">Funkce</span><span class="sxs-lookup"><span data-stu-id="8d83e-205">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="8d83e-206">Waitress bylo v provozu trochu pomalé.</span><span class="sxs-lookup"><span data-stu-id="8d83e-206">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="8d83e-207">0</span><span class="sxs-lookup"><span data-stu-id="8d83e-207">0</span></span>     |<span data-ttu-id="8d83e-208">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="8d83e-208">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="8d83e-209">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="8d83e-209">Crust is not good.</span></span>                    |    <span data-ttu-id="8d83e-210">0</span><span class="sxs-lookup"><span data-stu-id="8d83e-210">0</span></span>     |<span data-ttu-id="8d83e-211">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="8d83e-211">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="8d83e-212">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="8d83e-212">Wow... Loved this place.</span></span>              |    <span data-ttu-id="8d83e-213">1</span><span class="sxs-lookup"><span data-stu-id="8d83e-213">1</span></span>     |<span data-ttu-id="8d83e-214">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="8d83e-214">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="8d83e-215">Služba byla velmi výzvou.</span><span class="sxs-lookup"><span data-stu-id="8d83e-215">Service was very prompt.</span></span>              |    <span data-ttu-id="8d83e-216">1</span><span class="sxs-lookup"><span data-stu-id="8d83e-216">1</span></span>     |<span data-ttu-id="8d83e-217">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="8d83e-217">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="8d83e-218">Přidání sledovacího algoritmu</span><span class="sxs-lookup"><span data-stu-id="8d83e-218">Add a learning algorithm</span></span>

<span data-ttu-id="8d83e-219">Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-219">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="8d83e-220">Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="8d83e-220">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="8d83e-221">Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="8d83e-221">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](./snippets/sentiment-analysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="8d83e-222">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="8d83e-222">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="8d83e-223">Tento údaj je připojen k `estimator` a přijímá natrénuje `SentimentText` ( `Features` ) a `Label` vstupní parametry pro získání informací z historických dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-223">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="8d83e-224">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-224">Train the model</span></span>

<span data-ttu-id="8d83e-225">Přizpůsobte si model `splitTrainSet` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `BuildAndTrainModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-225">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](./snippets/sentiment-analysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="8d83e-226">Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.</span><span class="sxs-lookup"><span data-stu-id="8d83e-226">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="8d83e-227">Vrátí vyškolený model, který se má použít pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="8d83e-227">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="8d83e-228">Vrátí model na konci `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="8d83e-228">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/sentiment-analysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="8d83e-229">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-229">Evaluate the model</span></span>

<span data-ttu-id="8d83e-230">Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-230">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="8d83e-231">Vytvořte `Evaluate()` metodu, hned po `BuildAndTrainModel()` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8d83e-231">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="8d83e-232">`Evaluate()`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8d83e-232">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="8d83e-233">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-233">Loads the test dataset.</span></span>
    - <span data-ttu-id="8d83e-234">Vytvoří vyhodnocovací filtr BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="8d83e-234">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="8d83e-235">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="8d83e-235">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="8d83e-236">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="8d83e-236">Displays the metrics.</span></span>

2. <span data-ttu-id="8d83e-237">Přidejte volání do metody New z `Main()` metody přímo pod `BuildAndTrainModel()` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-237">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](./snippets/sentiment-analysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="8d83e-238">Transformujte `splitTestSet` data přidáním následujícího kódu do `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="8d83e-238">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](./snippets/sentiment-analysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="8d83e-239">Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-239">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="8d83e-240">Vyhodnoťte model přidáním následujícího jako další řádek kódu v `Evaluate()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-240">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](./snippets/sentiment-analysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="8d83e-241">Jakmile máte nastavení předpovědi ( `predictions` ), metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací datové sadě a vrátí objekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) , jak model provádí.</span><span class="sxs-lookup"><span data-stu-id="8d83e-241">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="8d83e-242">Zobrazení metrik pro ověřování modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-242">Displaying the metrics for model validation</span></span>

<span data-ttu-id="8d83e-243">K zobrazení metrik použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="8d83e-243">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](./snippets/sentiment-analysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="8d83e-244">`Accuracy`Metrika získá přesnost modelu, což je poměr správných předpovědi v sadě testů.</span><span class="sxs-lookup"><span data-stu-id="8d83e-244">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="8d83e-245">`AreaUnderRocCurve`Metrika označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy.</span><span class="sxs-lookup"><span data-stu-id="8d83e-245">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="8d83e-246">Chcete, aby byl co `AreaUnderRocCurve` nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-246">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="8d83e-247">`F1Score`Metrika získá skóre modelu F1, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="8d83e-247">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="8d83e-248">Chcete, aby byl co `F1Score` nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-248">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="8d83e-249">Předpověď výsledku testovacích dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-249">Predict the test data outcome</span></span>

1. <span data-ttu-id="8d83e-250">Vytvořte `UseModelWithSingleItem()` metodu hned za `Evaluate()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-250">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="8d83e-251">`UseModelWithSingleItem()`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8d83e-251">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="8d83e-252">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-252">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="8d83e-253">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-253">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="8d83e-254">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="8d83e-254">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="8d83e-255">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d83e-255">Displays the predicted results.</span></span>

2. <span data-ttu-id="8d83e-256">Přidejte volání do metody New z `Main()` metody přímo pod `Evaluate()` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-256">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="8d83e-257">Přidejte následující kód, který chcete vytvořit jako první řádek v `UseModelWithSingleItem()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-257">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](./snippets/sentiment-analysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="8d83e-258">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-258">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="8d83e-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="8d83e-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="8d83e-260">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="8d83e-260">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="8d83e-261">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d83e-261">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="8d83e-262">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="8d83e-262">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d83e-263">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="8d83e-263">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="8d83e-264">Přidejte komentář k otestování předpovědi vyškolených modelů v `UseModelWithSingleItem()` metodě vytvořením instance `SentimentData` :</span><span class="sxs-lookup"><span data-stu-id="8d83e-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="8d83e-265">Předání dat testovacích komentářů do do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) přidejte následujícím způsobem jako další řádky kódu v `UseModelWithSingleItem()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-265">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="8d83e-266">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="8d83e-267">Zobrazit `SentimentText` a odpovídající předpovědi mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](./snippets/sentiment-analysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="8d83e-268">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d83e-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="8d83e-269">Nasazení a předpověď položek Batch</span><span class="sxs-lookup"><span data-stu-id="8d83e-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="8d83e-270">Vytvořte `UseModelWithBatchItems()` metodu hned za `UseModelWithSingleItem()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="8d83e-271">`UseModelWithBatchItems()`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="8d83e-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="8d83e-272">Vytvoří data dávkového testu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-272">Creates batch test data.</span></span>
    - <span data-ttu-id="8d83e-273">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="8d83e-273">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="8d83e-274">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="8d83e-274">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="8d83e-275">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d83e-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="8d83e-276">Přidejte volání do metody New z `Main` metody přímo pod `UseModelWithSingleItem()` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="8d83e-277">Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů v `UseModelWithBatchItems()` metodě:</span><span class="sxs-lookup"><span data-stu-id="8d83e-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="8d83e-278">Předpověď komentáře mínění</span><span class="sxs-lookup"><span data-stu-id="8d83e-278">Predict comment sentiment</span></span>

<span data-ttu-id="8d83e-279">Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="8d83e-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="8d83e-280">Kombinování a zobrazení předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d83e-280">Combine and display the predictions</span></span>

<span data-ttu-id="8d83e-281">Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d83e-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](./snippets/sentiment-analysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="8d83e-282">Vzhledem k tomu `SentimentPrediction` , že je zděděn z `SentimentData` , `Transform()` Metoda naplněná `SentimentText` předpovězenými poli.</span><span class="sxs-lookup"><span data-stu-id="8d83e-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="8d83e-283">Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="8d83e-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](./snippets/sentiment-analysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="8d83e-284">Výsledky</span><span class="sxs-lookup"><span data-stu-id="8d83e-284">Results</span></span>

<span data-ttu-id="8d83e-285">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="8d83e-285">Your results should be similar to the following.</span></span> <span data-ttu-id="8d83e-286">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d83e-286">During processing, messages are displayed.</span></span> <span data-ttu-id="8d83e-287">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d83e-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="8d83e-288">Tyto výsledky byly z důvodu srozumitelnosti odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="8d83e-288">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="8d83e-289">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="8d83e-289">Congratulations!</span></span> <span data-ttu-id="8d83e-290">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění.</span><span class="sxs-lookup"><span data-stu-id="8d83e-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="8d83e-291">Sestavování úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="8d83e-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="8d83e-292">Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady.</span><span class="sxs-lookup"><span data-stu-id="8d83e-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="8d83e-293">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými [parametry Hyper-](../resources/glossary.md#hyperparameter) v pro každý algoritmus.</span><span class="sxs-lookup"><span data-stu-id="8d83e-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="8d83e-294">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="8d83e-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8d83e-295">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8d83e-295">Next steps</span></span>

<span data-ttu-id="8d83e-296">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="8d83e-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8d83e-297">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="8d83e-297">Create a console application</span></span>
> - <span data-ttu-id="8d83e-298">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-298">Prepare data</span></span>
> - <span data-ttu-id="8d83e-299">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="8d83e-299">Load the data</span></span>
> - <span data-ttu-id="8d83e-300">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-300">Build and train the model</span></span>
> - <span data-ttu-id="8d83e-301">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8d83e-301">Evaluate the model</span></span>
> - <span data-ttu-id="8d83e-302">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d83e-302">Use the model to make a prediction</span></span>
> - <span data-ttu-id="8d83e-303">Zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="8d83e-303">See the results</span></span>

<span data-ttu-id="8d83e-304">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="8d83e-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8d83e-305">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="8d83e-305">Issue Classification</span></span>](github-issue-classification.md)
