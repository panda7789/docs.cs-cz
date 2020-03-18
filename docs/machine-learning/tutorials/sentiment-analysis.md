---
title: 'Kurz: Analýza komentářů na webových stránkách - binární klasifikace'
description: Tento kurz ukazuje, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů na webu a provede příslušnou akci. Binární třídění mínění používá C# v sadě Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241127"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="39c5c-104">Kurz: Analýza mínění komentářů na webových stránkách s binární klasifikací v ML.NET</span><span class="sxs-lookup"><span data-stu-id="39c5c-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="39c5c-105">Tento kurz ukazuje, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů na webu a provede příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="39c5c-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="39c5c-106">Binární třídění mínění používá C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="39c5c-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="39c5c-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="39c5c-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="39c5c-108">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="39c5c-108">Create a console application</span></span>
> - <span data-ttu-id="39c5c-109">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-109">Prepare data</span></span>
> - <span data-ttu-id="39c5c-110">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-110">Load the data</span></span>
> - <span data-ttu-id="39c5c-111">Sestavení a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-111">Build and train the model</span></span>
> - <span data-ttu-id="39c5c-112">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-112">Evaluate the model</span></span>
> - <span data-ttu-id="39c5c-113">Pomocí modelu proveďte předpověď</span><span class="sxs-lookup"><span data-stu-id="39c5c-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="39c5c-114">Zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="39c5c-114">See the results</span></span>

<span data-ttu-id="39c5c-115">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)</span><span class="sxs-lookup"><span data-stu-id="39c5c-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="39c5c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39c5c-116">Prerequisites</span></span>

