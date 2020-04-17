---
title: 'Výuka: Kategorizovat iris květiny - k-znamená shlukování'
description: Naučte se používat ML.NET ve scénáři clusteringu
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fe9c3eb1313fbacf512710f6872c543dca281b17
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607425"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="52ed0-103">Kurz: Kategorizovat iris květiny pomocí k-prostředky shlukování s ML.NET</span><span class="sxs-lookup"><span data-stu-id="52ed0-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="52ed0-104">Tento kurz ukazuje, jak použít ML.NET k vytvoření [modelu clusteringu](../resources/tasks.md#clustering) pro [sadu dat květin iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="52ed0-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="52ed0-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="52ed0-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="52ed0-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="52ed0-106">Understand the problem</span></span>
> - <span data-ttu-id="52ed0-107">Výběr příslušného úkolu strojového učení</span><span class="sxs-lookup"><span data-stu-id="52ed0-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="52ed0-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-108">Prepare the data</span></span>
> - <span data-ttu-id="52ed0-109">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-109">Load and transform the data</span></span>
> - <span data-ttu-id="52ed0-110">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="52ed0-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="52ed0-111">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="52ed0-111">Train the model</span></span>
> - <span data-ttu-id="52ed0-112">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="52ed0-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52ed0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52ed0-113">Prerequisites</span></span>

- <span data-ttu-id="52ed0-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="52ed0-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="52ed0-115">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="52ed0-115">Understand the problem</span></span>

<span data-ttu-id="52ed0-116">Tento problém je o rozdělení souboru iris květů v různých skupinách na základě květinových prvků.</span><span class="sxs-lookup"><span data-stu-id="52ed0-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="52ed0-117">Tyto rysy jsou délka a šířka sepal a délka a šířka okvětního lístku.</span><span class="sxs-lookup"><span data-stu-id="52ed0-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="52ed0-118">V tomto kurzu předpokládejme, že typ každé květiny není znám.</span><span class="sxs-lookup"><span data-stu-id="52ed0-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="52ed0-119">Chcete se naučit strukturu sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.</span><span class="sxs-lookup"><span data-stu-id="52ed0-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="52ed0-120">Výběr příslušného úkolu strojového učení</span><span class="sxs-lookup"><span data-stu-id="52ed0-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="52ed0-121">Vzhledem k tomu, že nevíte, do které skupiny každá květina patří, zvolíte úkol [strojového učení bez dozoru.](../resources/glossary.md#unsupervised-machine-learning)</span><span class="sxs-lookup"><span data-stu-id="52ed0-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="52ed0-122">Chcete-li rozdělit sadu dat do skupin tak, aby prvky ve stejné skupině byly navzájem více podobné než prvky v jiných skupinách, použijte úlohu strojového učení [clusteringu.](../resources/tasks.md#clustering)</span><span class="sxs-lookup"><span data-stu-id="52ed0-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="52ed0-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="52ed0-123">Create a console application</span></span>

1. <span data-ttu-id="52ed0-124">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52ed0-124">Open Visual Studio.</span></span> <span data-ttu-id="52ed0-125">Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="52ed0-126">V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="52ed0-127">Pak vyberte šablonu projektu **Konzola Aplikace (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="52ed0-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="52ed0-128">Do textového pole **Název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="52ed0-129">Vytvořte adresář s názvem *Data* v projektu pro uložení datové sady a souborů modelů:</span><span class="sxs-lookup"><span data-stu-id="52ed0-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="52ed0-130">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="52ed0-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="52ed0-131">Zadejte "Data" a stiskněte enter.</span><span class="sxs-lookup"><span data-stu-id="52ed0-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="52ed0-132">Nainstalujte **balíček Microsoft.ML** NuGet:</span><span class="sxs-lookup"><span data-stu-id="52ed0-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="52ed0-133">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="52ed0-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="52ed0-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet,** vyhledejte **Microsoft.ML** a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="52ed0-135">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="52ed0-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="52ed0-136">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-136">Prepare the data</span></span>

1. <span data-ttu-id="52ed0-137">Stáhněte si datovou sadu [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *Data,* kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="52ed0-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="52ed0-138">Další informace o datové sadě duhovky naleznete na stránce [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia a na stránce Iris Data [Set,](http://archive.ics.uci.edu/ml/datasets/Iris) která je zdrojem datové sady.</span><span class="sxs-lookup"><span data-stu-id="52ed0-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="52ed0-139">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *iris.data* a vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="52ed0-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="52ed0-140">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="52ed0-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="52ed0-141">Datový soubor *iris.data* obsahuje pět sloupců, které představují:</span><span class="sxs-lookup"><span data-stu-id="52ed0-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="52ed0-142">sepal délka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="52ed0-142">sepal length in centimeters</span></span>
- <span data-ttu-id="52ed0-143">šířka sepalu v centimetrech</span><span class="sxs-lookup"><span data-stu-id="52ed0-143">sepal width in centimeters</span></span>
- <span data-ttu-id="52ed0-144">délka okvětního lístku v centimetrech</span><span class="sxs-lookup"><span data-stu-id="52ed0-144">petal length in centimeters</span></span>
- <span data-ttu-id="52ed0-145">šířka okvětních plodů v centimetrech</span><span class="sxs-lookup"><span data-stu-id="52ed0-145">petal width in centimeters</span></span>
- <span data-ttu-id="52ed0-146">typ iris květu</span><span class="sxs-lookup"><span data-stu-id="52ed0-146">type of iris flower</span></span>

<span data-ttu-id="52ed0-147">V zájmu clustering příkladu tohoto kurzu ignoruje poslední sloupec.</span><span class="sxs-lookup"><span data-stu-id="52ed0-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="52ed0-148">Vytvoření tříd dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-148">Create data classes</span></span>

<span data-ttu-id="52ed0-149">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="52ed0-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="52ed0-150">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="52ed0-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="52ed0-151">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="52ed0-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="52ed0-152">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="52ed0-153">Do nového souboru přidejte následující `using` direktivu:</span><span class="sxs-lookup"><span data-stu-id="52ed0-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="52ed0-154">Odeberte existující definici třídy a přidejte `IrisData` `ClusterPrediction`následující kód, který definuje třídy a , do *souboru IrisData.cs:*</span><span class="sxs-lookup"><span data-stu-id="52ed0-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="52ed0-155">`IrisData`je třída vstupních dat a má definice pro každou funkci ze sady dat.</span><span class="sxs-lookup"><span data-stu-id="52ed0-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="52ed0-156">Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.</span><span class="sxs-lookup"><span data-stu-id="52ed0-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="52ed0-157">Třída `ClusterPrediction` představuje výstup clusteringmodelu aplikovaného na instanci. `IrisData`</span><span class="sxs-lookup"><span data-stu-id="52ed0-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="52ed0-158">Pomocí atributu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) `PredictedClusterId` můžete `Distances` svázat pole a se sloupci **PredictedLabel** a **Score.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="52ed0-159">V případě clustering úlohy tyto sloupce mají následující význam:</span><span class="sxs-lookup"><span data-stu-id="52ed0-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="52ed0-160">**Sloupec PredictedLabel** obsahuje ID předpokládaného clusteru.</span><span class="sxs-lookup"><span data-stu-id="52ed0-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="52ed0-161">**Sloupec Notscore** obsahuje pole se kvadratými euklidovskými vzdálenostmi od centroidů kupy.</span><span class="sxs-lookup"><span data-stu-id="52ed0-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="52ed0-162">Délka pole se rovná počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="52ed0-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="52ed0-163">Použijte `float` typ k reprezentaci hodnot s plovoucí desetinnou desetinnou třídou vstupních dat a predikcí.</span><span class="sxs-lookup"><span data-stu-id="52ed0-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="52ed0-164">Definování dat a cest modelu</span><span class="sxs-lookup"><span data-stu-id="52ed0-164">Define data and model paths</span></span>

<span data-ttu-id="52ed0-165">Vraťte se do *Program.cs* souboru a přidejte dvě pole pro uložení cest k souboru sady dat a k souboru pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="52ed0-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="52ed0-166">`_dataPath`obsahuje cestu k souboru se sadou dat použitou k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="52ed0-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="52ed0-167">`_modelPath`obsahuje cestu k souboru, kde je uložen trénovaný model.</span><span class="sxs-lookup"><span data-stu-id="52ed0-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="52ed0-168">Chcete-li zadat tyto `Main` cesty, přidejte přímo nad metodu následující kód:</span><span class="sxs-lookup"><span data-stu-id="52ed0-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

<span data-ttu-id="52ed0-169">Chcete-li zkompilovat předchozí `using` kód, přidejte následující direktivy v horní části *souboru Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="52ed0-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="52ed0-170">Vytvořit kontext ML</span><span class="sxs-lookup"><span data-stu-id="52ed0-170">Create ML context</span></span>

<span data-ttu-id="52ed0-171">Do horní `using` části *Program.cs* souboru přidejte následující další direktivy:</span><span class="sxs-lookup"><span data-stu-id="52ed0-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="52ed0-172">V `Main` metodě nahraďte `Console.WriteLine("Hello World!");` řádek následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="52ed0-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="52ed0-173">Třída <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelu, předpověď a další úkoly.</span><span class="sxs-lookup"><span data-stu-id="52ed0-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="52ed0-174">To je srovnatelné koncepčně s použitím `DbContext` v entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="52ed0-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="52ed0-175">Nastavení načítání dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-175">Set up data loading</span></span>

<span data-ttu-id="52ed0-176">Přidejte do `Main` metody následující kód pro nastavení způsobu načítání dat:</span><span class="sxs-lookup"><span data-stu-id="52ed0-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="52ed0-177">Metoda [ `MLContext.Data.LoadFromTextFile` obecného rozšíření](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady `IrisData` z zadaného typu a vrátí, <xref:Microsoft.ML.IDataView> které lze použít jako vstup pro transformátory.</span><span class="sxs-lookup"><span data-stu-id="52ed0-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="52ed0-178">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="52ed0-178">Create a learning pipeline</span></span>

<span data-ttu-id="52ed0-179">V tomto kurzu učení kanálu clustering úlohy se skládá ze dvou následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="52ed0-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="52ed0-180">zřetězit načtené sloupce do jednoho sloupce **Funkce,** který používá shlukovací trenér;</span><span class="sxs-lookup"><span data-stu-id="52ed0-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="52ed0-181">pomocí <xref:Microsoft.ML.Trainers.KMeansTrainer> trenéra trénování modelu pomocí k-prostředky++ clustering algoritmus.</span><span class="sxs-lookup"><span data-stu-id="52ed0-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="52ed0-182">Do metody `Main` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="52ed0-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="52ed0-183">Kód určuje, že sada dat by měla být rozdělena do tří clusterů.</span><span class="sxs-lookup"><span data-stu-id="52ed0-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="52ed0-184">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="52ed0-184">Train the model</span></span>

<span data-ttu-id="52ed0-185">Kroky přidané v předchozích částech připravily kanál pro školení, ale žádný nebyl proveden.</span><span class="sxs-lookup"><span data-stu-id="52ed0-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="52ed0-186">Přidejte k metodě `Main` následující řádek pro načtení dat a trénování modelu:</span><span class="sxs-lookup"><span data-stu-id="52ed0-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="52ed0-187">Uložení modelu</span><span class="sxs-lookup"><span data-stu-id="52ed0-187">Save the model</span></span>

<span data-ttu-id="52ed0-188">V tomto okamžiku máte model, který lze integrovat do některé z existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="52ed0-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="52ed0-189">Chcete-li model uložit do souboru ZIP, `Main` přidejte k metodě následující kód:</span><span class="sxs-lookup"><span data-stu-id="52ed0-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="52ed0-190">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="52ed0-190">Use the model for predictions</span></span>

<span data-ttu-id="52ed0-191">Chcete-li předpovědi, <xref:Microsoft.ML.PredictionEngine%602> použijte třídu, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance typu výstupu.</span><span class="sxs-lookup"><span data-stu-id="52ed0-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="52ed0-192">Přidejte k metodě `Main` následující řádek pro vytvoření instance této třídy:</span><span class="sxs-lookup"><span data-stu-id="52ed0-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="52ed0-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="52ed0-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="52ed0-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="52ed0-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="52ed0-195">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="52ed0-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="52ed0-196">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ed0-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="52ed0-197">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="52ed0-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="52ed0-198">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="52ed0-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="52ed0-199">Vytvořte `TestIrisData` třídu pro testování testovacích dat instance:</span><span class="sxs-lookup"><span data-stu-id="52ed0-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="52ed0-200">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="52ed0-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="52ed0-201">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="52ed0-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="52ed0-202">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="52ed0-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="52ed0-203">Upravte třídu tak, aby byla statická jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="52ed0-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="52ed0-204">Tento kurz představuje jednu instanci dat duhovky v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="52ed0-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="52ed0-205">Můžete přidat další scénáře experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="52ed0-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="52ed0-206">Do `TestIrisData` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="52ed0-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="52ed0-207">Chcete-li zjistit cluster, do kterého zadaná *Program.cs* položka patří, vraťte se `Main` do souboru Program.cs a do metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="52ed0-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="52ed0-208">Spusťte program a zjistěte, který cluster obsahuje zadanou instanci dat a kvadračské vzdálenosti od této instance k centroidům clusteru.</span><span class="sxs-lookup"><span data-stu-id="52ed0-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="52ed0-209">Vaše výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="52ed0-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="52ed0-210">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="52ed0-210">Congratulations!</span></span> <span data-ttu-id="52ed0-211">Nyní jste úspěšně vytvořili model strojového učení pro clustering duhovky a použili jste ho k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="52ed0-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="52ed0-212">Zdrojový kód pro tento kurz najdete v úložišti [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering)</span><span class="sxs-lookup"><span data-stu-id="52ed0-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="52ed0-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="52ed0-213">Next steps</span></span>

<span data-ttu-id="52ed0-214">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="52ed0-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="52ed0-215">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="52ed0-215">Understand the problem</span></span>
> - <span data-ttu-id="52ed0-216">Výběr příslušného úkolu strojového učení</span><span class="sxs-lookup"><span data-stu-id="52ed0-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="52ed0-217">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-217">Prepare the data</span></span>
> - <span data-ttu-id="52ed0-218">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="52ed0-218">Load and transform the data</span></span>
> - <span data-ttu-id="52ed0-219">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="52ed0-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="52ed0-220">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="52ed0-220">Train the model</span></span>
> - <span data-ttu-id="52ed0-221">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="52ed0-221">Use the model for predictions</span></span>

<span data-ttu-id="52ed0-222">Podívejte se na naše úložiště GitHub, abyste se dál učili a našli další ukázky.</span><span class="sxs-lookup"><span data-stu-id="52ed0-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="52ed0-223">dotnet/machinelearning GitHub repozitář</span><span class="sxs-lookup"><span data-stu-id="52ed0-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
