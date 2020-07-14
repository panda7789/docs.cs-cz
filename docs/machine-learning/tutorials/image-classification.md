---
title: 'Kurz: model klasifikace imagí ML.NET z TensorFlow'
description: Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace imagí ML.NET. Model TensorFlow byl vyškolen pro klasifikaci imagí do tisíc kategorií. Model ML.NET využívá učení přenosu pro klasifikaci imagí do méně širších kategorií.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: a4c671816dce1fe2abdf77f81da0f27236136536
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282109"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="4d952-105">Kurz: generování modelu klasifikace imagí ML.NET z předem připraveného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="4d952-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="4d952-106">Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace imagí ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4d952-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="4d952-107">Model TensorFlow byl vyškolen pro klasifikaci imagí do tisíc kategorií.</span><span class="sxs-lookup"><span data-stu-id="4d952-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="4d952-108">Model ML.NET využívá část modelu TensorFlow ve svém kanálu k vytvoření modelu pro klasifikaci imagí do 3 kategorií.</span><span class="sxs-lookup"><span data-stu-id="4d952-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="4d952-109">Školení modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tunu školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="4d952-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="4d952-110">I když není tak efektivní jako školení vlastního modelu od začátku, pomůže vám tento proces zástupcem při práci s tisíci imagí a miliony imagí s popisky a vytvořit přizpůsobený model poměrně rychle (během hodiny na počítači bez GPU).</span><span class="sxs-lookup"><span data-stu-id="4d952-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="4d952-111">Tento kurz škáluje ještě více procesů a používá jenom spoustu školicích imagí.</span><span class="sxs-lookup"><span data-stu-id="4d952-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="4d952-112">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="4d952-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4d952-113">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="4d952-113">Understand the problem</span></span>
> * <span data-ttu-id="4d952-114">Zahrňte předem vyškolený model TensorFlow do kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d952-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="4d952-115">Výuka a vyhodnocení modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d952-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="4d952-116">Klasifikace testovací image</span><span class="sxs-lookup"><span data-stu-id="4d952-116">Classify a test image</span></span>

<span data-ttu-id="4d952-117">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="4d952-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="4d952-118">Všimněte si, že ve výchozím nastavení je konfigurace projektu .NET pro tento kurz určena pro .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="4d952-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="4d952-119">Co je transferové učení?</span><span class="sxs-lookup"><span data-stu-id="4d952-119">What is transfer learning?</span></span>

<span data-ttu-id="4d952-120">Učení přenosu je proces použití znalostí získaných při řešení jednoho problému a jeho použití na jiný, ale související problém.</span><span class="sxs-lookup"><span data-stu-id="4d952-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="4d952-121">Pro účely tohoto kurzu použijete část TensorFlow modelu vyškolená pro klasifikaci imagí do tisíc kategorií – v modelu ML.NET, který klasifikuje obrázky do 3 kategorií.</span><span class="sxs-lookup"><span data-stu-id="4d952-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d952-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d952-122">Prerequisites</span></span>

* <span data-ttu-id="4d952-123">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="4d952-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="4d952-124">Adresář assetů tutorial Soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="4d952-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="4d952-125">Model strojového učení InceptionV1</span><span class="sxs-lookup"><span data-stu-id="4d952-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="4d952-126">Vyberte správnou úlohu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="4d952-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="4d952-127">Hloubkové učení</span><span class="sxs-lookup"><span data-stu-id="4d952-127">Deep learning</span></span>

