---
title: 'Kurz: zařazení do kategorií – problémy s podporou – klasifikace s více třídami'
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace s více třídami ke klasifikaci problémů GitHubu, aby je bylo možné přiřadit k dané oblasti.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 7507463cfc5504182f028ab2ced9a03733c61f6d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774490"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="c826b-103">Kurz: kategorizace problémů podpory pomocí klasifikace s více třídami s ML .NET</span><span class="sxs-lookup"><span data-stu-id="c826b-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="c826b-104">Tento ukázkový kurz znázorňuje použití ML.NET k vytvoření klasifikátoru problémů GitHubu pro výuku modelu, který klasifikuje a odhadne popisek oblasti pro problém na GitHubu prostřednictvím konzolové aplikace .NET Core využívající C# v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c826b-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="c826b-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="c826b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c826b-106">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="c826b-106">Prepare your data</span></span>
> * <span data-ttu-id="c826b-107">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="c826b-107">Transform the data</span></span>
> * <span data-ttu-id="c826b-108">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-108">Train the model</span></span>
> * <span data-ttu-id="c826b-109">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-109">Evaluate the model</span></span>
> * <span data-ttu-id="c826b-110">Předpověď s vycvičeným modelem</span><span class="sxs-lookup"><span data-stu-id="c826b-110">Predict with the trained model</span></span>
> * <span data-ttu-id="c826b-111">Nasazení a předpověď pomocí načteného modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="c826b-112">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .</span><span class="sxs-lookup"><span data-stu-id="c826b-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c826b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c826b-113">Prerequisites</span></span>

* <span data-ttu-id="c826b-114">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="c826b-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="c826b-115">[Soubor s oddělovači (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv)se zastavuje na kartě GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c826b-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="c826b-116">[Soubor s oddělovači (issues_test. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv)se zastavuje na kartě Test.</span><span class="sxs-lookup"><span data-stu-id="c826b-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c826b-117">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="c826b-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="c826b-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c826b-118">Create a project</span></span>

1. <span data-ttu-id="c826b-119">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c826b-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="c826b-120">Z řádku nabídek vyberte **soubor** > **Nový** **projekt**  > .</span><span class="sxs-lookup"><span data-stu-id="c826b-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c826b-121">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="c826b-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c826b-122">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="c826b-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c826b-123">Do textového pole **název** zadejte "GitHubIssueClassification" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="c826b-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="c826b-124">Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady:</span><span class="sxs-lookup"><span data-stu-id="c826b-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="c826b-125">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **přidat** **novou složku** > .</span><span class="sxs-lookup"><span data-stu-id="c826b-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c826b-126">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="c826b-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="c826b-127">Vytvořte v projektu adresář s názvem *Models* a uložte svůj model:</span><span class="sxs-lookup"><span data-stu-id="c826b-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="c826b-128">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **přidat** **novou složku** > .</span><span class="sxs-lookup"><span data-stu-id="c826b-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c826b-129">Zadejte "modely" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="c826b-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="c826b-130">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="c826b-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="c826b-131">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c826b-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c826b-132">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml**, vyberte balíček v **1.0.0** v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="c826b-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="c826b-133">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="c826b-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="c826b-134">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="c826b-134">Prepare your data</span></span>

1. <span data-ttu-id="c826b-135">Stáhněte sady dat [issues_train. TSV](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test. TSV](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) a uložte je do složky *data* , která byla dříve vytvořena.</span><span class="sxs-lookup"><span data-stu-id="c826b-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="c826b-136">První datová sada Vlaks model strojového učení a druhá se dá použít k vyhodnocení toho, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="c826b-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="c826b-137">V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů. TSV \*a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c826b-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="c826b-138">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="c826b-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="c826b-139">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="c826b-139">Create classes and define paths</span></span>

