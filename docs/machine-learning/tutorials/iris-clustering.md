---
title: 'Kurz: kategorizace Iris květin – k – znamená clustering'
description: Naučte se používat ML.NET ve scénáři clusteringu.
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: a7199ce2e5217eaadfa10893eb1fbb3417e9be20
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204839"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="54c40-103">Kurz: kategorizace Iris květin pomocí k-znamená Clustering pomocí ML.NET</span><span class="sxs-lookup"><span data-stu-id="54c40-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="54c40-104">Tento kurz ukazuje, jak pomocí ML.NET vytvořit [model clusteringu](../resources/tasks.md#clustering) pro [datovou sadu Iris pro květ](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="54c40-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="54c40-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="54c40-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="54c40-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="54c40-106">Understand the problem</span></span>
> - <span data-ttu-id="54c40-107">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="54c40-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="54c40-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="54c40-108">Prepare the data</span></span>
> - <span data-ttu-id="54c40-109">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="54c40-109">Load and transform the data</span></span>
> - <span data-ttu-id="54c40-110">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="54c40-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="54c40-111">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="54c40-111">Train the model</span></span>
> - <span data-ttu-id="54c40-112">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="54c40-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54c40-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54c40-113">Prerequisites</span></span>

- <span data-ttu-id="54c40-114">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="54c40-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="54c40-115">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="54c40-115">Understand the problem</span></span>

<span data-ttu-id="54c40-116">Tento problém se týká dělení sady Iris květin v různých skupinách na základě funkcí květu.</span><span class="sxs-lookup"><span data-stu-id="54c40-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="54c40-117">Tyto funkce jsou délkou a šířkou sepal a délkou a šířkou Petal.</span><span class="sxs-lookup"><span data-stu-id="54c40-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="54c40-118">Pro účely tohoto kurzu Předpokládejme, že typ každé květe není znám.</span><span class="sxs-lookup"><span data-stu-id="54c40-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="54c40-119">Chcete se seznámit se strukturou sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.</span><span class="sxs-lookup"><span data-stu-id="54c40-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="54c40-120">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="54c40-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="54c40-121">Vzhledem k tomu, do které skupiny patří jednotlivé květy, si zvolíte úlohu [Machine Learning, která není pod dohledem](../resources/glossary.md#unsupervised-machine-learning) .</span><span class="sxs-lookup"><span data-stu-id="54c40-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="54c40-122">Chcete-li rozdělit datovou sadu ve skupinách takovým způsobem, že prvky ve stejné skupině jsou lépe podobné těm, než je to u jiných skupin, použijte úlohu strojového učení [clusteringu](../resources/tasks.md#clustering) .</span><span class="sxs-lookup"><span data-stu-id="54c40-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="54c40-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="54c40-123">Create a console application</span></span>

1. <span data-ttu-id="54c40-124">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54c40-124">Open Visual Studio.</span></span> <span data-ttu-id="54c40-125">Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="54c40-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="54c40-126">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="54c40-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="54c40-127">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="54c40-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="54c40-128">Do textového pole **název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="54c40-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="54c40-129">Vytvořte v projektu adresář s názvem *data* pro uložení datové sady a souborů modelu:</span><span class="sxs-lookup"><span data-stu-id="54c40-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="54c40-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="54c40-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="54c40-131">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="54c40-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="54c40-132">Nainstalujte balíček NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="54c40-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="54c40-133">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="54c40-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="54c40-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml** a vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="54c40-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="54c40-135">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="54c40-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="54c40-136">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="54c40-136">Prepare the data</span></span>

1. <span data-ttu-id="54c40-137">Stáhněte si sadu dat [Iris. data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *dat* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="54c40-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="54c40-138">Další informace o sadě dat Iris najdete na stránce Wikipedii [sady dat Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) a na stránce [sady dat Iris](https://archive.ics.uci.edu/ml/datasets/Iris) , která je zdrojem datové sady.</span><span class="sxs-lookup"><span data-stu-id="54c40-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="54c40-139">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *Iris. data* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="54c40-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="54c40-140">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="54c40-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="54c40-141">Soubor *Iris. data* obsahuje pět sloupců, které reprezentují:</span><span class="sxs-lookup"><span data-stu-id="54c40-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="54c40-142">Délka sepal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="54c40-142">sepal length in centimetres</span></span>
- <span data-ttu-id="54c40-143">sepal Šířka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="54c40-143">sepal width in centimetres</span></span>
- <span data-ttu-id="54c40-144">Délka Petal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="54c40-144">petal length in centimetres</span></span>
- <span data-ttu-id="54c40-145">Petal Šířka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="54c40-145">petal width in centimetres</span></span>
- <span data-ttu-id="54c40-146">typ Iris květu</span><span class="sxs-lookup"><span data-stu-id="54c40-146">type of iris flower</span></span>

<span data-ttu-id="54c40-147">V případě příkladu clusteringu tento kurz ignoruje poslední sloupec.</span><span class="sxs-lookup"><span data-stu-id="54c40-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="54c40-148">Vytváření datových tříd</span><span class="sxs-lookup"><span data-stu-id="54c40-148">Create data classes</span></span>

<span data-ttu-id="54c40-149">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="54c40-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="54c40-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="54c40-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="54c40-151">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="54c40-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="54c40-152">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="54c40-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="54c40-153">Do nového souboru přidejte následující direktivu `using`:</span><span class="sxs-lookup"><span data-stu-id="54c40-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="54c40-154">Odeberte existující definici třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, do souboru *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="54c40-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="54c40-155">`IrisData` je vstupní datová třída a má definice pro jednotlivé funkce z datové sady.</span><span class="sxs-lookup"><span data-stu-id="54c40-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="54c40-156">Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.</span><span class="sxs-lookup"><span data-stu-id="54c40-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="54c40-157">Třída `ClusterPrediction` představuje výstup modelu clusteringu, který se použije pro instanci `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="54c40-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="54c40-158">Pomocí atributu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) navažte `PredictedClusterId` a `Distances` pole do sloupců **PredictedLabel** a **skore** (pořadí).</span><span class="sxs-lookup"><span data-stu-id="54c40-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="54c40-159">V případě úlohy clusteringu mají tyto sloupce následující význam:</span><span class="sxs-lookup"><span data-stu-id="54c40-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="54c40-160">Sloupec **PredictedLabel** obsahuje ID předpokládaného clusteru.</span><span class="sxs-lookup"><span data-stu-id="54c40-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="54c40-161">Sloupec **skóre** obsahuje pole, které má na centroids Euclideané vzdálenosti na čtverci.</span><span class="sxs-lookup"><span data-stu-id="54c40-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="54c40-162">Délka pole se rovná počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="54c40-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="54c40-163">Použijte `float` typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupní a předpovědi třídy dat.</span><span class="sxs-lookup"><span data-stu-id="54c40-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="54c40-164">Definování cest k datům a modelům</span><span class="sxs-lookup"><span data-stu-id="54c40-164">Define data and model paths</span></span>

<span data-ttu-id="54c40-165">Vraťte se k souboru *program.cs* a přidejte dvě pole, do kterých se budou uchovávat cesty k souboru sady dat a k souboru pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="54c40-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="54c40-166">`_dataPath` obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="54c40-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="54c40-167">`_modelPath` obsahuje cestu k souboru, ve kterém je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="54c40-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="54c40-168">Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest:</span><span class="sxs-lookup"><span data-stu-id="54c40-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="54c40-169">Chcete-li provést předchozí kompilování kódu, přidejte následující direktivy `using` v horní části souboru *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="54c40-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="54c40-170">Vytvořit kontext ML</span><span class="sxs-lookup"><span data-stu-id="54c40-170">Create ML context</span></span>

<span data-ttu-id="54c40-171">Do horní části souboru *program.cs* přidejte následující dodatečné direktivy `using`:</span><span class="sxs-lookup"><span data-stu-id="54c40-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="54c40-172">V metodě `Main` nahraďte `Console.WriteLine("Hello World!");` řádek následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="54c40-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="54c40-173">Třída <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelů, předpovědi a další úkoly.</span><span class="sxs-lookup"><span data-stu-id="54c40-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="54c40-174">To je srovnatelné v koncepčním používání `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="54c40-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="54c40-175">Načítání dat instalace</span><span class="sxs-lookup"><span data-stu-id="54c40-175">Setup data loading</span></span>

<span data-ttu-id="54c40-176">Do metody `Main` přidejte následující kód, který nastaví způsob načtení dat:</span><span class="sxs-lookup"><span data-stu-id="54c40-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="54c40-177">[Metoda rozšíření generic`MLContext.Data.LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady ze zadaného typu `IrisData` a vrátí <xref:Microsoft.ML.IDataView>, které lze použít jako vstup pro transformátory.</span><span class="sxs-lookup"><span data-stu-id="54c40-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="54c40-178">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="54c40-178">Create a learning pipeline</span></span>

<span data-ttu-id="54c40-179">Pro účely tohoto kurzu se studijní kanál úlohy clusteringu skládá ze dvou následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="54c40-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="54c40-180">Zřetězí načtené sloupce do jednoho sloupce **funkce** , který používá clustering Trainer;</span><span class="sxs-lookup"><span data-stu-id="54c40-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="54c40-181">pomocí <xref:Microsoft.ML.Trainers.KMeansTrainer> Trainer můžete vytvořit výuku modelu pomocí algoritmu k, který je více než clustering.</span><span class="sxs-lookup"><span data-stu-id="54c40-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="54c40-182">Do `Main` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="54c40-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="54c40-183">Kód určuje, že sada dat by měla být rozdělena do tří clusterů.</span><span class="sxs-lookup"><span data-stu-id="54c40-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="54c40-184">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="54c40-184">Train the model</span></span>

<span data-ttu-id="54c40-185">Postup, který jste přidali v předchozích částech, připravil kanál pro školení, ale žádný nebyl proveden.</span><span class="sxs-lookup"><span data-stu-id="54c40-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="54c40-186">Přidejte následující řádek do metody `Main`, aby se provádělo načítání dat a školení modelu:</span><span class="sxs-lookup"><span data-stu-id="54c40-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="54c40-187">Uložit model</span><span class="sxs-lookup"><span data-stu-id="54c40-187">Save the model</span></span>

<span data-ttu-id="54c40-188">V tomto okamžiku máte model, který lze integrovat do jakékoli existující nebo nové aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="54c40-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="54c40-189">Chcete-li uložit model do souboru. zip, přidejte následující kód do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="54c40-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="54c40-190">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="54c40-190">Use the model for predictions</span></span>

<span data-ttu-id="54c40-191">K provedení předpovědi použijte třídu <xref:Microsoft.ML.PredictionEngine%602>, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance typu výstupu.</span><span class="sxs-lookup"><span data-stu-id="54c40-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="54c40-192">Přidejte následující řádek do metody `Main` pro vytvoření instance této třídy:</span><span class="sxs-lookup"><span data-stu-id="54c40-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="54c40-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="54c40-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="54c40-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="54c40-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="54c40-195">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="54c40-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="54c40-196">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="54c40-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="54c40-197">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="54c40-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="54c40-198">rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="54c40-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="54c40-199">Vytvořte třídu `TestIrisData` pro vytváření instancí testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="54c40-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="54c40-200">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="54c40-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="54c40-201">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="54c40-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="54c40-202">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="54c40-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="54c40-203">Upravte třídu tak, aby byla statická jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="54c40-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="54c40-204">Tento kurz zavádí jednu instanci dat Iris v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="54c40-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="54c40-205">Můžete přidat další scénáře pro experimentování s modelem.</span><span class="sxs-lookup"><span data-stu-id="54c40-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="54c40-206">Do `TestIrisData` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="54c40-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="54c40-207">Chcete-li zjistit cluster, do kterého patří zadaná položka, vraťte se do souboru *program.cs* a přidejte následující kód do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="54c40-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="54c40-208">Spusťte program, abyste viděli, který cluster obsahuje zadanou instanci dat a čtvercové vzdálenosti od této instance až po cluster centroids.</span><span class="sxs-lookup"><span data-stu-id="54c40-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="54c40-209">Výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="54c40-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="54c40-210">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="54c40-210">Congratulations!</span></span> <span data-ttu-id="54c40-211">Teď jste úspěšně vytvořili model strojového učení pro clustering Iris a použili ho k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="54c40-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="54c40-212">Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub.</span><span class="sxs-lookup"><span data-stu-id="54c40-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="54c40-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="54c40-213">Next steps</span></span>

<span data-ttu-id="54c40-214">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="54c40-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="54c40-215">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="54c40-215">Understand the problem</span></span>
> - <span data-ttu-id="54c40-216">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="54c40-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="54c40-217">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="54c40-217">Prepare the data</span></span>
> - <span data-ttu-id="54c40-218">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="54c40-218">Load and transform the data</span></span>
> - <span data-ttu-id="54c40-219">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="54c40-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="54c40-220">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="54c40-220">Train the model</span></span>
> - <span data-ttu-id="54c40-221">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="54c40-221">Use the model for predictions</span></span>

<span data-ttu-id="54c40-222">Podívejte se na naše úložiště GitHub a pokračujte v učení a Najděte další ukázky.</span><span class="sxs-lookup"><span data-stu-id="54c40-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="54c40-223">dotnet/machinelearning – úložiště GitHubu</span><span class="sxs-lookup"><span data-stu-id="54c40-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
