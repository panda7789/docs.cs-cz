---
title: 'Kurz: analýza míněních kontrol pomocí modelu TensorFlow'
description: V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu. Binární klasifikátor mínění je Konzolová aplikace v jazyce C# vyvinutá pomocí sady Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9a2e7f72d59e31cfd7db5b89bfad55bccb063cea
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281404"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="4b3f7-104">Kurz: analýza míněních recenzí filmů pomocí předem připraveného modelu TensorFlow v ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b3f7-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="4b3f7-105">V tomto kurzu se dozvíte, jak používat předem vyškolený model TensorFlow k klasifikaci mínění v komentářích k webu.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="4b3f7-106">Binární klasifikátor mínění je Konzolová aplikace v jazyce C# vyvinutá pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="4b3f7-107">Model TensorFlow použitý v tomto kurzu byl vyškolen pomocí recenzí filmů z databáze IMDB.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="4b3f7-108">Jakmile dokončíte vývoj aplikace, budete moci zadat text recenze filmu a aplikace vám oznámí, zda má recenze pozitivní nebo negativní mínění.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="4b3f7-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4b3f7-110">Načtení předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="4b3f7-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="4b3f7-111">Transformovat text komentáře webu k funkcím vhodným pro model</span><span class="sxs-lookup"><span data-stu-id="4b3f7-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="4b3f7-112">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="4b3f7-112">Use the model to make a prediction</span></span>

<span data-ttu-id="4b3f7-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b3f7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b3f7-114">Prerequisites</span></span>

* <span data-ttu-id="4b3f7-115">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="4b3f7-116">Nastavení</span><span class="sxs-lookup"><span data-stu-id="4b3f7-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="4b3f7-117">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="4b3f7-117">Create the application</span></span>

