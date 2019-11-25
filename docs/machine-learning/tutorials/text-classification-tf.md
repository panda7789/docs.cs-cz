---
title: 'Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model'
description: This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments. The binary sentiment classifier is a C# console application developed using Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 8c3544b60b1fba1d419ca091b0a1d85fbbdbe2d6
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204926"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="2cbc1-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span><span class="sxs-lookup"><span data-stu-id="2cbc1-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="2cbc1-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="2cbc1-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="2cbc1-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="2cbc1-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="2cbc1-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2cbc1-110">Load a pre-trained TensorFlow model</span><span class="sxs-lookup"><span data-stu-id="2cbc1-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="2cbc1-111">Transform website comment text into features suitable for the model</span><span class="sxs-lookup"><span data-stu-id="2cbc1-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="2cbc1-112">Use the model to make a prediction</span><span class="sxs-lookup"><span data-stu-id="2cbc1-112">Use the model to make a prediction</span></span>

<span data-ttu-id="2cbc1-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2cbc1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cbc1-114">Prerequisites</span></span>

* <span data-ttu-id="2cbc1-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="2cbc1-116">Instalace</span><span class="sxs-lookup"><span data-stu-id="2cbc1-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="2cbc1-117">Create the application</span><span class="sxs-lookup"><span data-stu-id="2cbc1-117">Create the application</span></span>

