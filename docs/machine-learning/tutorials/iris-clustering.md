---
title: 'Tutorial: Categorize iris flowers - k-means clustering'
description: Learn how to use ML.NET in a clustering scenario
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
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="17cfa-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span><span class="sxs-lookup"><span data-stu-id="17cfa-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="17cfa-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="17cfa-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="17cfa-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="17cfa-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="17cfa-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="17cfa-106">Understand the problem</span></span>
> - <span data-ttu-id="17cfa-107">Select the appropriate machine learning task</span><span class="sxs-lookup"><span data-stu-id="17cfa-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="17cfa-108">Prepare the data</span><span class="sxs-lookup"><span data-stu-id="17cfa-108">Prepare the data</span></span>
> - <span data-ttu-id="17cfa-109">Load and transform the data</span><span class="sxs-lookup"><span data-stu-id="17cfa-109">Load and transform the data</span></span>
> - <span data-ttu-id="17cfa-110">Choose a learning algorithm</span><span class="sxs-lookup"><span data-stu-id="17cfa-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="17cfa-111">Train the model</span><span class="sxs-lookup"><span data-stu-id="17cfa-111">Train the model</span></span>
> - <span data-ttu-id="17cfa-112">Use the model for predictions</span><span class="sxs-lookup"><span data-stu-id="17cfa-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17cfa-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17cfa-113">Prerequisites</span></span>

- <span data-ttu-id="17cfa-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span><span class="sxs-lookup"><span data-stu-id="17cfa-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="17cfa-115">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="17cfa-115">Understand the problem</span></span>

<span data-ttu-id="17cfa-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span><span class="sxs-lookup"><span data-stu-id="17cfa-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="17cfa-117">Those features are the length and width of a sepal and the length and width of a petal.</span><span class="sxs-lookup"><span data-stu-id="17cfa-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="17cfa-118">For this tutorial, assume that the type of each flower is unknown.</span><span class="sxs-lookup"><span data-stu-id="17cfa-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="17cfa-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span><span class="sxs-lookup"><span data-stu-id="17cfa-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="17cfa-120">Select the appropriate machine learning task</span><span class="sxs-lookup"><span data-stu-id="17cfa-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="17cfa-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span><span class="sxs-lookup"><span data-stu-id="17cfa-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="17cfa-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span><span class="sxs-lookup"><span data-stu-id="17cfa-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="17cfa-123">Create a console application</span><span class="sxs-lookup"><span data-stu-id="17cfa-123">Create a console application</span></span>

1. <span data-ttu-id="17cfa-124">Open Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17cfa-124">Open Visual Studio.</span></span> <span data-ttu-id="17cfa-125">Select **File** > **New** > **Project** from the menu bar.</span><span class="sxs-lookup"><span data-stu-id="17cfa-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="17cfa-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span><span class="sxs-lookup"><span data-stu-id="17cfa-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="17cfa-127">Then select the **Console App (.NET Core)** project template.</span><span class="sxs-lookup"><span data-stu-id="17cfa-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="17cfa-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span><span class="sxs-lookup"><span data-stu-id="17cfa-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="17cfa-129">Create a directory named *Data* in your project to store the data set and model files:</span><span class="sxs-lookup"><span data-stu-id="17cfa-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="17cfa-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span><span class="sxs-lookup"><span data-stu-id="17cfa-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="17cfa-131">Type "Data" and hit Enter.</span><span class="sxs-lookup"><span data-stu-id="17cfa-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="17cfa-132">Install the **Microsoft.ML** NuGet package:</span><span class="sxs-lookup"><span data-stu-id="17cfa-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="17cfa-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="17cfa-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="17cfa-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span><span class="sxs-lookup"><span data-stu-id="17cfa-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="17cfa-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span><span class="sxs-lookup"><span data-stu-id="17cfa-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="17cfa-136">Prepare the data</span><span class="sxs-lookup"><span data-stu-id="17cfa-136">Prepare the data</span></span>

1. <span data-ttu-id="17cfa-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span><span class="sxs-lookup"><span data-stu-id="17cfa-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="17cfa-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span><span class="sxs-lookup"><span data-stu-id="17cfa-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="17cfa-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span><span class="sxs-lookup"><span data-stu-id="17cfa-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="17cfa-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span><span class="sxs-lookup"><span data-stu-id="17cfa-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="17cfa-141">The *iris.data* file contains five columns that represent:</span><span class="sxs-lookup"><span data-stu-id="17cfa-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="17cfa-142">sepal length in centimetres</span><span class="sxs-lookup"><span data-stu-id="17cfa-142">sepal length in centimetres</span></span>
- <span data-ttu-id="17cfa-143">sepal width in centimetres</span><span class="sxs-lookup"><span data-stu-id="17cfa-143">sepal width in centimetres</span></span>
- <span data-ttu-id="17cfa-144">petal length in centimetres</span><span class="sxs-lookup"><span data-stu-id="17cfa-144">petal length in centimetres</span></span>
- <span data-ttu-id="17cfa-145">petal width in centimetres</span><span class="sxs-lookup"><span data-stu-id="17cfa-145">petal width in centimetres</span></span>
- <span data-ttu-id="17cfa-146">type of iris flower</span><span class="sxs-lookup"><span data-stu-id="17cfa-146">type of iris flower</span></span>

