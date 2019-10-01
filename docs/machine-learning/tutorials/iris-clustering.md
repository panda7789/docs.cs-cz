---
title: 'Kurz: kategorizace Iris květin – k – znamená clustering'
description: Naučte se používat ML.NET ve scénáři clusteringu.
author: pkulikov
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: e360cf2418e2003f9f40628c714e9e8ebd7c3e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698563"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="635c0-103">Kurz: kategorizace Iris květin pomocí k-znamená Clustering pomocí ML.NET</span><span class="sxs-lookup"><span data-stu-id="635c0-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="635c0-104">Tento kurz ukazuje, jak pomocí ML.NET vytvořit [model clusteringu](../resources/tasks.md#clustering) pro [datovou sadu Iris pro květ](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="635c0-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="635c0-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="635c0-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="635c0-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="635c0-106">Understand the problem</span></span>
> - <span data-ttu-id="635c0-107">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="635c0-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="635c0-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="635c0-108">Prepare the data</span></span>
> - <span data-ttu-id="635c0-109">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="635c0-109">Load and transform the data</span></span>
> - <span data-ttu-id="635c0-110">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="635c0-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="635c0-111">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="635c0-111">Train the model</span></span>
> - <span data-ttu-id="635c0-112">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="635c0-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="635c0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="635c0-113">Prerequisites</span></span>

- <span data-ttu-id="635c0-114">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="635c0-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="635c0-115">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="635c0-115">Understand the problem</span></span>

<span data-ttu-id="635c0-116">Tento problém se týká dělení sady Iris květin v různých skupinách na základě funkcí květu.</span><span class="sxs-lookup"><span data-stu-id="635c0-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="635c0-117">Tyto funkce jsou délkou a šířkou sepal a délkou a šířkou Petal.</span><span class="sxs-lookup"><span data-stu-id="635c0-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="635c0-118">Pro účely tohoto kurzu Předpokládejme, že typ každé květe není znám.</span><span class="sxs-lookup"><span data-stu-id="635c0-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="635c0-119">Chcete se seznámit se strukturou sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.</span><span class="sxs-lookup"><span data-stu-id="635c0-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="635c0-120">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="635c0-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="635c0-121">Vzhledem k tomu, do které skupiny patří jednotlivé květy, si zvolíte úlohu [Machine Learning, která není pod dohledem](../resources/glossary.md#unsupervised-machine-learning) .</span><span class="sxs-lookup"><span data-stu-id="635c0-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="635c0-122">Chcete-li rozdělit datovou sadu ve skupinách takovým způsobem, že prvky ve stejné skupině jsou lépe podobné těm, než je to u jiných skupin, použijte úlohu strojového učení [clusteringu](../resources/tasks.md#clustering) .</span><span class="sxs-lookup"><span data-stu-id="635c0-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="635c0-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="635c0-123">Create a console application</span></span>

1. <span data-ttu-id="635c0-124">Otevřete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="635c0-124">Open Visual Studio.</span></span> <span data-ttu-id="635c0-125">Z řádku nabídek vyberte **soubor** > **Nový** **projekt**  > .</span><span class="sxs-lookup"><span data-stu-id="635c0-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="635c0-126">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="635c0-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="635c0-127">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="635c0-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="635c0-128">Do textového pole **název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="635c0-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="635c0-129">Vytvořte v projektu adresář s názvem *data* pro uložení datové sady a souborů modelu:</span><span class="sxs-lookup"><span data-stu-id="635c0-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="635c0-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** **novou složku** > .</span><span class="sxs-lookup"><span data-stu-id="635c0-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="635c0-131">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="635c0-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="635c0-132">Nainstalujte balíček NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="635c0-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="635c0-133">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="635c0-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="635c0-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v **1.0.0** v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="635c0-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="635c0-135">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="635c0-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="635c0-136">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="635c0-136">Prepare the data</span></span>

1. <span data-ttu-id="635c0-137">Stáhněte si sadu dat [Iris. data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *dat* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="635c0-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="635c0-138">Další informace o sadě dat Iris najdete na stránce Wikipedii [sady dat Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) a na stránce [sady dat Iris](https://archive.ics.uci.edu/ml/datasets/Iris) , která je zdrojem datové sady.</span><span class="sxs-lookup"><span data-stu-id="635c0-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="635c0-139">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *Iris. data* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="635c0-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="635c0-140">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="635c0-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="635c0-141">Soubor *Iris. data* obsahuje pět sloupců, které reprezentují:</span><span class="sxs-lookup"><span data-stu-id="635c0-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="635c0-142">Délka sepal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="635c0-142">sepal length in centimetres</span></span>
- <span data-ttu-id="635c0-143">sepal Šířka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="635c0-143">sepal width in centimetres</span></span>
- <span data-ttu-id="635c0-144">Délka Petal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="635c0-144">petal length in centimetres</span></span>
- <span data-ttu-id="635c0-145">Petal Šířka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="635c0-145">petal width in centimetres</span></span>
- <span data-ttu-id="635c0-146">typ Iris květu</span><span class="sxs-lookup"><span data-stu-id="635c0-146">type of iris flower</span></span>

<span data-ttu-id="635c0-147">V případě příkladu clusteringu tento kurz ignoruje poslední sloupec.</span><span class="sxs-lookup"><span data-stu-id="635c0-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="635c0-148">Vytváření datových tříd</span><span class="sxs-lookup"><span data-stu-id="635c0-148">Create data classes</span></span>

<span data-ttu-id="635c0-149">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="635c0-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="635c0-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="635c0-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="635c0-151">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="635c0-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="635c0-152">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="635c0-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="635c0-153">Do nového souboru přidejte následující direktivu `using`:</span><span class="sxs-lookup"><span data-stu-id="635c0-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="635c0-154">Odeberte existující definici třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, do souboru *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="635c0-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="635c0-155">`IrisData` je vstupní datová třída a má definice pro jednotlivé funkce z datové sady.</span><span class="sxs-lookup"><span data-stu-id="635c0-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="635c0-156">Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.</span><span class="sxs-lookup"><span data-stu-id="635c0-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="635c0-157">Třída `ClusterPrediction` představuje výstup modelu clusteringu, který se použije pro instanci `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="635c0-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="635c0-158">Pomocí atributu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) navažte pole `PredictedClusterId` a `Distances` do sloupců **PredictedLabel** a **skore** .</span><span class="sxs-lookup"><span data-stu-id="635c0-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="635c0-159">V případě úlohy clusteringu mají tyto sloupce následující význam:</span><span class="sxs-lookup"><span data-stu-id="635c0-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="635c0-160">Sloupec **PredictedLabel** obsahuje ID předpokládaného clusteru.</span><span class="sxs-lookup"><span data-stu-id="635c0-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="635c0-161">Sloupec **skóre** obsahuje pole, které má na centroids Euclideané vzdálenosti na čtverci.</span><span class="sxs-lookup"><span data-stu-id="635c0-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="635c0-162">Délka pole se rovná počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="635c0-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="635c0-163">K reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách použijte typ `float`.</span><span class="sxs-lookup"><span data-stu-id="635c0-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="635c0-164">Definování cest k datům a modelům</span><span class="sxs-lookup"><span data-stu-id="635c0-164">Define data and model paths</span></span>

<span data-ttu-id="635c0-165">Vraťte se k souboru *program.cs* a přidejte dvě pole, do kterých se budou uchovávat cesty k souboru sady dat a k souboru pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="635c0-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="635c0-166">`_dataPath` obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="635c0-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="635c0-167">`_modelPath` obsahuje cestu k souboru, ve kterém je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="635c0-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="635c0-168">Přidejte následující kód přímo nad metodu `Main` a určete tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="635c0-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="635c0-169">Chcete-li provést předchozí kompilování kódu, přidejte následující direktivy `using` v horní části souboru *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="635c0-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="635c0-170">Vytvořit kontext ML</span><span class="sxs-lookup"><span data-stu-id="635c0-170">Create ML context</span></span>

<span data-ttu-id="635c0-171">Přidejte následující další direktivy `using` do horní části souboru *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="635c0-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="635c0-172">V metodě `Main` nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="635c0-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="635c0-173">Třída <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelů, předpovědi a další úkoly.</span><span class="sxs-lookup"><span data-stu-id="635c0-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="635c0-174">To je srovnatelné v koncepčním použití `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="635c0-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="635c0-175">Načítání dat instalace</span><span class="sxs-lookup"><span data-stu-id="635c0-175">Setup data loading</span></span>

<span data-ttu-id="635c0-176">Přidejte následující kód do metody `Main` a nastavte způsob, jak načíst data:</span><span class="sxs-lookup"><span data-stu-id="635c0-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="635c0-177">Obecná [metoda rozšíření `MLContext.Data.LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady ze zadaného typu `IrisData` a vrátí <xref:Microsoft.ML.IDataView>, které lze použít jako vstup pro transformátory.</span><span class="sxs-lookup"><span data-stu-id="635c0-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="635c0-178">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="635c0-178">Create a learning pipeline</span></span>

<span data-ttu-id="635c0-179">Pro účely tohoto kurzu se studijní kanál úlohy clusteringu skládá ze dvou následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="635c0-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="635c0-180">Zřetězí načtené sloupce do jednoho sloupce **funkce** , který používá clustering Trainer;</span><span class="sxs-lookup"><span data-stu-id="635c0-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="635c0-181">Použijte <xref:Microsoft.ML.Trainers.KMeansTrainer> Trainer k vytvoření výukového modelu pomocí algoritmu k.</span><span class="sxs-lookup"><span data-stu-id="635c0-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="635c0-182">Do metody `Main` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="635c0-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="635c0-183">Kód určuje, že sada dat by měla být rozdělena do tří clusterů.</span><span class="sxs-lookup"><span data-stu-id="635c0-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="635c0-184">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="635c0-184">Train the model</span></span>

<span data-ttu-id="635c0-185">Postup, který jste přidali v předchozích částech, připravil kanál pro školení, ale žádný nebyl proveden.</span><span class="sxs-lookup"><span data-stu-id="635c0-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="635c0-186">Přidejte následující řádek do metody `Main`, aby se provádělo načítání dat a školení modelu:</span><span class="sxs-lookup"><span data-stu-id="635c0-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="635c0-187">Uložit model</span><span class="sxs-lookup"><span data-stu-id="635c0-187">Save the model</span></span>

<span data-ttu-id="635c0-188">V tomto okamžiku máte model, který lze integrovat do jakékoli existující nebo nové aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="635c0-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="635c0-189">Chcete-li uložit model do souboru. zip, přidejte následující kód do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="635c0-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="635c0-190">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="635c0-190">Use the model for predictions</span></span>

<span data-ttu-id="635c0-191">K provedení předpovědi použijte třídu <xref:Microsoft.ML.PredictionEngine%602>, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance typu výstupu.</span><span class="sxs-lookup"><span data-stu-id="635c0-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="635c0-192">Přidejte následující řádek do metody `Main` pro vytvoření instance této třídy:</span><span class="sxs-lookup"><span data-stu-id="635c0-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="635c0-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="635c0-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="635c0-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="635c0-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="635c0-195">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="635c0-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="635c0-196">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="635c0-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="635c0-197">V této příručce najdete informace o [použití `PredictionEnginePool` v ASP.NET Core webovém rozhraní API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) .</span><span class="sxs-lookup"><span data-stu-id="635c0-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="635c0-198">rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="635c0-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="635c0-199">Vytvořte třídu `TestIrisData` pro domu instancí testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="635c0-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="635c0-200">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .</span><span class="sxs-lookup"><span data-stu-id="635c0-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="635c0-201">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="635c0-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="635c0-202">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="635c0-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="635c0-203">Upravte třídu tak, aby byla statická jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="635c0-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="635c0-204">Tento kurz zavádí jednu instanci dat Iris v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="635c0-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="635c0-205">Můžete přidat další scénáře pro experimentování s modelem.</span><span class="sxs-lookup"><span data-stu-id="635c0-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="635c0-206">Do třídy `TestIrisData` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="635c0-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="635c0-207">Chcete-li zjistit cluster, do kterého patří zadaná položka, vraťte se do souboru *program.cs* a přidejte následující kód do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="635c0-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="635c0-208">Spusťte program, abyste viděli, který cluster obsahuje zadanou instanci dat a čtvercové vzdálenosti od této instance až po cluster centroids.</span><span class="sxs-lookup"><span data-stu-id="635c0-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="635c0-209">Výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="635c0-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="635c0-210">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="635c0-210">Congratulations!</span></span> <span data-ttu-id="635c0-211">Teď jste úspěšně vytvořili model strojového učení pro clustering Iris a použili ho k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="635c0-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="635c0-212">Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub.</span><span class="sxs-lookup"><span data-stu-id="635c0-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="635c0-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="635c0-213">Next steps</span></span>

<span data-ttu-id="635c0-214">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="635c0-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="635c0-215">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="635c0-215">Understand the problem</span></span>
> - <span data-ttu-id="635c0-216">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="635c0-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="635c0-217">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="635c0-217">Prepare the data</span></span>
> - <span data-ttu-id="635c0-218">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="635c0-218">Load and transform the data</span></span>
> - <span data-ttu-id="635c0-219">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="635c0-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="635c0-220">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="635c0-220">Train the model</span></span>
> - <span data-ttu-id="635c0-221">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="635c0-221">Use the model for predictions</span></span>

<span data-ttu-id="635c0-222">Podívejte se na naše úložiště GitHub a pokračujte v učení a Najděte další ukázky.</span><span class="sxs-lookup"><span data-stu-id="635c0-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="635c0-223">dotnet/machinelearning – úložiště GitHubu</span><span class="sxs-lookup"><span data-stu-id="635c0-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
