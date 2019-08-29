---
title: 'Kurz: Analyzovat komentáře webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 4daa7734f12c57a177fab3c62fdd96bda22838af
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107169"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="26ce0-104">Kurz: Analýza mínění komentářů k webu pomocí binární klasifikace v ML.NET</span><span class="sxs-lookup"><span data-stu-id="26ce0-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="26ce0-105">V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="26ce0-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="26ce0-106">Mínění třídění binárních souborů používá C# v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="26ce0-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="26ce0-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="26ce0-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="26ce0-108">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="26ce0-108">Create a console application</span></span>
> - <span data-ttu-id="26ce0-109">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-109">Prepare data</span></span>
> - <span data-ttu-id="26ce0-110">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-110">Load the data</span></span>
> - <span data-ttu-id="26ce0-111">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-111">Build and train the model</span></span>
> - <span data-ttu-id="26ce0-112">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-112">Evaluate the model</span></span>
> - <span data-ttu-id="26ce0-113">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="26ce0-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="26ce0-114">Zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="26ce0-114">See the results</span></span>

<span data-ttu-id="26ce0-115">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="26ce0-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26ce0-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26ce0-116">Prerequisites</span></span>

- <span data-ttu-id="26ce0-117">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="26ce0-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="26ce0-118">[Datová sada vět mínění](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) s popiskem (Soubor ZIP)</span><span class="sxs-lookup"><span data-stu-id="26ce0-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="26ce0-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="26ce0-119">Create a console application</span></span>

1. <span data-ttu-id="26ce0-120">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="26ce0-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="26ce0-121">Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="26ce0-122">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="26ce0-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="26ce0-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="26ce0-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="26ce0-124">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="26ce0-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="26ce0-125">Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček.</span><span class="sxs-lookup"><span data-stu-id="26ce0-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="26ce0-126">Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="26ce0-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="26ce0-127">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="26ce0-128">Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="26ce0-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="26ce0-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="26ce0-129">al,.</span></span> <span data-ttu-id="26ce0-130">KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="26ce0-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="26ce0-131">UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="26ce0-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="26ce0-132">Irvine, certifikační autorita: University of California, školní informace a počítačové vědy.</span><span class="sxs-lookup"><span data-stu-id="26ce0-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="26ce0-133">Stáhněte [soubor zip datové sady mínění](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)s popiskem a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="26ce0-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="26ce0-134">Zkopírujte soubor do adresáře dat, který jste vytvořili. `yelp_labelled.txt`</span><span class="sxs-lookup"><span data-stu-id="26ce0-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="26ce0-135">V Průzkumník řešení klikněte pravým tlačítkem na `yelp_labeled.txt` soubor a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="26ce0-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="26ce0-136">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="26ce0-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="26ce0-137">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="26ce0-137">Create classes and define paths</span></span>

