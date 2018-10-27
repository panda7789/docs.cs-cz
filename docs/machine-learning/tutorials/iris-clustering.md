---
title: Pomocí ML.NET květin clusteru iris (clustery)
description: Zjistěte, jak použít ve scénáři clusteringu ML.NET
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bb41fd317507c14b46aea94e1ce576e390932a65
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453187"
---
# <a name="tutorial-use-mlnet-to-cluster-iris-flowers-clustering"></a><span data-ttu-id="c09af-103">Kurz: Použití ML.NET do clusteru květin iris (clustery)</span><span class="sxs-lookup"><span data-stu-id="c09af-103">Tutorial: Use ML.NET to cluster iris flowers (clustering)</span></span>

> [!NOTE]
> <span data-ttu-id="c09af-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="c09af-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c09af-105">Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c09af-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="c09af-106">Tento kurz ukazuje, jak použít ML.NET k sestavení [clusteringový model](../resources/tasks.md#clustering) pro [datovou sadu iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="c09af-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="c09af-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="c09af-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="c09af-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="c09af-108">Understand the problem</span></span>
> - <span data-ttu-id="c09af-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="c09af-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="c09af-110">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="c09af-110">Prepare the data</span></span>
> - <span data-ttu-id="c09af-111">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="c09af-111">Load and transform the data</span></span>
> - <span data-ttu-id="c09af-112">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="c09af-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="c09af-113">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c09af-113">Train the model</span></span>
> - <span data-ttu-id="c09af-114">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="c09af-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c09af-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c09af-115">Prerequisites</span></span>

- <span data-ttu-id="c09af-116">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="c09af-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="c09af-117">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="c09af-117">Understand the problem</span></span>

