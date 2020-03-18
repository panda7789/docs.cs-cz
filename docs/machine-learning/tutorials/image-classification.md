---
title: 'Kurz: ML.NET model klasifikace obrázků od TensorFlow'
description: Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace obrázků ML.NET. Model TensorFlow byl trénován tak, aby klasifikoval obrázky do tisíce kategorií. Model ML.NET využívá přenosučení klasifikovat obrázky do méně širších kategorií.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241023"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="9e52b-105">Kurz: Generování modelu klasifikace obrazu ML.NET z předem vytrénovaného modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="9e52b-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="9e52b-106">Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace obrázků ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9e52b-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="9e52b-107">Model TensorFlow byl trénován tak, aby klasifikoval obrázky do tisíce kategorií.</span><span class="sxs-lookup"><span data-stu-id="9e52b-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="9e52b-108">Model ML.NET využívá část modelu TensorFlow ve svém potrubí k trénování modelu pro klasifikaci obrázků do 3 kategorií.</span><span class="sxs-lookup"><span data-stu-id="9e52b-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="9e52b-109">Trénování modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tuny označených trénovacích dat a obrovské množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="9e52b-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="9e52b-110">I když není tak efektivní jako školení vlastní model od nuly, přenos učení vám umožní zástupce tohoto procesu tím, že pracuje s tisíci obrázků vs miliony označených obrázků a vybudovat vlastní model poměrně rychle (do hodiny na stroji bez GPU).</span><span class="sxs-lookup"><span data-stu-id="9e52b-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="9e52b-111">Tento kurz škáluje tento proces ještě dále, pomocí pouze tucet tréninkových obrázků.</span><span class="sxs-lookup"><span data-stu-id="9e52b-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="9e52b-112">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="9e52b-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9e52b-113">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="9e52b-113">Understand the problem</span></span>
> * <span data-ttu-id="9e52b-114">Začleňte předem vyškolený model TensorFlow do ML.NET potrubí</span><span class="sxs-lookup"><span data-stu-id="9e52b-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="9e52b-115">Trénování a hodnocení ML.NET modelu</span><span class="sxs-lookup"><span data-stu-id="9e52b-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="9e52b-116">Klasifikace testovacího obrázku</span><span class="sxs-lookup"><span data-stu-id="9e52b-116">Classify a test image</span></span>

<span data-ttu-id="9e52b-117">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)</span><span class="sxs-lookup"><span data-stu-id="9e52b-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="9e52b-118">Všimněte si, že ve výchozím nastavení konfigurace projektu .NET pro tento kurz cíle .NET jádro 2.2.</span><span class="sxs-lookup"><span data-stu-id="9e52b-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="9e52b-119">Co je učení přenosu?</span><span class="sxs-lookup"><span data-stu-id="9e52b-119">What is transfer learning?</span></span>

<span data-ttu-id="9e52b-120">Transfer learning je proces využití získaných znalostí při řešení jednoho problému a jeho uplatnění na jiný, ale související problém.</span><span class="sxs-lookup"><span data-stu-id="9e52b-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="9e52b-121">Pro účely tohoto kurzu použijete část modelu TensorFlow - trénovaný pro klasifikaci obrázků do tisíce kategorií - v modelu ML.NET, který klasifikuje obrázky do 3 kategorií.</span><span class="sxs-lookup"><span data-stu-id="9e52b-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e52b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e52b-122">Prerequisites</span></span>

