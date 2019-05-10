---
title: Klasifikaci problémy s úložištěm GitHub - klasifikace víc tříd
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy Githubu pro jejich přiřazení k dané oblasti.
ms.date: 05/02/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a4122d0cdfe6531275fabf94743882a82f2a13c1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063527"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="7888d-103">Kurz: Použití ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy s úložištěm GitHub</span><span class="sxs-lookup"><span data-stu-id="7888d-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="7888d-104">Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru problém Githubu pro trénování modelu, který klasifikuje a predikuje popisek oblasti pro problém na Githubu prostřednictvím aplikace konzoly .NET Core using C# v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7888d-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="7888d-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="7888d-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7888d-106">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="7888d-106">Prepare your data</span></span>
> * <span data-ttu-id="7888d-107">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="7888d-107">Transform the data</span></span>
> * <span data-ttu-id="7888d-108">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-108">Train the model</span></span>
> * <span data-ttu-id="7888d-109">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-109">Evaluate the model</span></span>
> * <span data-ttu-id="7888d-110">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-110">Predict with the trained model</span></span>
> * <span data-ttu-id="7888d-111">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="7888d-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="7888d-112">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.</span><span class="sxs-lookup"><span data-stu-id="7888d-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7888d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7888d-113">Prerequisites</span></span>