<span data-ttu-id="4d952-128">[Obsáhlý Learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, což jsou revolutionizing oblasti, jako je počítačové zpracování obrazu a rozpoznávání řeči.</span><span class="sxs-lookup"><span data-stu-id="4d952-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="4d952-129">Modely hloubkového učení jsou vyškoleny pomocí rozsáhlých sad [dat s popisky](https://en.wikipedia.org/wiki/Labeled_data) a [neuronové sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více výukových vrstev.</span><span class="sxs-lookup"><span data-stu-id="4d952-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="4d952-130">Obsáhlý Learning:</span><span class="sxs-lookup"><span data-stu-id="4d952-130">Deep learning:</span></span>

* <span data-ttu-id="4d952-131">Je lepší pro některé úkoly, jako je Počítačové zpracování obrazu.</span><span class="sxs-lookup"><span data-stu-id="4d952-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="4d952-132">Vyžaduje velké množství školicích dat.</span><span class="sxs-lookup"><span data-stu-id="4d952-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="4d952-133">Klasifikace obrázku je běžný Machine Learning úkol, který nám umožňuje automaticky klasifikovat obrázky do kategorií, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="4d952-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="4d952-134">Zjištění lidského obličeje v obrázku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="4d952-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="4d952-135">Detekce koček a psi.</span><span class="sxs-lookup"><span data-stu-id="4d952-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="4d952-136">Nebo jak na následujících obrázcích zjistit, jestli je image a (n) jídla, hračka nebo zařízení:</span><span class="sxs-lookup"><span data-stu-id="4d952-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="4d952-137">![](./media/image-classification/220px-Pepperoni_pizza.jpg)
 ![ ](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
 ![ Obrázek informační zprávy image Pizza image Teddy](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d952-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="4d952-138">Předchozí image patří do Wikimedia a jsou jim tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="4d952-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="4d952-139">Veřejné domény "220px-Pepperoni_pizza.jpg", <https://commons.wikimedia.org/w/index.php?curid=79505> ,</span><span class="sxs-lookup"><span data-stu-id="4d952-139">"220px-Pepperoni_pizza.jpg" Public Domain, <https://commons.wikimedia.org/w/index.php?curid=79505>,</span></span>
> * <span data-ttu-id="4d952-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" pomocí [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) – fotograficky založeného na programu cc-SA 2,0, <https://commons.wikimedia.org/w/index.php?curid=48166> .</span><span class="sxs-lookup"><span data-stu-id="4d952-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>.</span></span>
> * <span data-ttu-id="4d952-141">"193px-Broodrooster.jpg" podle [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) – vlastní práce, CC by-sa 3,0,<https://commons.wikimedia.org/w/index.php?curid=27403></span><span class="sxs-lookup"><span data-stu-id="4d952-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403></span></span>

<span data-ttu-id="4d952-142">`Inception model`Je vyškolená pro klasifikaci imagí do tisíc kategorií, ale pro tento kurz je potřeba klasifikovat obrázky v menší sadě kategorií a jenom na těchto kategoriích.</span><span class="sxs-lookup"><span data-stu-id="4d952-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="4d952-143">Zadejte `transfer` část `transfer learning` .</span><span class="sxs-lookup"><span data-stu-id="4d952-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="4d952-144">Můžete přenést `Inception model` schopnost rozpoznávat a klasifikovat obrázky pro nové kategorie omezené na vlastní třídění imagí.</span><span class="sxs-lookup"><span data-stu-id="4d952-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="4d952-145">Simulant</span><span class="sxs-lookup"><span data-stu-id="4d952-145">Food</span></span>
* <span data-ttu-id="4d952-146">Hračk</span><span class="sxs-lookup"><span data-stu-id="4d952-146">Toy</span></span>
* <span data-ttu-id="4d952-147">Náplně</span><span class="sxs-lookup"><span data-stu-id="4d952-147">Appliance</span></span>

<span data-ttu-id="4d952-148">V tomto kurzu se používá model hloubkového učení [modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) TensorFlow, který je oblíbený pro model rozpoznávání imagí, který je vyškolený pro `ImageNet` datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="4d952-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="4d952-149">Model TensorFlow klasifikuje celé obrázky do tisíc tříd, například "deštník", "Jersey" a "myčku".</span><span class="sxs-lookup"><span data-stu-id="4d952-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="4d952-150">Vzhledem k tomu `Inception model` , že již byl předem vyškolen na tisících různých imagí, interně obsahuje [funkce obrázků](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="4d952-151">Pomocí těchto interních funkcí obrázků v modelu můžete vytvořit nový model s mnohem menším počtem tříd.</span><span class="sxs-lookup"><span data-stu-id="4d952-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="4d952-152">Jak je znázorněno v následujícím diagramu, přidáte odkaz na balíčky NuGet ML.NET v aplikacích .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d952-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="4d952-153">V rámci zahrnutí ML.NET zahrnuje a odkazuje na nativní `TensorFlow` knihovnu, která umožňuje napsat kód, který načte existující soubor trained `TensorFlow` model.</span><span class="sxs-lookup"><span data-stu-id="4d952-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagram TensorFlow Transform ML.NET archu](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="4d952-155">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="4d952-155">Multiclass classification</span></span>

<span data-ttu-id="4d952-156">Po použití modelu TensorFlowho zahájení k extrakci funkcí vhodných jako vstup pro klasický algoritmus strojového učení přidáme ML.NET třídění s [více třídami](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="4d952-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="4d952-157">Konkrétní Trainer použitý v tomto případě je [algoritmus MULTINOMIAL logistické regrese](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="4d952-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="4d952-158">Algoritmus implementovaný tímto Trainer se dobře hodí v případě problémů s velkým počtem funkcí, což je případ pro model hloubkového učení, který pracuje s daty imagí.</span><span class="sxs-lookup"><span data-stu-id="4d952-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="4d952-159">Data</span><span class="sxs-lookup"><span data-stu-id="4d952-159">Data</span></span>

<span data-ttu-id="4d952-160">Existují dva zdroje dat: `.tsv` soubor a soubory obrázků.</span><span class="sxs-lookup"><span data-stu-id="4d952-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="4d952-161">`tags.tsv`Soubor obsahuje dva sloupce: první je definována jako `ImagePath` a druhá druhá odpovídá `Label` obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="4d952-162">Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="4d952-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="4d952-163">Obrázky školení a testování se nacházejí ve složkách assetů, které stáhnete do souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="4d952-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="4d952-164">Tyto image patří do Wikimedia.</span><span class="sxs-lookup"><span data-stu-id="4d952-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="4d952-165">*[Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), bezplatné úložiště médií.*</span><span class="sxs-lookup"><span data-stu-id="4d952-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="4d952-166">Načteno 10:48, 17. října 2018 z:<https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear></span><span class="sxs-lookup"><span data-stu-id="4d952-166">Retrieved 10:48, October 17, 2018 from: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
<https://commons.wikimedia.org/wiki/Teddy_bear></span></span>

## <a name="setup"></a><span data-ttu-id="4d952-167">Nastavení</span><span class="sxs-lookup"><span data-stu-id="4d952-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="4d952-168">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="4d952-168">Create a project</span></span>

1. <span data-ttu-id="4d952-169">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="4d952-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="4d952-170">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="4d952-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * <span data-ttu-id="4d952-171">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4d952-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="4d952-172">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="4d952-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="4d952-173">Vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="4d952-173">Select the **Install** button.</span></span>
    * <span data-ttu-id="4d952-174">V dialogovém okně **Náhled změn** vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="4d952-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="4d952-175">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, v dialogu pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="4d952-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="4d952-176">Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics**, **SciSharp. TensorFlow. Redist** a **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="4d952-176">Repeat these steps for **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** and **Microsoft.ML.TensorFlow**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="4d952-177">Stažení prostředků</span><span class="sxs-lookup"><span data-stu-id="4d952-177">Download assets</span></span>

1. <span data-ttu-id="4d952-178">Stáhněte si [soubor zip adresáře Project assets](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="4d952-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="4d952-179">Zkopírujte `assets` adresář do adresáře projektu *TransferLearningTF* .</span><span class="sxs-lookup"><span data-stu-id="4d952-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="4d952-180">Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu zahájení, který si stáhnete a přidáte v dalším kroku) potřebném pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="4d952-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="4d952-181">Stáhněte si [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="4d952-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="4d952-182">Zkopírujte obsah `inception5h` adresáře pouze do složky projektu *TransferLearningTF* `assets/inception` .</span><span class="sxs-lookup"><span data-stu-id="4d952-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="4d952-183">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="4d952-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Obsah adresáře v adresáři](./media/image-classification/inception-files.png)

1. <span data-ttu-id="4d952-185">V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4d952-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="4d952-186">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="4d952-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="4d952-187">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="4d952-187">Create classes and define paths</span></span>

1. <span data-ttu-id="4d952-188">`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="4d952-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/image-classification/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="4d952-189">Přidejte následující kód na řádek přímo nad `Main` metodu pro určení cest prostředků:</span><span class="sxs-lookup"><span data-stu-id="4d952-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](./snippets/image-classification/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="4d952-190">Vytvořte třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="4d952-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](./snippets/image-classification/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="4d952-191">`ImageData`je třída vstupních dat obrázku a obsahuje následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="4d952-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="4d952-192">`ImagePath`obsahuje název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="4d952-193">`Label`obsahuje hodnotu pro popisek obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="4d952-194">Přidejte do projektu novou třídu pro `ImagePrediction` :</span><span class="sxs-lookup"><span data-stu-id="4d952-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](./snippets/image-classification/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="4d952-195">`ImagePrediction`je třída prediktivních imagí a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="4d952-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="4d952-196">`Score`obsahuje procento spolehlivosti pro danou klasifikaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="4d952-197">`PredictedLabelValue`obsahuje hodnotu pro předpokládaný popisek klasifikace obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="4d952-198">`ImagePrediction`je třída použitá pro předpověď po vyškolení modelu.</span><span class="sxs-lookup"><span data-stu-id="4d952-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="4d952-199">Má `string` ( `ImagePath` ) pro cestu k obrázku.</span><span class="sxs-lookup"><span data-stu-id="4d952-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="4d952-200">`Label`Slouží k opakovanému použití a učení modelu.</span><span class="sxs-lookup"><span data-stu-id="4d952-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="4d952-201">`PredictedLabelValue`Je používán během předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="4d952-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="4d952-202">Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.</span><span class="sxs-lookup"><span data-stu-id="4d952-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="4d952-203">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="4d952-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="4d952-204">Inicializujte `mlContext` proměnnou novou instancí `MLContext` .</span><span class="sxs-lookup"><span data-stu-id="4d952-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="4d952-205">Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d952-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](./snippets/image-classification/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="4d952-206">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="4d952-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4d952-207">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4d952-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="4d952-208">Vytvoření struktury pro parametry modelu vytvářené</span><span class="sxs-lookup"><span data-stu-id="4d952-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="4d952-209">Model zahájení má několik parametrů, které je třeba předat.</span><span class="sxs-lookup"><span data-stu-id="4d952-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="4d952-210">Vytvořte strukturu pro mapování hodnot parametrů na popisné názvy pomocí následujícího kódu, a to hned za `Main()` metodou:</span><span class="sxs-lookup"><span data-stu-id="4d952-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](./snippets/image-classification/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="4d952-211">Vytvoření metody zobrazovacího nástroje</span><span class="sxs-lookup"><span data-stu-id="4d952-211">Create a display utility method</span></span>

<span data-ttu-id="4d952-212">Vzhledem k tomu, že zobrazíte data obrázku a související předpovědi více než jednou, vytvořte metodu zobrazení nástrojů pro zpracování zobrazení obrázků a výsledků předpovědi.</span><span class="sxs-lookup"><span data-stu-id="4d952-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="4d952-213">Vytvořte `DisplayResults()` metodu hned za `InceptionSettings` strukturou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4d952-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="4d952-214">Vyplňte text `DisplayResults` metody:</span><span class="sxs-lookup"><span data-stu-id="4d952-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](./snippets/image-classification/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="4d952-215">Vytvoření metody Utility souboru. TSV</span><span class="sxs-lookup"><span data-stu-id="4d952-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="4d952-216">Vytvořte `ReadFromTsv()` metodu hned za `DisplayResults()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4d952-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="4d952-217">Vyplňte text `ReadFromTsv` metody:</span><span class="sxs-lookup"><span data-stu-id="4d952-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](./snippets/image-classification/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="4d952-218">Kód analyzuje `tags.tsv` soubor, aby přidal cestu k souboru bitové kopie pro `ImagePath` vlastnost a načetl ho a `Label` do `ImageData` objektu.</span><span class="sxs-lookup"><span data-stu-id="4d952-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="4d952-219">Vytvoření metody pro předpověď</span><span class="sxs-lookup"><span data-stu-id="4d952-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="4d952-220">Vytvořte `ClassifySingleImage()` metodu těsně před `DisplayResults()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4d952-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="4d952-221">Vytvořte `ImageData` objekt, který obsahuje plně kvalifikovanou cestu a název souboru obrázku pro jednu z nich `ImagePath` .</span><span class="sxs-lookup"><span data-stu-id="4d952-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="4d952-222">Přidejte následující kód jako další řádky v `ClassifySingleImage()` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d952-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](./snippets/image-classification/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="4d952-223">Udělejte jednu předpověď přidáním následujícího kódu jako dalšího řádku v `ClassifySingleImage` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d952-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](./snippets/image-classification/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="4d952-224">K získání předpovědi použijte metodu [předpověď ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) .</span><span class="sxs-lookup"><span data-stu-id="4d952-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="4d952-225">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="4d952-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="4d952-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="4d952-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="4d952-227">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="4d952-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="4d952-228">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4d952-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="4d952-229">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="4d952-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4d952-230">`PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="4d952-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="4d952-231">Zobrazit výsledek předpovědi jako další řádek kódu v `ClassifySingleImage()` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d952-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](./snippets/image-classification/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="4d952-232">Vytvoření kanálu modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d952-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="4d952-233">Kanál ML.NET modelu je řetězec odhady.</span><span class="sxs-lookup"><span data-stu-id="4d952-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="4d952-234">Všimněte si, že během vytváření kanálu nedojde k žádnému spuštění.</span><span class="sxs-lookup"><span data-stu-id="4d952-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="4d952-235">Objekty Estimator jsou vytvořeny, ale nejsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="4d952-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="4d952-236">Přidejte metodu pro vytvoření modelu</span><span class="sxs-lookup"><span data-stu-id="4d952-236">Add a method to generate the model</span></span>

    <span data-ttu-id="4d952-237">Tato metoda je srdcem kurzu.</span><span class="sxs-lookup"><span data-stu-id="4d952-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="4d952-238">Vytvoří kanál pro model a navlakuje kanál k vytvoření modelu ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4d952-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="4d952-239">Vyhodnocuje také model proti dříve nezobrazeným datům testu.</span><span class="sxs-lookup"><span data-stu-id="4d952-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="4d952-240">Vytvořte `GenerateModel()` metodu hned za `InceptionSettings` strukturou a těsně před `DisplayResults()` metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4d952-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="4d952-241">Přidat odhady pro načtení, změnu velikosti a extrakci pixelů z dat obrázku:</span><span class="sxs-lookup"><span data-stu-id="4d952-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](./snippets/image-classification/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="4d952-242">Data obrázku musí být zpracována ve formátu, který očekává model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="4d952-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="4d952-243">V tomto případě jsou obrázky načteny do paměti, jsou změněna na konzistentní velikost a pixely jsou extrahovány do číselného vektoru.</span><span class="sxs-lookup"><span data-stu-id="4d952-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="4d952-244">Přidejte Estimator, abyste načetli model TensorFlow, a zadávejte skóre:</span><span class="sxs-lookup"><span data-stu-id="4d952-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](./snippets/image-classification/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="4d952-245">Tato fáze v kanálu načte model TensorFlow do paměti a pak zpracovává vektor hodnot obrazových bodů prostřednictvím sítě modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="4d952-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="4d952-246">Použití vstupů na model hloubkového učení a generování výstupu pomocí modelu se označuje jako **bodování**.</span><span class="sxs-lookup"><span data-stu-id="4d952-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="4d952-247">Při použití modelu v celém rozsahu je bodování odvozeno nebo předpověď.</span><span class="sxs-lookup"><span data-stu-id="4d952-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="4d952-248">V tomto případě použijete všechen TensorFlow model kromě poslední vrstvy, což je vrstva, která provádí odvození.</span><span class="sxs-lookup"><span data-stu-id="4d952-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="4d952-249">Výstup předposlední vrstvy je označený `softmax_2_preactivation` .</span><span class="sxs-lookup"><span data-stu-id="4d952-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="4d952-250">Výstup této vrstvy je efektivně vektor funkcí, které charakterizují původní vstupní image.</span><span class="sxs-lookup"><span data-stu-id="4d952-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="4d952-251">Tento vektor funkce generovaný modelem TensorFlow se použije jako vstup pro školicí algoritmus ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4d952-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="4d952-252">Přidejte Estimator k namapování popisků řetězce v školicích datech na hodnoty celočíselného klíče:</span><span class="sxs-lookup"><span data-stu-id="4d952-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](./snippets/image-classification/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="4d952-253">ML.NET Trainer, který je připojen k dalšímu, vyžaduje, aby popisky byly ve `key` formátu místo libovolných řetězců.</span><span class="sxs-lookup"><span data-stu-id="4d952-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="4d952-254">Klíč je číslo, které má jeden k jednomu mapování na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="4d952-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="4d952-255">Přidejte ML.NET školicí algoritmus:</span><span class="sxs-lookup"><span data-stu-id="4d952-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](./snippets/image-classification/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="4d952-256">Přidejte Estimator k namapování hodnoty předpovězeného klíče zpátky do řetězce:</span><span class="sxs-lookup"><span data-stu-id="4d952-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](./snippets/image-classification/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="4d952-257">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="4d952-257">Train the model</span></span>

1. <span data-ttu-id="4d952-258">Načtěte školicí data pomocí obálky [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) .</span><span class="sxs-lookup"><span data-stu-id="4d952-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="4d952-259">Přidejte následující kód jako další řádek v `GenerateModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d952-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](./snippets/image-classification/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="4d952-260">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="4d952-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="4d952-261">`IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="4d952-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="4d952-262">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="4d952-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="4d952-263">Vyškolit model s daty načtenými výše:</span><span class="sxs-lookup"><span data-stu-id="4d952-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](./snippets/image-classification/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="4d952-264">`Fit()`Metoda navlakuje váš model použitím školicí datové sady na kanál.</span><span class="sxs-lookup"><span data-stu-id="4d952-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="4d952-265">Vyhodnotit přesnost modelu</span><span class="sxs-lookup"><span data-stu-id="4d952-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="4d952-266">Načtěte a Transformujte testovací data přidáním následujícího kódu na další řádek `GenerateModel` metody:</span><span class="sxs-lookup"><span data-stu-id="4d952-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](./snippets/image-classification/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="4d952-267">Existuje několik ukázkových imagí, které můžete použít k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="4d952-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="4d952-268">Podobně jako u školicích dat je potřeba je načíst do `IDataView` , aby je bylo možné transformovat podle modelu.</span><span class="sxs-lookup"><span data-stu-id="4d952-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="4d952-269">Přidejte následující kód do `GenerateModel()` metody pro vyhodnocení modelu:</span><span class="sxs-lookup"><span data-stu-id="4d952-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](./snippets/image-classification/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="4d952-270">Jakmile máte předsadu předpovědi, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="4d952-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="4d952-271">Vyhodnotí model (porovná předpovězené hodnoty s testovací datovou sadou `labels` ).</span><span class="sxs-lookup"><span data-stu-id="4d952-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="4d952-272">Vrátí metriku výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="4d952-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="4d952-273">Zobrazit metriky přesnosti modelu</span><span class="sxs-lookup"><span data-stu-id="4d952-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="4d952-274">Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:</span><span class="sxs-lookup"><span data-stu-id="4d952-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](./snippets/image-classification/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="4d952-275">Pro klasifikaci imagí jsou vyhodnocovány následující metriky:</span><span class="sxs-lookup"><span data-stu-id="4d952-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="4d952-276">`Log-loss`– viz [ztráta protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="4d952-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="4d952-277">Chcete, aby byla ztráta protokolu co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="4d952-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="4d952-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="4d952-278">`Per class Log-loss`.</span></span> <span data-ttu-id="4d952-279">Požadujete, aby byla ztráta protokolu podle třídy co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="4d952-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="4d952-280">Přidejte následující kód, který vrátí vycvičený model jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="4d952-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](./snippets/image-classification/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="4d952-281">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4d952-281">Run the application!</span></span>

1. <span data-ttu-id="4d952-282">Přidejte volání do `GenerateModel` v `Main` metodě po vytvoření třídy MLContext:</span><span class="sxs-lookup"><span data-stu-id="4d952-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](./snippets/image-classification/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="4d952-283">Přidejte volání `ClassifySingleImage()` metody jako další řádek kódu v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="4d952-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](./snippets/image-classification/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="4d952-284">Spusťte konzolovou aplikaci (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="4d952-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="4d952-285">Výsledky by měly být podobné následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="4d952-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="4d952-286">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="4d952-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="4d952-287">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="4d952-287">Congratulations!</span></span> <span data-ttu-id="4d952-288">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci imagí tím, že použijete učení přenosu na `TensorFlow` model v ml.NET.</span><span class="sxs-lookup"><span data-stu-id="4d952-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="4d952-289">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="4d952-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="4d952-290">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="4d952-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4d952-291">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="4d952-291">Understand the problem</span></span>
> * <span data-ttu-id="4d952-292">Zahrňte předem vyškolený model TensorFlow do kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d952-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="4d952-293">Výuka a vyhodnocení modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d952-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="4d952-294">Klasifikace testovací image</span><span class="sxs-lookup"><span data-stu-id="4d952-294">Classify a test image</span></span>

<span data-ttu-id="4d952-295">Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku klasifikace rozbalené image.</span><span class="sxs-lookup"><span data-stu-id="4d952-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4d952-296">dotnet/machinelearning-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="4d952-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