<span data-ttu-id="c826b-140">Do horní části souboru *program.cs* přidejte následující dodatečné příkazy `using`:</span><span class="sxs-lookup"><span data-stu-id="c826b-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="c826b-141">Vytvořte tři globální pole pro uchování cest ke nedávno staženým souborům a globální proměnné pro `MLContext`,`DataView`a `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="c826b-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="c826b-142">`_trainDataPath` má cestu k datové sadě, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="c826b-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="c826b-143">`_testDataPath` má cestu k datové sadě, která se používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="c826b-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="c826b-144">`_modelPath` má cestu, kde je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="c826b-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="c826b-145">`_mlContext` je <xref:Microsoft.ML.MLContext>, který poskytuje kontext zpracování.</span><span class="sxs-lookup"><span data-stu-id="c826b-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="c826b-146">`_trainingDataView` je <xref:Microsoft.ML.IDataView> používá ke zpracování datové sady školení.</span><span class="sxs-lookup"><span data-stu-id="c826b-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="c826b-147">`_predEngine` je <xref:Microsoft.ML.PredictionEngine%602> používá se pro jednotlivé předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c826b-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="c826b-148">Přidejte následující kód na řádek vpravo nad `Main` metodou pro určení těchto cest a dalších proměnných:</span><span class="sxs-lookup"><span data-stu-id="c826b-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="c826b-149">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c826b-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="c826b-150">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="c826b-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="c826b-151">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="c826b-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="c826b-152">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="c826b-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="c826b-153">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="c826b-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="c826b-154">V editoru kódu se otevře soubor *GitHubIssueData.cs* .</span><span class="sxs-lookup"><span data-stu-id="c826b-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="c826b-155">Do horní části *GitHubIssueData.cs*přidejte následující příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="c826b-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="c826b-156">Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, do souboru *GitHubIssueData.cs* :</span><span class="sxs-lookup"><span data-stu-id="c826b-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="c826b-157">@No__t_0 je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="c826b-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="c826b-158">Identifikované `Features` jsou vstupy, které modelu udělíte k předpovídání popisku.</span><span class="sxs-lookup"><span data-stu-id="c826b-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="c826b-159">Pomocí [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v sadě dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="c826b-160">`GitHubIssue` je vstupní třída DataSet a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="c826b-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="c826b-161">první `ID` sloupce (ID problému GitHubu)</span><span class="sxs-lookup"><span data-stu-id="c826b-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="c826b-162">druhý sloupec `Area` (předpověď pro školení)</span><span class="sxs-lookup"><span data-stu-id="c826b-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="c826b-163">třetí sloupec `Title` (název problému GitHubu) je první `feature`, která se používá pro předpověď `Area`</span><span class="sxs-lookup"><span data-stu-id="c826b-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="c826b-164">čtvrtý sloupec `Description` je druhým `feature` použitým pro předpověď `Area`</span><span class="sxs-lookup"><span data-stu-id="c826b-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="c826b-165">`IssuePrediction` je třída použitá pro předpověď po vyškolení modelu.</span><span class="sxs-lookup"><span data-stu-id="c826b-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="c826b-166">Má jeden `string` (`Area`) a atribut `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="c826b-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="c826b-167">`PredictedLabel` se používá během předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="c826b-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="c826b-168">Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.</span><span class="sxs-lookup"><span data-stu-id="c826b-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="c826b-169">Všechny operace ML.NET začínají ve třídě [MLContext](xref:Microsoft.ML.MLContext) .</span><span class="sxs-lookup"><span data-stu-id="c826b-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="c826b-170">Inicializace `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="c826b-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="c826b-171">Je podobný a koncepčně `DBContext` v `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="c826b-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="c826b-172">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="c826b-172">Initialize variables in Main</span></span>

<span data-ttu-id="c826b-173">Inicializujte `_mlContext` globální proměnnou novou instancí `MLContext` s náhodným osivem (`seed: 0`) pro opakované nebo deterministické výsledky v rámci více školení.</span><span class="sxs-lookup"><span data-stu-id="c826b-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="c826b-174">Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="c826b-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="c826b-175">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c826b-175">Load the data</span></span>

<span data-ttu-id="c826b-176">ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data.</span><span class="sxs-lookup"><span data-stu-id="c826b-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="c826b-177">`IDataView` může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu).</span><span class="sxs-lookup"><span data-stu-id="c826b-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="c826b-178">Chcete-li inicializovat a načíst `_trainingDataView` globální proměnnou, aby ji bylo možné použít pro kanál, přidejte po inicializaci `mlContext` následující kód:</span><span class="sxs-lookup"><span data-stu-id="c826b-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="c826b-179">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="c826b-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="c826b-180">Převezme proměnné cesty k datům a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="c826b-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="c826b-181">Jako další řádek kódu v metodě `Main` přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="c826b-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="c826b-182">Metoda `ProcessData` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c826b-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="c826b-183">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="c826b-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="c826b-184">Vrátí kanál zpracování.</span><span class="sxs-lookup"><span data-stu-id="c826b-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="c826b-185">Vytvořte metodu `ProcessData` hned za metodou `Main` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="c826b-186">Extrakce funkcí a transformace dat</span><span class="sxs-lookup"><span data-stu-id="c826b-186">Extract Features and transform the data</span></span>

<span data-ttu-id="c826b-187">Vzhledem k tomu, že chcete předpovědět popisek GitHubu oblasti pro `GitHubIssue`, použijte metodu [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pro transformaci sloupce `Area` na typ číselného klíče `Label` sloupec (formát přijatý algoritmy klasifikace) a přidejte ho jako sloupec nové datové sady. :</span><span class="sxs-lookup"><span data-stu-id="c826b-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="c826b-188">Dále zavolejte `mlContext.Transforms.Text.FeaturizeText`, která transformuje sloupce text (`Title` a `Description`) na číselný vektor pro každý pojmenovaný `TitleFeaturized` a `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="c826b-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="c826b-189">Přidejte featurization pro oba sloupce do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c826b-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="c826b-190">Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí metody [CONCATENATE ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) .</span><span class="sxs-lookup"><span data-stu-id="c826b-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="c826b-191">Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** .</span><span class="sxs-lookup"><span data-stu-id="c826b-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="c826b-192">Přidejte tuto transformaci do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c826b-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="c826b-193">Dále přidejte <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pro ukládání DataView do mezipaměti, takže když Iterujte data víckrát pomocí mezipaměti, může dorazit k vyššímu výkonu, jako u následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="c826b-194">Použijte AppendCacheCheckpoint pro malé nebo střední datové sady k nižšímu času školení.</span><span class="sxs-lookup"><span data-stu-id="c826b-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="c826b-195">Nepoužívejte ho (odebrat. AppendCacheCheckpoint ()) při zpracování velmi rozsáhlých datových sad.</span><span class="sxs-lookup"><span data-stu-id="c826b-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="c826b-196">Vrátí kanál na konci metody `ProcessData`.</span><span class="sxs-lookup"><span data-stu-id="c826b-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="c826b-197">Tento krok zpracovává předzpracování/featurization.</span><span class="sxs-lookup"><span data-stu-id="c826b-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="c826b-198">Použití dalších součástí dostupných v ML.NET může mít za následek lepší výsledky v modelu.</span><span class="sxs-lookup"><span data-stu-id="c826b-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="c826b-199">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-199">Build and train the model</span></span>

