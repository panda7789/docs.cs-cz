---
title: 'Kurz: kategorizace Iris květin – k – znamená clustering'
description: Naučte se používat ML.NET ve scénáři clusteringu.
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 8ee8b177dc9cc89c4f54956b8c0a274b1d093ece
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282083"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="407a5-103">Kurz: kategorizace Iris květin pomocí k-znamená Clustering pomocí ML.NET</span><span class="sxs-lookup"><span data-stu-id="407a5-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="407a5-104">Tento kurz ukazuje, jak pomocí ML.NET vytvořit [model clusteringu](../resources/tasks.md#clustering) pro [datovou sadu Iris pro květ](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="407a5-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="407a5-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="407a5-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="407a5-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="407a5-106">Understand the problem</span></span>
> - <span data-ttu-id="407a5-107">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="407a5-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="407a5-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="407a5-108">Prepare the data</span></span>
> - <span data-ttu-id="407a5-109">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="407a5-109">Load and transform the data</span></span>
> - <span data-ttu-id="407a5-110">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="407a5-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="407a5-111">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="407a5-111">Train the model</span></span>
> - <span data-ttu-id="407a5-112">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="407a5-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="407a5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="407a5-113">Prerequisites</span></span>

- <span data-ttu-id="407a5-114">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="407a5-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="407a5-115">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="407a5-115">Understand the problem</span></span>

<span data-ttu-id="407a5-116">Tento problém se týká dělení sady Iris květin v různých skupinách na základě funkcí květu.</span><span class="sxs-lookup"><span data-stu-id="407a5-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="407a5-117">Tyto funkce jsou délkou a šířkou sepal a délkou a šířkou Petal.</span><span class="sxs-lookup"><span data-stu-id="407a5-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="407a5-118">Pro účely tohoto kurzu Předpokládejme, že typ každé květe není znám.</span><span class="sxs-lookup"><span data-stu-id="407a5-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="407a5-119">Chcete se seznámit se strukturou sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.</span><span class="sxs-lookup"><span data-stu-id="407a5-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="407a5-120">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="407a5-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="407a5-121">Vzhledem k tomu, do které skupiny patří jednotlivé květy, si zvolíte úlohu [Machine Learning, která není pod dohledem](../resources/glossary.md#unsupervised-machine-learning) .</span><span class="sxs-lookup"><span data-stu-id="407a5-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="407a5-122">Chcete-li rozdělit datovou sadu ve skupinách takovým způsobem, že prvky ve stejné skupině jsou lépe podobné těm, než je to u jiných skupin, použijte úlohu strojového učení [clusteringu](../resources/tasks.md#clustering) .</span><span class="sxs-lookup"><span data-stu-id="407a5-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="407a5-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="407a5-123">Create a console application</span></span>

1. <span data-ttu-id="407a5-124">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="407a5-124">Open Visual Studio.</span></span> <span data-ttu-id="407a5-125">Z řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt** .</span><span class="sxs-lookup"><span data-stu-id="407a5-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="407a5-126">V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="407a5-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="407a5-127">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="407a5-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="407a5-128">Do textového pole **název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="407a5-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="407a5-129">Vytvořte v projektu adresář s názvem *data* pro uložení datové sady a souborů modelu:</span><span class="sxs-lookup"><span data-stu-id="407a5-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="407a5-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat**  >  **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="407a5-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="407a5-131">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="407a5-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="407a5-132">Nainstalujte balíček NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="407a5-132">Install the **Microsoft.ML** NuGet package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="407a5-133">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="407a5-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="407a5-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml** a vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="407a5-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="407a5-135">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="407a5-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="407a5-136">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="407a5-136">Prepare the data</span></span>

1. <span data-ttu-id="407a5-137">Stáhněte si sadu dat [Iris. data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *dat* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="407a5-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="407a5-138">Další informace o sadě dat Iris najdete na stránce Wikipedii [sady dat Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) a na stránce [sady dat Iris](http://archive.ics.uci.edu/ml/datasets/Iris) , která je zdrojem datové sady.</span><span class="sxs-lookup"><span data-stu-id="407a5-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="407a5-139">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *Iris. data* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="407a5-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="407a5-140">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="407a5-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="407a5-141">Soubor *Iris. data* obsahuje pět sloupců, které reprezentují:</span><span class="sxs-lookup"><span data-stu-id="407a5-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="407a5-142">Délka sepal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="407a5-142">sepal length in centimeters</span></span>
- <span data-ttu-id="407a5-143">Šířka sepal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="407a5-143">sepal width in centimeters</span></span>
- <span data-ttu-id="407a5-144">Délka Petal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="407a5-144">petal length in centimeters</span></span>
- <span data-ttu-id="407a5-145">Šířka Petal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="407a5-145">petal width in centimeters</span></span>
- <span data-ttu-id="407a5-146">typ Iris květu</span><span class="sxs-lookup"><span data-stu-id="407a5-146">type of iris flower</span></span>

<span data-ttu-id="407a5-147">V případě příkladu clusteringu tento kurz ignoruje poslední sloupec.</span><span class="sxs-lookup"><span data-stu-id="407a5-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="407a5-148">Vytváření datových tříd</span><span class="sxs-lookup"><span data-stu-id="407a5-148">Create data classes</span></span>

<span data-ttu-id="407a5-149">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="407a5-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="407a5-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="407a5-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="407a5-151">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="407a5-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="407a5-152">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="407a5-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="407a5-153">`using`Do nového souboru přidejte následující direktivu:</span><span class="sxs-lookup"><span data-stu-id="407a5-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](./snippets/iris-clustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="407a5-154">Odeberte existující definici třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction` , do souboru *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="407a5-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](./snippets/iris-clustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="407a5-155">`IrisData`je vstupní datová třída a má definice pro jednotlivé funkce z datové sady.</span><span class="sxs-lookup"><span data-stu-id="407a5-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="407a5-156">Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.</span><span class="sxs-lookup"><span data-stu-id="407a5-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="407a5-157">`ClusterPrediction`Třída představuje výstup modelu clusteringu, který se použije pro `IrisData` instanci.</span><span class="sxs-lookup"><span data-stu-id="407a5-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="407a5-158">Použijte atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) k navázání `PredictedClusterId` `Distances` polí a ke sloupcům **PredictedLabel** a **skore** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="407a5-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="407a5-159">V případě úlohy clusteringu mají tyto sloupce následující význam:</span><span class="sxs-lookup"><span data-stu-id="407a5-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="407a5-160">Sloupec **PredictedLabel** obsahuje ID předpokládaného clusteru.</span><span class="sxs-lookup"><span data-stu-id="407a5-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="407a5-161">Sloupec **skóre** obsahuje pole, které má na centroids Euclideané vzdálenosti na čtverci.</span><span class="sxs-lookup"><span data-stu-id="407a5-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="407a5-162">Délka pole se rovná počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="407a5-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="407a5-163">Použijte `float` typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách.</span><span class="sxs-lookup"><span data-stu-id="407a5-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="407a5-164">Definování cest k datům a modelům</span><span class="sxs-lookup"><span data-stu-id="407a5-164">Define data and model paths</span></span>

<span data-ttu-id="407a5-165">Vraťte se k souboru *program.cs* a přidejte dvě pole, do kterých se budou uchovávat cesty k souboru sady dat a k souboru pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="407a5-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="407a5-166">`_dataPath`obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="407a5-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="407a5-167">`_modelPath`obsahuje cestu k souboru, ve kterém je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="407a5-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="407a5-168">Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest:</span><span class="sxs-lookup"><span data-stu-id="407a5-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](./snippets/iris-clustering/csharp/Program.cs#Paths)]

<span data-ttu-id="407a5-169">Chcete-li provést předchozí kompilování kódu, přidejte do `using` horní části souboru *program.cs* následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="407a5-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](./snippets/iris-clustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="407a5-170">Vytvořit kontext ML</span><span class="sxs-lookup"><span data-stu-id="407a5-170">Create ML context</span></span>

<span data-ttu-id="407a5-171">`using`Do horní části souboru *program.cs* přidejte následující další direktivy:</span><span class="sxs-lookup"><span data-stu-id="407a5-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](./snippets/iris-clustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="407a5-172">V `Main` metodě nahraďte `Console.WriteLine("Hello World!");` řádek následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="407a5-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](./snippets/iris-clustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="407a5-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType>Třída představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelů, předpovědi a další úkoly.</span><span class="sxs-lookup"><span data-stu-id="407a5-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="407a5-174">Tato informace je srovnatelná s používáním `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="407a5-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="407a5-175">Nastavení načítání dat</span><span class="sxs-lookup"><span data-stu-id="407a5-175">Set up data loading</span></span>

<span data-ttu-id="407a5-176">Přidejte následující kód do `Main` metody pro nastavení způsobu načítání dat:</span><span class="sxs-lookup"><span data-stu-id="407a5-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](./snippets/iris-clustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="407a5-177">Obecná [ `MLContext.Data.LoadFromTextFile` metoda rozšíření](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady ze zadaného `IrisData` typu a vrátí, <xref:Microsoft.ML.IDataView> které lze použít jako vstup pro transformátory.</span><span class="sxs-lookup"><span data-stu-id="407a5-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="407a5-178">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="407a5-178">Create a learning pipeline</span></span>

<span data-ttu-id="407a5-179">Pro účely tohoto kurzu se studijní kanál úlohy clusteringu skládá ze dvou následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="407a5-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="407a5-180">Zřetězí načtené sloupce do jednoho sloupce **funkce** , který používá clustering Trainer;</span><span class="sxs-lookup"><span data-stu-id="407a5-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="407a5-181">použijte <xref:Microsoft.ML.Trainers.KMeansTrainer> Trainer k vytvoření výukového modelu pomocí algoritmu k – znamená + + clustering.</span><span class="sxs-lookup"><span data-stu-id="407a5-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="407a5-182">Do metody `Main` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="407a5-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](./snippets/iris-clustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="407a5-183">Kód určuje, že sada dat by měla být rozdělena do tří clusterů.</span><span class="sxs-lookup"><span data-stu-id="407a5-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="407a5-184">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="407a5-184">Train the model</span></span>

<span data-ttu-id="407a5-185">Postup, který jste přidali v předchozích částech, připravil kanál pro školení, ale žádný nebyl proveden.</span><span class="sxs-lookup"><span data-stu-id="407a5-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="407a5-186">Přidejte následující řádek do `Main` metody pro provádění načítání dat a školení modelu:</span><span class="sxs-lookup"><span data-stu-id="407a5-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](./snippets/iris-clustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="407a5-187">Uložení modelu</span><span class="sxs-lookup"><span data-stu-id="407a5-187">Save the model</span></span>

<span data-ttu-id="407a5-188">V tomto okamžiku máte model, který lze integrovat do jakékoli existující nebo nové aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="407a5-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="407a5-189">Chcete-li uložit model do souboru. zip, přidejte do metody následující kód `Main` :</span><span class="sxs-lookup"><span data-stu-id="407a5-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](./snippets/iris-clustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="407a5-190">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="407a5-190">Use the model for predictions</span></span>

<span data-ttu-id="407a5-191">K provedení předpovědi použijte <xref:Microsoft.ML.PredictionEngine%602> třídu, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance výstupního typu.</span><span class="sxs-lookup"><span data-stu-id="407a5-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="407a5-192">Přidejte následující řádek do `Main` metody pro vytvoření instance této třídy:</span><span class="sxs-lookup"><span data-stu-id="407a5-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](./snippets/iris-clustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="407a5-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="407a5-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="407a5-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="407a5-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="407a5-195">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="407a5-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="407a5-196">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="407a5-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="407a5-197">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="407a5-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="407a5-198">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="407a5-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="407a5-199">Vytvořte `TestIrisData` třídu pro domovní testování instancí testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="407a5-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="407a5-200">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="407a5-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="407a5-201">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="407a5-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="407a5-202">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="407a5-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="407a5-203">Upravte třídu tak, aby byla statická jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="407a5-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](./snippets/iris-clustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="407a5-204">Tento kurz zavádí jednu instanci dat Iris v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="407a5-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="407a5-205">Můžete přidat další scénáře pro experimentování s modelem.</span><span class="sxs-lookup"><span data-stu-id="407a5-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="407a5-206">Do třídy přidejte následující kód `TestIrisData` :</span><span class="sxs-lookup"><span data-stu-id="407a5-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](./snippets/iris-clustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="407a5-207">Chcete-li zjistit cluster, do kterého patří zadaná položka, vraťte se do souboru *program.cs* a přidejte následující kód do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="407a5-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](./snippets/iris-clustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="407a5-208">Spusťte program, abyste viděli, který cluster obsahuje zadanou instanci dat a čtvercové vzdálenosti od této instance až po cluster centroids.</span><span class="sxs-lookup"><span data-stu-id="407a5-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="407a5-209">Výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="407a5-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="407a5-210">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="407a5-210">Congratulations!</span></span> <span data-ttu-id="407a5-211">Teď jste úspěšně vytvořili model strojového učení pro clustering Iris a použili ho k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="407a5-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="407a5-212">Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub.</span><span class="sxs-lookup"><span data-stu-id="407a5-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="407a5-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="407a5-213">Next steps</span></span>

<span data-ttu-id="407a5-214">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="407a5-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="407a5-215">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="407a5-215">Understand the problem</span></span>
> - <span data-ttu-id="407a5-216">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="407a5-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="407a5-217">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="407a5-217">Prepare the data</span></span>
> - <span data-ttu-id="407a5-218">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="407a5-218">Load and transform the data</span></span>
> - <span data-ttu-id="407a5-219">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="407a5-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="407a5-220">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="407a5-220">Train the model</span></span>
> - <span data-ttu-id="407a5-221">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="407a5-221">Use the model for predictions</span></span>

<span data-ttu-id="407a5-222">Podívejte se na naše úložiště GitHub a pokračujte v učení a Najděte další ukázky.</span><span class="sxs-lookup"><span data-stu-id="407a5-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="407a5-223">dotnet/machinelearning – úložiště GitHubu</span><span class="sxs-lookup"><span data-stu-id="407a5-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