* <span data-ttu-id="9e52b-123">[Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".</span><span class="sxs-lookup"><span data-stu-id="9e52b-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="9e52b-124">Adresář prostředků kurzu . SOUBOR ZIP</span><span class="sxs-lookup"><span data-stu-id="9e52b-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="9e52b-125">Model strojového učení InceptionV1</span><span class="sxs-lookup"><span data-stu-id="9e52b-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="9e52b-126">Výběr správného úkolu strojového učení</span><span class="sxs-lookup"><span data-stu-id="9e52b-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="9e52b-127">Hloubkové učení</span><span class="sxs-lookup"><span data-stu-id="9e52b-127">Deep learning</span></span>

<span data-ttu-id="9e52b-128">[Hluboké učení](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou strojového učení, která přináší revoluci v oblastech, jako je počítačové vidění a rozpoznávání řeči.</span><span class="sxs-lookup"><span data-stu-id="9e52b-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="9e52b-129">Modely hlubokého učení jsou trénované pomocí velkých sad [označených dat](https://en.wikipedia.org/wiki/Labeled_data) a [neuronových sítí,](https://en.wikipedia.org/wiki/Artificial_neural_network) které obsahují více vrstev učení.</span><span class="sxs-lookup"><span data-stu-id="9e52b-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="9e52b-130">Hluboké učení:</span><span class="sxs-lookup"><span data-stu-id="9e52b-130">Deep learning:</span></span>

* <span data-ttu-id="9e52b-131">Funguje lépe na některé úkoly, jako je počítačové vidění.</span><span class="sxs-lookup"><span data-stu-id="9e52b-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="9e52b-132">Vyžaduje obrovské množství trénovacích dat.</span><span class="sxs-lookup"><span data-stu-id="9e52b-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="9e52b-133">Klasifikace obrázků je běžný úkol strojového učení, který nám umožňuje automaticky klasifikovat obrázky do kategorií, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="9e52b-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="9e52b-134">Detekce lidské tváře na obrázku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="9e52b-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="9e52b-135">Detekce koček vs. psi.</span><span class="sxs-lookup"><span data-stu-id="9e52b-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="9e52b-136">Nebo jako na následujících obrázcích, určení, zda je obraz a(n) jídlo, toy, nebo zařízení:</span><span class="sxs-lookup"><span data-stu-id="9e52b-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="9e52b-137">![pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![obrázek](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![medvídek obrázek toaster obrázek](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="9e52b-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="9e52b-138">Předchozí obrázky patří do Wikimedia Commons a jsou připisovány takto:</span><span class="sxs-lookup"><span data-stu-id="9e52b-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="9e52b-139">"220px-Pepperoni_pizza.jpg" Public https://commons.wikimedia.org/w/index.php?curid=79505Domain, ,</span><span class="sxs-lookup"><span data-stu-id="9e52b-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="9e52b-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" Od [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-fotografoval, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="9e52b-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="9e52b-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Vlastní práce, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="9e52b-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="9e52b-142">Je `Inception model` trénovaný pro klasifikaci obrázků do tisíce kategorií, ale pro tento kurz je třeba klasifikovat obrázky v menší sadě kategorií a pouze v těchto kategoriích.</span><span class="sxs-lookup"><span data-stu-id="9e52b-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="9e52b-143">Zadejte `transfer` část `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="9e52b-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="9e52b-144">Schopnost `Inception model`'s rozpoznat a klasifikovat obrázky můžete přenést do nových omezených kategorií vlastního klasifikátoru obrázků.</span><span class="sxs-lookup"><span data-stu-id="9e52b-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="9e52b-145">Potravin</span><span class="sxs-lookup"><span data-stu-id="9e52b-145">Food</span></span>
* <span data-ttu-id="9e52b-146">Hračka</span><span class="sxs-lookup"><span data-stu-id="9e52b-146">Toy</span></span>
* <span data-ttu-id="9e52b-147">Přístroj</span><span class="sxs-lookup"><span data-stu-id="9e52b-147">Appliance</span></span>

<span data-ttu-id="9e52b-148">Tento kurz používá model hlubokého učení modelu TensorFlow [Inception,](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) což je oblíbený model rozpoznávání obrázků trénovaný v `ImageNet` datové sadě.</span><span class="sxs-lookup"><span data-stu-id="9e52b-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="9e52b-149">Model TensorFlow klasifikuje celé obrázky do tisíce tříd, například "Umbrella", "Jersey" a "Myčka nádobí".</span><span class="sxs-lookup"><span data-stu-id="9e52b-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="9e52b-150">Vzhledem `Inception model` k tomu, že již byl předem vyškolen na tisících různých obrázků, interně obsahuje [obrazové funkce](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrazu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="9e52b-151">Můžeme využít těchto interních obrazových prvků v modelu trénovat nový model s mnohem méně tříd.</span><span class="sxs-lookup"><span data-stu-id="9e52b-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="9e52b-152">Jak je znázorněno v následujícím diagramu, přidáte odkaz na ML.NET balíčky NuGet ve vašich aplikacích .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e52b-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="9e52b-153">Pod kryty ML.NET zahrnuje a `TensorFlow` odkazuje na nativní knihovnu, která `TensorFlow` umožňuje psát kód, který načte existující trénovaný soubor modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow transformace ML.NET Obloukový diagram](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="9e52b-155">Klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="9e52b-155">Multiclass classification</span></span>

<span data-ttu-id="9e52b-156">Po použití inceptičního modelu TensorFlow k extrahování funkcí vhodných jako vstup pro klasický algoritmus strojového učení přidáme ML.NET [klasifikátor více tříd](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="9e52b-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="9e52b-157">Specifickým trénem používaným v tomto případě je [multinomický logistický regresní algoritmus](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="9e52b-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="9e52b-158">Algoritmus implementovaný tímto trenérem funguje dobře na problémech s velkým počtem funkcí, což je případ modelu hlubokého učení pracujícího na obrazových datech.</span><span class="sxs-lookup"><span data-stu-id="9e52b-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="9e52b-159">Data</span><span class="sxs-lookup"><span data-stu-id="9e52b-159">Data</span></span>

<span data-ttu-id="9e52b-160">Existují dva zdroje dat: `.tsv` soubor a obrazové soubory.</span><span class="sxs-lookup"><span data-stu-id="9e52b-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="9e52b-161">Soubor `tags.tsv` obsahuje dva sloupce: první je `ImagePath` definován jako a `Label` druhý je odpovídající obrázku.</span><span class="sxs-lookup"><span data-stu-id="9e52b-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="9e52b-162">Následující ukázkový soubor nemá řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="9e52b-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="9e52b-163">Trénovací a testovací obrázky jsou umístěny ve složkách datových zdrojů, které stáhnete do souboru zip.</span><span class="sxs-lookup"><span data-stu-id="9e52b-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="9e52b-164">Tyto obrázky patří Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="9e52b-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="9e52b-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), úložiště svobodných médií.*</span><span class="sxs-lookup"><span data-stu-id="9e52b-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="9e52b-166">Načteno 10:48, říjen 17, 2018 z: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toasterhttps://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="9e52b-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="9e52b-167">Nastavení</span><span class="sxs-lookup"><span data-stu-id="9e52b-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="9e52b-168">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="9e52b-168">Create a project</span></span>

1. <span data-ttu-id="9e52b-169">Vytvořte **aplikaci .NET Core Console** s názvem "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="9e52b-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="9e52b-170">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="9e52b-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="9e52b-171">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9e52b-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="9e52b-172">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="9e52b-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="9e52b-173">Klikněte na rozevírací **seznam Verze,** vyberte balíček **1.4.0** v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="9e52b-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="9e52b-174">V dialogovém okně **Náhled změn** vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="9e52b-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="9e52b-175">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, vyberte v dialogovém okně **Přijetí licence** tlačítko **Souhlasím.**</span><span class="sxs-lookup"><span data-stu-id="9e52b-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="9e52b-176">Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** a **Microsoft.ML.TensorFlow v1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="9e52b-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="9e52b-177">Stažení datových zdrojů</span><span class="sxs-lookup"><span data-stu-id="9e52b-177">Download assets</span></span>

1. <span data-ttu-id="9e52b-178">Stáhnout [soubor zip adresáře datových zdrojů projektu](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)a rozbalit.</span><span class="sxs-lookup"><span data-stu-id="9e52b-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="9e52b-179">Zkopírujte `assets` adresář do adresáře projektu *TransferLearningTF.*</span><span class="sxs-lookup"><span data-stu-id="9e52b-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="9e52b-180">Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu Inception, který stáhnete a přidáte v dalším kroku) potřebnýpro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="9e52b-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="9e52b-181">Stáhněte si [model Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)a rozbalte.</span><span class="sxs-lookup"><span data-stu-id="9e52b-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="9e52b-182">Zkopírujte obsah `inception5h` adresáře, který se právě rozbalil, do adresáře projektu `assets/inception` *TransferLearningTF.*</span><span class="sxs-lookup"><span data-stu-id="9e52b-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="9e52b-183">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="9e52b-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Obsah adresáře pro počátek](./media/image-classification/inception-files.png)

1. <span data-ttu-id="9e52b-185">V Průzkumníku řešení klepněte pravým tlačítkem myši na jednotlivé soubory v adresáři datových zdrojů a podadresářích a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e52b-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="9e52b-186">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="9e52b-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="9e52b-187">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="9e52b-187">Create classes and define paths</span></span>

1. <span data-ttu-id="9e52b-188">Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:</span><span class="sxs-lookup"><span data-stu-id="9e52b-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="9e52b-189">Přidejte následující kód na řádek `Main` přímo nad metodou, abyste určili cesty majetku:</span><span class="sxs-lookup"><span data-stu-id="9e52b-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="9e52b-190">Vytvořte třídy pro vaše vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="9e52b-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="9e52b-191">`ImageData`je třída vstupních obrazových <xref:System.String> dat a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="9e52b-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="9e52b-192">`ImagePath`obsahuje název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="9e52b-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="9e52b-193">`Label`obsahuje hodnotu popisku obrázku.</span><span class="sxs-lookup"><span data-stu-id="9e52b-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="9e52b-194">Přidání nové třídy do `ImagePrediction`projektu pro:</span><span class="sxs-lookup"><span data-stu-id="9e52b-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="9e52b-195">`ImagePrediction`je třída predikce obrázku a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="9e52b-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="9e52b-196">`Score`obsahuje procento spolehlivosti pro danou klasifikaci obrazu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="9e52b-197">`PredictedLabelValue`obsahuje hodnotu pro popisek klasifikace předpovídaného obrázku.</span><span class="sxs-lookup"><span data-stu-id="9e52b-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="9e52b-198">`ImagePrediction`je třída použitá pro předpověď po trénovaném modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="9e52b-199">Má `string` (`ImagePath`) pro cestu obrazu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="9e52b-200">Používá `Label` se k opětovnému použití a trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="9e52b-201">Používá `PredictedLabelValue` se při predikci a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="9e52b-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="9e52b-202">Pro vyhodnocení se používá vstup s trénovacími daty, předpovídanými hodnotami a modelem.</span><span class="sxs-lookup"><span data-stu-id="9e52b-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="9e52b-203">Inicializovat proměnné v hlavní</span><span class="sxs-lookup"><span data-stu-id="9e52b-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="9e52b-204">Inicializovat `mlContext` proměnnou s `MLContext`novou instancí .</span><span class="sxs-lookup"><span data-stu-id="9e52b-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="9e52b-205">Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě: `Main`</span><span class="sxs-lookup"><span data-stu-id="9e52b-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="9e52b-206">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9e52b-207">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="9e52b-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="9e52b-208">Vytvoření struktury pro parametry modelu inception</span><span class="sxs-lookup"><span data-stu-id="9e52b-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="9e52b-209">Inception model má několik parametrů, které je třeba předat.</span><span class="sxs-lookup"><span data-stu-id="9e52b-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="9e52b-210">Vytvořte strukturu pro mapování hodnot parametrů na popisné názvy `Main()` s následujícím kódem, hned za metodou:</span><span class="sxs-lookup"><span data-stu-id="9e52b-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="9e52b-211">Vytvoření metody nástroje zobrazení</span><span class="sxs-lookup"><span data-stu-id="9e52b-211">Create a display utility method</span></span>

<span data-ttu-id="9e52b-212">Vzhledem k tomu, že budete zobrazovat obrazová data a související předpovědi více než jednou, vytvořte metodu nástroje zobrazení pro zpracování zobrazení výsledků obrazu a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="9e52b-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="9e52b-213">Vytvořte `DisplayResults()` metodu, `InceptionSettings` těsně za struct, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="9e52b-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="9e52b-214">Vyplňte tělo `DisplayResults` metody:</span><span class="sxs-lookup"><span data-stu-id="9e52b-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="9e52b-215">Vytvoření metody nástroje pro vytvoření souboru TSV</span><span class="sxs-lookup"><span data-stu-id="9e52b-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="9e52b-216">Vytvořte `ReadFromTsv()` metodu, `DisplayResults()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="9e52b-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="9e52b-217">Vyplňte tělo `ReadFromTsv` metody:</span><span class="sxs-lookup"><span data-stu-id="9e52b-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="9e52b-218">Kód `tags.tsv` analyzuje soubor přidat cestu k názvu souboru obrazu pro `ImagePath` vlastnost a načíst ji a `Label` do objektu. `ImageData`</span><span class="sxs-lookup"><span data-stu-id="9e52b-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="9e52b-219">Vytvoření metody pro vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="9e52b-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="9e52b-220">Vytvořte `ClassifySingleImage()` metodu, `DisplayResults()` těsně před metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="9e52b-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="9e52b-221">Vytvořte `ImageData` objekt, který obsahuje plně kvalifikovanou cestu `ImagePath`a název souboru obrázku pro singl .</span><span class="sxs-lookup"><span data-stu-id="9e52b-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="9e52b-222">Jako další řádky metody `ClassifySingleImage()` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9e52b-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="9e52b-223">Proveďte jednu předpověď přidáním následujícího kódu `ClassifySingleImage` jako následující řádek v metodě:</span><span class="sxs-lookup"><span data-stu-id="9e52b-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="9e52b-224">Chcete-li získat předpověď, použijte [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) metoda.</span><span class="sxs-lookup"><span data-stu-id="9e52b-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="9e52b-225">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="9e52b-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="9e52b-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="9e52b-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="9e52b-227">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="9e52b-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="9e52b-228">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9e52b-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="9e52b-229">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="9e52b-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9e52b-230">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="9e52b-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="9e52b-231">Zobrazit výsledek předpovědi jako další řádek `ClassifySingleImage()` kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="9e52b-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="9e52b-232">Konstrukce kanálu modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="9e52b-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="9e52b-233">Potrubí modelu ML.NET je řetězec odhadů.</span><span class="sxs-lookup"><span data-stu-id="9e52b-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="9e52b-234">Všimněte si, že žádné spuštění se stane během výstavby kanálu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="9e52b-235">Objekty odhadu jsou vytvořeny, ale nejsou provedeny.</span><span class="sxs-lookup"><span data-stu-id="9e52b-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="9e52b-236">Přidání metody pro generování modelu</span><span class="sxs-lookup"><span data-stu-id="9e52b-236">Add a method to generate the model</span></span>

    <span data-ttu-id="9e52b-237">Tato metoda je srdcem výukového programu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="9e52b-238">Vytvoří kanál pro model a trénuje potrubí k výrobě modelu ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9e52b-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="9e52b-239">Také vyhodnotí model proti některé dříve neviditelné testovací data.</span><span class="sxs-lookup"><span data-stu-id="9e52b-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="9e52b-240">Vytvořte `GenerateModel()` metodu, `InceptionSettings` těsně za strukturou `DisplayResults()` a těsně před metodou pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="9e52b-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="9e52b-241">Přidejte odhady k načtení, změně velikosti a extrahování obrazových bodů z obrazových dat:</span><span class="sxs-lookup"><span data-stu-id="9e52b-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="9e52b-242">Obrazová data musí být zpracována do formátu, který očekává model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="9e52b-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="9e52b-243">V tomto případě jsou obrazy načteny do paměti, zmenšeny na konzistentní velikost a obrazové body jsou extrahovány do číselného vektoru.</span><span class="sxs-lookup"><span data-stu-id="9e52b-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="9e52b-244">Přidejte odhad pro načtení modelu TensorFlow a jeho skóre:</span><span class="sxs-lookup"><span data-stu-id="9e52b-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="9e52b-245">Tato fáze v kanálu načte model TensorFlow do paměti a pak zpracuje vektor hodnot pixelů prostřednictvím sítě modelů TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="9e52b-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="9e52b-246">Použití vstupů na model hlubokého učení a generování výstupu pomocí modelu se označuje jako **vyhodnocování**.</span><span class="sxs-lookup"><span data-stu-id="9e52b-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="9e52b-247">Při použití modelu v plném rozsahu, bodování provede odvození nebo předpověď.</span><span class="sxs-lookup"><span data-stu-id="9e52b-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="9e52b-248">V tomto případě použijete celý model TensorFlow s výjimkou poslední vrstvy, což je vrstva, která provádí odvození.</span><span class="sxs-lookup"><span data-stu-id="9e52b-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="9e52b-249">Výstup předposlední vrstvy je `softmax_2_preactivation`označen .</span><span class="sxs-lookup"><span data-stu-id="9e52b-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="9e52b-250">Výstup této vrstvy je účinně vektor prvků, které charakterizují původní vstupní obrazy.</span><span class="sxs-lookup"><span data-stu-id="9e52b-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="9e52b-251">Tento vektor funkce generovaný modelem TensorFlow bude použit jako vstup do ML.NET trénovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="9e52b-252">Přidejte odhad k mapování popisků řetězců v trénovacích datech na hodnoty celého klíče:</span><span class="sxs-lookup"><span data-stu-id="9e52b-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="9e52b-253">ML.NET, který je připojen další vyžaduje, `key` aby jeho popisky být ve formátu, nikoli libovolné řetězce.</span><span class="sxs-lookup"><span data-stu-id="9e52b-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="9e52b-254">Klíč je číslo, které má mapování 1:1 na řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="9e52b-255">Přidejte ML.NET tréninkový algoritmus:</span><span class="sxs-lookup"><span data-stu-id="9e52b-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="9e52b-256">Přidejte odhad, chcete-li předpovědět hodnotu klíče namapovat zpět do řetězce:</span><span class="sxs-lookup"><span data-stu-id="9e52b-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="9e52b-257">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="9e52b-257">Train the model</span></span>

1. <span data-ttu-id="9e52b-258">Načtěte trénovací data pomocí obálky [LoadFromTextFile.](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options))</span><span class="sxs-lookup"><span data-stu-id="9e52b-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="9e52b-259">Jako další řádek `GenerateModel()` metody přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9e52b-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="9e52b-260">Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="9e52b-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="9e52b-261">`IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových).</span><span class="sxs-lookup"><span data-stu-id="9e52b-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="9e52b-262">Data lze načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu. `IDataView`</span><span class="sxs-lookup"><span data-stu-id="9e52b-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="9e52b-263">Trénování modelu s výše načtenými daty:</span><span class="sxs-lookup"><span data-stu-id="9e52b-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="9e52b-264">Metoda `Fit()` trénuje váš model použitím trénovací datové sady na kanál.</span><span class="sxs-lookup"><span data-stu-id="9e52b-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="9e52b-265">Vyhodnocení přesnosti modelu</span><span class="sxs-lookup"><span data-stu-id="9e52b-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="9e52b-266">Načtěte a transformujte testovací data přidáním následujícího `GenerateModel` kódu do dalšího řádku metody:</span><span class="sxs-lookup"><span data-stu-id="9e52b-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="9e52b-267">Existuje několik ukázkových obrázků, které můžete použít k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="9e52b-268">Stejně jako trénovací data, `IDataView`tyto musí být načteny do , tak, aby mohly být transformovány podle modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="9e52b-269">Přidejte do metody `GenerateModel()` následující kód pro vyhodnocení modelu:</span><span class="sxs-lookup"><span data-stu-id="9e52b-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="9e52b-270">Jakmile máte předpověď nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda:</span><span class="sxs-lookup"><span data-stu-id="9e52b-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="9e52b-271">Vyhodnotí model (porovná předpovídané hodnoty s `labels`testovací datovou sadou ).</span><span class="sxs-lookup"><span data-stu-id="9e52b-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="9e52b-272">Vrátí metriky výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="9e52b-273">Zobrazení metrik přesnosti modelu</span><span class="sxs-lookup"><span data-stu-id="9e52b-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="9e52b-274">Pomocí následujícího kódu můžete zobrazit metriky, sdílet výsledky a pak s nimi jednat:</span><span class="sxs-lookup"><span data-stu-id="9e52b-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="9e52b-275">Pro klasifikaci obrázků jsou vyhodnoceny následující metriky:</span><span class="sxs-lookup"><span data-stu-id="9e52b-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="9e52b-276">`Log-loss`- viz [Ztráta protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="9e52b-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="9e52b-277">Chcete, aby ztráta protokolu byla co nejblíže nule.</span><span class="sxs-lookup"><span data-stu-id="9e52b-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="9e52b-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="9e52b-278">`Per class Log-loss`.</span></span> <span data-ttu-id="9e52b-279">Chcete, aby ztráta protokolu na třídu byla co nejblíže nule.</span><span class="sxs-lookup"><span data-stu-id="9e52b-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="9e52b-280">Přidejte následující kód, který vrátí trénovaný model jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="9e52b-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="9e52b-281">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9e52b-281">Run the application!</span></span>

1. <span data-ttu-id="9e52b-282">Přidejte volání `GenerateModel` do `Main` metody po vytvoření třídy MLContext:</span><span class="sxs-lookup"><span data-stu-id="9e52b-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="9e52b-283">Přidejte volání `ClassifySingleImage()` metody jako další řádek kódu `Main` v metodě:</span><span class="sxs-lookup"><span data-stu-id="9e52b-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="9e52b-284">Spusťte konzolovou aplikaci (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="9e52b-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="9e52b-285">Výsledky by měly být podobné následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="9e52b-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="9e52b-286">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="9e52b-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="9e52b-287">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="9e52b-287">Congratulations!</span></span> <span data-ttu-id="9e52b-288">Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci `TensorFlow` obrázků použitím učení přenosu na model v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9e52b-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="9e52b-289">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)</span><span class="sxs-lookup"><span data-stu-id="9e52b-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="9e52b-290">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="9e52b-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9e52b-291">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="9e52b-291">Understand the problem</span></span>
> * <span data-ttu-id="9e52b-292">Začleňte předem vyškolený model TensorFlow do ML.NET potrubí</span><span class="sxs-lookup"><span data-stu-id="9e52b-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="9e52b-293">Trénování a hodnocení ML.NET modelu</span><span class="sxs-lookup"><span data-stu-id="9e52b-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="9e52b-294">Klasifikace testovacího obrázku</span><span class="sxs-lookup"><span data-stu-id="9e52b-294">Classify a test image</span></span>

<span data-ttu-id="9e52b-295">Podívejte se na ukázky Machine Learning úložiště GitHub prozkoumat rozbalené ukázky klasifikace obrázků.</span><span class="sxs-lookup"><span data-stu-id="9e52b-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9e52b-296">úložiště GitHub u dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="9e52b-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