1. <span data-ttu-id="2cbc1-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="2cbc1-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="2cbc1-119">Create a directory named *Data* in your project to save your data set files.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="2cbc1-120">Install the **Microsoft.ML NuGet Package**:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2cbc1-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2cbc1-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="2cbc1-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="2cbc1-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="2cbc1-125">Add the TensorFlow model to the project</span><span class="sxs-lookup"><span data-stu-id="2cbc1-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="2cbc1-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="2cbc1-127">The model is in TensorFlow SavedModel format.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="2cbc1-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="2cbc1-129">The zip file contains:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-129">The zip file contains:</span></span>

    * <span data-ttu-id="2cbc1-130">`saved_model.pb`: the TensorFlow model itself.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="2cbc1-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="2cbc1-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="2cbc1-133">The mapping is used to generate the input features for the TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="2cbc1-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="2cbc1-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model directory contents](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="2cbc1-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="2cbc1-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="2cbc1-139">Add using statements and global variables</span><span class="sxs-lookup"><span data-stu-id="2cbc1-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="2cbc1-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="2cbc1-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="2cbc1-142">`_modelPath` is the file path of the trained model.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="2cbc1-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="2cbc1-144">Model the data</span><span class="sxs-lookup"><span data-stu-id="2cbc1-144">Model the data</span></span>

<span data-ttu-id="2cbc1-145">Movie reviews are free form text.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-145">Movie reviews are free form text.</span></span> <span data-ttu-id="2cbc1-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="2cbc1-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="2cbc1-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="2cbc1-149">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2cbc1-149">Property</span></span>| <span data-ttu-id="2cbc1-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2cbc1-150">Value</span></span>|<span data-ttu-id="2cbc1-151">Typ</span><span class="sxs-lookup"><span data-stu-id="2cbc1-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="2cbc1-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="2cbc1-152">ReviewText</span></span>|<span data-ttu-id="2cbc1-153">this film is really good</span><span class="sxs-lookup"><span data-stu-id="2cbc1-153">this film is really good</span></span>|<span data-ttu-id="2cbc1-154">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="2cbc1-154">string</span></span>|
|<span data-ttu-id="2cbc1-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="2cbc1-155">VariableLengthFeatures</span></span>|<span data-ttu-id="2cbc1-156">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="2cbc1-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="2cbc1-157">int[]</span><span class="sxs-lookup"><span data-stu-id="2cbc1-157">int[]</span></span>|

<span data-ttu-id="2cbc1-158">The variable length feature array is then resized to a fixed length of 600.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="2cbc1-159">This is the length that the TensorFlow model expects.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="2cbc1-160">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2cbc1-160">Property</span></span>| <span data-ttu-id="2cbc1-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2cbc1-161">Value</span></span>|<span data-ttu-id="2cbc1-162">Typ</span><span class="sxs-lookup"><span data-stu-id="2cbc1-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="2cbc1-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="2cbc1-163">ReviewText</span></span>|<span data-ttu-id="2cbc1-164">this film is really good</span><span class="sxs-lookup"><span data-stu-id="2cbc1-164">this film is really good</span></span>|<span data-ttu-id="2cbc1-165">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="2cbc1-165">string</span></span>|
|<span data-ttu-id="2cbc1-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="2cbc1-166">VariableLengthFeatures</span></span>|<span data-ttu-id="2cbc1-167">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="2cbc1-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="2cbc1-168">int[]</span><span class="sxs-lookup"><span data-stu-id="2cbc1-168">int[]</span></span>|
|<span data-ttu-id="2cbc1-169">Funkce</span><span class="sxs-lookup"><span data-stu-id="2cbc1-169">Features</span></span>|<span data-ttu-id="2cbc1-170">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="2cbc1-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="2cbc1-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="2cbc1-171">int[600]</span></span>|

1. <span data-ttu-id="2cbc1-172">Create a class for your input data, after the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="2cbc1-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span><span class="sxs-lookup"><span data-stu-id="2cbc1-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="2cbc1-174">Create a class for the variable length features, after the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="2cbc1-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="2cbc1-176">All of the vector elements must be the same type.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="2cbc1-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="2cbc1-178">This class is used in the `ResizeFeatures` action.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="2cbc1-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="2cbc1-180">Create a class for the fixed length features, after the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="2cbc1-181">This class is used in the `ResizeFeatures` action.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="2cbc1-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="2cbc1-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="2cbc1-184">You cannot change this property name.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="2cbc1-185">Create a class for the prediction after the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="2cbc1-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="2cbc1-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="2cbc1-188">Create the MLContext, lookup dictionary, and action to resize features</span><span class="sxs-lookup"><span data-stu-id="2cbc1-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="2cbc1-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="2cbc1-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2cbc1-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="2cbc1-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="2cbc1-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="2cbc1-194">Word</span><span class="sxs-lookup"><span data-stu-id="2cbc1-194">Word</span></span>     |<span data-ttu-id="2cbc1-195">Index</span><span class="sxs-lookup"><span data-stu-id="2cbc1-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="2cbc1-196">kids</span><span class="sxs-lookup"><span data-stu-id="2cbc1-196">kids</span></span>     |  <span data-ttu-id="2cbc1-197">362</span><span class="sxs-lookup"><span data-stu-id="2cbc1-197">362</span></span>    |
    |<span data-ttu-id="2cbc1-198">want</span><span class="sxs-lookup"><span data-stu-id="2cbc1-198">want</span></span>     |  <span data-ttu-id="2cbc1-199">181</span><span class="sxs-lookup"><span data-stu-id="2cbc1-199">181</span></span>    |
    |<span data-ttu-id="2cbc1-200">wrong</span><span class="sxs-lookup"><span data-stu-id="2cbc1-200">wrong</span></span>    |  <span data-ttu-id="2cbc1-201">355</span><span class="sxs-lookup"><span data-stu-id="2cbc1-201">355</span></span>    |
    |<span data-ttu-id="2cbc1-202">efekty</span><span class="sxs-lookup"><span data-stu-id="2cbc1-202">effects</span></span>  |  <span data-ttu-id="2cbc1-203">302</span><span class="sxs-lookup"><span data-stu-id="2cbc1-203">302</span></span>    |
    |<span data-ttu-id="2cbc1-204">feeling</span><span class="sxs-lookup"><span data-stu-id="2cbc1-204">feeling</span></span>  |  <span data-ttu-id="2cbc1-205">547</span><span class="sxs-lookup"><span data-stu-id="2cbc1-205">547</span></span>    |

    <span data-ttu-id="2cbc1-206">Add the code below to create the lookup map:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="2cbc1-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="2cbc1-208">Load the pre-trained TensorFlow model</span><span class="sxs-lookup"><span data-stu-id="2cbc1-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="2cbc1-209">Add code to load the TensorFlow model:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="2cbc1-210">Once the model is loaded, you can extract its input and output schema.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="2cbc1-211">The schemas are displayed for interest and learning only.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="2cbc1-212">You do not need this code for the final application to function:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="2cbc1-213">The input schema is the fixed-length array of integer encoded words.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="2cbc1-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span><span class="sxs-lookup"><span data-stu-id="2cbc1-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="2cbc1-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="2cbc1-216">Create the ML.NET pipeline</span><span class="sxs-lookup"><span data-stu-id="2cbc1-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="2cbc1-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="2cbc1-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="2cbc1-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="2cbc1-220">Map the words onto their integer encoding using the lookup table that you declared above:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="2cbc1-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="2cbc1-222">Classify the input with the loaded TensorFlow model:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="2cbc1-223">The TensorFlow model output is called `Prediction/Softmax`.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="2cbc1-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="2cbc1-225">You cannot change this name.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-225">You cannot change this name.</span></span>

1. <span data-ttu-id="2cbc1-226">Create a new column for the output prediction:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="2cbc1-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="2cbc1-228">The `/` character is not allowed in a C# property name.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="2cbc1-229">Create the ML.NET model from the pipeline</span><span class="sxs-lookup"><span data-stu-id="2cbc1-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="2cbc1-230">Add the code to create the model from the pipeline:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="2cbc1-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="2cbc1-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="2cbc1-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="2cbc1-234">Use the model to make a prediction</span><span class="sxs-lookup"><span data-stu-id="2cbc1-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="2cbc1-235">Add the `PredictSentiment` method below the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="2cbc1-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="2cbc1-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2cbc1-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2cbc1-239">It's acceptable to use in single-threaded or prototype environments.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2cbc1-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2cbc1-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="2cbc1-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2cbc1-242">`PredictionEnginePool` service extension is currently in preview.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="2cbc1-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="2cbc1-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="2cbc1-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="2cbc1-246">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2cbc1-246">Property</span></span>| <span data-ttu-id="2cbc1-247">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2cbc1-247">Value</span></span>|<span data-ttu-id="2cbc1-248">Typ</span><span class="sxs-lookup"><span data-stu-id="2cbc1-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="2cbc1-249">Prediction</span><span class="sxs-lookup"><span data-stu-id="2cbc1-249">Prediction</span></span>|<span data-ttu-id="2cbc1-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="2cbc1-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="2cbc1-251">float[]</span><span class="sxs-lookup"><span data-stu-id="2cbc1-251">float[]</span></span>|

1. <span data-ttu-id="2cbc1-252">Display sentiment prediction using the following code:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="2cbc1-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="2cbc1-254">Výsledky</span><span class="sxs-lookup"><span data-stu-id="2cbc1-254">Results</span></span>

<span data-ttu-id="2cbc1-255">Build and run your application.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-255">Build and run your application.</span></span>

<span data-ttu-id="2cbc1-256">Your results should be similar to the following.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-256">Your results should be similar to the following.</span></span> <span data-ttu-id="2cbc1-257">During processing, messages are displayed.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-257">During processing, messages are displayed.</span></span> <span data-ttu-id="2cbc1-258">You may see warnings, or processing messages.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2cbc1-259">These messages have been removed from the following results for clarity.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="2cbc1-260">Congratulations!</span><span class="sxs-lookup"><span data-stu-id="2cbc1-260">Congratulations!</span></span> <span data-ttu-id="2cbc1-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="2cbc1-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span><span class="sxs-lookup"><span data-stu-id="2cbc1-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="2cbc1-263">In this tutorial, you learned how to:</span><span class="sxs-lookup"><span data-stu-id="2cbc1-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2cbc1-264">Load a pre-trained TensorFlow model</span><span class="sxs-lookup"><span data-stu-id="2cbc1-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="2cbc1-265">Transform website comment text into features suitable for the model</span><span class="sxs-lookup"><span data-stu-id="2cbc1-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="2cbc1-266">Use the model to make a prediction</span><span class="sxs-lookup"><span data-stu-id="2cbc1-266">Use the model to make a prediction</span></span>
