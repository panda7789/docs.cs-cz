---
title: 'Kurz: Analýza mínění recenze pomocí modelu TensorFlow'
description: Tento kurz ukazuje, jak používat předem vyškolený model TensorFlow ke klasifikaci mínění v komentářích k webu. Binární třídění mínění je konzolová aplikace jazyka C# vyvinutá pomocí sady Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241114"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="90ec9-104">Kurz: Analyzujte mínění filmových recenzí pomocí předem trénovaného modelu TensorFlow v ML.NET</span><span class="sxs-lookup"><span data-stu-id="90ec9-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="90ec9-105">Tento kurz ukazuje, jak používat předem vyškolený model TensorFlow ke klasifikaci mínění v komentářích k webu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="90ec9-106">Binární třídění mínění je konzolová aplikace jazyka C# vyvinutá pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90ec9-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="90ec9-107">Model TensorFlow použitý v tomto kurzu byl trénován pomocí filmových recenzí z databáze IMDB.</span><span class="sxs-lookup"><span data-stu-id="90ec9-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="90ec9-108">Jakmile dokončíte vývoj aplikace, budete moci zadat text pro kontrolu filmu a aplikace vám řekne, zda má recenze pozitivní nebo negativní sentiment.</span><span class="sxs-lookup"><span data-stu-id="90ec9-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="90ec9-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="90ec9-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="90ec9-110">Načtení předem vyškoleného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="90ec9-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="90ec9-111">Transformace textu komentáře na webových stránkách na funkce vhodné pro model</span><span class="sxs-lookup"><span data-stu-id="90ec9-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="90ec9-112">Pomocí modelu proveďte předpověď</span><span class="sxs-lookup"><span data-stu-id="90ec9-112">Use the model to make a prediction</span></span>

<span data-ttu-id="90ec9-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)</span><span class="sxs-lookup"><span data-stu-id="90ec9-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90ec9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90ec9-114">Prerequisites</span></span>

