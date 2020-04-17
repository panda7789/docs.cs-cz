---
title: 'Kurz: Detekce objektů pomocí modelu hlubokého učení ONNX'
description: Tento kurz ukazuje, jak používat předem trénovaný model hlubokého učení ONNX v ML.NET k detekci objektů v obrazech.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9677c6c9da542123146fc9eef9c311ef30c174e
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608007"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="f8c28-103">Kurz: Detekce objektů používajících ONNX v ML.NET</span><span class="sxs-lookup"><span data-stu-id="f8c28-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="f8c28-104">Naučte se používat předem trénovaný model ONNX v ML.NET k detekci objektů v obrazech.</span><span class="sxs-lookup"><span data-stu-id="f8c28-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="f8c28-105">Trénování modelu detekce objektů od začátku vyžaduje nastavení milionů parametrů, velké množství trénovacích dat označených popiskem a obrovské množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="f8c28-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="f8c28-106">Použití předem trénovaného modelu umožňuje zkrátit proces školení.</span><span class="sxs-lookup"><span data-stu-id="f8c28-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="f8c28-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="f8c28-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f8c28-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="f8c28-108">Understand the problem</span></span>
> - <span data-ttu-id="f8c28-109">Zjistěte, co je ONNX a jak funguje s ML.NET</span><span class="sxs-lookup"><span data-stu-id="f8c28-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="f8c28-110">Porozumět modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-110">Understand the model</span></span>
> - <span data-ttu-id="f8c28-111">Opětovné použití předem trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="f8c28-112">Detekce objektů s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="f8c28-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f8c28-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8c28-113">Pre-requisites</span></span>

