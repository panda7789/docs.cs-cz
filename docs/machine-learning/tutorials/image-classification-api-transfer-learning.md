---
title: 'Kurz: Automatická vizuální kontrola pomocí přenosu učení'
description: Tento kurz ukazuje, jak pomocí přenosu učení trénovat TensorFlow hluboké učení model v ML.NET pomocí rozhraní API pro detekci obrázků klasifikovat obrazy betonových povrchů jako popraskané nebo nepopraskané.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607555"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="2d121-103">Kurz: Automatická vizuální kontrola pomocí přenosu učení s ML.NET image klasifikace API</span><span class="sxs-lookup"><span data-stu-id="2d121-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="2d121-104">Naučte se trénovat vlastní model hlubokého učení pomocí přenosu učení, předem natrénovaný tentenzorflow model a ML.NET Image Classification API klasifikovat obrazy betonových povrchů jako popraskané nebo uncracked.</span><span class="sxs-lookup"><span data-stu-id="2d121-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="2d121-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="2d121-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2d121-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="2d121-106">Understand the problem</span></span>
> - <span data-ttu-id="2d121-107">Informace o rozhraní API pro klasifikaci obrázků ML.NET</span><span class="sxs-lookup"><span data-stu-id="2d121-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="2d121-108">Pochopte předem vytrénovaný model</span><span class="sxs-lookup"><span data-stu-id="2d121-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="2d121-109">Použití transferového učení k trénování vlastního modelu klasifikace obrázků TensorFlow</span><span class="sxs-lookup"><span data-stu-id="2d121-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="2d121-110">Klasifikovat obrázky s vlastním modelem</span><span class="sxs-lookup"><span data-stu-id="2d121-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2d121-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d121-111">Prerequisites</span></span>

- <span data-ttu-id="2d121-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="2d121-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="2d121-113">Přehled ukázky učení přenosu klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="2d121-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="2d121-114">Tato ukázka je aplikace konzoly C# .NET Core, která klasifikuje obrazy pomocí předem trénovaného modelu TensorFlow s hloubkovým učením.</span><span class="sxs-lookup"><span data-stu-id="2d121-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="2d121-115">Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2d121-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="2d121-116">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="2d121-116">Understand the problem</span></span>

<span data-ttu-id="2d121-117">Klasifikace obrázků je problém počítačového vidění.</span><span class="sxs-lookup"><span data-stu-id="2d121-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="2d121-118">Klasifikace obrázků převezme obraz jako vstup a kategorizuje jej do předepsané třídy.</span><span class="sxs-lookup"><span data-stu-id="2d121-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="2d121-119">Některé scénáře, kde je užitečná klasifikace bitových obrázků, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="2d121-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="2d121-120">Rozpoznávání obličeje</span><span class="sxs-lookup"><span data-stu-id="2d121-120">Facial recognition</span></span>
- <span data-ttu-id="2d121-121">Detekce emocí</span><span class="sxs-lookup"><span data-stu-id="2d121-121">Emotion detection</span></span>
- <span data-ttu-id="2d121-122">Lékařská diagnóza</span><span class="sxs-lookup"><span data-stu-id="2d121-122">Medical diagnosis</span></span>
- <span data-ttu-id="2d121-123">Detekce orientačních bodů</span><span class="sxs-lookup"><span data-stu-id="2d121-123">Landmark detection</span></span>

<span data-ttu-id="2d121-124">Tento kurz trénuje vlastní model klasifikace obrázků k provedení automatizované vizuální kontroly mostních palub k identifikaci struktur, které jsou poškozeny prasklinami.</span><span class="sxs-lookup"><span data-stu-id="2d121-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="2d121-125">rozhraní API pro klasifikaci obrázků ML.NET</span><span class="sxs-lookup"><span data-stu-id="2d121-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="2d121-126">ML.NET poskytuje různé způsoby provádění klasifikace obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="2d121-127">Tento kurz se vztahuje na učení přenosu pomocí rozhraní API klasifikace obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="2d121-128">Rozhraní API klasifikace obrázků využívá [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), nízkoúrovňové knihovny, která poskytuje vazby Jazyka C# pro rozhraní API Tentenflow C++.</span><span class="sxs-lookup"><span data-stu-id="2d121-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="2d121-129">Co je učení přenosu?</span><span class="sxs-lookup"><span data-stu-id="2d121-129">What is transfer learning?</span></span>