<span data-ttu-id="17cfa-147">For the sake of the clustering example, this tutorial ignores the last column.</span><span class="sxs-lookup"><span data-stu-id="17cfa-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="17cfa-148">Create data classes</span><span class="sxs-lookup"><span data-stu-id="17cfa-148">Create data classes</span></span>

<span data-ttu-id="17cfa-149">Create classes for the input data and the predictions:</span><span class="sxs-lookup"><span data-stu-id="17cfa-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="17cfa-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span><span class="sxs-lookup"><span data-stu-id="17cfa-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="17cfa-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="17cfa-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="17cfa-152">Then, select the **Add** button.</span><span class="sxs-lookup"><span data-stu-id="17cfa-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="17cfa-153">Add the following `using` directive to the new file:</span><span class="sxs-lookup"><span data-stu-id="17cfa-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="17cfa-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span><span class="sxs-lookup"><span data-stu-id="17cfa-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="17cfa-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span><span class="sxs-lookup"><span data-stu-id="17cfa-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="17cfa-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span><span class="sxs-lookup"><span data-stu-id="17cfa-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="17cfa-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span><span class="sxs-lookup"><span data-stu-id="17cfa-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="17cfa-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span><span class="sxs-lookup"><span data-stu-id="17cfa-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="17cfa-159">In case of the clustering task those columns have the following meaning:</span><span class="sxs-lookup"><span data-stu-id="17cfa-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="17cfa-160">**PredictedLabel** column contains the ID of the predicted cluster.</span><span class="sxs-lookup"><span data-stu-id="17cfa-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="17cfa-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span><span class="sxs-lookup"><span data-stu-id="17cfa-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="17cfa-162">The array length is equal to the number of clusters.</span><span class="sxs-lookup"><span data-stu-id="17cfa-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="17cfa-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span><span class="sxs-lookup"><span data-stu-id="17cfa-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="17cfa-164">Define data and model paths</span><span class="sxs-lookup"><span data-stu-id="17cfa-164">Define data and model paths</span></span>

<span data-ttu-id="17cfa-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span><span class="sxs-lookup"><span data-stu-id="17cfa-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="17cfa-166">`_dataPath` contains the path to the file with the data set used to train the model.</span><span class="sxs-lookup"><span data-stu-id="17cfa-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="17cfa-167">`_modelPath` contains the path to the file where the trained model is stored.</span><span class="sxs-lookup"><span data-stu-id="17cfa-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="17cfa-168">Add the following code right above the `Main` method to specify those paths:</span><span class="sxs-lookup"><span data-stu-id="17cfa-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="17cfa-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span><span class="sxs-lookup"><span data-stu-id="17cfa-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="17cfa-170">Create ML context</span><span class="sxs-lookup"><span data-stu-id="17cfa-170">Create ML context</span></span>

<span data-ttu-id="17cfa-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span><span class="sxs-lookup"><span data-stu-id="17cfa-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="17cfa-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span><span class="sxs-lookup"><span data-stu-id="17cfa-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="17cfa-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span><span class="sxs-lookup"><span data-stu-id="17cfa-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="17cfa-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="17cfa-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="17cfa-175">Setup data loading</span><span class="sxs-lookup"><span data-stu-id="17cfa-175">Setup data loading</span></span>

<span data-ttu-id="17cfa-176">Add the following code to the `Main` method to setup the way to load data:</span><span class="sxs-lookup"><span data-stu-id="17cfa-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="17cfa-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span><span class="sxs-lookup"><span data-stu-id="17cfa-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="17cfa-178">Create a learning pipeline</span><span class="sxs-lookup"><span data-stu-id="17cfa-178">Create a learning pipeline</span></span>

<span data-ttu-id="17cfa-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span><span class="sxs-lookup"><span data-stu-id="17cfa-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="17cfa-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span><span class="sxs-lookup"><span data-stu-id="17cfa-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="17cfa-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span><span class="sxs-lookup"><span data-stu-id="17cfa-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="17cfa-182">Add the following code to the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="17cfa-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="17cfa-183">The code specifies that the data set should be split in three clusters.</span><span class="sxs-lookup"><span data-stu-id="17cfa-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="17cfa-184">Train the model</span><span class="sxs-lookup"><span data-stu-id="17cfa-184">Train the model</span></span>

