---
title: Cluster květin iris pomocí clusteringu learner - ML.NET
description: Zjistěte, jak použít ve scénáři clusteringu ML.NET
author: pkulikov
ms.author: johalex
ms.date: 01/11/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 03a584095badf4b1c3318833f6e67367f27b32ba
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583716"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="b39f9-103">Kurz: Cluster květin iris pomocí clusteringu learner ML.NET</span><span class="sxs-lookup"><span data-stu-id="b39f9-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="b39f9-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="b39f9-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b39f9-105">Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b39f9-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b39f9-106">Tento kurz ukazuje, jak použít ML.NET k sestavení [clusteringový model](../resources/tasks.md#clustering) pro [datovou sadu iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="b39f9-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="b39f9-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b39f9-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b39f9-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b39f9-108">Understand the problem</span></span>
> - <span data-ttu-id="b39f9-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="b39f9-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="b39f9-110">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b39f9-110">Prepare the data</span></span>
> - <span data-ttu-id="b39f9-111">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="b39f9-111">Load and transform the data</span></span>
> - <span data-ttu-id="b39f9-112">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="b39f9-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="b39f9-113">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b39f9-113">Train the model</span></span>
> - <span data-ttu-id="b39f9-114">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="b39f9-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b39f9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b39f9-115">Prerequisites</span></span>

- <span data-ttu-id="b39f9-116">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b39f9-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b39f9-117">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b39f9-117">Understand the problem</span></span>

<span data-ttu-id="b39f9-118">Tento problém je o rozdělení sadu iris květin v různých skupinách na základě funkcí květinu.</span><span class="sxs-lookup"><span data-stu-id="b39f9-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="b39f9-119">Tyto funkce jsou délku a šířku sepal a délku a šířku petal.</span><span class="sxs-lookup"><span data-stu-id="b39f9-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="b39f9-120">Pro účely tohoto kurzu předpokládá, že typ jednotlivých květinu neznámý.</span><span class="sxs-lookup"><span data-stu-id="b39f9-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="b39f9-121">Chcete seznámit se se strukturou datové sady z funkcí a předpovědět, jak zapadá data instance této struktury.</span><span class="sxs-lookup"><span data-stu-id="b39f9-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="b39f9-122">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="b39f9-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="b39f9-123">Jak si nejste jisti, do které skupiny patří každý květinu, zvolte [nastavenou možnost bez dohledu strojového učení](../resources/glossary.md#unsupervised-machine-learning) úloh.</span><span class="sxs-lookup"><span data-stu-id="b39f9-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="b39f9-124">Pokud chcete rozdělit datové sady ve skupinách tak, že prvky ve stejné skupině jsou u jiného než více podobné těm v jiných skupinách, použijte [clustering](../resources/tasks.md#clustering) machine learning úloh.</span><span class="sxs-lookup"><span data-stu-id="b39f9-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b39f9-125">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="b39f9-125">Create a console application</span></span>

1. <span data-ttu-id="b39f9-126">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b39f9-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="b39f9-127">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="b39f9-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b39f9-128">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="b39f9-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="b39f9-129">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="b39f9-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b39f9-130">V **název** textového pole zadejte "IrisFlowerClustering" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b39f9-130">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="b39f9-131">Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:</span><span class="sxs-lookup"><span data-stu-id="b39f9-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="b39f9-132">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="b39f9-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b39f9-133">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="b39f9-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="b39f9-134">Nainstalujte **Microsoft.ML** balíček NuGet:</span><span class="sxs-lookup"><span data-stu-id="b39f9-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="b39f9-135">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b39f9-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b39f9-136">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b39f9-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b39f9-137">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="b39f9-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="b39f9-138">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b39f9-138">Prepare the data</span></span>

1. <span data-ttu-id="b39f9-139">Stáhněte si [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dat nastavit a uložit ho. tím *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="b39f9-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="b39f9-140">Další informace o datové sady iris najdete v článku [datovou sadu Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) stránky Wikipedia a [datovou sadu Iris](https://archive.ics.uci.edu/ml/datasets/Iris) stránku, což je zdrojové datové sady.</span><span class="sxs-lookup"><span data-stu-id="b39f9-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="b39f9-141">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *iris.data* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b39f9-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="b39f9-142">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="b39f9-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="b39f9-143">*Iris.data* soubor obsahuje pět sloupců, které představují:</span><span class="sxs-lookup"><span data-stu-id="b39f9-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="b39f9-144">sepal length v cm</span><span class="sxs-lookup"><span data-stu-id="b39f9-144">sepal length in centimetres</span></span>
- <span data-ttu-id="b39f9-145">sepal width v cm</span><span class="sxs-lookup"><span data-stu-id="b39f9-145">sepal width in centimetres</span></span>
- <span data-ttu-id="b39f9-146">petal length v cm</span><span class="sxs-lookup"><span data-stu-id="b39f9-146">petal length in centimetres</span></span>
- <span data-ttu-id="b39f9-147">petal width v cm</span><span class="sxs-lookup"><span data-stu-id="b39f9-147">petal width in centimetres</span></span>
- <span data-ttu-id="b39f9-148">Typ květinu iris</span><span class="sxs-lookup"><span data-stu-id="b39f9-148">type of iris flower</span></span>

<span data-ttu-id="b39f9-149">Pro účely clusteringu příkladu v tomto kurzu ignoruje posledního sloupce.</span><span class="sxs-lookup"><span data-stu-id="b39f9-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="b39f9-150">Vytvoření datových tříd</span><span class="sxs-lookup"><span data-stu-id="b39f9-150">Create data classes</span></span>

<span data-ttu-id="b39f9-151">Vytvoření třídy pro vstupní data a předpovědí:</span><span class="sxs-lookup"><span data-stu-id="b39f9-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b39f9-152">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="b39f9-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b39f9-153">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b39f9-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="b39f9-154">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b39f9-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b39f9-155">Přidejte následující `using` směrnice do nového souboru:</span><span class="sxs-lookup"><span data-stu-id="b39f9-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="b39f9-156">Odeberte stávající definice třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, možnosti *IrisData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b39f9-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="b39f9-157">`IrisData` je třída vstupní data a obsahuje definice pro jednotlivé funkce z datové sady.</span><span class="sxs-lookup"><span data-stu-id="b39f9-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="b39f9-158">Použití [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) atributy indexů zdrojových sloupců v souboru datové sady.</span><span class="sxs-lookup"><span data-stu-id="b39f9-158">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="b39f9-159">`ClusterPrediction` Třída reprezentuje výstup model clusteringu u `IrisData` instance.</span><span class="sxs-lookup"><span data-stu-id="b39f9-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="b39f9-160">Použití [Názevsloupce](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut pro vytvoření vazby `PredictedClusterId` a `Distances` polím **PredictedLabel** a **skóre** sloupce v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b39f9-160">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="b39f9-161">V případě clusteru úloh tyto sloupce mají následující význam:</span><span class="sxs-lookup"><span data-stu-id="b39f9-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="b39f9-162">**PredictedLabel** sloupec obsahuje ID předpokládané clusteru.</span><span class="sxs-lookup"><span data-stu-id="b39f9-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="b39f9-163">**Skóre** sloupec obsahuje pole s kvadratických Euclidean vzdálenosti se centroids clusteru.</span><span class="sxs-lookup"><span data-stu-id="b39f9-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="b39f9-164">Délka pole je rovna počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="b39f9-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="b39f9-165">Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.</span><span class="sxs-lookup"><span data-stu-id="b39f9-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="b39f9-166">Definovat cesty k datům a model</span><span class="sxs-lookup"><span data-stu-id="b39f9-166">Define data and model paths</span></span>

<span data-ttu-id="b39f9-167">Přejděte zpět *Program.cs* a přidejte dvě pole pro uložení cesty k souboru datové sady a do souboru uložit model:</span><span class="sxs-lookup"><span data-stu-id="b39f9-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="b39f9-168">`_dataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="b39f9-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="b39f9-169">`_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="b39f9-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="b39f9-170">Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="b39f9-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="b39f9-171">Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b39f9-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="b39f9-172">Vytvoří kontext ML</span><span class="sxs-lookup"><span data-stu-id="b39f9-172">Create ML context</span></span>

<span data-ttu-id="b39f9-173">Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b39f9-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="b39f9-174">V `Main` metoda, nahraďte `Console.WriteLine("Hello World!");` řádek s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b39f9-174">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="b39f9-175"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Třída představuje prostředí machine learning a poskytuje mechanismus pro protokolování a vstupních bodů pro načítání dat, trénování modelu, predikcí a další úlohy.</span><span class="sxs-lookup"><span data-stu-id="b39f9-175">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="b39f9-176">Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b39f9-176">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="b39f9-177">Nastavení načítání dat</span><span class="sxs-lookup"><span data-stu-id="b39f9-177">Setup data loading</span></span>

<span data-ttu-id="b39f9-178">Přidejte následující kód, který `Main` metoda nastavit způsob, jak načíst data:</span><span class="sxs-lookup"><span data-stu-id="b39f9-178">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

<span data-ttu-id="b39f9-179">Použití [obecný `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%60%601(Microsoft.ML.DataOperationsCatalog,System.Boolean,System.Char,System.Boolean,System.Boolean,System.Boolean)) metodu pro odvození schématu datové sady z `IrisData` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="b39f9-179">Use the [generic `CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%60%601(Microsoft.ML.DataOperationsCatalog,System.Boolean,System.Char,System.Boolean,System.Boolean,System.Boolean)) method to infer the dataset schema from the `IrisData` class definition.</span></span>

<span data-ttu-id="b39f9-180">Použití vytvořena instance <xref:Microsoft.ML.Data.TextLoader> instance má vytvořit <xref:Microsoft.Data.DataView.IDataView> instanci, která představuje zdroj dat pro trénovací datové sady:</span><span class="sxs-lookup"><span data-stu-id="b39f9-180">Use instantiated <xref:Microsoft.ML.Data.TextLoader> instance to create an <xref:Microsoft.Data.DataView.IDataView> instance, which represents the data source for the training data set:</span></span>

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="b39f9-181">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="b39f9-181">Create a learning pipeline</span></span>

<span data-ttu-id="b39f9-182">Pro účely tohoto kurzu kanál učení clusteringu úkolu se skládá z následujících dvou kroků:</span><span class="sxs-lookup"><span data-stu-id="b39f9-182">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="b39f9-183">zřetězit načíst sloupce do jednoho **funkce** sloupec, který používá clustering trainer;</span><span class="sxs-lookup"><span data-stu-id="b39f9-183">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="b39f9-184">použít <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer k natrénování modelu s použitím s kB – znamená, že ++ clustering algoritmus.</span><span class="sxs-lookup"><span data-stu-id="b39f9-184">use a <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="b39f9-185">Přidejte následující kód, který `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b39f9-185">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="b39f9-186">Kód určuje, že datová sada by měla lze rozdělit tři clustery.</span><span class="sxs-lookup"><span data-stu-id="b39f9-186">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="b39f9-187">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b39f9-187">Train the model</span></span>

<span data-ttu-id="b39f9-188">Kroky přidání v předchozích částech připravili kanálu pro školení, ale, že byly provedeny žádné.</span><span class="sxs-lookup"><span data-stu-id="b39f9-188">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="b39f9-189">Přidejte následující řádek, který `Main` metodu za účelem načtení dat a trénování modelu:</span><span class="sxs-lookup"><span data-stu-id="b39f9-189">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="b39f9-190">Uložit model</span><span class="sxs-lookup"><span data-stu-id="b39f9-190">Save the model</span></span>

<span data-ttu-id="b39f9-191">V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="b39f9-191">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="b39f9-192">Uložit model do souboru .zip, přidejte následující kód, který `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b39f9-192">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b39f9-193">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="b39f9-193">Use the model for predictions</span></span>

<span data-ttu-id="b39f9-194">K následné predikci, použijte <xref:Microsoft.ML.PredictionEngine%602> třídu, která přebírá instance typu vstupním kanálem transformer a vytváří instance typu výstupu.</span><span class="sxs-lookup"><span data-stu-id="b39f9-194">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="b39f9-195">Přidejte následující řádek, který `Main` metodu pro vytvoření instance této třídy:</span><span class="sxs-lookup"><span data-stu-id="b39f9-195">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="b39f9-196">Vytvořte `TestIrisData` třídy pro uložení testovací data instancí:</span><span class="sxs-lookup"><span data-stu-id="b39f9-196">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="b39f9-197">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="b39f9-197">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b39f9-198">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b39f9-198">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="b39f9-199">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b39f9-199">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b39f9-200">Upravte třídu pro statické stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b39f9-200">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="b39f9-201">Tento kurz představuje jednu instanci data iris v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="b39f9-201">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="b39f9-202">Můžete přidat další scénáře můžete experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="b39f9-202">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="b39f9-203">Přidejte následující kód do `TestIrisData` třídy:</span><span class="sxs-lookup"><span data-stu-id="b39f9-203">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="b39f9-204">Chcete-li zjistit, ke kterému zadaná položka patří do clusteru, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b39f9-204">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="b39f9-205">Spusťte program clusteru, které obsahuje instanci zadaného data a kvadratických vzdálenosti směrem dovnitř od této instance na centroids clusteru.</span><span class="sxs-lookup"><span data-stu-id="b39f9-205">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="b39f9-206">Výsledky by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="b39f9-206">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="b39f9-207">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="b39f9-207">Congratulations!</span></span> <span data-ttu-id="b39f9-208">Teď jste úspěšně sestaven služby machine learning model iris clustering a použít ho k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="b39f9-208">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="b39f9-209">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="b39f9-209">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b39f9-210">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b39f9-210">Next steps</span></span>

<span data-ttu-id="b39f9-211">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="b39f9-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b39f9-212">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="b39f9-212">Understand the problem</span></span>
> - <span data-ttu-id="b39f9-213">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="b39f9-213">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="b39f9-214">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b39f9-214">Prepare the data</span></span>
> - <span data-ttu-id="b39f9-215">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="b39f9-215">Load and transform the data</span></span>
> - <span data-ttu-id="b39f9-216">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="b39f9-216">Choose a learning algorithm</span></span>
> - <span data-ttu-id="b39f9-217">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b39f9-217">Train the model</span></span>
> - <span data-ttu-id="b39f9-218">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="b39f9-218">Use the model for predictions</span></span>

<span data-ttu-id="b39f9-219">Přečtěte si našeho úložiště GitHub, pokračujte ve čtení a najít další ukázky.</span><span class="sxs-lookup"><span data-stu-id="b39f9-219">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b39f9-220">DotNet/machinelearning úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="b39f9-220">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
