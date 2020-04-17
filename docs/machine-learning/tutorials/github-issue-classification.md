---
title: 'Kurz: Kategorizace problémů s podporou – klasifikace více tříd'
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace více tříd ke klasifikaci githubu a přiřadit je k dané oblasti.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fc0e935a36c52627903dac2a7b29d6f534695ea0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608059"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="49527-103">Kurz: Kategorizovat problémy s podporou pomocí klasifikace více tříd s ML.NET</span><span class="sxs-lookup"><span data-stu-id="49527-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="49527-104">Tento ukázkový kurz ilustruje použití ML.NET k vytvoření klasifikátoru problémů GitHub utrénovat model, který klasifikuje a předpovídá popisek Area pro problém GitHub prostřednictvím aplikace konzoly .NET Core pomocí Jazyka C# v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49527-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="49527-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="49527-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="49527-106">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="49527-106">Prepare your data</span></span>
> * <span data-ttu-id="49527-107">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="49527-107">Transform the data</span></span>
> * <span data-ttu-id="49527-108">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="49527-108">Train the model</span></span>
> * <span data-ttu-id="49527-109">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="49527-109">Evaluate the model</span></span>
> * <span data-ttu-id="49527-110">Předvídejte pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="49527-110">Predict with the trained model</span></span>
> * <span data-ttu-id="49527-111">Nasazení a předvídání s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="49527-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="49527-112">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)</span><span class="sxs-lookup"><span data-stu-id="49527-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49527-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49527-113">Prerequisites</span></span>

