---
title: 'Kurz: generování modelu klasifikace imagí ML.NET z předem připraveného modelu TensorFlow'
description: Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace imagí ML.NET. Model TensorFlow byl vyškolen pro klasifikaci imagí do tisíc kategorií. Model ML.NET využívá učení přenosu pro klasifikaci imagí do méně širších kategorií.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 8ae966330ca85722c72c92e26363d99c7d9de3e7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698652"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="fe9f2-105">Kurz: generování modelu klasifikace imagí ML.NET z předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="fe9f2-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="fe9f2-106">Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace imagí ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="fe9f2-107">Model TensorFlow byl vyškolen pro klasifikaci imagí do tisíc kategorií.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="fe9f2-108">Model ML.NET využívá část modelu TensorFlow ve svém kanálu k vytvoření modelu pro klasifikaci imagí do 3 kategorií.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="fe9f2-109">Školení modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tunu školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="fe9f2-110">I když není tak efektivní jako školení vlastního modelu od začátku, pomůže vám tento proces zástupcem pracovat s tisíci imagí. miliony imagí s popisky a sestavování vlastního modelu je poměrně rychlé (během hodiny na počítači bez GPU).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="fe9f2-111">Tento kurz škáluje ještě více procesů a používá jenom spoustu školicích imagí.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="fe9f2-112">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fe9f2-113">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="fe9f2-113">Understand the problem</span></span>
> * <span data-ttu-id="fe9f2-114">Zahrňte předem vyškolený model TensorFlow do kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe9f2-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="fe9f2-115">Výuka a vyhodnocení modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe9f2-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="fe9f2-116">Klasifikace testovací image</span><span class="sxs-lookup"><span data-stu-id="fe9f2-116">Classify a test image</span></span>

<span data-ttu-id="fe9f2-117">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="fe9f2-118">Všimněte si, že ve výchozím nastavení je konfigurace projektu .NET pro tento kurz určena pro .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="fe9f2-119">Co je učení přenosu?</span><span class="sxs-lookup"><span data-stu-id="fe9f2-119">What is transfer learning?</span></span>

<span data-ttu-id="fe9f2-120">Učení přenosu je proces použití znalostí získaných při řešení jednoho problému a jeho použití na jiný, ale související problém.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="fe9f2-121">Pro účely tohoto kurzu použijete část TensorFlow modelu vyškolená pro klasifikaci imagí do tisíc kategorií – v modelu ML.NET, který klasifikuje obrázky do 3 kategorií.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fe9f2-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe9f2-122">Prerequisites</span></span>

* <span data-ttu-id="fe9f2-123">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="fe9f2-124">Balíček NuGet pro Microsoft.ML 1.3.1</span><span class="sxs-lookup"><span data-stu-id="fe9f2-124">Microsoft.ML 1.3.1 Nuget package</span></span>
* <span data-ttu-id="fe9f2-125">Balíček NuGet pro Microsoft. ML. ImageAnalytics 1.3.1</span><span class="sxs-lookup"><span data-stu-id="fe9f2-125">Microsoft.ML.ImageAnalytics 1.3.1 Nuget package</span></span>
* <span data-ttu-id="fe9f2-126">Balíček NuGet pro Microsoft. ML. TensorFlow 1.3.1</span><span class="sxs-lookup"><span data-stu-id="fe9f2-126">Microsoft.ML.TensorFlow 1.3.1 Nuget package</span></span>

