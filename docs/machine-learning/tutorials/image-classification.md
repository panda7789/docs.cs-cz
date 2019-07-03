---
title: 'Kurz: Třídění image obsloužených TensorFlow - learningu'
description: Zjistěte, jak přeučování TensorFlow model klasifikace obrázků s využitím learningu a ML.NET. Původní model se trénuje klasifikovat jednotlivých obrázků. Po přetrénování, nový model slouží k uspořádání obrázků do kategorií.
ms.date: 06/12/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 9344d0757e140995dfd9ce7d1a355910a81c6d31
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539853"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="d22d3-105">Kurz: Přeučování klasifikátor TensorFlow image s learningu a ML.NET</span><span class="sxs-lookup"><span data-stu-id="d22d3-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="d22d3-106">Zjistěte, jak přeučování TensorFlow model klasifikace obrázků s využitím learningu a ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d22d3-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="d22d3-107">Původní model se trénuje klasifikovat jednotlivých obrázků.</span><span class="sxs-lookup"><span data-stu-id="d22d3-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="d22d3-108">Po přetrénování, nový model slouží k uspořádání obrázků do kategorií.</span><span class="sxs-lookup"><span data-stu-id="d22d3-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="d22d3-109">Školení [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model úplně od začátku vyžaduje nastavení miliony parametry, spoustu s popiskem trénovacích dat a velké množství výpočetních prostředků (vzdálené stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="d22d3-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="d22d3-110">Přestože není tak účinné jako trénujete model pro vlastní úplně od začátku, learningu vám umožní místní tento proces při práci s tisíci imagí a miliony označené obrázky a poměrně rychle vytvářet vlastní model (za hodinu na počítači bez GPU).</span><span class="sxs-lookup"><span data-stu-id="d22d3-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="d22d3-111">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="d22d3-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d22d3-112">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="d22d3-112">Understand the problem</span></span>
> * <span data-ttu-id="d22d3-113">Opakovaně používat a vyladit předem natrénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="d22d3-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="d22d3-114">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="d22d3-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="d22d3-115">Co je přenos učení?</span><span class="sxs-lookup"><span data-stu-id="d22d3-115">What is transfer learning?</span></span>

<span data-ttu-id="d22d3-116">Co když můžete znovu použít model, který již byl před vyškolit tak, aby podobný problém vyřešit a přeučování všechny nebo některé z vrstev tento model, aby byl váš problém vyřešit?</span><span class="sxs-lookup"><span data-stu-id="d22d3-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="d22d3-117">Opětovné použití součást již trénovaného modelu vytvoříte nový model Tato technika se nazývá [přenos learning](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="d22d3-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="d22d3-118">Přehled ukázky klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="d22d3-118">Image classification sample overview</span></span>

<span data-ttu-id="d22d3-119">Ukázka je konzolová aplikace, která používá ML.NET k sestavení třídění image opětovným použitím předem vytrénovaných model pro klasifikaci obrázků s menším objemem trénovací data.</span><span class="sxs-lookup"><span data-stu-id="d22d3-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="d22d3-120">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) úložiště.</span><span class="sxs-lookup"><span data-stu-id="d22d3-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="d22d3-121">Všimněte si, že ve výchozím nastavení, zaměřuje .NET konfigurace projektu pro účely tohoto kurzu .NET core 2.2.</span><span class="sxs-lookup"><span data-stu-id="d22d3-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d22d3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d22d3-122">Prerequisites</span></span>

* <span data-ttu-id="d22d3-123">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d22d3-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="d22d3-124">Balíček Nuget Microsoft.ML 1.0.0</span><span class="sxs-lookup"><span data-stu-id="d22d3-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="d22d3-125">Balíček Nuget Microsoft.ML.ImageAnalytics 1.0.0</span><span class="sxs-lookup"><span data-stu-id="d22d3-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="d22d3-126">Balíček Nuget Microsoft.ML.TensorFlow 0.12.0</span><span class="sxs-lookup"><span data-stu-id="d22d3-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="d22d3-127">Adresář, který kurzů aktiv. Soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="d22d3-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="d22d3-128">Model InceptionV3 strojového učení</span><span class="sxs-lookup"><span data-stu-id="d22d3-128">The InceptionV3 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="d22d3-129">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="d22d3-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="d22d3-130">[Obsáhlý learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, která je revolutionizing oblastem, jako pro počítačové zpracování obrazu a řeči.</span><span class="sxs-lookup"><span data-stu-id="d22d3-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="d22d3-131">Obsáhlý learning jsou trénované modely s využitím velkých sad [označené data](https://en.wikipedia.org/wiki/Labeled_data) a [neuronových sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více vrstev učení.</span><span class="sxs-lookup"><span data-stu-id="d22d3-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="d22d3-132">Obsáhlý learning:</span><span class="sxs-lookup"><span data-stu-id="d22d3-132">Deep learning:</span></span>

* <span data-ttu-id="d22d3-133">Na některé úkoly, jako je pro počítačové zpracování obrazu vrací lepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="d22d3-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="d22d3-134">Provádí také data obrovské objemy.</span><span class="sxs-lookup"><span data-stu-id="d22d3-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="d22d3-135">Klasifikace obrázků je běžný úkol Machine Learning, která umožňuje automaticky klasifikovat bitové kopie do více kategorií, jako například:</span><span class="sxs-lookup"><span data-stu-id="d22d3-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="d22d3-136">Detekuje lidské tváře v obrázku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="d22d3-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="d22d3-137">Zjišťování koček a psů.</span><span class="sxs-lookup"><span data-stu-id="d22d3-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="d22d3-138">Nebo jako v následujících imagí zjištění, zda je bitová kopie položku food, hračka nebo zařízení:</span><span class="sxs-lookup"><span data-stu-id="d22d3-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="d22d3-139">![Obrázek pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![míša opatřeny image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="d22d3-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="d22d3-140">Předchozí obrázky Commons o Wikimedia patří a mají atributy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d22d3-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="d22d3-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="d22d3-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="d22d3-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" podle [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) -svým fotografovali kopie BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="d22d3-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="d22d3-143">"193px-Broodrooster.jpg" podle [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) – vlastní práci, CC BY SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="d22d3-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="d22d3-144">Přenos learning obsahuje několik strategií, jako například *přeučování všechny vrstvy* a *předposlední vrstvy*.</span><span class="sxs-lookup"><span data-stu-id="d22d3-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="d22d3-145">V tomto kurzu se vysvětlují, ukazují, jak používat *předposlední vrstvy strategie*.</span><span class="sxs-lookup"><span data-stu-id="d22d3-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="d22d3-146">*Předposlední vrstvy strategie* opětovně používá model, který je již předběžně školení k vyřešení konkrétního problému.</span><span class="sxs-lookup"><span data-stu-id="d22d3-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="d22d3-147">Strategie pak retrains poslední vrstva tohoto modelu k němu nový problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="d22d3-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="d22d3-148">Opětovné použití předem natrénovaných modelů jako součást nového modelu vám ušetří spoustu času a prostředků.</span><span class="sxs-lookup"><span data-stu-id="d22d3-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="d22d3-149">Opětovně používá model klasifikace obrázků [vzniku modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), model rozpoznávání image Oblíbené trénovaných na `ImageNet` datovou sadu, ve kterém modelu TensorFlow pokusí o klasifikaci celého Image na tisíc třídy, jako je třeba " Zastřešující","Jersey"a"Nádobí".</span><span class="sxs-lookup"><span data-stu-id="d22d3-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="d22d3-150">`Inception v3 model` Dají považovat za [hluboké konvoluční neuronové sítě](https://en.wikipedia.org/wiki/Convolutional_neural_network) a dosáhnout adekvátní výkon na pevné visual rozpoznávání úloh, odpovídající nebo překročení lidské výkonu v některé domény.</span><span class="sxs-lookup"><span data-stu-id="d22d3-150">The `Inception v3 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="d22d3-151">/ Algoritmem modelu byla vypracovanou organizací cccppf více výzkumní pracovníci a podle původního dokumentu: ["Jiný pohled na architekturu zahájení pro počítačové zpracování obrazu" podle Szegedy, et. Al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="d22d3-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="d22d3-152">Protože `Inception model` již byl před trénovaných na tisíce jinou Image, obsahuje [obrázku funkce](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné k identifikaci image.</span><span class="sxs-lookup"><span data-stu-id="d22d3-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="d22d3-153">Nižších vrstvách funkce image rozpoznat jednoduché funkce (například okraje) a vyšší vrstvy rozpoznávání podobě komplexních funkcí (jako je například tvary).</span><span class="sxs-lookup"><span data-stu-id="d22d3-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="d22d3-154">Poslední vrstva se trénuje proti mnohem menší sady dat, vzhledem k tomu, že začínáte s pre trénovaného modelu, která již analyzuje jak klasifikovat bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d22d3-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="d22d3-155">Jako model umožňuje klasifikovat více než dvě kategorie, toto je příklad [roc třídění](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="d22d3-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="d22d3-156">`TensorFlow` je oblíbená obsáhlého learningu a nástrojů strojového učení pro školení hluboké neuronové sítě (a obecné numerické výpočty) a je implementovaný jako `transformer` v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d22d3-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="d22d3-157">V tomto kurzu se používá pro opětovné použití `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="d22d3-158">Jak je znázorněno v následujícím diagramu, přidejte odkaz na balíčky ML.NET NuGet v aplikacích .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d22d3-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="d22d3-159">Pod pokličkou, ML.NET zahrnuje a odkazuje na nativní `TensorFlow` knihovnu, která umožňuje napsat kód, který načte existující školení `TensorFlow` souboru modelu pro vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="d22d3-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Transformace TensorFlow ML.NET Arch diagramu](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="d22d3-161">`Inception model` Trénovaných ke klasifikaci obrázků do tisíce kategorií, ale je potřeba klasifikace obrázků v menší sadu kategorií a pouze tyto kategorie.</span><span class="sxs-lookup"><span data-stu-id="d22d3-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="d22d3-162">Zadejte `transfer` součástí `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="d22d3-163">Můžete převést `Inception model`vaší schopnost rozpoznat a klasifikace obrázků na nové omezené kategorie klasifikátoru vlastní image.</span><span class="sxs-lookup"><span data-stu-id="d22d3-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="d22d3-164">Chystáte se přeučování poslední vrstva tohoto modelu používáte sadu tří kategorií:</span><span class="sxs-lookup"><span data-stu-id="d22d3-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="d22d3-165">Potravinářství</span><span class="sxs-lookup"><span data-stu-id="d22d3-165">Food</span></span>
* <span data-ttu-id="d22d3-166">Hračka</span><span class="sxs-lookup"><span data-stu-id="d22d3-166">Toy</span></span>
* <span data-ttu-id="d22d3-167">Zařízení</span><span class="sxs-lookup"><span data-stu-id="d22d3-167">Appliance</span></span>

<span data-ttu-id="d22d3-168">Používá vaše vrstvy [algoritmu logistické regrese multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) co nejrychleji najít správnou kategorii.</span><span class="sxs-lookup"><span data-stu-id="d22d3-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="d22d3-169">Tento algoritmus klasifikuje pomocí pravděpodobnosti určit odpověď, poskytuje jednu hodnotu na správnou kategorii a nulová hodnota ostatním.</span><span class="sxs-lookup"><span data-stu-id="d22d3-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="d22d3-170">DataSet</span><span class="sxs-lookup"><span data-stu-id="d22d3-170">DataSet</span></span>

<span data-ttu-id="d22d3-171">Existují dva zdroje dat: `.tsv` souborů a souborů obrázků.</span><span class="sxs-lookup"><span data-stu-id="d22d3-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="d22d3-172">`tags.tsv` Soubor obsahuje dva sloupce: první z nich je definován jako `ImagePath` a druhý je `Label` odpovídající do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d22d3-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="d22d3-173">Následující příklad souboru nemá řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="d22d3-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="d22d3-174">Trénovací a testovací bitové kopie jsou umístěny ve složkách prostředky, které budete stáhnout jako soubor zip.</span><span class="sxs-lookup"><span data-stu-id="d22d3-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="d22d3-175">Tyto Image patří do Commons o Wikimedia.</span><span class="sxs-lookup"><span data-stu-id="d22d3-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="d22d3-176">*[Commons o Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), úložiště volných médií.*</span><span class="sxs-lookup"><span data-stu-id="d22d3-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="d22d3-177">Načtená 10:48, 17. října 2018 od:</span><span class="sxs-lookup"><span data-stu-id="d22d3-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="d22d3-178">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="d22d3-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="d22d3-179">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="d22d3-179">Create a project</span></span>

1. <span data-ttu-id="d22d3-180">Vytvoření **konzolovou aplikaci .NET Core** nazývá "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="d22d3-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="d22d3-181">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="d22d3-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d22d3-182">V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d22d3-183">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="d22d3-184">Klikněte na **verze** rozevíracího seznamu, vyberte **1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d22d3-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d22d3-185">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="d22d3-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="d22d3-186">Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics v1.0.0** a **Microsoft.ML.TensorFlow v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="d22d3-187">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="d22d3-187">Prepare your data</span></span>

1. <span data-ttu-id="d22d3-188">Stáhněte si [souboru zip projektu prostředků adresáře](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="d22d3-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="d22d3-189">Kopírovat `assets` adresáře do vašeho *TransferLearningTF* adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="d22d3-190">Tento adresář a jeho podadresářích obsahovat soubory dat a podporu (s výjimkou vzniku modelu, který budete stáhnout a přidat v dalším kroku) pro tento kurz potřeba.</span><span class="sxs-lookup"><span data-stu-id="d22d3-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="d22d3-191">Stáhněte si [vzniku modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="d22d3-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="d22d3-192">Zkopírujte obsah `inception5h` rozzipoval. stačí do adresáře vašeho *TransferLearningTF* projektu `assets\inputs-train\inception` adresáře.</span><span class="sxs-lookup"><span data-stu-id="d22d3-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="d22d3-193">Tento adresář obsahuje model a další podpůrné soubory pro tento kurz potřeba, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="d22d3-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Obsah adresáře zahájení](./media/image-classification/inception-files.png)

5. <span data-ttu-id="d22d3-195">V Průzkumníku řešení klikněte pravým tlačítkem myši na každém ze souborů v majetku adresáře a podadresářů a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="d22d3-196">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d22d3-197">Vytváření tříd a definovat cesty</span><span class="sxs-lookup"><span data-stu-id="d22d3-197">Create classes and define paths</span></span>

<span data-ttu-id="d22d3-198">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="d22d3-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="d22d3-199">Vytvořte globální pole pro uložení cest k různým prostředkům a globálních proměnných pro `LabelTokey`,`ImageReal`, a `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="d22d3-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="d22d3-200">`_assetsPath` obsahuje cestu k prostředky.</span><span class="sxs-lookup"><span data-stu-id="d22d3-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="d22d3-201">`_trainTagsTsv` má cestu k souboru tsv školení image data značek.</span><span class="sxs-lookup"><span data-stu-id="d22d3-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="d22d3-202">`_predictTagsTsv` má cestu k souboru tsv předpovědi image data značek.</span><span class="sxs-lookup"><span data-stu-id="d22d3-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="d22d3-203">`_trainImagesFolder` obsahuje v cestě k obrázkům využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="d22d3-204">`_predictImagesFolder` obsahuje v cestě k obrázkům zařazují trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="d22d3-205">`_inceptionPb` obsahuje cestu k předem vytrénovaných vzniku model znovu použije k přeučování modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="d22d3-206">`_inputImageClassifierZip` má cesta kde trénovaný model je načtený z.</span><span class="sxs-lookup"><span data-stu-id="d22d3-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="d22d3-207">`_outputImageClassifierZip` obsahuje cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="d22d3-208">`LabelTokey` je `Label` hodnotu namapovány na klíče.</span><span class="sxs-lookup"><span data-stu-id="d22d3-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="d22d3-209">`ImageReal`  je sloupec obsahující hodnotu předpokládané obrázku.</span><span class="sxs-lookup"><span data-stu-id="d22d3-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="d22d3-210">`PredictedLabelValue` je sloupec obsahující hodnoty předpovězené popisku.</span><span class="sxs-lookup"><span data-stu-id="d22d3-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="d22d3-211">Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="d22d3-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="d22d3-212">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="d22d3-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="d22d3-213">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="d22d3-214">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d22d3-215">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d22d3-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="d22d3-216">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d22d3-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d22d3-217">*ImageData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d22d3-218">Přidejte následující `using` příkaz do horní části *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="d22d3-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="d22d3-219">Odeberte stávající definice třídy a přidejte následující kód `ImageData` třídu *ImageData.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="d22d3-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="d22d3-220">`ImageData` je třída dat vstupního obrázku a má následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="d22d3-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="d22d3-221">`ImagePath` obsahuje název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="d22d3-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="d22d3-222">`Label` obsahuje hodnotu pro popisek image.</span><span class="sxs-lookup"><span data-stu-id="d22d3-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="d22d3-223">Přidejte novou třídu do projektu pro `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="d22d3-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="d22d3-224">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d22d3-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d22d3-225">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="d22d3-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="d22d3-226">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d22d3-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d22d3-227">*ImagePrediction.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="d22d3-228">Odebrat i `System.Collections.Generic` a `System.Text` `using` příkazů v horní části *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="d22d3-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="d22d3-229">Odeberte stávající definice třídy a přidejte následující kód, který má `ImagePrediction` do třídy *ImagePrediction.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="d22d3-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="d22d3-230">`ImagePrediction` je třída prediktivní vkládání obrázků a obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="d22d3-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="d22d3-231">`Score` obsahuje procento spolehlivosti pro danou image klasifikaci.</span><span class="sxs-lookup"><span data-stu-id="d22d3-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="d22d3-232">`PredictedLabelValue` obsahuje hodnotu pro popisek klasifikace předpokládané image.</span><span class="sxs-lookup"><span data-stu-id="d22d3-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="d22d3-233">`ImagePrediction` Třída slouží k předpovědi po model se trénuje.</span><span class="sxs-lookup"><span data-stu-id="d22d3-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="d22d3-234">Má `string` (`ImagePath`) pro cestu k obrázku.</span><span class="sxs-lookup"><span data-stu-id="d22d3-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="d22d3-235">`Label` Se používá pro opětovné použití přeučování modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="d22d3-236">`PredictedLabelValue` Se používá při předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="d22d3-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="d22d3-237">Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.</span><span class="sxs-lookup"><span data-stu-id="d22d3-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="d22d3-238">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d22d3-239">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d22d3-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d22d3-240">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="d22d3-240">Initialize variables in Main</span></span>

<span data-ttu-id="d22d3-241">Inicializovat `mlContext` proměnné s novou instanci třídy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="d22d3-242">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="d22d3-243">Vytvořte strukturu pro výchozí parametry</span><span class="sxs-lookup"><span data-stu-id="d22d3-243">Create a struct for default parameters</span></span>

<span data-ttu-id="d22d3-244">Zahájení model má několik výchozích parametrů, které je potřeba předat.</span><span class="sxs-lookup"><span data-stu-id="d22d3-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="d22d3-245">Vytvořte strukturu pro mapování výchozí hodnoty parametrů pro popisných názvů následujícím kódem, bezprostředně po `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="d22d3-246">Vytvořit metodu nástroj zobrazení</span><span class="sxs-lookup"><span data-stu-id="d22d3-246">Create a display utility method</span></span>

<span data-ttu-id="d22d3-247">Vzhledem k tomu, že budete více než jednou zobrazovat obrazová data a související predikcí, vytvořte metodu zobrazení nástroj pro zpracování zobrazení výsledků image a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="d22d3-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="d22d3-248">`DisplayResults()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="d22d3-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="d22d3-249">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="d22d3-249">Displays the predicted results.</span></span>

<span data-ttu-id="d22d3-250">Vytvořte `DisplayResults()` metoda, hned za `InceptionSettings` struktury, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="d22d3-251">`Transform()` Metoda vyplní `ImagePath` v `ImagePrediction` spolu s předpokládanou pole.</span><span class="sxs-lookup"><span data-stu-id="d22d3-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="d22d3-252">V průběhu procesu ML.NET jednotlivých komponent přidá sloupce, a to usnadňuje zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="d22d3-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="d22d3-253">Budete volat `DisplayResults()` metoda v metodách klasifikace dvě image.</span><span class="sxs-lookup"><span data-stu-id="d22d3-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="d22d3-254">Vytvořit metodu nástroj soubor TSV</span><span class="sxs-lookup"><span data-stu-id="d22d3-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="d22d3-255">`ReadFromTsv()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="d22d3-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="d22d3-256">Přečte data bitové kopie `tags.tsv` souboru.</span><span class="sxs-lookup"><span data-stu-id="d22d3-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="d22d3-257">Cesta k souboru se přidá k názvu souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d22d3-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="d22d3-258">Načte datový soubor do použití rozhraní IEnumerable`ImageData` objektu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="d22d3-259">Vytvořte `ReadFromTsv()` metoda, hned za `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="d22d3-260">Následující kód analyzuje prostřednictvím `tags.tsv` soubor a přidejte cestu k souboru na název souboru obrázku `ImagePath` vlastnost a načtěte ho a `Label` do `ImageData` objektu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="d22d3-261">Přidejte jako první řádek `ReadFromTsv()` metody.</span><span class="sxs-lookup"><span data-stu-id="d22d3-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="d22d3-262">Budete potřebovat plně kvalifikovanou cestu k zobrazení výsledků předpovědí.</span><span class="sxs-lookup"><span data-stu-id="d22d3-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="d22d3-263">Existují tři hlavní koncepty v ML.NET: [Data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer), a [odhady](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="d22d3-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="d22d3-264">Opakovaně používat a vyladit předem natrénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="d22d3-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="d22d3-265">Přidejte následující volání `ReuseAndTuneInceptionModel()`metody jako další řádek kódu v `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="d22d3-266">`ReuseAndTuneInceptionModel()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="d22d3-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="d22d3-267">Načte data</span><span class="sxs-lookup"><span data-stu-id="d22d3-267">Loads the data</span></span>
* <span data-ttu-id="d22d3-268">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="d22d3-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="d22d3-269">Stanoví skóre TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="d22d3-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="d22d3-270">Vyladí (retrains) modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="d22d3-271">Zobrazí výsledky modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-271">Displays model results.</span></span>
* <span data-ttu-id="d22d3-272">Vyhodnotí modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-272">Evaluates the model.</span></span>
* <span data-ttu-id="d22d3-273">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-273">Returns the model.</span></span>

<span data-ttu-id="d22d3-274">Vytvořit `ReuseAndTuneInceptionModel()` metoda, hned za `InceptionSettings` struktury a těsně před `DisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="d22d3-275">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="d22d3-275">Load the data</span></span>

<span data-ttu-id="d22d3-276">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="d22d3-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d22d3-277">`IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="d22d3-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="d22d3-278">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="d22d3-279">Načtení dat pomocí `MLContext.Data.LoadFromTextFile` obálky.</span><span class="sxs-lookup"><span data-stu-id="d22d3-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="d22d3-280">Přidejte následující kód jako další řádek `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="d22d3-281">Extrakce funkce a transformaci dat</span><span class="sxs-lookup"><span data-stu-id="d22d3-281">Extract Features and transform the data</span></span>

<span data-ttu-id="d22d3-282">Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning.</span><span class="sxs-lookup"><span data-stu-id="d22d3-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="d22d3-283">Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="d22d3-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="d22d3-284">Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) dat, a při práci s hluboké neuronové sítě musí přizpůsobit imagí do formátu očekávaném v síti.</span><span class="sxs-lookup"><span data-stu-id="d22d3-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="d22d3-285">Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="d22d3-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="d22d3-286">Po trénování a hodnocení předpovědět **popisek** hodnot sloupců.</span><span class="sxs-lookup"><span data-stu-id="d22d3-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="d22d3-287">Jak při použití předem natrénovaných modelů, mapování polí na nový model [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="d22d3-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="d22d3-288">Tato metoda transformuje `Label` na číselný typ klíče (`LabelTokey`) sloupce a přidejte ho jako nový sloupec datové sady:  Pojmenujte toto `estimator` jako také přidáte školitele k němu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="d22d3-289">Přidáte další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="d22d3-290">Váš odhad používá předem pro zpracování obrázků [hluboké Neuronové Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers pro extrakci funkce.</span><span class="sxs-lookup"><span data-stu-id="d22d3-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="d22d3-291">Při zpracování komplexnějších hluboké neuronové sítě, můžete přizpůsobit bitové kopie do formátu očekávanému sítě.</span><span class="sxs-lookup"><span data-stu-id="d22d3-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="d22d3-292">To je důvod, že použití několika transformací bitové kopie k načtení dat obrázků do očekávanému vzoru:</span><span class="sxs-lookup"><span data-stu-id="d22d3-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="d22d3-293">`LoadImages`Transformace obrázky jsou načtena do paměti jako typ rastrového obrázku.</span><span class="sxs-lookup"><span data-stu-id="d22d3-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="d22d3-294">`ResizeImages` Transformace změní velikost obrázků předem natrénovaných modelů má definovaný vstupní image šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="d22d3-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="d22d3-295">`ExtractPixels` Transformace extrahuje pixely ze vstupní Image a převede je na číselné vektoru.</span><span class="sxs-lookup"><span data-stu-id="d22d3-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="d22d3-296">Přidejte tyto image transformace jako další řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="d22d3-297">`LoadTensorFlowModel` Je pohodlné metodu, která umožňuje `TensorFlow` model, který se má načíst jednou a potom vytvoří `TensorFlowEstimator` pomocí `ScoreTensorFlowModel`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="d22d3-298">`ScoreTensorFlowModel` Výpisy zadaný výstupy ( `Inception model`vaší image funkce `softmax2_pre_activation`) a stanoví skóre datové sady pomocí předem vytrénovaných `TensorFlow` modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="d22d3-299">`softmax2_pre_activation` sestavit model k zjištění, které třída obrázků patří.</span><span class="sxs-lookup"><span data-stu-id="d22d3-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="d22d3-300">`softmax2_pre_activation` vrací pravděpodobnost pro každou kategorii pro bitovou kopii a ve všech těchto pravděpodobností musíte přidat až 1.</span><span class="sxs-lookup"><span data-stu-id="d22d3-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="d22d3-301">Předpokládá, že obraz bude patřit pouze jednu kategorii, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="d22d3-302">Třída</span><span class="sxs-lookup"><span data-stu-id="d22d3-302">Class</span></span>         | <span data-ttu-id="d22d3-303">Pravděpodobnost</span><span class="sxs-lookup"><span data-stu-id="d22d3-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="d22d3-304">0.001</span><span class="sxs-lookup"><span data-stu-id="d22d3-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="d22d3-305">0.95</span><span class="sxs-lookup"><span data-stu-id="d22d3-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="d22d3-306">0,06</span><span class="sxs-lookup"><span data-stu-id="d22d3-306">0.06</span></span>         |

<span data-ttu-id="d22d3-307">Připojte `TensorFlowTransform` k `estimator` s následující řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="d22d3-308">Zvolte cvičení algoritmu</span><span class="sxs-lookup"><span data-stu-id="d22d3-308">Choose a training algorithm</span></span>

<span data-ttu-id="d22d3-309">Chcete-li přidat cvičení algoritmu, zavolejte `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` obalující metodu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="d22d3-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) se připojí `estimator` a přijímá funkce vzniku bitové kopie (`softmax2_pre_activation`) a `Label` vstupní parametry učit se z historických dat.</span><span class="sxs-lookup"><span data-stu-id="d22d3-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="d22d3-311">Přidáte trainer následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d22d3-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="d22d3-312">Je také nutné `predictedlabel` k `predictedlabelvalue`:</span><span class="sxs-lookup"><span data-stu-id="d22d3-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="d22d3-313">`Fit()` Metoda trénovat modelu transformace datové sady a aplikováním školení.</span><span class="sxs-lookup"><span data-stu-id="d22d3-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="d22d3-314">Přizpůsobení modelu, který má trénovací datové sady a vrátí trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="d22d3-315">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda vytváří předpovědi pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="d22d3-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="d22d3-316">Transformace `Training` data přidáním následujícího kódu do `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="d22d3-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="d22d3-317">Převod dat obrázků a předpovědi `DataViews` do silného typu `IEnumerables` spárovat pro snadnější zobrazení.</span><span class="sxs-lookup"><span data-stu-id="d22d3-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="d22d3-318">Použití `MLContext.CreateEnumerable()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="d22d3-319">Volání `DisplayResults()` metodu pro zobrazení vašich dat a předpovědí na dalším řádku `ReuseAndTuneInceptionModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-319">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="d22d3-320">Jakmile budete mít předpovědi nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="d22d3-321">Posuzuje modelu (porovná předpovězené hodnoty v datové sadě skutečná `Labels`).</span><span class="sxs-lookup"><span data-stu-id="d22d3-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="d22d3-322">Vrátí metriky výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="d22d3-323">Přidejte následující kód, který `ReuseAndTuneInceptionModel()` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="d22d3-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="d22d3-324">Klasifikace obrázků, se vyhodnotí následující metriky:</span><span class="sxs-lookup"><span data-stu-id="d22d3-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="d22d3-325">`Log-loss` -naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="d22d3-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="d22d3-326">Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="d22d3-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="d22d3-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-327">`Per class Log-loss`.</span></span> <span data-ttu-id="d22d3-328">Budete chtít na třídu protokolu ztrátu byly co nejblíže nuly nejvíce.</span><span class="sxs-lookup"><span data-stu-id="d22d3-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="d22d3-329">Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d22d3-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="d22d3-330">Přidejte následující kód, který vrátí trénovaného modelu jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="d22d3-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="d22d3-331">Klasifikace obrázků s načíst model</span><span class="sxs-lookup"><span data-stu-id="d22d3-331">Classify images with a loaded model</span></span>

<span data-ttu-id="d22d3-332">Přidejte následující volání `ClassifyImages()` metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="d22d3-333">`ClassifyImages()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="d22d3-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="d22d3-334">Operace čtení. Soubor TSV do `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="d22d3-335">Předpovídá klasifikace obrázků na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="d22d3-336">Vytvořit `ClassifyImages()` metoda, hned za `ReuseAndTuneInceptionModel()` metoda a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="d22d3-337">Nejprve volat `ReadFromTsv()` metodu pro vytvoření `IEnumerable<ImageData>` třídu, která obsahuje plně kvalifikovanou cestu pro každý `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="d22d3-338">Je nutné tuto cesta k souboru spárovat se vaše data a předpovědi výsledky.</span><span class="sxs-lookup"><span data-stu-id="d22d3-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="d22d3-339">Je také potřeba převést `IEnumerable<ImageData>` třídu `IDataView` , kterou použijete k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="d22d3-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="d22d3-340">Přidejte následující kód jako následující dva řádky v `ClassifyImages()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="d22d3-341">Kategorie testu image data s využitím předpovědět, jako jste to udělali dříve s trénovací data bitové kopie, [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) předaný metodě modelu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="d22d3-342">Přidejte následující kód, který `ClassifyImages()` metodu pro předpovědi a k převodu `predictions` `IDataView` do `IEnumerable` pro párování a zobrazení:</span><span class="sxs-lookup"><span data-stu-id="d22d3-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="d22d3-343">Spárujte a zobrazit testovací data bitové kopie a predikcí, přidejte následující kód k volání `DisplayResults()` metoda dříve vytvořeny jako další řádek v `ClassifyImages()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="d22d3-344">Klasifikovat jedné image s načíst model</span><span class="sxs-lookup"><span data-stu-id="d22d3-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="d22d3-345">Přidejte následující volání `ClassifySingleImage()` metody jako další řádek kódu v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="d22d3-346">`ClassifySingleImage()` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="d22d3-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="d22d3-347">Načtení `ImageData` instance.</span><span class="sxs-lookup"><span data-stu-id="d22d3-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="d22d3-348">Předpovídá klasifikace obrázků na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="d22d3-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="d22d3-349">Vytvořit `ClassifySingleImage()` metoda, hned za `ClassifyImages()` metoda a těsně před `PairAndDisplayResults()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d22d3-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="d22d3-350">Nejprve vytvořte `ImageData` třídu, která obsahuje plně kvalifikovaný název souboru cestu a image pro jednoho `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="d22d3-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="d22d3-351">Přidejte následující kód jako následující řádky `ClassifySingleImage()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="d22d3-352">[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které provádí predikcí na jednu instanci data.</span><span class="sxs-lookup"><span data-stu-id="d22d3-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="d22d3-353">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce vytváří predikcí na jeden sloupec data.</span><span class="sxs-lookup"><span data-stu-id="d22d3-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="d22d3-354">Předejte `imageData` k `PredictionEngine` předpovědět kategorie obrázku tak, že přidáte následující kód, který `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="d22d3-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="d22d3-355">Jako další řádek kódu v zobrazení výsledků předpovědí `ClassifySingleImage()` metody:</span><span class="sxs-lookup"><span data-stu-id="d22d3-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="d22d3-356">Výsledky</span><span class="sxs-lookup"><span data-stu-id="d22d3-356">Results</span></span>

<span data-ttu-id="d22d3-357">Po provedení předchozích kroků spuštění aplikace konzoly (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="d22d3-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="d22d3-358">Vaše výsledky by měly být podobně jako následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d22d3-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="d22d3-359">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="d22d3-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="d22d3-360">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="d22d3-360">Congratulations!</span></span> <span data-ttu-id="d22d3-361">Teď úspěšně sestavíte model strojového učení pro klasifikace obrázků opětovným použitím předem vytrénovaných `TensorFlow` model ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d22d3-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="d22d3-362">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) úložiště.</span><span class="sxs-lookup"><span data-stu-id="d22d3-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="d22d3-363">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="d22d3-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d22d3-364">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="d22d3-364">Understand the problem</span></span>
> * <span data-ttu-id="d22d3-365">Opakovaně používat a vyladit předem natrénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="d22d3-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="d22d3-366">Klasifikace obrázků s načíst model</span><span class="sxs-lookup"><span data-stu-id="d22d3-366">Classify images with a loaded model</span></span>

<span data-ttu-id="d22d3-367">Projděte si úložišti GitHub s ukázkami Machine Learning a prozkoumejte ukázkový klasifikace rozšířené image.</span><span class="sxs-lookup"><span data-stu-id="d22d3-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d22d3-368">úložiště GitHub DotNet/machinelearning – ukázky</span><span class="sxs-lookup"><span data-stu-id="d22d3-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
