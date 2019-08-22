---
title: 'Kurz: Kategorizace Iris květin – k – znamená clusteringu'
description: Naučte se používat ML.NET ve scénáři clusteringu.
author: pkulikov
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 772558be14d207475d20083f5a6b729f03766471
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666650"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="6d72d-103">Kurz: Kategorizace Iris květin pomocí k-znamená Clustering pomocí ML.NET</span><span class="sxs-lookup"><span data-stu-id="6d72d-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="6d72d-104">Tento kurz ukazuje, jak pomocí ML.NET vytvořit [model clusteringu](../resources/tasks.md#clustering) pro [datovou sadu Iris pro květ](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="6d72d-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="6d72d-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="6d72d-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="6d72d-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="6d72d-106">Understand the problem</span></span>
> - <span data-ttu-id="6d72d-107">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="6d72d-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="6d72d-108">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="6d72d-108">Prepare the data</span></span>
> - <span data-ttu-id="6d72d-109">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="6d72d-109">Load and transform the data</span></span>
> - <span data-ttu-id="6d72d-110">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="6d72d-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="6d72d-111">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6d72d-111">Train the model</span></span>
> - <span data-ttu-id="6d72d-112">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6d72d-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d72d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d72d-113">Prerequisites</span></span>

- <span data-ttu-id="6d72d-114">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="6d72d-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="6d72d-115">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="6d72d-115">Understand the problem</span></span>

<span data-ttu-id="6d72d-116">Tento problém se týká dělení sady Iris květin v různých skupinách na základě funkcí květu.</span><span class="sxs-lookup"><span data-stu-id="6d72d-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="6d72d-117">Tyto funkce jsou délkou a šířkou sepal a délkou a šířkou Petal.</span><span class="sxs-lookup"><span data-stu-id="6d72d-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="6d72d-118">Pro účely tohoto kurzu Předpokládejme, že typ každé květe není znám.</span><span class="sxs-lookup"><span data-stu-id="6d72d-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="6d72d-119">Chcete se seznámit se strukturou sady dat z funkcí a předpovědět, jak instance dat odpovídá této struktuře.</span><span class="sxs-lookup"><span data-stu-id="6d72d-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="6d72d-120">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="6d72d-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="6d72d-121">Vzhledem k tomu, do které skupiny patří jednotlivé květy, si zvolíte úlohu [Machine Learning](../resources/glossary.md#unsupervised-machine-learning) , která není pod dohledem.</span><span class="sxs-lookup"><span data-stu-id="6d72d-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="6d72d-122">Chcete-li rozdělit datovou sadu ve skupinách takovým způsobem, že prvky ve stejné skupině jsou lépe podobné těm, než je to u jiných skupin, použijte úlohu strojového učení [clusteringu](../resources/tasks.md#clustering) .</span><span class="sxs-lookup"><span data-stu-id="6d72d-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="6d72d-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="6d72d-123">Create a console application</span></span>

1. <span data-ttu-id="6d72d-124">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d72d-124">Open Visual Studio.</span></span> <span data-ttu-id="6d72d-125">Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="6d72d-126">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="6d72d-127">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="6d72d-128">Do textového pole **název** zadejte "IrisFlowerClustering" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="6d72d-129">Vytvořte v projektu adresář s názvem *data* pro uložení datové sady a souborů modelu:</span><span class="sxs-lookup"><span data-stu-id="6d72d-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="6d72d-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="6d72d-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="6d72d-131">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="6d72d-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="6d72d-132">Nainstalujte balíček NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="6d72d-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="6d72d-133">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6d72d-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="6d72d-134">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v **1.0.0** v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="6d72d-135">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="6d72d-136">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="6d72d-136">Prepare the data</span></span>

1. <span data-ttu-id="6d72d-137">Stáhněte si sadu dat [Iris. data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) a uložte ji do složky *dat* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="6d72d-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="6d72d-138">Další informace o sadě dat Iris najdete na stránce Wikipedii [sady dat Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) a na stránce [sady dat Iris](https://archive.ics.uci.edu/ml/datasets/Iris) , která je zdrojem datové sady.</span><span class="sxs-lookup"><span data-stu-id="6d72d-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="6d72d-139">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *Iris. data* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6d72d-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="6d72d-140">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="6d72d-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="6d72d-141">Soubor *Iris. data* obsahuje pět sloupců, které reprezentují:</span><span class="sxs-lookup"><span data-stu-id="6d72d-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="6d72d-142">Délka sepal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="6d72d-142">sepal length in centimetres</span></span>
- <span data-ttu-id="6d72d-143">sepal Šířka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="6d72d-143">sepal width in centimetres</span></span>
- <span data-ttu-id="6d72d-144">Délka Petal v centimetrech</span><span class="sxs-lookup"><span data-stu-id="6d72d-144">petal length in centimetres</span></span>
- <span data-ttu-id="6d72d-145">Petal Šířka v centimetrech</span><span class="sxs-lookup"><span data-stu-id="6d72d-145">petal width in centimetres</span></span>
- <span data-ttu-id="6d72d-146">typ Iris květu</span><span class="sxs-lookup"><span data-stu-id="6d72d-146">type of iris flower</span></span>

<span data-ttu-id="6d72d-147">V případě příkladu clusteringu tento kurz ignoruje poslední sloupec.</span><span class="sxs-lookup"><span data-stu-id="6d72d-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="6d72d-148">Vytváření datových tříd</span><span class="sxs-lookup"><span data-stu-id="6d72d-148">Create data classes</span></span>

<span data-ttu-id="6d72d-149">Vytvořte třídy pro vstupní data a předpovědi:</span><span class="sxs-lookup"><span data-stu-id="6d72d-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="6d72d-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="6d72d-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="6d72d-151">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="6d72d-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="6d72d-152">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="6d72d-153">Do nového souboru `using` přidejte následující direktivu:</span><span class="sxs-lookup"><span data-stu-id="6d72d-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="6d72d-154">Odeberte existující definici třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, do souboru *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="6d72d-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="6d72d-155">`IrisData`je vstupní datová třída a má definice pro jednotlivé funkce z datové sady.</span><span class="sxs-lookup"><span data-stu-id="6d72d-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="6d72d-156">Pomocí atributu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v souboru sady dat.</span><span class="sxs-lookup"><span data-stu-id="6d72d-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="6d72d-157">Třída představuje výstup modelu clusteringu, který `IrisData` se použije pro instanci. `ClusterPrediction`</span><span class="sxs-lookup"><span data-stu-id="6d72d-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="6d72d-158">Použijte atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) k navázání `PredictedClusterId` polí `Distances` a ke sloupcům **PredictedLabel** a **skore** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6d72d-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="6d72d-159">V případě úlohy clusteringu mají tyto sloupce následující význam:</span><span class="sxs-lookup"><span data-stu-id="6d72d-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="6d72d-160">Sloupec **PredictedLabel** obsahuje ID předpokládaného clusteru.</span><span class="sxs-lookup"><span data-stu-id="6d72d-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="6d72d-161">Sloupec **skóre** obsahuje pole, které má na centroids Euclideané vzdálenosti na čtverci.</span><span class="sxs-lookup"><span data-stu-id="6d72d-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="6d72d-162">Délka pole se rovná počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="6d72d-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="6d72d-163">`float` Použijte typ pro reprezentaci hodnot s plovoucí desetinnou čárkou ve vstupních a prediktivních datových třídách.</span><span class="sxs-lookup"><span data-stu-id="6d72d-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="6d72d-164">Definování cest k datům a modelům</span><span class="sxs-lookup"><span data-stu-id="6d72d-164">Define data and model paths</span></span>

<span data-ttu-id="6d72d-165">Vraťte se k souboru *program.cs* a přidejte dvě pole, do kterých se budou uchovávat cesty k souboru sady dat a k souboru pro uložení modelu:</span><span class="sxs-lookup"><span data-stu-id="6d72d-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="6d72d-166">`_dataPath`obsahuje cestu k souboru s datovou sadou, která se používá ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="6d72d-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="6d72d-167">`_modelPath`obsahuje cestu k souboru, ve kterém je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="6d72d-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="6d72d-168">Přidejte následující kód přímo nad `Main` metodu pro určení těchto cest:</span><span class="sxs-lookup"><span data-stu-id="6d72d-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="6d72d-169">Chcete-li provést předchozí kompilování kódu, přidejte `using` do horní části souboru *program.cs* následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="6d72d-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="6d72d-170">Vytvořit kontext ML</span><span class="sxs-lookup"><span data-stu-id="6d72d-170">Create ML context</span></span>

<span data-ttu-id="6d72d-171">Do horní části souboru `using` *program.cs* přidejte následující další direktivy:</span><span class="sxs-lookup"><span data-stu-id="6d72d-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="6d72d-172">V metodě nahraďte `Console.WriteLine("Hello World!");`řádeknásledujícímkódem: `Main`</span><span class="sxs-lookup"><span data-stu-id="6d72d-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="6d72d-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Třída představuje prostředí strojového učení a poskytuje mechanismy pro protokolování a vstupní body pro načítání dat, školení modelů, předpovědi a další úkoly.</span><span class="sxs-lookup"><span data-stu-id="6d72d-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="6d72d-174">Tato informace je srovnatelná s používáním `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6d72d-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="6d72d-175">Načítání dat instalace</span><span class="sxs-lookup"><span data-stu-id="6d72d-175">Setup data loading</span></span>

<span data-ttu-id="6d72d-176">Přidejte následující kód do `Main` metody pro nastavení způsobu načtení dat:</span><span class="sxs-lookup"><span data-stu-id="6d72d-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="6d72d-177">Obecná `IrisData` [ `MLContext.Data.LoadFromTextFile` metoda rozšíření](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) odvodí schéma datové sady ze zadaného typu a vrátí <xref:Microsoft.ML.IDataView> , které lze použít jako vstup pro transformátory.</span><span class="sxs-lookup"><span data-stu-id="6d72d-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="6d72d-178">Vytvoření výukového kanálu</span><span class="sxs-lookup"><span data-stu-id="6d72d-178">Create a learning pipeline</span></span>

<span data-ttu-id="6d72d-179">Pro účely tohoto kurzu se studijní kanál úlohy clusteringu skládá ze dvou následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="6d72d-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="6d72d-180">Zřetězí načtené sloupce do jednoho sloupce **funkce** , který používá clustering Trainer;</span><span class="sxs-lookup"><span data-stu-id="6d72d-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="6d72d-181">Použijte Trainer <xref:Microsoft.ML.Trainers.KMeansTrainer> k vytvoření výukového modelu pomocí algoritmu k – znamená + + clustering.</span><span class="sxs-lookup"><span data-stu-id="6d72d-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="6d72d-182">Do `Main` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="6d72d-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="6d72d-183">Kód určuje, že sada dat by měla být rozdělena do tří clusterů.</span><span class="sxs-lookup"><span data-stu-id="6d72d-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="6d72d-184">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6d72d-184">Train the model</span></span>

<span data-ttu-id="6d72d-185">Postup, který jste přidali v předchozích částech, připravil kanál pro školení, ale žádný nebyl proveden.</span><span class="sxs-lookup"><span data-stu-id="6d72d-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="6d72d-186">Přidejte následující řádek do `Main` metody pro provádění načítání dat a školení modelu:</span><span class="sxs-lookup"><span data-stu-id="6d72d-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="6d72d-187">Uložit model</span><span class="sxs-lookup"><span data-stu-id="6d72d-187">Save the model</span></span>

<span data-ttu-id="6d72d-188">V tomto okamžiku máte model, který lze integrovat do jakékoli existující nebo nové aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="6d72d-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="6d72d-189">Chcete-li uložit model do souboru. zip, přidejte do `Main` metody následující kód:</span><span class="sxs-lookup"><span data-stu-id="6d72d-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="6d72d-190">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6d72d-190">Use the model for predictions</span></span>

<span data-ttu-id="6d72d-191">K provedení předpovědi použijte <xref:Microsoft.ML.PredictionEngine%602> třídu, která přebírá instance vstupního typu prostřednictvím kanálu transformátoru a vytváří instance výstupního typu.</span><span class="sxs-lookup"><span data-stu-id="6d72d-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="6d72d-192">Přidejte následující řádek do `Main` metody pro vytvoření instance této třídy:</span><span class="sxs-lookup"><span data-stu-id="6d72d-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="6d72d-193">`TestIrisData` Vytvořte třídu pro domovní testování instancí testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="6d72d-193">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="6d72d-194">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="6d72d-194">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="6d72d-195">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="6d72d-195">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="6d72d-196">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="6d72d-196">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="6d72d-197">Upravte třídu tak, aby byla statická jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d72d-197">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="6d72d-198">Tento kurz zavádí jednu instanci dat Iris v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="6d72d-198">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="6d72d-199">Můžete přidat další scénáře pro experimentování s modelem.</span><span class="sxs-lookup"><span data-stu-id="6d72d-199">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="6d72d-200">Do `TestIrisData` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="6d72d-200">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="6d72d-201">Chcete-li zjistit cluster, do kterého patří zadaná položka, vraťte se do souboru *program.cs* a přidejte následující kód do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="6d72d-201">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="6d72d-202">Spusťte program, abyste viděli, který cluster obsahuje zadanou instanci dat a čtvercové vzdálenosti od této instance až po cluster centroids.</span><span class="sxs-lookup"><span data-stu-id="6d72d-202">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="6d72d-203">Výsledky by měly být podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="6d72d-203">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="6d72d-204">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="6d72d-204">Congratulations!</span></span> <span data-ttu-id="6d72d-205">Teď jste úspěšně vytvořili model strojového učení pro clustering Iris a použili ho k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6d72d-205">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="6d72d-206">Zdrojový kód pro tento kurz najdete v úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub.</span><span class="sxs-lookup"><span data-stu-id="6d72d-206">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d72d-207">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6d72d-207">Next steps</span></span>

<span data-ttu-id="6d72d-208">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="6d72d-208">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="6d72d-209">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="6d72d-209">Understand the problem</span></span>
> - <span data-ttu-id="6d72d-210">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="6d72d-210">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="6d72d-211">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="6d72d-211">Prepare the data</span></span>
> - <span data-ttu-id="6d72d-212">Načtení a transformace dat</span><span class="sxs-lookup"><span data-stu-id="6d72d-212">Load and transform the data</span></span>
> - <span data-ttu-id="6d72d-213">Výběr algoritmu učení</span><span class="sxs-lookup"><span data-stu-id="6d72d-213">Choose a learning algorithm</span></span>
> - <span data-ttu-id="6d72d-214">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6d72d-214">Train the model</span></span>
> - <span data-ttu-id="6d72d-215">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6d72d-215">Use the model for predictions</span></span>

<span data-ttu-id="6d72d-216">Podívejte se na naše úložiště GitHub a pokračujte v učení a Najděte další ukázky.</span><span class="sxs-lookup"><span data-stu-id="6d72d-216">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="6d72d-217">dotnet/machinelearning – úložiště GitHubu</span><span class="sxs-lookup"><span data-stu-id="6d72d-217">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