<span data-ttu-id="c09af-118">Tento problém je o rozdělení sadu iris květin v různých skupinách na základě funkcí květinu.</span><span class="sxs-lookup"><span data-stu-id="c09af-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="c09af-119">Tyto funkce jsou délku a šířku sepal a délku a šířku petal.</span><span class="sxs-lookup"><span data-stu-id="c09af-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="c09af-120">Pro účely tohoto kurzu předpokládá, že typ jednotlivých květinu neznámý.</span><span class="sxs-lookup"><span data-stu-id="c09af-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="c09af-121">Chcete seznámit se se strukturou datové sady z funkcí a předpovědět, jak zapadá data instance této struktury.</span><span class="sxs-lookup"><span data-stu-id="c09af-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="c09af-122">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="c09af-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="c09af-123">Jak si nejste jisti, do které skupiny patří každý květinu, zvolte [nastavenou možnost bez dohledu strojového učení](../resources/glossary.md#unsupervised-machine-learning) úloh.</span><span class="sxs-lookup"><span data-stu-id="c09af-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="c09af-124">Pokud chcete rozdělit datové sady ve skupinách tak, že prvky ve stejné skupině jsou u jiného než více podobné těm v jiných skupinách, použijte [clustering](../resources/tasks.md#clustering) machine learning úloh.</span><span class="sxs-lookup"><span data-stu-id="c09af-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c09af-125">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="c09af-125">Create a console application</span></span>

1. <span data-ttu-id="c09af-126">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c09af-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="c09af-127">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="c09af-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c09af-128">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="c09af-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c09af-129">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="c09af-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c09af-130">V **název** textového pole zadejte "IrisClustering" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c09af-130">In the **Name** text box, type "IrisClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="c09af-131">Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:</span><span class="sxs-lookup"><span data-stu-id="c09af-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="c09af-132">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="c09af-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c09af-133">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="c09af-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="c09af-134">Nainstalujte **Microsoft.ML** balíček NuGet:</span><span class="sxs-lookup"><span data-stu-id="c09af-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="c09af-135">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c09af-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c09af-136">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c09af-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="c09af-137">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="c09af-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="c09af-138">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="c09af-138">Prepare the data</span></span>

1. <span data-ttu-id="c09af-139">Stáhněte si [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dat nastavit a uložit ho. tím *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="c09af-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="c09af-140">Další informace o datové sady iris najdete v článku [datovou sadu Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) stránky Wikipedia a [datovou sadu Iris](http://archive.ics.uci.edu/ml/datasets/Iris) stránku, což je zdrojové datové sady.</span><span class="sxs-lookup"><span data-stu-id="c09af-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="c09af-141">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *iris.data* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c09af-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="c09af-142">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="c09af-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="c09af-143">*Iris.data* soubor obsahuje pět sloupců, které představují:</span><span class="sxs-lookup"><span data-stu-id="c09af-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="c09af-144">sepal length v cm</span><span class="sxs-lookup"><span data-stu-id="c09af-144">sepal length in centimetres</span></span>
- <span data-ttu-id="c09af-145">sepal width v cm</span><span class="sxs-lookup"><span data-stu-id="c09af-145">sepal width in centimetres</span></span>
- <span data-ttu-id="c09af-146">petal length v cm</span><span class="sxs-lookup"><span data-stu-id="c09af-146">petal length in centimetres</span></span>
- <span data-ttu-id="c09af-147">petal width v cm</span><span class="sxs-lookup"><span data-stu-id="c09af-147">petal width in centimetres</span></span>
- <span data-ttu-id="c09af-148">Typ květinu iris</span><span class="sxs-lookup"><span data-stu-id="c09af-148">type of iris flower</span></span>

<span data-ttu-id="c09af-149">Pro účely clusteringu příkladu v tomto kurzu ignoruje posledního sloupce.</span><span class="sxs-lookup"><span data-stu-id="c09af-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="c09af-150">Vytvoření datových tříd</span><span class="sxs-lookup"><span data-stu-id="c09af-150">Create data classes</span></span>

<span data-ttu-id="c09af-151">Vytvoření třídy pro vstupní data a předpovědí:</span><span class="sxs-lookup"><span data-stu-id="c09af-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="c09af-152">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="c09af-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="c09af-153">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="c09af-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="c09af-154">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c09af-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="c09af-155">Přidejte následující `using` směrnice do nového souboru:</span><span class="sxs-lookup"><span data-stu-id="c09af-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

<span data-ttu-id="c09af-156">Odeberte stávající definice třídy a přidejte následující kód, který definuje třídy `IrisData` a `ClusterPrediction`, možnosti *IrisData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="c09af-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

<span data-ttu-id="c09af-157">`IrisData` je třída vstupní data a obsahuje definice pro jednotlivé funkce z datové sady.</span><span class="sxs-lookup"><span data-stu-id="c09af-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="c09af-158">Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atributy indexů zdrojových sloupců v souboru datové sady.</span><span class="sxs-lookup"><span data-stu-id="c09af-158">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="c09af-159">`ClusterPrediction` Třída reprezentuje výstup model clusteringu u `IrisData` instance.</span><span class="sxs-lookup"><span data-stu-id="c09af-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="c09af-160">Použití [Názevsloupce](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut pro vytvoření vazby `PredictedClusterId` a `Distances` polím **PredictedLabel** a **skóre** sloupce v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c09af-160">Use the [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="c09af-161">V případě clusteru úloh tyto sloupce mají následující význam:</span><span class="sxs-lookup"><span data-stu-id="c09af-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="c09af-162">**PredictedLabel** sloupec obsahuje ID předpokládané clusteru.</span><span class="sxs-lookup"><span data-stu-id="c09af-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="c09af-163">**Skóre** sloupec obsahuje pole s kvadratických Euclidean vzdálenosti se centroids clusteru.</span><span class="sxs-lookup"><span data-stu-id="c09af-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="c09af-164">Délka pole je rovna počtu clusterů.</span><span class="sxs-lookup"><span data-stu-id="c09af-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="c09af-165">Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.</span><span class="sxs-lookup"><span data-stu-id="c09af-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="c09af-166">Definovat cesty k datům a model</span><span class="sxs-lookup"><span data-stu-id="c09af-166">Define data and model paths</span></span>

<span data-ttu-id="c09af-167">Přejděte zpět *Program.cs* a přidejte dvě pole pro uložení cesty k souboru datové sady a do souboru uložit model:</span><span class="sxs-lookup"><span data-stu-id="c09af-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="c09af-168">`_dataPath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="c09af-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="c09af-169">`_modelPath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="c09af-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="c09af-170">Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="c09af-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

<span data-ttu-id="c09af-171">Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="c09af-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="c09af-172">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="c09af-172">Create a learning pipeline</span></span>

<span data-ttu-id="c09af-173">Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="c09af-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

<span data-ttu-id="c09af-174">V `Main` metoda, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c09af-174">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

<span data-ttu-id="c09af-175">`Train` Metoda trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="c09af-175">The `Train` method trains the model.</span></span> <span data-ttu-id="c09af-176">Vytvoření metody hned pod `Main` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c09af-176">Create that method just below the `Main` method, using the following code:</span></span>

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

<span data-ttu-id="c09af-177">Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="c09af-177">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="c09af-178">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="c09af-178">Add the following code into the `Train` method:</span></span>

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a><span data-ttu-id="c09af-179">Načítání a transformace dat.</span><span class="sxs-lookup"><span data-stu-id="c09af-179">Load and transform data</span></span>

<span data-ttu-id="c09af-180">Prvním krokem k provedení je načíst trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="c09af-180">The first step to perform is to load the training data set.</span></span> <span data-ttu-id="c09af-181">V našem případě trénovací datové sady se ukládají v textovém souboru s cestu definovanou `_dataPath` pole.</span><span class="sxs-lookup"><span data-stu-id="c09af-181">In our case, the training data set is stored in the text file with a path defined by the `_dataPath` field.</span></span> <span data-ttu-id="c09af-182">Sloupce v souboru jsou oddělené čárkou (",").</span><span class="sxs-lookup"><span data-stu-id="c09af-182">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="c09af-183">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="c09af-183">Add the following code into the `Train` method:</span></span>

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

<span data-ttu-id="c09af-184">Dalším krokem je kombinací všech sloupců funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="c09af-184">The next step is to combine all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="c09af-185">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="c09af-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="c09af-186">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c09af-186">Add the following code:</span></span>

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="c09af-187">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="c09af-187">Choose a learning algorithm</span></span>

<span data-ttu-id="c09af-188">Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vyberte algoritmus učení (**learner**).</span><span class="sxs-lookup"><span data-stu-id="c09af-188">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="c09af-189">Learner trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="c09af-189">The learner trains the model.</span></span> <span data-ttu-id="c09af-190">Poskytuje ML.NET <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> student, který implementuje [algoritmus k-means](https://en.wikipedia.org/wiki/K-means_clustering) vylepšené metodou pro výběr centroids počáteční clusteru.</span><span class="sxs-lookup"><span data-stu-id="c09af-190">ML.NET provides a <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> learner that implements [k-means algorithm](https://en.wikipedia.org/wiki/K-means_clustering) with an improved method for choosing the initial cluster centroids.</span></span>

<span data-ttu-id="c09af-191">Přidejte následující kód do `Train` metoda po zpracování dat kód přidaný v předchozím kroku:</span><span class="sxs-lookup"><span data-stu-id="c09af-191">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

<span data-ttu-id="c09af-192">Použití <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> vlastnosti a určit tak počet clusterů.</span><span class="sxs-lookup"><span data-stu-id="c09af-192">Use the <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> property to specify number of clusters.</span></span> <span data-ttu-id="c09af-193">Výše uvedený kód určuje, že datová sada by měla lze rozdělit tři clustery.</span><span class="sxs-lookup"><span data-stu-id="c09af-193">The code above specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="c09af-194">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c09af-194">Train the model</span></span>

<span data-ttu-id="c09af-195">Kroky přidání v předchozích částech připravili kanálu pro školení, ale, že byly provedeny žádné.</span><span class="sxs-lookup"><span data-stu-id="c09af-195">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="c09af-196">`pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přijímá instanci `TInput` zadejte a vypíše instance `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="c09af-196">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="c09af-197">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="c09af-197">Add the following code into the `Train` method:</span></span>

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a><span data-ttu-id="c09af-198">Uložit model</span><span class="sxs-lookup"><span data-stu-id="c09af-198">Save the model</span></span>

<span data-ttu-id="c09af-199">V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="c09af-199">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="c09af-200">Uložit model do souboru .zip, přidejte následující kód, který `Main` metodu pod volání `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="c09af-200">To save your model to a .zip file, add the following code to the `Main` method below the call to the `Train` method:</span></span>

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

<span data-ttu-id="c09af-201">Pomocí `await` v `Main` znamená, že metoda `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:</span><span class="sxs-lookup"><span data-stu-id="c09af-201">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

<span data-ttu-id="c09af-202">Budete také muset přidat následující `using` direktiv v horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="c09af-202">You also need to add the following `using` directive at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

<span data-ttu-id="c09af-203">Vzhledem k tomu, `async Main` metoda je funkce přidané v jazyce C# 7.1 a výchozí jazyková verze projektu je C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="c09af-203">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="c09af-204">Chcete-li to mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c09af-204">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="c09af-205">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c09af-205">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="c09af-206">V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="c09af-206">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="c09af-207">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c09af-207">Select the **OK** button.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="c09af-208">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="c09af-208">Use the model for predictions</span></span>

<span data-ttu-id="c09af-209">Vytvořte `TestIrisData` třídy pro uložení testovací data instancí:</span><span class="sxs-lookup"><span data-stu-id="c09af-209">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="c09af-210">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="c09af-210">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="c09af-211">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="c09af-211">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="c09af-212">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c09af-212">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="c09af-213">Upravte třídu pro statické stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c09af-213">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

<span data-ttu-id="c09af-214">Tento kurz představuje jednu instanci data iris v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="c09af-214">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="c09af-215">Můžete přidat další scénáře můžete experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="c09af-215">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="c09af-216">Přidejte následující kód do `TestIrisData` třídy:</span><span class="sxs-lookup"><span data-stu-id="c09af-216">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

<span data-ttu-id="c09af-217">Chcete-li zjistit, ke kterému zadaná položka patří do clusteru, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="c09af-217">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

<span data-ttu-id="c09af-218">Spusťte program clusteru, které obsahuje instanci zadaného data a kvadratických vzdálenosti směrem dovnitř od této instance na centroids clusteru.</span><span class="sxs-lookup"><span data-stu-id="c09af-218">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="c09af-219">Výsledky by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="c09af-219">Your results should be similar to the following.</span></span> <span data-ttu-id="c09af-220">Jak zpracovává kanálu, může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c09af-220">As the pipeline processes, it might display warnings or processing messages.</span></span> <span data-ttu-id="c09af-221">Ty se odstranily z následující výstup pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="c09af-221">These have been removed from the following output for clarity.</span></span>

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

<span data-ttu-id="c09af-222">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="c09af-222">Congratulations!</span></span> <span data-ttu-id="c09af-223">Teď jste úspěšně sestaven služby machine learning model iris clustering a použít ho k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="c09af-223">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="c09af-224">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="c09af-224">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c09af-225">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c09af-225">Next steps</span></span>

<span data-ttu-id="c09af-226">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="c09af-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="c09af-227">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="c09af-227">Understand the problem</span></span>
> - <span data-ttu-id="c09af-228">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="c09af-228">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="c09af-229">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="c09af-229">Prepare the data</span></span>
> - <span data-ttu-id="c09af-230">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="c09af-230">Load and transform the data</span></span>
> - <span data-ttu-id="c09af-231">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="c09af-231">Choose a learning algorithm</span></span>
> - <span data-ttu-id="c09af-232">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c09af-232">Train the model</span></span>
> - <span data-ttu-id="c09af-233">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="c09af-233">Use the model for predictions</span></span>

<span data-ttu-id="c09af-234">Přečtěte si našeho úložiště GitHub, pokračujte ve čtení a najít další ukázky.</span><span class="sxs-lookup"><span data-stu-id="c09af-234">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c09af-235">DotNet/machinelearning úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="c09af-235">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
