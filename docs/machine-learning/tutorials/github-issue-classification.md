---
title: 'Kurz: zařazení do kategorií – problémy s podporou – klasifikace s více třídami'
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace s více třídami ke klasifikaci problémů GitHubu, aby je bylo možné přiřadit k dané oblasti.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 48f5f213802b09168cbc21da1b22e84ec53756fe
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282070"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="fd962-103">Kurz: kategorizace problémů podpory pomocí klasifikace s více třídami s ML.NET</span><span class="sxs-lookup"><span data-stu-id="fd962-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="fd962-104">Tento vzorový kurz ilustruje použití ML.NET k vytvoření klasifikátoru problémů GitHubu pro výuku modelu, který klasifikuje a odhadne popisek oblasti pro problém na GitHubu prostřednictvím konzolové aplikace .NET Core využívající C# v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd962-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="fd962-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="fd962-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fd962-106">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="fd962-106">Prepare your data</span></span>
> * <span data-ttu-id="fd962-107">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="fd962-107">Transform the data</span></span>
> * <span data-ttu-id="fd962-108">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-108">Train the model</span></span>
> * <span data-ttu-id="fd962-109">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-109">Evaluate the model</span></span>
> * <span data-ttu-id="fd962-110">Předpověď s vycvičeným modelem</span><span class="sxs-lookup"><span data-stu-id="fd962-110">Predict with the trained model</span></span>
> * <span data-ttu-id="fd962-111">Nasazení a předpověď pomocí načteného modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="fd962-112">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .</span><span class="sxs-lookup"><span data-stu-id="fd962-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd962-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd962-113">Prerequisites</span></span>

