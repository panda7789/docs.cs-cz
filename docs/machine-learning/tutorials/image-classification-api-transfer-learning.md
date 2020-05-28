---
title: 'Kurz: automatizované vizuální prověřování pomocí učení přenosu'
description: V tomto kurzu se dozvíte, jak pomocí funkce Transfer Learning vytvořit TensorFlow model hloubkového učení v ML.NET pomocí rozhraní API pro detekci imagí pro klasifikaci imagí konkrétních ploch jako prasklé nebo neprasklé.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2915259d7c7031b9e699c7fd0cf65cf723c41680
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144419"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="2354e-103">Kurz: automatizované vizuální prověřování pomocí přenosu přenosu s rozhraním API pro klasifikaci imagí ML.NET</span><span class="sxs-lookup"><span data-stu-id="2354e-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="2354e-104">Naučte se naučit vlastní model hloubkového učení s využitím učení přenosu, předTensorFlowho modelu a rozhraní API pro klasifikaci imagí ml.NET pro klasifikaci imagí konkrétních povrchů jako prasklé nebo prolomené.</span><span class="sxs-lookup"><span data-stu-id="2354e-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="2354e-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="2354e-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2354e-106">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="2354e-106">Understand the problem</span></span>
> - <span data-ttu-id="2354e-107">Další informace o rozhraní API pro klasifikaci imagí ML.NET</span><span class="sxs-lookup"><span data-stu-id="2354e-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="2354e-108">Pochopení předvýukového modelu</span><span class="sxs-lookup"><span data-stu-id="2354e-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="2354e-109">Použití učení transferu k výuce vlastního modelu klasifikace imagí TensorFlow</span><span class="sxs-lookup"><span data-stu-id="2354e-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="2354e-110">Klasifikace imagí pomocí vlastního modelu</span><span class="sxs-lookup"><span data-stu-id="2354e-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2354e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2354e-111">Prerequisites</span></span>

- <span data-ttu-id="2354e-112">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="2354e-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="2354e-113">Přehled výukového kurzu přenosu klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="2354e-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="2354e-114">Tato ukázka je Konzolová aplikace C# .NET Core, která klasifikuje Image pomocí předTensorFlowho modelu hloubkového učení.</span><span class="sxs-lookup"><span data-stu-id="2354e-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="2354e-115">Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2354e-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="2354e-116">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="2354e-116">Understand the problem</span></span>

<span data-ttu-id="2354e-117">Klasifikace obrázku je problém počítačové vize.</span><span class="sxs-lookup"><span data-stu-id="2354e-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="2354e-118">Klasifikace obrázku bere jako vstup obrázek a zařadí ho do předepsané třídy.</span><span class="sxs-lookup"><span data-stu-id="2354e-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="2354e-119">Některé scénáře, kde je klasifikace obrázku užitečná, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="2354e-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="2354e-120">Rozpoznávání obličeje</span><span class="sxs-lookup"><span data-stu-id="2354e-120">Facial recognition</span></span>
- <span data-ttu-id="2354e-121">Detekce emoce</span><span class="sxs-lookup"><span data-stu-id="2354e-121">Emotion detection</span></span>
- <span data-ttu-id="2354e-122">Lékařské diagnostiky</span><span class="sxs-lookup"><span data-stu-id="2354e-122">Medical diagnosis</span></span>
- <span data-ttu-id="2354e-123">Detekce orientačních bodů</span><span class="sxs-lookup"><span data-stu-id="2354e-123">Landmark detection</span></span>

<span data-ttu-id="2354e-124">V tomto kurzu se nasazuje model klasifikace vlastních imagí, který provede automatizovanou vizuální kontrolu balíčku mostu a identifikuje tak struktury, které jsou poškozené prasklinami.</span><span class="sxs-lookup"><span data-stu-id="2354e-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="2354e-125">Rozhraní API pro klasifikaci imagí ML.NET</span><span class="sxs-lookup"><span data-stu-id="2354e-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="2354e-126">ML.NET poskytuje různé způsoby provádění klasifikace imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="2354e-127">Tento kurz se týká učení přenosu pomocí rozhraní API klasifikace imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="2354e-128">Rozhraní API pro klasifikaci imagí využívá [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)knihovnu nižší úrovně, která poskytuje vazby jazyka C# pro rozhraní API pro TensorFlow C++.</span><span class="sxs-lookup"><span data-stu-id="2354e-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="2354e-129">Co je učení přenosu?</span><span class="sxs-lookup"><span data-stu-id="2354e-129">What is transfer learning?</span></span>