* [<span data-ttu-id="fe9f2-127">Adresář assetů tutorial Soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="fe9f2-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="fe9f2-128">Model strojového učení InceptionV1</span><span class="sxs-lookup"><span data-stu-id="fe9f2-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="fe9f2-129">Vyberte správnou úlohu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-129">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="fe9f2-130">Obsáhlý Learning</span><span class="sxs-lookup"><span data-stu-id="fe9f2-130">Deep learning</span></span>

<span data-ttu-id="fe9f2-131">[Obsáhlý Learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, což jsou revolutionizing oblasti, jako je počítačové zpracování obrazu a rozpoznávání řeči.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-131">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="fe9f2-132">Modely hloubkového učení jsou vyškoleny pomocí rozsáhlých sad [dat s popisky](https://en.wikipedia.org/wiki/Labeled_data) a [neuronové sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více výukových vrstev.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-132">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="fe9f2-133">Obsáhlý Learning:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-133">Deep learning:</span></span>

* <span data-ttu-id="fe9f2-134">Je lepší pro některé úkoly, jako je Počítačové zpracování obrazu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-134">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="fe9f2-135">Vyžaduje velké množství školicích dat.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-135">Requires huge amounts of training data.</span></span>

<span data-ttu-id="fe9f2-136">Klasifikace obrázku je běžný Machine Learning úkol, který nám umožňuje automaticky klasifikovat obrázky do kategorií, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-136">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="fe9f2-137">Zjištění lidského obličeje v obrázku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-137">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="fe9f2-138">Detekce koček a psi.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-138">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="fe9f2-139">Nebo jak na následujících obrázcích zjistit, jestli je image a (n) jídla, hračka nebo zařízení:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-139">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="fe9f2-140">![pizza obrázek @ no__t-1 @ no__t-2teddy Bear image @ no__t-3 @ no__t-4toaster image @ no__t-5</span><span class="sxs-lookup"><span data-stu-id="fe9f2-140">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="fe9f2-141">Předchozí image patří do Wikimedia a jsou jim tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-141">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="fe9f2-142">Veřejná doména "220px-Pepperoni_pizza. jpg", https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="fe9f2-142">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="fe9f2-143">"119px-Nalle_-_a_small_brown_teddy_bear. jpg" pomocí [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) – s fotografací, CC by-SA 2,0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-143">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="fe9f2-144">"193px-Broodrooster. jpg" podle [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) vlastní práce, CC by-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="fe9f2-144">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="fe9f2-145">@No__t-0 se vyškole pro klasifikaci imagí do tisíc kategorií, ale pro tento kurz je potřeba klasifikovat obrázky v menší sadě kategorií a jenom v těchto kategoriích.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-145">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="fe9f2-146">Zadejte `transfer` část `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-146">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="fe9f2-147">Můžete přenést `Inception model` schopnost rozpoznávat a klasifikovat obrázky pro nové kategorie omezené na vlastní třídění imagí.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-147">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="fe9f2-148">Simulant</span><span class="sxs-lookup"><span data-stu-id="fe9f2-148">Food</span></span>
* <span data-ttu-id="fe9f2-149">Hračk</span><span class="sxs-lookup"><span data-stu-id="fe9f2-149">Toy</span></span>
* <span data-ttu-id="fe9f2-150">Náplně</span><span class="sxs-lookup"><span data-stu-id="fe9f2-150">Appliance</span></span>

<span data-ttu-id="fe9f2-151">V tomto kurzu se používá model hloubkového učení [modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) TensorFlow, který je oblíbený pro model rozpoznávání imagí, který je vyškolený v datové sadě `ImageNet`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-151">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="fe9f2-152">Model TensorFlow klasifikuje celé obrázky do tisíc tříd, například "deštník", "Jersey" a "myčku".</span><span class="sxs-lookup"><span data-stu-id="fe9f2-152">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="fe9f2-153">Vzhledem k tomu, že `Inception model` již byl předem vyškolen na tisících různých imagí, interně obsahuje [funkce obrázků](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-153">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="fe9f2-154">Pomocí těchto interních funkcí obrázků v modelu můžete vytvořit nový model s mnohem menším počtem tříd.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-154">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="fe9f2-155">Jak je znázorněno v následujícím diagramu, přidáte odkaz na balíčky NuGet ML.NET v aplikacích .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-155">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="fe9f2-156">V rámci zahrnutí ML.NET zahrnuje a odkazuje na nativní knihovnu @no__t 0, která umožňuje napsat kód, který načte existující školený soubor modelu `TensorFlow`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-156">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagram TensorFlow Transform ML.NET archu](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="fe9f2-158">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="fe9f2-158">Multiclass classification</span></span>

<span data-ttu-id="fe9f2-159">Po použití modelu TensorFlowho zahájení k extrakci funkcí vhodných jako vstup pro klasický algoritmus strojového učení přidáme ML.NET třídění s [více třídami](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-159">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="fe9f2-160">Konkrétní Trainer použitý v tomto případě je [algoritmus MULTINOMIAL logistické regrese](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-160">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="fe9f2-161">Algoritmus implementovaný tímto Trainer se dobře hodí v případě problémů s velkým počtem funkcí, což je případ pro model hloubkového učení, který pracuje s daty imagí.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-161">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="fe9f2-162">Data</span><span class="sxs-lookup"><span data-stu-id="fe9f2-162">Data</span></span>

<span data-ttu-id="fe9f2-163">Existují dva zdroje dat: soubor `.tsv` a soubory obrázků.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-163">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="fe9f2-164">Soubor `tags.tsv` obsahuje dva sloupce: první z nich je definována jako `ImagePath` a druhá hodnota je `Label` odpovídající imagi.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-164">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="fe9f2-165">Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-165">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="fe9f2-166">Obrázky školení a testování se nacházejí ve složkách assetů, které stáhnete do souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-166">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="fe9f2-167">Tyto image patří do Wikimedia.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-167">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="fe9f2-168">*[Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), bezplatné úložiště médií.*</span><span class="sxs-lookup"><span data-stu-id="fe9f2-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="fe9f2-169">Načteno 10:48, 17. října 2018 z: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="fe9f2-169">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="fe9f2-170">Instalace</span><span class="sxs-lookup"><span data-stu-id="fe9f2-170">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="fe9f2-171">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fe9f2-171">Create a project</span></span>

1. <span data-ttu-id="fe9f2-172">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="fe9f2-172">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="fe9f2-173">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="fe9f2-174">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="fe9f2-175">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="fe9f2-176">Klikněte na rozevírací seznam **verze** , v seznamu vyberte balíček **1.3.1** a vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-176">Click on the **Version** drop-down, select the **1.3.1** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="fe9f2-177">V dialogovém okně **Náhled změn** vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-177">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="fe9f2-178">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, v dialogu pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-178">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="fe9f2-179">Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics v 1.3.1** a **Microsoft. ml. TensorFlow v 1.3.1**.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-179">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.3.1** and **Microsoft.ML.TensorFlow v1.3.1**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="fe9f2-180">Stažení prostředků</span><span class="sxs-lookup"><span data-stu-id="fe9f2-180">Download assets</span></span>

1. <span data-ttu-id="fe9f2-181">Stáhněte si [soubor zip adresáře Project assets](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-181">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="fe9f2-182">Zkopírujte adresář `assets` do adresáře projektu *TransferLearningTF* .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-182">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="fe9f2-183">Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu zahájení, který si stáhnete a přidáte v dalším kroku) potřebném pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-183">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="fe9f2-184">Stáhněte si [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-184">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="fe9f2-185">Zkopírujte obsah adresáře `inception5h` pouze do složky projektu *TransferLearningTF* `assets/inputs-train/inception`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-185">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inputs-train/inception` directory.</span></span> <span data-ttu-id="fe9f2-186">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-186">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Obsah adresáře v adresáři](./media/image-classification/inception-files.png)

1. <span data-ttu-id="fe9f2-188">V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-188">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="fe9f2-189">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="fe9f2-190">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="fe9f2-190">Create classes and define paths</span></span>

1. <span data-ttu-id="fe9f2-191">Do horní části souboru *program.cs* přidejte následující dodatečné příkazy `using`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="fe9f2-192">Přidejte následující kód na řádek vpravo nad metodou `Main` pro určení cest prostředků:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-192">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="fe9f2-193">Vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-193">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="fe9f2-194">`ImageData` je vstupní třída dat obrázku a má následující pole <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-194">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="fe9f2-195">`ImagePath` obsahuje název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-195">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="fe9f2-196">`Label` obsahuje hodnotu pro popisek obrázku.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-196">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="fe9f2-197">Přidejte do projektu novou třídu pro `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-197">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="fe9f2-198">`ImagePrediction` je třída předpovědi obrázku a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-198">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="fe9f2-199">`Score` obsahuje procento spolehlivosti pro danou klasifikaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-199">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="fe9f2-200">`PredictedLabelValue` obsahuje hodnotu pro předpokládaný popisek klasifikace obrázku.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-200">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="fe9f2-201">`ImagePrediction` je třída použitá pro předpověď po vyškolení modelu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-201">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="fe9f2-202">Pro cestu k imagi má `string` (`ImagePath`).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-202">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="fe9f2-203">@No__t-0 slouží k opakovanému použití a výukového modelu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-203">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="fe9f2-204">@No__t-0 se používá během předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-204">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="fe9f2-205">Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-205">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="fe9f2-206">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="fe9f2-206">Initialize variables in Main</span></span>

1. <span data-ttu-id="fe9f2-207">Inicializujte proměnnou `mlContext` novou instancí `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-207">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="fe9f2-208">Nahraďte řádek `Console.WriteLine("Hello World!")` následujícím kódem v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-208">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="fe9f2-209">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje se `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-209">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fe9f2-210">Je podobné, koncepčně, `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-210">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="fe9f2-211">Vytvoření struktury pro parametry modelu vytvářené</span><span class="sxs-lookup"><span data-stu-id="fe9f2-211">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="fe9f2-212">Model zahájení má několik parametrů, které je třeba předat.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-212">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="fe9f2-213">Vytvořte strukturu pro mapování hodnot parametrů na popisné názvy pomocí následujícího kódu, a to hned za metodou `Main()`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-213">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="fe9f2-214">Vytvoření metody zobrazovacího nástroje</span><span class="sxs-lookup"><span data-stu-id="fe9f2-214">Create a display utility method</span></span>

<span data-ttu-id="fe9f2-215">Vzhledem k tomu, že zobrazíte data obrázku a související předpovědi více než jednou, vytvořte metodu zobrazení nástrojů pro zpracování zobrazení obrázků a výsledků předpovědi.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-215">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="fe9f2-216">Vytvořte metodu `DisplayResults()` hned za strukturou `InceptionSettings` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-216">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="fe9f2-217">Vyplňte text metody `DisplayResults`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-217">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="fe9f2-218">Vytvoření metody Utility souboru. TSV</span><span class="sxs-lookup"><span data-stu-id="fe9f2-218">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="fe9f2-219">Vytvořte metodu `ReadFromTsv()` hned za metodou `DisplayResults()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-219">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="fe9f2-220">Vyplňte text metody `ReadFromTsv`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-220">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="fe9f2-221">Kód analyzuje soubor `tags.tsv`, aby přidal cestu k souboru bitové kopie pro vlastnost `ImagePath` a načetl ji a `Label` do objektu `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-221">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="fe9f2-222">Vytvoření metody pro předpověď</span><span class="sxs-lookup"><span data-stu-id="fe9f2-222">Create a method to make a prediction</span></span>

1. <span data-ttu-id="fe9f2-223">Vytvořte metodu `ClassifySingleImage()` těsně před metodou `DisplayResults()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-223">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="fe9f2-224">Vytvořte objekt `ImageData`, který obsahuje plně kvalifikovanou cestu a název souboru obrázku pro jednu `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-224">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="fe9f2-225">Přidejte následující kód jako další řádky v metodě `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-225">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="fe9f2-226">Proveďte jednu předpověď přidáním následujícího kódu jako dalšího řádku do metody `ClassifySingleImage`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-226">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="fe9f2-227">K získání předpovědi použijte metodu [předpověď ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-227">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="fe9f2-228">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-228">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="fe9f2-229">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-229">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="fe9f2-230">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-230">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="fe9f2-231">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-231">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="fe9f2-232">V této příručce najdete informace o [použití `PredictionEnginePool` v ASP.NET Core webovém rozhraní API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-232">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

    > [!NOTE]
    > <span data-ttu-id="fe9f2-233">rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-233">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="fe9f2-234">Zobrazit výsledek předpovědi jako další řádek kódu v metodě `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-234">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="fe9f2-235">Vytvoření kanálu modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe9f2-235">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="fe9f2-236">Kanál ML.NET modelu je řetězec odhady.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-236">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="fe9f2-237">Všimněte si, že během vytváření kanálu nedojde k žádnému spuštění.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-237">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="fe9f2-238">Objekty Estimator jsou vytvořeny, ale nejsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-238">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="fe9f2-239">Přidejte metodu pro vytvoření modelu</span><span class="sxs-lookup"><span data-stu-id="fe9f2-239">Add a method to generate the model</span></span>

    <span data-ttu-id="fe9f2-240">Tato metoda je srdcem kurzu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-240">This method is the heart of the tutorial.</span></span> <span data-ttu-id="fe9f2-241">Vytvoří kanál pro model a navlakuje kanál k vytvoření modelu ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-241">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="fe9f2-242">Vyhodnocuje také model proti dříve nezobrazeným datům testu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-242">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="fe9f2-243">Vytvořte metodu `GenerateModel()` hned za strukturou `InceptionSettings` a těsně před metodou `DisplayResults()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-243">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="fe9f2-244">Přidat odhady pro načtení, změnu velikosti a extrakci pixelů z dat obrázku:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-244">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="fe9f2-245">Data obrázku musí být zpracována ve formátu, který očekává model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-245">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="fe9f2-246">V tomto případě jsou obrázky načteny do paměti, jsou změněna na konzistentní velikost a pixely jsou extrahovány do číselného vektoru.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-246">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="fe9f2-247">Přidejte Estimator, abyste načetli model TensorFlow, a zadávejte skóre:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-247">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="fe9f2-248">Tato fáze v kanálu načte model TensorFlow do paměti a pak zpracovává vektor hodnot obrazových bodů prostřednictvím sítě modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-248">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="fe9f2-249">Použití vstupů na model hloubkového učení a generování výstupu pomocí modelu se označuje jako **bodování**.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-249">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="fe9f2-250">Při použití modelu v celém rozsahu je bodování odvozeno nebo předpověď.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-250">When using the model in its entirety, scoring makes an inference, or prediction.</span></span> 

    <span data-ttu-id="fe9f2-251">V tomto případě použijete všechen TensorFlow model kromě poslední vrstvy, což je vrstva, která provádí odvození.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-251">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="fe9f2-252">Výstup předposlední vrstvy je označený `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-252">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="fe9f2-253">Výstup této vrstvy je efektivně vektor funkcí, které charakterizují původní vstupní image.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-253">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="fe9f2-254">Tento vektor funkce generovaný modelem TensorFlow se použije jako vstup pro školicí algoritmus ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-254">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="fe9f2-255">Přidejte Estimator k namapování popisků řetězce v školicích datech na hodnoty celočíselného klíče:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-255">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="fe9f2-256">ML.NET Trainer, který je připojen k dalšímu, vyžaduje, aby popisky byly ve formátu `key`, nikoli v libovolném řetězci.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-256">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="fe9f2-257">Klíč je číslo, které má jeden k jednomu mapování na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-257">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="fe9f2-258">Přidejte ML.NET školicí algoritmus:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-258">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="fe9f2-259">Přidejte Estimator k namapování hodnoty předpovězeného klíče zpátky do řetězce:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-259">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="fe9f2-260">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="fe9f2-260">Train the model</span></span>

1. <span data-ttu-id="fe9f2-261">Načtěte školicí data pomocí obálky [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-261">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="fe9f2-262">Přidejte následující kód jako další řádek v metodě `GenerateModel()`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-262">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="fe9f2-263">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-263">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="fe9f2-264">`IDataView` je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-264">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="fe9f2-265">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-265">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="fe9f2-266">Vyškolit model s daty načtenými výše:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-266">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="fe9f2-267">Metoda `Fit()` nahlaste svůj model použitím datové sady školení na kanál.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-267">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="fe9f2-268">Vyhodnotit přesnost modelu</span><span class="sxs-lookup"><span data-stu-id="fe9f2-268">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="fe9f2-269">Načtěte a Transformujte testovací data přidáním následujícího kódu na další řádek metody `GenerateModel`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-269">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="fe9f2-270">Existuje několik ukázkových imagí, které můžete použít k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-270">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="fe9f2-271">Podobně jako u školicích dat je třeba je načíst do `IDataView`, aby je bylo možné transformovat podle modelu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-271">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>
   
1. <span data-ttu-id="fe9f2-272">Přidejte následující kód do metody `GenerateModel()` pro vyhodnocení modelu:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-272">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="fe9f2-273">Jakmile máte předsadu předpovědi, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="fe9f2-273">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="fe9f2-274">Vyhodnotí model (porovná předpovězené hodnoty s testovací datovou sadou `labels`).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-274">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="fe9f2-275">Vrátí metriku výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-275">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="fe9f2-276">Zobrazit metriky přesnosti modelu</span><span class="sxs-lookup"><span data-stu-id="fe9f2-276">Display the model accuracy metrics</span></span>

    <span data-ttu-id="fe9f2-277">Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-277">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="fe9f2-278">Pro klasifikaci imagí jsou vyhodnocovány následující metriky:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-278">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="fe9f2-279">`Log-loss` – Podívejte se na [ztrátu protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-279">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="fe9f2-280">Chcete, aby byla ztráta protokolu co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-280">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="fe9f2-281">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-281">`Per class Log-loss`.</span></span> <span data-ttu-id="fe9f2-282">Požadujete, aby byla ztráta protokolu podle třídy co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-282">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="fe9f2-283">Přidejte následující kód, který vrátí vycvičený model jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-283">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="fe9f2-284">Spusťte aplikaci!</span><span class="sxs-lookup"><span data-stu-id="fe9f2-284">Run the application!</span></span>

1. <span data-ttu-id="fe9f2-285">Po vytvoření třídy MLContext přidejte volání `GenerateModel` v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-285">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="fe9f2-286">Přidejte volání metody `ClassifySingleImage()` jako další řádek kódu v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-286">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="fe9f2-287">Spusťte konzolovou aplikaci (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="fe9f2-287">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="fe9f2-288">Výsledky by měly být podobné následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-288">Your results should be similar to the following output.</span></span>  <span data-ttu-id="fe9f2-289">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-289">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli.jpg predicted as: food with score: 0.976743
    Image: pizza.jpg predicted as: food with score: 0.9751652
    Image: pizza2.jpg predicted as: food with score: 0.9660203
    Image: teddy2.jpg predicted as: toy with score: 0.9748783
    Image: teddy3.jpg predicted as: toy with score: 0.9829691
    Image: teddy4.jpg predicted as: toy with score: 0.9868168
    Image: toaster.jpg predicted as: appliance with score: 0.9769174
    Image: toaster2.png predicted as: appliance with score: 0.9800823
    =============== Classification metrics ===============
    LogLoss is: 0.0228266745633507
    PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

<span data-ttu-id="fe9f2-290">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="fe9f2-290">Congratulations!</span></span> <span data-ttu-id="fe9f2-291">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci imagí tím, že použijete učení přenosu na model `TensorFlow` v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-291">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="fe9f2-292">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="fe9f2-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="fe9f2-293">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="fe9f2-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fe9f2-294">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="fe9f2-294">Understand the problem</span></span>
> * <span data-ttu-id="fe9f2-295">Zahrňte předem vyškolený model TensorFlow do kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe9f2-295">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="fe9f2-296">Výuka a vyhodnocení modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe9f2-296">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="fe9f2-297">Klasifikace testovací image</span><span class="sxs-lookup"><span data-stu-id="fe9f2-297">Classify a test image</span></span>

<span data-ttu-id="fe9f2-298">Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku klasifikace rozbalené image.</span><span class="sxs-lookup"><span data-stu-id="fe9f2-298">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="fe9f2-299">dotnet/machinelearning-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="fe9f2-299">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