* <span data-ttu-id="90ec9-115">[Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".</span><span class="sxs-lookup"><span data-stu-id="90ec9-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="90ec9-116">Nastavení</span><span class="sxs-lookup"><span data-stu-id="90ec9-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="90ec9-117">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="90ec9-117">Create the application</span></span>

1. <span data-ttu-id="90ec9-118">Vytvořte **aplikaci .NET Core Console** s názvem "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="90ec9-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="90ec9-119">Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.</span><span class="sxs-lookup"><span data-stu-id="90ec9-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="90ec9-120">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="90ec9-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="90ec9-121">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="90ec9-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="90ec9-122">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet.** **Vyhledejte Microsoft.ML**, vyberte požadovaný balíček a pak vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="90ec9-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="90ec9-123">Pokračujte v instalaci souhlasem s licenčními podmínkami pro vámi zvolené balíček.</span><span class="sxs-lookup"><span data-stu-id="90ec9-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="90ec9-124">Opakujte tyto kroky pro **Microsoft.ML.TensorFlow** a **SciSharp.TensorFlow.Redist**.</span><span class="sxs-lookup"><span data-stu-id="90ec9-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="90ec9-125">Přidání modelu TensorFlow do projektu</span><span class="sxs-lookup"><span data-stu-id="90ec9-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="90ec9-126">Model pro tento kurz je z [úložiště Dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub.</span><span class="sxs-lookup"><span data-stu-id="90ec9-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="90ec9-127">Model je ve formátu TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="90ec9-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="90ec9-128">Stáhněte si [soubor sentiment_model zip](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)a rozbalte.</span><span class="sxs-lookup"><span data-stu-id="90ec9-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="90ec9-129">Soubor zip obsahuje:</span><span class="sxs-lookup"><span data-stu-id="90ec9-129">The zip file contains:</span></span>

    * <span data-ttu-id="90ec9-130">`saved_model.pb`: samotný model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="90ec9-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="90ec9-131">Model má pevnou délku (velikost 600) celé pole funkcí představujících text v řetězci revize IMDB a vynaloží dvě pravděpodobnosti, které součet 1: pravděpodobnost, že vstupní revize má kladný sentiment a pravděpodobnost, že vstupní revize má negativní sentiment.</span><span class="sxs-lookup"><span data-stu-id="90ec9-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="90ec9-132">`imdb_word_index.csv`: mapování z jednotlivých slov na celá hodnota.</span><span class="sxs-lookup"><span data-stu-id="90ec9-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="90ec9-133">Mapování se používá ke generování vstupních funkcí pro model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="90ec9-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="90ec9-134">Zkopírujte obsah nejvnitřnějšího `sentiment_model` adresáře do adresáře projektu `sentiment_model` *TextClassificationTF.*</span><span class="sxs-lookup"><span data-stu-id="90ec9-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="90ec9-135">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="90ec9-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model obsah adresáře](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="90ec9-137">V Průzkumníku řešení klepněte pravým tlačítkem myši na jednotlivé soubory v `sentiment_model` adresáři a podadresáři a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="90ec9-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="90ec9-138">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="90ec9-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="90ec9-139">Přidání pomocí příkazů a globálních proměnných</span><span class="sxs-lookup"><span data-stu-id="90ec9-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="90ec9-140">Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:</span><span class="sxs-lookup"><span data-stu-id="90ec9-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="90ec9-141">Vytvořte dvě globální proměnné `Main` přímo nad metodou, která pojme uloženou cestu k souboru modelu a délku vektoru prvku.</span><span class="sxs-lookup"><span data-stu-id="90ec9-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="90ec9-142">`_modelPath`je cesta k souboru trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="90ec9-143">`FeatureLength`je délka pole celého prvku, které model očekává.</span><span class="sxs-lookup"><span data-stu-id="90ec9-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="90ec9-144">Modelování dat</span><span class="sxs-lookup"><span data-stu-id="90ec9-144">Model the data</span></span>

<span data-ttu-id="90ec9-145">Filmové recenze jsou textz volné formy.</span><span class="sxs-lookup"><span data-stu-id="90ec9-145">Movie reviews are free form text.</span></span> <span data-ttu-id="90ec9-146">Aplikace převede text do vstupního formátu očekávaného modelem v několika samostatných fázích.</span><span class="sxs-lookup"><span data-stu-id="90ec9-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="90ec9-147">Prvním z nich je rozdělit text na samostatná slova a použít poskytnutý soubor mapování mapovat každé slovo na kódování celé číslo.</span><span class="sxs-lookup"><span data-stu-id="90ec9-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="90ec9-148">Výsledkem této transformace je pole s proměnnou délkou celéčíslo s délkou odpovídající počtu slov ve větě.</span><span class="sxs-lookup"><span data-stu-id="90ec9-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="90ec9-149">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90ec9-149">Property</span></span>| <span data-ttu-id="90ec9-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="90ec9-150">Value</span></span>|<span data-ttu-id="90ec9-151">Typ</span><span class="sxs-lookup"><span data-stu-id="90ec9-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="90ec9-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="90ec9-152">ReviewText</span></span>|<span data-ttu-id="90ec9-153">tento film je opravdu dobrý</span><span class="sxs-lookup"><span data-stu-id="90ec9-153">this film is really good</span></span>|<span data-ttu-id="90ec9-154">řetězec</span><span class="sxs-lookup"><span data-stu-id="90ec9-154">string</span></span>|
|<span data-ttu-id="90ec9-155">Proměnné Funkce délky</span><span class="sxs-lookup"><span data-stu-id="90ec9-155">VariableLengthFeatures</span></span>|<span data-ttu-id="90ec9-156">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="90ec9-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="90ec9-157">int[]</span><span class="sxs-lookup"><span data-stu-id="90ec9-157">int[]</span></span>|

<span data-ttu-id="90ec9-158">Pole prvku proměnné délky se pak mění na pevnou délku 600.</span><span class="sxs-lookup"><span data-stu-id="90ec9-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="90ec9-159">Toto je délka, kterou model TensorFlow očekává.</span><span class="sxs-lookup"><span data-stu-id="90ec9-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="90ec9-160">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90ec9-160">Property</span></span>| <span data-ttu-id="90ec9-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="90ec9-161">Value</span></span>|<span data-ttu-id="90ec9-162">Typ</span><span class="sxs-lookup"><span data-stu-id="90ec9-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="90ec9-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="90ec9-163">ReviewText</span></span>|<span data-ttu-id="90ec9-164">tento film je opravdu dobrý</span><span class="sxs-lookup"><span data-stu-id="90ec9-164">this film is really good</span></span>|<span data-ttu-id="90ec9-165">řetězec</span><span class="sxs-lookup"><span data-stu-id="90ec9-165">string</span></span>|
|<span data-ttu-id="90ec9-166">Proměnné Funkce délky</span><span class="sxs-lookup"><span data-stu-id="90ec9-166">VariableLengthFeatures</span></span>|<span data-ttu-id="90ec9-167">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="90ec9-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="90ec9-168">int[]</span><span class="sxs-lookup"><span data-stu-id="90ec9-168">int[]</span></span>|
|<span data-ttu-id="90ec9-169">Funkce</span><span class="sxs-lookup"><span data-stu-id="90ec9-169">Features</span></span>|<span data-ttu-id="90ec9-170">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="90ec9-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="90ec9-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="90ec9-171">int[600]</span></span>|

1. <span data-ttu-id="90ec9-172">Vytvořte třídu pro vstupní `Main` data po metodě:</span><span class="sxs-lookup"><span data-stu-id="90ec9-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="90ec9-173">Třída vstupních `MovieReview`dat , `string` má pro`ReviewText`komentáře uživatele ( ).</span><span class="sxs-lookup"><span data-stu-id="90ec9-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="90ec9-174">Vytvořte třídu pro prvky `Main` proměnné délky po metodě:</span><span class="sxs-lookup"><span data-stu-id="90ec9-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="90ec9-175">Vlastnost `VariableLengthFeatures` má atribut [VectorType,](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) který ji označuje jako vektor.</span><span class="sxs-lookup"><span data-stu-id="90ec9-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="90ec9-176">Všechny vektorové prvky musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="90ec9-177">V datových sadách s velkým počtem sloupců se načtení více sloupců jako jednoho vektoru sníží počet dat, když aplikujete transformace dat.</span><span class="sxs-lookup"><span data-stu-id="90ec9-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="90ec9-178">Tato třída se `ResizeFeatures` používá v akci.</span><span class="sxs-lookup"><span data-stu-id="90ec9-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="90ec9-179">Názvy jeho vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v DataView lze použít jako _vstup_ do akce vlastní mapování.</span><span class="sxs-lookup"><span data-stu-id="90ec9-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="90ec9-180">Vytvořte třídu pro prvky `Main` pevné délky po metodě:</span><span class="sxs-lookup"><span data-stu-id="90ec9-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="90ec9-181">Tato třída se `ResizeFeatures` používá v akci.</span><span class="sxs-lookup"><span data-stu-id="90ec9-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="90ec9-182">Názvy jeho vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v DataView lze použít jako _výstup_ vlastní akce mapování.</span><span class="sxs-lookup"><span data-stu-id="90ec9-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="90ec9-183">Všimněte si, že `Features` název vlastnosti je určen modelem TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="90ec9-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="90ec9-184">Tento název vlastnosti nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="90ec9-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="90ec9-185">Vytvořte třídu pro `Main` předpověď po metodě:</span><span class="sxs-lookup"><span data-stu-id="90ec9-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="90ec9-186">`MovieReviewSentimentPrediction`je třída předpověď použitá po trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="90ec9-187">`MovieReviewSentimentPrediction`má jedno `float` pole`Prediction`( `VectorType` ) a atribut.</span><span class="sxs-lookup"><span data-stu-id="90ec9-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="90ec9-188">Vytvoření funkce MLContext, vyhledávacího slovníku a akce pro změna velikosti funkcí</span><span class="sxs-lookup"><span data-stu-id="90ec9-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="90ec9-189">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET.</span><span class="sxs-lookup"><span data-stu-id="90ec9-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="90ec9-190">Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="90ec9-191">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="90ec9-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="90ec9-192">Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro deklarování a inicializaci proměnné mlContext:</span><span class="sxs-lookup"><span data-stu-id="90ec9-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="90ec9-193">Vytvořte slovník pro kódování slov jako celá čísla [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) pomocí metody pro načtení mapových dat ze souboru, jak je vidět v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="90ec9-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="90ec9-194">Word</span><span class="sxs-lookup"><span data-stu-id="90ec9-194">Word</span></span>     |<span data-ttu-id="90ec9-195">Index</span><span class="sxs-lookup"><span data-stu-id="90ec9-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="90ec9-196">Děti</span><span class="sxs-lookup"><span data-stu-id="90ec9-196">kids</span></span>     |  <span data-ttu-id="90ec9-197">362</span><span class="sxs-lookup"><span data-stu-id="90ec9-197">362</span></span>    |
    |<span data-ttu-id="90ec9-198">chcete</span><span class="sxs-lookup"><span data-stu-id="90ec9-198">want</span></span>     |  <span data-ttu-id="90ec9-199">181</span><span class="sxs-lookup"><span data-stu-id="90ec9-199">181</span></span>    |
    |<span data-ttu-id="90ec9-200">Špatně</span><span class="sxs-lookup"><span data-stu-id="90ec9-200">wrong</span></span>    |  <span data-ttu-id="90ec9-201">355</span><span class="sxs-lookup"><span data-stu-id="90ec9-201">355</span></span>    |
    |<span data-ttu-id="90ec9-202">effects</span><span class="sxs-lookup"><span data-stu-id="90ec9-202">effects</span></span>  |  <span data-ttu-id="90ec9-203">302</span><span class="sxs-lookup"><span data-stu-id="90ec9-203">302</span></span>    |
    |<span data-ttu-id="90ec9-204">Pocit</span><span class="sxs-lookup"><span data-stu-id="90ec9-204">feeling</span></span>  |  <span data-ttu-id="90ec9-205">547</span><span class="sxs-lookup"><span data-stu-id="90ec9-205">547</span></span>    |

    <span data-ttu-id="90ec9-206">Chcete-li vytvořit vyhledávací mapu, přidejte níže uvedený kód:</span><span class="sxs-lookup"><span data-stu-id="90ec9-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="90ec9-207">Přidáním `Action` a změňte velikost celého pole slova s proměnnou délkou do celého pole s pevnou velikostí s dalšími řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="90ec9-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="90ec9-208">Načtěte předem vyškolený model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="90ec9-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="90ec9-209">Přidání kódu pro načtení modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="90ec9-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="90ec9-210">Po načtení modelu můžete extrahovat jeho vstupní a výstupní schéma.</span><span class="sxs-lookup"><span data-stu-id="90ec9-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="90ec9-211">Schémata jsou zobrazeny pouze pro zájem a učení.</span><span class="sxs-lookup"><span data-stu-id="90ec9-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="90ec9-212">Tento kód nepotřebujete, aby konečná aplikace fungovala:</span><span class="sxs-lookup"><span data-stu-id="90ec9-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    <span data-ttu-id="90ec9-213">Vstupní schéma je pole s pevnou délkou celočíselných kódovaných slov.</span><span class="sxs-lookup"><span data-stu-id="90ec9-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="90ec9-214">Schéma výstupu je plovoucí pole pravděpodobností označující, zda mínění recenze je negativní nebo pozitivní .</span><span class="sxs-lookup"><span data-stu-id="90ec9-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="90ec9-215">Tyto hodnoty se součet 1, jako pravděpodobnost, že je pozitivní je doplněk pravděpodobnosti sentimentu je záporná.</span><span class="sxs-lookup"><span data-stu-id="90ec9-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="90ec9-216">Vytvoření kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="90ec9-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="90ec9-217">Vytvořte kanál a rozdělte vstupní text na slova pomocí [tokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformace rozdělit text na slova jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="90ec9-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="90ec9-218">[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformace používá mezery analyzovat text/řetězec do slov.</span><span class="sxs-lookup"><span data-stu-id="90ec9-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="90ec9-219">Vytvoří nový sloupec a rozdělí každý vstupní řetězec na vektor podřetězců na základě uživatelem definovaného oddělovače.</span><span class="sxs-lookup"><span data-stu-id="90ec9-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="90ec9-220">Namapujte slova na jejich celé kódování pomocí vyhledávací tabulky, kterou jste deklarovali výše:</span><span class="sxs-lookup"><span data-stu-id="90ec9-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. <span data-ttu-id="90ec9-221">Změňte velikost celočíselné kódování proměnné délky na kódování s pevnou délkou, kterou model požaduje:</span><span class="sxs-lookup"><span data-stu-id="90ec9-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. <span data-ttu-id="90ec9-222">Klasifikujte vstup s načteným modelem TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="90ec9-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="90ec9-223">Výstup modelu TensorFlow `Prediction/Softmax`se nazývá .</span><span class="sxs-lookup"><span data-stu-id="90ec9-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="90ec9-224">Všimněte si, že název `Prediction/Softmax` je určen modelem TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="90ec9-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="90ec9-225">Tento název nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="90ec9-225">You cannot change this name.</span></span>

1. <span data-ttu-id="90ec9-226">Vytvořte nový sloupec pro předpověď výstupu:</span><span class="sxs-lookup"><span data-stu-id="90ec9-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="90ec9-227">Je třeba zkopírovat `Prediction/Softmax` sloupec do jednoho s názvem, který lze použít `Prediction`jako vlastnost ve třídě C#: .</span><span class="sxs-lookup"><span data-stu-id="90ec9-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="90ec9-228">Znak `/` není povolen v názvu vlastnosti Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="90ec9-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="90ec9-229">Vytvoření modelu ML.NET z kanálu</span><span class="sxs-lookup"><span data-stu-id="90ec9-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="90ec9-230">Přidejte kód pro vytvoření modelu z kanálu:</span><span class="sxs-lookup"><span data-stu-id="90ec9-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="90ec9-231">Model ML.NET je vytvořen z řetězce odhadců v kanálu `Fit` voláním metody.</span><span class="sxs-lookup"><span data-stu-id="90ec9-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="90ec9-232">V tomto případě nejsme montáž žádná data k vytvoření modelu, jako tensorflow model již byl dříve trénovaný.</span><span class="sxs-lookup"><span data-stu-id="90ec9-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="90ec9-233">Dodáváme prázdný objekt zobrazení dat, aby `Fit` splňoval požadavky metody.</span><span class="sxs-lookup"><span data-stu-id="90ec9-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="90ec9-234">Pomocí modelu proveďte předpověď</span><span class="sxs-lookup"><span data-stu-id="90ec9-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="90ec9-235">Přidejte `PredictSentiment` metodu `Main` pod metodu:</span><span class="sxs-lookup"><span data-stu-id="90ec9-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="90ec9-236">Přidejte následující kód `PredictionEngine` k vytvoření jako `PredictSentiment()` první řádek v metodě:</span><span class="sxs-lookup"><span data-stu-id="90ec9-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="90ec9-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="90ec9-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="90ec9-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="90ec9-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="90ec9-239">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="90ec9-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="90ec9-240">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="90ec9-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="90ec9-241">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="90ec9-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="90ec9-242">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="90ec9-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="90ec9-243">Přidejte komentář k testování predikce `Predict()` trénovaného modelu `MovieReview`v metodě vytvořením instance :</span><span class="sxs-lookup"><span data-stu-id="90ec9-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. <span data-ttu-id="90ec9-244">Předejte data testovacích `Prediction Engine` komentářů přidáním dalších `PredictSentiment()` řádků kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="90ec9-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. <span data-ttu-id="90ec9-245">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jeden řádek dat:</span><span class="sxs-lookup"><span data-stu-id="90ec9-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="90ec9-246">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90ec9-246">Property</span></span>| <span data-ttu-id="90ec9-247">Hodnota</span><span class="sxs-lookup"><span data-stu-id="90ec9-247">Value</span></span>|<span data-ttu-id="90ec9-248">Typ</span><span class="sxs-lookup"><span data-stu-id="90ec9-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="90ec9-249">Prediction (Předpověď)</span><span class="sxs-lookup"><span data-stu-id="90ec9-249">Prediction</span></span>|<span data-ttu-id="90ec9-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="90ec9-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="90ec9-251">plovák[]</span><span class="sxs-lookup"><span data-stu-id="90ec9-251">float[]</span></span>|

1. <span data-ttu-id="90ec9-252">Zobrazení předpovědi mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="90ec9-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="90ec9-253">Přidejte volání `PredictSentiment` na konci `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="90ec9-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="90ec9-254">Výsledky</span><span class="sxs-lookup"><span data-stu-id="90ec9-254">Results</span></span>

<span data-ttu-id="90ec9-255">Sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="90ec9-255">Build and run your application.</span></span>

<span data-ttu-id="90ec9-256">Vaše výsledky by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-256">Your results should be similar to the following.</span></span> <span data-ttu-id="90ec9-257">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="90ec9-257">During processing, messages are displayed.</span></span> <span data-ttu-id="90ec9-258">Může se zobrazit upozornění nebo zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="90ec9-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="90ec9-259">Tyto zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="90ec9-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="90ec9-260">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="90ec9-260">Congratulations!</span></span> <span data-ttu-id="90ec9-261">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předvídání mínění zpráv opětovným použitím předem trénovaného `TensorFlow` modelu v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="90ec9-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="90ec9-262">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)</span><span class="sxs-lookup"><span data-stu-id="90ec9-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="90ec9-263">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="90ec9-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="90ec9-264">Načtení předem vyškoleného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="90ec9-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="90ec9-265">Transformace textu komentáře na webových stránkách na funkce vhodné pro model</span><span class="sxs-lookup"><span data-stu-id="90ec9-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="90ec9-266">Pomocí modelu proveďte předpověď</span><span class="sxs-lookup"><span data-stu-id="90ec9-266">Use the model to make a prediction</span></span>