<span data-ttu-id="2354e-130">Učení pro přenos používá znalostní bázi získaná od řešení jednoho problému s jiným souvisejícím problémem.</span><span class="sxs-lookup"><span data-stu-id="2354e-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="2354e-131">Školení modelu hloubkového učení od začátku vyžaduje nastavení několika parametrů, velkého množství podrobných školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="2354e-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="2354e-132">Použití předzpracovaného modelu spolu s učením přenosu vám umožní zástupce školicího procesu.</span><span class="sxs-lookup"><span data-stu-id="2354e-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="2354e-133">Školicí proces</span><span class="sxs-lookup"><span data-stu-id="2354e-133">Training process</span></span>

<span data-ttu-id="2354e-134">Rozhraní API klasifikace imagí spustí školicí proces načtením předinstalovaného modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="2354e-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="2354e-135">Školicí proces se skládá ze dvou kroků:</span><span class="sxs-lookup"><span data-stu-id="2354e-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="2354e-136">Fáze kritického bodu</span><span class="sxs-lookup"><span data-stu-id="2354e-136">Bottleneck phase</span></span>
2. <span data-ttu-id="2354e-137">Fáze školení</span><span class="sxs-lookup"><span data-stu-id="2354e-137">Training phase</span></span>

![Postup školení](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="2354e-139">Fáze kritického bodu</span><span class="sxs-lookup"><span data-stu-id="2354e-139">Bottleneck phase</span></span>

<span data-ttu-id="2354e-140">Během fáze kritických míst se načte sada školicích imagí a jako vstup a funkce se použijí pixelové hodnoty pro zmrazené vrstvy předinstalovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="2354e-141">Zmrazené vrstvy zahrnují všechny vrstvy v neuronové síti až do poslední vrstvy, která je Poznáma jako kritická vrstva.</span><span class="sxs-lookup"><span data-stu-id="2354e-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="2354e-142">Tyto vrstvy se označují jako zmrazené, protože na těchto vrstvách a operacích neproběhne žádné školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="2354e-143">Je v těchto zmrazených vrstvách, kde jsou vypočítány vzory nižší úrovně, které usnadňují model odlišení různých tříd.</span><span class="sxs-lookup"><span data-stu-id="2354e-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="2354e-144">Čím větší je počet vrstev, tím více výpočetně náročné je tento krok.</span><span class="sxs-lookup"><span data-stu-id="2354e-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="2354e-145">Naštěstí, protože se jedná o jednorázový výpočet, mohou být výsledky uloženy do mezipaměti a použity v pozdějších spuštěních při experimentování s různými parametry.</span><span class="sxs-lookup"><span data-stu-id="2354e-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="2354e-146">Fáze školení</span><span class="sxs-lookup"><span data-stu-id="2354e-146">Training phase</span></span>

<span data-ttu-id="2354e-147">Až budou výstupní hodnoty z kritické fáze vypočítány, používají se jako vstup k přeškolování finální vrstvy modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="2354e-148">Tento proces je iterativní a spouští se v počtu pokusů určených parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="2354e-149">Během každého spuštění jsou vyhodnocovány ztráty a přesnost.</span><span class="sxs-lookup"><span data-stu-id="2354e-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="2354e-150">Pak jsou provedeny příslušné úpravy pro zlepšení modelu s cílem minimalizovat ztrátu a maximalizovat přesnost.</span><span class="sxs-lookup"><span data-stu-id="2354e-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="2354e-151">Po dokončení školení jsou výstupem dva formáty modelů.</span><span class="sxs-lookup"><span data-stu-id="2354e-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="2354e-152">Jedna z nich je `.pb` verze modelu a druhá je `.zip` ml.NET serializovaná verze modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="2354e-153">Při práci v prostředích podporovaných aplikací ML.NET se doporučuje použít `.zip` verzi modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="2354e-154">V prostředích, kde ML.NET není podporovaný, máte ale možnost použít tuto `.pb` verzi.</span><span class="sxs-lookup"><span data-stu-id="2354e-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="2354e-155">Pochopení předvýukového modelu</span><span class="sxs-lookup"><span data-stu-id="2354e-155">Understand the pretrained model</span></span>

<span data-ttu-id="2354e-156">Předem vydaný model použitý v tomto kurzu je 101 varianta modelu zbytkové sítě (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="2354e-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="2354e-157">Původní model je vyškolen pro klasifikaci imagí do tisíc kategorií.</span><span class="sxs-lookup"><span data-stu-id="2354e-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="2354e-158">Model bere jako vstup obrázek o velikosti 224 × 224 a vypisuje pravděpodobnosti třídy pro každou třídu, na které je technologie IT vyškolená.</span><span class="sxs-lookup"><span data-stu-id="2354e-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="2354e-159">Součástí tohoto modelu je vyučování nového modelu pomocí vlastních imagí, aby bylo možné předpovědi mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="2354e-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="2354e-160">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="2354e-160">Create console application</span></span>

<span data-ttu-id="2354e-161">Teď, když máte obecné znalosti o učení přenosů a rozhraní API klasifikace imagí, je čas sestavování aplikace.</span><span class="sxs-lookup"><span data-stu-id="2354e-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="2354e-162">Vytvořte **konzolovou aplikaci C# .NET Core** nazvanou "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="2354e-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="2354e-163">Nainstalujte balíček NuGet verze **Microsoft.ml** **1.4.0** :</span><span class="sxs-lookup"><span data-stu-id="2354e-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="2354e-164">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2354e-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="2354e-165">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="2354e-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="2354e-166">Vyberte kartu **Procházet**.</span><span class="sxs-lookup"><span data-stu-id="2354e-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="2354e-167">Zaškrtněte políčko **zahrnout předběžné verze** .</span><span class="sxs-lookup"><span data-stu-id="2354e-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="2354e-168">Vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="2354e-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="2354e-169">Vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="2354e-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="2354e-170">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="2354e-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="2354e-171">Opakujte tyto kroky pro balíček **Microsoft. ml. Vision** verze **1.4.0**, **SciSharp. TensorFlow. Redist** verze **1.15.0**a **Microsoft. ml. ImageAnalytics** verze **1.4.0** NuGet Packages.</span><span class="sxs-lookup"><span data-stu-id="2354e-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2354e-172">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="2354e-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="2354e-173">Datové sady pro tento kurz jsou z Maguire, matolin; Dorafshan, Sattar; a Tomáš, Robert J., "SDNET2018: konkrétní datová sada obrázku trhlin pro aplikace pro strojové učení" (2018).</span><span class="sxs-lookup"><span data-stu-id="2354e-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="2354e-174">Procházet všechny datové sady.</span><span class="sxs-lookup"><span data-stu-id="2354e-174">Browse all Datasets.</span></span> <span data-ttu-id="2354e-175">Papír 48.</span><span class="sxs-lookup"><span data-stu-id="2354e-175">Paper 48.</span></span> <https://digitalcommons.usu.edu/all_datasets/48>

<span data-ttu-id="2354e-176">SDNET2018 je datová sada obrázků, která obsahuje poznámky pro neprasklé a neprasklé konkrétní struktury (balíčky mostů, stěny a Pavement).</span><span class="sxs-lookup"><span data-stu-id="2354e-176">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Ukázky balíčku pro přemostění datových sad SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="2354e-178">Data jsou uspořádaná ve třech podadresářích:</span><span class="sxs-lookup"><span data-stu-id="2354e-178">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="2354e-179">D obsahuje obrázky na balíčku mostu.</span><span class="sxs-lookup"><span data-stu-id="2354e-179">D contains bridge deck images</span></span>
- <span data-ttu-id="2354e-180">P obsahuje image Pavement</span><span class="sxs-lookup"><span data-stu-id="2354e-180">P contains pavement images</span></span>
- <span data-ttu-id="2354e-181">W obsahuje obrázky na zdi</span><span class="sxs-lookup"><span data-stu-id="2354e-181">W contains wall images</span></span>

<span data-ttu-id="2354e-182">Každý z těchto podadresářů obsahuje dva další předem opravené podadresáře:</span><span class="sxs-lookup"><span data-stu-id="2354e-182">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="2354e-183">C je předpona používaná pro prasklé povrchy</span><span class="sxs-lookup"><span data-stu-id="2354e-183">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="2354e-184">U je předpona používaná pro prolomené povrchy.</span><span class="sxs-lookup"><span data-stu-id="2354e-184">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="2354e-185">V tomto kurzu se používají jenom balíčky balíčku mostu.</span><span class="sxs-lookup"><span data-stu-id="2354e-185">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="2354e-186">Stáhněte si [datovou sadu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="2354e-186">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="2354e-187">Vytvořte ve svém projektu adresář s názvem "assety" a uložte soubory DataSet.</span><span class="sxs-lookup"><span data-stu-id="2354e-187">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="2354e-188">Zkopírujte podadresáře *CD* a *ud* z naposledy nekomprimovaného adresáře do adresáře *assety* .</span><span class="sxs-lookup"><span data-stu-id="2354e-188">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="2354e-189">Vytvoření vstupní a výstupní třídy</span><span class="sxs-lookup"><span data-stu-id="2354e-189">Create input and output classes</span></span>

1. <span data-ttu-id="2354e-190">Otevřete soubor *program.cs* a nahraďte existující `using` příkazy v horní části souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2354e-190">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="2354e-191">Pod `Program` třídou v *program.cs*vytvořte třídu s názvem `ImageData` .</span><span class="sxs-lookup"><span data-stu-id="2354e-191">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="2354e-192">Tato třída slouží k reprezentaci počátečních načtených dat.</span><span class="sxs-lookup"><span data-stu-id="2354e-192">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="2354e-193">`ImageData`obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2354e-193">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="2354e-194">`ImagePath`je plně kvalifikovaná cesta, kde je obrázek uložený.</span><span class="sxs-lookup"><span data-stu-id="2354e-194">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="2354e-195">`Label`je kategorie, do které patří obrázek.</span><span class="sxs-lookup"><span data-stu-id="2354e-195">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="2354e-196">Toto je hodnota, která se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2354e-196">This is the value to predict.</span></span>

1. <span data-ttu-id="2354e-197">Vytváření tříd pro vstupní a výstupní data</span><span class="sxs-lookup"><span data-stu-id="2354e-197">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="2354e-198">Pod `ImageData` třídou definujte schéma vstupních dat v nové třídě s názvem `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="2354e-198">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="2354e-199">`ModelInput`obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2354e-199">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="2354e-200">`Image`je `byte[]` reprezentace obrázku.</span><span class="sxs-lookup"><span data-stu-id="2354e-200">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="2354e-201">Model očekává, že budou data obrázku tohoto typu pro účely školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-201">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="2354e-202">`LabelAsKey`je numerická reprezentace `Label` .</span><span class="sxs-lookup"><span data-stu-id="2354e-202">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="2354e-203">`ImagePath`je plně kvalifikovaná cesta, kde je obrázek uložený.</span><span class="sxs-lookup"><span data-stu-id="2354e-203">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="2354e-204">`Label`je kategorie, do které patří obrázek.</span><span class="sxs-lookup"><span data-stu-id="2354e-204">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="2354e-205">Toto je hodnota, která se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2354e-205">This is the value to predict.</span></span>

        <span data-ttu-id="2354e-206">Jenom `Image` a `LabelAsKey` se používají ke výukě modelu a k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2354e-206">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="2354e-207">`ImagePath`Vlastnosti a `Label` jsou udržovány pro usnadnění přístupu k původnímu názvu a kategorii souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="2354e-207">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="2354e-208">Pak pod `ModelInput` třídou definujte schéma výstupních dat v nové třídě s názvem `ModelOutput` .</span><span class="sxs-lookup"><span data-stu-id="2354e-208">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="2354e-209">`ModelOutput`obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2354e-209">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="2354e-210">`ImagePath`je plně kvalifikovaná cesta, kde je obrázek uložený.</span><span class="sxs-lookup"><span data-stu-id="2354e-210">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="2354e-211">`Label`je původní kategorie, do které patří obrázek.</span><span class="sxs-lookup"><span data-stu-id="2354e-211">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="2354e-212">Toto je hodnota, která se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="2354e-212">This is the value to predict.</span></span>
        - <span data-ttu-id="2354e-213">`PredictedLabel`je hodnota předpokládaná modelem.</span><span class="sxs-lookup"><span data-stu-id="2354e-213">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="2354e-214">Podobně jako se `ModelInput` vyžaduje, `PredictedLabel` aby předpovědi, protože obsahuje předpovědi vytvořenou modelem, je nutné provést pouze příkaz.</span><span class="sxs-lookup"><span data-stu-id="2354e-214">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="2354e-215">`ImagePath`Vlastnosti a `Label` jsou zachovány pro usnadnění přístupu k původnímu názvu a kategorii souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="2354e-215">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="2354e-216">Vytvořit adresář pracovního prostoru</span><span class="sxs-lookup"><span data-stu-id="2354e-216">Create workspace directory</span></span>

<span data-ttu-id="2354e-217">Když se data o školení a ověřování často nemění, je vhodné při dalších spuštěních ukládat do mezipaměti vypočtené kritické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2354e-217">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="2354e-218">V projektu vytvořte nový adresář s názvem *pracovní prostor* , ve kterém budou uloženy vypočítané kritické hodnoty a `.pb` verze modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-218">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="2354e-219">Definování cest a inicializovat proměnné</span><span class="sxs-lookup"><span data-stu-id="2354e-219">Define paths and initialize variables</span></span>

1. <span data-ttu-id="2354e-220">V rámci `Main` metody definujte umístění vašich assetů, vypočtených kritických hodnot a `.pb` verze modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-220">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="2354e-221">Inicializujte `mlContext` proměnnou novou instancí třídy [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="2354e-221">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="2354e-222">Třída [MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje MLContext vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu pro vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="2354e-222">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2354e-223">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2354e-223">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2354e-224">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="2354e-224">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="2354e-225">Metoda vytvoření nástroje pro načítání dat</span><span class="sxs-lookup"><span data-stu-id="2354e-225">Create data loading utility method</span></span>

<span data-ttu-id="2354e-226">Bitové kopie jsou uloženy ve dvou podadresářích.</span><span class="sxs-lookup"><span data-stu-id="2354e-226">The images are stored in two subdirectories.</span></span> <span data-ttu-id="2354e-227">Před načtením dat je třeba ji naformátovat na seznam `ImageData` objektů.</span><span class="sxs-lookup"><span data-stu-id="2354e-227">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="2354e-228">Uděláte to tak, že vytvoříte `LoadImagesFromDirectory` metodu pod `Main` metodou.</span><span class="sxs-lookup"><span data-stu-id="2354e-228">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="2354e-229">V rámci `LoadImagesDirectory` Přidat následující kód pro získání všech cest k souborům z podadresářů:</span><span class="sxs-lookup"><span data-stu-id="2354e-229">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="2354e-230">Pak Iterujte každý ze souborů pomocí `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2354e-230">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="2354e-231">V rámci `foreach` příkazu ověřte, zda jsou přípony souborů podporovány.</span><span class="sxs-lookup"><span data-stu-id="2354e-231">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="2354e-232">Rozhraní API klasifikace obrázků podporuje formáty JPEG a PNG.</span><span class="sxs-lookup"><span data-stu-id="2354e-232">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="2354e-233">Pak Získejte popisek pro soubor.</span><span class="sxs-lookup"><span data-stu-id="2354e-233">Then, get the label for the file.</span></span> <span data-ttu-id="2354e-234">Pokud `useFolderNameAsLabel` je parametr nastaven na hodnotu `true` , pak je jako popisek použit nadřazený adresář, kde je soubor uložen.</span><span class="sxs-lookup"><span data-stu-id="2354e-234">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="2354e-235">V opačném případě očekává, že popisek bude prefixem názvu souboru nebo samotného názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="2354e-235">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="2354e-236">Nakonec vytvořte novou instanci `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="2354e-236">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="2354e-237">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="2354e-237">Prepare the data</span></span>

1. <span data-ttu-id="2354e-238">Zpátky v `Main` metodě použijte `LoadFromDirectory` metodu Utility k získání seznamu imagí použitých pro školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-238">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="2354e-239">Pak načtěte obrázky do objektu [`IDataView`](xref:Microsoft.ML.IDataView) pomocí [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody.</span><span class="sxs-lookup"><span data-stu-id="2354e-239">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="2354e-240">Data se načítají v pořadí, v jakém byla načtena z adresářů.</span><span class="sxs-lookup"><span data-stu-id="2354e-240">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="2354e-241">Chcete-li vyrovnávat data, přemístěte je pomocí [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) metody.</span><span class="sxs-lookup"><span data-stu-id="2354e-241">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="2354e-242">Modely strojového učení očekávají, že vstup bude v číselném formátu.</span><span class="sxs-lookup"><span data-stu-id="2354e-242">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="2354e-243">Proto je nutné před školením provést některé předzpracování dat.</span><span class="sxs-lookup"><span data-stu-id="2354e-243">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="2354e-244">Vytvořte vytvořit [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) z [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` transformací a.</span><span class="sxs-lookup"><span data-stu-id="2354e-244">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="2354e-245">`MapValueToKey`Transformace přebírá hodnotu kategorií ve `Label` sloupci, převádí ji na číselnou `KeyType` hodnotu a ukládá ji do nového sloupce s názvem `LabelAsKey` .</span><span class="sxs-lookup"><span data-stu-id="2354e-245">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="2354e-246">`LoadImages`Převezme hodnoty ze `ImagePath` sloupce spolu s `imageFolder` parametrem pro načtení imagí pro školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-246">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="2354e-247">Použijte [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metodu pro použití dat na `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) následovaný [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) metodou, která vrátí [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předem zpracovaná data.</span><span class="sxs-lookup"><span data-stu-id="2354e-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="2354e-248">Pro výuku modelu je důležité, abyste měli školicí datovou sadu i ověřovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="2354e-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="2354e-249">Model je vyškolený v sadě školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-249">The model is trained on the training set.</span></span> <span data-ttu-id="2354e-250">Jak dobře je předpovědi na nezpracovaných datech, je měřeno výkonem proti sadě ověřování.</span><span class="sxs-lookup"><span data-stu-id="2354e-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="2354e-251">V závislosti na výsledcích tohoto výkonu model provádí úpravy podle toho, co se naučilo ve snaze zlepšit.</span><span class="sxs-lookup"><span data-stu-id="2354e-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="2354e-252">Sada ověření může pocházet z rozdělení původní datové sady nebo z jiného zdroje, který již byl pro tento účel vyhrazen.</span><span class="sxs-lookup"><span data-stu-id="2354e-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="2354e-253">V tomto případě je předem zpracovaná datová sada rozdělena do školicích, ověřovacích a testovacích sad.</span><span class="sxs-lookup"><span data-stu-id="2354e-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="2354e-254">Výše uvedený vzor kódu provádí dvě rozdělení.</span><span class="sxs-lookup"><span data-stu-id="2354e-254">The code sample above performs two splits.</span></span> <span data-ttu-id="2354e-255">Předem zpracovaná data jsou nejprve rozdělena a 70% se používá pro školení, zatímco se k ověřování používá zbývajících 30%.</span><span class="sxs-lookup"><span data-stu-id="2354e-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="2354e-256">Potom je 30% ověřovací sada dále rozdělena na ověřování a sady testů, kde se pro ověřování používá 90% a pro testování se používá 10%.</span><span class="sxs-lookup"><span data-stu-id="2354e-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="2354e-257">Způsob, jak se zamyslet na účel těchto datových oddílů, je provedení zkoušky.</span><span class="sxs-lookup"><span data-stu-id="2354e-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="2354e-258">Při studiu pro zkoušku si Projděte poznámky, knihy nebo jiné prostředky, abyste získali informace o konceptech, které se na této zkoušce nacházejí.</span><span class="sxs-lookup"><span data-stu-id="2354e-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="2354e-259">To je to, pro který je vlaková sada.</span><span class="sxs-lookup"><span data-stu-id="2354e-259">This is what the train set is for.</span></span> <span data-ttu-id="2354e-260">Pak můžete pořizovat napodobnou zkoušku k ověření vašeho vědomí.</span><span class="sxs-lookup"><span data-stu-id="2354e-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="2354e-261">Tady se objeví ověřovací sada.</span><span class="sxs-lookup"><span data-stu-id="2354e-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="2354e-262">Chcete před provedením samotné zkoušky ověřit, zda máte dobré pojetí konceptů.</span><span class="sxs-lookup"><span data-stu-id="2354e-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="2354e-263">Na základě těchto výsledků si poznamenejte, co se vám nepovedlo nebo nerozumělo, a zahrňte své změny do kontroly skutečné zkoušky.</span><span class="sxs-lookup"><span data-stu-id="2354e-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="2354e-264">Nakonec můžete provést zkoušku.</span><span class="sxs-lookup"><span data-stu-id="2354e-264">Finally, you take the exam.</span></span> <span data-ttu-id="2354e-265">To je to, co je testovací sada používána pro.</span><span class="sxs-lookup"><span data-stu-id="2354e-265">This is what the test set is used for.</span></span> <span data-ttu-id="2354e-266">Nikdy jste neviděli otázky, které se týkají zkoušky, a teď pomocí toho, co jste se naučili při školení a ověřování, abyste mohli vaše znalosti na úkol použít.</span><span class="sxs-lookup"><span data-stu-id="2354e-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="2354e-267">Přiřaďte oddíly jejich příslušné hodnoty pro data vlaku, ověřování a testování.</span><span class="sxs-lookup"><span data-stu-id="2354e-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="2354e-268">Definování školicího kanálu</span><span class="sxs-lookup"><span data-stu-id="2354e-268">Define the training pipeline</span></span>

<span data-ttu-id="2354e-269">Školení modelů se skládá z několika kroků.</span><span class="sxs-lookup"><span data-stu-id="2354e-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="2354e-270">Rozhraní API pro klasifikaci imagí slouží jako první, používá se k učení modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="2354e-271">Zakódované popisky ve `PredictedLabel` sloupci pak budou převedeny zpátky na původní hodnotu kategorií pomocí `MapKeyToValue` transformace.</span><span class="sxs-lookup"><span data-stu-id="2354e-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="2354e-272">Vytvořte novou proměnnou pro uložení sady požadovaných a volitelných parametrů pro `ImageClassificationTrainer` .</span><span class="sxs-lookup"><span data-stu-id="2354e-272">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="2354e-273">A `ImageClassificationTrainer` trvá několik volitelných parametrů:</span><span class="sxs-lookup"><span data-stu-id="2354e-273">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="2354e-274">`FeatureColumnName`je sloupec, který se používá jako vstup pro model.</span><span class="sxs-lookup"><span data-stu-id="2354e-274">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="2354e-275">`LabelColumnName`je sloupec, jehož hodnota má být předpovězena.</span><span class="sxs-lookup"><span data-stu-id="2354e-275">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="2354e-276">`ValidationSet`je [`IDataView`](xref:Microsoft.ML.IDataView) obsahující ověřovací data.</span><span class="sxs-lookup"><span data-stu-id="2354e-276">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="2354e-277">`Arch`definuje, které z předdefinovaných architektur modelů se mají použít.</span><span class="sxs-lookup"><span data-stu-id="2354e-277">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="2354e-278">V tomto kurzu použijeme 101 variant modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="2354e-278">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="2354e-279">`MetricsCallback`váže funkci, aby sledovala průběh během školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-279">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="2354e-280">`TestOnTrainSet`instruuje model, aby měřil výkon proti školicí sadě, když není k dispozici žádná sada ověření.</span><span class="sxs-lookup"><span data-stu-id="2354e-280">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="2354e-281">`ReuseTrainSetBottleneckCachedValues`Určuje, zda se mají v následných fázích použít hodnoty uložené v mezipaměti z fáze kritického bodu.</span><span class="sxs-lookup"><span data-stu-id="2354e-281">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="2354e-282">Kritická fáze je jednorázové výpočtu předávacího přenosu, který je výpočetně náročný při prvním provedení.</span><span class="sxs-lookup"><span data-stu-id="2354e-282">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="2354e-283">Pokud se školicí data nezmění a chcete experimentovat s jiným počtem epochs nebo dávky, použití hodnot uložených v mezipaměti významně zkracuje dobu potřebnou k výuce modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-283">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="2354e-284">`ReuseValidationSetBottleneckCachedValues`je podobný `ReuseTrainSetBottleneckCachedValues` pouze v případě, že v tomto případě je pro datovou sadu ověřování.</span><span class="sxs-lookup"><span data-stu-id="2354e-284">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="2354e-285">`WorkspacePath`Definuje adresář, kam se mají ukládat vypočtené hodnoty kritických bodů a `.pb` verze modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-285">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="2354e-286">Definujte [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) školicí kanál, který se skládá z `mapLabelEstimator` a `ImageClassificationTrainer` .</span><span class="sxs-lookup"><span data-stu-id="2354e-286">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="2354e-287">Použijte [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metodu pro výuku modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-287">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="2354e-288">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="2354e-288">Use the model</span></span>

<span data-ttu-id="2354e-289">Teď, když jste si proškole svůj model, je čas ho použít ke klasifikaci imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-289">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="2354e-290">Pod `Main` metodou vytvořte novou metodu, která je volána `OutputPrediction` pro zobrazení informací o předpovědi v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="2354e-290">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="2354e-291">Klasifikace jednoho obrázku</span><span class="sxs-lookup"><span data-stu-id="2354e-291">Classify a single image</span></span>

1. <span data-ttu-id="2354e-292">Přidejte novou metodu nazvanou `ClassifySingleImage` pod `Main` metodu pro vytvoření a výstup jedné předpovědi imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-292">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="2354e-293">Vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uvnitř `ClassifySingleImage` metody.</span><span class="sxs-lookup"><span data-stu-id="2354e-293">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="2354e-294">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Je praktické rozhraní API, které umožňuje předat a potom provést předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="2354e-294">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="2354e-295">Chcete-li získat přístup k jediné `ModelInput` instanci, proveďte převod na `data` [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody a poté Získejte první sledování.</span><span class="sxs-lookup"><span data-stu-id="2354e-295">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="2354e-296">[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*)K klasifikaci obrázku použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="2354e-296">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="2354e-297">Výstup předpovědi do konzoly s `OutputPrediction` metodou.</span><span class="sxs-lookup"><span data-stu-id="2354e-297">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="2354e-298">Uvnitř `Main` metody zavolejte `ClassifySingleImage` pomocí testovací sady imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-298">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="2354e-299">Klasifikace více imagí</span><span class="sxs-lookup"><span data-stu-id="2354e-299">Classify multiple images</span></span>

1. <span data-ttu-id="2354e-300">Přidejte novou metodu nazvanou `ClassifyImages` pod `ClassifySingleImage` metodu pro vytvoření a výstup více předpovědi obrázků.</span><span class="sxs-lookup"><span data-stu-id="2354e-300">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="2354e-301">Vytvořte objekt [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předpovědi pomocí [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody.</span><span class="sxs-lookup"><span data-stu-id="2354e-301">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="2354e-302">Do metody přidejte následující kód `ClassifyImages` .</span><span class="sxs-lookup"><span data-stu-id="2354e-302">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="2354e-303">Chcete-li iterovat přes předpovědi, převeďte na `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metodu pomocí metody a pak Získejte prvních 10 pozorování.</span><span class="sxs-lookup"><span data-stu-id="2354e-303">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="2354e-304">Iterujte a navýstupujte původní a předpovězené popisky pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2354e-304">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="2354e-305">Nakonec v rámci `Main` metody zavolejte `ClassifyImages` pomocí testovací sady imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-305">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="2354e-306">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2354e-306">Run the application</span></span>

<span data-ttu-id="2354e-307">Spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2354e-307">Run your console app.</span></span> <span data-ttu-id="2354e-308">Výstup by měl vypadat podobně jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2354e-308">The output should be similar to that below.</span></span> <span data-ttu-id="2354e-309">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="2354e-309">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="2354e-310">V případě zkrácení byl výstup zúžený.</span><span class="sxs-lookup"><span data-stu-id="2354e-310">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="2354e-311">**Fáze kritického bodu**</span><span class="sxs-lookup"><span data-stu-id="2354e-311">**Bottleneck phase**</span></span>

<span data-ttu-id="2354e-312">Pro název Image se nevytiskne žádná hodnota, protože image se načítají, `byte[]` takže není k dispozici žádný název Image k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2354e-312">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="2354e-313">**Fáze školení**</span><span class="sxs-lookup"><span data-stu-id="2354e-313">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="2354e-314">**Klasifikovat výstup imagí**</span><span class="sxs-lookup"><span data-stu-id="2354e-314">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="2354e-315">Po kontrole obrázku *7001 -220. jpg* vidíte, že ve skutečnosti není prasklý.</span><span class="sxs-lookup"><span data-stu-id="2354e-315">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Obrázek datové sady SDNET2018 použité pro předpověď](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="2354e-317">Gratulujeme!</span><span class="sxs-lookup"><span data-stu-id="2354e-317">Congratulations!</span></span> <span data-ttu-id="2354e-318">Teď jste úspěšně vytvořili model hloubkového učení pro klasifikaci imagí.</span><span class="sxs-lookup"><span data-stu-id="2354e-318">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="2354e-319">Zlepšení modelu</span><span class="sxs-lookup"><span data-stu-id="2354e-319">Improve the model</span></span>

<span data-ttu-id="2354e-320">Pokud nejste spokojeni s výsledky modelu, můžete se pokusit zvýšit jeho výkon tak, že zkusíte některé z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="2354e-320">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="2354e-321">**Další data**: Další příklady, ze kterých se model učí, je lepší.</span><span class="sxs-lookup"><span data-stu-id="2354e-321">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="2354e-322">Stáhněte si úplnou [datovou sadu SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) a využijte ji ke školení.</span><span class="sxs-lookup"><span data-stu-id="2354e-322">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="2354e-323">**Rozšíření dat**: běžnou technikou pro přidání různých druhů dat je rozšíření dat pomocí obrázku a použití různých transformací (otočení, překlopení, posunutí a oříznutí).</span><span class="sxs-lookup"><span data-stu-id="2354e-323">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="2354e-324">Tím se přidá více různých příkladů modelu, ze kterého se naučíte.</span><span class="sxs-lookup"><span data-stu-id="2354e-324">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="2354e-325">**Školení pro delší dobu**: čím delší je, tím bude model lépe vyladěný.</span><span class="sxs-lookup"><span data-stu-id="2354e-325">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="2354e-326">Zvýšení počtu epochs může zlepšit výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="2354e-326">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="2354e-327">**Experiment s parametrem Hyper-Parameters**: Kromě parametrů používaných v tomto kurzu můžete další parametry vyladit tak, aby potenciálně vylepšily výkon.</span><span class="sxs-lookup"><span data-stu-id="2354e-327">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="2354e-328">Změna studijní frekvence, která určuje velikost aktualizací v modelu po každém epocha, může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="2354e-328">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="2354e-329">**Použití jiné architektury modelů**: v závislosti na tom, jak vaše data vypadají, se může model, který se nejlépe učí jeho funkcí, lišit.</span><span class="sxs-lookup"><span data-stu-id="2354e-329">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="2354e-330">Pokud nejste spokojeni s výkonem modelu, zkuste změnit architekturu.</span><span class="sxs-lookup"><span data-stu-id="2354e-330">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2354e-331">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2354e-331">Additional Resources</span></span>

- <span data-ttu-id="2354e-332">[Obsáhlý Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="2354e-332">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2354e-333">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2354e-333">Next steps</span></span>

<span data-ttu-id="2354e-334">V tomto kurzu jste zjistili, jak vytvořit vlastní model hloubkového učení s využitím učení přenosu, předTensorFlowho modelu klasifikace imagí a rozhraní API pro klasifikaci ml.NET pro klasifikaci imagí konkrétních povrchů jako prasklé nebo prolomené.</span><span class="sxs-lookup"><span data-stu-id="2354e-334">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="2354e-335">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="2354e-335">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2354e-336">Detekce objektu</span><span class="sxs-lookup"><span data-stu-id="2354e-336">Object Detection</span></span>](object-detection-onnx.md)