* <span data-ttu-id="fd962-114">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="fd962-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="fd962-115">[Soubor s oddělovači (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv)se zastavuje na kartě GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fd962-115">The [GitHub issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="fd962-116">[Soubor s oddělovači (issues_test. TSV) problému GitHubu](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="fd962-116">The [GitHub issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="fd962-117">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="fd962-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="fd962-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fd962-118">Create a project</span></span>

1. <span data-ttu-id="fd962-119">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fd962-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="fd962-120">Z řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt** .</span><span class="sxs-lookup"><span data-stu-id="fd962-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="fd962-121">V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="fd962-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="fd962-122">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="fd962-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="fd962-123">Do textového pole **název** zadejte "GitHubIssueClassification" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="fd962-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="fd962-124">Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady:</span><span class="sxs-lookup"><span data-stu-id="fd962-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="fd962-125">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="fd962-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="fd962-126">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="fd962-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="fd962-127">Vytvořte v projektu adresář s názvem *Models* a uložte svůj model:</span><span class="sxs-lookup"><span data-stu-id="fd962-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="fd962-128">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="fd962-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="fd962-129">Zadejte "modely" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="fd962-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="fd962-130">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="fd962-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="fd962-131">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fd962-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="fd962-132">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml** a vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="fd962-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="fd962-133">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="fd962-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="fd962-134">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="fd962-134">Prepare your data</span></span>

1. <span data-ttu-id="fd962-135">Stáhněte sady dat [issues_train. TSV](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test. TSV](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) a uložte je do složky *data* , která byla dříve vytvořena.</span><span class="sxs-lookup"><span data-stu-id="fd962-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="fd962-136">První datová sada Vlaks model strojového učení a druhá se dá použít k vyhodnocení toho, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="fd962-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="fd962-137">V Průzkumník řešení klikněte pravým tlačítkem na každý ze \* souborů. TSV a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fd962-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="fd962-138">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="fd962-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="fd962-139">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="fd962-139">Create classes and define paths</span></span>

<span data-ttu-id="fd962-140">`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="fd962-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="fd962-141">Vytvořte tři globální pole pro uchování cest ke nedávno staženým souborům a globální proměnné pro `MLContext` , `DataView` a `PredictionEngine` :</span><span class="sxs-lookup"><span data-stu-id="fd962-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="fd962-142">`_trainDataPath`má cestu k datové sadě, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="fd962-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="fd962-143">`_testDataPath`má cestu k datové sadě, která se používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="fd962-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="fd962-144">`_modelPath`má cestu, kde je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="fd962-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="fd962-145">`_mlContext`je rozhraní <xref:Microsoft.ML.MLContext> , které poskytuje kontext zpracování.</span><span class="sxs-lookup"><span data-stu-id="fd962-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="fd962-146">`_trainingDataView`<xref:Microsoft.ML.IDataView>slouží ke zpracování datové sady školení.</span><span class="sxs-lookup"><span data-stu-id="fd962-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="fd962-147">`_predEngine`je <xref:Microsoft.ML.PredictionEngine%602> použit pro jeden předpovědi.</span><span class="sxs-lookup"><span data-stu-id="fd962-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="fd962-148">Přidejte následující kód na řádek přímo nad `Main` metodu pro určení těchto cest a dalších proměnných:</span><span class="sxs-lookup"><span data-stu-id="fd962-148">Add the following code to the line directly above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="fd962-149">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="fd962-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="fd962-150">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="fd962-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="fd962-151">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="fd962-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="fd962-152">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="fd962-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="fd962-153">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="fd962-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="fd962-154">V editoru kódu se otevře soubor *GitHubIssueData.cs* .</span><span class="sxs-lookup"><span data-stu-id="fd962-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="fd962-155">`using`Do horní části *GitHubIssueData.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fd962-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="fd962-156">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction` , do souboru *GitHubIssueData.cs* :</span><span class="sxs-lookup"><span data-stu-id="fd962-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="fd962-157">`label`Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="fd962-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="fd962-158">Identifikované `Features` jsou vstupy, které modelu přiřadíte pro předpověď popisku.</span><span class="sxs-lookup"><span data-stu-id="fd962-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="fd962-159">Pomocí [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v sadě dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="fd962-160">`GitHubIssue`je vstupní datovou třídou a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="fd962-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="fd962-161">první sloupec `ID` (ID problému GitHubu)</span><span class="sxs-lookup"><span data-stu-id="fd962-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="fd962-162">druhý sloupec `Area` (předpověď pro školení)</span><span class="sxs-lookup"><span data-stu-id="fd962-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="fd962-163">třetí sloupec `Title` (název problému GitHubu) je první, který se `feature` používá pro předpověď`Area`</span><span class="sxs-lookup"><span data-stu-id="fd962-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="fd962-164">čtvrtý sloupec `Description` je druhým `feature` použitým pro předpověď`Area`</span><span class="sxs-lookup"><span data-stu-id="fd962-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="fd962-165">`IssuePrediction`je třída použitá pro předpověď po vyškolení modelu.</span><span class="sxs-lookup"><span data-stu-id="fd962-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="fd962-166">Má jeden `string` ( `Area` ) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="fd962-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="fd962-167">`PredictedLabel`Je používán během předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="fd962-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="fd962-168">Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.</span><span class="sxs-lookup"><span data-stu-id="fd962-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="fd962-169">Všechny operace ML.NET začínají ve třídě [MLContext](xref:Microsoft.ML.MLContext) .</span><span class="sxs-lookup"><span data-stu-id="fd962-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="fd962-170">Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="fd962-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fd962-171">Je podobný, koncepčně, na `DBContext` v `Entity Framework` .</span><span class="sxs-lookup"><span data-stu-id="fd962-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="fd962-172">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="fd962-172">Initialize variables in Main</span></span>

<span data-ttu-id="fd962-173">Inicializovat `_mlContext` globální proměnnou s novou instancí `MLContext` s náhodným osivem ( `seed: 0` ) pro opakované nebo deterministické výsledky v rámci více školení.</span><span class="sxs-lookup"><span data-stu-id="fd962-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="fd962-174">Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="fd962-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](./snippets/github-issue-classification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="fd962-175">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="fd962-175">Load the data</span></span>

<span data-ttu-id="fd962-176">ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data.</span><span class="sxs-lookup"><span data-stu-id="fd962-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="fd962-177">`IDataView`může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu).</span><span class="sxs-lookup"><span data-stu-id="fd962-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="fd962-178">Chcete-li inicializovat a načíst `_trainingDataView` globální proměnnou, aby ji bylo možné použít pro kanál, přidejte po inicializaci následující kód `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="fd962-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](./snippets/github-issue-classification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="fd962-179">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="fd962-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="fd962-180">Převezme proměnné cesty k datům a vrátí `IDataView` .</span><span class="sxs-lookup"><span data-stu-id="fd962-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="fd962-181">Přidejte následující jako další řádek kódu v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="fd962-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](./snippets/github-issue-classification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="fd962-182">`ProcessData`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="fd962-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="fd962-183">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="fd962-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="fd962-184">Vrátí kanál zpracování.</span><span class="sxs-lookup"><span data-stu-id="fd962-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="fd962-185">Vytvořte `ProcessData` metodu hned za `Main` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="fd962-186">Extrakce funkcí a transformace dat</span><span class="sxs-lookup"><span data-stu-id="fd962-186">Extract Features and transform the data</span></span>

<span data-ttu-id="fd962-187">Vzhledem k tomu, že chcete předpovědět popisek GitHubu oblasti pro `GitHubIssue` , použijte metodu [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pro transformaci `Area` sloupce do sloupce typu numerický klíč `Label` (formát přijatý algoritmy klasifikace) a přidejte ho jako sloupec nové datové sady:</span><span class="sxs-lookup"><span data-stu-id="fd962-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](./snippets/github-issue-classification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="fd962-188">Dále zavolejte `mlContext.Transforms.Text.FeaturizeText` , které transformuje sloupce textu ( `Title` a `Description` ) na číselné vektory pro každý z nich `TitleFeaturized` a `DescriptionFeaturized` .</span><span class="sxs-lookup"><span data-stu-id="fd962-188">Next, call `mlContext.Transforms.Text.FeaturizeText`, which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="fd962-189">Přidejte featurization pro oba sloupce do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="fd962-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](./snippets/github-issue-classification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="fd962-190">Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí metody [CONCATENATE ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) .</span><span class="sxs-lookup"><span data-stu-id="fd962-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="fd962-191">Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** .</span><span class="sxs-lookup"><span data-stu-id="fd962-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="fd962-192">Přidejte tuto transformaci do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="fd962-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](./snippets/github-issue-classification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="fd962-193">V dalším kroku přidejte objekt, <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> aby se zobrazila mezipaměť, takže když provedete iteraci dat víckrát pomocí mezipaměti, může dorazit k vyššímu výkonu, jako u následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](./snippets/github-issue-classification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="fd962-194">Použijte AppendCacheCheckpoint pro malé nebo střední datové sady k nižšímu času školení.</span><span class="sxs-lookup"><span data-stu-id="fd962-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="fd962-195">Nepoužívejte ho (odebrat. AppendCacheCheckpoint ()) při zpracování velmi rozsáhlých datových sad.</span><span class="sxs-lookup"><span data-stu-id="fd962-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="fd962-196">Vrátí kanál na konci `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="fd962-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](./snippets/github-issue-classification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="fd962-197">Tento krok zpracovává předzpracování/featurization.</span><span class="sxs-lookup"><span data-stu-id="fd962-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="fd962-198">Použití dalších součástí dostupných v ML.NET může mít za následek lepší výsledky v modelu.</span><span class="sxs-lookup"><span data-stu-id="fd962-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="fd962-199">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-199">Build and train the model</span></span>

<span data-ttu-id="fd962-200">Do metody přidejte následující volání `BuildAndTrainModel` metody jako další řádek kódu v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="fd962-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](./snippets/github-issue-classification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="fd962-201">`BuildAndTrainModel`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="fd962-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="fd962-202">Vytvoří třídu školicího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="fd962-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="fd962-203">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="fd962-203">Trains the model.</span></span>
* <span data-ttu-id="fd962-204">Odhadne oblast na základě školicích dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="fd962-205">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="fd962-205">Returns the model.</span></span>

<span data-ttu-id="fd962-206">Vytvořte `BuildAndTrainModel` metodu hned za `Main` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="fd962-207">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="fd962-207">About the classification task</span></span>

<span data-ttu-id="fd962-208">Klasifikace je úloha strojového učení, která používá data k **určení** kategorie, typu nebo třídy položky nebo řádku dat a je často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="fd962-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="fd962-209">Binární: buď A nebo B.</span><span class="sxs-lookup"><span data-stu-id="fd962-209">Binary: either A or B.</span></span>
* <span data-ttu-id="fd962-210">Více tříd: více kategorií, které mohou být předpovězeny pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="fd962-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="fd962-211">Pro tento typ problému použijte algoritmus učení s více třídami, protože předpověď kategorie problému může být jednou z více kategorií (více tříd), nikoli jenom dvou (binární).</span><span class="sxs-lookup"><span data-stu-id="fd962-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="fd962-212">Přidejte algoritmus Machine Learning do definice transformace dat tak, že do prvního řádku kódu přidáte následující `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="fd962-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](./snippets/github-issue-classification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="fd962-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je váš algoritmus školicích kurzů pro klasifikace více tříd.</span><span class="sxs-lookup"><span data-stu-id="fd962-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="fd962-214">Tento údaj je připojen k `pipeline` a přijímá natrénuje `Title` a `Description` ( `Features` ) a `Label` vstupní parametry pro získání informací z historických dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="fd962-215">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-215">Train the model</span></span>

<span data-ttu-id="fd962-216">Přizpůsobte si model `splitTrainSet` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `BuildAndTrainModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="fd962-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](./snippets/github-issue-classification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="fd962-217">`Fit()`Metoda navlakuje váš model transformací datové sady a použitím školení.</span><span class="sxs-lookup"><span data-stu-id="fd962-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="fd962-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="fd962-219">Přidejte toto jako další řádek v `BuildAndTrainModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="fd962-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="fd962-220">Předpověď s vycvičeným modelem</span><span class="sxs-lookup"><span data-stu-id="fd962-220">Predict with the trained model</span></span>

<span data-ttu-id="fd962-221">Přidejte problém GitHubu pro otestování předpovědi vyškolených modelů v `Predict` metodě vytvořením instance `GitHubIssue` :</span><span class="sxs-lookup"><span data-stu-id="fd962-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](./snippets/github-issue-classification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="fd962-222">Použití funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:</span><span class="sxs-lookup"><span data-stu-id="fd962-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](./snippets/github-issue-classification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="fd962-223">Použití modelu: předpověď výsledků</span><span class="sxs-lookup"><span data-stu-id="fd962-223">Using the model: prediction results</span></span>

<span data-ttu-id="fd962-224">Zobrazit `GitHubIssue` a odpovídající `Area` předpověď popisku, aby bylo možné sdílet výsledky a odpovídajícím způsobem je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="fd962-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="fd962-225">Pomocí následujícího kódu vytvořte zobrazení výsledků <xref:System.Console.WriteLine?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="fd962-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](./snippets/github-issue-classification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="fd962-226">Vrátí vyškolený model, který se má použít pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="fd962-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="fd962-227">Vrátí model na konci `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="fd962-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](./snippets/github-issue-classification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="fd962-228">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-228">Evaluate the model</span></span>

<span data-ttu-id="fd962-229">Teď, když jste vytvořili a naučili model, je nutné ho vyhodnotit s jinou datovou sadou pro zajištění a ověření kvality.</span><span class="sxs-lookup"><span data-stu-id="fd962-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="fd962-230">V `Evaluate` metodě je model vytvořen v nástroji `BuildAndTrainModel` předán k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="fd962-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="fd962-231">Vytvořte `Evaluate` metodu hned po `BuildAndTrainModel` , jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="fd962-232">`Evaluate`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="fd962-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="fd962-233">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="fd962-233">Loads the test dataset.</span></span>
* <span data-ttu-id="fd962-234">Vytvoří filtr s více třídami.</span><span class="sxs-lookup"><span data-stu-id="fd962-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="fd962-235">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="fd962-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="fd962-236">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="fd962-236">Displays the metrics.</span></span>

<span data-ttu-id="fd962-237">Přidejte volání do metody New z `Main` metody přímo pod `BuildAndTrainModel` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/github-issue-classification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="fd962-238">Stejně jako v případě, že jste použili datovou sadu školení, načtěte testovací datovou sadu přidáním následujícího kódu do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="fd962-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/github-issue-classification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="fd962-239">Metoda [Evaluate ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) počítá metriky kvality pro model používající zadanou datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="fd962-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="fd962-240">Vrátí <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> objekt, který obsahuje celkové metriky vypočítané filtry klasifikace s více třídami.</span><span class="sxs-lookup"><span data-stu-id="fd962-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="fd962-241">Chcete-li zobrazit metriky pro určení kvality modelu, je nutné je nejprve získat.</span><span class="sxs-lookup"><span data-stu-id="fd962-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="fd962-242">Všimněte si použití metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) `_trainedModel` globální proměnné Machine Learning ( [ITransformer](xref:Microsoft.ML.ITransformer)) k zadání funkcí a vrácení předpovědi.</span><span class="sxs-lookup"><span data-stu-id="fd962-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="fd962-243">Do metody přidejte následující kód `Evaluate` jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="fd962-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](./snippets/github-issue-classification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="fd962-244">Pro klasifikaci s více třídami jsou vyhodnocovány následující metriky:</span><span class="sxs-lookup"><span data-stu-id="fd962-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="fd962-245">Mikropřesnost – každá dvojice vzorových tříd přispívá stejně jako metrika přesnosti.</span><span class="sxs-lookup"><span data-stu-id="fd962-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="fd962-246">Chcete, aby byla mikropřesnost co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="fd962-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="fd962-247">Přesnost makra – každá třída přispívá stejně jako metrika přesnosti.</span><span class="sxs-lookup"><span data-stu-id="fd962-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="fd962-248">Minoritní třídy mají stejnou váhu jako větší třídy.</span><span class="sxs-lookup"><span data-stu-id="fd962-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="fd962-249">Chcete, aby byla přesnost makra co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="fd962-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="fd962-250">Protokolová ztráta – viz [ztráta protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="fd962-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="fd962-251">Chcete, aby byla ztráta protokolu co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="fd962-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="fd962-252">Omezení ztrát v protokolu – rozsahy od [-INF, 1,00], kde 1,00 je perfektní předpovědi a 0 označuje střední hodnotu předpovědi.</span><span class="sxs-lookup"><span data-stu-id="fd962-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="fd962-253">Je třeba co nejblíže omezit ztrátu protokolu.</span><span class="sxs-lookup"><span data-stu-id="fd962-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="fd962-254">Zobrazení metrik pro ověřování modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="fd962-255">Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:</span><span class="sxs-lookup"><span data-stu-id="fd962-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](./snippets/github-issue-classification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="fd962-256">Uložení modelu do souboru</span><span class="sxs-lookup"><span data-stu-id="fd962-256">Save the model to a file</span></span>

<span data-ttu-id="fd962-257">Jakmile se model splní, uložte ho do souboru, aby se předpovědi později nebo v jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd962-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="fd962-258">Do metody `Evaluate` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="fd962-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="fd962-259">Vytvořte `SaveModelAsFile` metodu pod vaší `Evaluate` metodou.</span><span class="sxs-lookup"><span data-stu-id="fd962-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="fd962-260">Do metody přidejte následující kód `SaveModelAsFile` .</span><span class="sxs-lookup"><span data-stu-id="fd962-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="fd962-261">Tento kód používá [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metodu k serializaci a uložení výukového modelu jako souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="fd962-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="fd962-262">Nasazení a předpověď pomocí modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="fd962-263">Přidejte volání do metody New z `Main` metody přímo pod `Evaluate` voláním metody pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](./snippets/github-issue-classification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="fd962-264">Vytvořte `PredictIssue` metodu hned za `Evaluate` metodou (a těsně před `SaveModelAsFile` metodou) pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fd962-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="fd962-265">`PredictIssue`Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="fd962-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="fd962-266">Načte uložený model.</span><span class="sxs-lookup"><span data-stu-id="fd962-266">Loads the saved model</span></span>
* <span data-ttu-id="fd962-267">Vytvoří jeden problém testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="fd962-268">Odhadne oblast na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="fd962-269">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="fd962-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="fd962-270">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="fd962-270">Displays the predicted results.</span></span>

<span data-ttu-id="fd962-271">Načtěte uložený model do aplikace přidáním následujícího kódu do `PredictIssue` metody:</span><span class="sxs-lookup"><span data-stu-id="fd962-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="fd962-272">Přidejte problém GitHubu pro otestování předpovědi vyškolených modelů v `Predict` metodě vytvořením instance `GitHubIssue` :</span><span class="sxs-lookup"><span data-stu-id="fd962-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](./snippets/github-issue-classification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="fd962-273">Jak jste předtím pracovali, vytvořte `PredictionEngine` instanci s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="fd962-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="fd962-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="fd962-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="fd962-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="fd962-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="fd962-276">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="fd962-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="fd962-277">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd962-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="fd962-278">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="fd962-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="fd962-279">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="fd962-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="fd962-280">Použijte `PredictionEngine` pro předpověď popisku oblasti GitHub přidáním následujícího kódu do `PredictIssue` metody pro předpověď:</span><span class="sxs-lookup"><span data-stu-id="fd962-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](./snippets/github-issue-classification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="fd962-281">Použití načteného modelu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="fd962-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="fd962-282">Zobrazí se, aby `Area` se problém kategorizoval, a podle toho ho zařadí.</span><span class="sxs-lookup"><span data-stu-id="fd962-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="fd962-283">Pomocí následujícího kódu vytvořte zobrazení výsledků <xref:System.Console.WriteLine?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="fd962-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](./snippets/github-issue-classification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="fd962-284">Výsledky</span><span class="sxs-lookup"><span data-stu-id="fd962-284">Results</span></span>

<span data-ttu-id="fd962-285">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="fd962-285">Your results should be similar to the following.</span></span> <span data-ttu-id="fd962-286">V průběhu procesu kanálu se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="fd962-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="fd962-287">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="fd962-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="fd962-288">Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="fd962-288">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="fd962-289">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="fd962-289">Congratulations!</span></span> <span data-ttu-id="fd962-290">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď popisku oblasti pro problém GitHubu.</span><span class="sxs-lookup"><span data-stu-id="fd962-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="fd962-291">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .</span><span class="sxs-lookup"><span data-stu-id="fd962-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fd962-292">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fd962-292">Next steps</span></span>

<span data-ttu-id="fd962-293">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="fd962-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fd962-294">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="fd962-294">Prepare your data</span></span>
> * <span data-ttu-id="fd962-295">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="fd962-295">Transform the data</span></span>
> * <span data-ttu-id="fd962-296">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-296">Train the model</span></span>
> * <span data-ttu-id="fd962-297">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-297">Evaluate the model</span></span>
> * <span data-ttu-id="fd962-298">Předpověď s vycvičeným modelem</span><span class="sxs-lookup"><span data-stu-id="fd962-298">Predict with the trained model</span></span>
> * <span data-ttu-id="fd962-299">Nasazení a předpověď pomocí načteného modelu</span><span class="sxs-lookup"><span data-stu-id="fd962-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="fd962-300">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="fd962-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="fd962-301">Předpovídání tarifů taxislužby</span><span class="sxs-lookup"><span data-stu-id="fd962-301">Taxi Fare Predictor</span></span>](predict-prices.md)