<span data-ttu-id="2d121-130">Transfer learning aplikuje znalosti získané z řešení jednoho problému na jiný související problém.</span><span class="sxs-lookup"><span data-stu-id="2d121-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="2d121-131">Školení modelu hlubokého učení od začátku vyžaduje nastavení několika parametrů, velké množství označených trénovacích dat a obrovské množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="2d121-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="2d121-132">Použití předem trénovaného modelu spolu s učením přenosu umožňuje zkrátit proces školení.</span><span class="sxs-lookup"><span data-stu-id="2d121-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="2d121-133">Tréninkový proces</span><span class="sxs-lookup"><span data-stu-id="2d121-133">Training process</span></span>

<span data-ttu-id="2d121-134">Rozhraní API klasifikace obrázků spustí proces školení načtením předem trénovaného modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="2d121-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="2d121-135">Proces školení se skládá ze dvou kroků:</span><span class="sxs-lookup"><span data-stu-id="2d121-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="2d121-136">Fáze kritického místa</span><span class="sxs-lookup"><span data-stu-id="2d121-136">Bottleneck phase</span></span>
2. <span data-ttu-id="2d121-137">Tréninková fáze</span><span class="sxs-lookup"><span data-stu-id="2d121-137">Training phase</span></span>

![Tréninkové kroky](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="2d121-139">Fáze kritického místa</span><span class="sxs-lookup"><span data-stu-id="2d121-139">Bottleneck phase</span></span>

<span data-ttu-id="2d121-140">Během fáze kritického bodu se načte sada trénovacích bitových kopií a hodnoty obrazových bodů se použijí jako vstup nebo prvky pro zmrazené vrstvy předem trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="2d121-141">Zmrazené vrstvy zahrnují všechny vrstvy v neuronové síti až do předposlední vrstvy, neformálně známé jako vrstva kritického místa.</span><span class="sxs-lookup"><span data-stu-id="2d121-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="2d121-142">Tyto vrstvy jsou označovány jako zmrazené, protože žádné školení dojde v těchto vrstvách a operace jsou předávací.</span><span class="sxs-lookup"><span data-stu-id="2d121-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="2d121-143">Je to v těchto zmrazených vrstev, kde jsou počítány vzorky nižší úrovně, které pomáhají modelu rozlišovat mezi různými třídami.</span><span class="sxs-lookup"><span data-stu-id="2d121-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="2d121-144">Čím větší je počet vrstev, tím více je tento krok výpočtově náročnější.</span><span class="sxs-lookup"><span data-stu-id="2d121-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="2d121-145">Naštěstí vzhledem k tomu, že se jedná o jednorázový výpočet, výsledky mohou být uloženy do mezipaměti a použity v pozdějších spuštěních při experimentování s různými parametry.</span><span class="sxs-lookup"><span data-stu-id="2d121-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="2d121-146">Tréninková fáze</span><span class="sxs-lookup"><span data-stu-id="2d121-146">Training phase</span></span>

<span data-ttu-id="2d121-147">Jakmile jsou vypočteny výstupní hodnoty z fáze kritického místa, jsou použity jako vstup pro přeškolit konečnou vrstvu modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="2d121-148">Tento proces je iterativní a běží pro počet časů určených parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="2d121-149">Během každého spuštění se vyhodnocuje ztráta a přesnost.</span><span class="sxs-lookup"><span data-stu-id="2d121-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="2d121-150">Poté jsou provedeny příslušné úpravy pro zlepšení modelu s cílem minimalizovat ztrátu a maximalizovat přesnost.</span><span class="sxs-lookup"><span data-stu-id="2d121-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="2d121-151">Po dokončení školení jsou výstupem dva formáty modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="2d121-152">Jedním z nich `.pb` je verze modelu a `.zip` druhý je ML.NET serializovanou verzi modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="2d121-153">Při práci v prostředích podporovaných ML.NET se `.zip` doporučuje použít verzi modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="2d121-154">V prostředích, kde není podporována ML.NET, však `.pb` máte možnost použít verzi.</span><span class="sxs-lookup"><span data-stu-id="2d121-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="2d121-155">Pochopte předem vytrénovaný model</span><span class="sxs-lookup"><span data-stu-id="2d121-155">Understand the pretrained model</span></span>

<span data-ttu-id="2d121-156">Předem trénovaný model použitý v tomto kurzu je 101vrstvá varianta modelu ResNet (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="2d121-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="2d121-157">Původní model je trénován pro klasifikaci obrázků do tisíce kategorií.</span><span class="sxs-lookup"><span data-stu-id="2d121-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="2d121-158">Model bere jako vstup obraz o velikosti 224 x 224 a výstupy pravděpodobnosti třídy pro každou třídu, na které je trénovaný.</span><span class="sxs-lookup"><span data-stu-id="2d121-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="2d121-159">Část tohoto modelu se používá k trénování nového modelu pomocí vlastních bitových kopií k předpovědi mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="2d121-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="2d121-160">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="2d121-160">Create console application</span></span>

<span data-ttu-id="2d121-161">Teď, když máte obecné znalosti o přenosu učení a rozhraní API klasifikace obrázků, je čas k vytvoření aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d121-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="2d121-162">Vytvořte **aplikaci základní konzoly C# .NET** s názvem "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="2d121-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="2d121-163">Nainstalujte **Microsoft.ML** verze **1.4.0** NuGet balíček:</span><span class="sxs-lookup"><span data-stu-id="2d121-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="2d121-164">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2d121-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="2d121-165">Jako zdroj balíčku zvolte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="2d121-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="2d121-166">Vyberte kartu **Procházet**.</span><span class="sxs-lookup"><span data-stu-id="2d121-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="2d121-167">Zaškrtněte políčko **Zahrnout předběžnou verzi.**</span><span class="sxs-lookup"><span data-stu-id="2d121-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="2d121-168">Vyhledejte **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="2d121-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="2d121-169">Vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="2d121-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="2d121-170">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="2d121-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="2d121-171">Opakujte tyto kroky pro balíčky **Microsoft.ML.Vision** verze **1.4.0**, **SciSharp.TensorFlow.Redist** verze **1.15.0**a **Microsoft.ML.ImageAnalytics** verze **1.4.0** NuGet.</span><span class="sxs-lookup"><span data-stu-id="2d121-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2d121-172">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="2d121-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="2d121-173">Datové sady pro tento kurz jsou z Maguire, Marc; Dorafshan, Sattar; a Thomas, Robert J., "SDNET2018: Konkrétní datová sada obrazu bez vak pro aplikace strojového učení" (2018).</span><span class="sxs-lookup"><span data-stu-id="2d121-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="2d121-174">Procházet všechny datové sady.</span><span class="sxs-lookup"><span data-stu-id="2d121-174">Browse all Datasets.</span></span> <span data-ttu-id="2d121-175">Papír 48.</span><span class="sxs-lookup"><span data-stu-id="2d121-175">Paper 48.</span></span> <span data-ttu-id="2d121-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="2d121-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="2d121-177">SDNET2018 je obrazová datová sada, která obsahuje poznámky pro popraskané a neprasklé betonové konstrukce (mostní paluby, stěny a dlažba).</span><span class="sxs-lookup"><span data-stu-id="2d121-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Ukázky mostního balíčku datové sady SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="2d121-179">Data jsou uspořádána do tří podadresářů:</span><span class="sxs-lookup"><span data-stu-id="2d121-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="2d121-180">D obsahuje obrázky mostní paluby</span><span class="sxs-lookup"><span data-stu-id="2d121-180">D contains bridge deck images</span></span>
- <span data-ttu-id="2d121-181">P obsahuje obrázky chodníků</span><span class="sxs-lookup"><span data-stu-id="2d121-181">P contains pavement images</span></span>
- <span data-ttu-id="2d121-182">W obsahuje nástěnné obrázky</span><span class="sxs-lookup"><span data-stu-id="2d121-182">W contains wall images</span></span>

<span data-ttu-id="2d121-183">Každý z těchto podadresářů obsahuje dva další podadresáře s předponou:</span><span class="sxs-lookup"><span data-stu-id="2d121-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="2d121-184">C je předpona používaná pro prasklé povrchy</span><span class="sxs-lookup"><span data-stu-id="2d121-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="2d121-185">U je předpona používaná pro neprasklé povrchy</span><span class="sxs-lookup"><span data-stu-id="2d121-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="2d121-186">V tomto kurzu se používají pouze obrazy mostové paluby.</span><span class="sxs-lookup"><span data-stu-id="2d121-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="2d121-187">Stáhněte si [datovou sadu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="2d121-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="2d121-188">Vytvořte adresář s názvem "datové zdroje" v projektu pro uložení souborů datové sady.</span><span class="sxs-lookup"><span data-stu-id="2d121-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="2d121-189">Zkopírujte podadresáře *CD* a *UD* z nedávno rozepnutého adresáře do adresáře *datových zdrojů.*</span><span class="sxs-lookup"><span data-stu-id="2d121-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="2d121-190">Vytvoření vstupních a výstupních tříd</span><span class="sxs-lookup"><span data-stu-id="2d121-190">Create input and output classes</span></span>

1. <span data-ttu-id="2d121-191">Otevřete *soubor Program.cs* a `using` nahraďte existující příkazy v horní části souboru následujícími:</span><span class="sxs-lookup"><span data-stu-id="2d121-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="2d121-192">Pod `Program` třídou v *Program.cs*vytvořte třídu s názvem `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="2d121-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="2d121-193">Tato třída se používá k reprezentaci původně načtených dat.</span><span class="sxs-lookup"><span data-stu-id="2d121-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="2d121-194">`ImageData`obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2d121-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="2d121-195">`ImagePath`je plně kvalifikovaná cesta, do které je obraz uložen.</span><span class="sxs-lookup"><span data-stu-id="2d121-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="2d121-196">`Label`je kategorie, do které obrázek patří.</span><span class="sxs-lookup"><span data-stu-id="2d121-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="2d121-197">Toto je hodnota předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2d121-197">This is the value to predict.</span></span>

1. <span data-ttu-id="2d121-198">Vytváření tříd pro vstupní a výstupní data</span><span class="sxs-lookup"><span data-stu-id="2d121-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="2d121-199">Pod `ImageData` třídou definujte schéma vstupních dat v nové `ModelInput`třídě s názvem .</span><span class="sxs-lookup"><span data-stu-id="2d121-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="2d121-200">`ModelInput`obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2d121-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="2d121-201">`Image`je `byte[]` reprezentace obrazu.</span><span class="sxs-lookup"><span data-stu-id="2d121-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="2d121-202">Model očekává, že obrazová data budou tohoto typu pro trénování.</span><span class="sxs-lookup"><span data-stu-id="2d121-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="2d121-203">`LabelAsKey`je číselná reprezentace `Label`rozhraní .</span><span class="sxs-lookup"><span data-stu-id="2d121-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="2d121-204">`ImagePath`je plně kvalifikovaná cesta, do které je obraz uložen.</span><span class="sxs-lookup"><span data-stu-id="2d121-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="2d121-205">`Label`je kategorie, do které obrázek patří.</span><span class="sxs-lookup"><span data-stu-id="2d121-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="2d121-206">Toto je hodnota předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2d121-206">This is the value to predict.</span></span>

        <span data-ttu-id="2d121-207">Pouze `Image` `LabelAsKey` a slouží k trénování modelu a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2d121-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="2d121-208">`ImagePath` Vlastnosti `Label` a jsou uchovávány pro usnadnění přístupu k původnímu názvu souboru obrázku a kategorii.</span><span class="sxs-lookup"><span data-stu-id="2d121-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="2d121-209">Potom pod `ModelInput` třídou definujte schéma výstupních dat v nové `ModelOutput`třídě s názvem .</span><span class="sxs-lookup"><span data-stu-id="2d121-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="2d121-210">`ModelOutput`obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2d121-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="2d121-211">`ImagePath`je plně kvalifikovaná cesta, do které je obraz uložen.</span><span class="sxs-lookup"><span data-stu-id="2d121-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="2d121-212">`Label`je původní kategorie, do které obrázek patří.</span><span class="sxs-lookup"><span data-stu-id="2d121-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="2d121-213">Toto je hodnota předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2d121-213">This is the value to predict.</span></span>
        - <span data-ttu-id="2d121-214">`PredictedLabel`je hodnota předpovězená modelem.</span><span class="sxs-lookup"><span data-stu-id="2d121-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="2d121-215">Podobně `ModelInput`jako , `PredictedLabel` pouze je nutné, aby předpovědi, protože obsahuje předpověď provedené modelem.</span><span class="sxs-lookup"><span data-stu-id="2d121-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="2d121-216">`ImagePath` Vlastnosti `Label` a jsou zachovány pro usnadnění přístupu k původnímu názvu souboru obrázku a kategorii.</span><span class="sxs-lookup"><span data-stu-id="2d121-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="2d121-217">Vytvoření adresáře pracovního prostoru</span><span class="sxs-lookup"><span data-stu-id="2d121-217">Create workspace directory</span></span>

<span data-ttu-id="2d121-218">Pokud se data školení a ověření nemění často, je vhodné ukládat do mezipaměti vypočítané hodnoty kritického místa pro další spuštění.</span><span class="sxs-lookup"><span data-stu-id="2d121-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="2d121-219">V projektu vytvořte nový adresář s názvem *pracovní prostor* pro `.pb` uložení vypočítaných hodnot kritického místa a verze modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="2d121-220">Definování cest a inicializaci proměnných</span><span class="sxs-lookup"><span data-stu-id="2d121-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="2d121-221">Uvnitř `Main` metody definujte umístění prostředků, vypočítané hodnoty `.pb` kritického místa a verzi modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="2d121-222">Inicializovat `mlContext` proměnnou s novou instanci [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="2d121-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="2d121-223">Třída [MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET a inicializace mlContext vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2d121-224">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="2d121-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2d121-225">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="2d121-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="2d121-226">Vytvořit metodu načítání dat</span><span class="sxs-lookup"><span data-stu-id="2d121-226">Create data loading utility method</span></span>

<span data-ttu-id="2d121-227">Obrázky jsou uloženy ve dvou podadresářích.</span><span class="sxs-lookup"><span data-stu-id="2d121-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="2d121-228">Před načtením dat je třeba je naformátovat do seznamu `ImageData` objektů.</span><span class="sxs-lookup"><span data-stu-id="2d121-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="2d121-229">Chcete-li tak `LoadImagesFromDirectory` učinit, `Main` vytvořte metodu pod metodou.</span><span class="sxs-lookup"><span data-stu-id="2d121-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="2d121-230">Uvnitř `LoadImagesDirectory` přidáte následující kód získat všechny cesty k souborům z podadresářů:</span><span class="sxs-lookup"><span data-stu-id="2d121-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="2d121-231">Potom iterát prostřednictvím každého ze `foreach` souborů pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="2d121-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="2d121-232">Uvnitř `foreach` příkazu zkontrolujte, zda jsou podporovány přípony souborů.</span><span class="sxs-lookup"><span data-stu-id="2d121-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="2d121-233">Rozhraní API pro klasifikaci obrázků podporuje formáty JPEG a PNG.</span><span class="sxs-lookup"><span data-stu-id="2d121-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="2d121-234">Potom získat popisek pro soubor.</span><span class="sxs-lookup"><span data-stu-id="2d121-234">Then, get the label for the file.</span></span> <span data-ttu-id="2d121-235">Pokud `useFolderNameAsLabel` je parametr `true`nastaven na hodnotu , použije se jako popisek nadřazený adresář, do kterého je soubor uložen.</span><span class="sxs-lookup"><span data-stu-id="2d121-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="2d121-236">V opačném případě očekává, že popisek bude předponou názvu souboru nebo samotného názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="2d121-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="2d121-237">Nakonec vytvořte novou `ModelInput`instanci .</span><span class="sxs-lookup"><span data-stu-id="2d121-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="2d121-238">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="2d121-238">Prepare the data</span></span>

1. <span data-ttu-id="2d121-239">Zpět v `Main` metodě, `LoadFromDirectory` použijte metodu utility získat seznam obrázků používaných pro školení.</span><span class="sxs-lookup"><span data-stu-id="2d121-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="2d121-240">Potom načtěte obrázky do [`IDataView`](xref:Microsoft.ML.IDataView) pomocí [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody.</span><span class="sxs-lookup"><span data-stu-id="2d121-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="2d121-241">Data jsou načtena v pořadí, v jakém byla přečtena z adresářů.</span><span class="sxs-lookup"><span data-stu-id="2d121-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="2d121-242">Chcete-li data vyvážit, [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) zamíchejte je pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="2d121-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="2d121-243">Modely strojového učení očekávají, že vstup bude v číselném formátu.</span><span class="sxs-lookup"><span data-stu-id="2d121-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="2d121-244">Proto některé předběžné zpracování je třeba provést na data před školení.</span><span class="sxs-lookup"><span data-stu-id="2d121-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="2d121-245">Vytvořte [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) skládá z [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` a transformuje.</span><span class="sxs-lookup"><span data-stu-id="2d121-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="2d121-246">Transformace `MapValueToKey` převezme kategorickou hodnotu ve sloupci, `Label` převede ji na číselnou `KeyType` `LabelAsKey`hodnotu a uloží ji do nového sloupce s názvem .</span><span class="sxs-lookup"><span data-stu-id="2d121-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="2d121-247">Trvá `LoadImages` hodnoty ze `ImagePath` sloupce spolu `imageFolder` s parametrem načíst obrázky pro školení.</span><span class="sxs-lookup"><span data-stu-id="2d121-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="2d121-248">Pomocí [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody použijte data následovaný `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) metodou, která vrátí [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předem zpracovaná data.</span><span class="sxs-lookup"><span data-stu-id="2d121-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="2d121-249">Chcete-li trénovat model, je důležité mít trénovací datovou sadu, stejně jako ověřovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="2d121-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="2d121-250">Model je trénován na tréninkové sadě.</span><span class="sxs-lookup"><span data-stu-id="2d121-250">The model is trained on the training set.</span></span> <span data-ttu-id="2d121-251">Jak dobře to dělá předpovědi na neviditelná data se měří výkon proti sada ověření.</span><span class="sxs-lookup"><span data-stu-id="2d121-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="2d121-252">Na základě výsledků tohoto výkonu model provádí úpravy toho, co se naučil ve snaze zlepšit.</span><span class="sxs-lookup"><span data-stu-id="2d121-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="2d121-253">Ověřovací sada může pocházet buď z rozdělení původní datové sady nebo z jiného zdroje, který již byl vyhrazen pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="2d121-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="2d121-254">V tomto případě je předzpracovaná datová sada rozdělena na trénovací, ověřovací a testovací sady.</span><span class="sxs-lookup"><span data-stu-id="2d121-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="2d121-255">Ukázka kódu výše provede dvě rozdělení.</span><span class="sxs-lookup"><span data-stu-id="2d121-255">The code sample above performs two splits.</span></span> <span data-ttu-id="2d121-256">Nejprve jsou předzpracovaná data rozdělena a 70 % se používá pro školení, zatímco zbývajících 30 % se používá k ověření.</span><span class="sxs-lookup"><span data-stu-id="2d121-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="2d121-257">Potom 30% ověřovací sada je dále rozdělena do validace a testovací sady, kde 90 % se používá pro ověření a 10 % se používá pro testování.</span><span class="sxs-lookup"><span data-stu-id="2d121-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="2d121-258">Způsob, jak přemýšlet o účelu těchto datových oddílů je při zkoušce.</span><span class="sxs-lookup"><span data-stu-id="2d121-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="2d121-259">Při studiu na zkoušku, můžete zkontrolovat své poznámky, knihy, nebo jiné zdroje, abyste si pochopení pojmů, které jsou na zkoušku.</span><span class="sxs-lookup"><span data-stu-id="2d121-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="2d121-260">Na tohle je vlaková souprava.</span><span class="sxs-lookup"><span data-stu-id="2d121-260">This is what the train set is for.</span></span> <span data-ttu-id="2d121-261">Pak můžete udělat falešnou zkoušku, abyste si ověřili své znalosti.</span><span class="sxs-lookup"><span data-stu-id="2d121-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="2d121-262">To je místo, kde validační sada přijde vhod.</span><span class="sxs-lookup"><span data-stu-id="2d121-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="2d121-263">Chcete-li zkontrolovat, zda máte dobrý přehled o pojmy před přijetím skutečné zkoušky.</span><span class="sxs-lookup"><span data-stu-id="2d121-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="2d121-264">Na základě těchto výsledků, budete mít na vědomí, co jste udělali špatně, nebo nerozuměl dobře a začlenit své změny, jak si prohlédnout pro skutečnou zkoušku.</span><span class="sxs-lookup"><span data-stu-id="2d121-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="2d121-265">Nakonec si udělej zkoušku.</span><span class="sxs-lookup"><span data-stu-id="2d121-265">Finally, you take the exam.</span></span> <span data-ttu-id="2d121-266">To je to, co testovací sada se používá pro.</span><span class="sxs-lookup"><span data-stu-id="2d121-266">This is what the test set is used for.</span></span> <span data-ttu-id="2d121-267">Nikdy jste neviděli otázky, které jsou na zkoušku a nyní používají to, co jste se naučili z tréninku a validace aplikovat své znalosti na úkol po ruce.</span><span class="sxs-lookup"><span data-stu-id="2d121-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="2d121-268">Přiřaďte oddíly jejich příslušné hodnoty pro data vlaku, ověření a testování.</span><span class="sxs-lookup"><span data-stu-id="2d121-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="2d121-269">Definování kanálu školení</span><span class="sxs-lookup"><span data-stu-id="2d121-269">Define the training pipeline</span></span>

<span data-ttu-id="2d121-270">Model školení se skládá z několika kroků.</span><span class="sxs-lookup"><span data-stu-id="2d121-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="2d121-271">Nejprve rozhraní API klasifikace obrázků se používá k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="2d121-272">Poté jsou kódované popisky `PredictedLabel` ve sloupci převedeny zpět na `MapKeyToValue` původní kategorickou hodnotu pomocí transformace.</span><span class="sxs-lookup"><span data-stu-id="2d121-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="2d121-273">Vytvořte novou proměnnou pro uložení sady požadovaných `ImageClassificationTrainer`a volitelných parametrů pro rozhraní .</span><span class="sxs-lookup"><span data-stu-id="2d121-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="2d121-274">A `ImageClassificationTrainer` má několik volitelných parametrů:</span><span class="sxs-lookup"><span data-stu-id="2d121-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="2d121-275">`FeatureColumnName`je sloupec, který se používá jako vstup pro model.</span><span class="sxs-lookup"><span data-stu-id="2d121-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="2d121-276">`LabelColumnName`je sloupec pro hodnotu předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2d121-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="2d121-277">`ValidationSet`je [`IDataView`](xref:Microsoft.ML.IDataView) obsahující ověřovací údaje.</span><span class="sxs-lookup"><span data-stu-id="2d121-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="2d121-278">`Arch`definuje, které z předem trénovaných architektur modelu použít.</span><span class="sxs-lookup"><span data-stu-id="2d121-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="2d121-279">Tento kurz používá 101vrstvou variantu modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="2d121-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="2d121-280">`MetricsCallback`váže funkci ke sledování průběhu během tréninku.</span><span class="sxs-lookup"><span data-stu-id="2d121-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="2d121-281">`TestOnTrainSet`říká modelu k měření výkonu proti trénovací sady, když není k dispozici žádná sada ověření.</span><span class="sxs-lookup"><span data-stu-id="2d121-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="2d121-282">`ReuseTrainSetBottleneckCachedValues`říká modelu, zda použít hodnoty uložené v mezipaměti z fáze kritického místa v následných spuštěních.</span><span class="sxs-lookup"><span data-stu-id="2d121-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="2d121-283">Fáze kritického místa je jednorázový průchozí výpočetní, který je výpočtově náročný při prvním provedení.</span><span class="sxs-lookup"><span data-stu-id="2d121-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="2d121-284">Pokud se trénovací data nezmění a chcete experimentovat s různým počtem epoch nebo velikostí dávky, použití hodnot uložených v mezipaměti výrazně zkracuje dobu potřebnou k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="2d121-285">`ReuseValidationSetBottleneckCachedValues`je podobný `ReuseTrainSetBottleneckCachedValues` pouze tomu, že v tomto případě je pro ověřovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="2d121-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="2d121-286">`WorkspacePath`definuje adresář, kam se mají ukládat `.pb` vypočítané hodnoty kritického místa a verze modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="2d121-287">Definujte [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) kanál školení, který `mapLabelEstimator` se `ImageClassificationTrainer`skládá z a .</span><span class="sxs-lookup"><span data-stu-id="2d121-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="2d121-288">Pomocí [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody trénovat model.</span><span class="sxs-lookup"><span data-stu-id="2d121-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="2d121-289">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="2d121-289">Use the model</span></span>

<span data-ttu-id="2d121-290">Nyní, když jste vycvičili model, je čas jej použít ke klasifikaci obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="2d121-291">Pod `Main` metodou vytvořte novou metodu nástroje volanou `OutputPrediction` k zobrazení informací o predikci v konzole.</span><span class="sxs-lookup"><span data-stu-id="2d121-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="2d121-292">Klasifikace jednoho obrázku</span><span class="sxs-lookup"><span data-stu-id="2d121-292">Classify a single image</span></span>

1. <span data-ttu-id="2d121-293">Přidejte novou `ClassifySingleImage` metodu `Main` nazývanou pod metodu, aby se a výstup jedné predikce obrazu.</span><span class="sxs-lookup"><span data-stu-id="2d121-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="2d121-294">Vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uvnitř `ClassifySingleImage` metody.</span><span class="sxs-lookup"><span data-stu-id="2d121-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="2d121-295">Je [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) rozhraní API pohodlí, které umožňuje předat a potom provést předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="2d121-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="2d121-296">Chcete-li `ModelInput` získat přístup `data` [`IDataView`](xref:Microsoft.ML.IDataView) k [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) jedné [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) instanci, převeďte na pomocí metody a pak získat první pozorování.</span><span class="sxs-lookup"><span data-stu-id="2d121-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="2d121-297">Pomocí [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody klasifikovat obraz.</span><span class="sxs-lookup"><span data-stu-id="2d121-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="2d121-298">Výstup předpověď do konzoly `OutputPrediction` s metodou.</span><span class="sxs-lookup"><span data-stu-id="2d121-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="2d121-299">Uvnitř `Main` metody volejte `ClassifySingleImage` pomocí testovací sady obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="2d121-300">Klasifikace více obrázků</span><span class="sxs-lookup"><span data-stu-id="2d121-300">Classify multiple images</span></span>

1. <span data-ttu-id="2d121-301">Přidejte novou `ClassifyImages` metodu `ClassifySingleImage` nazývanou pod metodu pro vytvoření a výstup více předpovědí obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="2d121-302">Vytvořte [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předpovědi pomocí [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody.</span><span class="sxs-lookup"><span data-stu-id="2d121-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="2d121-303">Do `ClassifyImages` metody přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="2d121-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="2d121-304">Chcete-li itorovat přes předpovědi, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) převést na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody a pak získat prvních 10 pozorování.</span><span class="sxs-lookup"><span data-stu-id="2d121-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="2d121-305">Iterate a výstup původní a předpovídané popisky pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2d121-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="2d121-306">Nakonec uvnitř `Main` metody volání `ClassifyImages` pomocí testovací sady obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="2d121-307">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2d121-307">Run the application</span></span>

<span data-ttu-id="2d121-308">Spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2d121-308">Run your console app.</span></span> <span data-ttu-id="2d121-309">Výstup by měl být podobný tomu níže.</span><span class="sxs-lookup"><span data-stu-id="2d121-309">The output should be similar to that below.</span></span> <span data-ttu-id="2d121-310">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="2d121-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="2d121-311">Pro stručnost byl výstup zhuštěn.</span><span class="sxs-lookup"><span data-stu-id="2d121-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="2d121-312">**Fáze kritického místa**</span><span class="sxs-lookup"><span data-stu-id="2d121-312">**Bottleneck phase**</span></span>

<span data-ttu-id="2d121-313">Pro název obrázku není vytištěna žádná hodnota, `byte[]` protože obrázky jsou načteny jako a proto není k dispozici žádný název obrázku.</span><span class="sxs-lookup"><span data-stu-id="2d121-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="2d121-314">**Tréninková fáze**</span><span class="sxs-lookup"><span data-stu-id="2d121-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="2d121-315">**Klasifikace výstupu obrazů**</span><span class="sxs-lookup"><span data-stu-id="2d121-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="2d121-316">Při kontrole *7001-220.jpg* obraz, můžete vidět, že to ve skutečnosti není popraskané.</span><span class="sxs-lookup"><span data-stu-id="2d121-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Obrázek datové sady SDNET2018 použitý pro předpověď](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="2d121-318">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="2d121-318">Congratulations!</span></span> <span data-ttu-id="2d121-319">Nyní jste úspěšně vytvořili model hlubokého učení pro klasifikaci obrázků.</span><span class="sxs-lookup"><span data-stu-id="2d121-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="2d121-320">Zlepšete model</span><span class="sxs-lookup"><span data-stu-id="2d121-320">Improve the model</span></span>

<span data-ttu-id="2d121-321">Pokud nejste spokojeni s výsledky modelu, můžete se pokusit zlepšit jeho výkon vyzkoušením některých z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="2d121-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="2d121-322">**Více dat**: Čím více příkladů se model naučí, tím lépe se provádí.</span><span class="sxs-lookup"><span data-stu-id="2d121-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="2d121-323">Stáhněte si úplnou [datovou sadu SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) a použijte ji k trénování.</span><span class="sxs-lookup"><span data-stu-id="2d121-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="2d121-324">**Rozšířit data**: Běžnou technikou pro přidání rozmanitosti k datům je rozšířit data pořízením obrázku a použitím různých transformací (otočení, překlopení, posun, oříznutí).</span><span class="sxs-lookup"><span data-stu-id="2d121-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="2d121-325">Tím přidáte rozmanitější příklady pro model učit se od.</span><span class="sxs-lookup"><span data-stu-id="2d121-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="2d121-326">**Vlak na delší dobu:** Čím déle budete trénovat, tím více naladěn model bude.</span><span class="sxs-lookup"><span data-stu-id="2d121-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="2d121-327">Zvýšení počtu epoch může zlepšit výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="2d121-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="2d121-328">**Experimentujte s hyper-parametry**: Kromě parametrů použitých v tomto kurzu lze vyladit další parametry, které potenciálně zlepšují výkon.</span><span class="sxs-lookup"><span data-stu-id="2d121-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="2d121-329">Změna rychlostučení, která určuje velikost aktualizací provedených v modelu po každé epochy může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="2d121-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="2d121-330">**Použití jiné architektury modelu**: V závislosti na tom, jak data vypadají, se model, který se nejlépe naučí jeho funkce, může lišit.</span><span class="sxs-lookup"><span data-stu-id="2d121-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="2d121-331">Pokud nejste spokojeni s výkonem modelu, zkuste změnit architekturu.</span><span class="sxs-lookup"><span data-stu-id="2d121-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2d121-332">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2d121-332">Additional Resources</span></span>

- <span data-ttu-id="2d121-333">[Hloubkové učení vs Strojové učení](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="2d121-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2d121-334">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2d121-334">Next steps</span></span>

<span data-ttu-id="2d121-335">V tomto kurzu jste se naučili, jak vytvořit vlastní model hlubokého učení pomocí přenosu učení, předem vycvičené klasifikace obrázků TensorFlow model a ML.NET klasifikace obrázků API pro klasifikaci obrazů betonových povrchů jako popraskané nebo uncracked.</span><span class="sxs-lookup"><span data-stu-id="2d121-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="2d121-336">Přejdete k dalšímu kurzu, abyste se dozvěděli více.</span><span class="sxs-lookup"><span data-stu-id="2d121-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d121-337">Detekce objektů</span><span class="sxs-lookup"><span data-stu-id="2d121-337">Object Detection</span></span>](object-detection-onnx.md)