<span data-ttu-id="17cfa-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span><span class="sxs-lookup"><span data-stu-id="17cfa-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="17cfa-186">Add the following line to the `Main` method to perform data loading and model training:</span><span class="sxs-lookup"><span data-stu-id="17cfa-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="17cfa-187">Save the model</span><span class="sxs-lookup"><span data-stu-id="17cfa-187">Save the model</span></span>

<span data-ttu-id="17cfa-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span><span class="sxs-lookup"><span data-stu-id="17cfa-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="17cfa-189">To save your model to a .zip file, add the following code to the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="17cfa-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="17cfa-190">Use the model for predictions</span><span class="sxs-lookup"><span data-stu-id="17cfa-190">Use the model for predictions</span></span>

<span data-ttu-id="17cfa-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span><span class="sxs-lookup"><span data-stu-id="17cfa-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="17cfa-192">Add the following line to the `Main` method to create an instance of that class:</span><span class="sxs-lookup"><span data-stu-id="17cfa-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="17cfa-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="17cfa-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="17cfa-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span><span class="sxs-lookup"><span data-stu-id="17cfa-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="17cfa-195">It's acceptable to use in single-threaded or prototype environments.</span><span class="sxs-lookup"><span data-stu-id="17cfa-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="17cfa-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span><span class="sxs-lookup"><span data-stu-id="17cfa-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="17cfa-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="17cfa-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="17cfa-198">`PredictionEnginePool` service extension is currently in preview.</span><span class="sxs-lookup"><span data-stu-id="17cfa-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="17cfa-199">Create the `TestIrisData` class to house test data instances:</span><span class="sxs-lookup"><span data-stu-id="17cfa-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="17cfa-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span><span class="sxs-lookup"><span data-stu-id="17cfa-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="17cfa-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="17cfa-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="17cfa-202">Then, select the **Add** button.</span><span class="sxs-lookup"><span data-stu-id="17cfa-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="17cfa-203">Modify the class to be static like in the following example:</span><span class="sxs-lookup"><span data-stu-id="17cfa-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="17cfa-204">This tutorial introduces one iris data instance within this class.</span><span class="sxs-lookup"><span data-stu-id="17cfa-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="17cfa-205">You can add other scenarios to experiment with the model.</span><span class="sxs-lookup"><span data-stu-id="17cfa-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="17cfa-206">Add the following code into the `TestIrisData` class:</span><span class="sxs-lookup"><span data-stu-id="17cfa-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="17cfa-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="17cfa-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="17cfa-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span><span class="sxs-lookup"><span data-stu-id="17cfa-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="17cfa-209">Your results should be similar to the following:</span><span class="sxs-lookup"><span data-stu-id="17cfa-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="17cfa-210">Congratulations!</span><span class="sxs-lookup"><span data-stu-id="17cfa-210">Congratulations!</span></span> <span data-ttu-id="17cfa-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span><span class="sxs-lookup"><span data-stu-id="17cfa-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="17cfa-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span><span class="sxs-lookup"><span data-stu-id="17cfa-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="17cfa-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="17cfa-213">Next steps</span></span>

<span data-ttu-id="17cfa-214">In this tutorial, you learned how to:</span><span class="sxs-lookup"><span data-stu-id="17cfa-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="17cfa-215">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="17cfa-215">Understand the problem</span></span>
> - <span data-ttu-id="17cfa-216">Select the appropriate machine learning task</span><span class="sxs-lookup"><span data-stu-id="17cfa-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="17cfa-217">Prepare the data</span><span class="sxs-lookup"><span data-stu-id="17cfa-217">Prepare the data</span></span>
> - <span data-ttu-id="17cfa-218">Load and transform the data</span><span class="sxs-lookup"><span data-stu-id="17cfa-218">Load and transform the data</span></span>
> - <span data-ttu-id="17cfa-219">Choose a learning algorithm</span><span class="sxs-lookup"><span data-stu-id="17cfa-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="17cfa-220">Train the model</span><span class="sxs-lookup"><span data-stu-id="17cfa-220">Train the model</span></span>
> - <span data-ttu-id="17cfa-221">Use the model for predictions</span><span class="sxs-lookup"><span data-stu-id="17cfa-221">Use the model for predictions</span></span>

<span data-ttu-id="17cfa-222">Check out our GitHub repository to continue learning and find more samples.</span><span class="sxs-lookup"><span data-stu-id="17cfa-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="17cfa-223">dotnet/machinelearning GitHub repository</span><span class="sxs-lookup"><span data-stu-id="17cfa-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
