---
title: 'Kurz: automatizované vizuální prověřování pomocí učení přenosu'
description: V tomto kurzu se dozvíte, jak pomocí funkce Transfer Learning vytvořit TensorFlow model hloubkového učení v ML.NET pomocí rozhraní API pro detekci imagí pro klasifikaci imagí konkrétních ploch jako prasklé nebo neprasklé.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961985"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="68c5d-103">Kurz: automatizované vizuální prověřování pomocí přenosu přenosu s rozhraním API pro klasifikaci imagí ML.NET</span><span class="sxs-lookup"><span data-stu-id="68c5d-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="68c5d-104">Naučte se naučit vlastní model hloubkového učení s využitím učení přenosu, předTensorFlowho modelu a rozhraní API pro klasifikaci imagí ml.NET pro klasifikaci imagí konkrétních povrchů jako prasklé nebo prolomené.</span><span class="sxs-lookup"><span data-stu-id="68c5d-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

> [!NOTE]
> <span data-ttu-id="68c5d-105">V tomto kurzu se používá verze Preview rozhraní ML.NET API pro klasifikaci imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-105">This tutorial uses a preview version of the ML.NET Image Classification API.</span></span>

<span data-ttu-id="68c5d-106">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="68c5d-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="68c5d-107">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="68c5d-107">Understand the problem</span></span>
> - <span data-ttu-id="68c5d-108">Další informace o rozhraní API pro klasifikaci imagí ML.NET</span><span class="sxs-lookup"><span data-stu-id="68c5d-108">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="68c5d-109">Pochopení předvýukového modelu</span><span class="sxs-lookup"><span data-stu-id="68c5d-109">Understand the pretrained model</span></span>
> - <span data-ttu-id="68c5d-110">Použití učení transferu k výuce vlastního modelu klasifikace imagí TensorFlow</span><span class="sxs-lookup"><span data-stu-id="68c5d-110">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="68c5d-111">Klasifikace imagí pomocí vlastního modelu</span><span class="sxs-lookup"><span data-stu-id="68c5d-111">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68c5d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68c5d-112">Prerequisites</span></span>

- <span data-ttu-id="68c5d-113">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="68c5d-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="68c5d-114">Přehled výukového kurzu přenosu klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="68c5d-114">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="68c5d-115">Tato ukázka je Konzolová aplikace C# .NET Core, která klasifikuje Image pomocí předvýukového modelu TensorFlow hloubkového učení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-115">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="68c5d-116">Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-116">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="68c5d-117">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="68c5d-117">Understand the problem</span></span>

<span data-ttu-id="68c5d-118">Klasifikace obrázku je problém počítačové vize.</span><span class="sxs-lookup"><span data-stu-id="68c5d-118">Image classification is a computer vision problem.</span></span> <span data-ttu-id="68c5d-119">Klasifikace obrázku bere jako vstup obrázek a zařadí ho do předepsané třídy.</span><span class="sxs-lookup"><span data-stu-id="68c5d-119">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="68c5d-120">Některé scénáře, kde je klasifikace obrázku užitečná, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="68c5d-120">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="68c5d-121">Rozpoznávání obličeje</span><span class="sxs-lookup"><span data-stu-id="68c5d-121">Facial recognition</span></span>
- <span data-ttu-id="68c5d-122">Detekce emoce</span><span class="sxs-lookup"><span data-stu-id="68c5d-122">Emotion detection</span></span>
- <span data-ttu-id="68c5d-123">Lékařské diagnostiky</span><span class="sxs-lookup"><span data-stu-id="68c5d-123">Medical diagnosis</span></span>
- <span data-ttu-id="68c5d-124">Detekce orientačních bodů</span><span class="sxs-lookup"><span data-stu-id="68c5d-124">Landmark detection</span></span>

<span data-ttu-id="68c5d-125">V tomto kurzu se nasazuje model klasifikace vlastních imagí, který provede automatizovanou vizuální kontrolu balíčku mostu a identifikuje tak struktury, které jsou poškozené prasklinami.</span><span class="sxs-lookup"><span data-stu-id="68c5d-125">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="68c5d-126">Rozhraní API pro klasifikaci imagí ML.NET</span><span class="sxs-lookup"><span data-stu-id="68c5d-126">ML.NET Image Classification API</span></span>

<span data-ttu-id="68c5d-127">ML.NET poskytuje různé způsoby provádění klasifikace imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-127">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="68c5d-128">Tento kurz se týká učení přenosu pomocí rozhraní API klasifikace imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-128">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="68c5d-129">Rozhraní API pro klasifikaci imagí využívá [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)knihovnu nižší úrovně, která poskytuje C# vazby pro rozhraní TensorFlow C++ API.</span><span class="sxs-lookup"><span data-stu-id="68c5d-129">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="68c5d-130">Co je učení přenosu?</span><span class="sxs-lookup"><span data-stu-id="68c5d-130">What is transfer learning?</span></span>

<span data-ttu-id="68c5d-131">Učení pro přenos používá znalostní bázi získaná od řešení jednoho problému s jiným souvisejícím problémem.</span><span class="sxs-lookup"><span data-stu-id="68c5d-131">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="68c5d-132">Školení modelu hloubkového učení od začátku vyžaduje nastavení několika parametrů, velkého množství podrobných školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="68c5d-132">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="68c5d-133">Použití předzpracovaného modelu spolu s učením přenosu vám umožní zástupce školicího procesu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-133">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span> 