<span data-ttu-id="c826b-200">Přidejte následující volání metody `BuildAndTrainModel`jako další řádek kódu v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="c826b-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="c826b-201">Metoda `BuildAndTrainModel` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c826b-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="c826b-202">Vytvoří třídu školicího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="c826b-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="c826b-203">Navlakuje model.</span><span class="sxs-lookup"><span data-stu-id="c826b-203">Trains the model.</span></span>
* <span data-ttu-id="c826b-204">Odhadne oblast na základě školicích dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="c826b-205">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="c826b-205">Returns the model.</span></span>

<span data-ttu-id="c826b-206">Vytvořte metodu `BuildAndTrainModel` hned za metodou `Main` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="c826b-207">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="c826b-207">About the classification task</span></span>

<span data-ttu-id="c826b-208">Klasifikace je úloha strojového učení, která používá data k **určení** kategorie, typu nebo třídy položky nebo řádku dat a je často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="c826b-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="c826b-209">Binární: buď A nebo B.</span><span class="sxs-lookup"><span data-stu-id="c826b-209">Binary: either A or B.</span></span>
* <span data-ttu-id="c826b-210">Více tříd: více kategorií, které mohou být předpovězeny pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="c826b-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="c826b-211">Pro tento typ problému použijte algoritmus učení s více třídami, protože předpověď kategorie problému může být jednou z více kategorií (více tříd), nikoli jenom dvou (binární).</span><span class="sxs-lookup"><span data-stu-id="c826b-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="c826b-212">Přidejte algoritmus Machine Learning do definice transformace dat tak, že jako první řádek kódu v `BuildAndTrainModel()`přidáte následující:</span><span class="sxs-lookup"><span data-stu-id="c826b-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="c826b-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je váš algoritmus školicích kurzů pro klasifikace více tříd.</span><span class="sxs-lookup"><span data-stu-id="c826b-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="c826b-214">Tento údaj je připojen k `pipeline` a přijímá natrénuje `Title` a `Description` (`Features`) a vstupní parametry `Label` pro další informace z historických dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="c826b-215">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-215">Train the model</span></span>

