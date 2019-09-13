---
title: 'Kurz: Přeučení klasifikátoru imagí TensorFlow – učení pro přenos'
description: Naučte se, jak předávat model TensorFlow pro klasifikaci imagí pomocí učení pro přenos a ML.NET. Původní model byl vyškolený pro klasifikaci jednotlivých imagí. Po přeškolení nový model uspořádá obrázky do rozsáhlých kategorií.
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: eb6e3d3f3a33aa7360802ce1bc6c16532539c828
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929241"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="57fa8-105">Kurz: Přeškolování klasifikátoru imagí TensorFlow pomocí učení přenosu a ML.NET</span><span class="sxs-lookup"><span data-stu-id="57fa8-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="57fa8-106">Naučte se, jak předávat model TensorFlow pro klasifikaci imagí pomocí učení pro přenos a ML.NET.</span><span class="sxs-lookup"><span data-stu-id="57fa8-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="57fa8-107">Původní model byl vyškolený pro klasifikaci jednotlivých imagí.</span><span class="sxs-lookup"><span data-stu-id="57fa8-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="57fa8-108">Po přeškolení nový model uspořádá obrázky do rozsáhlých kategorií.</span><span class="sxs-lookup"><span data-stu-id="57fa8-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="57fa8-109">Školení modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tunu školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="57fa8-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="57fa8-110">I když není tak efektivní jako školení vlastního modelu od začátku, pomůže vám tento proces zástupcem pracovat s tisíci imagí. miliony imagí s popisky a sestavování vlastního modelu je poměrně rychlé (během hodiny na počítači bez GPU).</span><span class="sxs-lookup"><span data-stu-id="57fa8-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="57fa8-111">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="57fa8-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="57fa8-112">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="57fa8-112">Understand the problem</span></span>
> * <span data-ttu-id="57fa8-113">Opakované využití a vyladění předučeného modelu</span><span class="sxs-lookup"><span data-stu-id="57fa8-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="57fa8-114">Klasifikace imagí</span><span class="sxs-lookup"><span data-stu-id="57fa8-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="57fa8-115">Co je učení přenosu?</span><span class="sxs-lookup"><span data-stu-id="57fa8-115">What is transfer learning?</span></span>

<span data-ttu-id="57fa8-116">Co když byste mohli znovu použít model, který už je předem vyškolený, aby vyřešil podobný problém a znovu provedl jednu nebo několik vrstev tohoto modelu, aby problém vyřešil?</span><span class="sxs-lookup"><span data-stu-id="57fa8-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="57fa8-117">Tato metoda opětovného použití části již vyškolených modelů pro sestavení nového modelu se označuje jako [učení přenosu](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="57fa8-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="57fa8-118">Ukázka klasifikace obrázků – přehled</span><span class="sxs-lookup"><span data-stu-id="57fa8-118">Image classification sample overview</span></span>

<span data-ttu-id="57fa8-119">Ukázka je Konzolová aplikace, která používá ML.NET k vytvoření klasifikátoru imagí tím, že znovu používá předem připravený model pro klasifikaci imagí s malým množstvím školicích dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="57fa8-120">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="57fa8-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="57fa8-121">Všimněte si, že ve výchozím nastavení je konfigurace projektu .NET pro tento kurz určena pro .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="57fa8-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57fa8-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57fa8-122">Prerequisites</span></span>