1. <span data-ttu-id="26ce0-138">Do horní části souboru `using` *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="26ce0-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="26ce0-139">Vytvořte dvě globální pole, která budou uchovávat nedávno staženou cestu k souboru datové sady a uloženou cestu k souboru modelu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    - <span data-ttu-id="26ce0-140">`_dataPath`má cestu k datové sadě, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    - <span data-ttu-id="26ce0-141">`_modelPath`má cestu, kde je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="26ce0-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="26ce0-142">Přidejte následující kód na řádek přímo nad `Main` metodu pro určení cest:</span><span class="sxs-lookup"><span data-stu-id="26ce0-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="26ce0-143">Dále vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="26ce0-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="26ce0-144">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="26ce0-145">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="26ce0-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="26ce0-146">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="26ce0-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="26ce0-147">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="26ce0-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="26ce0-148">V editoru kódu se otevře soubor *SentimentData.cs* .</span><span class="sxs-lookup"><span data-stu-id="26ce0-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="26ce0-149">Do horní části `using` *SentimentData.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="26ce0-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="26ce0-150">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do souboru *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="26ce0-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="26ce0-151">Způsob přípravy dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-151">How the data was prepared</span></span>
<span data-ttu-id="26ce0-152">Vstupní třída datové sady, `SentimentData` `string` má hodnotu pro `bool` komentáře uživatele (`SentimentText`) a hodnotu (`Sentiment`) pro mínění (kladné) nebo 0 (negativní).</span><span class="sxs-lookup"><span data-stu-id="26ce0-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="26ce0-153">Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="26ce0-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="26ce0-154">Kromě toho `Sentiment` má vlastnost atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) k `Label` označení jako pole.</span><span class="sxs-lookup"><span data-stu-id="26ce0-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="26ce0-155">Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="26ce0-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="26ce0-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="26ce0-156">SentimentText</span></span>                         |<span data-ttu-id="26ce0-157">Mínění (popisek)</span><span class="sxs-lookup"><span data-stu-id="26ce0-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="26ce0-158">Waitress bylo v provozu trochu pomalé.</span><span class="sxs-lookup"><span data-stu-id="26ce0-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="26ce0-159">0</span><span class="sxs-lookup"><span data-stu-id="26ce0-159">0</span></span>     |
|<span data-ttu-id="26ce0-160">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="26ce0-160">Crust is not good.</span></span>                    |    <span data-ttu-id="26ce0-161">0</span><span class="sxs-lookup"><span data-stu-id="26ce0-161">0</span></span>     |
|<span data-ttu-id="26ce0-162">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="26ce0-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="26ce0-163">1</span><span class="sxs-lookup"><span data-stu-id="26ce0-163">1</span></span>     |
|<span data-ttu-id="26ce0-164">Služba byla velmi výzvou.</span><span class="sxs-lookup"><span data-stu-id="26ce0-164">Service was very prompt.</span></span>              |    <span data-ttu-id="26ce0-165">1</span><span class="sxs-lookup"><span data-stu-id="26ce0-165">1</span></span>     |

<span data-ttu-id="26ce0-166">`SentimentPrediction`je třída předpovědi, která se používá po školení modelu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-166">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="26ce0-167">Dědí z `SentimentData` , aby se vstup `SentimentText` mohl zobrazit společně s předpovědí výstupu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-167">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="26ce0-168">Logická hodnota je hodnota, kterou model předpovídá, pokud je zadán s novým vstupem `SentimentText`. `Prediction`</span><span class="sxs-lookup"><span data-stu-id="26ce0-168">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="26ce0-169">Třída `SentimentPrediction` Output obsahuje dvě další vlastnosti, které jsou vypočítány `Score` modelem: – nezpracované skóre počítané modelem a `Probability` – skóre, které se kalibruje na pravděpodobnost textu s kladným míněníem.</span><span class="sxs-lookup"><span data-stu-id="26ce0-169">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="26ce0-170">V tomto kurzu je `Prediction`nejdůležitější vlastností.</span><span class="sxs-lookup"><span data-stu-id="26ce0-170">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="26ce0-171">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-171">Load the data</span></span>
<span data-ttu-id="26ce0-172">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="26ce0-172">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="26ce0-173">`IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="26ce0-173">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="26ce0-174">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-174">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="26ce0-175">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET.</span><span class="sxs-lookup"><span data-stu-id="26ce0-175">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="26ce0-176">Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="26ce0-176">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="26ce0-177">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="26ce0-177">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="26ce0-178">Aplikaci připravíte a pak načtěte data:</span><span class="sxs-lookup"><span data-stu-id="26ce0-178">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="26ce0-179">Nahraďte `Main` řádek v metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="26ce0-179">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="26ce0-180">Přidejte následující jako další řádek kódu v `Main()` metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-180">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="26ce0-181">Vytvořte metodu hned `Main()` za metodou pomocí následujícího kódu: `LoadData()`</span><span class="sxs-lookup"><span data-stu-id="26ce0-181">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="26ce0-182">`LoadData()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="26ce0-182">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="26ce0-183">Načte data.</span><span class="sxs-lookup"><span data-stu-id="26ce0-183">Loads the data.</span></span>
    - <span data-ttu-id="26ce0-184">Rozdělí načtenou datovou sadu do sady výukových a testovacích datových sad.</span><span class="sxs-lookup"><span data-stu-id="26ce0-184">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="26ce0-185">Vrátí rozdělený vlak a testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="26ce0-185">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="26ce0-186">Do prvního řádku `LoadData()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="26ce0-186">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="26ce0-187">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="26ce0-187">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="26ce0-188">Převezme proměnné cesty k datům a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="26ce0-188">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="26ce0-189">Rozdělení datové sady pro školení modelů a testování</span><span class="sxs-lookup"><span data-stu-id="26ce0-189">Split the dataset for model training and testing</span></span>

<span data-ttu-id="26ce0-190">Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-190">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="26ce0-191">Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v `LoadData()` metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-191">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="26ce0-192">Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení do třídy [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) .</span><span class="sxs-lookup"><span data-stu-id="26ce0-192">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="26ce0-193">Zadejte procento testovací sady dat s `testFraction`parametrem.</span><span class="sxs-lookup"><span data-stu-id="26ce0-193">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="26ce0-194">Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-194">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="26ce0-195">Vraťte se `splitDataView` na konec `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="26ce0-195">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="26ce0-196">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-196">Build and train the model</span></span>