<span data-ttu-id="c826b-216">Přizpůsobit model na data `splitTrainSet` a vrátit vyškolený model přidáním následujícího jako další řádek kódu v metodě `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="c826b-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="c826b-217">Metoda `Fit()`navlakuje model pomocí transformace datové sady a použití školení.</span><span class="sxs-lookup"><span data-stu-id="c826b-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="c826b-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="c826b-219">Přidejte toto jako další řádek v metodě `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="c826b-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="c826b-220">Předpověď s vycvičeným modelem</span><span class="sxs-lookup"><span data-stu-id="c826b-220">Predict with the trained model</span></span>

<span data-ttu-id="c826b-221">Přidáním problému GitHubu otestujete předpověď vyškolených modelů v metodě `Predict` vytvořením instance `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="c826b-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="c826b-222">Použití funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:</span><span class="sxs-lookup"><span data-stu-id="c826b-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="c826b-223">Použití modelu: předpověď výsledků</span><span class="sxs-lookup"><span data-stu-id="c826b-223">Using the model: prediction results</span></span>

<span data-ttu-id="c826b-224">Zobrazí `GitHubIssue` a odpovídající předpověď popisku `Area`, aby bylo možné sdílet výsledky a podle nich pracovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c826b-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="c826b-225">Pomocí následujícího kódu <xref:System.Console.WriteLine?displayProperty=nameWithType> vytvořte zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="c826b-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="c826b-226">Vrátí vyškolený model, který se má použít pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="c826b-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="c826b-227">Vrátí model na konci metody `BuildAndTrainModel`.</span><span class="sxs-lookup"><span data-stu-id="c826b-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="c826b-228">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-228">Evaluate the model</span></span>

<span data-ttu-id="c826b-229">Teď, když jste vytvořili a naučili model, je nutné ho vyhodnotit s jinou datovou sadou pro zajištění a ověření kvality.</span><span class="sxs-lookup"><span data-stu-id="c826b-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="c826b-230">V metodě `Evaluate` se model vytvořený v `BuildAndTrainModel` předává, aby se vyhodnotil.</span><span class="sxs-lookup"><span data-stu-id="c826b-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="c826b-231">Vytvořte metodu `Evaluate` hned po `BuildAndTrainModel`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="c826b-232">Metoda `Evaluate` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c826b-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="c826b-233">Načte testovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="c826b-233">Loads the test dataset.</span></span>
* <span data-ttu-id="c826b-234">Vytvoří filtr s více třídami.</span><span class="sxs-lookup"><span data-stu-id="c826b-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="c826b-235">Vyhodnotí model a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="c826b-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="c826b-236">Zobrazí metriky.</span><span class="sxs-lookup"><span data-stu-id="c826b-236">Displays the metrics.</span></span>

<span data-ttu-id="c826b-237">Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `BuildAndTrainModel`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="c826b-238">Stejně jako v případě, že jste použili datovou sadu školení, načtěte testovací datovou sadu přidáním následujícího kódu do metody `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="c826b-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="c826b-239">Metoda [Evaluate ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) počítá metriky kvality pro model používající zadanou datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="c826b-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="c826b-240">Vrátí objekt <xref:Microsoft.ML.Data.MulticlassClassificationMetrics>, který obsahuje celkové metriky vypočítané filtry klasifikace více tříd.</span><span class="sxs-lookup"><span data-stu-id="c826b-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="c826b-241">Chcete-li zobrazit metriky pro určení kvality modelu, je nutné je nejprve získat.</span><span class="sxs-lookup"><span data-stu-id="c826b-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="c826b-242">Všimněte si použití metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) `_trainedModel` globální proměnné ( [ITransformer](xref:Microsoft.ML.ITransformer)) pro zadání funkcí a vrácení předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c826b-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="c826b-243">Přidejte následující kód do metody `Evaluate` jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="c826b-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="c826b-244">Pro klasifikaci s více třídami jsou vyhodnocovány následující metriky:</span><span class="sxs-lookup"><span data-stu-id="c826b-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="c826b-245">Mikropřesnost – každá dvojice vzorových tříd přispívá stejně jako metrika přesnosti.</span><span class="sxs-lookup"><span data-stu-id="c826b-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="c826b-246">Má být mikropřesnost co nejblíže k 1.</span><span class="sxs-lookup"><span data-stu-id="c826b-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="c826b-247">Přesnost makra – každá třída přispívá stejně jako metrika přesnosti.</span><span class="sxs-lookup"><span data-stu-id="c826b-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="c826b-248">Minoritní třídy mají stejnou váhu jako větší třídy.</span><span class="sxs-lookup"><span data-stu-id="c826b-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="c826b-249">Chcete, aby byla přesnost makra co nejblíže k 1.</span><span class="sxs-lookup"><span data-stu-id="c826b-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="c826b-250">Protokolová ztráta – viz [ztráta protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="c826b-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="c826b-251">Chcete, aby byla ztráta protokolu co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="c826b-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="c826b-252">Omezení ztrát v protokolu – rozsahy od [-INF, 100], kde 100 je perfektní předpovědi a 0 označuje střední hodnotu předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c826b-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="c826b-253">Chcete omezit ztrátu protokolu tak, aby byla co nejblíže nule.</span><span class="sxs-lookup"><span data-stu-id="c826b-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="c826b-254">Zobrazení metrik pro ověřování modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="c826b-255">Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:</span><span class="sxs-lookup"><span data-stu-id="c826b-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="c826b-256">Uložení modelu do souboru</span><span class="sxs-lookup"><span data-stu-id="c826b-256">Save the model to a file</span></span>