* <span data-ttu-id="57fa8-123">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="57fa8-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="57fa8-124">Balíček NuGet pro Microsoft.ML 1.0.0</span><span class="sxs-lookup"><span data-stu-id="57fa8-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="57fa8-125">Balíček NuGet Microsoft. ML. ImageAnalytics 1.0.0</span><span class="sxs-lookup"><span data-stu-id="57fa8-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="57fa8-126">Balíček NuGet Microsoft. ML. TensorFlow 0.12.0</span><span class="sxs-lookup"><span data-stu-id="57fa8-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="57fa8-127">Adresář assetů tutorial Soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="57fa8-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="57fa8-128">Model strojového učení InceptionV1</span><span class="sxs-lookup"><span data-stu-id="57fa8-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="57fa8-129">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="57fa8-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="57fa8-130">[Obsáhlý Learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, což jsou revolutionizing oblasti, jako je počítačové zpracování obrazu a rozpoznávání řeči.</span><span class="sxs-lookup"><span data-stu-id="57fa8-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="57fa8-131">Modely hloubkového učení jsou vyškoleny pomocí rozsáhlých sad [dat s popisky](https://en.wikipedia.org/wiki/Labeled_data) a [neuronové sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více výukových vrstev.</span><span class="sxs-lookup"><span data-stu-id="57fa8-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="57fa8-132">Obsáhlý Learning:</span><span class="sxs-lookup"><span data-stu-id="57fa8-132">Deep learning:</span></span>

* <span data-ttu-id="57fa8-133">Je lepší pro některé úkoly, jako je Počítačové zpracování obrazu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="57fa8-134">Provede i velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="57fa8-135">Klasifikace obrázku je běžný Machine Learning úkol, který nám umožňuje automaticky klasifikovat obrázky do více kategorií, například:</span><span class="sxs-lookup"><span data-stu-id="57fa8-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="57fa8-136">Zjištění lidského obličeje v obrázku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="57fa8-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="57fa8-137">Detekce koček a psi.</span><span class="sxs-lookup"><span data-stu-id="57fa8-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="57fa8-138">Nebo jako v následujících imagích, které určují, jestli je image a (n) jídla, hračka nebo zařízení:</span><span class="sxs-lookup"><span data-stu-id="57fa8-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="57fa8-139">![obrázek![informační](./media/image-classification/220px-Pepperoni_pizza.jpg)
zprávy image Pizza](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
image![Teddy](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="57fa8-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="57fa8-140">Předchozí image patří do Wikimedia a jsou jim tyto atributy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="57fa8-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505 ,</span><span class="sxs-lookup"><span data-stu-id="57fa8-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="57fa8-142">"119px-Nalle_-_a_small_brown_teddy_bear. jpg" pomocí [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) – s použitím uživatelsky optimalizovaného grafu, kopie od-SA https://commons.wikimedia.org/w/index.php?curid=48166 2,0,.</span><span class="sxs-lookup"><span data-stu-id="57fa8-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="57fa8-143">"193px-Broodrooster. jpg" podle [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) vlastní práce, CC by-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="57fa8-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="57fa8-144">Učení přenosu zahrnuje několik strategií, jako je například *převlakování všech vrstev* a *předposlední vrstvy*.</span><span class="sxs-lookup"><span data-stu-id="57fa8-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="57fa8-145">V tomto kurzu se dozvíte, jak používat *předposlední strategii vrstev*.</span><span class="sxs-lookup"><span data-stu-id="57fa8-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="57fa8-146">*Předposlední strategie vrstev* znovu používá model, který již byl předem vyškolen pro vyřešení konkrétního problému.</span><span class="sxs-lookup"><span data-stu-id="57fa8-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="57fa8-147">Strategie potom přeškolí konečnou vrstvu tohoto modelu, aby vyřešila nový problém.</span><span class="sxs-lookup"><span data-stu-id="57fa8-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="57fa8-148">Po opětovném použití předem připraveného modelu v rámci nového modelu ušetříte významný čas a prostředky.</span><span class="sxs-lookup"><span data-stu-id="57fa8-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="57fa8-149">Model klasifikace imagí znovu používá [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení, oblíbený model rozpoznávání imagí, který je vyškolený pro `ImageNet` datovou sadu, kde se TensorFlow model snaží klasifikovat celé obrázky do tisíc tříd, jako jsou "deštník", "Jersey" a " Myčka nádobí.</span><span class="sxs-lookup"><span data-stu-id="57fa8-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="57fa8-150">Může být klasifikován jako [rozsáhlá síť neuronové konvoluční](https://en.wikipedia.org/wiki/Convolutional_neural_network) a může dosáhnout přiměřeného výkonu pro úlohy s vysokým vizuálním rozpoznáváním, v porovnání s nebo překročení lidského výkonu v některých doménách. `Inception v1 model`</span><span class="sxs-lookup"><span data-stu-id="57fa8-150">The `Inception v1 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="57fa8-151">Model/algoritmus byl vyvinutý několika výzkumníky a na základě původního papíru: ["Přemýšlení architektury zahájení pro Počítačové zpracování obrazu" podle Szegedy, et. VŠ.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="57fa8-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="57fa8-152">Vzhledem k tomu, že již byl předem vyškolen na tisících různých imagí, obsahuje [funkce obrázků](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrázku. `Inception model`</span><span class="sxs-lookup"><span data-stu-id="57fa8-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="57fa8-153">Nižší vrstvy funkcí obrázku rozpoznávají jednoduché funkce (například hrany) a vyšší vrstvy rozpoznávají složitější funkce (například tvary).</span><span class="sxs-lookup"><span data-stu-id="57fa8-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="57fa8-154">Konečná vrstva je vyučena s mnohem menším množstvím dat, protože začínáte předučeným modelem, který již rozumí způsobu klasifikace obrázků.</span><span class="sxs-lookup"><span data-stu-id="57fa8-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="57fa8-155">Jak model umožňuje klasifikovat více než dvě kategorie, jedná se například o [klasifikátor více tříd](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="57fa8-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="57fa8-156">`TensorFlow`je oblíbená sada nástrojů pro hloubkové učení a strojové učení, která umožňuje školicí neuronové sítě (a obecné číselné výpočty) a implementuje se jako `transformer` v ml.NET.</span><span class="sxs-lookup"><span data-stu-id="57fa8-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="57fa8-157">Pro tento kurz se používá k opakovanému použití `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="57fa8-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="57fa8-158">Jak je znázorněno v následujícím diagramu, přidáte odkaz na balíčky NuGet ML.NET v aplikacích .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="57fa8-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="57fa8-159">V rámci zahrnutí ml.NET zahrnuje a odkazuje na nativní `TensorFlow` knihovnu, která umožňuje napsat kód, který načte existující soubor trained `TensorFlow` model pro bodování.</span><span class="sxs-lookup"><span data-stu-id="57fa8-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Diagram TensorFlow Transform ML.NET archu](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="57fa8-161">`Inception model` Je vyškolena pro klasifikaci imagí do tisíc kategorií, ale je třeba klasifikovat obrázky v menší sadě kategorií a pouze na tyto kategorie.</span><span class="sxs-lookup"><span data-stu-id="57fa8-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="57fa8-162">`transfer` Zadejte`transfer learning`část.</span><span class="sxs-lookup"><span data-stu-id="57fa8-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="57fa8-163">Můžete přenést `Inception model`schopnost rozpoznávat a klasifikovat obrázky pro nové kategorie omezené na vlastní třídění imagí.</span><span class="sxs-lookup"><span data-stu-id="57fa8-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="57fa8-164">Chystáte se přesměrovat finální vrstvu tohoto modelu pomocí sady tří kategorií:</span><span class="sxs-lookup"><span data-stu-id="57fa8-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="57fa8-165">Potravinářství</span><span class="sxs-lookup"><span data-stu-id="57fa8-165">Food</span></span>
* <span data-ttu-id="57fa8-166">Hračk</span><span class="sxs-lookup"><span data-stu-id="57fa8-166">Toy</span></span>
* <span data-ttu-id="57fa8-167">Náplně</span><span class="sxs-lookup"><span data-stu-id="57fa8-167">Appliance</span></span>

<span data-ttu-id="57fa8-168">Vaše vrstva používá [algoritmus MULTINOMIAL logistické regrese](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) k co nejrychlejšímu nalezení správné kategorie.</span><span class="sxs-lookup"><span data-stu-id="57fa8-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="57fa8-169">Tento algoritmus klasifikuje použití pravděpodobností k určení odpovědi, zadání jedné hodnoty do správné kategorie a nulová hodnoty ostatním.</span><span class="sxs-lookup"><span data-stu-id="57fa8-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="57fa8-170">DataSet</span><span class="sxs-lookup"><span data-stu-id="57fa8-170">DataSet</span></span>

<span data-ttu-id="57fa8-171">Existují dva zdroje dat: `.tsv` soubor a soubory obrázků.</span><span class="sxs-lookup"><span data-stu-id="57fa8-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="57fa8-172">Soubor obsahuje dva sloupce: první je definována jako `ImagePath` a druhá druhá `Label` odpovídá obrázku. `tags.tsv`</span><span class="sxs-lookup"><span data-stu-id="57fa8-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="57fa8-173">Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="57fa8-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="57fa8-174">Obrázky školení a testování se nacházejí ve složkách assetů, které stáhnete do souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="57fa8-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="57fa8-175">Tyto image patří do Wikimedia.</span><span class="sxs-lookup"><span data-stu-id="57fa8-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="57fa8-176">*[Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), bezplatné úložiště médií.*</span><span class="sxs-lookup"><span data-stu-id="57fa8-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="57fa8-177">Načteno 10:48, 17. října 2018 z:</span><span class="sxs-lookup"><span data-stu-id="57fa8-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="57fa8-178">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="57fa8-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="57fa8-179">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="57fa8-179">Create a project</span></span>

1. <span data-ttu-id="57fa8-180">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="57fa8-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="57fa8-181">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="57fa8-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="57fa8-182">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="57fa8-183">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="57fa8-184">Klikněte na rozevírací seznam **verze** , v seznamu vyberte balíček **1.0.0** a vyberte tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="57fa8-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="57fa8-185">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="57fa8-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="57fa8-186">Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics v 1.0.0** a **Microsoft. ml. TensorFlow v 0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="57fa8-187">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="57fa8-187">Prepare your data</span></span>

1. <span data-ttu-id="57fa8-188">Stáhněte si [soubor zip adresáře Project assets](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="57fa8-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="57fa8-189">Zkopírujte adresář do adresáře projektu *TransferLearningTF.* `assets`</span><span class="sxs-lookup"><span data-stu-id="57fa8-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="57fa8-190">Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu zahájení, který si stáhnete a přidáte v dalším kroku) potřebném pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="57fa8-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="57fa8-191">Stáhněte si [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="57fa8-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="57fa8-192">Zkopírujte obsah `inception5h` adresáře pouze do složky projektu `assets\inputs-train\inception` *TransferLearningTF* .</span><span class="sxs-lookup"><span data-stu-id="57fa8-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="57fa8-193">Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="57fa8-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Obsah adresáře v adresáři](./media/image-classification/inception-files.png)

5. <span data-ttu-id="57fa8-195">V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="57fa8-196">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="57fa8-197">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="57fa8-197">Create classes and define paths</span></span>

<span data-ttu-id="57fa8-198">Do horní části souboru `using` *program.cs* přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="57fa8-199">Vytvořte globální pole pro uchování cest k různým prostředkům a globální proměnné pro `LabelTokey`,`ImageReal` `PredictedLabelValue`a:</span><span class="sxs-lookup"><span data-stu-id="57fa8-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="57fa8-200">`_assetsPath`má cestu k assetům.</span><span class="sxs-lookup"><span data-stu-id="57fa8-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="57fa8-201">`_trainTagsTsv`má cestu k souboru. TSV datových značek pro školicí image.</span><span class="sxs-lookup"><span data-stu-id="57fa8-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="57fa8-202">`_predictTagsTsv`má cestu k souboru TSV značek dat předpovědi.</span><span class="sxs-lookup"><span data-stu-id="57fa8-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="57fa8-203">`_trainImagesFolder`má cestu k obrázkům používaným ke výukě modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="57fa8-204">`_predictImagesFolder`má cestu k obrázkům, které mají být klasifikovány podle vyškolených modelů.</span><span class="sxs-lookup"><span data-stu-id="57fa8-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="57fa8-205">`_inceptionPb`má cestu k předučenému modelu zahájení, který se má znovu použít k přeškolování modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="57fa8-206">`_inputImageClassifierZip`má cestu, ze které je načten model trained.</span><span class="sxs-lookup"><span data-stu-id="57fa8-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="57fa8-207">`_outputImageClassifierZip`má cestu, kde je uložený model trained.</span><span class="sxs-lookup"><span data-stu-id="57fa8-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="57fa8-208">`LabelTokey``Label` je hodnota namapovaná na klíč.</span><span class="sxs-lookup"><span data-stu-id="57fa8-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="57fa8-209">`ImageReal`je sloupec obsahující předpovězenou hodnotu obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="57fa8-210">`PredictedLabelValue`je sloupec obsahující předpokládanou hodnotu popisku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="57fa8-211">Přidejte následující kód na řádek přímo nad `Main` metodu pro určení těchto cest a dalších proměnných:</span><span class="sxs-lookup"><span data-stu-id="57fa8-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="57fa8-212">Vytvořte některé třídy pro vstupní data a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="57fa8-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="57fa8-213">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="57fa8-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="57fa8-214">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="57fa8-215">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *imageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="57fa8-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="57fa8-216">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="57fa8-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="57fa8-217">V editoru kódu se otevře soubor *imageData.cs* .</span><span class="sxs-lookup"><span data-stu-id="57fa8-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="57fa8-218">Do horní části `using` *imageData.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="57fa8-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="57fa8-219">Odeberte existující definici třídy a přidejte následující kód pro `ImageData` třídu do souboru *imageData.cs* :</span><span class="sxs-lookup"><span data-stu-id="57fa8-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="57fa8-220">`ImageData`je třída vstupních dat obrázku a obsahuje následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="57fa8-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="57fa8-221">`ImagePath`obsahuje název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="57fa8-222">`Label`obsahuje hodnotu pro popisek obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="57fa8-223">Přidejte do projektu novou třídu pro `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="57fa8-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="57fa8-224">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="57fa8-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="57fa8-225">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="57fa8-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="57fa8-226">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="57fa8-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="57fa8-227">V editoru kódu se otevře soubor *ImagePrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="57fa8-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="57fa8-228">`System.Collections.Generic` Odeberte příkazy`using` a v horní části *ImagePrediction.cs:* `System.Text`</span><span class="sxs-lookup"><span data-stu-id="57fa8-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="57fa8-229">Odeberte existující definici třídy a přidejte následující kód, který má `ImagePrediction` třídu, do souboru *ImagePrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="57fa8-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="57fa8-230">`ImagePrediction`je třída prediktivních imagí a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="57fa8-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="57fa8-231">`Score`obsahuje procento spolehlivosti pro danou klasifikaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="57fa8-232">`PredictedLabelValue`obsahuje hodnotu pro předpokládaný popisek klasifikace obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="57fa8-233">`ImagePrediction`je třída použitá pro předpověď po vyškolení modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="57fa8-234">Má `string` (`ImagePath`) pro cestu k obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="57fa8-235">`Label` Slouží k opakovanému použití a přeučení modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="57fa8-236">`PredictedLabelValue` Je používán během předpovědi a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="57fa8-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="57fa8-237">Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.</span><span class="sxs-lookup"><span data-stu-id="57fa8-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="57fa8-238">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="57fa8-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="57fa8-239">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="57fa8-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="57fa8-240">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="57fa8-240">Initialize variables in Main</span></span>

<span data-ttu-id="57fa8-241">Inicializujte `MLContext`proměnnou novou instancí. `mlContext`</span><span class="sxs-lookup"><span data-stu-id="57fa8-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="57fa8-242">`Main` Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="57fa8-243">Vytvoření struktury pro výchozí parametry</span><span class="sxs-lookup"><span data-stu-id="57fa8-243">Create a struct for default parameters</span></span>

<span data-ttu-id="57fa8-244">Model zahájení má několik výchozích parametrů, které je třeba předat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="57fa8-245">Vytvořte strukturu pro mapování výchozích hodnot parametrů na popisné názvy pomocí následujícího kódu, a to hned za `Main()` metodou:</span><span class="sxs-lookup"><span data-stu-id="57fa8-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="57fa8-246">Vytvoření metody zobrazovacího nástroje</span><span class="sxs-lookup"><span data-stu-id="57fa8-246">Create a display utility method</span></span>

<span data-ttu-id="57fa8-247">Vzhledem k tomu, že zobrazíte data obrázku a související předpovědi více než jednou, vytvořte metodu zobrazení nástrojů pro zpracování zobrazení obrázků a výsledků předpovědi.</span><span class="sxs-lookup"><span data-stu-id="57fa8-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="57fa8-248">`DisplayResults()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="57fa8-249">Zobrazí předpovězené výsledky.</span><span class="sxs-lookup"><span data-stu-id="57fa8-249">Displays the predicted results.</span></span>

<span data-ttu-id="57fa8-250">Vytvořte metodu hned `InceptionSettings` za strukturou pomocí následujícího kódu: `DisplayResults()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="57fa8-251">Metoda naplněná `ImagePath`společněspředpovězenými poli.`ImagePrediction` `Transform()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="57fa8-252">V průběhu procesu ML.NET jednotlivé komponenty přidávají sloupce a usnadňují zobrazení výsledků:</span><span class="sxs-lookup"><span data-stu-id="57fa8-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="57fa8-253">`DisplayResults()` Metodu zavoláte do dvou metod klasifikace imagí.</span><span class="sxs-lookup"><span data-stu-id="57fa8-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="57fa8-254">Vytvoření metody Utility souboru. TSV</span><span class="sxs-lookup"><span data-stu-id="57fa8-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="57fa8-255">`ReadFromTsv()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="57fa8-256">Přečte soubor dat `tags.tsv` obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="57fa8-257">Přidá cestu k souboru s názvem souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="57fa8-258">Načte data souboru do objektu IEnumerable`ImageData` .</span><span class="sxs-lookup"><span data-stu-id="57fa8-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="57fa8-259">Vytvořte metodu hned `PairAndDisplayResults()` za metodou pomocí následujícího kódu: `ReadFromTsv()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="57fa8-260">Následující kód analyzuje `tags.tsv` soubor, aby přidal cestu k souboru bitové kopie pro danou `ImagePath` vlastnost `Label` a načetl `ImageData` ji a do objektu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="57fa8-261">Přidejte ho jako první řádek `ReadFromTsv()` metody.</span><span class="sxs-lookup"><span data-stu-id="57fa8-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="57fa8-262">K zobrazení výsledků předpovědi potřebujete plně kvalifikovanou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="57fa8-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="57fa8-263">ML.NET jsou tři hlavní koncepty: [Data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer)a [odhady](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="57fa8-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="57fa8-264">Opakované použití a vyladění předem připraveného modelu</span><span class="sxs-lookup"><span data-stu-id="57fa8-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="57fa8-265">Do metody přidejte následující volání `ReuseAndTuneInceptionModel()`metody jako další řádek kódu `Main()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="57fa8-266">`ReuseAndTuneInceptionModel()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="57fa8-267">Načte data.</span><span class="sxs-lookup"><span data-stu-id="57fa8-267">Loads the data</span></span>
* <span data-ttu-id="57fa8-268">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="57fa8-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="57fa8-269">Skóre modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="57fa8-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="57fa8-270">Vyladí (převlaky) modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="57fa8-271">Zobrazí výsledky modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-271">Displays model results.</span></span>
* <span data-ttu-id="57fa8-272">Vyhodnotí model.</span><span class="sxs-lookup"><span data-stu-id="57fa8-272">Evaluates the model.</span></span>
* <span data-ttu-id="57fa8-273">Vrátí model.</span><span class="sxs-lookup"><span data-stu-id="57fa8-273">Returns the model.</span></span>

<span data-ttu-id="57fa8-274">Vytvořte metodu hned `InceptionSettings` za`DisplayResults()` strukturou a těsně před metodou pomocí následujícího kódu: `ReuseAndTuneInceptionModel()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="57fa8-275">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="57fa8-275">Load the data</span></span>

<span data-ttu-id="57fa8-276">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="57fa8-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="57fa8-277">`IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="57fa8-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="57fa8-278">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="57fa8-279">Načtěte data pomocí `MLContext.Data.LoadFromTextFile` obálky.</span><span class="sxs-lookup"><span data-stu-id="57fa8-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="57fa8-280">Přidejte následující kód jako další řádek v `ReuseAndTuneInceptionModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="57fa8-281">Extrakce funkcí a transformace dat</span><span class="sxs-lookup"><span data-stu-id="57fa8-281">Extract Features and transform the data</span></span>

<span data-ttu-id="57fa8-282">Data před zpracováním a čištěním jsou důležité úlohy, ke kterým dochází předtím, než se pro strojové učení efektivně použije datová sada.</span><span class="sxs-lookup"><span data-stu-id="57fa8-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="57fa8-283">Použití dat bez těchto úloh modelování může způsobit zavádějící výsledky.</span><span class="sxs-lookup"><span data-stu-id="57fa8-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="57fa8-284">Algoritmy strojového učení rozumějí data [natrénuje](../resources/glossary.md#feature) a při práci s hlubokými neuronové sítěmi musíte image přizpůsobit podle formátu očekávaného sítí.</span><span class="sxs-lookup"><span data-stu-id="57fa8-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="57fa8-285">Tento formát je [číselného vektoru](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="57fa8-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="57fa8-286">Po školení a vyhodnocení vyhodnoťte hodnoty sloupce **popisek** .</span><span class="sxs-lookup"><span data-stu-id="57fa8-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="57fa8-287">Při použití předem připraveného modelu mapujte pole do nového modelu pomocí metody [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) .</span><span class="sxs-lookup"><span data-stu-id="57fa8-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="57fa8-288">Tato metoda transformuje `Label` sloupec do číselného typu klíče (`LabelTokey`) a přidá ho jako sloupec nové datové sady:  Pojmenujte ho `estimator` , protože do něj taky přidáte Trainer.</span><span class="sxs-lookup"><span data-stu-id="57fa8-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="57fa8-289">Přidat další řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="57fa8-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="57fa8-290">Pro extrakci funkcí používá Estimator zpracování imagí předem vyškolenou [neuronové síť (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers.</span><span class="sxs-lookup"><span data-stu-id="57fa8-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="57fa8-291">Při práci s hluboce neuronové sítěmi přiřadíte image k očekávanému formátu sítě.</span><span class="sxs-lookup"><span data-stu-id="57fa8-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="57fa8-292">To je důvod, proč pomocí několika transformací obrázku získá obrazová data do očekávaného formátu modelu:</span><span class="sxs-lookup"><span data-stu-id="57fa8-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="57fa8-293">`LoadImages`Transformační obrázky jsou načteny do paměti jako typ rastrového obrázku.</span><span class="sxs-lookup"><span data-stu-id="57fa8-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="57fa8-294">`ResizeImages` Transformace změní velikost obrázků jako předučený model s definovanou šířkou a výškou vstupní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="57fa8-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="57fa8-295">Tato `ExtractPixels` transformace extrahuje pixely ze vstupních imagí a převede je na číselný vektor.</span><span class="sxs-lookup"><span data-stu-id="57fa8-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="57fa8-296">Přidejte tyto transformace obrázků jako další řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="57fa8-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="57fa8-297">Je pohodlnější způsob, který `TensorFlow` umožňuje načíst model `TensorFlowEstimator` jednou a pak vytvoří pomocí `ScoreTensorFlowModel`. `LoadTensorFlowModel`</span><span class="sxs-lookup"><span data-stu-id="57fa8-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="57fa8-298">Extrahuje zadané výstupy `Inception model`(funkce `softmax2_pre_activation`obrázku) a vyhodnotí datovou sadu pomocí předem připraveného `TensorFlow` modelu. `ScoreTensorFlowModel`</span><span class="sxs-lookup"><span data-stu-id="57fa8-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="57fa8-299">`softmax2_pre_activation`pomáhá modelu při určování, do které třídy patří obrázky.</span><span class="sxs-lookup"><span data-stu-id="57fa8-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="57fa8-300">`softmax2_pre_activation`vrací pravděpodobnost pro každou kategorii pro obrázek a všechny tyto pravděpodobnosti musí přidat až 1.</span><span class="sxs-lookup"><span data-stu-id="57fa8-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="57fa8-301">Předpokládá, že bitová kopie bude patřit pouze do jedné kategorie, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="57fa8-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="57fa8-302">Třída</span><span class="sxs-lookup"><span data-stu-id="57fa8-302">Class</span></span>         | <span data-ttu-id="57fa8-303">Jakou</span><span class="sxs-lookup"><span data-stu-id="57fa8-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="57fa8-304">0,001</span><span class="sxs-lookup"><span data-stu-id="57fa8-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="57fa8-305">0,95</span><span class="sxs-lookup"><span data-stu-id="57fa8-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="57fa8-306">0,06</span><span class="sxs-lookup"><span data-stu-id="57fa8-306">0.06</span></span>         |

<span data-ttu-id="57fa8-307">`TensorFlowTransform` Přidejte`estimator` k a následující řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="57fa8-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="57fa8-308">Zvolit algoritmus školení</span><span class="sxs-lookup"><span data-stu-id="57fa8-308">Choose a training algorithm</span></span>

<span data-ttu-id="57fa8-309">Chcete-li přidat školicí algoritmus, zavolejte `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` metodu obálky.</span><span class="sxs-lookup"><span data-stu-id="57fa8-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="57fa8-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) je připojen k `estimator` a přijímá funkce informování imagí `Label` (`softmax2_pre_activation`) a vstupní parametry, abyste se dozvěděli z historických dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="57fa8-311">Přidejte Trainer s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="57fa8-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="57fa8-312">Je také nutné namapovat `predictedlabel` `predictedlabelvalue`na:</span><span class="sxs-lookup"><span data-stu-id="57fa8-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="57fa8-313">`Fit()` Metoda navlakuje váš model transformací datové sady a použitím školení.</span><span class="sxs-lookup"><span data-stu-id="57fa8-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="57fa8-314">Přizpůsobte model do datové sady školení a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `ReuseAndTuneInceptionModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="57fa8-315">Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro více zadaných vstupních řádků testovací sady dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="57fa8-316">Transformujte `ReuseAndTuneInceptionModel()`data přidáním následujícího kódu do: `Training`</span><span class="sxs-lookup"><span data-stu-id="57fa8-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="57fa8-317">Převeďte obrazová data a `DataViews` předpovědi na dvojici `IEnumerables` se silným typem a pro snazší zobrazení.</span><span class="sxs-lookup"><span data-stu-id="57fa8-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="57fa8-318">Použijte k tomu metodu pomocí následujícího kódu: `MLContext.CreateEnumerable()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="57fa8-319">Zavolejte metodu pro zobrazení dat a předpovědi jako další řádek `ReuseAndTuneInceptionModel()` v metodě: `DisplayResults()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-319">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="57fa8-320">Jakmile máte předsadu předpovědi, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="57fa8-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="57fa8-321">Vyhodnotí model (porovná předpovězené hodnoty se skutečnou datovou `Labels`sadou).</span><span class="sxs-lookup"><span data-stu-id="57fa8-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="57fa8-322">Vrátí metriku výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="57fa8-323">Do `ReuseAndTuneInceptionModel()` metody přidejte následující kód jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="57fa8-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="57fa8-324">Pro klasifikaci imagí jsou vyhodnocovány následující metriky:</span><span class="sxs-lookup"><span data-stu-id="57fa8-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="57fa8-325">`Log-loss`– viz [ztráta protokolu](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="57fa8-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="57fa8-326">Chcete, aby byla ztráta protokolu co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="57fa8-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="57fa8-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="57fa8-327">`Per class Log-loss`.</span></span> <span data-ttu-id="57fa8-328">Požadujete, aby byla ztráta protokolu podle třídy co nejblíže k nule.</span><span class="sxs-lookup"><span data-stu-id="57fa8-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="57fa8-329">Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:</span><span class="sxs-lookup"><span data-stu-id="57fa8-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="57fa8-330">Přidejte následující kód, který vrátí vycvičený model jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="57fa8-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="57fa8-331">Klasifikace imagí pomocí načteného modelu</span><span class="sxs-lookup"><span data-stu-id="57fa8-331">Classify images with a loaded model</span></span>

<span data-ttu-id="57fa8-332">Do metody přidejte následující volání `ClassifyImages()` metody jako další řádek kódu `Main` v metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="57fa8-333">`ClassifyImages()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="57fa8-334">Operace. Soubor TSV do `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="57fa8-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="57fa8-335">Předpovídá klasifikace obrázků na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="57fa8-336">Vytvořte metodu hned `ReuseAndTuneInceptionModel()` za`PairAndDisplayResults()` metodou a těsně před metodou pomocí následujícího kódu: `ClassifyImages()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="57fa8-337">Nejprve zavolejte `ReadFromTsv()` metodu pro `IEnumerable<ImageData>` vytvoření třídy, která obsahuje úplnou cestu pro každý z nich `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="57fa8-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="57fa8-338">K spárování vašich dat a výsledků předpovědi potřebujete tuto cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="57fa8-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="57fa8-339">Také je nutné převést `IEnumerable<ImageData>` třídu na objekt `IDataView` , který budete používat k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="57fa8-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="57fa8-340">Přidejte následující kód jako následující dva řádky v `ClassifyImages()` metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="57fa8-341">Jak jste prošli s daty školicích imagí, předpověď kategorie testovacích dat pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) předaného modelu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="57fa8-342">Přidejte `ClassifyImages()` následující kód do metody pro předpovědi a pro `predictions` `IDataView` převod `IEnumerable` na pro párování a zobrazení:</span><span class="sxs-lookup"><span data-stu-id="57fa8-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="57fa8-343">Pro spárování a zobrazení dat testovací image a předpovědi přidejte následující kód pro volání `DisplayResults()` metody dříve vytvořené jako další řádek `ClassifyImages()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="57fa8-344">Klasifikace jednoho obrázku s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="57fa8-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="57fa8-345">Do metody přidejte následující volání `ClassifySingleImage()` metody jako další řádek kódu `Main` v metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="57fa8-346">`ClassifySingleImage()` Metoda provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="57fa8-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="57fa8-347">`ImageData` Načte instanci.</span><span class="sxs-lookup"><span data-stu-id="57fa8-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="57fa8-348">Odhadne klasifikaci obrázku na základě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="57fa8-349">Vytvořte metodu hned `ClassifyImages()` za`PairAndDisplayResults()` metodou a těsně před metodou pomocí následujícího kódu: `ClassifySingleImage()`</span><span class="sxs-lookup"><span data-stu-id="57fa8-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="57fa8-350">Nejprve vytvořte `ImageData` třídu, která obsahuje plně kvalifikovanou cestu a název souboru obrázku pro jednu `ImagePath`z nich.</span><span class="sxs-lookup"><span data-stu-id="57fa8-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="57fa8-351">Přidejte následující kód jako další řádky v `ClassifySingleImage()` metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="57fa8-352">[Třída PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které provádí předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="57fa8-353">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden sloupec dat.</span><span class="sxs-lookup"><span data-stu-id="57fa8-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="57fa8-354">Předat `imageData` do `ClassifySingleImage()`a předpovědět kategorii obrázku přidáním následujícího kódu do: `PredictionEngine`</span><span class="sxs-lookup"><span data-stu-id="57fa8-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="57fa8-355">Zobrazit výsledek předpovědi jako další řádek kódu v `ClassifySingleImage()` metodě:</span><span class="sxs-lookup"><span data-stu-id="57fa8-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="57fa8-356">Výsledky</span><span class="sxs-lookup"><span data-stu-id="57fa8-356">Results</span></span>

<span data-ttu-id="57fa8-357">Po provedení předchozích kroků spusťte konzolovou aplikaci (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="57fa8-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="57fa8-358">Výsledky by měly být podobné následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="57fa8-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="57fa8-359">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="57fa8-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="57fa8-360">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="57fa8-360">Congratulations!</span></span> <span data-ttu-id="57fa8-361">Teď jste úspěšně vytvořili model strojového učení pro klasifikaci imagí tím, že znovu použijete předem připravený `TensorFlow` model v ml.NET.</span><span class="sxs-lookup"><span data-stu-id="57fa8-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="57fa8-362">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="57fa8-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="57fa8-363">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="57fa8-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="57fa8-364">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="57fa8-364">Understand the problem</span></span>
> * <span data-ttu-id="57fa8-365">Opakované využití a vyladění předučeného modelu</span><span class="sxs-lookup"><span data-stu-id="57fa8-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="57fa8-366">Klasifikace imagí pomocí načteného modelu</span><span class="sxs-lookup"><span data-stu-id="57fa8-366">Classify images with a loaded model</span></span>

<span data-ttu-id="57fa8-367">Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku klasifikace rozbalené image.</span><span class="sxs-lookup"><span data-stu-id="57fa8-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="57fa8-368">dotnet/machinelearning-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="57fa8-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