1. <span data-ttu-id="4b3f7-118">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="4b3f7-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="4b3f7-119">Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="4b3f7-120">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="4b3f7-121">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4b3f7-122">Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="4b3f7-123">Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="4b3f7-124">Opakujte tyto kroky pro **Microsoft. ml. TensorFlow**, **Microsoft. ml. SampleUtils** a **SciSharp. TensorFlow. Redist**.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-124">Repeat these steps for **Microsoft.ML.TensorFlow**, **Microsoft.ML.SampleUtils** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="4b3f7-125">Přidání modelu TensorFlow do projektu</span><span class="sxs-lookup"><span data-stu-id="4b3f7-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="4b3f7-126">Model pro tento kurz je z úložiště GitHub [/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="4b3f7-127">Model je ve formátu TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="4b3f7-128">Stáhněte [soubor zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="4b3f7-129">Soubor zip obsahuje:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-129">The zip file contains:</span></span>

    * <span data-ttu-id="4b3f7-130">`saved_model.pb`: TensorFlow samotný model.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="4b3f7-131">Model přebírá pevnou délku (Size 600) celočíselné pole funkcí reprezentující text v řetězci IMDB revize a má dvě pravděpodobnosti, které se sčítají 1: pravděpodobnost, že vstupní revize má pozitivní mínění, a pravděpodobnost, že vstupní revize má negativní mínění.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="4b3f7-132">`imdb_word_index.csv`: mapování jednotlivých slov na celočíselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="4b3f7-133">Mapování slouží k vygenerování vstupních funkcí modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="4b3f7-134">Zkopírujte obsah nejvnitřnějšího `sentiment_model` adresáře do adresáře projektu *TextClassificationTF* `sentiment_model` .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="4b3f7-135">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![obsah sentiment_model adresáře](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="4b3f7-137">V Průzkumník řešení klikněte pravým tlačítkem myši na každý ze souborů v `sentiment_model` adresáři a v podadresáři a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="4b3f7-138">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="4b3f7-139">Přidat příkazy using a globální proměnné</span><span class="sxs-lookup"><span data-stu-id="4b3f7-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="4b3f7-140">`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](./snippets/text-classification-tf/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="4b3f7-141">Vytvořte dvě globální proměnné přímo nad `Main` metodu pro uchování cesty k souboru uloženého modelu a délku vektoru funkce.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](./snippets/text-classification-tf/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="4b3f7-142">`_modelPath`je cesta k souboru trained modelu.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="4b3f7-143">`FeatureLength`je délka pole funkce celého čísla, které model očekává.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="4b3f7-144">Modelování dat</span><span class="sxs-lookup"><span data-stu-id="4b3f7-144">Model the data</span></span>

<span data-ttu-id="4b3f7-145">Recenze filmů je text bezplatné Form.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-145">Movie reviews are free form text.</span></span> <span data-ttu-id="4b3f7-146">Vaše aplikace převede text na vstupní formát očekávaný modelem v řadě diskrétních fází.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="4b3f7-147">První je rozdělit text na samostatná slova a použít poskytnutý soubor mapování pro mapování jednotlivých slov na celočíselné kódování.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="4b3f7-148">Výsledkem této transformace je pole celé číslo proměnné s délkou odpovídající počtu slov ve větě.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="4b3f7-149">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4b3f7-149">Property</span></span>| <span data-ttu-id="4b3f7-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4b3f7-150">Value</span></span>|<span data-ttu-id="4b3f7-151">Typ</span><span class="sxs-lookup"><span data-stu-id="4b3f7-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="4b3f7-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="4b3f7-152">ReviewText</span></span>|<span data-ttu-id="4b3f7-153">Tato film je skutečně dobrá</span><span class="sxs-lookup"><span data-stu-id="4b3f7-153">this film is really good</span></span>|<span data-ttu-id="4b3f7-154">řetězec</span><span class="sxs-lookup"><span data-stu-id="4b3f7-154">string</span></span>|
|<span data-ttu-id="4b3f7-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="4b3f7-155">VariableLengthFeatures</span></span>|<span data-ttu-id="4b3f7-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="4b3f7-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="4b3f7-157">int []</span><span class="sxs-lookup"><span data-stu-id="4b3f7-157">int[]</span></span>|

<span data-ttu-id="4b3f7-158">Velikost pole s proměnnou délkou se pak změní na pevně stanovenou délku 600.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="4b3f7-159">Jedná se o délku, kterou model TensorFlow očekává.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="4b3f7-160">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4b3f7-160">Property</span></span>| <span data-ttu-id="4b3f7-161">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4b3f7-161">Value</span></span>|<span data-ttu-id="4b3f7-162">Typ</span><span class="sxs-lookup"><span data-stu-id="4b3f7-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="4b3f7-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="4b3f7-163">ReviewText</span></span>|<span data-ttu-id="4b3f7-164">Tato film je skutečně dobrá</span><span class="sxs-lookup"><span data-stu-id="4b3f7-164">this film is really good</span></span>|<span data-ttu-id="4b3f7-165">řetězec</span><span class="sxs-lookup"><span data-stu-id="4b3f7-165">string</span></span>|
|<span data-ttu-id="4b3f7-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="4b3f7-166">VariableLengthFeatures</span></span>|<span data-ttu-id="4b3f7-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="4b3f7-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="4b3f7-168">int []</span><span class="sxs-lookup"><span data-stu-id="4b3f7-168">int[]</span></span>|
|<span data-ttu-id="4b3f7-169">Funkce</span><span class="sxs-lookup"><span data-stu-id="4b3f7-169">Features</span></span>|<span data-ttu-id="4b3f7-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="4b3f7-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="4b3f7-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="4b3f7-171">int[600]</span></span>|

1. <span data-ttu-id="4b3f7-172">Vytvořte třídu pro vstupní data za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](./snippets/text-classification-tf/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="4b3f7-173">Vstupní datová třída `MovieReview` obsahuje `string` komentář pro uživatele ( `ReviewText` ).</span><span class="sxs-lookup"><span data-stu-id="4b3f7-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="4b3f7-174">Vytvořte třídu pro funkce s proměnlivou délkou za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="4b3f7-175">`VariableLengthFeatures`Vlastnost má atribut [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) , který ho určí jako vektor.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="4b3f7-176">Všechny prvky Vector musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="4b3f7-177">U datových sad s velkým počtem sloupců načítá více sloupců jako jeden vektor při použití transformace dat.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="4b3f7-178">Tato třída se používá v `ResizeFeatures` akci.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="4b3f7-179">Názvy vlastností (v tomto případě pouze jeden) se používají k označení, které sloupce v zobrazení DataView lze použít jako _vstup_ pro akci vlastního mapování.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="4b3f7-180">Vytvořte třídu pro funkce s pevnou délkou za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="4b3f7-181">Tato třída se používá v `ResizeFeatures` akci.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="4b3f7-182">Názvy vlastností (v tomto případě pouze jeden) se používají k označení toho, které sloupce v zobrazení DataView lze použít jako _výstup_ akce vlastního mapování.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="4b3f7-183">Všimněte si, že název vlastnosti `Features` je určen modelem TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="4b3f7-184">Tento název vlastnosti nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="4b3f7-185">Vytvořte třídu pro předpověď za `Main` metodou:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](./snippets/text-classification-tf/csharp/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="4b3f7-186">`MovieReviewSentimentPrediction`je třídou předpovědi použitou po školení modelu.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="4b3f7-187">`MovieReviewSentimentPrediction`má jedno `float` pole ( `Prediction` ) a `VectorType` atribut.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="4b3f7-188">Vytvoření MLContext, vyhledávacího slovníku a akce pro změnu velikosti funkcí</span><span class="sxs-lookup"><span data-stu-id="4b3f7-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="4b3f7-189">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="4b3f7-190">Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4b3f7-191">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="4b3f7-192">Nahraďte `Console.WriteLine("Hello World!")` řádek v `Main` metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](./snippets/text-classification-tf/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="4b3f7-193">Vytvořte slovník pro kódování slov jako celé číslo pomocí [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody pro načtení mapování dat ze souboru, jak je vidět v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="4b3f7-194">Word</span><span class="sxs-lookup"><span data-stu-id="4b3f7-194">Word</span></span>     |<span data-ttu-id="4b3f7-195">Index</span><span class="sxs-lookup"><span data-stu-id="4b3f7-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="4b3f7-196">dětí</span><span class="sxs-lookup"><span data-stu-id="4b3f7-196">kids</span></span>     |  <span data-ttu-id="4b3f7-197">362</span><span class="sxs-lookup"><span data-stu-id="4b3f7-197">362</span></span>    |
    |<span data-ttu-id="4b3f7-198">požadovaného</span><span class="sxs-lookup"><span data-stu-id="4b3f7-198">want</span></span>     |  <span data-ttu-id="4b3f7-199">181</span><span class="sxs-lookup"><span data-stu-id="4b3f7-199">181</span></span>    |
    |<span data-ttu-id="4b3f7-200">něco</span><span class="sxs-lookup"><span data-stu-id="4b3f7-200">wrong</span></span>    |  <span data-ttu-id="4b3f7-201">355</span><span class="sxs-lookup"><span data-stu-id="4b3f7-201">355</span></span>    |
    |<span data-ttu-id="4b3f7-202">effects</span><span class="sxs-lookup"><span data-stu-id="4b3f7-202">effects</span></span>  |  <span data-ttu-id="4b3f7-203">302</span><span class="sxs-lookup"><span data-stu-id="4b3f7-203">302</span></span>    |
    |<span data-ttu-id="4b3f7-204">úplně</span><span class="sxs-lookup"><span data-stu-id="4b3f7-204">feeling</span></span>  |  <span data-ttu-id="4b3f7-205">547</span><span class="sxs-lookup"><span data-stu-id="4b3f7-205">547</span></span>    |

    <span data-ttu-id="4b3f7-206">Přidejte následující kód pro vytvoření mapy vyhledávání:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](./snippets/text-classification-tf/csharp/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="4b3f7-207">Přidejte, `Action` Chcete-li změnit velikost pole celé číslo proměnné na celé číslo s pevnou velikostí s dalšími řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](./snippets/text-classification-tf/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="4b3f7-208">Načtení předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="4b3f7-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="4b3f7-209">Přidejte kód pro načtení modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="4b3f7-210">Po načtení modelu můžete extrahovat jeho vstupní a výstupní schéma.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="4b3f7-211">Schémata se zobrazují jenom pro vás a jenom učení.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="4b3f7-212">Tento kód nepotřebujete, aby konečná aplikace fungovala:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](./snippets/text-classification-tf/csharp/Program.cs#GetModelSchema)]

    <span data-ttu-id="4b3f7-213">Vstupní schéma je pole s pevnou délkou kódovaných slov typu Integer.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="4b3f7-214">Výstupní schéma je plovoucí pole pravděpodobnosti, které označuje, zda je mínění revize záporná nebo kladná.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="4b3f7-215">Tyto hodnoty se sčítají na 1, protože pravděpodobnost, že je kladné, je doplňkem pravděpodobnosti mínění negativní.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="4b3f7-216">Vytvoření kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4b3f7-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="4b3f7-217">Vytvořte kanál a rozdělte vstupní text na slova pomocí transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) pro rozdělení textu na slova jako další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](./snippets/text-classification-tf/csharp/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="4b3f7-218">Transformace [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) používá mezery k analýze textu nebo řetězce na slova.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="4b3f7-219">Vytvoří nový sloupec a rozdělí jednotlivé vstupní řetězce na vektor podřetězců na základě oddělovače definovaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="4b3f7-220">Namapujte slova na celočíselné kódování pomocí vyhledávací tabulky, kterou jste deklarovali výše:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](./snippets/text-classification-tf/csharp/Program.cs#MapValue)]

1. <span data-ttu-id="4b3f7-221">Změňte velikost celočíselných kódování proměnné na pevnou délku, kterou vyžaduje model:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](./snippets/text-classification-tf/csharp/Program.cs#CustomMapping)]

1. <span data-ttu-id="4b3f7-222">Klasifikace vstupu pomocí načteného modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="4b3f7-223">Výstup modelu TensorFlow se zavolá `Prediction/Softmax` .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="4b3f7-224">Všimněte si, že název `Prediction/Softmax` je určený podle modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="4b3f7-225">Tento název nemůžete změnit.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-225">You cannot change this name.</span></span>

1. <span data-ttu-id="4b3f7-226">Vytvoří nový sloupec pro předpověď výstupu:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](./snippets/text-classification-tf/csharp/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="4b3f7-227">Je nutné zkopírovat `Prediction/Softmax` sloupec do jednoho s názvem, který lze použít jako vlastnost ve třídě C#: `Prediction` .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="4b3f7-228">`/`Znak není povolen v názvu vlastnosti C#.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="4b3f7-229">Vytvoření modelu ML.NET z kanálu</span><span class="sxs-lookup"><span data-stu-id="4b3f7-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="4b3f7-230">Přidejte kód pro vytvoření modelu z kanálu:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](./snippets/text-classification-tf/csharp/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="4b3f7-231">Model ML.NET se vytvoří z řetězce odhady v kanálu voláním `Fit` metody.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="4b3f7-232">V takovém případě nebudeme pro vytvoření modelu vytvářet žádná data, protože model TensorFlow již byl dříve vyškolen.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="4b3f7-233">Dodáváme prázdný objekt zobrazení dat, který splňuje požadavky `Fit` metody.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="4b3f7-234">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="4b3f7-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="4b3f7-235">Přidejte `PredictSentiment` metodu pod `Main` metodu:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="4b3f7-236">Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek v `PredictSentiment()` metodě:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](./snippets/text-classification-tf/csharp/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="4b3f7-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="4b3f7-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="4b3f7-239">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="4b3f7-240">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="4b3f7-241">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="4b3f7-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4b3f7-242">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="4b3f7-243">Přidejte komentář k otestování předpovědi vyškolených modelů v `Predict()` metodě vytvořením instance `MovieReview` :</span><span class="sxs-lookup"><span data-stu-id="4b3f7-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](./snippets/text-classification-tf/csharp/Program.cs#CreateTestData)]

1. <span data-ttu-id="4b3f7-244">Předání dat testovacích komentářů do do `Prediction Engine` přidejte další řádky kódu v `PredictSentiment()` metodě:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](./snippets/text-classification-tf/csharp/Program.cs#Predict)]

1. <span data-ttu-id="4b3f7-245">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="4b3f7-246">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4b3f7-246">Property</span></span>| <span data-ttu-id="4b3f7-247">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4b3f7-247">Value</span></span>|<span data-ttu-id="4b3f7-248">Typ</span><span class="sxs-lookup"><span data-stu-id="4b3f7-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="4b3f7-249">Předpověď</span><span class="sxs-lookup"><span data-stu-id="4b3f7-249">Prediction</span></span>|<span data-ttu-id="4b3f7-250">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="4b3f7-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="4b3f7-251">float []</span><span class="sxs-lookup"><span data-stu-id="4b3f7-251">float[]</span></span>|

1. <span data-ttu-id="4b3f7-252">Zobrazit předpovědi mínění pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](./snippets/text-classification-tf/csharp/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="4b3f7-253">Na `PredictSentiment` konec metody přidejte volání `Main` :</span><span class="sxs-lookup"><span data-stu-id="4b3f7-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](./snippets/text-classification-tf/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="4b3f7-254">Výsledky</span><span class="sxs-lookup"><span data-stu-id="4b3f7-254">Results</span></span>

<span data-ttu-id="4b3f7-255">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-255">Build and run your application.</span></span>

<span data-ttu-id="4b3f7-256">Výsledky by měly vypadat podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-256">Your results should be similar to the following.</span></span> <span data-ttu-id="4b3f7-257">Během zpracování se zobrazí zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-257">During processing, messages are displayed.</span></span> <span data-ttu-id="4b3f7-258">Můžou se zobrazovat upozornění nebo zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="4b3f7-259">Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="4b3f7-260">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="4b3f7-260">Congratulations!</span></span> <span data-ttu-id="4b3f7-261">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění opětovným použitím předem připraveného `TensorFlow` modelu v ml.NET.</span><span class="sxs-lookup"><span data-stu-id="4b3f7-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="4b3f7-262">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="4b3f7-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="4b3f7-263">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="4b3f7-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4b3f7-264">Načtení předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="4b3f7-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="4b3f7-265">Transformovat text komentáře webu k funkcím vhodným pro model</span><span class="sxs-lookup"><span data-stu-id="4b3f7-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="4b3f7-266">Použití modelu k vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="4b3f7-266">Use the model to make a prediction</span></span>