<span data-ttu-id="c826b-257">Jakmile se model splní, uložte ho do souboru, aby se předpovědi později nebo v jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c826b-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="c826b-258">Do metody `Evaluate` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c826b-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="c826b-259">V metodě `Evaluate` vytvořte metodu `SaveModelAsFile`.</span><span class="sxs-lookup"><span data-stu-id="c826b-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="c826b-260">Do metody `SaveModelAsFile` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c826b-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="c826b-261">Tento kód používá metodu [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) k serializaci a uložení výukového modelu jako souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="c826b-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="c826b-262">Nasazení a předpověď pomocí modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="c826b-263">Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `Evaluate`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="c826b-264">Vytvořte metodu `PredictIssue` hned za metodou `Evaluate` (a těsně před metodou `SaveModelAsFile`) pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c826b-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="c826b-265">Metoda `PredictIssue` provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c826b-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="c826b-266">Načte uložený model.</span><span class="sxs-lookup"><span data-stu-id="c826b-266">Loads the saved model</span></span>
* <span data-ttu-id="c826b-267">Vytvoří jeden problém testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="c826b-268">Odhadne oblast na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="c826b-269">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="c826b-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="c826b-270">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="c826b-270">Displays the predicted results.</span></span>

<span data-ttu-id="c826b-271">Načtěte uložený model do aplikace přidáním následujícího kódu do metody `PredictIssue`:</span><span class="sxs-lookup"><span data-stu-id="c826b-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