1. <span data-ttu-id="26ce0-197">Do metody přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu `Main()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-197">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="26ce0-198">`BuildAndTrainModel()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="26ce0-198">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="26ce0-199">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="26ce0-199">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="26ce0-200">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="26ce0-200">Trains the model.</span></span>
    - <span data-ttu-id="26ce0-201">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-201">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="26ce0-202">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="26ce0-202">Returns the model.</span></span>

2. <span data-ttu-id="26ce0-203">Vytvořte metodu hned `Main()` za metodou pomocí následujícího kódu: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="26ce0-203">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="26ce0-204">Extrakce a transformace dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-204">Extract and transform the data</span></span>

1. <span data-ttu-id="26ce0-205">Zavolat `FeaturizeText` jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-205">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="26ce0-206">Metoda v předchozím kódu převede textový sloupec (`SentimentText`) na sloupec typu `Features` číselného klíče, který používá algoritmus strojového učení, a přidá ho jako sloupec nové datové sady: `FeaturizeText()`</span><span class="sxs-lookup"><span data-stu-id="26ce0-206">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="26ce0-207">SentimentText</span><span class="sxs-lookup"><span data-stu-id="26ce0-207">SentimentText</span></span>                         |<span data-ttu-id="26ce0-208">Mínění</span><span class="sxs-lookup"><span data-stu-id="26ce0-208">Sentiment</span></span> |<span data-ttu-id="26ce0-209">Funkce</span><span class="sxs-lookup"><span data-stu-id="26ce0-209">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="26ce0-210">Waitress bylo v provozu trochu pomalé.</span><span class="sxs-lookup"><span data-stu-id="26ce0-210">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="26ce0-211">0</span><span class="sxs-lookup"><span data-stu-id="26ce0-211">0</span></span>     |<span data-ttu-id="26ce0-212">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="26ce0-212">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="26ce0-213">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="26ce0-213">Crust is not good.</span></span>                    |    <span data-ttu-id="26ce0-214">0</span><span class="sxs-lookup"><span data-stu-id="26ce0-214">0</span></span>     |<span data-ttu-id="26ce0-215">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="26ce0-215">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="26ce0-216">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="26ce0-216">Wow... Loved this place.</span></span>              |    <span data-ttu-id="26ce0-217">1</span><span class="sxs-lookup"><span data-stu-id="26ce0-217">1</span></span>     |<span data-ttu-id="26ce0-218">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="26ce0-218">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="26ce0-219">Služba byla velmi výzvou.</span><span class="sxs-lookup"><span data-stu-id="26ce0-219">Service was very prompt.</span></span>              |    <span data-ttu-id="26ce0-220">1</span><span class="sxs-lookup"><span data-stu-id="26ce0-220">1</span></span>     |<span data-ttu-id="26ce0-221">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="26ce0-221">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="26ce0-222">Přidání sledovacího algoritmu</span><span class="sxs-lookup"><span data-stu-id="26ce0-222">Add a learning algorithm</span></span>

<span data-ttu-id="26ce0-223">Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-223">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="26ce0-224">Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="26ce0-224">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="26ce0-225">Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="26ce0-225">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="26ce0-226">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="26ce0-226">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="26ce0-227">Tento `estimator` údaj je připojen k a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry pro získání informací z historických dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-227">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="26ce0-228">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-228">Train the model</span></span>

