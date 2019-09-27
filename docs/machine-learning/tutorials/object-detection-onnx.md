---
title: 'Kurz: Rozpoznávání objektů pomocí hloubkového učení s ONNX a ML.NET'
description: V tomto kurzu se dozvíte, jak pomocí předem připraveného modelu ONNX hloubkového učení v ML.NET detekovat objekty v obrázcích.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4856608e2c944c3a0fee65a328076bf1581f3d2a
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332624"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="99051-103">Kurz: Rozpoznávání objektů pomocí ONNX v ML.NET</span><span class="sxs-lookup"><span data-stu-id="99051-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="99051-104">Naučte se používat předem vyškolený model ONNX v ML.NET ke zjišťování objektů v obrázcích.</span><span class="sxs-lookup"><span data-stu-id="99051-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="99051-105">Školení modelu detekce objektu od začátku vyžaduje nastavení milionů parametrů, velké množství označených školicích dat a obrovské množství výpočetních prostředků (stovky hodin GPU).</span><span class="sxs-lookup"><span data-stu-id="99051-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="99051-106">Použití předem připraveného modelu vám umožní zástupce školicího procesu.</span><span class="sxs-lookup"><span data-stu-id="99051-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="99051-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="99051-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="99051-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="99051-108">Understand the problem</span></span>
> - <span data-ttu-id="99051-109">Zjistěte, co je ONNX a jak funguje s ML.NET</span><span class="sxs-lookup"><span data-stu-id="99051-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="99051-110">Pochopení modelu</span><span class="sxs-lookup"><span data-stu-id="99051-110">Understand the model</span></span>
> - <span data-ttu-id="99051-111">Opakované použití předem připraveného modelu</span><span class="sxs-lookup"><span data-stu-id="99051-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="99051-112">Detekovat objekty s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="99051-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="99051-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99051-113">Pre-requisites</span></span>

