---
title: 'Kurz: Analýza míněních recenzí filmů pomocí předem připraveného modelu TensorFlow'
description: V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu. Mínění třídění binárního prostředí C# je Konzolová aplikace vyvinutá pomocí sady Visual Studio.
ms.date: 09/11/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 38b935814d713284dae1ca931b90c63bbcac332b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216894"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="fed65-104">Kurz: Analýza míněních recenzí filmů pomocí předem připraveného modelu TensorFlow v ML.NET</span><span class="sxs-lookup"><span data-stu-id="fed65-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="fed65-105">V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu.</span><span class="sxs-lookup"><span data-stu-id="fed65-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="fed65-106">Mínění třídění binárního prostředí C# je Konzolová aplikace vyvinutá pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fed65-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="fed65-107">Model TensorFlow použitý v tomto kurzu byl vyškolen pomocí recenzí filmů z databáze IMDB.</span><span class="sxs-lookup"><span data-stu-id="fed65-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="fed65-108">Jakmile dokončíte vývoj aplikace, budete moci zadat text recenze filmu a aplikace vám oznámí, zda má recenze pozitivní nebo negativní mínění.</span><span class="sxs-lookup"><span data-stu-id="fed65-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="fed65-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="fed65-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fed65-110">Načtení předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="fed65-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="fed65-111">Transformovat text komentáře webu k funkcím vhodným pro model</span><span class="sxs-lookup"><span data-stu-id="fed65-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="fed65-112">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="fed65-112">Use the model to make a prediction</span></span>

<span data-ttu-id="fed65-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="fed65-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fed65-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fed65-114">Prerequisites</span></span>

* <span data-ttu-id="fed65-115">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="fed65-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="fed65-116">Instalace</span><span class="sxs-lookup"><span data-stu-id="fed65-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="fed65-117">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="fed65-117">Create the application</span></span>

