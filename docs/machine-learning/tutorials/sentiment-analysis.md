---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 45e94e325fc4fbfaf1e71f7839d5083e44d5863e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973693"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="5fdea-103">Kurz: Použití ML.NET ve scénáři binární klasifikace analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="5fdea-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="5fdea-104">Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru mínění pochopit mínění příchozí komentáře webu přijmout vhodná opatření prostřednictvím aplikace konzoly .NET Core using C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5fdea-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to understand sentiment of incoming website comments to take the appropriate action via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="5fdea-105">Ve světě služby machine learning tohoto typu predikcí se nazývá binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="5fdea-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="5fdea-106">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="5fdea-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="5fdea-107">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5fdea-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="5fdea-108">Tento kurz a související ukázkové právě používáte **preview verze 1.0.0 ML.NET**.</span><span class="sxs-lookup"><span data-stu-id="5fdea-108">This tutorial and related sample are currently using **ML.NET version 1.0.0 preview**.</span></span> <span data-ttu-id="5fdea-109">Další informace najdete v tématu poznámky k verzi v [dotnet/machinelearning úložiště GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="5fdea-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="5fdea-110">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="5fdea-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5fdea-111">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="5fdea-111">Understand the problem</span></span>
> * <span data-ttu-id="5fdea-112">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="5fdea-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="5fdea-113">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-113">Prepare your data</span></span>
> * <span data-ttu-id="5fdea-114">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-114">Transform the data</span></span>
> * <span data-ttu-id="5fdea-115">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-115">Train the model</span></span>
> * <span data-ttu-id="5fdea-116">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-116">Evaluate the model</span></span>
> * <span data-ttu-id="5fdea-117">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-117">Predict with the trained model</span></span>
> * <span data-ttu-id="5fdea-118">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="5fdea-118">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="5fdea-119">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="5fdea-119">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fdea-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fdea-120">Prerequisites</span></span>

* <span data-ttu-id="5fdea-121">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="5fdea-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="5fdea-122">Soubor zip UCI subjektivního hodnocení s popiskem věty datové sady</span><span class="sxs-lookup"><span data-stu-id="5fdea-122">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="create-a-console-application"></a><span data-ttu-id="5fdea-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="5fdea-123">Create a console application</span></span>

1. <span data-ttu-id="5fdea-124">Vytvoření **konzolovou aplikaci .NET Core** nazývá "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="5fdea-124">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="5fdea-125">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady.</span><span class="sxs-lookup"><span data-stu-id="5fdea-125">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="5fdea-126">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="5fdea-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="5fdea-127">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5fdea-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="5fdea-128">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="5fdea-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="5fdea-129">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="5fdea-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="5fdea-130">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-130">Prepare your data</span></span>

1. <span data-ttu-id="5fdea-131">Stáhněte si [soubor zip The UCI subjektivního hodnocení s popiskem věty datové sady (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="5fdea-131">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="5fdea-132">Kopírovat `yelp_labelled.txt` soubor do *Data* adresáře, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="5fdea-132">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5fdea-133">Tento kurz používá datové sady jsou z "From skupina na jednotlivé popisky pomocí podrobné funkce", Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="5fdea-133">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="5fdea-134">al,.</span><span class="sxs-lookup"><span data-stu-id="5fdea-134">al,.</span></span> <span data-ttu-id="5fdea-135">Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="5fdea-135">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="5fdea-136">UCI strojového učení úložiště [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="5fdea-136">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="5fdea-137">Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.</span><span class="sxs-lookup"><span data-stu-id="5fdea-137">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="5fdea-138">V Průzkumníku řešení klikněte pravým tlačítkem myši `yelp_labeled.txt` a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5fdea-138">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="5fdea-139">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="5fdea-139">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="5fdea-140">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="5fdea-140">Create classes and define paths</span></span>

<span data-ttu-id="5fdea-141">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="5fdea-141">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="5fdea-142">Je potřeba vytvořit dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-142">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="5fdea-143">`_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-143">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="5fdea-144">`_modelPath` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-144">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="5fdea-145">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="5fdea-145">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="5fdea-146">Je potřeba vytvořit některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="5fdea-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="5fdea-147">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="5fdea-148">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="5fdea-148">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="5fdea-149">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="5fdea-149">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="5fdea-150">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="5fdea-150">Then, select the **Add** button.</span></span>

    <span data-ttu-id="5fdea-151">*SentimentData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-151">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="5fdea-152">Přidejte následující `using` příkaz do horní části *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="5fdea-152">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="5fdea-153">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="5fdea-153">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="5fdea-154">Třída vstupní datová sada `SentimentData`, má `string` pro komentář (`SentimentText`) a `bool` (`Sentiment`), který má hodnotu mínění buď pozitivní (1) nebo záporná (0).</span><span class="sxs-lookup"><span data-stu-id="5fdea-154">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive (1) or negative (0).</span></span> <span data-ttu-id="5fdea-155">Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy připojené k nim, který popisuje soubor pořadí dat u každého pole.</span><span class="sxs-lookup"><span data-stu-id="5fdea-155">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="5fdea-156">Kromě toho `Sentiment` má vlastnost [Názevsloupce](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atribut nastavit jako `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="5fdea-156">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="5fdea-157">Následující příklad souboru nemá řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5fdea-157">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="5fdea-158">SentimentText</span><span class="sxs-lookup"><span data-stu-id="5fdea-158">SentimentText</span></span>                         |<span data-ttu-id="5fdea-159">Mínění (popisek)</span><span class="sxs-lookup"><span data-stu-id="5fdea-159">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="5fdea-160">Waitress pomalý trochu ve službě.</span><span class="sxs-lookup"><span data-stu-id="5fdea-160">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="5fdea-161">0</span><span class="sxs-lookup"><span data-stu-id="5fdea-161">0</span></span>     |
|<span data-ttu-id="5fdea-162">Povrch ovšem není vhodné.</span><span class="sxs-lookup"><span data-stu-id="5fdea-162">Crust is not good.</span></span>                    |    <span data-ttu-id="5fdea-163">0</span><span class="sxs-lookup"><span data-stu-id="5fdea-163">0</span></span>     |
|<span data-ttu-id="5fdea-164">WOW... Miluju toto místo.</span><span class="sxs-lookup"><span data-stu-id="5fdea-164">Wow... Loved this place.</span></span>              |    <span data-ttu-id="5fdea-165">1</span><span class="sxs-lookup"><span data-stu-id="5fdea-165">1</span></span>     |
|<span data-ttu-id="5fdea-166">Služba se velmi výzvy.</span><span class="sxs-lookup"><span data-stu-id="5fdea-166">Service was very prompt.</span></span>              |    <span data-ttu-id="5fdea-167">1</span><span class="sxs-lookup"><span data-stu-id="5fdea-167">1</span></span>     |

<span data-ttu-id="5fdea-168">`SentimentPrediction` je třída předpovědi používá po cvičení modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-168">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="5fdea-169">Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="5fdea-169">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="5fdea-170">`Label` Slouží k vytvoření a trénování modelu a jeho rozdělení na testovací datové použít také k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-170">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="5fdea-171">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="5fdea-171">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="5fdea-172">Pro vyhodnocení se používají trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="5fdea-172">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="5fdea-173">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-173">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="5fdea-174">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="5fdea-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="5fdea-175">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="5fdea-175">Initialize variables in Main</span></span>

<span data-ttu-id="5fdea-176">Nahraďte `Console.WriteLine("Hello World!")` řádku v `Main` metodu, jak deklarovat a inicializovat proměnnou mlContext následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5fdea-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="5fdea-177">Přidejte následující položky jako další řádek kódu `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-177">Add the following as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="5fdea-178">`LoadData()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5fdea-178">The `LoadData()` method executes the following tasks:</span></span>

* <span data-ttu-id="5fdea-179">Načte data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-179">Loads the data.</span></span>
* <span data-ttu-id="5fdea-180">Rozdělí načíst datovou sadu na trénování a testování datových sad.</span><span class="sxs-lookup"><span data-stu-id="5fdea-180">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="5fdea-181">Vrátí hodnotu rozdělení trénují a testují datové sady.</span><span class="sxs-lookup"><span data-stu-id="5fdea-181">Returns the split train and test datasets.</span></span>

<span data-ttu-id="5fdea-182">Vytvořte `LoadData()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
public static TrainTestData LoadData(MLContext mlContext)
{

}
```

## <a name="load-the-data"></a><span data-ttu-id="5fdea-183">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-183">Load the data</span></span>

<span data-ttu-id="5fdea-184">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="5fdea-184">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="5fdea-185">`IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="5fdea-185">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="5fdea-186">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-186">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>
<span data-ttu-id="5fdea-187">Přidejte následující kód jako první řádek `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-187">Add the following code as the first line of the `LoadData()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="5fdea-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru.</span><span class="sxs-lookup"><span data-stu-id="5fdea-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="5fdea-189">Přijímá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="5fdea-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="5fdea-190">Rozdělení datové sady pro trénování a testování modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="5fdea-191">Dále je třeba trénovací datové sady pro trénování modelu a datové sady testů k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-191">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span>

<span data-ttu-id="5fdea-192">Načtená data rozdělením potřebné datové sady, přidejte následující kód jako další řádek `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="5fdea-193">Předchozí kód používá [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metodu rozdělit načíst datovou sadu na trénování a testování datových sad a vrátit je do [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) třídy.</span><span class="sxs-lookup"><span data-stu-id="5fdea-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="5fdea-194">Zadejte procento dat pomocí nastavení testu `testFraction`parametru.</span><span class="sxs-lookup"><span data-stu-id="5fdea-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="5fdea-195">Výchozí hodnota je 10 %, ale je použít 20 %, v tomto případě k vyhodnocení další data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-195">The default is 10% but you use 20% in this case to evaluate more data.</span></span>  

<span data-ttu-id="5fdea-196">Vrátit `splitDataView` na konci `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="5fdea-197">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-197">Build and train the model</span></span>

<span data-ttu-id="5fdea-198">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="5fdea-199">`BuildAndTrainModel()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5fdea-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="5fdea-200">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-200">Extracts and transforms the data.</span></span>
* <span data-ttu-id="5fdea-201">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-201">Trains the model.</span></span>
* <span data-ttu-id="5fdea-202">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-202">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="5fdea-203">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-203">Returns the model.</span></span>

<span data-ttu-id="5fdea-204">Vytvořte `BuildAndTrainModel()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="5fdea-205">Extrahovat a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-205">Extract and transform the data</span></span>

<span data-ttu-id="5fdea-206">Volání `FeaturizeText` jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-206">Call `FeaturizeText` as the next line of code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

<span data-ttu-id="5fdea-207">`FeaturizeText()` Metoda v předchozím kódu převede textový sloupec (`SentimentText`) na číselný typ klíče `Features` sloupec používá algoritmu strojového učení a přidá ho jakou novou datovou sadu sloupce:</span><span class="sxs-lookup"><span data-stu-id="5fdea-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

|<span data-ttu-id="5fdea-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="5fdea-208">SentimentText</span></span>                         |<span data-ttu-id="5fdea-209">Mínění</span><span class="sxs-lookup"><span data-stu-id="5fdea-209">Sentiment</span></span> |<span data-ttu-id="5fdea-210">Funkce</span><span class="sxs-lookup"><span data-stu-id="5fdea-210">Features</span></span>              |
|--------------------------------------|----------|----------------------|
|<span data-ttu-id="5fdea-211">Waitress pomalý trochu ve službě.</span><span class="sxs-lookup"><span data-stu-id="5fdea-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="5fdea-212">0</span><span class="sxs-lookup"><span data-stu-id="5fdea-212">0</span></span>     |<span data-ttu-id="5fdea-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="5fdea-213">[0.76, 0.65, 0.44, …]</span></span> |
|<span data-ttu-id="5fdea-214">Povrch ovšem není vhodné.</span><span class="sxs-lookup"><span data-stu-id="5fdea-214">Crust is not good.</span></span>                    |    <span data-ttu-id="5fdea-215">0</span><span class="sxs-lookup"><span data-stu-id="5fdea-215">0</span></span>     |<span data-ttu-id="5fdea-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="5fdea-216">[0.98, 0.43, 0.54, …]</span></span> |
|<span data-ttu-id="5fdea-217">WOW... Miluju toto místo.</span><span class="sxs-lookup"><span data-stu-id="5fdea-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="5fdea-218">1</span><span class="sxs-lookup"><span data-stu-id="5fdea-218">1</span></span>     |<span data-ttu-id="5fdea-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="5fdea-219">[0.35, 0.73, 0.46, …]</span></span> |
|<span data-ttu-id="5fdea-220">Služba se velmi výzvy.</span><span class="sxs-lookup"><span data-stu-id="5fdea-220">Service was very prompt.</span></span>              |    <span data-ttu-id="5fdea-221">1</span><span class="sxs-lookup"><span data-stu-id="5fdea-221">1</span></span>     |<span data-ttu-id="5fdea-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="5fdea-222">[0.39, 0, 0.75, …]</span></span>    |

## <a name="add-a-learning-algorithm"></a><span data-ttu-id="5fdea-223">Přidat algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="5fdea-223">Add a learning algorithm</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="5fdea-224">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="5fdea-224">About the classification task</span></span>

<span data-ttu-id="5fdea-225">"To je A nebo B?"</span><span class="sxs-lookup"><span data-stu-id="5fdea-225">"Is it A or B?"</span></span>

![algoritmu strojového učení klasifikace](./media/sentiment-analysis/classification.png)

<span data-ttu-id="5fdea-227">Klasifikace je algoritmus strojového učení, který používá data **určit** kategorie, typ nebo třída položky nebo řádek dat a je často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="5fdea-227">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="5fdea-228">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="5fdea-228">Binary: either A or B.</span></span>
* <span data-ttu-id="5fdea-229">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-229">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="5fdea-230">Protože webu komentáře zapotřebí klasifikováno jako kladné nebo záporné, můžete pomocí binární klasifikace úlohy.</span><span class="sxs-lookup"><span data-stu-id="5fdea-230">Because the website comments need to be classified as either positive or negative, you use the Binary Classification task.</span></span>

<span data-ttu-id="5fdea-231">Přidat úlohy strojového učení do definice transformace dat přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="5fdea-231">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="5fdea-232">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je vaše klasifikace cvičení algoritmu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-232">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="5fdea-233">To se připojí `estimator` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="5fdea-233">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="5fdea-234">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-234">Train the model</span></span>

<span data-ttu-id="5fdea-235">Přizpůsobit modelu, který má `splitTrainSet` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-235">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="5fdea-236">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="5fdea-236">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="5fdea-237">Vrátí že model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="5fdea-237">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="5fdea-238">Model na konci vrátit `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-238">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="5fdea-239">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-239">Evaluate the model</span></span>

<span data-ttu-id="5fdea-240">Po model se trénuje, slouží k vyhodnocení výkonu modelu kontroly kvality a ověřování testovací data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-240">After your model is trained, use your test data to evaluate how your model is performing for quality assurance and validation.</span></span> <span data-ttu-id="5fdea-241">Vytvořte `Evaluate()` metoda, hned za `BuildAndTrainModel()`, následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5fdea-241">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="5fdea-242">`Evaluate()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5fdea-242">The `Evaluate()` method executes the following tasks:</span></span>

* <span data-ttu-id="5fdea-243">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="5fdea-243">Loads the test dataset.</span></span>
* <span data-ttu-id="5fdea-244">Chyba při vyhodnocování BinaryClassification vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5fdea-244">Creates the BinaryClassification evaluator.</span></span>
* <span data-ttu-id="5fdea-245">Vyhodnotí modelu a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="5fdea-245">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="5fdea-246">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="5fdea-246">Displays the metrics.</span></span>

<span data-ttu-id="5fdea-247">Přidejte volání do nové metody z `Main()` metody, v rámci `BuildAndTrainModel()` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-247">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="5fdea-248">Transformace `splitTestSet` data přidáním následujícího kódu do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="5fdea-248">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="5fdea-249">Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda k následné predikci pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="5fdea-249">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="5fdea-250">Přidáním následujícího kódu jako další řádek kódu ve vyhodnocení modelu `Evaluate()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-250">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="5fdea-251">Jakmile budete mít do predikce. Nastavte (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` datovou sadu testů a vrátí [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objektu, na jaký je výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-251">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="5fdea-252">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-252">Displaying the metrics for model validation</span></span>

<span data-ttu-id="5fdea-253">Použijte následující kód k zobrazení metriky:</span><span class="sxs-lookup"><span data-stu-id="5fdea-253">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="5fdea-254">`Accuracy` Metrika získá přesnost modelu, který je poměr správné predikce v testovací sadě.</span><span class="sxs-lookup"><span data-stu-id="5fdea-254">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="5fdea-255">`AreaUnderRocCurve` Metrika vyjadřuje důvěru modelu je správně klasifikace třídy kladné a záporné.</span><span class="sxs-lookup"><span data-stu-id="5fdea-255">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="5fdea-256">Chcete, aby `AreaUnderRocCurve` bude blízko jeden nejvíce.</span><span class="sxs-lookup"><span data-stu-id="5fdea-256">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="5fdea-257">`F1Score` Metrika získá modelu F1 skóre, které je míra rovnováhu mezi [přesnost](../resources/glossary.md#precision) a [spojené s vracením](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="5fdea-257">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="5fdea-258">Chcete, aby `F1Score` bude blízko jeden nejvíce.</span><span class="sxs-lookup"><span data-stu-id="5fdea-258">You want the `F1Score` to be as close to one as possible.</span></span>

## <a name="predict-the-test-data-outcome"></a><span data-ttu-id="5fdea-259">Předpověď data výsledek testu</span><span class="sxs-lookup"><span data-stu-id="5fdea-259">Predict the test data outcome</span></span>

<span data-ttu-id="5fdea-260">Vytvořte `UseModelWithSingleItem()` metoda, hned za `Evaluate()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-260">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="5fdea-261">`UseModelWithSingleItem()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5fdea-261">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

* <span data-ttu-id="5fdea-262">Vytvoří jeden komentář testovací data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-262">Creates a single comment of test data.</span></span>
* <span data-ttu-id="5fdea-263">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="5fdea-264">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="5fdea-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="5fdea-265">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="5fdea-265">Displays the predicted results.</span></span>

<span data-ttu-id="5fdea-266">Přidejte volání do nové metody z `Main()` metody, v rámci `Evaluate()` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-266">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="5fdea-267">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je vhodné rozhraní API, což vám umožní předat a pak proveďte predikcí na jednu instanci data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-267">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="5fdea-268">Přidejte následující kód k vytvoření jako první řádek `Predict()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-268">add the following code to create as the first line in the `Predict()` Method:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="5fdea-269">Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict()` metodu tak, že vytvoříte instanci `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="5fdea-269">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

<span data-ttu-id="5fdea-270">Předání dat komentář test `Prediction Engine` přidáním následujícího kódu jako další řádky kódu ve `UseModelWithSingleItem()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-270">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

<span data-ttu-id="5fdea-271">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) predikcí na jednom řádku dat díky funkce.</span><span class="sxs-lookup"><span data-stu-id="5fdea-271">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

### <a name="use-the-model-prediction"></a><span data-ttu-id="5fdea-272">Použití modelu: předpověď</span><span class="sxs-lookup"><span data-stu-id="5fdea-272">Use the model: prediction</span></span>

<span data-ttu-id="5fdea-273">Zobrazení `SentimentText` a odpovídající předpovědí mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-273">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="5fdea-274">Nasazení a předvídání položky služby batch</span><span class="sxs-lookup"><span data-stu-id="5fdea-274">Deploy and predict batch items</span></span>

<span data-ttu-id="5fdea-275">Vytvořte `UseModelWithBatchItems()` metoda, hned za `UseModelWithSingleItem()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-275">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

```csharp
public static void UseModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="5fdea-276">`UseModelWithBatchItems()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5fdea-276">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

* <span data-ttu-id="5fdea-277">Vytvoří služby batch testovací data.</span><span class="sxs-lookup"><span data-stu-id="5fdea-277">Creates batch test data.</span></span>
* <span data-ttu-id="5fdea-278">Předpovídá subjektivního hodnocení na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="5fdea-278">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="5fdea-279">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="5fdea-279">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="5fdea-280">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="5fdea-280">Displays the predicted results.</span></span>

<span data-ttu-id="5fdea-281">Přidejte volání do nové metody z `Main` metody, v rámci `UseModelWithSingleItem()` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-281">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

<span data-ttu-id="5fdea-282">Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `UseModelWithBatchItems()` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-282">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="use-the-model-for-prediction"></a><span data-ttu-id="5fdea-283">Použití modelu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="5fdea-283">Use the model for prediction</span></span>

<span data-ttu-id="5fdea-284">Použít model k predikci komentář data subjektivního hodnocení s využitím [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-284">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="5fdea-285">Spojit a zobrazit předpovědi</span><span class="sxs-lookup"><span data-stu-id="5fdea-285">Combine and display the predictions</span></span>

<span data-ttu-id="5fdea-286">Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5fdea-286">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="5fdea-287">Před zobrazením předpokládané výsledky, kombinovat původním komentářem s jeho pomocí předpokládané subjektivního hodnocení [Zip()](xref:System.Linq.Enumerable.Zip%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="5fdea-287">Before displaying the predicted results, combine the original comment with its predicted sentiment using the [Zip()](xref:System.Linq.Enumerable.Zip%2A) method:</span></span>

[!code-csharp[BuildTuples](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="5fdea-288">Teď, když `SentimentText` a `Sentiment` jsou kombinované ve třídě, zobrazit výsledky:</span><span class="sxs-lookup"><span data-stu-id="5fdea-288">Now that `SentimentText` and `Sentiment` are combined in a class, display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="5fdea-289">Výsledky</span><span class="sxs-lookup"><span data-stu-id="5fdea-289">Results</span></span>

<span data-ttu-id="5fdea-290">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="5fdea-290">Your results should be similar to the following.</span></span> <span data-ttu-id="5fdea-291">Během zpracování zprávy se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="5fdea-291">During processing, messages are displayed.</span></span> <span data-ttu-id="5fdea-292">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="5fdea-292">You may see warnings, or processing messages.</span></span> <span data-ttu-id="5fdea-293">Ty se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="5fdea-293">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="5fdea-294">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="5fdea-294">Congratulations!</span></span> <span data-ttu-id="5fdea-295">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění.</span><span class="sxs-lookup"><span data-stu-id="5fdea-295">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="5fdea-296">Vytváření modelů po úspěšné je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="5fdea-296">Building successful models is an iterative process.</span></span> <span data-ttu-id="5fdea-297">Tento model má nižší počáteční kvalita jako kurz používá malé datové sady poskytují rychlý model školení.</span><span class="sxs-lookup"><span data-stu-id="5fdea-297">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="5fdea-298">Pokud si nejste spokojeni s kvalitou modelu, můžete zkusit ho vylepšit tím, že poskytuje větší cvičných datových sad nebo výběrem jiné trénování algoritmů s různými [hyperparametry](../resources/glossary.md##hyperparameter) pro jednotlivé algoritmy.</span><span class="sxs-lookup"><span data-stu-id="5fdea-298">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="5fdea-299">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.</span><span class="sxs-lookup"><span data-stu-id="5fdea-299">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5fdea-300">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5fdea-300">Next steps</span></span>

<span data-ttu-id="5fdea-301">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="5fdea-301">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5fdea-302">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="5fdea-302">Understand the problem</span></span>
> * <span data-ttu-id="5fdea-303">Vyberte algoritmus učení příslušný počítač</span><span class="sxs-lookup"><span data-stu-id="5fdea-303">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="5fdea-304">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-304">Prepare your data</span></span>
> * <span data-ttu-id="5fdea-305">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="5fdea-305">Transform the data</span></span>
> * <span data-ttu-id="5fdea-306">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-306">Train the model</span></span>
> * <span data-ttu-id="5fdea-307">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-307">Evaluate the model</span></span>
> * <span data-ttu-id="5fdea-308">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="5fdea-308">Predict with the trained model</span></span>
> * <span data-ttu-id="5fdea-309">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="5fdea-309">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="5fdea-310">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="5fdea-310">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5fdea-311">Klasifikace problému</span><span class="sxs-lookup"><span data-stu-id="5fdea-311">Issue Classification</span></span>](github-issue-classification.md)