* <span data-ttu-id="7888d-114">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7888d-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="7888d-115">[Githubu problémy s daty oddělenými tabulátory souboru (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="7888d-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="7888d-116">[Problémy Githubu testovací soubor oddělených tabulátory (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="7888d-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7888d-117">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="7888d-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="7888d-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="7888d-118">Create a project</span></span>

1. <span data-ttu-id="7888d-119">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7888d-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="7888d-120">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="7888d-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="7888d-121">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="7888d-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="7888d-122">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="7888d-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="7888d-123">V **název** textového pole zadejte "GitHubIssueClassification" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7888d-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="7888d-124">Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="7888d-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="7888d-125">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="7888d-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="7888d-126">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="7888d-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="7888d-127">Vytvořte adresář *modely* ve vašem projektu a uložit model:</span><span class="sxs-lookup"><span data-stu-id="7888d-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="7888d-128">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="7888d-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="7888d-129">Zadejte "Modely" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="7888d-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="7888d-130">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="7888d-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="7888d-131">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7888d-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7888d-132">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte **v 1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7888d-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="7888d-133">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="7888d-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="7888d-134">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="7888d-134">Prepare your data</span></span>

1. <span data-ttu-id="7888d-135">Stáhněte si [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka.</span><span class="sxs-lookup"><span data-stu-id="7888d-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="7888d-136">První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.</span><span class="sxs-lookup"><span data-stu-id="7888d-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="7888d-137">V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7888d-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="7888d-138">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="7888d-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="7888d-139">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="7888d-139">Create classes and define paths</span></span>

<span data-ttu-id="7888d-140">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="7888d-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="7888d-141">Vytvořte tři globální pole pro uložení cest k naposledy stažené soubory a globálních proměnných pro `MLContext`,`DataView`, a `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="7888d-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="7888d-142">`_trainDataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="7888d-143">`_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="7888d-144">`_modelPath` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="7888d-145">`_mlContext` je <xref:Microsoft.ML.MLContext> , která poskytuje kontext zpracování.</span><span class="sxs-lookup"><span data-stu-id="7888d-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="7888d-146">`_trainingDataView` je <xref:Microsoft.ML.IDataView> používají ke zpracování trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="7888d-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="7888d-147">`_predEngine` je <xref:Microsoft.ML.PredictionEngine%602> používá pro jeden předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7888d-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="7888d-148">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="7888d-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="7888d-149">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7888d-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="7888d-150">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="7888d-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="7888d-151">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="7888d-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="7888d-152">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="7888d-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="7888d-153">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7888d-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7888d-154">*GitHubIssueData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7888d-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="7888d-155">Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="7888d-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="7888d-156">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, možnosti *GitHubIssueData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="7888d-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="7888d-157">`label` Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="7888d-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="7888d-158">Identifikovanou `Features` jsou vstupy, poskytují model k predikci popisek.</span><span class="sxs-lookup"><span data-stu-id="7888d-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="7888d-159">Použití [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) k určení indexů zdrojových sloupců v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="7888d-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="7888d-160">`GitHubIssue` je třída vstupní datová sada a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="7888d-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="7888d-161">první sloupec `ID` (ID problému Githubu)</span><span class="sxs-lookup"><span data-stu-id="7888d-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="7888d-162">druhý sloupec `Area` (Předpověď pro školení)</span><span class="sxs-lookup"><span data-stu-id="7888d-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="7888d-163">třetí sloupec `Title` (název problému Githubu) je prvním `feature` používá pro predikci `Area`</span><span class="sxs-lookup"><span data-stu-id="7888d-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="7888d-164">čtvrtý sloupec `Description` tím dokončím `feature` používá pro predikci `Area`</span><span class="sxs-lookup"><span data-stu-id="7888d-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="7888d-165">`IssuePrediction` Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="7888d-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="7888d-166">Má jediný `string` (`Area`) a `PredictedLabel` `ColumnName` atribut.</span><span class="sxs-lookup"><span data-stu-id="7888d-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="7888d-167">`PredictedLabel` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="7888d-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="7888d-168">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="7888d-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="7888d-169">Všechny operace ML.NET spustit v [MLContext](xref:Microsoft.ML.MLContext) třídy.</span><span class="sxs-lookup"><span data-stu-id="7888d-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="7888d-170">Inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7888d-171">Je to podobné, koncepčně `DBContext` v `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="7888d-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="7888d-172">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="7888d-172">Initialize variables in Main</span></span>

<span data-ttu-id="7888d-173">Inicializovat `_mlContext` globální proměnnou s novou instanci třídy `MLContext` s náhodná počáteční hodnota (`seed: 0`) pro opakovatelné/deterministické výsledky napříč více školení.</span><span class="sxs-lookup"><span data-stu-id="7888d-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="7888d-174">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="7888d-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="7888d-175">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="7888d-175">Load the data</span></span>

<span data-ttu-id="7888d-176">Používá ML.NET [IDataView třídy](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob, jak popisují číselné nebo text tabulková data.</span><span class="sxs-lookup"><span data-stu-id="7888d-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="7888d-177">`IDataView` můžete načíst buď textové soubory nebo v reálném čase (například SQL databázi nebo soubory protokolů).</span><span class="sxs-lookup"><span data-stu-id="7888d-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="7888d-178">K inicializaci a načíst `_trainingDataView` globální proměnné, aby bylo možné používat pro kanál, přidejte následující kód za `mlContext` inicializace:</span><span class="sxs-lookup"><span data-stu-id="7888d-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="7888d-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru.</span><span class="sxs-lookup"><span data-stu-id="7888d-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="7888d-180">Přijímá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="7888d-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="7888d-181">Přidejte následující položky jako další řádek kódu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="7888d-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="7888d-182">`ProcessData` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="7888d-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="7888d-183">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="7888d-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="7888d-184">Vrátí kanálu zpracování.</span><span class="sxs-lookup"><span data-stu-id="7888d-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="7888d-185">Vytvořte `ProcessData` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="7888d-186">Extrakce funkce a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="7888d-186">Extract Features and transform the data</span></span>

<span data-ttu-id="7888d-187">Jak chcete předpovědět popisek oblasti Githubu `GitHubIssue`, použít [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody k transformaci `Area` sloupců na číselný typ klíče `Label` sloupec (formát přijal algoritmy klasifikace ) a přidejte ho jako nový sloupec datové sady:</span><span class="sxs-lookup"><span data-stu-id="7888d-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="7888d-188">Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` která transformuje text (`Title` a `Description`) sloupce jako číselné vektor pro každou volá `TitleFeaturized` a `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="7888d-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="7888d-189">Snadné pro oba sloupce pro přidání do kanálu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7888d-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="7888d-190">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="7888d-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="7888d-191">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="7888d-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="7888d-192">Připojte tuto transformaci na kanál s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7888d-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="7888d-193">V dalším kroku připojit <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pro ukládání do mezipaměti DataView, takže při iteraci přes data s využitím více než jednou mezipaměti může dosahovat vyšších výkonů, stejně jako u následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="7888d-194">Můžete snížit dobu výuky AppendCacheCheckpoint pro malé a střední datové sady.</span><span class="sxs-lookup"><span data-stu-id="7888d-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="7888d-195">Nepoužívejte ho (odebrat. AppendCacheCheckpoint()) při zpracování velmi velkých datových sad.</span><span class="sxs-lookup"><span data-stu-id="7888d-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="7888d-196">Kanál na konci vrátit `ProcessData` metody.</span><span class="sxs-lookup"><span data-stu-id="7888d-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="7888d-197">Tento krok zpracovává předběžného zpracování a snadné.</span><span class="sxs-lookup"><span data-stu-id="7888d-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="7888d-198">Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.</span><span class="sxs-lookup"><span data-stu-id="7888d-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="7888d-199">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-199">Build and train the model</span></span>

<span data-ttu-id="7888d-200">Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="7888d-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="7888d-201">`BuildAndTrainModel` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="7888d-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="7888d-202">Vytvoří třídu algoritmus školení.</span><span class="sxs-lookup"><span data-stu-id="7888d-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="7888d-203">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-203">Trains the model.</span></span>
* <span data-ttu-id="7888d-204">Předpovídá oblasti založené na trénovací data.</span><span class="sxs-lookup"><span data-stu-id="7888d-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="7888d-205">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-205">Returns the model.</span></span>

<span data-ttu-id="7888d-206">Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="7888d-207">O úloze klasifikace</span><span class="sxs-lookup"><span data-stu-id="7888d-207">About the classification task</span></span>

<span data-ttu-id="7888d-208">Klasifikace je úloha strojového učení, který používá data **určit** kategorie, typ nebo třída položky nebo řádek dat a je často jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="7888d-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="7888d-209">Binární soubor: buď A a B.</span><span class="sxs-lookup"><span data-stu-id="7888d-209">Binary: either A or B.</span></span>
* <span data-ttu-id="7888d-210">Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.</span><span class="sxs-lookup"><span data-stu-id="7888d-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="7888d-211">Pro tento typ problému používejte klasifikaci Multiclass učení algoritmu, protože predikci kategorii problému může být jeden z více kategorií (multiclass) místo jen dvou (binární).</span><span class="sxs-lookup"><span data-stu-id="7888d-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="7888d-212">Připojení algoritmu strojového učení do definice transformace dat přidáním následujícího kódu jako první řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="7888d-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="7888d-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je algoritmus školení klasifikace víc tříd.</span><span class="sxs-lookup"><span data-stu-id="7888d-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="7888d-214">To se připojí `pipeline` a přijímá natrénuje `Title` a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="7888d-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="7888d-215">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-215">Train the model</span></span>

<span data-ttu-id="7888d-216">Přizpůsobit modelu, který má `splitTrainSet` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="7888d-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="7888d-217">`Fit()`Metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="7888d-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="7888d-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je vhodné rozhraní API, což vám umožní předat a pak proveďte predikcí na jednu instanci data.</span><span class="sxs-lookup"><span data-stu-id="7888d-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="7888d-219">Přidat jako na následující řádek `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="7888d-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="7888d-220">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-220">Predict with the trained model</span></span>

<span data-ttu-id="7888d-221">Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="7888d-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="7888d-222">Použití [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce díky predikcí na jednom řádku dat:</span><span class="sxs-lookup"><span data-stu-id="7888d-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="7888d-223">Pomocí modelu: předpověď výsledků</span><span class="sxs-lookup"><span data-stu-id="7888d-223">Using the model: prediction results</span></span>

<span data-ttu-id="7888d-224">Zobrazení `GitHubIssue` a odpovídající `Area` popisek predikcí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="7888d-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="7888d-225">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="7888d-226">Vrátí že model se trénuje má použít pro hodnocení</span><span class="sxs-lookup"><span data-stu-id="7888d-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="7888d-227">Model na konci vrátit `BuildAndTrainModel` metody.</span><span class="sxs-lookup"><span data-stu-id="7888d-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="7888d-228">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-228">Evaluate the model</span></span>

<span data-ttu-id="7888d-229">Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování.</span><span class="sxs-lookup"><span data-stu-id="7888d-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="7888d-230">V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="7888d-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="7888d-231">Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="7888d-232">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="7888d-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="7888d-233">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="7888d-233">Loads the test dataset.</span></span>
* <span data-ttu-id="7888d-234">Vytvoří víc tříd Chyba při vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="7888d-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="7888d-235">Vyhodnotí modelu a vytvoření metriky.</span><span class="sxs-lookup"><span data-stu-id="7888d-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="7888d-236">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="7888d-236">Displays the metrics.</span></span>

<span data-ttu-id="7888d-237">Přidejte volání do nové metody z `Main` metody, v rámci `BuildAndTrainModel` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="7888d-238">Stejně jako dříve trénovací datové sady, načíst datovou sadu testů tak, že přidáte následující kód, který `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="7888d-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="7888d-239">[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) metoda vypočítá metrik kvality pro model pomocí zadaného objektu dataset.</span><span class="sxs-lookup"><span data-stu-id="7888d-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="7888d-240">Vrátí <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení klasifikace víc tříd.</span><span class="sxs-lookup"><span data-stu-id="7888d-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="7888d-241">Pokud chcete zobrazit metriky pro určení kvality tohoto modelu, musíte je získat první.</span><span class="sxs-lookup"><span data-stu-id="7888d-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="7888d-242">Použití Všimněte si, že [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda služby machine learning `_trainedModel` globální proměnné ( [ITransformer](xref:Microsoft.ML.ITransformer)) k zadání funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7888d-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="7888d-243">Přidejte následující kód, který `Evaluate` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="7888d-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="7888d-244">Klasifikace víc tříd, se vyhodnotí následující metriky:</span><span class="sxs-lookup"><span data-stu-id="7888d-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="7888d-245">Micro přesnost – každá dvojice ukázkovou třídu přispívá stejně metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="7888d-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="7888d-246">Chcete, aby Micro přesnost, aby byly co nejblíže 1 nejvíce.</span><span class="sxs-lookup"><span data-stu-id="7888d-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="7888d-247">Přesnost – makro – každá třída přispívá stejně metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="7888d-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="7888d-248">Třídy minority disponují stejnou váhu jako větší třídy.</span><span class="sxs-lookup"><span data-stu-id="7888d-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="7888d-249">Chcete, aby byly co nejblíže 1 nejvíce přesnost – makro.</span><span class="sxs-lookup"><span data-stu-id="7888d-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="7888d-250">Protokol ztrát – naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="7888d-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="7888d-251">Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="7888d-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="7888d-252">Od ztráty protokolu snížení - [-inf, 100], kde 100 je ideální předpovědi a 0 označuje střední předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7888d-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="7888d-253">Chcete, aby omezení ztráty protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="7888d-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="7888d-254">Zobrazení metrik pro ověření modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="7888d-255">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7888d-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="7888d-256">Nasazení a predikce v modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-256">Deploy and Predict with a model</span></span>

<span data-ttu-id="7888d-257">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-257">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="7888d-258">Vytvořit `PredictIssue` metoda, hned za `Evaluate` – metoda (a těsně před `SaveModelAsFile` metoda), pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-258">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="7888d-259">`PredictIssue` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="7888d-259">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="7888d-260">Vytvoří jen jeden problém testovací data.</span><span class="sxs-lookup"><span data-stu-id="7888d-260">Creates a single issue of test data.</span></span>
* <span data-ttu-id="7888d-261">Předpovídá oblasti na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="7888d-261">Predicts Area based on test data.</span></span>
* <span data-ttu-id="7888d-262">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="7888d-262">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="7888d-263">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="7888d-263">Displays the predicted results.</span></span>

<span data-ttu-id="7888d-264">Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="7888d-264">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="7888d-265">Stejně jako dříve, vytvořit `PredictionEngine` instance s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7888d-265">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="7888d-266">Použití `PredictionEngine` předpovědět popisek oblasti Githubu přidáním následujícího kódu `PredictIssue` metodu pro předpověď:</span><span class="sxs-lookup"><span data-stu-id="7888d-266">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="7888d-267">Použití načíst model pro předpověď</span><span class="sxs-lookup"><span data-stu-id="7888d-267">Using the loaded model for prediction</span></span>

<span data-ttu-id="7888d-268">Zobrazení `Area` kategorizace problém a příslušně na ně reagovat na něj.</span><span class="sxs-lookup"><span data-stu-id="7888d-268">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="7888d-269">Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:</span><span class="sxs-lookup"><span data-stu-id="7888d-269">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="7888d-270">Výsledky</span><span class="sxs-lookup"><span data-stu-id="7888d-270">Results</span></span>

<span data-ttu-id="7888d-271">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="7888d-271">Your results should be similar to the following.</span></span> <span data-ttu-id="7888d-272">Při zpracování kanálu zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="7888d-272">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="7888d-273">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7888d-273">You may see warnings, or processing messages.</span></span> <span data-ttu-id="7888d-274">Tyto zprávy se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="7888d-274">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="7888d-275">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="7888d-275">Congratulations!</span></span> <span data-ttu-id="7888d-276">Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat popisek oblasti pro problém na Githubu.</span><span class="sxs-lookup"><span data-stu-id="7888d-276">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="7888d-277">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.</span><span class="sxs-lookup"><span data-stu-id="7888d-277">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7888d-278">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7888d-278">Next steps</span></span>

<span data-ttu-id="7888d-279">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="7888d-279">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7888d-280">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="7888d-280">Prepare your data</span></span>
> * <span data-ttu-id="7888d-281">Transformace dat</span><span class="sxs-lookup"><span data-stu-id="7888d-281">Transform the data</span></span>
> * <span data-ttu-id="7888d-282">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-282">Train the model</span></span>
> * <span data-ttu-id="7888d-283">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-283">Evaluate the model</span></span>
> * <span data-ttu-id="7888d-284">Predikce v trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="7888d-284">Predict with the trained model</span></span>
> * <span data-ttu-id="7888d-285">Nasazení a predikce v načíst model</span><span class="sxs-lookup"><span data-stu-id="7888d-285">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="7888d-286">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="7888d-286">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7888d-287">Prediktivní tarif taxislužby města</span><span class="sxs-lookup"><span data-stu-id="7888d-287">Taxi Fare Predictor</span></span>](taxi-fare.md)