- <span data-ttu-id="39c5c-117">[Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou pro vývoj napříč platformami ".NET Core"</span><span class="sxs-lookup"><span data-stu-id="39c5c-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="39c5c-118">[Datová sada vět mínění UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)</span><span class="sxs-lookup"><span data-stu-id="39c5c-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="39c5c-119">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="39c5c-119">Create a console application</span></span>

1. <span data-ttu-id="39c5c-120">Vytvořte **aplikaci .NET Core Console** s názvem "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="39c5c-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="39c5c-121">Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="39c5c-122">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="39c5c-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="39c5c-123">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="39c5c-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="39c5c-124">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet.** **Vyhledejte Microsoft.ML**, vyberte požadovaný balíček a pak vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="39c5c-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="39c5c-125">Pokračujte v instalaci souhlasem s licenčními podmínkami pro vámi zvolené balíček.</span><span class="sxs-lookup"><span data-stu-id="39c5c-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="39c5c-126">Proveďte totéž pro balíček **Microsoft.ML.FastTree** NuGet.</span><span class="sxs-lookup"><span data-stu-id="39c5c-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="39c5c-127">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="39c5c-128">Datové sady pro tento kurz jsou ze skupiny na jednotlivé popisky pomocí deep funkce, Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="39c5c-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="39c5c-129">Al.</span><span class="sxs-lookup"><span data-stu-id="39c5c-129">al,.</span></span> <span data-ttu-id="39c5c-130">KDD 2015 a hostované v Úložišti strojového učení UCI - Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="39c5c-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="39c5c-131">Úložiště strojového učeníhttp://archive.ics.uci.edu/mlUCI [ ].</span><span class="sxs-lookup"><span data-stu-id="39c5c-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="39c5c-132">Irvine, KALIFORNIE: Kalifornská univerzita, Škola informací a informatiky.</span><span class="sxs-lookup"><span data-stu-id="39c5c-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="39c5c-133">Stáhnout [UCI Sentiment označené věty soubor ZIP](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)soubor zip a rozbalit.</span><span class="sxs-lookup"><span data-stu-id="39c5c-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="39c5c-134">Zkopírujte `yelp_labelled.txt` soubor do *datového adresáře,* který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="39c5c-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="39c5c-135">V Průzkumníku řešení klepněte pravým tlačítkem `yelp_labeled.txt` myši na soubor a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="39c5c-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="39c5c-136">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="39c5c-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="39c5c-137">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="39c5c-137">Create classes and define paths</span></span>

1. <span data-ttu-id="39c5c-138">Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:</span><span class="sxs-lookup"><span data-stu-id="39c5c-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="39c5c-139">Přidejte následující kód na řádek `Main` přímo nad metodou, chcete-li vytvořit pole pro uložení nedávno stažené cesty souboru datové sady:</span><span class="sxs-lookup"><span data-stu-id="39c5c-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="39c5c-140">Dále vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="39c5c-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="39c5c-141">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="39c5c-142">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="39c5c-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="39c5c-143">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="39c5c-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="39c5c-144">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="39c5c-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="39c5c-145">Soubor *SentimentData.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="39c5c-146">Na začátek `using` *SentimentData.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="39c5c-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="39c5c-147">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do *souboru SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="39c5c-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="39c5c-148">Jak byla data připravena</span><span class="sxs-lookup"><span data-stu-id="39c5c-148">How the data was prepared</span></span>

<span data-ttu-id="39c5c-149">Vstupní třída datové `SentimentData`sady , `string` má pro`SentimentText`komentáře `bool` uživatele`Sentiment`( ) a ( ) hodnotu buď 1 (kladné) nebo 0 (negativní) pro mínění.</span><span class="sxs-lookup"><span data-stu-id="39c5c-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="39c5c-150">K oběma polím jsou připojeny atributy [LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) které popisují pořadí datových souborů každého pole.</span><span class="sxs-lookup"><span data-stu-id="39c5c-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="39c5c-151">Kromě toho `Sentiment` vlastnost má [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atribut k `Label` označení jako pole.</span><span class="sxs-lookup"><span data-stu-id="39c5c-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="39c5c-152">Následující ukázkový soubor nemá řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="39c5c-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="39c5c-153">SentimentText</span><span class="sxs-lookup"><span data-stu-id="39c5c-153">SentimentText</span></span>                         |<span data-ttu-id="39c5c-154">Mínění (popisek)</span><span class="sxs-lookup"><span data-stu-id="39c5c-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="39c5c-155">Servírka byla trochu pomalá ve službě.</span><span class="sxs-lookup"><span data-stu-id="39c5c-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="39c5c-156">0</span><span class="sxs-lookup"><span data-stu-id="39c5c-156">0</span></span>     |
|<span data-ttu-id="39c5c-157">Kůrka není dobrá.</span><span class="sxs-lookup"><span data-stu-id="39c5c-157">Crust is not good.</span></span>                    |    <span data-ttu-id="39c5c-158">0</span><span class="sxs-lookup"><span data-stu-id="39c5c-158">0</span></span>     |
|<span data-ttu-id="39c5c-159">Wow... Miloval toto místo.</span><span class="sxs-lookup"><span data-stu-id="39c5c-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="39c5c-160">1</span><span class="sxs-lookup"><span data-stu-id="39c5c-160">1</span></span>     |
|<span data-ttu-id="39c5c-161">Služba byla velmi rychlá.</span><span class="sxs-lookup"><span data-stu-id="39c5c-161">Service was very prompt.</span></span>              |    <span data-ttu-id="39c5c-162">1</span><span class="sxs-lookup"><span data-stu-id="39c5c-162">1</span></span>     |

<span data-ttu-id="39c5c-163">`SentimentPrediction`je třída předpověď použitá po trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="39c5c-164">Dědí z `SentimentData` tak, `SentimentText` aby vstup lze zobrazit spolu s předpovědí výstupu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="39c5c-165">Logická `Prediction` hodnota je hodnota, kterou model předpovídá `SentimentText`při dodání s novým vstupem .</span><span class="sxs-lookup"><span data-stu-id="39c5c-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="39c5c-166">Výstupní třída `SentimentPrediction` obsahuje dvě další vlastnosti `Score` vypočítané podle modelu: - `Probability` nezpracované skóre vypočítané modelem a - skóre kalibrované podle pravděpodobnosti, že text bude mít kladný názor.</span><span class="sxs-lookup"><span data-stu-id="39c5c-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="39c5c-167">Pro tento kurz je `Prediction`nejdůležitější vlastností .</span><span class="sxs-lookup"><span data-stu-id="39c5c-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="39c5c-168">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-168">Load the data</span></span>

<span data-ttu-id="39c5c-169">Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="39c5c-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="39c5c-170">`IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových).</span><span class="sxs-lookup"><span data-stu-id="39c5c-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="39c5c-171">Data lze načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu. `IDataView`</span><span class="sxs-lookup"><span data-stu-id="39c5c-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="39c5c-172">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET.</span><span class="sxs-lookup"><span data-stu-id="39c5c-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="39c5c-173">Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="39c5c-174">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="39c5c-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="39c5c-175">Připravíte aplikaci a pak načtete data:</span><span class="sxs-lookup"><span data-stu-id="39c5c-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="39c5c-176">Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro deklarování a inicializaci proměnné mlContext:</span><span class="sxs-lookup"><span data-stu-id="39c5c-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="39c5c-177">Jako další řádek kódu v metodě přidejte `Main()` následující:</span><span class="sxs-lookup"><span data-stu-id="39c5c-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="39c5c-178">Vytvořte `LoadData()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="39c5c-179">Metoda `LoadData()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="39c5c-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="39c5c-180">Načte data.</span><span class="sxs-lookup"><span data-stu-id="39c5c-180">Loads the data.</span></span>
    - <span data-ttu-id="39c5c-181">Rozdělí načtenou datovou sadu na datové sady train a test.</span><span class="sxs-lookup"><span data-stu-id="39c5c-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="39c5c-182">Vrátí rozdělený vlak a testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="39c5c-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="39c5c-183">Jako první řádek `LoadData()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="39c5c-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="39c5c-184">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru.</span><span class="sxs-lookup"><span data-stu-id="39c5c-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="39c5c-185">Přebírá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="39c5c-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="39c5c-186">Rozdělení datové sady pro trénování a testování modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="39c5c-187">Při přípravě modelu použijete část datové sady k jeho trénování a část datové sady k testování přesnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="39c5c-188">Chcete-li načtená data rozdělit do potřebných datových sad, `LoadData()` přidejte následující kód jako další řádek metody:</span><span class="sxs-lookup"><span data-stu-id="39c5c-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="39c5c-189">Předchozí kód používá [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metoda rozdělit načtené datové sady do datových sad train a test a vrátit je ve třídě [TrainTestData.](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData)</span><span class="sxs-lookup"><span data-stu-id="39c5c-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="39c5c-190">Zadejte procento dat testovací `testFraction`sady s parametrem.</span><span class="sxs-lookup"><span data-stu-id="39c5c-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="39c5c-191">Výchozí hodnota je 10 %, v tomto případě použijete 20 % k vyhodnocení více dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="39c5c-192">Vraťte `splitDataView` na konci `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="39c5c-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="39c5c-193">Sestavení a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-193">Build and train the model</span></span>

1. <span data-ttu-id="39c5c-194">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek `Main()` kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="39c5c-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="39c5c-195">Metoda `BuildAndTrainModel()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="39c5c-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="39c5c-196">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="39c5c-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="39c5c-197">Trénuje model.</span><span class="sxs-lookup"><span data-stu-id="39c5c-197">Trains the model.</span></span>
    - <span data-ttu-id="39c5c-198">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="39c5c-199">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="39c5c-199">Returns the model.</span></span>

2. <span data-ttu-id="39c5c-200">Vytvořte `BuildAndTrainModel()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="39c5c-201">Extrahování a transformace dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-201">Extract and transform the data</span></span>

1. <span data-ttu-id="39c5c-202">Volání `FeaturizeText` jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="39c5c-203">Metoda `FeaturizeText()` v předchozím kódu převede textový`SentimentText`sloupec ( ) `Features` na sloupec číselného typu klíče, který používá algoritmus strojového učení, a přidá jej jako nový sloupec datové sady:</span><span class="sxs-lookup"><span data-stu-id="39c5c-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="39c5c-204">SentimentText</span><span class="sxs-lookup"><span data-stu-id="39c5c-204">SentimentText</span></span>                         |<span data-ttu-id="39c5c-205">Mínění</span><span class="sxs-lookup"><span data-stu-id="39c5c-205">Sentiment</span></span> |<span data-ttu-id="39c5c-206">Funkce</span><span class="sxs-lookup"><span data-stu-id="39c5c-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="39c5c-207">Servírka byla trochu pomalá ve službě.</span><span class="sxs-lookup"><span data-stu-id="39c5c-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="39c5c-208">0</span><span class="sxs-lookup"><span data-stu-id="39c5c-208">0</span></span>     |<span data-ttu-id="39c5c-209">[0.76, 0.65, 0.44, ...]</span><span class="sxs-lookup"><span data-stu-id="39c5c-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="39c5c-210">Kůrka není dobrá.</span><span class="sxs-lookup"><span data-stu-id="39c5c-210">Crust is not good.</span></span>                    |    <span data-ttu-id="39c5c-211">0</span><span class="sxs-lookup"><span data-stu-id="39c5c-211">0</span></span>     |<span data-ttu-id="39c5c-212">[0.98, 0.43, 0.54, ...]</span><span class="sxs-lookup"><span data-stu-id="39c5c-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="39c5c-213">Wow... Miloval toto místo.</span><span class="sxs-lookup"><span data-stu-id="39c5c-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="39c5c-214">1</span><span class="sxs-lookup"><span data-stu-id="39c5c-214">1</span></span>     |<span data-ttu-id="39c5c-215">[0.35, 0.73, 0.46, ...]</span><span class="sxs-lookup"><span data-stu-id="39c5c-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="39c5c-216">Služba byla velmi rychlá.</span><span class="sxs-lookup"><span data-stu-id="39c5c-216">Service was very prompt.</span></span>              |    <span data-ttu-id="39c5c-217">1</span><span class="sxs-lookup"><span data-stu-id="39c5c-217">1</span></span>     |<span data-ttu-id="39c5c-218">[0.39, 0, 0.75, ...]</span><span class="sxs-lookup"><span data-stu-id="39c5c-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="39c5c-219">Přidání algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="39c5c-219">Add a learning algorithm</span></span>

<span data-ttu-id="39c5c-220">Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="39c5c-221">Aplikace kategorizuje komentáře webu jako kladné nebo záporné, proto použijte úlohu binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="39c5c-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="39c5c-222">Přidejte úlohu strojového učení k definicím transformace dat přidáním `BuildAndTrainModel()`následujícího jako následující řádek kódu v aplikaci :</span><span class="sxs-lookup"><span data-stu-id="39c5c-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="39c5c-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš algoritmus školení klasifikace.</span><span class="sxs-lookup"><span data-stu-id="39c5c-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="39c5c-224">To je připojen `estimator` k a přijímá featurized `SentimentText` ( `Label` `Features`) a vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="39c5c-225">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-225">Train the model</span></span>

<span data-ttu-id="39c5c-226">Připevněte model `splitTrainSet` k datům a vraťte trénovaný model `BuildAndTrainModel()` přidáním následujícího jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="39c5c-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="39c5c-227">[Metoda Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trénuje váš model transformací datové sady a použitím školení.</span><span class="sxs-lookup"><span data-stu-id="39c5c-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="39c5c-228">Vrátit model vyškolený k použití pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="39c5c-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="39c5c-229">Vraťte model na konci `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="39c5c-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="39c5c-230">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-230">Evaluate the model</span></span>

<span data-ttu-id="39c5c-231">Po tréninek modelu použijte testovací data ověřit výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="39c5c-232">Vytvořte `Evaluate()` metodu, `BuildAndTrainModel()`těsně po , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="39c5c-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="39c5c-233">Metoda `Evaluate()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="39c5c-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="39c5c-234">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="39c5c-235">Vytvoří hodnotitel binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="39c5c-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="39c5c-236">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="39c5c-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="39c5c-237">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="39c5c-237">Displays the metrics.</span></span>

2. <span data-ttu-id="39c5c-238">Přidejte volání nové metody `Main()` z metody, `BuildAndTrainModel()` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="39c5c-239">Transformace `splitTestSet` dat přidáním následujícího `Evaluate()`kódu do aplikace :</span><span class="sxs-lookup"><span data-stu-id="39c5c-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="39c5c-240">Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda, aby předpovědi pro více zapředpokladu vstupní řádky testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="39c5c-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="39c5c-241">Vyhodnoťte model přidáním následujícího `Evaluate()` jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="39c5c-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="39c5c-242">Jakmile máte předpověď set`predictions`( ), [Assess()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda vyhodnotí model, který porovná `Labels` předpovídané hodnoty s aktuální v testovací datové sady a vrátí [KalibrdBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objekt o tom, jak model funguje.</span><span class="sxs-lookup"><span data-stu-id="39c5c-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="39c5c-243">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="39c5c-244">K zobrazení metrik použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="39c5c-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="39c5c-245">Metrika `Accuracy` získá přesnost modelu, což je podíl správné předpovědi v testovací sadě.</span><span class="sxs-lookup"><span data-stu-id="39c5c-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="39c5c-246">Metrika `AreaUnderRocCurve` označuje, jak jistý model je správně klasifikovat kladné a záporné třídy.</span><span class="sxs-lookup"><span data-stu-id="39c5c-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="39c5c-247">Chcete, `AreaUnderRocCurve` aby byl co nejblíže k jednomu, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="39c5c-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="39c5c-248">Metrika `F1Score` získá skóre F1 modelu, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="39c5c-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="39c5c-249">Chcete, `F1Score` aby byl co nejblíže k jednomu, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="39c5c-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="39c5c-250">Předpovědět výsledek testovacích dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="39c5c-251">Vytvořte `UseModelWithSingleItem()` metodu, `Evaluate()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="39c5c-252">Metoda `UseModelWithSingleItem()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="39c5c-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="39c5c-253">Vytvoří jeden komentář testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="39c5c-254">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="39c5c-255">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="39c5c-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="39c5c-256">Zobrazí předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="39c5c-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="39c5c-257">Přidejte volání nové metody `Main()` z metody, `Evaluate()` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="39c5c-258">Přidejte následující kód, který chcete `UseModelWithSingleItem()` vytvořit jako první řádek metody:</span><span class="sxs-lookup"><span data-stu-id="39c5c-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="39c5c-259">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="39c5c-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="39c5c-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="39c5c-261">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="39c5c-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="39c5c-262">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="39c5c-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="39c5c-263">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="39c5c-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="39c5c-264">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="39c5c-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="39c5c-265">Přidejte komentář k testování predikce `UseModelWithSingleItem()` trénovaného modelu `SentimentData`v metodě vytvořením instance :</span><span class="sxs-lookup"><span data-stu-id="39c5c-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="39c5c-266">Předat data testovacíkomentář [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do následující ho přidáním následující jako `UseModelWithSingleItem()` další řádky kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="39c5c-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="39c5c-267">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jeden řádek dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="39c5c-268">Zobrazení `SentimentText` a odpovídající předpověď mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="39c5c-269">Použití modelu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="39c5c-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="39c5c-270">Nasazení a předvídání dávkových položek</span><span class="sxs-lookup"><span data-stu-id="39c5c-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="39c5c-271">Vytvořte `UseModelWithBatchItems()` metodu, `UseModelWithSingleItem()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="39c5c-272">Metoda `UseModelWithBatchItems()` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="39c5c-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="39c5c-273">Vytvoří data dávkového testu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-273">Creates batch test data.</span></span>
    - <span data-ttu-id="39c5c-274">Předpovídá mínění na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="39c5c-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="39c5c-275">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="39c5c-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="39c5c-276">Zobrazí předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="39c5c-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="39c5c-277">Přidejte volání nové metody `Main` z metody, `UseModelWithSingleItem()` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="39c5c-278">Přidejte některé komentáře k testování předpovědi `UseModelWithBatchItems()` trénovaného modelu v metodě:</span><span class="sxs-lookup"><span data-stu-id="39c5c-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="39c5c-279">Předpovídat mínění komentářů</span><span class="sxs-lookup"><span data-stu-id="39c5c-279">Predict comment sentiment</span></span>

<span data-ttu-id="39c5c-280">Model slouží k předvídání mínění dat komentáře pomocí metody [Transform():](xref:Microsoft.ML.ITransformer.Transform%2A)</span><span class="sxs-lookup"><span data-stu-id="39c5c-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="39c5c-281">Zkombinujte a zobrazte předpovědi</span><span class="sxs-lookup"><span data-stu-id="39c5c-281">Combine and display the predictions</span></span>

<span data-ttu-id="39c5c-282">Vytvořte záhlaví pro předpovědi pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="39c5c-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="39c5c-283">Protože `SentimentPrediction` je zděděna z `SentimentData`, `Transform()` metoda naplněná `SentimentText` předpovídanými poli.</span><span class="sxs-lookup"><span data-stu-id="39c5c-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="39c5c-284">Při procesu procesu ML.NET každá komponenta přidává sloupce, což usnadňuje zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="39c5c-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="39c5c-285">Výsledky</span><span class="sxs-lookup"><span data-stu-id="39c5c-285">Results</span></span>

<span data-ttu-id="39c5c-286">Vaše výsledky by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-286">Your results should be similar to the following.</span></span> <span data-ttu-id="39c5c-287">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="39c5c-287">During processing, messages are displayed.</span></span> <span data-ttu-id="39c5c-288">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="39c5c-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="39c5c-289">Ty byly odstraněny z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="39c5c-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="39c5c-290">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="39c5c-290">Congratulations!</span></span> <span data-ttu-id="39c5c-291">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předvídání mínění zpráv.</span><span class="sxs-lookup"><span data-stu-id="39c5c-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="39c5c-292">Vytváření úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="39c5c-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="39c5c-293">Tento model má počáteční nižší kvalitu jako kurz používá malé datové sady poskytovat rychlé školení modelu.</span><span class="sxs-lookup"><span data-stu-id="39c5c-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="39c5c-294">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit vylepšit tím, že poskytuje větší trénovací datové sady nebo výběrem různých trénovacích algoritmů s různými hyperparametry pro každý [algoritmus.](../resources/glossary.md#hyperparameter)</span><span class="sxs-lookup"><span data-stu-id="39c5c-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="39c5c-295">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)</span><span class="sxs-lookup"><span data-stu-id="39c5c-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="39c5c-296">Další kroky</span><span class="sxs-lookup"><span data-stu-id="39c5c-296">Next steps</span></span>

<span data-ttu-id="39c5c-297">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="39c5c-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="39c5c-298">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="39c5c-298">Create a console application</span></span>
> - <span data-ttu-id="39c5c-299">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-299">Prepare data</span></span>
> - <span data-ttu-id="39c5c-300">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="39c5c-300">Load the data</span></span>
> - <span data-ttu-id="39c5c-301">Sestavení a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-301">Build and train the model</span></span>
> - <span data-ttu-id="39c5c-302">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="39c5c-302">Evaluate the model</span></span>
> - <span data-ttu-id="39c5c-303">Pomocí modelu proveďte předpověď</span><span class="sxs-lookup"><span data-stu-id="39c5c-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="39c5c-304">Zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="39c5c-304">See the results</span></span>

<span data-ttu-id="39c5c-305">Přejdete k dalšímu kurzu, abyste se dozvěděli více</span><span class="sxs-lookup"><span data-stu-id="39c5c-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="39c5c-306">Klasifikace problémů</span><span class="sxs-lookup"><span data-stu-id="39c5c-306">Issue Classification</span></span>](github-issue-classification.md)