<span data-ttu-id="26ce0-229">Přizpůsobte si model `splitTrainSet` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu `BuildAndTrainModel()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-229">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="26ce0-230">Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.</span><span class="sxs-lookup"><span data-stu-id="26ce0-230">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="26ce0-231">Vrátí vyškolený model, který se má použít pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="26ce0-231">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="26ce0-232">Vrátí model na konci `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="26ce0-232">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="26ce0-233">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-233">Evaluate the model</span></span>

<span data-ttu-id="26ce0-234">Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-234">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="26ce0-235">Vytvořte metodu, hned po `BuildAndTrainModel()`, s následujícím kódem: `Evaluate()`</span><span class="sxs-lookup"><span data-stu-id="26ce0-235">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="26ce0-236">`Evaluate()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="26ce0-236">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="26ce0-237">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-237">Loads the test dataset.</span></span>
    - <span data-ttu-id="26ce0-238">Vytvoří vyhodnocovací filtr BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="26ce0-238">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="26ce0-239">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="26ce0-239">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="26ce0-240">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="26ce0-240">Displays the metrics.</span></span>

2. <span data-ttu-id="26ce0-241">Přidejte volání do metody New z `Main()` metody přímo `BuildAndTrainModel()` pod voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-241">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="26ce0-242">Transformujte `Evaluate()`data přidáním následujícího kódu do: `splitTestSet`</span><span class="sxs-lookup"><span data-stu-id="26ce0-242">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="26ce0-243">Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-243">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="26ce0-244">Vyhodnoťte model přidáním následujícího jako další řádek kódu v `Evaluate()` metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-244">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="26ce0-245">Po nastavení`predictions`předpovědi () Metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečnou `Labels` hodnotou v testovací sadě a vrátí [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objekt, na kterém model probíhá.</span><span class="sxs-lookup"><span data-stu-id="26ce0-245">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="26ce0-246">Zobrazení metrik pro ověřování modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-246">Displaying the metrics for model validation</span></span>

<span data-ttu-id="26ce0-247">K zobrazení metrik použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="26ce0-247">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="26ce0-248">`Accuracy` Metrika získá přesnost modelu, což je poměr správných předpovědi v sadě testů.</span><span class="sxs-lookup"><span data-stu-id="26ce0-248">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="26ce0-249">`AreaUnderRocCurve` Metrika označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy.</span><span class="sxs-lookup"><span data-stu-id="26ce0-249">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="26ce0-250">Chcete, aby `AreaUnderRocCurve` byl co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-250">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="26ce0-251">Metrika získá skóre modelu F1, což je míra rovnováhy mezi přesností a [](../resources/glossary.md#precision) odvoláním. [](../resources/glossary.md#recall) `F1Score`</span><span class="sxs-lookup"><span data-stu-id="26ce0-251">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="26ce0-252">Chcete, aby `F1Score` byl co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-252">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="26ce0-253">Předpověď výsledku testovacích dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-253">Predict the test data outcome</span></span>

1. <span data-ttu-id="26ce0-254">Vytvořte metodu hned `Evaluate()` za metodou pomocí následujícího kódu: `UseModelWithSingleItem()`</span><span class="sxs-lookup"><span data-stu-id="26ce0-254">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="26ce0-255">`UseModelWithSingleItem()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="26ce0-255">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="26ce0-256">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-256">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="26ce0-257">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-257">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="26ce0-258">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="26ce0-258">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="26ce0-259">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="26ce0-259">Displays the predicted results.</span></span>

2. <span data-ttu-id="26ce0-260">Přidejte volání do metody New z `Main()` metody přímo `Evaluate()` pod voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-260">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="26ce0-261">Přidejte následující kód, který chcete vytvořit jako první řádek v `UseModelWithSingleItem()` metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-261">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="26ce0-262">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-262">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="26ce0-263">Přidejte komentář k otestování předpovědi vyškolených modelů v `UseModelWithSingleItem()` metodě vytvořením `SentimentData`instance:</span><span class="sxs-lookup"><span data-stu-id="26ce0-263">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="26ce0-264">Předání dat testovacích komentářů do do `Prediction Engine` přidejte následujícím způsobem jako další řádky kódu `UseModelWithSingleItem()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-264">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="26ce0-265">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-265">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="26ce0-266">Zobrazit `SentimentText` a odpovídající předpovědi mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-266">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="26ce0-267">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="26ce0-267">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="26ce0-268">Nasazení a předpověď položek Batch</span><span class="sxs-lookup"><span data-stu-id="26ce0-268">Deploy and predict batch items</span></span>