- <span data-ttu-id="99051-114">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="99051-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="99051-115">Balíček NuGet Microsoft.ML</span><span class="sxs-lookup"><span data-stu-id="99051-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="99051-116">Balíček NuGet Microsoft. ML. ImageAnalytics</span><span class="sxs-lookup"><span data-stu-id="99051-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="99051-117">Balíček NuGet Microsoft. ML. OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="99051-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="99051-118">YOLOv2 předučený model s drobnými verzemi</span><span class="sxs-lookup"><span data-stu-id="99051-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/tiny_yolov2)
- <span data-ttu-id="99051-119">[Netron](https://github.com/lutzroeder/netron) volitelné</span><span class="sxs-lookup"><span data-stu-id="99051-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="99051-120">Přehled ukázky rozpoznávání objektů ONNX</span><span class="sxs-lookup"><span data-stu-id="99051-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="99051-121">Tato ukázka vytvoří konzolovou aplikaci .NET Core, která detekuje objekty v rámci Image pomocí předem připraveného modelu ONNX hloubkového učení.</span><span class="sxs-lookup"><span data-stu-id="99051-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="99051-122">Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="99051-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="99051-123">Co je rozpoznávání objektů?</span><span class="sxs-lookup"><span data-stu-id="99051-123">What is object detection?</span></span>

<span data-ttu-id="99051-124">Detekce objektu je problém počítačové vize.</span><span class="sxs-lookup"><span data-stu-id="99051-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="99051-125">V úzce souvisejícím s klasifikací imagí provádí detekce objektů klasifikaci obrázků v podrobnějším měřítku.</span><span class="sxs-lookup"><span data-stu-id="99051-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="99051-126">Detekce objektů vyhledává _a_ kategorizuje entity v rámci imagí.</span><span class="sxs-lookup"><span data-stu-id="99051-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="99051-127">Použijte detekci objektů, pokud obrázky obsahují více objektů různých typů.</span><span class="sxs-lookup"><span data-stu-id="99051-127">Use object detection when images contain multiple objects of different types.</span></span>

![Souběžné obrázky znázorňující klasifikaci obrázku psa na levé straně a klasifikace objektů skupiny v rámci psa se zobrazí vpravo.](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="99051-129">Mezi případy použití při detekci objektu patří:</span><span class="sxs-lookup"><span data-stu-id="99051-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="99051-130">Osobní hnací automobily</span><span class="sxs-lookup"><span data-stu-id="99051-130">Self-Driving Cars</span></span>
- <span data-ttu-id="99051-131">Robotika</span><span class="sxs-lookup"><span data-stu-id="99051-131">Robotics</span></span>
- <span data-ttu-id="99051-132">Rozpoznávání tváře</span><span class="sxs-lookup"><span data-stu-id="99051-132">Face Detection</span></span>
- <span data-ttu-id="99051-133">Bezpečnost na pracovišti</span><span class="sxs-lookup"><span data-stu-id="99051-133">Workplace Safety</span></span>
- <span data-ttu-id="99051-134">Počítání objektů</span><span class="sxs-lookup"><span data-stu-id="99051-134">Object Counting</span></span>
- <span data-ttu-id="99051-135">Rozpoznávání aktivit</span><span class="sxs-lookup"><span data-stu-id="99051-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="99051-136">Vyberte model hloubkového učení.</span><span class="sxs-lookup"><span data-stu-id="99051-136">Select a deep learning model</span></span>

<span data-ttu-id="99051-137">Obsáhlý Learning je podmnožinou strojového učení.</span><span class="sxs-lookup"><span data-stu-id="99051-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="99051-138">Aby bylo možné naučit modely hloubkového učení, jsou potřeba velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="99051-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="99051-139">Vzory v datech jsou reprezentovány řadou vrstev.</span><span class="sxs-lookup"><span data-stu-id="99051-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="99051-140">Vztahy v datech jsou kódovány jako připojení mezi vrstvami, které obsahují váhy.</span><span class="sxs-lookup"><span data-stu-id="99051-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="99051-141">Čím vyšší je váha, tím silnější je vztah.</span><span class="sxs-lookup"><span data-stu-id="99051-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="99051-142">Souhrnně je tato série vrstev a připojení známá jako umělá neuronové síť.</span><span class="sxs-lookup"><span data-stu-id="99051-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="99051-143">Více vrstev v síti, "hlubší", je díky tomu rozsáhlá neuronové síť.</span><span class="sxs-lookup"><span data-stu-id="99051-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="99051-144">Existují různé typy sítí neuronové, nejběžnější jsou vícevrstvé Perceptron (MLP), konvoluční neuronové Network (CNN) a znovu aktuální neuronové síť (RNN).</span><span class="sxs-lookup"><span data-stu-id="99051-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="99051-145">Nejzákladnější je MLP, který mapuje sadu vstupů na sadu výstupů.</span><span class="sxs-lookup"><span data-stu-id="99051-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="99051-146">Tato neuronové síť je dobrá, pokud data neobsahují prostorová nebo časová komponenta.</span><span class="sxs-lookup"><span data-stu-id="99051-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="99051-147">CNN využívá vrstvy konvoluční ke zpracování prostorových informací obsažených v datech.</span><span class="sxs-lookup"><span data-stu-id="99051-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="99051-148">Dobrým případem použití pro DNN je zpracování obrazu k detekci přítomnosti funkce v oblasti obrázku (například je tam uprostřed obrázku nějaký nos?).</span><span class="sxs-lookup"><span data-stu-id="99051-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="99051-149">Nakonec RNN umožní, aby se jako vstup použila trvalá stavová nebo paměť.</span><span class="sxs-lookup"><span data-stu-id="99051-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="99051-150">RNN se používají pro analýzu časových řad, kde je důležité sekvenční řazení a kontext událostí.</span><span class="sxs-lookup"><span data-stu-id="99051-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="99051-151">Pochopení modelu</span><span class="sxs-lookup"><span data-stu-id="99051-151">Understand the model</span></span>

<span data-ttu-id="99051-152">Detekce objektu je úloha zpracování obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-152">Object detection is an image processing task.</span></span> <span data-ttu-id="99051-153">Proto se většina modelů hloubkového učení, které jsou vyškolené k vyřešení tohoto problému, DNN.</span><span class="sxs-lookup"><span data-stu-id="99051-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="99051-154">Model použitý v tomto kurzu je malý model YOLOv2, což je kompaktnější verze modelu YOLOv2 popsané v dokumentu: ["YOLO9000: Lepší, rychlejší a silnější "od Redmon a Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="99051-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="99051-155">Drobný YOLOv2 je vyškolená pro datovou sadu Pascal a skládá se z 15 vrstev, které mohou odhadnout 20 různých tříd objektů.</span><span class="sxs-lookup"><span data-stu-id="99051-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="99051-156">Vzhledem k tomu, že malá YOLOv2 je Zhuštěná verze původního modelu YOLOv2, je mezi rychlostí a přesností provedeno kompromis.</span><span class="sxs-lookup"><span data-stu-id="99051-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="99051-157">Různé vrstvy, které tvoří model, lze vizuálně vymezit pomocí nástrojů, jako je Netron.</span><span class="sxs-lookup"><span data-stu-id="99051-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="99051-158">Kontrola modelu by způsobila mapování propojení mezi všemi vrstvami tvořící neuronové síť, kde každá z vrstev obsahuje název vrstvy spolu s rozměry příslušného vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="99051-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="99051-159">Datové struktury používané k popisu vstupů a výstupů modelu jsou známé jako modely.</span><span class="sxs-lookup"><span data-stu-id="99051-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="99051-160">Křížové procesory si můžete představit jako kontejnery, které ukládají data v N-dimenzích.</span><span class="sxs-lookup"><span data-stu-id="99051-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="99051-161">V případě malých YOLOv2 je `image` název vstupní vrstvy a očekává se tensor dimenzí. `3 x 416 x 416`</span><span class="sxs-lookup"><span data-stu-id="99051-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="99051-162">Název výstupní vrstvy je `grid` a generuje výstupní tensor dimenzí. `125 x 13 x 13`</span><span class="sxs-lookup"><span data-stu-id="99051-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Vstupní vrstva je rozdělená na skryté vrstvy a pak na výstupní vrstvu.](./media/object-detection-onnx/netron-model-map.png)

<span data-ttu-id="99051-164">Model YOLO přebírá obrázek `3(RGB) x 416px x 416px`.</span><span class="sxs-lookup"><span data-stu-id="99051-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="99051-165">Model provede tento vstup a předá jej prostřednictvím různých vrstev a vytvoří výstup.</span><span class="sxs-lookup"><span data-stu-id="99051-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="99051-166">Výstup rozdělí vstupní obrázek do `13 x 13` mřížky, přičemž každou buňku v mřížce `125` tvoří hodnoty.</span><span class="sxs-lookup"><span data-stu-id="99051-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="99051-167">Co je model ONNX?</span><span class="sxs-lookup"><span data-stu-id="99051-167">What is an ONNX model?</span></span>

<span data-ttu-id="99051-168">Open neuronové Network Exchange (ONNX) je open source formát pro modely AI.</span><span class="sxs-lookup"><span data-stu-id="99051-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="99051-169">ONNX podporuje interoperabilitu mezi platformami.</span><span class="sxs-lookup"><span data-stu-id="99051-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="99051-170">To znamená, že můžete model vytvořit v jedné z mnoha oblíbených rozhraní pro strojové učení, jako je PyTorch, převést ho do formátu ONNX a spotřebovat model ONNX v jiném rozhraní jako ML.NET.</span><span class="sxs-lookup"><span data-stu-id="99051-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="99051-171">Další informace najdete na [webu ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="99051-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![ONNX podporované formáty, které se importují do ONNX, a pak se používají jinými formáty podporovanými ONNX](./media/object-detection-onnx/onnx-frameworks.png)

<span data-ttu-id="99051-173">Předem vyškolený neYOLOv2 model je uložený ve formátu ONNX, serializovaná reprezentace vrstev a zjištěné vzory těchto vrstev.</span><span class="sxs-lookup"><span data-stu-id="99051-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="99051-174">V ml.NET se vzájemná spolupráce s ONNX dosahuje [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) pomocí [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) balíčků NuGet a.</span><span class="sxs-lookup"><span data-stu-id="99051-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="99051-175">[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) Balíček obsahuje řadu transformací, které přijímají obrázek a zakódují je do numerických hodnot, které lze použít jako vstup do předpovědi nebo školicího kanálu.</span><span class="sxs-lookup"><span data-stu-id="99051-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="99051-176">[`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) Balíček využívá modul runtime ONNX k načtení modelu ONNX a použije ho k tomu, aby předpovědi na základě poskytnutého vstupu.</span><span class="sxs-lookup"><span data-stu-id="99051-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![Tok dat ONNX souboru do modulu runtime ONNX a nakonec do C# aplikace](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="99051-178">Nastavení projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="99051-178">Set up the .NET Core project</span></span>

<span data-ttu-id="99051-179">Teď, když máte obecné informace o tom, co ONNX je a jak malý YOLOv2 funguje, je čas sestavit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="99051-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="99051-180">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="99051-180">Create a console application</span></span>

1. <span data-ttu-id="99051-181">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "ObjectDetection".</span><span class="sxs-lookup"><span data-stu-id="99051-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="99051-182">Nainstalujte **balíček NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="99051-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="99051-183">V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="99051-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="99051-184">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="99051-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="99051-185">Vyberte tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="99051-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="99051-186">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="99051-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="99051-187">Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics** a **Microsoft. ml. OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="99051-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="99051-188">Příprava dat a předem vyškoleného modelu</span><span class="sxs-lookup"><span data-stu-id="99051-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="99051-189">Stáhněte si [soubor zip adresáře prostředků projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="99051-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="99051-190">Zkopírujte adresář do adresáře projektu *ObjectDetection.* `assets`</span><span class="sxs-lookup"><span data-stu-id="99051-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="99051-191">Tento adresář a jeho podadresáře obsahují soubory obrázků (kromě nemalého modelu YOLOv2, který si stáhnete a přidáte v dalším kroku) potřebného pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="99051-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="99051-192">Stáhněte si [malý YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [modelu ONNX pro zoologickéii](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="99051-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="99051-193">Otevřete příkazový řádek a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="99051-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="99051-194">Zkopírujte extrahovaný `model.onnx` soubor z adresáře a pak ho přejmenujte do adresáře `assets\Model` projektu ObjectDetection a přejmenujte ho na. `TinyYolo2_model.onnx`</span><span class="sxs-lookup"><span data-stu-id="99051-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="99051-195">Tento adresář obsahuje model potřebný pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="99051-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="99051-196">V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="99051-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="99051-197">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="99051-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="99051-198">Vytváření tříd a definování cest</span><span class="sxs-lookup"><span data-stu-id="99051-198">Create classes and define paths</span></span>

<span data-ttu-id="99051-199">Otevřete soubor *program.cs* a na začátek souboru přidejte následující `using` další příkazy:</span><span class="sxs-lookup"><span data-stu-id="99051-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="99051-200">Dále definujte cesty různých prostředků.</span><span class="sxs-lookup"><span data-stu-id="99051-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="99051-201">Nejprve do `Program` třídy přidejte `GetAbsolutePath` metodu `Main` pod metodu.</span><span class="sxs-lookup"><span data-stu-id="99051-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="99051-202">Pak uvnitř `Main` metody vytvořte pole pro uložení umístění vašich assetů.</span><span class="sxs-lookup"><span data-stu-id="99051-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="99051-203">Přidejte do projektu nový adresář, do kterého se budou ukládat vstupní data a třídy předpovědi.</span><span class="sxs-lookup"><span data-stu-id="99051-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="99051-204">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak vyberte **Přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="99051-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="99051-205">Když se nová složka zobrazí v Průzkumník řešení, pojmenujte ji "datastructures".</span><span class="sxs-lookup"><span data-stu-id="99051-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="99051-206">Vytvořte vstupní datovou třídu v nově vytvořených adresářích *Datastrukturas* .</span><span class="sxs-lookup"><span data-stu-id="99051-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="99051-207">V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *datastrukturas* a pak vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="99051-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="99051-208">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="99051-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="99051-209">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="99051-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99051-210">V editoru kódu se otevře soubor *ImageNetData.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="99051-211">Do horní části `using` *ImageNetData.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="99051-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="99051-212">Odeberte existující definici třídy a přidejte následující kód pro `ImageNetData` třídu do souboru *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="99051-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="99051-213">`ImageNetData`je třída vstupních dat obrázku a obsahuje následující <xref:System.String> pole:</span><span class="sxs-lookup"><span data-stu-id="99051-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="99051-214">`ImagePath`obsahuje cestu, kde je obrázek uložen.</span><span class="sxs-lookup"><span data-stu-id="99051-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="99051-215">`Label`obsahuje název souboru.</span><span class="sxs-lookup"><span data-stu-id="99051-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="99051-216">Kromě toho `ImageNetData` obsahuje metodu `ReadFromFile` , která načte více souborů `imageFolder` obrázků uložených v `ImageNetData` zadané cestě a vrátí je jako kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="99051-216">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="99051-217">Vytvořte třídu předpovědi v adresáři *datastruktuře* .</span><span class="sxs-lookup"><span data-stu-id="99051-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="99051-218">V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *datastrukturas* a pak vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="99051-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="99051-219">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="99051-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="99051-220">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="99051-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99051-221">V editoru kódu se otevře soubor *ImageNetPrediction.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="99051-222">Do horní části `using` *ImageNetPrediction.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="99051-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="99051-223">Odeberte existující definici třídy a přidejte následující kód pro `ImageNetPrediction` třídu do souboru *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="99051-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="99051-224">`ImageNetPrediction`je třída dat předpovědi a má následující `float[]` pole:</span><span class="sxs-lookup"><span data-stu-id="99051-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="99051-225">`PredictedLabel`obsahuje rozměry, skóre objektů a pravděpodobnosti třídy pro každé z ohraničujících polí zjištěných v obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-225">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="99051-226">Inicializovat proměnné v Main</span><span class="sxs-lookup"><span data-stu-id="99051-226">Initialize variables in Main</span></span>

<span data-ttu-id="99051-227">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="99051-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="99051-228">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="99051-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="99051-229">`Main` `MLContext` `outputFolder` Inicializujte proměnnou s novou instancí přidáním následujícího řádku do metody program.cs pod polem. `mlContext`</span><span class="sxs-lookup"><span data-stu-id="99051-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="99051-230">Vytvoření analyzátoru pro výstupy modelu po zpracování</span><span class="sxs-lookup"><span data-stu-id="99051-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="99051-231">Model segmentuje obrázek do `13 x 13` mřížky, kde je `32px x 32px`každá buňka mřížky.</span><span class="sxs-lookup"><span data-stu-id="99051-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="99051-232">Každá buňka mřížky obsahuje 5 potenciálních ohraničovacích rámečků objektů.</span><span class="sxs-lookup"><span data-stu-id="99051-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="99051-233">Ohraničující rámeček má 25 prvků:</span><span class="sxs-lookup"><span data-stu-id="99051-233">A bounding box has  25 elements:</span></span>

![Ukázka mřížky vlevo a vzorek ohraničovacího rámečku na pravé straně](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="99051-235">`x`pozice x středu ohraničovacího boxu vzhledem k buňce mřížky, ke které je přidružena.</span><span class="sxs-lookup"><span data-stu-id="99051-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="99051-236">`y`pozice y ohraničovacího boxu v středu vzhledem k buňce mřížky, ke které je přidružena.</span><span class="sxs-lookup"><span data-stu-id="99051-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="99051-237">`w`Šířka ohraničovacího rámečku</span><span class="sxs-lookup"><span data-stu-id="99051-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="99051-238">`h`Výška ohraničovacího rámečku</span><span class="sxs-lookup"><span data-stu-id="99051-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="99051-239">`o`Hodnota spolehlivosti, kterou objekt existuje v ohraničujícím poli, označované také jako skóre objektu.</span><span class="sxs-lookup"><span data-stu-id="99051-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="99051-240">`p1-p20`pravděpodobnost třídy pro každou 20 tříd, které jsou předpovězeny modelem.</span><span class="sxs-lookup"><span data-stu-id="99051-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="99051-241">Celkem 25 prvků popisujících každé 5 ohraničujících polí tvoří prvky 125 obsažené v každé buňce mřížky.</span><span class="sxs-lookup"><span data-stu-id="99051-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="99051-242">Výstup generovaný předučeným ONNX modelem je float Array Length `21125`, který představuje prvky tensor s rozměry. `125 x 13 x 13`</span><span class="sxs-lookup"><span data-stu-id="99051-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="99051-243">Aby bylo možné transformovat předpovědi generované modelem na tensor, je nutné provést některé práce po zpracování.</span><span class="sxs-lookup"><span data-stu-id="99051-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="99051-244">Provedete to tak, že vytvoříte sadu tříd, které vám pomůžou analyzovat výstup.</span><span class="sxs-lookup"><span data-stu-id="99051-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="99051-245">Přidáním nového adresáře do projektu můžete uspořádat sadu tříd analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="99051-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="99051-246">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak vyberte **Přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="99051-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="99051-247">Když se nová složka zobrazí v Průzkumník řešení, pojmenujte ji "YoloParser".</span><span class="sxs-lookup"><span data-stu-id="99051-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="99051-248">Vytváření ohraničovacích rámečků a dimenzí</span><span class="sxs-lookup"><span data-stu-id="99051-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="99051-249">Výstup dat modelu obsahuje souřadnice a rozměry ohraničujících polí objektů v rámci obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="99051-250">Vytvořte základní třídu pro dimenze.</span><span class="sxs-lookup"><span data-stu-id="99051-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="99051-251">V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *YoloParser* a pak vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="99051-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="99051-252">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="99051-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="99051-253">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="99051-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99051-254">V editoru kódu se otevře soubor *DimensionsBase.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="99051-255">Odeberte všechny `using` příkazy a existující definici třídy.</span><span class="sxs-lookup"><span data-stu-id="99051-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="99051-256">Do souboru DimensionsBase.cs přidejte následující kód `DimensionsBase` pro třídu:</span><span class="sxs-lookup"><span data-stu-id="99051-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="99051-257">`DimensionsBase`má následující `float` pole:</span><span class="sxs-lookup"><span data-stu-id="99051-257">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="99051-258">`X`obsahuje pozici objektu podél osy x.</span><span class="sxs-lookup"><span data-stu-id="99051-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="99051-259">`Y`obsahuje pozici objektu podél osy y.</span><span class="sxs-lookup"><span data-stu-id="99051-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="99051-260">`Height`obsahuje výšku objektu.</span><span class="sxs-lookup"><span data-stu-id="99051-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="99051-261">`Width`obsahuje šířku objektu.</span><span class="sxs-lookup"><span data-stu-id="99051-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="99051-262">Dále vytvořte třídu pro vaše ohraničovací rámečky.</span><span class="sxs-lookup"><span data-stu-id="99051-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="99051-263">V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *YoloParser* a pak vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="99051-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="99051-264">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="99051-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="99051-265">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="99051-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99051-266">V editoru kódu se otevře soubor *YoloBoundingBox.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="99051-267">Do horní části `using` *YoloBoundingBox.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="99051-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="99051-268">Hned nad existující definicí třídy přidejte novou definici třídy s názvem `BoundingBoxDimensions` , která dědí `DimensionsBase` z třídy, aby obsahovala rozměry příslušného ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="99051-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="99051-269">Odeberte existující `YoloBoundingBox` definici třídy a přidejte následující kód `YoloBoundingBox` pro třídu do souboru *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="99051-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="99051-270">`YoloBoundingBox`má následující pole:</span><span class="sxs-lookup"><span data-stu-id="99051-270">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="99051-271">`Dimensions`obsahuje rozměry ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="99051-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="99051-272">`Label`obsahuje třídu objektu zjištěnou v ohraničujícím poli.</span><span class="sxs-lookup"><span data-stu-id="99051-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="99051-273">`Confidence`obsahuje jistotu třídy.</span><span class="sxs-lookup"><span data-stu-id="99051-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="99051-274">`Rect`obsahuje obdélníkové vyjádření rozměrů ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="99051-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="99051-275">`BoxColor`obsahuje barvu spojenou s příslušnou třídou použitou k vykreslení na obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="99051-276">Vytvoření analyzátoru</span><span class="sxs-lookup"><span data-stu-id="99051-276">Create the parser</span></span>

<span data-ttu-id="99051-277">Nyní, když jsou vytvořeny třídy dimenzí a ohraničujících polí, je čas vytvořit analyzátor.</span><span class="sxs-lookup"><span data-stu-id="99051-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="99051-278">V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *YoloParser* a pak vyberte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="99051-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="99051-279">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="99051-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="99051-280">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="99051-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99051-281">V editoru kódu se otevře soubor *YoloOutputParser.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="99051-282">Do horní části `using` *YoloOutputParser.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="99051-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="99051-283">Uvnitř definice existující `YoloOutputParser` třídy přidejte vnořenou třídu, která obsahuje rozměry každé buňky v obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="99051-284">Přidejte následující kód pro `CellDimensions` třídu, která dědí `DimensionsBase` z třídy `YoloOutputParser` v horní části definice třídy.</span><span class="sxs-lookup"><span data-stu-id="99051-284">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="99051-285">Uvnitř definice `YoloOutputParser` třídy přidejte následující konstantu a pole.</span><span class="sxs-lookup"><span data-stu-id="99051-285">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="99051-286">`ROW_COUNT`je počet řádků v mřížce, na který je obrázek rozdělen.</span><span class="sxs-lookup"><span data-stu-id="99051-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="99051-287">`COL_COUNT`je počet sloupců v mřížce, na který je obrázek rozdělen.</span><span class="sxs-lookup"><span data-stu-id="99051-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="99051-288">`CHANNEL_COUNT`je celkový počet hodnot obsažených v jedné buňce mřížky.</span><span class="sxs-lookup"><span data-stu-id="99051-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="99051-289">`BOXES_PER_CELL`je počet ohraničujících polí v buňce,</span><span class="sxs-lookup"><span data-stu-id="99051-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="99051-290">`BOX_INFO_FEATURE_COUNT`je počet funkcí obsažených v rámci pole (x, y, Výška, Šířka, spolehlivost).</span><span class="sxs-lookup"><span data-stu-id="99051-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="99051-291">`CLASS_COUNT`je počet tříd předpovědi obsažených v každém ohraničujícím poli.</span><span class="sxs-lookup"><span data-stu-id="99051-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="99051-292">`CELL_WIDTH`je šířka jedné buňky v mřížce obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="99051-293">`CELL_HEIGHT`je výška jedné buňky v mřížce obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="99051-294">`channelStride`je počáteční pozice aktuální buňky v mřížce.</span><span class="sxs-lookup"><span data-stu-id="99051-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="99051-295">Když model vytvoří předpověď, označovanou také jako bodování, rozdělí `416px x 416px` vstupní obrázek do mřížky buněk `13 x 13`velikosti.</span><span class="sxs-lookup"><span data-stu-id="99051-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="99051-296">Každá buňka obsahuje hodnotu `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="99051-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="99051-297">V každé buňce jsou 5 ohraničujících polí, z nichž každý obsahuje 5 funkcí (x, y, Šířka, Výška, spolehlivost).</span><span class="sxs-lookup"><span data-stu-id="99051-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="99051-298">Kromě toho každý ohraničovací rámeček obsahuje pravděpodobnost každé třídy, která v tomto případě je 20.</span><span class="sxs-lookup"><span data-stu-id="99051-298">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="99051-299">Každá buňka proto obsahuje 125 informací (5 funkcí + 20 pravděpodobností třídy).</span><span class="sxs-lookup"><span data-stu-id="99051-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="99051-300">`channelStride` Pro všechna 5 ohraničovacích rámečků vytvořte seznam ukotvení:</span><span class="sxs-lookup"><span data-stu-id="99051-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="99051-301">Kotvy jsou předem definované poměry výšky a šířky ohraničujících polí.</span><span class="sxs-lookup"><span data-stu-id="99051-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="99051-302">Většina objektů nebo tříd zjištěných modelem má podobné poměry.</span><span class="sxs-lookup"><span data-stu-id="99051-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="99051-303">To je výhodné při vytváření ohraničujících rámečků.</span><span class="sxs-lookup"><span data-stu-id="99051-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="99051-304">Místo předpovědi ohraničujících polí se počítá posun z předdefinovaných dimenzí a proto se zkrátí výpočet vyžadovaný pro předpověď ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="99051-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="99051-305">Tyto poměry kotvy jsou obvykle počítány na základě použité datové sady.</span><span class="sxs-lookup"><span data-stu-id="99051-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="99051-306">V tomto případě, protože je známá datová sada a hodnoty byly předem vypočítány, kotvy mohou být pevně kódované.</span><span class="sxs-lookup"><span data-stu-id="99051-306">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="99051-307">Dále definujte popisky nebo třídy, které bude model předpovědět.</span><span class="sxs-lookup"><span data-stu-id="99051-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="99051-308">Tento model předpovídá 20 tříd, které jsou podmnožinou celkového počtu tříd předpokládaných původním YOLOv2m modelem.</span><span class="sxs-lookup"><span data-stu-id="99051-308">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="99051-309">Přidejte seznam popisků pod `anchors`.</span><span class="sxs-lookup"><span data-stu-id="99051-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="99051-310">Ke každé z těchto tříd jsou přiřazeny barvy.</span><span class="sxs-lookup"><span data-stu-id="99051-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="99051-311">Přiřaďte barvy vaší třídy pod `labels`vaše:</span><span class="sxs-lookup"><span data-stu-id="99051-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="99051-312">Vytváření pomocných funkcí</span><span class="sxs-lookup"><span data-stu-id="99051-312">Create helper functions</span></span>

<span data-ttu-id="99051-313">Ve fázi následného zpracování se účastní řada kroků.</span><span class="sxs-lookup"><span data-stu-id="99051-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="99051-314">V takovém případě je možné využít několik pomocných metod.</span><span class="sxs-lookup"><span data-stu-id="99051-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="99051-315">Pomocné metody používané v analyzátoru jsou:</span><span class="sxs-lookup"><span data-stu-id="99051-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="99051-316">`Sigmoid`použije funkci sigmoid, která vypíše číslo mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="99051-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="99051-317">`Softmax`normalizuje vstupní vektor na rozdělení pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="99051-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="99051-318">`GetOffset`mapuje prvky ve výstupu jednorozměrného modelu na odpovídající pozici v `125 x 13 x 13` tensor.</span><span class="sxs-lookup"><span data-stu-id="99051-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="99051-319">`ExtractBoundingBoxes`extrahuje dimenze ohraničovacího rámečku pomocí `GetOffset` metody z výstupu modelu.</span><span class="sxs-lookup"><span data-stu-id="99051-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="99051-320">`GetConfidence`extrahuje hodnotu spolehlivosti, která určuje, jak se v modelu zjistilo, že byl zjištěn objekt a `Sigmoid` pomocí funkce jej zapíná na procento.</span><span class="sxs-lookup"><span data-stu-id="99051-320">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="99051-321">`MapBoundingBoxToCell`používá rozměry ohraničovacího boxu a mapuje je na příslušnou buňku v rámci obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="99051-322">`ExtractClasses`extrahuje třídu předpovědi pro ohraničující rámeček z výstupu modelu pomocí `GetOffset` metody a převede je na rozdělení pravděpodobnosti `Softmax` pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="99051-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="99051-323">`GetTopResult`vybere třídu ze seznamu předpokládaných tříd s nejvyšší pravděpodobností.</span><span class="sxs-lookup"><span data-stu-id="99051-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="99051-324">`IntersectionOverUnion`filtry překrývající ohraničovací rámečky s nižší pravděpodobností.</span><span class="sxs-lookup"><span data-stu-id="99051-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="99051-325">Přidejte kód pro všechny pomocné metody pod seznam `classColors`.</span><span class="sxs-lookup"><span data-stu-id="99051-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="99051-326">Po definování všech pomocných metod je čas je použít ke zpracování výstupu modelu.</span><span class="sxs-lookup"><span data-stu-id="99051-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="99051-327">`IntersectionOverUnion` Pod metodou`ParseOutputs` vytvořte metodu pro zpracování výstupu generovaného modelem.</span><span class="sxs-lookup"><span data-stu-id="99051-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="99051-328">Vytvořte seznam pro ukládání ohraničujících polí a definujte proměnné uvnitř `ParseOutputs` metody.</span><span class="sxs-lookup"><span data-stu-id="99051-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="99051-329">Každý obrázek je rozdělen do mřížky `13 x 13` buněk.</span><span class="sxs-lookup"><span data-stu-id="99051-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="99051-330">Každá buňka obsahuje pět ohraničujících rámečků.</span><span class="sxs-lookup"><span data-stu-id="99051-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="99051-331">`boxes` Pod proměnnou přidejte kód pro zpracování všech polí v každé z buněk.</span><span class="sxs-lookup"><span data-stu-id="99051-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="99051-332">Uvnitř cyklické smyčky Vypočítejte počáteční pozici aktuálního pole ve výstupu jednorozměrného modelu.</span><span class="sxs-lookup"><span data-stu-id="99051-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="99051-333">Přímo pod ním použijte `ExtractBoundingBoxDimensions` metodu k získání rozměrů aktuálního ohraničovacího boxu.</span><span class="sxs-lookup"><span data-stu-id="99051-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="99051-334">Pak použijte `GetConfidence` metodu k získání důvěry pro aktuální ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="99051-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="99051-335">Potom použijte `MapBoundingBoxToCell` metodu k namapování aktuálního ohraničovacího boxu na aktuálně zpracovávanou buňku.</span><span class="sxs-lookup"><span data-stu-id="99051-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="99051-336">Před provedením dalšího zpracování ověřte, zda je hodnota spolehlivosti větší, než je zadaná prahová hodnota.</span><span class="sxs-lookup"><span data-stu-id="99051-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="99051-337">Pokud ne, zpracujte další ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="99051-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="99051-338">V opačném případě pokračujte ve zpracování výstupu.</span><span class="sxs-lookup"><span data-stu-id="99051-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="99051-339">Dalším krokem je získání pravděpodobnosti rozdělení předpokládaných tříd pro aktuální ohraničovací rámeček pomocí `ExtractClasses` metody.</span><span class="sxs-lookup"><span data-stu-id="99051-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="99051-340">Pak použijte `GetTopResult` metodu k získání hodnoty a indexu třídy s nejvyšší pravděpodobností pro aktuální pole a výpočet svého skóre.</span><span class="sxs-lookup"><span data-stu-id="99051-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="99051-341">`topScore` Použijte k opětovnému zadání jenom těch ohraničujících rámečků, které jsou nad určenou prahovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="99051-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="99051-342">Nakonec, pokud aktuální ohraničující rámeček překračuje prahovou hodnotu, vytvořte nový `BoundingBox` objekt a přidejte ho `boxes` do seznamu.</span><span class="sxs-lookup"><span data-stu-id="99051-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="99051-343">Po zpracování všech buněk v imagi vrátí `boxes` seznam.</span><span class="sxs-lookup"><span data-stu-id="99051-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="99051-344">Do `ParseOutputs` metody přidejte následující návratový příkaz pod nejvíce vnější smyčka for-Loop.</span><span class="sxs-lookup"><span data-stu-id="99051-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="99051-345">Filtrovat překrývající se rámečky</span><span class="sxs-lookup"><span data-stu-id="99051-345">Filter overlapping boxes</span></span>

<span data-ttu-id="99051-346">Teď, když se všechna vysoce důvěrně ohraničená pole extrahují z výstupu modelu, je potřeba provést další filtrování, aby se překrývající image odebraly.</span><span class="sxs-lookup"><span data-stu-id="99051-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="99051-347">Přidejte metodu nazvanou `FilterBoundingBoxes` `ParseOutputs` pod metodu:</span><span class="sxs-lookup"><span data-stu-id="99051-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="99051-348">`FilterBoundingBoxes` Uvnitř metody Začněte tím, že vytvoříte pole, které se rovná velikosti zjištěných polí, a označíte všechny sloty jako aktivní nebo připravené ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="99051-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="99051-349">Pak seřaďte seznam obsahující vaše ohraničující pole v sestupném pořadí na základě jistoty.</span><span class="sxs-lookup"><span data-stu-id="99051-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="99051-350">Potom vytvořte seznam pro ukládání filtrovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="99051-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="99051-351">Zahajte zpracování každého ohraničovacího rámečku tak, že do každého ohraničovacího pole zahájíte iteraci.</span><span class="sxs-lookup"><span data-stu-id="99051-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="99051-352">Uvnitř tohoto cyklu for-Loop ověřte, zda je možné zpracovat aktuální ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="99051-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="99051-353">Pokud ano, přidejte ohraničovací rámeček do seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="99051-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="99051-354">Pokud výsledky překročí zadaný limit pro extrakci, zrušte rozdělení smyčky.</span><span class="sxs-lookup"><span data-stu-id="99051-354">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="99051-355">Do příkazu if-přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="99051-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="99051-356">V opačném případě se podívejte na sousedící ohraničovací rámečky.</span><span class="sxs-lookup"><span data-stu-id="99051-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="99051-357">Pod kontrolu limitu pole přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="99051-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="99051-358">Podobně jako v prvním poli, pokud je sousední pole aktivní nebo připravené ke zpracování, použijte `IntersectionOverUnion` metodu ke kontrole, zda první pole a druhé pole překročí zadanou prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="99051-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="99051-359">Přidejte následující kód do vnitřní smyčky for Loop.</span><span class="sxs-lookup"><span data-stu-id="99051-359">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="99051-360">Mimo vnitřní smyčku for-Loop, která kontroluje sousední ohraničená pole, se podívejte, zda existují zbývající ohraničovací rámečky, které mají být zpracovány.</span><span class="sxs-lookup"><span data-stu-id="99051-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="99051-361">Pokud ne, přerušte vnější smyčka for-Loop.</span><span class="sxs-lookup"><span data-stu-id="99051-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="99051-362">Nakonec, mimo počáteční cyklus smyčky `FilterBoundingBoxes` pro metodu, vrátí výsledky:</span><span class="sxs-lookup"><span data-stu-id="99051-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="99051-363">Výborně!</span><span class="sxs-lookup"><span data-stu-id="99051-363">Great!</span></span> <span data-ttu-id="99051-364">Nyní je čas použít tento kód spolu s modelem pro bodování.</span><span class="sxs-lookup"><span data-stu-id="99051-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="99051-365">Použití modelu pro bodování</span><span class="sxs-lookup"><span data-stu-id="99051-365">Use the model for scoring</span></span>

<span data-ttu-id="99051-366">Stejně jako u následného zpracování je několik kroků v postupu hodnocení.</span><span class="sxs-lookup"><span data-stu-id="99051-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="99051-367">K tomu je potřeba přidat třídu, která bude obsahovat logiku bodování pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="99051-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="99051-368">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="99051-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="99051-369">V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="99051-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="99051-370">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="99051-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99051-371">V editoru kódu se otevře soubor *OnnxModelScorer.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="99051-372">Do horní části `using` *OnnxModelScorer.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="99051-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="99051-373">Do definice `OnnxModelScorer` třídy přidejte následující proměnné.</span><span class="sxs-lookup"><span data-stu-id="99051-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="99051-374">Přímo pod tím vytvořte konstruktor pro `OnnxModelScorer` třídu, která bude inicializovat dříve definované proměnné.</span><span class="sxs-lookup"><span data-stu-id="99051-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="99051-375">Po vytvoření konstruktoru definujte několik struktur, které obsahují proměnné související s nastavením obrázku a modelu.</span><span class="sxs-lookup"><span data-stu-id="99051-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="99051-376">Vytvořte strukturu s názvem `ImageNetSettings` , aby obsahovala výšku a šířku očekávanou jako vstup pro model.</span><span class="sxs-lookup"><span data-stu-id="99051-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="99051-377">Potom vytvořte další strukturu s názvem `TinyYoloModelSettings` , která obsahuje názvy vstupní a výstupní vrstvy modelu.</span><span class="sxs-lookup"><span data-stu-id="99051-377">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="99051-378">Chcete-li vizualizovat název vstupní a výstupní vrstvy modelu, můžete použít nástroj, jako je [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="99051-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="99051-379">Dále vytvořte první sadu metod, které se použijí pro bodování.</span><span class="sxs-lookup"><span data-stu-id="99051-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="99051-380">Vytvořte metodu uvnitř vaší `OnnxModelScorer` třídy. `LoadModel`</span><span class="sxs-lookup"><span data-stu-id="99051-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="99051-381">`LoadModel` Uvnitř metody přidejte následující kód pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="99051-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="99051-382">Kanály ml.NET musí znát schéma dat, aby fungovalo při [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) volání metody.</span><span class="sxs-lookup"><span data-stu-id="99051-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="99051-383">V takovém případě se použije proces podobný školení.</span><span class="sxs-lookup"><span data-stu-id="99051-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="99051-384">Vzhledem k tomu, že nedojde k žádnému skutečnému školení, je přijatelné použít [`IDataView`](xref:Microsoft.ML.IDataView)prázdné.</span><span class="sxs-lookup"><span data-stu-id="99051-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="99051-385">Vytvořte nový [`IDataView`](xref:Microsoft.ML.IDataView) pro kanál z prázdného seznamu.</span><span class="sxs-lookup"><span data-stu-id="99051-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="99051-386">Níže definujte kanál.</span><span class="sxs-lookup"><span data-stu-id="99051-386">Below that, define the pipeline.</span></span> <span data-ttu-id="99051-387">Kanál se skládá ze čtyř transformací.</span><span class="sxs-lookup"><span data-stu-id="99051-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="99051-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)načte obrázek jako rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="99051-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="99051-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)změní měřítko obrázku na zadanou velikost (v tomto případě `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="99051-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="99051-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)změní reprezentace obrázku z rastrového obrázku na číselný vektor.</span><span class="sxs-lookup"><span data-stu-id="99051-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="99051-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)Načte model ONNX a použije ho ke stanovení skóre z poskytnutých dat.</span><span class="sxs-lookup"><span data-stu-id="99051-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="99051-392">V `LoadModel` metodě`data` pod proměnnou definujte svůj kanál.</span><span class="sxs-lookup"><span data-stu-id="99051-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="99051-393">Nyní je čas vytvořit instanci modelu pro bodování.</span><span class="sxs-lookup"><span data-stu-id="99051-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="99051-394">[`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) Zavolejte metodu na kanálu a vraťte ji k dalšímu zpracování.</span><span class="sxs-lookup"><span data-stu-id="99051-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="99051-395">Po načtení modelu je možné ho použít k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="99051-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="99051-396">Pro usnadnění tohoto procesu vytvořte metodu nazvanou `PredictDataUsingModel` `LoadModel` pod metodou.</span><span class="sxs-lookup"><span data-stu-id="99051-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="99051-397">Dovnitř do `PredictDataUsingModel`přidejte následující kód pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="99051-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="99051-398">Pak použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu k vyhodnocení dat.</span><span class="sxs-lookup"><span data-stu-id="99051-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="99051-399">Extrakce předpokládaných pravděpodobností a jejich vrácení pro další zpracování.</span><span class="sxs-lookup"><span data-stu-id="99051-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="99051-400">Teď, když jsou oba kroky nastavené, je zkombinovat do jediné metody.</span><span class="sxs-lookup"><span data-stu-id="99051-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="99051-401">Pod metodou přidejte novou metodu s názvem `Score`. `PredictDataUsingModel`</span><span class="sxs-lookup"><span data-stu-id="99051-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="99051-402">Už to skoro je!</span><span class="sxs-lookup"><span data-stu-id="99051-402">Almost there!</span></span> <span data-ttu-id="99051-403">Teď je čas na to, aby se všechno používalo.</span><span class="sxs-lookup"><span data-stu-id="99051-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="99051-404">Detekovat objekty</span><span class="sxs-lookup"><span data-stu-id="99051-404">Detect objects</span></span>

<span data-ttu-id="99051-405">Po dokončení celého nastavení je čas detekovat některé objekty.</span><span class="sxs-lookup"><span data-stu-id="99051-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="99051-406">Začněte tím, že přidáte odkazy na skore a analyzátor ve vaší třídě *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="99051-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="99051-407">Skóre a analýza výstupů modelu</span><span class="sxs-lookup"><span data-stu-id="99051-407">Score and parse model outputs</span></span>

<span data-ttu-id="99051-408">V rámci metody třídy program.cs přidejte příkaz try-catch. `Main`</span><span class="sxs-lookup"><span data-stu-id="99051-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="99051-409">`try` Uvnitř bloku začněte implementací logiky detekce objektů.</span><span class="sxs-lookup"><span data-stu-id="99051-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="99051-410">Nejdřív načtěte data do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="99051-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="99051-411">Pak vytvořte instanci `OnnxModelScorer` a použijte ji k vyhodnocení načtených dat.</span><span class="sxs-lookup"><span data-stu-id="99051-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="99051-412">Nyní je čas pro krok po zpracování.</span><span class="sxs-lookup"><span data-stu-id="99051-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="99051-413">Vytvořte instanci `YoloOutputParser` a použijte ji ke zpracování výstupu modelu.</span><span class="sxs-lookup"><span data-stu-id="99051-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="99051-414">Až se výstup modelu zpracuje, je čas vykreslit ohraničovací rámečky na obrázcích.</span><span class="sxs-lookup"><span data-stu-id="99051-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="99051-415">Vizualizovat předpovědi</span><span class="sxs-lookup"><span data-stu-id="99051-415">Visualize predictions</span></span>

<span data-ttu-id="99051-416">Poté, co model vyhodnotí obrázky a byly zpracovány výstupy, musí být ohraničovací pole vykreslena na obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="99051-417">Uděláte to tak, že do *program.cs*přidáte `DrawBoundingBox` metodu, `GetAbsolutePath` která je volána pod metodou.</span><span class="sxs-lookup"><span data-stu-id="99051-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="99051-418">Nejdřív načtěte obrázek a v `DrawBoundingBox` metodě Získejte rozměry výšky a šířky.</span><span class="sxs-lookup"><span data-stu-id="99051-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="99051-419">Pak vytvořte smyčku For-Each k iterování každého ohraničovacího pole zjištěného modelem.</span><span class="sxs-lookup"><span data-stu-id="99051-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="99051-420">Uvnitř smyčky for-each Získejte rozměry ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="99051-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="99051-421">Vzhledem k tomu, že rozměry ohraničovacího rámečku odpovídají vstupnímu typu `416 x 416`, Škálujte rozměry ohraničovacího pole tak, aby odpovídaly skutečné velikosti obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="99051-422">Pak definujte šablonu pro text, který se zobrazí nad každým ohraničujícím polem.</span><span class="sxs-lookup"><span data-stu-id="99051-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="99051-423">Text bude obsahovat třídu objektu uvnitř příslušného ohraničovacího rámečku a také jistotu.</span><span class="sxs-lookup"><span data-stu-id="99051-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="99051-424">Chcete-li kreslit na obrázek, převeďte jej na [`Graphics`](xref:System.Drawing.Graphics) objekt.</span><span class="sxs-lookup"><span data-stu-id="99051-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="99051-425">[`Graphics`](xref:System.Drawing.Graphics) V bloku `using` kódu vyladění nastavení objektu grafiky.</span><span class="sxs-lookup"><span data-stu-id="99051-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="99051-426">Níže můžete nastavit možnosti písma a barvy pro text a ohraničovací rámeček.</span><span class="sxs-lookup"><span data-stu-id="99051-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="99051-427">Vytvořte a vyplňte obdélník nad ohraničujícím polem, který bude obsahovat text pomocí [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) metody.</span><span class="sxs-lookup"><span data-stu-id="99051-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="99051-428">To vám pomůže kontrastovat text a zlepšit čitelnost.</span><span class="sxs-lookup"><span data-stu-id="99051-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="99051-429">Pak nakreslete text a ohraničovací rámeček na obrázku pomocí [`DrawString`](xref:System.Drawing.Graphics.DrawString*) metod a. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)</span><span class="sxs-lookup"><span data-stu-id="99051-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="99051-430">Mimo smyčku For-Each přidejte kód pro uložení obrázků v `outputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="99051-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="99051-431">Pro další zpětnou vazbu, kterou aplikace provádí předpovědi podle očekávání za běhu, přidejte metodu, `LogDetectedObjects` která je `DrawBoundingBox` volána pod metodou v souboru *program.cs* pro výstup zjištěných objektů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="99051-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="99051-432">Teď, když máte pomocné metody k vytvoření vizuální zpětné vazby z předpovědi, přidejte smyčku for-Loop k iterování všech imagí s hodnocením.</span><span class="sxs-lookup"><span data-stu-id="99051-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="99051-433">Uvnitř smyčky for-Loop Získá název souboru obrázku a ohraničená pole, která jsou k němu přidružená.</span><span class="sxs-lookup"><span data-stu-id="99051-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="99051-434">Níže použijte `DrawBoundingBox` metodu pro vykreslení ohraničujících polí na obrázku.</span><span class="sxs-lookup"><span data-stu-id="99051-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="99051-435">Nakonec použijte `LogDetectedObjects` metodu pro výstup předpovědi do konzoly.</span><span class="sxs-lookup"><span data-stu-id="99051-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="99051-436">Po příkazu try-catch přidejte další logiku, která indikuje, že proces je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="99051-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="99051-437">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="99051-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="99051-438">Výsledky</span><span class="sxs-lookup"><span data-stu-id="99051-438">Results</span></span>

<span data-ttu-id="99051-439">Po provedení předchozích kroků spusťte konzolovou aplikaci (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="99051-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="99051-440">Výsledky by měly být podobné následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="99051-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="99051-441">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="99051-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="99051-442">Chcete-li zobrazit obrázky s ohraničujícími poli, přejděte do `assets/images/output/` adresáře.</span><span class="sxs-lookup"><span data-stu-id="99051-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="99051-443">Níže je ukázka z jedné ze zpracovaných imagí.</span><span class="sxs-lookup"><span data-stu-id="99051-443">Below is a sample from one of the processed images.</span></span>

![Ukázka zpracovaného obrázku dinning místnosti](./media/object-detection-onnx/image3.jpg)

<span data-ttu-id="99051-445">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="99051-445">Congratulations!</span></span> <span data-ttu-id="99051-446">Nyní jste úspěšně vytvořili model strojového učení pro detekci objektů opětovným použitím předem připraveného `ONNX` modelu v ml.NET.</span><span class="sxs-lookup"><span data-stu-id="99051-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="99051-447">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .</span><span class="sxs-lookup"><span data-stu-id="99051-447">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="99051-448">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="99051-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="99051-449">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="99051-449">Understand the problem</span></span>
> - <span data-ttu-id="99051-450">Zjistěte, co je ONNX a jak funguje s ML.NET</span><span class="sxs-lookup"><span data-stu-id="99051-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="99051-451">Pochopení modelu</span><span class="sxs-lookup"><span data-stu-id="99051-451">Understand the model</span></span>
> - <span data-ttu-id="99051-452">Opakované použití předem připraveného modelu</span><span class="sxs-lookup"><span data-stu-id="99051-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="99051-453">Detekovat objekty s načteným modelem</span><span class="sxs-lookup"><span data-stu-id="99051-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="99051-454">Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku detekce rozbaleného objektu.</span><span class="sxs-lookup"><span data-stu-id="99051-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="99051-455">dotnet/machinelearning-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="99051-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