* <span data-ttu-id="49527-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="49527-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="49527-115">[Github problémy kartu oddělený soubor (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="49527-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="49527-116">[Github vydává soubor oddělený testovací kartou (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="49527-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="49527-117">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="49527-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="49527-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="49527-118">Create a project</span></span>

1. <span data-ttu-id="49527-119">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="49527-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="49527-120">Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.**</span><span class="sxs-lookup"><span data-stu-id="49527-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="49527-121">V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="49527-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="49527-122">Pak vyberte šablonu projektu **Konzola Aplikace (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="49527-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="49527-123">Do textového pole **Název** zadejte "GitHubIssueClassification" a pak vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="49527-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="49527-124">Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat:</span><span class="sxs-lookup"><span data-stu-id="49527-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="49527-125">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="49527-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="49527-126">Zadejte "Data" a stiskněte enter.</span><span class="sxs-lookup"><span data-stu-id="49527-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="49527-127">Vytvořte adresář s názvem *Modely* v projektu pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="49527-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="49527-128">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="49527-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="49527-129">Zadejte "Modely" a stiskněte enter.</span><span class="sxs-lookup"><span data-stu-id="49527-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="49527-130">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="49527-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="49527-131">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="49527-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="49527-132">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML** a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="49527-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="49527-133">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="49527-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="49527-134">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="49527-134">Prepare your data</span></span>

1. <span data-ttu-id="49527-135">Stáhněte si datové sady [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) a uložte je do dříve vytvořené složky *Data.*</span><span class="sxs-lookup"><span data-stu-id="49527-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="49527-136">První datová sada trénuje model strojového učení a druhá slouží k vyhodnocení, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="49527-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="49527-137">V Průzkumníku řešení klepněte \*pravým tlačítkem myši na jednotlivé soubory tsv a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="49527-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="49527-138">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="49527-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="49527-139">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="49527-139">Create classes and define paths</span></span>

<span data-ttu-id="49527-140">Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:</span><span class="sxs-lookup"><span data-stu-id="49527-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="49527-141">Vytvořte tři globální pole pro uložení cest k nedávno staženým `MLContext`souborům a globálních proměnných pro ,`DataView`a `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="49527-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="49527-142">`_trainDataPath`má cestu k datové sadě použité k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="49527-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="49527-143">`_testDataPath`má cestu k datové sadě použité k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="49527-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="49527-144">`_modelPath`má cestu, kde je trénovaný model uložen.</span><span class="sxs-lookup"><span data-stu-id="49527-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="49527-145">`_mlContext`<xref:Microsoft.ML.MLContext> je, který poskytuje kontext zpracování.</span><span class="sxs-lookup"><span data-stu-id="49527-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="49527-146">`_trainingDataView`<xref:Microsoft.ML.IDataView> slouží ke zpracování trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="49527-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="49527-147">`_predEngine`je <xref:Microsoft.ML.PredictionEngine%602> používá pro jednotlivé předpovědi.</span><span class="sxs-lookup"><span data-stu-id="49527-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="49527-148">Přidejte následující kód na řádek `Main` přímo nad metodou, abyste určili tyto cesty a další proměnné:</span><span class="sxs-lookup"><span data-stu-id="49527-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="49527-149">Vytvořte některé třídy pro vaše vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="49527-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="49527-150">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="49527-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="49527-151">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="49527-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="49527-152">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="49527-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="49527-153">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="49527-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="49527-154">V editoru kódu se otevře *soubor GitHubIssueData.cs.*</span><span class="sxs-lookup"><span data-stu-id="49527-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="49527-155">Na začátek `using` *GitHubIssueData.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="49527-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="49527-156">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, do souboru *GitHubIssueData.cs:*</span><span class="sxs-lookup"><span data-stu-id="49527-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="49527-157">Je `label` sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="49527-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="49527-158">Identifikované `Features` jsou vstupy, které dáte modelu předpovědět Label.</span><span class="sxs-lookup"><span data-stu-id="49527-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="49527-159">Pomocí [atributu LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="49527-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="49527-160">`GitHubIssue`je vstupní třída datové sady <xref:System.String> a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="49527-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="49527-161">první sloupec `ID` (ID problému GitHub)</span><span class="sxs-lookup"><span data-stu-id="49527-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="49527-162">druhý sloupec `Area` (předpověď pro trénink)</span><span class="sxs-lookup"><span data-stu-id="49527-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="49527-163">třetí sloupec `Title` (název problému GitHub) `feature` je první použitý pro předvídání`Area`</span><span class="sxs-lookup"><span data-stu-id="49527-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="49527-164">čtvrtý sloupec `Description` je `feature` druhý, který se používá pro předvídání`Area`</span><span class="sxs-lookup"><span data-stu-id="49527-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="49527-165">`IssuePrediction`je třída použitá pro předpověď po trénovaném modelu.</span><span class="sxs-lookup"><span data-stu-id="49527-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="49527-166">Má jeden `string` (`Area`) `PredictedLabel` `ColumnName` a atribut.</span><span class="sxs-lookup"><span data-stu-id="49527-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="49527-167">Používá `PredictedLabel` se při predikci a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="49527-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="49527-168">Pro vyhodnocení se používá vstup s trénovacími daty, předpovídanými hodnotami a modelem.</span><span class="sxs-lookup"><span data-stu-id="49527-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="49527-169">Všechny operace ML.NET spustit ve třídě [MLContext.](xref:Microsoft.ML.MLContext)</span><span class="sxs-lookup"><span data-stu-id="49527-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="49527-170">Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="49527-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="49527-171">Je to podobné, koncepčně, do `DBContext` . `Entity Framework`</span><span class="sxs-lookup"><span data-stu-id="49527-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="49527-172">Inicializovat proměnné v hlavní</span><span class="sxs-lookup"><span data-stu-id="49527-172">Initialize variables in Main</span></span>

<span data-ttu-id="49527-173">Inicializovat `_mlContext` globální proměnnou s `MLContext` novou instancí`seed: 0`s náhodným osivem ( ) pro opakovatelné/deterministické výsledky napříč více tréninky.</span><span class="sxs-lookup"><span data-stu-id="49527-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="49527-174">Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě: `Main`</span><span class="sxs-lookup"><span data-stu-id="49527-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="49527-175">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="49527-175">Load the data</span></span>

<span data-ttu-id="49527-176">ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisu číselných nebo textových tabulkových dat.</span><span class="sxs-lookup"><span data-stu-id="49527-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="49527-177">`IDataView`můžete načíst textové soubory nebo v reálném čase (například SQL database nebo log files).</span><span class="sxs-lookup"><span data-stu-id="49527-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="49527-178">Chcete-li inicializovat a načíst `_trainingDataView` globální proměnnou, abyste ji `mlContext` mohli použít pro kanál, přidejte po inicializaci následující kód:</span><span class="sxs-lookup"><span data-stu-id="49527-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="49527-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru.</span><span class="sxs-lookup"><span data-stu-id="49527-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="49527-180">Přebírá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="49527-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="49527-181">Jako další řádek kódu v metodě přidejte `Main` následující:</span><span class="sxs-lookup"><span data-stu-id="49527-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="49527-182">Metoda `ProcessData` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="49527-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="49527-183">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="49527-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="49527-184">Vrátí kanál zpracování.</span><span class="sxs-lookup"><span data-stu-id="49527-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="49527-185">Vytvořte `ProcessData` metodu, `Main` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="49527-186">Extrahování prvků a transformace dat</span><span class="sxs-lookup"><span data-stu-id="49527-186">Extract Features and transform the data</span></span>

<span data-ttu-id="49527-187">Chcete-li předpovědět popisek Area GitHub `GitHubIssue`pro , použijte metodu [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) k transformaci `Area` sloupce do sloupce číselného typu `Label` klíče (formát přijatý klasifikačními algoritmy) a přidejte jej jako nový sloupec datové sady:</span><span class="sxs-lookup"><span data-stu-id="49527-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="49527-188">Dále volání, `mlContext.Transforms.Text.FeaturizeText` které transformuje text (`Title` a `Description`) `TitleFeaturized` sloupce `DescriptionFeaturized`do číselného vektoru pro každý volal a .</span><span class="sxs-lookup"><span data-stu-id="49527-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="49527-189">Připojit featurization pro oba sloupce do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="49527-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="49527-190">Poslední krok v přípravě dat kombinuje všechny sloupce funkce do sloupce **Funkce** pomocí metody [Concatenate().](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A)</span><span class="sxs-lookup"><span data-stu-id="49527-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="49527-191">Ve výchozím nastavení algoritmus učení zpracovává pouze funkce ze sloupce **Funkce.**</span><span class="sxs-lookup"><span data-stu-id="49527-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="49527-192">Připojit tuto transformaci do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="49527-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="49527-193">Dále připojit <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do mezipaměti DataView, takže při iterát přes data vícekrát pomocí mezipaměti může získat lepší výkon, jako s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="49527-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="49527-194">Použijte AppendCacheCheckpoint pro malé a střední datové sady snížit dobu trénování.</span><span class="sxs-lookup"><span data-stu-id="49527-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="49527-195">Nepoužívejte jej (odstraňte . AppendCacheCheckpoint()) při zpracování velmi velké datové sady.</span><span class="sxs-lookup"><span data-stu-id="49527-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="49527-196">Vrátit potrubí na konci `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="49527-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="49527-197">Tento krok zpracovává předběžné zpracování/featurization.</span><span class="sxs-lookup"><span data-stu-id="49527-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="49527-198">Použití dalších součástí dostupných v ML.NET může umožnit lepší výsledky s modelem.</span><span class="sxs-lookup"><span data-stu-id="49527-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="49527-199">Sestavení a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="49527-199">Build and train the model</span></span>

<span data-ttu-id="49527-200">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek `Main` kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="49527-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="49527-201">Metoda `BuildAndTrainModel` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="49527-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="49527-202">Vytvoří třídu trénovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="49527-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="49527-203">Trénuje model.</span><span class="sxs-lookup"><span data-stu-id="49527-203">Trains the model.</span></span>
* <span data-ttu-id="49527-204">Předpovídá oblast na základě trénovacích dat.</span><span class="sxs-lookup"><span data-stu-id="49527-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="49527-205">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="49527-205">Returns the model.</span></span>

<span data-ttu-id="49527-206">Vytvořte `BuildAndTrainModel` metodu, `Main` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="49527-207">O úkolu klasifikace</span><span class="sxs-lookup"><span data-stu-id="49527-207">About the classification task</span></span>

<span data-ttu-id="49527-208">Klasifikace je úloha strojového učení, která používá data k **určení** kategorie, typu nebo třídy položky nebo řádku dat a je často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="49527-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="49527-209">Binární: buď A nebo B.</span><span class="sxs-lookup"><span data-stu-id="49527-209">Binary: either A or B.</span></span>
* <span data-ttu-id="49527-210">Vícetřídy: více kategorií, které lze předpovědět pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="49527-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="49527-211">Pro tento typ problému použijte algoritmus učení klasifikace více tříd, protože předpověď kategorie problému může být jedna z více kategorií (více tříd) spíše než pouze dvě (binární).</span><span class="sxs-lookup"><span data-stu-id="49527-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="49527-212">Přidejte algoritmus strojového učení k definicím transformace dat přidáním `BuildAndTrainModel()`následujícího jako první řádek kódu v aplikaci :</span><span class="sxs-lookup"><span data-stu-id="49527-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="49527-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je váš vícetřídní algoritmus klasifikace školení.</span><span class="sxs-lookup"><span data-stu-id="49527-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="49527-214">To je připojen `pipeline` k a přijímá `Title` featurized a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="49527-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="49527-215">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="49527-215">Train the model</span></span>

<span data-ttu-id="49527-216">Připevněte model `splitTrainSet` k datům a vraťte trénovaný model `BuildAndTrainModel()` přidáním následujícího jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="49527-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="49527-217">Metoda `Fit()`trénuje váš model transformací datové sady a použitím školení.</span><span class="sxs-lookup"><span data-stu-id="49527-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="49527-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje předat a potom provést předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="49527-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="49527-219">Přidejte to jako další `BuildAndTrainModel()` řádek v metodě:</span><span class="sxs-lookup"><span data-stu-id="49527-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="49527-220">Předvídejte pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="49527-220">Predict with the trained model</span></span>

<span data-ttu-id="49527-221">Přidejte problém GitHub k testování predikce `Predict` trénovaného `GitHubIssue`modelu v metodě vytvořením instance :</span><span class="sxs-lookup"><span data-stu-id="49527-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="49527-222">Použití [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce provede předpověď na jeden řádek dat:</span><span class="sxs-lookup"><span data-stu-id="49527-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="49527-223">Použití modelu: predikce výsledků</span><span class="sxs-lookup"><span data-stu-id="49527-223">Using the model: prediction results</span></span>

<span data-ttu-id="49527-224">Zobrazit `GitHubIssue` a `Area` odpovídající popisek predikce s cílem sdílet výsledky a jednat podle nich odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="49527-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="49527-225">Vytvořte zobrazení výsledků pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="49527-226">Vrátit model vyškolený k použití pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="49527-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="49527-227">Vrátit model na konci `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="49527-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="49527-228">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="49527-228">Evaluate the model</span></span>

<span data-ttu-id="49527-229">Teď, když jste vytvořili a trénovali model, musíte ho vyhodnotit pomocí jiné datové sady pro zajištění kvality a ověření.</span><span class="sxs-lookup"><span data-stu-id="49527-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="49527-230">V `Evaluate` metodě je model `BuildAndTrainModel` vytvořený v aplikaci předán k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="49527-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="49527-231">Vytvořte `Evaluate` metodu, `BuildAndTrainModel`těsně po , jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="49527-232">Metoda `Evaluate` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="49527-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="49527-233">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="49527-233">Loads the test dataset.</span></span>
* <span data-ttu-id="49527-234">Vytvoří vícetřídní vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="49527-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="49527-235">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="49527-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="49527-236">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="49527-236">Displays the metrics.</span></span>

<span data-ttu-id="49527-237">Přidejte volání nové metody `Main` z metody, `BuildAndTrainModel` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="49527-238">Stejně jako dříve s trénovací datovou sadou načtěte testovací datovou sadu přidáním následujícího kódu k metodě: `Evaluate`</span><span class="sxs-lookup"><span data-stu-id="49527-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="49527-239">[Metoda Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) vypočítá metriky kvality pro model pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="49527-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="49527-240">Vrátí <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> objekt, který obsahuje celkové metriky vypočítané vyhodnocením klasifikace více tříd.</span><span class="sxs-lookup"><span data-stu-id="49527-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="49527-241">Chcete-li zobrazit metriky k určení kvality modelu, musíte je nejprve získat.</span><span class="sxs-lookup"><span data-stu-id="49527-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="49527-242">Všimněte si použití [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda `_trainedModel` globální proměnné strojového učení [(ITransformer)](xref:Microsoft.ML.ITransformer)pro zadání funkcí a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="49527-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="49527-243">Jako další řádek `Evaluate` přidejte do metody následující kód:</span><span class="sxs-lookup"><span data-stu-id="49527-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="49527-244">Následující metriky jsou vyhodnocovány pro klasifikaci více tříd:</span><span class="sxs-lookup"><span data-stu-id="49527-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="49527-245">Mikropřesnost - Každý pár třídy vzorků přispívá stejnou měrou k metrike přesnosti.</span><span class="sxs-lookup"><span data-stu-id="49527-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="49527-246">Chcete, aby mikro přesnost byla co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="49527-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="49527-247">Přesnost maker – každá třída přispívá stejnou měrou k metrike přesnosti.</span><span class="sxs-lookup"><span data-stu-id="49527-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="49527-248">Menšinové třídy mají stejnou váhu jako větší třídy.</span><span class="sxs-lookup"><span data-stu-id="49527-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="49527-249">Chcete, aby přesnost maker byla co nejblíže jedné.</span><span class="sxs-lookup"><span data-stu-id="49527-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="49527-250">Log-loss - viz [Ztráta protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="49527-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="49527-251">Chcete, aby ztráta protokolu byla co nejblíže nule.</span><span class="sxs-lookup"><span data-stu-id="49527-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="49527-252">Snížení ztráty protokolu - rozsahy od [-inf, 1.00], kde 1.00 je perfektní předpovědi a 0 označuje střední předpovědi.</span><span class="sxs-lookup"><span data-stu-id="49527-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="49527-253">Chcete, aby snížení ztráty protokolu bylo co nejblíže k jednomu.</span><span class="sxs-lookup"><span data-stu-id="49527-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="49527-254">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="49527-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="49527-255">Pomocí následujícího kódu můžete zobrazit metriky, sdílet výsledky a pak s nimi jednat:</span><span class="sxs-lookup"><span data-stu-id="49527-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="49527-256">Uložení modelu do souboru</span><span class="sxs-lookup"><span data-stu-id="49527-256">Save the model to a file</span></span>

<span data-ttu-id="49527-257">Po splnění modelu jej uložte do souboru a vytvořte předpovědi později nebo v jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49527-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="49527-258">Do metody `Evaluate` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="49527-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="49527-259">Vytvořte `SaveModelAsFile` metodu `Evaluate` pod metodou.</span><span class="sxs-lookup"><span data-stu-id="49527-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="49527-260">Přidejte do `SaveModelAsFile` metody následující kód.</span><span class="sxs-lookup"><span data-stu-id="49527-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="49527-261">Tento kód [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) používá metodu serializovat a uložit trénovaný model jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="49527-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="49527-262">Nasazení a předvídání pomocí modelu</span><span class="sxs-lookup"><span data-stu-id="49527-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="49527-263">Přidejte volání nové metody `Main` z metody, `Evaluate` přímo pod volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="49527-264">Vytvořte `PredictIssue` metodu, `Evaluate` těsně po metodě `SaveModelAsFile` (a těsně před metodou), pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="49527-265">Metoda `PredictIssue` provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="49527-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="49527-266">Načte uložený model</span><span class="sxs-lookup"><span data-stu-id="49527-266">Loads the saved model</span></span>
* <span data-ttu-id="49527-267">Vytvoří jeden problém testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="49527-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="49527-268">Předpovídá oblast na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="49527-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="49527-269">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="49527-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="49527-270">Zobrazí předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="49527-270">Displays the predicted results.</span></span>

<span data-ttu-id="49527-271">Načtěte uložený model do aplikace přidáním následujícího kódu k metodě: `PredictIssue`</span><span class="sxs-lookup"><span data-stu-id="49527-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="49527-272">Přidejte problém GitHub k testování predikce `Predict` trénovaného `GitHubIssue`modelu v metodě vytvořením instance :</span><span class="sxs-lookup"><span data-stu-id="49527-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="49527-273">Stejně jako dříve `PredictionEngine` vytvořte instanci s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="49527-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="49527-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="49527-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="49527-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="49527-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="49527-276">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="49527-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="49527-277">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49527-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="49527-278">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="49527-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="49527-279">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="49527-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="49527-280">Použijte `PredictionEngine` k předvídání popisek Oblasti GitHub `PredictIssue` přidáním následujícího kódu k metodě pro předpověď:</span><span class="sxs-lookup"><span data-stu-id="49527-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="49527-281">Použití načteného modelu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="49527-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="49527-282">Zobrazit, `Area` aby bylo možné problém kategorizovat a podle toho jednat.</span><span class="sxs-lookup"><span data-stu-id="49527-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="49527-283">Vytvořte zobrazení výsledků pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="49527-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="49527-284">Výsledky</span><span class="sxs-lookup"><span data-stu-id="49527-284">Results</span></span>

<span data-ttu-id="49527-285">Vaše výsledky by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="49527-285">Your results should be similar to the following.</span></span> <span data-ttu-id="49527-286">Jako procesy kanálu se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="49527-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="49527-287">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="49527-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="49527-288">Tyto zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="49527-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="49527-289">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="49527-289">Congratulations!</span></span> <span data-ttu-id="49527-290">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předvídání popisek oblasti pro problém GitHub.</span><span class="sxs-lookup"><span data-stu-id="49527-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="49527-291">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)</span><span class="sxs-lookup"><span data-stu-id="49527-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="49527-292">Další kroky</span><span class="sxs-lookup"><span data-stu-id="49527-292">Next steps</span></span>

<span data-ttu-id="49527-293">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="49527-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="49527-294">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="49527-294">Prepare your data</span></span>
> * <span data-ttu-id="49527-295">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="49527-295">Transform the data</span></span>
> * <span data-ttu-id="49527-296">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="49527-296">Train the model</span></span>
> * <span data-ttu-id="49527-297">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="49527-297">Evaluate the model</span></span>
> * <span data-ttu-id="49527-298">Předvídejte pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="49527-298">Predict with the trained model</span></span>
> * <span data-ttu-id="49527-299">Nasazení a předvídání s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="49527-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="49527-300">Přejdete k dalšímu kurzu, abyste se dozvěděli více</span><span class="sxs-lookup"><span data-stu-id="49527-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="49527-301">Prediktor jízdného taxi</span><span class="sxs-lookup"><span data-stu-id="49527-301">Taxi Fare Predictor</span></span>](predict-prices.md)