<span data-ttu-id="c826b-272">Přidáním problému GitHubu otestujete předpověď vyškolených modelů v metodě `Predict` vytvořením instance `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="c826b-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="c826b-273">Jak jste předtím pracovali, vytvořte instanci `PredictionEngine` s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c826b-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="c826b-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="c826b-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="c826b-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="c826b-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="c826b-276">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="c826b-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="c826b-277">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c826b-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="c826b-278">V této příručce najdete informace o [použití `PredictionEnginePool` v ASP.NET Core webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application) .</span><span class="sxs-lookup"><span data-stu-id="c826b-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="c826b-279">rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="c826b-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="c826b-280">Pomocí `PredictionEngine` předpovědět popisek GitHubu oblasti přidáním následujícího kódu do metody `PredictIssue` pro předpověď:</span><span class="sxs-lookup"><span data-stu-id="c826b-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="c826b-281">Použití načteného modelu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="c826b-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="c826b-282">Umožňuje zobrazit `Area`, aby se problém kategorizoval, a podle toho ho zařadí.</span><span class="sxs-lookup"><span data-stu-id="c826b-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="c826b-283">Pomocí následujícího kódu <xref:System.Console.WriteLine?displayProperty=nameWithType> vytvořte zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="c826b-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="c826b-284">Výsledky</span><span class="sxs-lookup"><span data-stu-id="c826b-284">Results</span></span>

<span data-ttu-id="c826b-285">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="c826b-285">Your results should be similar to the following.</span></span> <span data-ttu-id="c826b-286">V průběhu procesu kanálu se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="c826b-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="c826b-287">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="c826b-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="c826b-288">Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="c826b-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="c826b-289">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="c826b-289">Congratulations!</span></span> <span data-ttu-id="c826b-290">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď popisku oblasti pro problém GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c826b-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="c826b-291">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .</span><span class="sxs-lookup"><span data-stu-id="c826b-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c826b-292">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c826b-292">Next steps</span></span>

<span data-ttu-id="c826b-293">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="c826b-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c826b-294">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="c826b-294">Prepare your data</span></span>
> * <span data-ttu-id="c826b-295">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="c826b-295">Transform the data</span></span>
> * <span data-ttu-id="c826b-296">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-296">Train the model</span></span>
> * <span data-ttu-id="c826b-297">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-297">Evaluate the model</span></span>
> * <span data-ttu-id="c826b-298">Předpověď s vycvičeným modelem</span><span class="sxs-lookup"><span data-stu-id="c826b-298">Predict with the trained model</span></span>
> * <span data-ttu-id="c826b-299">Nasazení a předpověď pomocí načteného modelu</span><span class="sxs-lookup"><span data-stu-id="c826b-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="c826b-300">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="c826b-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c826b-301">Předpovídání tarifů taxislužby</span><span class="sxs-lookup"><span data-stu-id="c826b-301">Taxi Fare Predictor</span></span>](taxi-fare.md)