- <span data-ttu-id="f8c28-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="f8c28-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="f8c28-115">Microsoft.ML Balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="f8c28-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="f8c28-116">Balíček Microsoft.ML.ImageAnalytics NuGet</span><span class="sxs-lookup"><span data-stu-id="f8c28-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="f8c28-117">Balíček Microsoft.ML.OnnxTransformer NuGet</span><span class="sxs-lookup"><span data-stu-id="f8c28-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="f8c28-118">Malý YOLOv2 předem vyškolený model</span><span class="sxs-lookup"><span data-stu-id="f8c28-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- <span data-ttu-id="f8c28-119">[Netron](https://github.com/lutzroeder/netron) (volitelně)</span><span class="sxs-lookup"><span data-stu-id="f8c28-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="f8c28-120">Ukázka detekce objektů ONNX – přehled</span><span class="sxs-lookup"><span data-stu-id="f8c28-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="f8c28-121">Tato ukázka vytvoří aplikaci konzoly .NET core, která detekuje objekty v rámci bitové kopie pomocí předem trénovaného modelu ONNX s hloubkovým učením.</span><span class="sxs-lookup"><span data-stu-id="f8c28-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="f8c28-122">Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="f8c28-123">Co je detekce objektů?</span><span class="sxs-lookup"><span data-stu-id="f8c28-123">What is object detection?</span></span>

<span data-ttu-id="f8c28-124">Detekce objektů je problém s počítačovým viděním.</span><span class="sxs-lookup"><span data-stu-id="f8c28-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="f8c28-125">Zatímco úzce souvisí s klasifikací obrazu, detekce objektů provádí klasifikaci obrazu v podrobnějším měřítku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="f8c28-126">Detekce objektů vyhledá _a_ kategorizuje entity v rámci bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="f8c28-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="f8c28-127">Detekce objektů použijte, pokud obrazy obsahují více objektů různých typů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-127">Use object detection when images contain multiple objects of different types.</span></span>

![Snímky obrazovky znázorňující klasifikaci obrázků versus klasifikaci objektů.](./media/object-detection-onnx/img-classification-obj-detection.png)

<span data-ttu-id="f8c28-129">Některé případy použití pro detekci objektů patří:</span><span class="sxs-lookup"><span data-stu-id="f8c28-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="f8c28-130">Samořiditelná auta</span><span class="sxs-lookup"><span data-stu-id="f8c28-130">Self-Driving Cars</span></span>
- <span data-ttu-id="f8c28-131">Robotika</span><span class="sxs-lookup"><span data-stu-id="f8c28-131">Robotics</span></span>
- <span data-ttu-id="f8c28-132">Detekce obličeje</span><span class="sxs-lookup"><span data-stu-id="f8c28-132">Face Detection</span></span>
- <span data-ttu-id="f8c28-133">Bezpečnost na pracovišti</span><span class="sxs-lookup"><span data-stu-id="f8c28-133">Workplace Safety</span></span>
- <span data-ttu-id="f8c28-134">Počítání objektů</span><span class="sxs-lookup"><span data-stu-id="f8c28-134">Object Counting</span></span>
- <span data-ttu-id="f8c28-135">Rozpoznávání aktivit</span><span class="sxs-lookup"><span data-stu-id="f8c28-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="f8c28-136">Výběr modelu hlubokého učení</span><span class="sxs-lookup"><span data-stu-id="f8c28-136">Select a deep learning model</span></span>

<span data-ttu-id="f8c28-137">Hluboké učení je podmnožinou strojového učení.</span><span class="sxs-lookup"><span data-stu-id="f8c28-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="f8c28-138">Pro trénování modelů hlubokého učení je vyžadováno velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="f8c28-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="f8c28-139">Vzorky v datech jsou reprezentovány řadou vrstev.</span><span class="sxs-lookup"><span data-stu-id="f8c28-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="f8c28-140">Vztahy v datech jsou kódovány jako spojení mezi vrstvami obsahujícími závaží.</span><span class="sxs-lookup"><span data-stu-id="f8c28-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="f8c28-141">Čím vyšší je váha, tím silnější je vztah.</span><span class="sxs-lookup"><span data-stu-id="f8c28-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="f8c28-142">Společně, tato řada vrstev a připojení jsou známé jako umělé neuronové sítě.</span><span class="sxs-lookup"><span data-stu-id="f8c28-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="f8c28-143">Čím více vrstev v síti, tím "hlubší" je, což z ní činí hlubokou neuronovou síť.</span><span class="sxs-lookup"><span data-stu-id="f8c28-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="f8c28-144">Existují různé typy neuronových sítí, nejběžnější je vícevrstvý perceptron (MLP), konvoluční neuronová síť (CNN) a rekurentní neuronová síť (RNN).</span><span class="sxs-lookup"><span data-stu-id="f8c28-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="f8c28-145">Nejzákladnější je MLP, který mapuje sadu vstupů na sadu výstupů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="f8c28-146">Tato neuronová síť je dobrá, když data nemají prostorovou nebo časovou složku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="f8c28-147">CNN využívá konvoluční vrstvy ke zpracování prostorových informací obsažených v datech.</span><span class="sxs-lookup"><span data-stu-id="f8c28-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="f8c28-148">Dobrým případem použití pro CNNs je zpracování obrazu pro detekci přítomnosti prvku v oblasti obrazu (například je nos ve středu obrazu?).</span><span class="sxs-lookup"><span data-stu-id="f8c28-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="f8c28-149">Nakonec rnns umožňují trvalost stavu nebo paměti, které mají být použity jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f8c28-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="f8c28-150">RNNs se používají pro analýzu časových řad, kde je důležité sekvenční řazení a kontext událostí.</span><span class="sxs-lookup"><span data-stu-id="f8c28-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="f8c28-151">Porozumět modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-151">Understand the model</span></span>

<span data-ttu-id="f8c28-152">Detekce objektů je úloha zpracování obrazu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-152">Object detection is an image-processing task.</span></span> <span data-ttu-id="f8c28-153">Proto většina modelů hlubokého učení vyškolených k vyřešení tohoto problému jsou CNNs.</span><span class="sxs-lookup"><span data-stu-id="f8c28-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="f8c28-154">Model použitý v tomto tutoriálu je model Tiny YOLOv2, kompaktnější verze modelu YOLOv2 popsaná v dokumentu: ["YOLO9000: Lepší, rychlejší, silnější" od Redmon a Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="f8c28-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="f8c28-155">Tiny YOLOv2 je trénovaný na datové sadě Pascal VOC a skládá se z 15 vrstev, které dokáží předpovědět 20 různých tříd objektů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="f8c28-156">Vzhledem k tomu, že Tiny YOLOv2 je zkrácená verze původního modelu YOLOv2, je proveden kompromis mezi rychlostí a přesností.</span><span class="sxs-lookup"><span data-stu-id="f8c28-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="f8c28-157">Různé vrstvy, které tvoří model, lze vizualizovat pomocí nástrojů, jako je Netron.</span><span class="sxs-lookup"><span data-stu-id="f8c28-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="f8c28-158">Kontrola modelu by přinesla mapování spojení mezi všemi vrstvami, které tvoří neuronovou síť, kde by každá vrstva obsahovala název vrstvy spolu s rozměry příslušného vstupu / výstupu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="f8c28-159">Datové struktury používané k popisu vstupů a výstupů modelu jsou označovány jako tenzory.</span><span class="sxs-lookup"><span data-stu-id="f8c28-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="f8c28-160">Tenzory si lze myslet jako kontejnery, které ukládají data v N-dimenzích.</span><span class="sxs-lookup"><span data-stu-id="f8c28-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="f8c28-161">V případě Tiny YOLOv2 je `image` název vstupní vrstvy a očekává tenzor `3 x 416 x 416`rozměrů .</span><span class="sxs-lookup"><span data-stu-id="f8c28-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="f8c28-162">Název výstupní vrstvy `grid` je a generuje výstupní tenzor rozměrů `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="f8c28-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Vstupní vrstva je rozdělena do skrytých vrstev a pak výstupní vrstva](./media/object-detection-onnx/netron-model-map-layers.png)

<span data-ttu-id="f8c28-164">Model YOLO pořídí `3(RGB) x 416px x 416px`obraz .</span><span class="sxs-lookup"><span data-stu-id="f8c28-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="f8c28-165">Model převezme tento vstup a předá jej přes různé vrstvy k vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="f8c28-166">Výstup rozdělí vstupní obraz do `13 x 13` mřížky, přičemž každá buňka v mřížce se skládá z `125` hodnot.</span><span class="sxs-lookup"><span data-stu-id="f8c28-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="f8c28-167">Co je model ONNX?</span><span class="sxs-lookup"><span data-stu-id="f8c28-167">What is an ONNX model?</span></span>

<span data-ttu-id="f8c28-168">Open Neural Network Exchange (ONNX) je open source formát pro modely AI.</span><span class="sxs-lookup"><span data-stu-id="f8c28-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="f8c28-169">ONNX podporuje interoperabilitu mezi rámci.</span><span class="sxs-lookup"><span data-stu-id="f8c28-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="f8c28-170">To znamená, že můžete trénovat model v jednom z mnoha populárních rámců strojového učení, jako je PyTorch, převést jej do formátu ONNX a spotřebovávat model ONNX v jiném rámci, jako je ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f8c28-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="f8c28-171">Chcete-li se dozvědět více, navštivte [webové stránky ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="f8c28-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![Diagram používaných formátů podporovaných onnx.](./media/object-detection-onnx/onnx-supported-formats.png)

<span data-ttu-id="f8c28-173">Předem vycvičený model Tiny YOLOv2 je uložen ve formátu ONNX, což je serializovaná reprezentace vrstev a naučených vzorů těchto vrstev.</span><span class="sxs-lookup"><span data-stu-id="f8c28-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="f8c28-174">V ML.NET je interoperabilita [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) s [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) ONNX dosažena s balíčky a NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8c28-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="f8c28-175">Balíček [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) obsahuje řadu transformací, které berou bitovou kopii a kódují ji do číselných hodnot, které lze použít jako vstup do kanálu předpověď nebo školení.</span><span class="sxs-lookup"><span data-stu-id="f8c28-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="f8c28-176">Balíček [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) využívá onnx runtime načíst model ONNX a použít jej k předpovědi na základě vstupní poskytované.</span><span class="sxs-lookup"><span data-stu-id="f8c28-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![Tok dat souboru ONNX do runtime ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="f8c28-178">Nastavení projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f8c28-178">Set up the .NET Core project</span></span>

<span data-ttu-id="f8c28-179">Nyní, když máte obecné znalosti o tom, co je ONNX a jak Funguje Tiny YOLOv2, je čas vytvořit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f8c28-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="f8c28-180">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="f8c28-180">Create a console application</span></span>

1. <span data-ttu-id="f8c28-181">Vytvořte **aplikaci konzoly .NET Core console** nazvanou "ObjectDetection".</span><span class="sxs-lookup"><span data-stu-id="f8c28-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="f8c28-182">Nainstalujte **balíček nuget Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="f8c28-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="f8c28-183">V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="f8c28-184">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="f8c28-185">Vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="f8c28-186">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="f8c28-187">Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics** a **Microsoft.ML.OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="f8c28-188">Příprava dat a předem trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="f8c28-189">Stáhnout [soubor zip adresáře datových zdrojů projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) a rozbalit.</span><span class="sxs-lookup"><span data-stu-id="f8c28-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="f8c28-190">Zkopírujte `assets` adresář do adresáře projektu *ObjectDetection.*</span><span class="sxs-lookup"><span data-stu-id="f8c28-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="f8c28-191">Tento adresář a jeho podadresáře obsahují obrazové soubory (s výjimkou modelu Tiny YOLOv2, který si stáhnete a přidáte v dalším kroku) potřebné pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="f8c28-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="f8c28-192">Stáhněte si [model Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)a rozbalte.</span><span class="sxs-lookup"><span data-stu-id="f8c28-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="f8c28-193">Otevřete příkazový řádek a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f8c28-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="f8c28-194">Zkopírujte extrahovaný `model.onnx` soubor z adresáře, který `assets\Model` se rozbalil do adresáře projektu `TinyYolo2_model.onnx` *ObjectDetection,* a přejmenujte jej na .</span><span class="sxs-lookup"><span data-stu-id="f8c28-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="f8c28-195">Tento adresář obsahuje model potřebný pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="f8c28-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="f8c28-196">V Průzkumníku řešení klepněte pravým tlačítkem myši na jednotlivé soubory v adresáři datových zdrojů a podadresářích a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="f8c28-197">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f8c28-198">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="f8c28-198">Create classes and define paths</span></span>

<span data-ttu-id="f8c28-199">Otevřete *Program.cs* soubor a `using` přidejte do horní části souboru následující další příkazy:</span><span class="sxs-lookup"><span data-stu-id="f8c28-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="f8c28-200">Dále definujte cesty různých prostředků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="f8c28-201">Nejprve přidejte metodu `GetAbsolutePath` pod metodu `Main` ve `Program` třídě.</span><span class="sxs-lookup"><span data-stu-id="f8c28-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="f8c28-202">Potom uvnitř `Main` metody vytvořte pole pro uložení umístění prostředků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="f8c28-203">Přidejte do projektu nový adresář pro ukládání vstupních dat a tříd předpovědi.</span><span class="sxs-lookup"><span data-stu-id="f8c28-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="f8c28-204">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="f8c28-205">Když se nová složka zobrazí v Průzkumníku řešení, pojmenujte ji "DataStructures".</span><span class="sxs-lookup"><span data-stu-id="f8c28-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="f8c28-206">Vytvořte třídu vstupních dat v nově vytvořeném *adresáři DataStructures.*</span><span class="sxs-lookup"><span data-stu-id="f8c28-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="f8c28-207">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *DataStructures* a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f8c28-208">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="f8c28-209">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f8c28-210">Soubor *ImageNetData.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f8c28-211">Na začátek `using` *ImageNetData.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="f8c28-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="f8c28-212">Odeberte existující definici třídy `ImageNetData` a přidejte do *ImageNetData.cs* souboru následující kód pro třídu:</span><span class="sxs-lookup"><span data-stu-id="f8c28-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="f8c28-213">`ImageNetData`je třída vstupních obrazových <xref:System.String> dat a má následující pole:</span><span class="sxs-lookup"><span data-stu-id="f8c28-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="f8c28-214">`ImagePath`obsahuje cestu, na které je obraz uložen.</span><span class="sxs-lookup"><span data-stu-id="f8c28-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="f8c28-215">`Label`obsahuje název souboru.</span><span class="sxs-lookup"><span data-stu-id="f8c28-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="f8c28-216">Navíc obsahuje `ImageNetData` metodu, `ReadFromFile` která načte více `imageFolder` obrazových souborů uložených `ImageNetData` v zadané cestě a vrátí je jako kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-216">Additionally, `ImageNetData` contains a method `ReadFromFile` that loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="f8c28-217">Vytvořte třídu předpověď v adresáři *DataStructures.*</span><span class="sxs-lookup"><span data-stu-id="f8c28-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="f8c28-218">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *DataStructures* a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f8c28-219">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="f8c28-220">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f8c28-221">V editoru kódu se otevře *ImageNetPrediction.cs* soubor.</span><span class="sxs-lookup"><span data-stu-id="f8c28-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="f8c28-222">Na začátek `using` *ImageNetPrediction.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="f8c28-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="f8c28-223">Odeberte existující definici třídy `ImageNetPrediction` a přidejte do *ImageNetPrediction.cs* souboru následující kód pro třídu:</span><span class="sxs-lookup"><span data-stu-id="f8c28-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="f8c28-224">`ImageNetPrediction`je třída dat předpověď a `float[]` má následující pole:</span><span class="sxs-lookup"><span data-stu-id="f8c28-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="f8c28-225">`PredictedLabel`obsahuje kóty, skóre objektu a pravděpodobnosti třídy pro každý z ohraničovacích rámečků zjištěných v obraze.</span><span class="sxs-lookup"><span data-stu-id="f8c28-225">`PredictedLabel` contains the dimensions, objectness score, and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f8c28-226">Inicializovat proměnné v hlavní</span><span class="sxs-lookup"><span data-stu-id="f8c28-226">Initialize variables in Main</span></span>

<span data-ttu-id="f8c28-227">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f8c28-228">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="f8c28-229">Inicializovat `mlContext` proměnnou s `MLContext` novou instancí přidáním následujícího řádku k metodě `Main` *Program.cs* pod `outputFolder` polem.</span><span class="sxs-lookup"><span data-stu-id="f8c28-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="f8c28-230">Vytvoření analyzátoru pro výstupy modelu po zpracování</span><span class="sxs-lookup"><span data-stu-id="f8c28-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="f8c28-231">Model segmentuje obraz `13 x 13` do mřížky, kde `32px x 32px`je každá buňka mřížky .</span><span class="sxs-lookup"><span data-stu-id="f8c28-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="f8c28-232">Každá buňka mřížky obsahuje 5 polí pro ohraničování potenciálních objektů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="f8c28-233">Ohraničovací rámeček má 25 prvků:</span><span class="sxs-lookup"><span data-stu-id="f8c28-233">A bounding box has  25 elements:</span></span>

![Ukázka mřížky vlevo a ukázka ohraničovacího rámečku vpravo](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="f8c28-235">`x`pozice x středového ohraničovacího rámečku vzhledem k buňce mřížky, ke které je přidružena.</span><span class="sxs-lookup"><span data-stu-id="f8c28-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="f8c28-236">`y`pozice y středového ohraničovacího rámečku vzhledem k buňce mřížky, ke které je přidružena.</span><span class="sxs-lookup"><span data-stu-id="f8c28-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="f8c28-237">`w`šířku ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="f8c28-238">`h`výšku ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="f8c28-239">`o`hodnota spolehlivosti, která objekt existuje v ohraničovacím rámečku, označovaná také jako skóre objektu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="f8c28-240">`p1-p20`pravděpodobnosti třídy pro každou z 20 tříd předpovídaných modelem.</span><span class="sxs-lookup"><span data-stu-id="f8c28-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="f8c28-241">Celkem 25 prvků popisujících každý z 5 ohraničovacích rámečků tvoří 125 prvků obsažených v každé buňce mřížky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="f8c28-242">Výstupem generovaným předem trénovaným modelem ONNX je plovoucí pole délky `21125`, `125 x 13 x 13`představující prvky tenzoru s rozměry .</span><span class="sxs-lookup"><span data-stu-id="f8c28-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="f8c28-243">Chcete-li transformovat předpovědi generované modelem do tenzoru, je vyžadována některá práce po zpracování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="f8c28-244">Chcete-li tak učinit, vytvořte sadu tříd, které vám pomohou analyzovat výstup.</span><span class="sxs-lookup"><span data-stu-id="f8c28-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="f8c28-245">Přidejte do projektu nový adresář pro uspořádání sady tříd analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="f8c28-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="f8c28-246">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="f8c28-247">Když se nová složka zobrazí v Průzkumníku řešení, pojmenujte ji "YoloParser".</span><span class="sxs-lookup"><span data-stu-id="f8c28-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="f8c28-248">Vytvoření ohraničovacích rámečků a kót</span><span class="sxs-lookup"><span data-stu-id="f8c28-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="f8c28-249">Výstup dat modelem obsahuje souřadnice a rozměry ohraničovacích rámečků objektů v obraze.</span><span class="sxs-lookup"><span data-stu-id="f8c28-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="f8c28-250">Vytvořte základní třídu pro kóty.</span><span class="sxs-lookup"><span data-stu-id="f8c28-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="f8c28-251">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *YoloParser* a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f8c28-252">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="f8c28-253">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f8c28-254">V editoru kódu se otevře *soubor DimensionsBase.cs.*</span><span class="sxs-lookup"><span data-stu-id="f8c28-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="f8c28-255">Odeberte všechny `using` příkazy a existující definici třídy.</span><span class="sxs-lookup"><span data-stu-id="f8c28-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="f8c28-256">Do souboru `DimensionsBase` *DimensionsBase.cs* přidejte následující kód třídy:</span><span class="sxs-lookup"><span data-stu-id="f8c28-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="f8c28-257">`DimensionsBase`má následující `float` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f8c28-257">`DimensionsBase` has the following `float` properties:</span></span>

    - <span data-ttu-id="f8c28-258">`X`obsahuje polohu objektu podél osy x.</span><span class="sxs-lookup"><span data-stu-id="f8c28-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="f8c28-259">`Y`obsahuje polohu objektu podél osy y.</span><span class="sxs-lookup"><span data-stu-id="f8c28-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="f8c28-260">`Height`obsahuje výšku objektu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="f8c28-261">`Width`obsahuje šířku objektu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="f8c28-262">Dále vytvořte třídu pro ohraničovací rámečky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="f8c28-263">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *YoloParser* a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f8c28-264">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="f8c28-265">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f8c28-266">V editoru kódu se otevře *YoloBoundingBox.cs* soubor.</span><span class="sxs-lookup"><span data-stu-id="f8c28-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="f8c28-267">Na začátek `using` *YoloBoundingBox.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="f8c28-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="f8c28-268">Těsně nad existující definici třídy přidejte novou definici třídy s názvem, `BoundingBoxDimensions` která dědí z `DimensionsBase` třídy, aby obsahovala rozměry příslušného ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` that inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="f8c28-269">Odeberte `YoloBoundingBox` existující definici třídy `YoloBoundingBox` a přidejte do *souboru YoloBoundingBox.cs* následující kód pro třídu:</span><span class="sxs-lookup"><span data-stu-id="f8c28-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="f8c28-270">`YoloBoundingBox`má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f8c28-270">`YoloBoundingBox` has the following properties:</span></span>

    - <span data-ttu-id="f8c28-271">`Dimensions`obsahuje rozměry ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="f8c28-272">`Label`obsahuje třídu objektu zjištěnou v ohraničovacím rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="f8c28-273">`Confidence`obsahuje důvěru třídy.</span><span class="sxs-lookup"><span data-stu-id="f8c28-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="f8c28-274">`Rect`obsahuje obdélníkovou reprezentaci rozměrů ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="f8c28-275">`BoxColor`obsahuje barvu přidruženou k příslušné třídě použité k kreslení na obrázek.</span><span class="sxs-lookup"><span data-stu-id="f8c28-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="f8c28-276">Vytvoření analyzátoru</span><span class="sxs-lookup"><span data-stu-id="f8c28-276">Create the parser</span></span>

<span data-ttu-id="f8c28-277">Nyní, když jsou vytvořeny třídy pro kóty a ohraničovací rámečky, je čas vytvořit analyzátor.</span><span class="sxs-lookup"><span data-stu-id="f8c28-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="f8c28-278">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *YoloParser* a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f8c28-279">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="f8c28-280">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f8c28-281">V editoru kódu se otevře *YoloOutputParser.cs* soubor.</span><span class="sxs-lookup"><span data-stu-id="f8c28-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="f8c28-282">Na začátek `using` *YoloOutputParser.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="f8c28-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="f8c28-283">Uvnitř existující `YoloOutputParser` definice třídy přidejte vnořenou třídu, která obsahuje rozměry každé buňky v obraze.</span><span class="sxs-lookup"><span data-stu-id="f8c28-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="f8c28-284">Přidejte následující kód `CellDimensions` pro třídu, `DimensionsBase` která dědí `YoloOutputParser` z třídy v horní části definice třídy.</span><span class="sxs-lookup"><span data-stu-id="f8c28-284">Add the following code for the `CellDimensions` class that inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="f8c28-285">Uvnitř `YoloOutputParser` definice třídy přidejte následující konstanty a pole.</span><span class="sxs-lookup"><span data-stu-id="f8c28-285">Inside the `YoloOutputParser` class definition, add the following constants and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="f8c28-286">`ROW_COUNT`je počet řádků v mřížce, na který je obraz rozdělen.</span><span class="sxs-lookup"><span data-stu-id="f8c28-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="f8c28-287">`COL_COUNT`je počet sloupců v mřížce, na který je obraz rozdělen.</span><span class="sxs-lookup"><span data-stu-id="f8c28-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="f8c28-288">`CHANNEL_COUNT`je celkový počet hodnot obsažených v jedné buňce mřížky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="f8c28-289">`BOXES_PER_CELL`je počet ohraničovacích rámečků v buňce,</span><span class="sxs-lookup"><span data-stu-id="f8c28-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="f8c28-290">`BOX_INFO_FEATURE_COUNT`je počet prvků obsažených v rámečku (x,y,výška,šířka,spolehlivost).</span><span class="sxs-lookup"><span data-stu-id="f8c28-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="f8c28-291">`CLASS_COUNT`je počet předpovědí tříd obsažených v každém ohraničovacím rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="f8c28-292">`CELL_WIDTH`je šířka jedné buňky v mřížce obrazu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="f8c28-293">`CELL_HEIGHT`je výška jedné buňky v mřížce obrazu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="f8c28-294">`channelStride`je počáteční pozice aktuální buňky v mřížce.</span><span class="sxs-lookup"><span data-stu-id="f8c28-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="f8c28-295">Když model provede předpověď, označovanou také jako `416px x 416px` vyhodnocování, rozdělí `13 x 13`vstupní obraz do mřížky buněk o velikosti .</span><span class="sxs-lookup"><span data-stu-id="f8c28-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="f8c28-296">Každá buňka `32px x 32px`obsahuje je .</span><span class="sxs-lookup"><span data-stu-id="f8c28-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="f8c28-297">V každé buňce je 5 ohraničovacích rámečků, z nichž každý obsahuje 5 prvků (x, y, šířka, výška, spolehlivost).</span><span class="sxs-lookup"><span data-stu-id="f8c28-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="f8c28-298">Kromě toho každý ohraničovací rámeček obsahuje pravděpodobnost každé třídy, která je v tomto případě 20.</span><span class="sxs-lookup"><span data-stu-id="f8c28-298">In addition, each bounding box contains the probability of each of the classes, which in this case is 20.</span></span> <span data-ttu-id="f8c28-299">Proto každá buňka obsahuje 125 kusů informací (5 funkcí + 20 pravděpodobností třídy).</span><span class="sxs-lookup"><span data-stu-id="f8c28-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="f8c28-300">Vytvořte níže uvedený `channelStride` seznam kotev pro všech 5 ohraničovacích rámečků:</span><span class="sxs-lookup"><span data-stu-id="f8c28-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="f8c28-301">Kotvy jsou předem definované poměry výšky a šířky ohraničovacích rámečků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="f8c28-302">Většina objektů nebo tříd zjištěných modelem má podobné poměry.</span><span class="sxs-lookup"><span data-stu-id="f8c28-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="f8c28-303">To je cenné, pokud jde o vytváření ohraničovacích rámečků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="f8c28-304">Namísto předvídání ohraničovacích rámečků se vypočítá posun od předdefinovaných dimenzí, čímž se sníží výpočet potřebný k předvídání ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="f8c28-305">Tyto kotevní poměry se obvykle počítají na základě použité datové sady.</span><span class="sxs-lookup"><span data-stu-id="f8c28-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="f8c28-306">V tomto případě vzhledem k tomu, že je datová sada známa a hodnoty byly předem vypočítány, mohou být ukotvení pevně zakódována.</span><span class="sxs-lookup"><span data-stu-id="f8c28-306">In this case, because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="f8c28-307">Dále definujte popisky nebo třídy, které bude model předpovídat.</span><span class="sxs-lookup"><span data-stu-id="f8c28-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="f8c28-308">Tento model předpovídá 20 tříd, což je podmnožina celkového počtu tříd předpovídaných původním modelem YOLOv2.</span><span class="sxs-lookup"><span data-stu-id="f8c28-308">This model predicts 20 classes, which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="f8c28-309">Přidejte seznam štítků `anchors`pod .</span><span class="sxs-lookup"><span data-stu-id="f8c28-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="f8c28-310">Ke každé třídě jsou přidruženy barvy.</span><span class="sxs-lookup"><span data-stu-id="f8c28-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="f8c28-311">Přiřaďte barvy `labels`třídy pod :</span><span class="sxs-lookup"><span data-stu-id="f8c28-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="f8c28-312">Vytváření pomocné funkce</span><span class="sxs-lookup"><span data-stu-id="f8c28-312">Create helper functions</span></span>

<span data-ttu-id="f8c28-313">Ve fázi následného zpracování je zapojena řada kroků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="f8c28-314">Na pomoc s tím lze použít několik pomocných metod.</span><span class="sxs-lookup"><span data-stu-id="f8c28-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="f8c28-315">Pomocné metody používané analyzátorem jsou:</span><span class="sxs-lookup"><span data-stu-id="f8c28-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="f8c28-316">`Sigmoid`použije sigmoidní funkci, která vypisuje číslo mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="f8c28-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="f8c28-317">`Softmax`normalizuje vstupní vektor do rozdělení pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="f8c28-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="f8c28-318">`GetOffset`mapuje prvky v jednorozměrném výstupu modelu `125 x 13 x 13` do odpovídající polohy v tenzoru.</span><span class="sxs-lookup"><span data-stu-id="f8c28-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="f8c28-319">`ExtractBoundingBoxes`extrahuje kóty ohraničovacího rámečku `GetOffset` metodou z výstupu modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="f8c28-320">`GetConfidence`extrahuje hodnotu spolehlivosti, která uvádí, jak jistý je `Sigmoid` model, že detekoval objekt a používá funkci k jeho přeměně na procento.</span><span class="sxs-lookup"><span data-stu-id="f8c28-320">`GetConfidence` extracts the confidence value that states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="f8c28-321">`MapBoundingBoxToCell`použije rozměry ohraničovacího rámečku a mapuje je na příslušnou buňku v obraze.</span><span class="sxs-lookup"><span data-stu-id="f8c28-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="f8c28-322">`ExtractClasses`extrahuje předpovědi třídy pro ohraničovací `GetOffset` rámeček z výstupu modelu pomocí `Softmax` metody a změní je na rozdělení pravděpodobnosti pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="f8c28-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="f8c28-323">`GetTopResult`vybere třídu ze seznamu předpovídaných tříd s nejvyšší pravděpodobností.</span><span class="sxs-lookup"><span data-stu-id="f8c28-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="f8c28-324">`IntersectionOverUnion`filtruje překrývající se ohraničovací pole s nižší pravděpodobností.</span><span class="sxs-lookup"><span data-stu-id="f8c28-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="f8c28-325">Přidejte kód pro všechny pomocné metody `classColors`pod seznam .</span><span class="sxs-lookup"><span data-stu-id="f8c28-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="f8c28-326">Jakmile definujete všechny pomocné metody, je čas je použít ke zpracování výstupu modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="f8c28-327">Pod `IntersectionOverUnion` metodou vytvořte `ParseOutputs` metodu pro zpracování výstupu generovaného modelem.</span><span class="sxs-lookup"><span data-stu-id="f8c28-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="f8c28-328">Vytvořte seznam pro uložení ohraničovacích `ParseOutputs` rámečků a definování proměnných uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="f8c28-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="f8c28-329">Každý obrázek je rozdělen `13 x 13` do mřížky buněk.</span><span class="sxs-lookup"><span data-stu-id="f8c28-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="f8c28-330">Každá buňka obsahuje pět ohraničovacích rámečků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="f8c28-331">Pod `boxes` proměnnou přidejte kód pro zpracování všech polí v každé z buněk.</span><span class="sxs-lookup"><span data-stu-id="f8c28-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

<span data-ttu-id="f8c28-332">Uvnitř smyčky zcela uvnitř vypočítejte počáteční pozici aktuálního pole v rámci výstupu jednorozměrného modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="f8c28-333">Přímo pod tím `ExtractBoundingBoxDimensions` použijte metodu k získání rozměrů aktuálního ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="f8c28-334">Potom použijte `GetConfidence` metodu k získání jistoty pro aktuální ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="f8c28-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="f8c28-335">Poté použijte metodu `MapBoundingBoxToCell` k mapování aktuálního ohraničovacího rámečku na aktuální zpracovávanou buňku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="f8c28-336">Před dalším zpracováním zkontrolujte, zda je hodnota spolehlivosti větší než stanovená prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="f8c28-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="f8c28-337">Pokud ne, zpracujte další ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="f8c28-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="f8c28-338">V opačném případě pokračujte ve zpracování výstupu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="f8c28-339">Dalším krokem je získání rozdělení pravděpodobnosti předpovídané třídy pro aktuální `ExtractClasses` ohraničovací rámeček pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="f8c28-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="f8c28-340">Potom použijte `GetTopResult` metodu k získání hodnoty a indexu třídy s nejvyšší pravděpodobností pro aktuální pole a vypočítat jeho skóre.</span><span class="sxs-lookup"><span data-stu-id="f8c28-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="f8c28-341">Použijte `topScore` chcete znovu zachovat pouze ty ohraničovací pole, které jsou nad zadanou prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="f8c28-342">Nakonec, pokud aktuální ohraničovací rámeček `BoundingBox` překročí prahovou hodnotu, vytvořte nový objekt a přidejte jej do `boxes` seznamu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="f8c28-343">Po zpracování všech buněk v obraze vraťte `boxes` seznam.</span><span class="sxs-lookup"><span data-stu-id="f8c28-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="f8c28-344">Přidejte následující příkaz return pod vnější nejvíce `ParseOutputs` pro smyčku v metodě.</span><span class="sxs-lookup"><span data-stu-id="f8c28-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="f8c28-345">Filtrování překrývajících se polí</span><span class="sxs-lookup"><span data-stu-id="f8c28-345">Filter overlapping boxes</span></span>

<span data-ttu-id="f8c28-346">Nyní, když byly z výstupu modelu extrahovány všechny vysoce sebevědomé ohraničovací rámečky, je třeba provést další filtrování, aby se odstranily překrývající se obrazy.</span><span class="sxs-lookup"><span data-stu-id="f8c28-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="f8c28-347">Přidejte metodu `FilterBoundingBoxes` `ParseOutputs` volanou pod metodu:</span><span class="sxs-lookup"><span data-stu-id="f8c28-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="f8c28-348">Uvnitř `FilterBoundingBoxes` metody začněte vytvořením pole rovnajícímse velikosti zjištěných polí a označením všech slotů jako aktivních nebo připravených ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="f8c28-349">Potom seřaďte seznam obsahující ohraničovací rámečky v sestupném pořadí na základě spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="f8c28-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="f8c28-350">Poté vytvořte seznam pro uložení filtrovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="f8c28-351">Začněte zpracovávat každý ohraničovací rámeček iteracem nad každým z ohraničovacích rámečků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="f8c28-352">Uvnitř tohoto for-loop zkontrolujte, zda lze zpracovat aktuální ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="f8c28-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="f8c28-353">Pokud ano, přidejte ohraničovací rámeček do seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="f8c28-354">Pokud výsledky překročí stanovený limit krabic, které mají být extrahovány, vylomte ze smyčky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-354">If the results exceed the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="f8c28-355">Do příkazu if přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f8c28-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="f8c28-356">V opačném případě se podívejte na sousední ohraničovací rámečky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="f8c28-357">Pod zaškrtnutí políčka přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f8c28-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="f8c28-358">Stejně jako první pole, pokud je sousední pole aktivní `IntersectionOverUnion` nebo připraveno ke zpracování, použijte metodu ke kontrole, zda první a druhé pole překračují zadanou prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="f8c28-359">Přidejte následující kód do nejvnitřnější ho smyčky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-359">Add the following code to your innermost for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="f8c28-360">Mimo vnitřní nejvíce for-loop, který kontroluje sousední ohraničovací rámečky, zjistěte, zda existují zbývající ohraničovací rámečky, které mají být zpracovány.</span><span class="sxs-lookup"><span data-stu-id="f8c28-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="f8c28-361">Pokud ne, vypukne z vnější smyčky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="f8c28-362">Nakonec mimo počáteční for-loop `FilterBoundingBoxes` metody vrátí výsledky:</span><span class="sxs-lookup"><span data-stu-id="f8c28-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="f8c28-363">Výborně!</span><span class="sxs-lookup"><span data-stu-id="f8c28-363">Great!</span></span> <span data-ttu-id="f8c28-364">Nyní je čas použít tento kód spolu s modelem pro bodování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="f8c28-365">Použití modelu pro vyhodnocování</span><span class="sxs-lookup"><span data-stu-id="f8c28-365">Use the model for scoring</span></span>

<span data-ttu-id="f8c28-366">Stejně jako u post-processing, existuje několik kroků v bodování kroky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="f8c28-367">Chcete-li pomoci s tím, přidejte třídu, která bude obsahovat logiku hodnocení do projektu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="f8c28-368">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8c28-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f8c28-369">V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="f8c28-370">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="f8c28-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f8c28-371">V editoru kódu se otevře *OnnxModelScorer.cs* soubor.</span><span class="sxs-lookup"><span data-stu-id="f8c28-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="f8c28-372">Na začátek `using` *OnnxModelScorer.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="f8c28-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="f8c28-373">Uvnitř `OnnxModelScorer` definice třídy přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8c28-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="f8c28-374">Přímo pod tím vytvořte konstruktor pro třídu, `OnnxModelScorer` která inicializuje dříve definované proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8c28-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="f8c28-375">Po vytvoření konstruktoru definujte několik struktur, které obsahují proměnné související s nastavením obrazu a modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="f8c28-376">Vytvořte strukturu `ImageNetSettings` volanou tak, aby obsahovala očekávanou výšku a šířku jako vstup pro model.</span><span class="sxs-lookup"><span data-stu-id="f8c28-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="f8c28-377">Poté vytvořte další strukturu `TinyYoloModelSettings` nazvanou, která obsahuje názvy vstupních a výstupních vrstev modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-377">After that, create another struct called `TinyYoloModelSettings` that contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="f8c28-378">Chcete-li vizualizovat název vstupních a výstupních vrstev modelu, můžete použít nástroj, jako je [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="f8c28-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="f8c28-379">Dále vytvořte první sadu metod, které se používají pro vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="f8c28-380">Vytvořte `LoadModel` metodu `OnnxModelScorer` uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="f8c28-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="f8c28-381">Uvnitř `LoadModel` metody přidejte následující kód pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="f8c28-382">ML.NET kanály potřebují znát schéma dat pracovat, když [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="f8c28-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="f8c28-383">V tomto případě bude použit proces podobný tréninku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="f8c28-384">Protože se však neprovádí žádné skutečné školení, [`IDataView`](xref:Microsoft.ML.IDataView)je přijatelné použít prázdný .</span><span class="sxs-lookup"><span data-stu-id="f8c28-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f8c28-385">Vytvořte [`IDataView`](xref:Microsoft.ML.IDataView) nový pro kanál z prázdného seznamu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="f8c28-386">Pod tím definujte kanál.</span><span class="sxs-lookup"><span data-stu-id="f8c28-386">Below that, define the pipeline.</span></span> <span data-ttu-id="f8c28-387">Kanál se bude skládat ze čtyř transformací.</span><span class="sxs-lookup"><span data-stu-id="f8c28-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="f8c28-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)načte obraz jako bitmapu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="f8c28-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)změní měřítko obrázku na zadanou velikost `416 x 416`(v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="f8c28-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="f8c28-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)změní reprezentaci obrazu obrazových bodů z bitmapy na číselný vektor.</span><span class="sxs-lookup"><span data-stu-id="f8c28-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="f8c28-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)načte model ONNX a použije jej ke skóre na poskytnutých datech.</span><span class="sxs-lookup"><span data-stu-id="f8c28-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="f8c28-392">Definujte kanál `LoadModel` v metodě pod proměnnou. `data`</span><span class="sxs-lookup"><span data-stu-id="f8c28-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="f8c28-393">Nyní je čas na vytvoření instance modelu pro bodování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="f8c28-394">Volání [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metody na kanálu a vrátit ji k dalšímu zpracování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="f8c28-395">Jakmile je model načten, lze jej potom použít k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="f8c28-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="f8c28-396">Chcete-li tento proces usnadnit, vytvořte metodu volanou `PredictDataUsingModel` pod `LoadModel` metodou.</span><span class="sxs-lookup"><span data-stu-id="f8c28-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="f8c28-397">Uvnitř `PredictDataUsingModel`, přidejte následující kód pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="f8c28-398">Potom použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu k skóre dat.</span><span class="sxs-lookup"><span data-stu-id="f8c28-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="f8c28-399">Extrahujte předpokládané pravděpodobnosti a vraťte je pro další zpracování.</span><span class="sxs-lookup"><span data-stu-id="f8c28-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="f8c28-400">Nyní, když jsou nastaveny oba kroky, zkombinujte je do jedné metody.</span><span class="sxs-lookup"><span data-stu-id="f8c28-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="f8c28-401">Pod `PredictDataUsingModel` metodu přidejte novou `Score`metodu nazvanou .</span><span class="sxs-lookup"><span data-stu-id="f8c28-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="f8c28-402">Už jsem skoro tam!</span><span class="sxs-lookup"><span data-stu-id="f8c28-402">Almost there!</span></span> <span data-ttu-id="f8c28-403">Nyní je čas, aby to všechno k použití.</span><span class="sxs-lookup"><span data-stu-id="f8c28-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="f8c28-404">Detekce objektů</span><span class="sxs-lookup"><span data-stu-id="f8c28-404">Detect objects</span></span>

<span data-ttu-id="f8c28-405">Nyní, když je všechna instalace dokončena, je čas zjistit některé objekty.</span><span class="sxs-lookup"><span data-stu-id="f8c28-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="f8c28-406">Začněte přidáním odkazů na střelce a analyzátor ve vaší *třídě Program.cs.*</span><span class="sxs-lookup"><span data-stu-id="f8c28-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="f8c28-407">Skóre a analyzovat výstupy modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-407">Score and parse model outputs</span></span>

<span data-ttu-id="f8c28-408">Uvnitř `Main` metody *Program.cs* třídy přidejte příkaz try-catch.</span><span class="sxs-lookup"><span data-stu-id="f8c28-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="f8c28-409">Uvnitř `try` bloku začněte implementovat logiku detekce objektů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="f8c28-410">Nejprve načtěte [`IDataView`](xref:Microsoft.ML.IDataView)data do .</span><span class="sxs-lookup"><span data-stu-id="f8c28-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="f8c28-411">Potom vytvořte instanci `OnnxModelScorer` a použijte ji k skóre načtených dat.</span><span class="sxs-lookup"><span data-stu-id="f8c28-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="f8c28-412">Nyní je čas na post-processing krok.</span><span class="sxs-lookup"><span data-stu-id="f8c28-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="f8c28-413">Vytvořte instanci `YoloOutputParser` a použijte ji ke zpracování výstupu modelu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="f8c28-414">Jakmile je výstup modelu zpracován, je čas nakreslit ohraničovací rámečky na obrázcích.</span><span class="sxs-lookup"><span data-stu-id="f8c28-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="f8c28-415">Vizualizace předpovědí</span><span class="sxs-lookup"><span data-stu-id="f8c28-415">Visualize predictions</span></span>

<span data-ttu-id="f8c28-416">Poté, co model zaznamenal obrázky a výstupy byly zpracovány, ohraničovací rámečky musí být nakresleny na obrázku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="f8c28-417">Chcete-li tak učinit, `DrawBoundingBox` přidejte metodu volanou pod metodu `GetAbsolutePath` uvnitř *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="f8c28-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="f8c28-418">Nejprve načtěte obrázek a získejte `DrawBoundingBox` rozměry výšky a šířky v metodě.</span><span class="sxs-lookup"><span data-stu-id="f8c28-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="f8c28-419">Potom vytvořte smyčku for-each, která bude iterátovat každý z ohraničovacích rámečků zjištěných modelem.</span><span class="sxs-lookup"><span data-stu-id="f8c28-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="f8c28-420">Uvnitř smyčky pro každý získáte rozměry ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="f8c28-421">Vzhledem k tomu, že rozměry ohraničovacího rámečku `416 x 416`odpovídají vstupu modelu , změňte měřítko rozměrů ohraničovacího rámečku tak, aby odpovídaly skutečné velikosti obrazu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="f8c28-422">Potom definujte šablonu pro text, který se zobrazí nad každým ohraničovacím rámečkem.</span><span class="sxs-lookup"><span data-stu-id="f8c28-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="f8c28-423">Text bude obsahovat třídu objektu uvnitř příslušného ohraničovacího rámečku a také spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="f8c28-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="f8c28-424">Chcete-li kreslit na obrázek, [`Graphics`](xref:System.Drawing.Graphics) převeďte jej na objekt.</span><span class="sxs-lookup"><span data-stu-id="f8c28-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="f8c28-425">Uvnitř `using` bloku kódu vylaďte [`Graphics`](xref:System.Drawing.Graphics) nastavení objektu grafiky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="f8c28-426">Pod tím nastavte volby písma a barev pro text a ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="f8c28-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="f8c28-427">Vytvořte a vyplňte obdélník nad ohraničovacím rámečkem, [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) aby obsahoval text pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="f8c28-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="f8c28-428">To pomůže kontrast textu a zlepšit čitelnost.</span><span class="sxs-lookup"><span data-stu-id="f8c28-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="f8c28-429">Potom nakreslete text a ohraničovací rámeček na obrázek pomocí metod [`DrawString`](xref:System.Drawing.Graphics.DrawString*) a. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)</span><span class="sxs-lookup"><span data-stu-id="f8c28-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="f8c28-430">Mimo smyčku for-each přidejte kód pro `outputDirectory`uložení obrázků v .</span><span class="sxs-lookup"><span data-stu-id="f8c28-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="f8c28-431">Pro další zpětnou vazbu, že aplikace je vytváření předpovědi podle očekávání za běhu, přidejte metodu volanou `LogDetectedObjects` pod `DrawBoundingBox` metodou v *souboru Program.cs* k výstupu zjištěných objektů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f8c28-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="f8c28-432">Nyní, když máte pomocné metody k vytvoření vizuální zpětné vazby z předpovědi, přidejte for-loop iterovat přes každý z skórované obrázky.</span><span class="sxs-lookup"><span data-stu-id="f8c28-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="f8c28-433">Uvnitř for-loop získáte název souboru obrázku a ohraničovací chodnících, které jsou s ním spojené.</span><span class="sxs-lookup"><span data-stu-id="f8c28-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="f8c28-434">Pod tím použijte `DrawBoundingBox` metodu k nakreslení ohraničovacích rámečků na obrázku.</span><span class="sxs-lookup"><span data-stu-id="f8c28-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="f8c28-435">Nakonec použijte metodu `LogDetectedObjects` k výstupu předpovědi do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f8c28-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="f8c28-436">Po try-catch prohlášení, přidejte další logiku označující proces probíhá.</span><span class="sxs-lookup"><span data-stu-id="f8c28-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="f8c28-437">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="f8c28-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="f8c28-438">Výsledky</span><span class="sxs-lookup"><span data-stu-id="f8c28-438">Results</span></span>

<span data-ttu-id="f8c28-439">Po provedení předchozích kroků spusťte konzolovou aplikaci (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="f8c28-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="f8c28-440">Výsledky by měly být podobné následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="f8c28-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="f8c28-441">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="f8c28-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

<span data-ttu-id="f8c28-442">Chcete-li zobrazit obrázky s ohraničovacími rámečky, přejděte do `assets/images/output/` adresáře.</span><span class="sxs-lookup"><span data-stu-id="f8c28-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="f8c28-443">Níže je ukázka z jednoho ze zpracovaných obrázků.</span><span class="sxs-lookup"><span data-stu-id="f8c28-443">Below is a sample from one of the processed images.</span></span>

![Ukázkový zpracovaný obraz jídelny](./media/object-detection-onnx/dinning-room-table-chairs.png)

<span data-ttu-id="f8c28-445">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="f8c28-445">Congratulations!</span></span> <span data-ttu-id="f8c28-446">Nyní jste úspěšně vytvořili model strojového učení pro detekci `ONNX` objektů opětovným použitím předem trénovaného modelu v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f8c28-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="f8c28-447">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)</span><span class="sxs-lookup"><span data-stu-id="f8c28-447">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="f8c28-448">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="f8c28-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f8c28-449">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="f8c28-449">Understand the problem</span></span>
> - <span data-ttu-id="f8c28-450">Zjistěte, co je ONNX a jak funguje s ML.NET</span><span class="sxs-lookup"><span data-stu-id="f8c28-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="f8c28-451">Porozumět modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-451">Understand the model</span></span>
> - <span data-ttu-id="f8c28-452">Opětovné použití předem trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="f8c28-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="f8c28-453">Detekce objektů s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="f8c28-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="f8c28-454">Podívejte se na ukázky Machine Learning úložiště GitHub prozkoumat rozbalené ukázky detekce objektů.</span><span class="sxs-lookup"><span data-stu-id="f8c28-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f8c28-455">úložiště GitHub u dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="f8c28-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