## <a name="training-process"></a><span data-ttu-id="68c5d-134">Školicí proces</span><span class="sxs-lookup"><span data-stu-id="68c5d-134">Training process</span></span>

<span data-ttu-id="68c5d-135">Rozhraní API klasifikace imagí spustí školicí proces načtením předinstalovaného modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="68c5d-135">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="68c5d-136">Školicí proces se skládá ze dvou kroků:</span><span class="sxs-lookup"><span data-stu-id="68c5d-136">The training process consists of two steps:</span></span>

1. <span data-ttu-id="68c5d-137">Fáze kritického bodu</span><span class="sxs-lookup"><span data-stu-id="68c5d-137">Bottleneck phase</span></span>
2. <span data-ttu-id="68c5d-138">Fáze školení</span><span class="sxs-lookup"><span data-stu-id="68c5d-138">Training phase</span></span>

![Postup školení](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="68c5d-140">Fáze kritického bodu</span><span class="sxs-lookup"><span data-stu-id="68c5d-140">Bottleneck phase</span></span>

<span data-ttu-id="68c5d-141">Během fáze kritických míst se načte sada školicích imagí a jako vstup a funkce se použijí pixelové hodnoty pro zmrazené vrstvy předinstalovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-141">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="68c5d-142">Zmrazené vrstvy zahrnují všechny vrstvy v neuronové síti až do poslední vrstvy, která je Poznáma jako kritická vrstva.</span><span class="sxs-lookup"><span data-stu-id="68c5d-142">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="68c5d-143">Tyto vrstvy se označují jako zmrazené, protože na těchto vrstvách a operacích neproběhne žádné školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-143">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="68c5d-144">Je v těchto zmrazených vrstvách, kde jsou vypočítány vzory nižší úrovně, které usnadňují model odlišení různých tříd.</span><span class="sxs-lookup"><span data-stu-id="68c5d-144">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="68c5d-145">Čím větší je počet vrstev, tím více výpočetně náročné je tento krok.</span><span class="sxs-lookup"><span data-stu-id="68c5d-145">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="68c5d-146">Naštěstí, protože se jedná o jednorázový výpočet, mohou být výsledky uloženy do mezipaměti a použity v pozdějších spuštěních při experimentování s různými parametry.</span><span class="sxs-lookup"><span data-stu-id="68c5d-146">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="68c5d-147">Fáze školení</span><span class="sxs-lookup"><span data-stu-id="68c5d-147">Training phase</span></span>

<span data-ttu-id="68c5d-148">Až budou výstupní hodnoty z kritické fáze vypočítány, používají se jako vstup k přeškolování finální vrstvy modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-148">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="68c5d-149">Tento proces je iterativní a spouští se v počtu pokusů určených parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-149">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="68c5d-150">Během každého spuštění jsou vyhodnocovány ztráty a přesnost.</span><span class="sxs-lookup"><span data-stu-id="68c5d-150">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="68c5d-151">Pak jsou provedeny příslušné úpravy pro zlepšení modelu s cílem minimalizovat ztrátu a maximalizovat přesnost.</span><span class="sxs-lookup"><span data-stu-id="68c5d-151">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="68c5d-152">Po dokončení školení jsou výstupem dva formáty modelů.</span><span class="sxs-lookup"><span data-stu-id="68c5d-152">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="68c5d-153">Jednou z nich je `.pb` verze modelu a druhá je serializovaná verze modelu `.zip` ML.NET.</span><span class="sxs-lookup"><span data-stu-id="68c5d-153">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="68c5d-154">Při práci v prostředích podporovaných aplikací ML.NET se doporučuje použít verzi modelu `.zip`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-154">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="68c5d-155">V prostředích, kde ML.NET není podporovaný, máte ale možnost použít verzi `.pb`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-155">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="68c5d-156">Pochopení předvýukového modelu</span><span class="sxs-lookup"><span data-stu-id="68c5d-156">Understand the pretrained model</span></span>

<span data-ttu-id="68c5d-157">Předem vydaný model použitý v tomto kurzu je 101 varianta modelu zbytkové sítě (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="68c5d-157">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="68c5d-158">Původní model je vyškolen pro klasifikaci imagí do tisíc kategorií.</span><span class="sxs-lookup"><span data-stu-id="68c5d-158">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="68c5d-159">Model bere jako vstup obrázek o velikosti 224 × 224 a vypisuje pravděpodobnosti třídy pro každou třídu, na které je technologie IT vyškolená.</span><span class="sxs-lookup"><span data-stu-id="68c5d-159">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="68c5d-160">Součástí tohoto modelu je vyučování nového modelu pomocí vlastních imagí, aby bylo možné předpovědi mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="68c5d-160">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span> 

## <a name="create-console-application"></a><span data-ttu-id="68c5d-161">Vytvořit konzolovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="68c5d-161">Create console application</span></span>

<span data-ttu-id="68c5d-162">Teď, když máte obecné znalosti o učení přenosů a rozhraní API klasifikace imagí, je čas sestavování aplikace.</span><span class="sxs-lookup"><span data-stu-id="68c5d-162">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="68c5d-163">Vytvořte  **C# konzolovou aplikaci .NET Core** nazvanou "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="68c5d-163">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="68c5d-164">Nainstalujte balíček NuGet **Microsoft.ml 1.4.0-preview2** :</span><span class="sxs-lookup"><span data-stu-id="68c5d-164">Install the **Microsoft.ML 1.4.0-preview2** NuGet Package:</span></span>
    1. <span data-ttu-id="68c5d-165">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="68c5d-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="68c5d-166">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="68c5d-166">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="68c5d-167">Vyberte kartu **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="68c5d-167">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="68c5d-168">Zaškrtněte políčko **zahrnout předběžné verze** .</span><span class="sxs-lookup"><span data-stu-id="68c5d-168">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="68c5d-169">Vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="68c5d-169">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="68c5d-170">Vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="68c5d-170">Select the **Install** button.</span></span>
    1. <span data-ttu-id="68c5d-171">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="68c5d-171">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="68c5d-172">Opakujte tyto kroky pro **Microsoft. ml. DNN 0.16.0-preview2** a **Microsoft. ml. ImageAnalytics 1.4.0-preview2**.</span><span class="sxs-lookup"><span data-stu-id="68c5d-172">Repeat these steps for **Microsoft.ML.Dnn 0.16.0-preview2** and **Microsoft.ML.ImageAnalytics 1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="68c5d-173">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="68c5d-173">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="68c5d-174">Datové sady pro tento kurz jsou z Maguire, matolin; Dorafshan, Sattar; a Tomáš, Robert J., "SDNET2018: konkrétní datová sada obrázku trhlin pro aplikace pro strojové učení" (2018).</span><span class="sxs-lookup"><span data-stu-id="68c5d-174">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="68c5d-175">Procházet všechny datové sady.</span><span class="sxs-lookup"><span data-stu-id="68c5d-175">Browse all Datasets.</span></span> <span data-ttu-id="68c5d-176">Papír 48.</span><span class="sxs-lookup"><span data-stu-id="68c5d-176">Paper 48.</span></span> <span data-ttu-id="68c5d-177">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="68c5d-177">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="68c5d-178">SDNET2018 je datová sada obrázků, která obsahuje poznámky pro neprasklé a neprasklé konkrétní struktury (balíčky mostů, stěny a Pavement).</span><span class="sxs-lookup"><span data-stu-id="68c5d-178">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span> 

![Ukázky balíčku pro přemostění datových sad SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="68c5d-180">Data jsou uspořádaná ve třech podadresářích:</span><span class="sxs-lookup"><span data-stu-id="68c5d-180">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="68c5d-181">D obsahuje obrázky na balíčku mostu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-181">D contains bridge deck images</span></span>
- <span data-ttu-id="68c5d-182">P obsahuje image Pavement</span><span class="sxs-lookup"><span data-stu-id="68c5d-182">P contains pavement images</span></span>
- <span data-ttu-id="68c5d-183">W obsahuje obrázky na zdi</span><span class="sxs-lookup"><span data-stu-id="68c5d-183">W contains wall images</span></span>

<span data-ttu-id="68c5d-184">Každý z těchto podadresářů obsahuje dva další předem opravené podadresáře:</span><span class="sxs-lookup"><span data-stu-id="68c5d-184">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="68c5d-185">C je předpona používaná pro prasklé povrchy</span><span class="sxs-lookup"><span data-stu-id="68c5d-185">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="68c5d-186">U je předpona používaná pro prolomené povrchy.</span><span class="sxs-lookup"><span data-stu-id="68c5d-186">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="68c5d-187">V tomto kurzu se používají jenom balíčky balíčku mostu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-187">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="68c5d-188">Stáhněte si [datovou sadu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="68c5d-188">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="68c5d-189">Vytvořte ve svém projektu adresář s názvem "assety" a uložte soubory DataSet.</span><span class="sxs-lookup"><span data-stu-id="68c5d-189">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="68c5d-190">Zkopírujte podadresáře *CD* a *ud* z naposledy nekomprimovaného adresáře do adresáře *assety* .</span><span class="sxs-lookup"><span data-stu-id="68c5d-190">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="68c5d-191">Vytvoření vstupní a výstupní třídy</span><span class="sxs-lookup"><span data-stu-id="68c5d-191">Create input and output classes</span></span>

1. <span data-ttu-id="68c5d-192">Otevřete soubor *program.cs* a nahraďte existující příkazy `using` v horní části souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="68c5d-192">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="68c5d-193">Pod třídou `Program` v *program.cs*vytvořte třídu s názvem `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-193">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="68c5d-194">Tato třída slouží k reprezentaci počátečních načtených dat.</span><span class="sxs-lookup"><span data-stu-id="68c5d-194">This class is used to represent the initially loaded data.</span></span> 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    <span data-ttu-id="68c5d-195">`ImageData` obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="68c5d-195">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="68c5d-196">`ImagePath` je plně kvalifikovaná cesta, kde je obrázek uložený.</span><span class="sxs-lookup"><span data-stu-id="68c5d-196">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="68c5d-197">`Label` je kategorie, do které patří obrázek.</span><span class="sxs-lookup"><span data-stu-id="68c5d-197">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="68c5d-198">Toto je hodnota, která se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="68c5d-198">This is the value to predict.</span></span>

1. <span data-ttu-id="68c5d-199">Vytváření tříd pro vstupní a výstupní data</span><span class="sxs-lookup"><span data-stu-id="68c5d-199">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="68c5d-200">Pod `ImageData` třídou definujte schéma vstupních dat v nové třídě s názvem `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-200">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        <span data-ttu-id="68c5d-201">`ModelInput` obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="68c5d-201">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="68c5d-202">`ImagePath` je plně kvalifikovaná cesta, kde je obrázek uložený.</span><span class="sxs-lookup"><span data-stu-id="68c5d-202">`ImagePath` is the fully qualified path where the image is stored.</span></span> 
        - <span data-ttu-id="68c5d-203">`Label` je kategorie, do které patří obrázek.</span><span class="sxs-lookup"><span data-stu-id="68c5d-203">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="68c5d-204">Toto je hodnota, která se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="68c5d-204">This is the value to predict.</span></span>
        - <span data-ttu-id="68c5d-205">`Image` je `byte[]` reprezentace obrázku.</span><span class="sxs-lookup"><span data-stu-id="68c5d-205">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="68c5d-206">Model očekává, že budou data obrázku tohoto typu pro účely školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-206">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="68c5d-207">`LabelAsKey` je numerická reprezentace `Label`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-207">`LabelAsKey` is the numerical representation of the `Label`.</span></span> 

        <span data-ttu-id="68c5d-208">Pro výuku modelu a předpovědi se používají jenom `Image` a `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-208">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="68c5d-209">Vlastnosti `ImagePath` a `Label` jsou pro usnadnění přístupu k původnímu názvu souboru bitové kopie a kategorii zachovány.</span><span class="sxs-lookup"><span data-stu-id="68c5d-209">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="68c5d-210">Pak pod `ModelInput` třídy definujte schéma výstupních dat v nové třídě s názvem `ModelOutput`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-210">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span> 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        <span data-ttu-id="68c5d-211">`ModelOutput` obsahuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="68c5d-211">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="68c5d-212">`ImagePath` je plně kvalifikovaná cesta, kde je obrázek uložený.</span><span class="sxs-lookup"><span data-stu-id="68c5d-212">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="68c5d-213">`Label` je původní kategorie, do které patří obrázek.</span><span class="sxs-lookup"><span data-stu-id="68c5d-213">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="68c5d-214">Toto je hodnota, která se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="68c5d-214">This is the value to predict.</span></span> 
        - <span data-ttu-id="68c5d-215">`PredictedLabel` je hodnota předpokládaná modelem.</span><span class="sxs-lookup"><span data-stu-id="68c5d-215">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="68c5d-216">Podobně jako u `ModelInput`se vyžaduje jenom `PredictedLabel` k předpovědi, protože obsahuje předpovědi vytvořenou modelem.</span><span class="sxs-lookup"><span data-stu-id="68c5d-216">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="68c5d-217">Vlastnosti `ImagePath` a `Label` jsou pro usnadnění přístupu k původnímu názvu souboru bitové kopie a kategorii zachovány.</span><span class="sxs-lookup"><span data-stu-id="68c5d-217">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="68c5d-218">Definování cest a inicializovat proměnné</span><span class="sxs-lookup"><span data-stu-id="68c5d-218">Define paths and initialize variables</span></span>

1. <span data-ttu-id="68c5d-219">V rámci metody `Main` definujte umístění vašich assetů.</span><span class="sxs-lookup"><span data-stu-id="68c5d-219">Inside the `Main` method, define the location of your assets.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. <span data-ttu-id="68c5d-220">Pak inicializujte `mlContext` proměnnou novou instancí třídy [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="68c5d-220">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

<span data-ttu-id="68c5d-221">Třída [MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje MLContext vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu pro vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="68c5d-221">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="68c5d-222">Je podobné, koncepčně, `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="68c5d-222">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="68c5d-223">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="68c5d-223">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="68c5d-224">Metoda vytvoření nástroje pro načítání dat</span><span class="sxs-lookup"><span data-stu-id="68c5d-224">Create data loading utility method</span></span>

<span data-ttu-id="68c5d-225">Bitové kopie jsou uloženy ve dvou podadresářích.</span><span class="sxs-lookup"><span data-stu-id="68c5d-225">The images are stored in two subdirectories.</span></span> <span data-ttu-id="68c5d-226">Před načtením dat je třeba ji naformátovat na seznam `ImageData` objektů.</span><span class="sxs-lookup"><span data-stu-id="68c5d-226">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="68c5d-227">Provedete to tak, že vytvoříte metodu `LoadImagesFromDirectory` pod metodou `Main`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-227">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="68c5d-228">Uvnitř `LoadImagesDirectory` přidejte následující kód pro získání všech cest k souborům z podadresářů:</span><span class="sxs-lookup"><span data-stu-id="68c5d-228">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. <span data-ttu-id="68c5d-229">Potom Iterujte každý ze souborů pomocí příkazu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-229">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="68c5d-230">V rámci příkazu `foreach` ověřte, zda jsou přípony souborů podporovány.</span><span class="sxs-lookup"><span data-stu-id="68c5d-230">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="68c5d-231">Rozhraní API klasifikace obrázků podporuje formáty JPEG a PNG.</span><span class="sxs-lookup"><span data-stu-id="68c5d-231">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. <span data-ttu-id="68c5d-232">Pak Získejte popisek pro soubor.</span><span class="sxs-lookup"><span data-stu-id="68c5d-232">Then, get the label for the file.</span></span> <span data-ttu-id="68c5d-233">Je-li parametr `useFolderNameAsLabel` nastaven na hodnotu `true`, bude jako popisek použit nadřazený adresář, kde je soubor uložen.</span><span class="sxs-lookup"><span data-stu-id="68c5d-233">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="68c5d-234">V opačném případě očekává, že popisek bude prefixem názvu souboru nebo samotného názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="68c5d-234">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. <span data-ttu-id="68c5d-235">Nakonec vytvořte novou instanci `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-235">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a><span data-ttu-id="68c5d-236">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="68c5d-236">Prepare the data</span></span>

1. <span data-ttu-id="68c5d-237">Zpět v metodě `Main` použijte metodu `LoadFromDirectory` Utility k získání seznamu imagí použitých pro školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-237">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. <span data-ttu-id="68c5d-238">Pak načtěte obrázky do [`IDataView`](xref:Microsoft.ML.IDataView) pomocí metody [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="68c5d-238">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. <span data-ttu-id="68c5d-239">Data se načítají v pořadí, v jakém byla načtena z adresářů.</span><span class="sxs-lookup"><span data-stu-id="68c5d-239">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="68c5d-240">Chcete-li vyrovnávat data, přemístěte je pomocí metody [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .</span><span class="sxs-lookup"><span data-stu-id="68c5d-240">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. <span data-ttu-id="68c5d-241">Modely strojového učení očekávají, že vstup bude v číselném formátu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-241">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="68c5d-242">Proto je nutné před školením provést některé předzpracování dat.</span><span class="sxs-lookup"><span data-stu-id="68c5d-242">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="68c5d-243">Vytvoří [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) tvořená [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) a [`LoadImages`mi](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transformacemi.</span><span class="sxs-lookup"><span data-stu-id="68c5d-243">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transforms.</span></span> <span data-ttu-id="68c5d-244">`MapValueToKey` transformace přebírá hodnotu kategorií ve sloupci `Label`, převede ji na číselnou `KeyType` hodnotu a uloží ji do nového sloupce s názvem `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-244">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="68c5d-245">`LoadImages` přebírá hodnoty z `ImagePath` sloupce spolu s parametrem `imageFolder` pro načtení imagí pro školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-245">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span> <span data-ttu-id="68c5d-246">Nastavení `useImageType` na `false` převede obrázky na `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-246">Setting the `useImageType` to `false` converts the images into a `byte[]`.</span></span> 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. <span data-ttu-id="68c5d-247">Použijte metodu [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) pro použití dat na `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) následovaný metodou [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , která vrací [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předem zpracovaná data.</span><span class="sxs-lookup"><span data-stu-id="68c5d-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="68c5d-248">Pro výuku modelu je důležité, abyste měli školicí datovou sadu i ověřovací datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="68c5d-249">Model je vyškolený v sadě školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-249">The model is trained on the training set.</span></span> <span data-ttu-id="68c5d-250">Jak dobře je předpovědi na nezpracovaných datech, je měřeno výkonem proti sadě ověřování.</span><span class="sxs-lookup"><span data-stu-id="68c5d-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="68c5d-251">V závislosti na výsledcích tohoto výkonu model provádí úpravy podle toho, co se naučilo ve snaze zlepšit.</span><span class="sxs-lookup"><span data-stu-id="68c5d-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="68c5d-252">Sada ověření může pocházet z rozdělení původní datové sady nebo z jiného zdroje, který již byl pro tento účel vyhrazen.</span><span class="sxs-lookup"><span data-stu-id="68c5d-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="68c5d-253">V tomto případě je předem zpracovaná datová sada rozdělena do školicích, ověřovacích a testovacích sad.</span><span class="sxs-lookup"><span data-stu-id="68c5d-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="68c5d-254">Výše uvedený vzor kódu provádí dvě rozdělení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-254">The code sample above performs two splits.</span></span> <span data-ttu-id="68c5d-255">Předem zpracovaná data jsou nejprve rozdělena a 70% se používá pro školení, zatímco se k ověřování používá zbývajících 30%.</span><span class="sxs-lookup"><span data-stu-id="68c5d-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="68c5d-256">Potom je 30% ověřovací sada dále rozdělena na ověřování a sady testů, kde se pro ověřování používá 90% a pro testování se používá 10%.</span><span class="sxs-lookup"><span data-stu-id="68c5d-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span> 

    <span data-ttu-id="68c5d-257">Způsob, jak se zamyslet na účel těchto datových oddílů, je provedení zkoušky.</span><span class="sxs-lookup"><span data-stu-id="68c5d-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="68c5d-258">Při studiu pro zkoušku si Projděte poznámky, knihy nebo jiné prostředky, abyste získali informace o konceptech, které se na této zkoušce nacházejí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="68c5d-259">To je to, pro který je vlaková sada.</span><span class="sxs-lookup"><span data-stu-id="68c5d-259">This is what the train set is for.</span></span> <span data-ttu-id="68c5d-260">Pak můžete pořizovat napodobnou zkoušku k ověření vašeho vědomí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="68c5d-261">Tady se objeví ověřovací sada.</span><span class="sxs-lookup"><span data-stu-id="68c5d-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="68c5d-262">Chcete před provedením samotné zkoušky ověřit, zda máte dobré pojetí konceptů.</span><span class="sxs-lookup"><span data-stu-id="68c5d-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="68c5d-263">Na základě těchto výsledků si poznamenejte, co se vám nepovedlo nebo nerozumělo, a zahrňte své změny do kontroly skutečné zkoušky.</span><span class="sxs-lookup"><span data-stu-id="68c5d-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="68c5d-264">Nakonec můžete provést zkoušku.</span><span class="sxs-lookup"><span data-stu-id="68c5d-264">Finally, you take the exam.</span></span> <span data-ttu-id="68c5d-265">To je to, co je testovací sada používána pro.</span><span class="sxs-lookup"><span data-stu-id="68c5d-265">This is what the test set is used for.</span></span> <span data-ttu-id="68c5d-266">Nikdy jste neviděli otázky, které se týkají zkoušky, a teď pomocí toho, co jste se naučili při školení a ověřování, abyste mohli vaše znalosti na úkol použít.</span><span class="sxs-lookup"><span data-stu-id="68c5d-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span> 

1. <span data-ttu-id="68c5d-267">Přiřaďte oddíly jejich příslušné hodnoty pro data vlaku, ověřování a testování.</span><span class="sxs-lookup"><span data-stu-id="68c5d-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="68c5d-268">Definování školicího kanálu</span><span class="sxs-lookup"><span data-stu-id="68c5d-268">Define the training pipeline</span></span>

<span data-ttu-id="68c5d-269">Školení modelů se skládá z několika kroků.</span><span class="sxs-lookup"><span data-stu-id="68c5d-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="68c5d-270">Rozhraní API pro klasifikaci imagí slouží jako první, používá se k učení modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="68c5d-271">Zakódované popisky ve sloupci `PredictedLabel` se pak převádějí zpátky na původní hodnotu kategorií pomocí `MapKeyToValue` transformaci.</span><span class="sxs-lookup"><span data-stu-id="68c5d-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span> 

1. <span data-ttu-id="68c5d-272">Definujte kanál školení [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) , který se skládá z `mapLabelEstimator` a transformačních `ImageClassification`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-272">Define the training [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline that consists of both the `mapLabelEstimator` and the `ImageClassification` transforms.</span></span>

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    <span data-ttu-id="68c5d-273">`ImageClassification` Estimator přebírá několik parametrů:</span><span class="sxs-lookup"><span data-stu-id="68c5d-273">The `ImageClassification` estimator takes in several parameters:</span></span>

    - <span data-ttu-id="68c5d-274">`featuresColumnName` je sloupec, který se používá jako vstup pro model.</span><span class="sxs-lookup"><span data-stu-id="68c5d-274">`featuresColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="68c5d-275">`labelColumnName` je sloupec, jehož hodnota se má předpovědět.</span><span class="sxs-lookup"><span data-stu-id="68c5d-275">`labelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="68c5d-276">`arch` definuje, které z předdefinovaných architektur modelů se mají použít.</span><span class="sxs-lookup"><span data-stu-id="68c5d-276">`arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="68c5d-277">V tomto kurzu použijeme 101 variant modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="68c5d-277">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="68c5d-278">`epoch` určuje maximální počet iterací pro celou datovou sadu v průběhu procesu školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-278">`epoch` specifies the maximum number of iterations over the entire dataset throughout the training process.</span></span> <span data-ttu-id="68c5d-279">Čím vyšší je číslo, tím déle bude model vlaků pro a potenciálně lepší model, který je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="68c5d-279">The higher the number, the longer the model trains for and potentially the better model that is produced.</span></span>
    - <span data-ttu-id="68c5d-280">`batchSize` je počet vzorků, které se mají použít v čase školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-280">`batchSize` is the number of samples to use at a time for training.</span></span> <span data-ttu-id="68c5d-281">Během jednoho Epocha se ke školení a aktualizaci modelu použijí víc dávek, které se rovnají batchSize.</span><span class="sxs-lookup"><span data-stu-id="68c5d-281">During one epoch, multiple batches equal to the batchSize are used to train and update the model.</span></span> <span data-ttu-id="68c5d-282">Čím nižší číslo, tím méně paměti se vyžaduje při zpracování každé dávky.</span><span class="sxs-lookup"><span data-stu-id="68c5d-282">The lower the number, the less memory required when each batch is processed.</span></span>
    - <span data-ttu-id="68c5d-283">`testOnTrainSet` oznamuje modelu, aby měřil výkon proti školicí sadě, když není k dispozici žádná ověřovací sada.</span><span class="sxs-lookup"><span data-stu-id="68c5d-283">`testOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="68c5d-284">`metricsCallback` váže funkci, aby sledovala průběh během školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-284">`metricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="68c5d-285">`validationSet` je [`IDataView`](xref:Microsoft.ML.IDataView) obsahující ověřovací data.</span><span class="sxs-lookup"><span data-stu-id="68c5d-285">`validationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="68c5d-286">`reuseTrainSetBottleneckCachedValues` instruuje model, zda se mají v následných fázích použít hodnoty uložené v mezipaměti z fáze kritického bodu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-286">`reuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="68c5d-287">Kritická fáze je jednorázové výpočtu předávacího přenosu, který je výpočetně náročný při prvním provedení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-287">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="68c5d-288">Pokud se školicí data nezmění a chcete experimentovat s jiným počtem epochs nebo dávky, použití hodnot uložených v mezipaměti významně zkracuje dobu potřebnou k výuce modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-288">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="68c5d-289">`reuseValidationSetBottleneckCachedValues` je podobná `reuseTrainSetBottleneckCachedValues` pouze v tomto případě je to pro datovou sadu ověřování.</span><span class="sxs-lookup"><span data-stu-id="68c5d-289">`reuseValidationSetBottleneckCachedValues` is similar to `reuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="68c5d-290">`disableEarlyStopping` oznamuje ImageClassification Estimator, jestli se má používat strategie prvotního zastavení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-290">`disableEarlyStopping` tells the ImageClassification estimator whether to employ an early stopping strategy.</span></span> <span data-ttu-id="68c5d-291">V rámci modelu vyhledává optimální hodnoty, které jim umožní zajistit přesnou předpovědii během školení, výkon se může zvýšit nebo snížit.</span><span class="sxs-lookup"><span data-stu-id="68c5d-291">As the model searches for the optimal values that will help it make accurate predictions during training, performance may increase or decrease.</span></span> <span data-ttu-id="68c5d-292">V opačném případě, pokud model dosáhne poslední epocha, může to být případ, kdy jsou vzorce, které se naučily od školení, neoptimální.</span><span class="sxs-lookup"><span data-stu-id="68c5d-292">Ultimately, if the model reaches the last epoch, it may be the case that the patterns it learned from training are suboptimal.</span></span> <span data-ttu-id="68c5d-293">Předčasné zastavení sleduje školení pro tyto poklesy výkonu a zastavuje školicí proces ve snaze zachovat optimální verzi modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-293">Early stopping monitors training for these drops in performance and stops the training process in an effort to preserve an optimal version of the model.</span></span>

1. <span data-ttu-id="68c5d-294">Pro výuku modelu použijte metodu [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) .</span><span class="sxs-lookup"><span data-stu-id="68c5d-294">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a><span data-ttu-id="68c5d-295">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="68c5d-295">Use the model</span></span>

<span data-ttu-id="68c5d-296">Teď, když jste si proškole svůj model, je čas ho použít ke klasifikaci imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-296">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="68c5d-297">Pod metodou `Main` vytvořte novou metodu Utility nazvanou `OutputPrediction`, která zobrazí informace o předpovědi v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="68c5d-297">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a><span data-ttu-id="68c5d-298">Klasifikace jednoho obrázku</span><span class="sxs-lookup"><span data-stu-id="68c5d-298">Classify a single image</span></span>

1. <span data-ttu-id="68c5d-299">Přidejte novou metodu nazvanou `ClassifySingleImage` pod `Main` metodu pro vytvoření a výstup jedné předpovědi imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-299">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="68c5d-300">V rámci metody `ClassifySingleImage` vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) .</span><span class="sxs-lookup"><span data-stu-id="68c5d-300">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="68c5d-301">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="68c5d-301">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. <span data-ttu-id="68c5d-302">Chcete-li získat přístup k jedné instanci `ModelInput`, převeďte [`IDataView`](xref:Microsoft.ML.IDataView) `data` na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a poté Získejte první sledování.</span><span class="sxs-lookup"><span data-stu-id="68c5d-302">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span> 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="68c5d-303">K klasifikaci obrázku použijte metodu [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) .</span><span class="sxs-lookup"><span data-stu-id="68c5d-303">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="68c5d-304">Výstup předpovědi do konzoly s metodou `OutputPrediction`.</span><span class="sxs-lookup"><span data-stu-id="68c5d-304">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. <span data-ttu-id="68c5d-305">Uvnitř metody `Main` volejte `ClassifySingleImage` pomocí testovací sady imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-305">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a><span data-ttu-id="68c5d-306">Klasifikace více imagí</span><span class="sxs-lookup"><span data-stu-id="68c5d-306">Classify multiple images</span></span>

1. <span data-ttu-id="68c5d-307">Přidejte novou metodu nazvanou `ClassifyImages` pod `ClassifySingleImage` metodu pro vytvoření a výstup více předpovědi obrázků.</span><span class="sxs-lookup"><span data-stu-id="68c5d-307">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="68c5d-308">Vytvořte [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předpovědi pomocí metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) .</span><span class="sxs-lookup"><span data-stu-id="68c5d-308">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="68c5d-309">Do metody `ClassifyImages` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="68c5d-309">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. <span data-ttu-id="68c5d-310">Chcete-li iterovat přes předpovědi, převeďte `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a potom Získejte prvních 10 pozorování.</span><span class="sxs-lookup"><span data-stu-id="68c5d-310">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="68c5d-311">Iterujte a navýstupujte původní a předpovězené popisky pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="68c5d-311">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. <span data-ttu-id="68c5d-312">Nakonec v rámci metody `Main` volejte `ClassifyImages` pomocí testovací sady imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-312">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a><span data-ttu-id="68c5d-313">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="68c5d-313">Run the application</span></span>

<span data-ttu-id="68c5d-314">Spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="68c5d-314">Run your console app.</span></span> <span data-ttu-id="68c5d-315">Výstup by měl vypadat podobně jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="68c5d-315">The output should be similar to that below.</span></span> <span data-ttu-id="68c5d-316">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="68c5d-316">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="68c5d-317">V případě zkrácení byl výstup zúžený.</span><span class="sxs-lookup"><span data-stu-id="68c5d-317">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="68c5d-318">**Fáze kritického bodu**</span><span class="sxs-lookup"><span data-stu-id="68c5d-318">**Bottleneck phase**</span></span>

<span data-ttu-id="68c5d-319">Pro název Image se nevytiskne žádná hodnota, protože image jsou načtené jako `byte[]` proto, že není k dispozici žádný název Image k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-319">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

<span data-ttu-id="68c5d-320">**Fáze školení**</span><span class="sxs-lookup"><span data-stu-id="68c5d-320">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="68c5d-321">**Klasifikovat výstup imagí**</span><span class="sxs-lookup"><span data-stu-id="68c5d-321">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="68c5d-322">Po kontrole obrázku *7001 -220. jpg* vidíte, že ve skutečnosti není prasklý.</span><span class="sxs-lookup"><span data-stu-id="68c5d-322">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span> 

![Obrázek datové sady SDNET2018 použité pro předpověď](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="68c5d-324">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="68c5d-324">Congratulations!</span></span> <span data-ttu-id="68c5d-325">Teď jste úspěšně vytvořili model hloubkového učení pro klasifikaci imagí.</span><span class="sxs-lookup"><span data-stu-id="68c5d-325">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="68c5d-326">Zlepšení modelu</span><span class="sxs-lookup"><span data-stu-id="68c5d-326">Improve the model</span></span>

<span data-ttu-id="68c5d-327">Pokud nejste spokojeni s výsledky modelu, můžete se pokusit zvýšit jeho výkon tak, že zkusíte některé z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="68c5d-327">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="68c5d-328">**Další data**: Další příklady, ze kterých se model učí, je lepší.</span><span class="sxs-lookup"><span data-stu-id="68c5d-328">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="68c5d-329">Stáhněte si úplnou [datovou sadu SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) a využijte ji ke školení.</span><span class="sxs-lookup"><span data-stu-id="68c5d-329">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span> 
- <span data-ttu-id="68c5d-330">**Rozšíření dat**: běžnou technikou pro přidání různých druhů dat je rozšíření dat pomocí obrázku a použití různých transformací (otočení, překlopení, posunutí a oříznutí).</span><span class="sxs-lookup"><span data-stu-id="68c5d-330">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="68c5d-331">Tím se přidá více různých příkladů modelu, ze kterého se naučíte.</span><span class="sxs-lookup"><span data-stu-id="68c5d-331">This adds more varied examples for the model to learn from.</span></span> 
- <span data-ttu-id="68c5d-332">**Školení pro delší dobu**: čím delší je, tím bude model lépe vyladěný.</span><span class="sxs-lookup"><span data-stu-id="68c5d-332">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="68c5d-333">Zvýšení počtu epochs může zlepšit výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-333">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="68c5d-334">**Experiment s parametrem Hyper-Parameters**: Kromě parametrů používaných v tomto kurzu můžete další parametry vyladit tak, aby potenciálně vylepšily výkon.</span><span class="sxs-lookup"><span data-stu-id="68c5d-334">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="68c5d-335">Změna studijní frekvence, která určuje velikost aktualizací v modelu po každém epocha, může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="68c5d-335">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="68c5d-336">**Použití jiné architektury modelů**: v závislosti na tom, jak vaše data vypadají, se může model, který se nejlépe učí jeho funkcí, lišit.</span><span class="sxs-lookup"><span data-stu-id="68c5d-336">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="68c5d-337">Pokud nejste spokojeni s výkonem modelu, zkuste změnit architekturu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-337">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="68c5d-338">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="68c5d-338">Additional Resources</span></span>

- <span data-ttu-id="68c5d-339">[Obsáhlý Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="68c5d-339">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="68c5d-340">Další kroky</span><span class="sxs-lookup"><span data-stu-id="68c5d-340">Next steps</span></span>

<span data-ttu-id="68c5d-341">V tomto kurzu jste zjistili, jak vytvořit vlastní model hloubkového učení s využitím učení přenosu, předTensorFlowho modelu klasifikace imagí a rozhraní API pro klasifikaci ml.NET pro klasifikaci imagí konkrétních povrchů jako prasklé nebo prolomené.</span><span class="sxs-lookup"><span data-stu-id="68c5d-341">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="68c5d-342">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="68c5d-342">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="68c5d-343">Detekce objektu</span><span class="sxs-lookup"><span data-stu-id="68c5d-343">Object Detection</span></span>](object-detection-onnx.md)