1. <span data-ttu-id="fed65-118">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="fed65-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="fed65-119">Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.</span><span class="sxs-lookup"><span data-stu-id="fed65-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="fed65-120">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="fed65-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="fed65-121">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fed65-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="fed65-122">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="fed65-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="fed65-123">Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček.</span><span class="sxs-lookup"><span data-stu-id="fed65-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="fed65-124">Opakujte tento postup pro **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="fed65-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="fed65-125">Přidání modelu TensorFlow do projektu</span><span class="sxs-lookup"><span data-stu-id="fed65-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="fed65-126">Model pro tento kurz je z úložiště GitHub [/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="fed65-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="fed65-127">Model je ve formátu TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="fed65-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="fed65-128">Stáhněte si [soubor zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="fed65-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="fed65-129">Soubor zip obsahuje:</span><span class="sxs-lookup"><span data-stu-id="fed65-129">The zip file contains:</span></span>

    * <span data-ttu-id="fed65-130">`saved_model.pb`: TensorFlow samotný model.</span><span class="sxs-lookup"><span data-stu-id="fed65-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="fed65-131">Model přebírá pevnou délku (Size 600) celočíselné pole funkcí reprezentující text v řetězci IMDB revize a vytvoří výstup dvou pravděpodobností, které se sčítají 1: pravděpodobnost, že vstupní revize má pozitivní mínění a pravděpodobnost, že kontrola vstupu má negativní mínění</span><span class="sxs-lookup"><span data-stu-id="fed65-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="fed65-132">`imdb_word_index.csv`: mapování jednotlivých slov na celočíselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fed65-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="fed65-133">Mapování slouží k vygenerování vstupních funkcí modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fed65-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="fed65-134">Zkopírujte obsah nejvnitřnějšího `sentiment_model` adresáře do adresáře projektu `sentiment_model` *TextClassificationTF* .</span><span class="sxs-lookup"><span data-stu-id="fed65-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="fed65-135">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="fed65-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![obsah adresáře sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="fed65-137">V Průzkumník řešení klikněte pravým tlačítkem myši na každý ze souborů v `sentiment_model` adresáři a v podadresáři a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fed65-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="fed65-138">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="fed65-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="fed65-139">Přidat příkazy using a globální proměnné</span><span class="sxs-lookup"><span data-stu-id="fed65-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="fed65-140">Do horní části souboru `using` *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="fed65-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="fed65-141">Vytvořte dvě globální proměnné přímo nad `Main` metodu pro uchování cesty k souboru uloženého modelu a délku vektoru funkce.</span><span class="sxs-lookup"><span data-stu-id="fed65-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="fed65-142">`_modelPath`je cesta k souboru trained modelu.</span><span class="sxs-lookup"><span data-stu-id="fed65-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="fed65-143">`FeatureLength`je délka pole funkce celého čísla, které model očekává.</span><span class="sxs-lookup"><span data-stu-id="fed65-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="fed65-144">Modelování dat</span><span class="sxs-lookup"><span data-stu-id="fed65-144">Model the data</span></span>

<span data-ttu-id="fed65-145">Recenze filmů je text bezplatné Form.</span><span class="sxs-lookup"><span data-stu-id="fed65-145">Movie reviews are free form text.</span></span> <span data-ttu-id="fed65-146">Vaše aplikace převede text na vstupní formát očekávaný modelem v řadě diskrétních fází.</span><span class="sxs-lookup"><span data-stu-id="fed65-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="fed65-147">První je rozdělit text na samostatná slova a použít poskytnutý soubor mapování pro mapování jednotlivých slov na celočíselné kódování.</span><span class="sxs-lookup"><span data-stu-id="fed65-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="fed65-148">Výsledkem této transformace je pole celé číslo proměnné s délkou odpovídající počtu slov ve větě.</span><span class="sxs-lookup"><span data-stu-id="fed65-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="fed65-149">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fed65-149">Property</span></span>| <span data-ttu-id="fed65-150">Value</span><span class="sxs-lookup"><span data-stu-id="fed65-150">Value</span></span>|<span data-ttu-id="fed65-151">type</span><span class="sxs-lookup"><span data-stu-id="fed65-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="fed65-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="fed65-152">ReviewText</span></span>|<span data-ttu-id="fed65-153">Tato film je skutečně dobrá</span><span class="sxs-lookup"><span data-stu-id="fed65-153">this film is really good</span></span>|<span data-ttu-id="fed65-154">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="fed65-154">string</span></span>|
|<span data-ttu-id="fed65-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="fed65-155">VariableLengthFeatures</span></span>|<span data-ttu-id="fed65-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="fed65-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="fed65-157">int []</span><span class="sxs-lookup"><span data-stu-id="fed65-157">int[]</span></span>|

<span data-ttu-id="fed65-158">Velikost pole s proměnnou délkou se pak změní na pevně stanovenou délku 600.</span><span class="sxs-lookup"><span data-stu-id="fed65-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="fed65-159">Jedná se o délku, kterou model TensorFlow očekává.</span><span class="sxs-lookup"><span data-stu-id="fed65-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="fed65-160">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fed65-160">Property</span></span>| <span data-ttu-id="fed65-161">Value</span><span class="sxs-lookup"><span data-stu-id="fed65-161">Value</span></span>|<span data-ttu-id="fed65-162">Typ</span><span class="sxs-lookup"><span data-stu-id="fed65-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="fed65-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="fed65-163">ReviewText</span></span>|<span data-ttu-id="fed65-164">Tato film je skutečně dobrá</span><span class="sxs-lookup"><span data-stu-id="fed65-164">this film is really good</span></span>|<span data-ttu-id="fed65-165">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="fed65-165">string</span></span>|
|<span data-ttu-id="fed65-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="fed65-166">VariableLengthFeatures</span></span>|<span data-ttu-id="fed65-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="fed65-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="fed65-168">int []</span><span class="sxs-lookup"><span data-stu-id="fed65-168">int[]</span></span>|
|<span data-ttu-id="fed65-169">Funkce</span><span class="sxs-lookup"><span data-stu-id="fed65-169">Features</span></span>|<span data-ttu-id="fed65-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="fed65-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="fed65-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="fed65-171">int[600]</span></span>|

1. <span data-ttu-id="fed65-172">Vytvořte třídu pro vstupní data za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="fed65-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="fed65-173">Vstupní datová třída `MovieReview` `string` obsahuje komentář pro uživatele (`ReviewText`).</span><span class="sxs-lookup"><span data-stu-id="fed65-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="fed65-174">Vytvořte třídu pro funkce s proměnlivou délkou za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="fed65-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="fed65-175">Vlastnost má atribut VectorType, který ho určí jako vektor. [](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) `VariableLengthFeatures`</span><span class="sxs-lookup"><span data-stu-id="fed65-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="fed65-176">Všechny prvky Vector musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="fed65-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="fed65-177">U datových sad s velkým počtem sloupců načítá více sloupců jako jeden vektor při použití transformace dat.</span><span class="sxs-lookup"><span data-stu-id="fed65-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="fed65-178">Tato třída se používá v `ResizeFeatures` akci.</span><span class="sxs-lookup"><span data-stu-id="fed65-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="fed65-179">Názvy vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v zobrazení DataView lze použít jako _vstup_ pro akci vlastního mapování.</span><span class="sxs-lookup"><span data-stu-id="fed65-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="fed65-180">Vytvořte třídu pro funkce s pevnou délkou za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="fed65-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="fed65-181">Tato třída se používá v `ResizeFeatures` akci.</span><span class="sxs-lookup"><span data-stu-id="fed65-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="fed65-182">Názvy vlastností (v tomto případě pouze jeden) se používají k označení toho, které sloupce v zobrazení DataView lze použít jako _výstup_ akce vlastního mapování.</span><span class="sxs-lookup"><span data-stu-id="fed65-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="fed65-183">Všimněte si, že název vlastnosti `Features` je určen modelem TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fed65-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="fed65-184">Tento název vlastnosti nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="fed65-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="fed65-185">Vytvořte třídu pro předpověď za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="fed65-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="fed65-186">`MovieReviewSentimentPrediction`je třídou předpovědi použitou po školení modelu.</span><span class="sxs-lookup"><span data-stu-id="fed65-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="fed65-187">`MovieReviewSentimentPrediction`má jedno `float` pole (`Prediction`) a `VectorType` atribut.</span><span class="sxs-lookup"><span data-stu-id="fed65-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="fed65-188">Vytvoření MLContext, vyhledávacího slovníku a akce pro změnu velikosti funkcí</span><span class="sxs-lookup"><span data-stu-id="fed65-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="fed65-189">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET.</span><span class="sxs-lookup"><span data-stu-id="fed65-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="fed65-190">Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="fed65-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fed65-191">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fed65-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="fed65-192">Nahraďte `Main` řádek v metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="fed65-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="fed65-193">Vytvořte slovník pro kódování slov jako celé číslo pomocí [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody pro načtení mapování dat ze souboru, jak je vidět v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="fed65-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="fed65-194">Word</span><span class="sxs-lookup"><span data-stu-id="fed65-194">Word</span></span>     |<span data-ttu-id="fed65-195">Index</span><span class="sxs-lookup"><span data-stu-id="fed65-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="fed65-196">dětí</span><span class="sxs-lookup"><span data-stu-id="fed65-196">kids</span></span>     |  <span data-ttu-id="fed65-197">362</span><span class="sxs-lookup"><span data-stu-id="fed65-197">362</span></span>    |
    |<span data-ttu-id="fed65-198">požadovaného</span><span class="sxs-lookup"><span data-stu-id="fed65-198">want</span></span>     |  <span data-ttu-id="fed65-199">181</span><span class="sxs-lookup"><span data-stu-id="fed65-199">181</span></span>    |
    |<span data-ttu-id="fed65-200">něco</span><span class="sxs-lookup"><span data-stu-id="fed65-200">wrong</span></span>    |  <span data-ttu-id="fed65-201">355</span><span class="sxs-lookup"><span data-stu-id="fed65-201">355</span></span>    |
    |<span data-ttu-id="fed65-202">efekty</span><span class="sxs-lookup"><span data-stu-id="fed65-202">effects</span></span>  |  <span data-ttu-id="fed65-203">302</span><span class="sxs-lookup"><span data-stu-id="fed65-203">302</span></span>    |
    |<span data-ttu-id="fed65-204">úplně</span><span class="sxs-lookup"><span data-stu-id="fed65-204">feeling</span></span>  |  <span data-ttu-id="fed65-205">547</span><span class="sxs-lookup"><span data-stu-id="fed65-205">547</span></span>    |

    <span data-ttu-id="fed65-206">Přidejte následující kód pro vytvoření mapy vyhledávání:</span><span class="sxs-lookup"><span data-stu-id="fed65-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="fed65-207">Přidejte, `Action` Chcete-li změnit velikost pole celé číslo proměnné na celé číslo s pevnou velikostí s dalšími řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="fed65-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="fed65-208">Načtení předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="fed65-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="fed65-209">Přidejte kód pro načtení modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="fed65-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="fed65-210">Po načtení modelu můžete extrahovat jeho vstupní a výstupní schéma.</span><span class="sxs-lookup"><span data-stu-id="fed65-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="fed65-211">Schémata se zobrazují jenom pro vás a jenom učení.</span><span class="sxs-lookup"><span data-stu-id="fed65-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="fed65-212">Tento kód nepotřebujete, aby konečná aplikace fungovala:</span><span class="sxs-lookup"><span data-stu-id="fed65-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="fed65-213">Vstupní schéma je pole s pevnou délkou kódovaných slov typu Integer.</span><span class="sxs-lookup"><span data-stu-id="fed65-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="fed65-214">Výstupní schéma je plovoucí pole pravděpodobnosti, které označuje, zda je mínění revize záporná nebo kladná.</span><span class="sxs-lookup"><span data-stu-id="fed65-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="fed65-215">Tyto hodnoty se sčítají na 1, protože pravděpodobnost, že je kladné, je doplňkem pravděpodobnosti mínění negativní.</span><span class="sxs-lookup"><span data-stu-id="fed65-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="fed65-216">Vytvoření kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="fed65-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="fed65-217">Vytvořte kanál a rozdělte vstupní text na slova pomocí transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) pro rozdělení textu na slova jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="fed65-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="fed65-218">Transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) používá mezery k analýze textu nebo řetězce na slova.</span><span class="sxs-lookup"><span data-stu-id="fed65-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="fed65-219">Vytvoří nový sloupec a rozdělí jednotlivé vstupní řetězce na vektor podřetězců na základě oddělovače definovaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="fed65-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="fed65-220">Namapujte slova na celočíselné kódování pomocí vyhledávací tabulky, kterou jste deklarovali výše:</span><span class="sxs-lookup"><span data-stu-id="fed65-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="fed65-221">Změňte velikost celočíselných kódování proměnné na pevnou délku, kterou vyžaduje model:</span><span class="sxs-lookup"><span data-stu-id="fed65-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="fed65-222">Klasifikace vstupu pomocí načteného modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="fed65-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="fed65-223">Výstup modelu TensorFlow se zavolá `Prediction/Softmax`.</span><span class="sxs-lookup"><span data-stu-id="fed65-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="fed65-224">Všimněte si, že `Prediction/Softmax` název je určený podle modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fed65-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="fed65-225">Tento název nemůžete změnit.</span><span class="sxs-lookup"><span data-stu-id="fed65-225">You cannot change this name.</span></span>

1. <span data-ttu-id="fed65-226">Vytvoří nový sloupec pro předpověď výstupu:</span><span class="sxs-lookup"><span data-stu-id="fed65-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="fed65-227">Je nutné zkopírovat `Prediction/Softmax` sloupec do jednoho s názvem, který lze použít jako vlastnost ve C# třídě: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="fed65-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="fed65-228">Znak není povolen v názvu C# vlastnosti. `/`</span><span class="sxs-lookup"><span data-stu-id="fed65-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="fed65-229">Vytvoření modelu ML.NET z kanálu</span><span class="sxs-lookup"><span data-stu-id="fed65-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="fed65-230">Přidejte kód pro vytvoření modelu z kanálu:</span><span class="sxs-lookup"><span data-stu-id="fed65-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="fed65-231">Model ml.NET se vytvoří z řetězce odhady v kanálu voláním `Fit` metody.</span><span class="sxs-lookup"><span data-stu-id="fed65-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="fed65-232">V takovém případě nebudeme pro vytvoření modelu vytvářet žádná data, protože model TensorFlow již byl dříve vyškolen.</span><span class="sxs-lookup"><span data-stu-id="fed65-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="fed65-233">Dodáváme prázdný objekt zobrazení dat, který splňuje požadavky `Fit` metody.</span><span class="sxs-lookup"><span data-stu-id="fed65-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="fed65-234">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="fed65-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="fed65-235">`PredictSentiment` Přidejte metodu`Main` pod metodu:</span><span class="sxs-lookup"><span data-stu-id="fed65-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="fed65-236">Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek `PredictSentiment()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="fed65-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="fed65-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje vytvořit předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="fed65-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to make a prediction on a single instance of data.</span></span>

1. <span data-ttu-id="fed65-238">Přidejte komentář k otestování předpovědi vyškolených modelů v `Predict()` metodě vytvořením `MovieReview`instance:</span><span class="sxs-lookup"><span data-stu-id="fed65-238">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="fed65-239">Předání dat testovacích komentářů do do `Prediction Engine` přidejte další řádky kódu `PredictSentiment()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="fed65-239">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="fed65-240">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:</span><span class="sxs-lookup"><span data-stu-id="fed65-240">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="fed65-241">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fed65-241">Property</span></span>| <span data-ttu-id="fed65-242">Value</span><span class="sxs-lookup"><span data-stu-id="fed65-242">Value</span></span>|<span data-ttu-id="fed65-243">Typ</span><span class="sxs-lookup"><span data-stu-id="fed65-243">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="fed65-244">Předpověď</span><span class="sxs-lookup"><span data-stu-id="fed65-244">Prediction</span></span>|<span data-ttu-id="fed65-245">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="fed65-245">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="fed65-246">float []</span><span class="sxs-lookup"><span data-stu-id="fed65-246">float[]</span></span>|

1. <span data-ttu-id="fed65-247">Zobrazit předpovědi mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fed65-247">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="fed65-248">Na konec `PredictSentiment` `Main` metody přidejte volání:</span><span class="sxs-lookup"><span data-stu-id="fed65-248">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="fed65-249">Výsledky</span><span class="sxs-lookup"><span data-stu-id="fed65-249">Results</span></span>

<span data-ttu-id="fed65-250">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fed65-250">Build and run your application.</span></span>

<span data-ttu-id="fed65-251">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="fed65-251">Your results should be similar to the following.</span></span> <span data-ttu-id="fed65-252">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="fed65-252">During processing, messages are displayed.</span></span> <span data-ttu-id="fed65-253">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="fed65-253">You may see warnings, or processing messages.</span></span> <span data-ttu-id="fed65-254">Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="fed65-254">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="fed65-255">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="fed65-255">Congratulations!</span></span> <span data-ttu-id="fed65-256">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění opětovným použitím předem připraveného `TensorFlow` modelu v ml.NET.</span><span class="sxs-lookup"><span data-stu-id="fed65-256">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="fed65-257">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="fed65-257">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="fed65-258">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="fed65-258">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fed65-259">Načtení předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="fed65-259">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="fed65-260">Transformovat text komentáře webu k funkcím vhodným pro model</span><span class="sxs-lookup"><span data-stu-id="fed65-260">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="fed65-261">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="fed65-261">Use the model to make a prediction</span></span>