1. <span data-ttu-id="26ce0-269">Vytvořte metodu hned `UseModelWithSingleItem()` za metodou pomocí následujícího kódu: `UseModelWithBatchItems()`</span><span class="sxs-lookup"><span data-stu-id="26ce0-269">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="26ce0-270">`UseModelWithBatchItems()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="26ce0-270">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="26ce0-271">Vytvoří data dávkového testu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-271">Creates batch test data.</span></span>
    - <span data-ttu-id="26ce0-272">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="26ce0-272">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="26ce0-273">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="26ce0-273">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="26ce0-274">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="26ce0-274">Displays the predicted results.</span></span>

2. <span data-ttu-id="26ce0-275">Přidejte volání do metody New z `Main` metody přímo `UseModelWithSingleItem()` pod voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-275">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="26ce0-276">Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů `UseModelWithBatchItems()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="26ce0-276">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="26ce0-277">Předpověď komentáře mínění</span><span class="sxs-lookup"><span data-stu-id="26ce0-277">Predict comment sentiment</span></span>

<span data-ttu-id="26ce0-278">Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="26ce0-278">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="26ce0-279">Kombinování a zobrazení předpovědi</span><span class="sxs-lookup"><span data-stu-id="26ce0-279">Combine and display the predictions</span></span>

<span data-ttu-id="26ce0-280">Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="26ce0-280">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="26ce0-281">Vzhledem `SentimentPrediction` k tomu, `SentimentData`že je `Transform()` zděděn z `SentimentText` , metoda naplněná předpovězenými poli.</span><span class="sxs-lookup"><span data-stu-id="26ce0-281">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="26ce0-282">Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="26ce0-282">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="26ce0-283">Výsledky</span><span class="sxs-lookup"><span data-stu-id="26ce0-283">Results</span></span>

<span data-ttu-id="26ce0-284">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="26ce0-284">Your results should be similar to the following.</span></span> <span data-ttu-id="26ce0-285">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="26ce0-285">During processing, messages are displayed.</span></span> <span data-ttu-id="26ce0-286">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="26ce0-286">You may see warnings, or processing messages.</span></span> <span data-ttu-id="26ce0-287">Tyto výsledky byly z důvodu srozumitelnosti odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="26ce0-287">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="26ce0-288">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="26ce0-288">Congratulations!</span></span> <span data-ttu-id="26ce0-289">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění.</span><span class="sxs-lookup"><span data-stu-id="26ce0-289">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="26ce0-290">Sestavování úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="26ce0-290">Building successful models is an iterative process.</span></span> <span data-ttu-id="26ce0-291">Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady.</span><span class="sxs-lookup"><span data-stu-id="26ce0-291">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="26ce0-292">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými [parametry Hyper-](../resources/glossary.md##hyperparameter) v pro každý algoritmus.</span><span class="sxs-lookup"><span data-stu-id="26ce0-292">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="26ce0-293">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="26ce0-293">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="26ce0-294">Další kroky</span><span class="sxs-lookup"><span data-stu-id="26ce0-294">Next steps</span></span>

<span data-ttu-id="26ce0-295">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="26ce0-295">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="26ce0-296">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="26ce0-296">Create a console application</span></span>
> - <span data-ttu-id="26ce0-297">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-297">Prepare data</span></span>
> - <span data-ttu-id="26ce0-298">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="26ce0-298">Load the data</span></span>
> - <span data-ttu-id="26ce0-299">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-299">Build and train the model</span></span>
> - <span data-ttu-id="26ce0-300">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="26ce0-300">Evaluate the model</span></span>
> - <span data-ttu-id="26ce0-301">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="26ce0-301">Use the model to make a prediction</span></span>
> - <span data-ttu-id="26ce0-302">Zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="26ce0-302">See the results</span></span>

<span data-ttu-id="26ce0-303">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="26ce0-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="26ce0-304">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="26ce0-304">Issue Classification</span></span>](github-issue-classification.md)
