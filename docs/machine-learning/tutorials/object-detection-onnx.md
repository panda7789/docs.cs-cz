---
title: 'Kurz: Detekce objektů pomocí modelu hlubokého učení ONNX'
description: Tento kurz ukazuje, jak používat předem trénovaný model hlubokého učení ONNX v ML.NET k detekci objektů v obrazech.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ff9986c09e39f5c4d24f52c351db6455ff63e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092717"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Kurz: Detekce objektů používajících ONNX v ML.NET

Naučte se používat předem trénovaný model ONNX v ML.NET k detekci objektů v obrazech.

Trénování modelu detekce objektů od začátku vyžaduje nastavení milionů parametrů, velké množství trénovacích dat označených popiskem a obrovské množství výpočetních prostředků (stovky hodin GPU). Použití předem trénovaného modelu umožňuje zkrátit proces školení.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Pochopení problému
> - Zjistěte, co je ONNX a jak funguje s ML.NET
> - Porozumět modelu
> - Opětovné použití předem trénovaného modelu
> - Detekce objektů s načteným modelem

## <a name="pre-requisites"></a>Požadavky

- [Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".
- [Microsoft.ML Balíček NuGet](https://www.nuget.org/packages/Microsoft.ML/)
- [Balíček Microsoft.ML.ImageAnalytics NuGet](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Balíček Microsoft.ML.OnnxTransformer NuGet](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Malý YOLOv2 předem vyškolený model](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) (volitelně)

## <a name="onnx-object-detection-sample-overview"></a>Ukázka detekce objektů ONNX – přehled

Tato ukázka vytvoří aplikaci konzoly .NET core, která detekuje objekty v rámci bitové kopie pomocí předem trénovaného modelu ONNX s hloubkovým učením. Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) na GitHubu.

## <a name="what-is-object-detection"></a>Co je detekce objektů?

Detekce objektů je problém s počítačovým viděním. Zatímco úzce souvisí s klasifikací obrazu, detekce objektů provádí klasifikaci obrazu v podrobnějším měřítku. Detekce objektů vyhledá _a_ kategorizuje entity v rámci bitových kopií. Detekce objektů použijte, pokud obrazy obsahují více objektů různých typů.

![Snímky obrazovky znázorňující klasifikaci obrázků versus klasifikaci objektů.](./media/object-detection-onnx/img-classification-obj-detection.png)

Některé případy použití pro detekci objektů patří:

- Samořiditelná auta
- Robotika
- Detekce obličeje
- Bezpečnost na pracovišti
- Počítání objektů
- Rozpoznávání aktivit

## <a name="select-a-deep-learning-model"></a>Výběr modelu hlubokého učení

Hluboké učení je podmnožinou strojového učení. Pro trénování modelů hlubokého učení je vyžadováno velké množství dat. Vzorky v datech jsou reprezentovány řadou vrstev. Vztahy v datech jsou kódovány jako spojení mezi vrstvami obsahujícími závaží. Čím vyšší je váha, tím silnější je vztah. Společně, tato řada vrstev a připojení jsou známé jako umělé neuronové sítě. Čím více vrstev v síti, tím "hlubší" je, což z ní činí hlubokou neuronovou síť.

Existují různé typy neuronových sítí, nejběžnější je vícevrstvý perceptron (MLP), konvoluční neuronová síť (CNN) a rekurentní neuronová síť (RNN). Nejzákladnější je MLP, který mapuje sadu vstupů na sadu výstupů. Tato neuronová síť je dobrá, když data nemají prostorovou nebo časovou složku. CNN využívá konvoluční vrstvy ke zpracování prostorových informací obsažených v datech. Dobrým případem použití pro CNNs je zpracování obrazu pro detekci přítomnosti prvku v oblasti obrazu (například je nos ve středu obrazu?). Nakonec rnns umožňují trvalost stavu nebo paměti, které mají být použity jako vstup. RNNs se používají pro analýzu časových řad, kde je důležité sekvenční řazení a kontext událostí.

### <a name="understand-the-model"></a>Porozumět modelu

Detekce objektů je úloha zpracování obrazu. Proto většina modelů hlubokého učení vyškolených k vyřešení tohoto problému jsou CNNs. Model použitý v tomto tutoriálu je model Tiny YOLOv2, kompaktnější verze modelu YOLOv2 popsaná v dokumentu: ["YOLO9000: Lepší, rychlejší, silnější" od Redmon a Fadhari](https://arxiv.org/pdf/1612.08242.pdf). Tiny YOLOv2 je trénovaný na datové sadě Pascal VOC a skládá se z 15 vrstev, které dokáží předpovědět 20 různých tříd objektů. Vzhledem k tomu, že Tiny YOLOv2 je zkrácená verze původního modelu YOLOv2, je proveden kompromis mezi rychlostí a přesností. Různé vrstvy, které tvoří model, lze vizualizovat pomocí nástrojů, jako je Netron. Kontrola modelu by přinesla mapování spojení mezi všemi vrstvami, které tvoří neuronovou síť, kde by každá vrstva obsahovala název vrstvy spolu s rozměry příslušného vstupu / výstupu. Datové struktury používané k popisu vstupů a výstupů modelu jsou označovány jako tenzory. Tenzory si lze myslet jako kontejnery, které ukládají data v N-dimenzích. V případě Tiny YOLOv2 je `image` název vstupní vrstvy a očekává tenzor `3 x 416 x 416`rozměrů . Název výstupní vrstvy `grid` je a generuje výstupní tenzor rozměrů `125 x 13 x 13`.

![Vstupní vrstva je rozdělena do skrytých vrstev a pak výstupní vrstva](./media/object-detection-onnx/netron-model-map-layers.png)

Model YOLO pořídí `3(RGB) x 416px x 416px`obraz . Model převezme tento vstup a předá jej přes různé vrstvy k vytvoření výstupu. Výstup rozdělí vstupní obraz do `13 x 13` mřížky, přičemž každá buňka v mřížce se skládá z `125` hodnot.

### <a name="what-is-an-onnx-model"></a>Co je model ONNX?

Open Neural Network Exchange (ONNX) je open source formát pro modely AI. ONNX podporuje interoperabilitu mezi rámci. To znamená, že můžete trénovat model v jednom z mnoha populárních rámců strojového učení, jako je PyTorch, převést jej do formátu ONNX a spotřebovávat model ONNX v jiném rámci, jako je ML.NET. Chcete-li se dozvědět více, navštivte [webové stránky ONNX](https://onnx.ai/).

![Diagram používaných formátů podporovaných onnx.](./media/object-detection-onnx/onnx-supported-formats.png)

Předem vycvičený model Tiny YOLOv2 je uložen ve formátu ONNX, což je serializovaná reprezentace vrstev a naučených vzorů těchto vrstev. V ML.NET je interoperabilita [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) s [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) ONNX dosažena s balíčky a NuGet. Balíček [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) obsahuje řadu transformací, které berou bitovou kopii a kódují ji do číselných hodnot, které lze použít jako vstup do kanálu předpověď nebo školení. Balíček [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) využívá onnx runtime načíst model ONNX a použít jej k předpovědi na základě vstupní poskytované.

![Tok dat souboru ONNX do runtime ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Nastavení projektu .NET Core

Nyní, když máte obecné znalosti o tom, co je ONNX a jak Funguje Tiny YOLOv2, je čas vytvořit aplikaci.

### <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **aplikaci konzoly .NET Core console** nazvanou "ObjectDetection".

1. Nainstalujte **balíček nuget Microsoft.ML**:

    - V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.
    - Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ML**.
    - Vyberte tlačítko **Instalovat.**
    - V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.
    - Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics** a **Microsoft.ML.OnnxTransformer**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Příprava dat a předem trénovaného modelu

1. Stáhnout [soubor zip adresáře datových zdrojů projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) a rozbalit.

1. Zkopírujte `assets` adresář do adresáře projektu *ObjectDetection.* Tento adresář a jeho podadresáře obsahují obrazové soubory (s výjimkou modelu Tiny YOLOv2, který si stáhnete a přidáte v dalším kroku) potřebné pro tento kurz.

1. Stáhněte si [model Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)a rozbalte.

    Otevřete příkazový řádek a zadejte následující příkaz:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Zkopírujte extrahovaný `model.onnx` soubor z adresáře, který `assets\Model` se rozbalil do adresáře projektu `TinyYolo2_model.onnx` *ObjectDetection,* a přejmenujte jej na . Tento adresář obsahuje model potřebný pro tento kurz.

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na jednotlivé soubory v adresáři datových zdrojů a podadresářích a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

Otevřete *Program.cs* soubor a `using` přidejte do horní části souboru následující další příkazy:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Dále definujte cesty různých prostředků.

1. Nejprve přidejte metodu `GetAbsolutePath` pod metodu `Main` ve `Program` třídě.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Potom uvnitř `Main` metody vytvořte pole pro uložení umístění prostředků.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Přidejte do projektu nový adresář pro ukládání vstupních dat a tříd předpovědi.

V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Když se nová složka zobrazí v Průzkumníku řešení, pojmenujte ji "DataStructures".

Vytvořte třídu vstupních dat v nově vytvořeném *adresáři DataStructures.*

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *DataStructures* a pak vyberte **přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *ImageNetData.cs*. Potom vyberte tlačítko **Přidat.**

    Soubor *ImageNetData.cs* se otevře v editoru kódu. Na začátek `using` *ImageNetData.cs*přidejte následující příkaz :

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Odeberte existující definici třídy `ImageNetData` a přidejte do *ImageNetData.cs* souboru následující kód pro třídu:

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`je třída vstupních obrazových <xref:System.String> dat a má následující pole:

    - `ImagePath`obsahuje cestu, na které je obraz uložen.
    - `Label`obsahuje název souboru.

    Navíc obsahuje `ImageNetData` metodu, `ReadFromFile` která načte více `imageFolder` obrazových souborů uložených `ImageNetData` v zadané cestě a vrátí je jako kolekci objektů.

Vytvořte třídu předpověď v adresáři *DataStructures.*

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *DataStructures* a pak vyberte **přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *ImageNetPrediction.cs*. Potom vyberte tlačítko **Přidat.**

    V editoru kódu se otevře *ImageNetPrediction.cs* soubor. Na začátek `using` *ImageNetPrediction.cs*přidejte následující příkaz :

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Odeberte existující definici třídy `ImageNetPrediction` a přidejte do *ImageNetPrediction.cs* souboru následující kód pro třídu:

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`je třída dat předpověď a `float[]` má následující pole:

    - `PredictedLabel`obsahuje kóty, skóre objektu a pravděpodobnosti třídy pro každý z ohraničovacích rámečků zjištěných v obraze.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v hlavní

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

Inicializovat `mlContext` proměnnou s `MLContext` novou instancí přidáním následujícího řádku k metodě `Main` *Program.cs* pod `outputFolder` polem.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Vytvoření analyzátoru pro výstupy modelu po zpracování

Model segmentuje obraz `13 x 13` do mřížky, kde `32px x 32px`je každá buňka mřížky . Každá buňka mřížky obsahuje 5 polí pro ohraničování potenciálních objektů. Ohraničovací rámeček má 25 prvků:

![Ukázka mřížky vlevo a ukázka ohraničovacího rámečku vpravo](./media/object-detection-onnx/model-output-description.png)

- `x`pozice x středového ohraničovacího rámečku vzhledem k buňce mřížky, ke které je přidružena.
- `y`pozice y středového ohraničovacího rámečku vzhledem k buňce mřížky, ke které je přidružena.
- `w`šířku ohraničovacího rámečku.
- `h`výšku ohraničovacího rámečku.
- `o`hodnota spolehlivosti, která objekt existuje v ohraničovacím rámečku, označovaná také jako skóre objektu.
- `p1-p20`pravděpodobnosti třídy pro každou z 20 tříd předpovídaných modelem.

Celkem 25 prvků popisujících každý z 5 ohraničovacích rámečků tvoří 125 prvků obsažených v každé buňce mřížky.

Výstupem generovaným předem trénovaným modelem ONNX je plovoucí pole délky `21125`, `125 x 13 x 13`představující prvky tenzoru s rozměry . Chcete-li transformovat předpovědi generované modelem do tenzoru, je vyžadována některá práce po zpracování. Chcete-li tak učinit, vytvořte sadu tříd, které vám pomohou analyzovat výstup.

Přidejte do projektu nový adresář pro uspořádání sady tříd analyzátoru.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Když se nová složka zobrazí v Průzkumníku řešení, pojmenujte ji "YoloParser".

### <a name="create-bounding-boxes-and-dimensions"></a>Vytvoření ohraničovacích rámečků a kót

Výstup dat modelem obsahuje souřadnice a rozměry ohraničovacích rámečků objektů v obraze. Vytvořte základní třídu pro kóty.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *YoloParser* a pak vyberte **přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *DimensionsBase.cs*. Potom vyberte tlačítko **Přidat.**

    V editoru kódu se otevře *soubor DimensionsBase.cs.* Odeberte všechny `using` příkazy a existující definici třídy.

    Do souboru `DimensionsBase` *DimensionsBase.cs* přidejte následující kód třídy:

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`má následující `float` vlastnosti:

    - `X`obsahuje polohu objektu podél osy x.
    - `Y`obsahuje polohu objektu podél osy y.
    - `Height`obsahuje výšku objektu.
    - `Width`obsahuje šířku objektu.

Dále vytvořte třídu pro ohraničovací rámečky.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *YoloParser* a pak vyberte **přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *YoloBoundingBox.cs*. Potom vyberte tlačítko **Přidat.**

    V editoru kódu se otevře *YoloBoundingBox.cs* soubor. Na začátek `using` *YoloBoundingBox.cs*přidejte následující příkaz :

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Těsně nad existující definici třídy přidejte novou definici třídy s názvem, `BoundingBoxDimensions` která dědí z `DimensionsBase` třídy, aby obsahovala rozměry příslušného ohraničovacího rámečku.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Odeberte `YoloBoundingBox` existující definici třídy `YoloBoundingBox` a přidejte do *souboru YoloBoundingBox.cs* následující kód pro třídu:

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`má následující vlastnosti:

    - `Dimensions`obsahuje rozměry ohraničovacího rámečku.
    - `Label`obsahuje třídu objektu zjištěnou v ohraničovacím rámečku.
    - `Confidence`obsahuje důvěru třídy.
    - `Rect`obsahuje obdélníkovou reprezentaci rozměrů ohraničovacího rámečku.
    - `BoxColor`obsahuje barvu přidruženou k příslušné třídě použité k kreslení na obrázek.

### <a name="create-the-parser"></a>Vytvoření analyzátoru

Nyní, když jsou vytvořeny třídy pro kóty a ohraničovací rámečky, je čas vytvořit analyzátor.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na adresář *YoloParser* a pak vyberte **přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *YoloOutputParser.cs*. Potom vyberte tlačítko **Přidat.**

    V editoru kódu se otevře *YoloOutputParser.cs* soubor. Na začátek `using` *YoloOutputParser.cs*přidejte následující příkaz :

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Uvnitř existující `YoloOutputParser` definice třídy přidejte vnořenou třídu, která obsahuje rozměry každé buňky v obraze. Přidejte následující kód `CellDimensions` pro třídu, `DimensionsBase` která dědí `YoloOutputParser` z třídy v horní části definice třídy.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Uvnitř `YoloOutputParser` definice třídy přidejte následující konstanty a pole.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`je počet řádků v mřížce, na který je obraz rozdělen.
    - `COL_COUNT`je počet sloupců v mřížce, na který je obraz rozdělen.
    - `CHANNEL_COUNT`je celkový počet hodnot obsažených v jedné buňce mřížky.
    - `BOXES_PER_CELL`je počet ohraničovacích rámečků v buňce,
    - `BOX_INFO_FEATURE_COUNT`je počet prvků obsažených v rámečku (x,y,výška,šířka,spolehlivost).
    - `CLASS_COUNT`je počet předpovědí tříd obsažených v každém ohraničovacím rámečku.
    - `CELL_WIDTH`je šířka jedné buňky v mřížce obrazu.
    - `CELL_HEIGHT`je výška jedné buňky v mřížce obrazu.
    - `channelStride`je počáteční pozice aktuální buňky v mřížce.

    Když model provede předpověď, označovanou také jako `416px x 416px` vyhodnocování, rozdělí `13 x 13`vstupní obraz do mřížky buněk o velikosti . Každá buňka `32px x 32px`obsahuje je . V každé buňce je 5 ohraničovacích rámečků, z nichž každý obsahuje 5 prvků (x, y, šířka, výška, spolehlivost). Kromě toho každý ohraničovací rámeček obsahuje pravděpodobnost každé třídy, která je v tomto případě 20. Proto každá buňka obsahuje 125 kusů informací (5 funkcí + 20 pravděpodobností třídy).

Vytvořte níže uvedený `channelStride` seznam kotev pro všech 5 ohraničovacích rámečků:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Kotvy jsou předem definované poměry výšky a šířky ohraničovacích rámečků. Většina objektů nebo tříd zjištěných modelem má podobné poměry. To je cenné, pokud jde o vytváření ohraničovacích rámečků. Namísto předvídání ohraničovacích rámečků se vypočítá posun od předdefinovaných dimenzí, čímž se sníží výpočet potřebný k předvídání ohraničovacího rámečku. Tyto kotevní poměry se obvykle počítají na základě použité datové sady. V tomto případě vzhledem k tomu, že je datová sada známa a hodnoty byly předem vypočítány, mohou být ukotvení pevně zakódována.

Dále definujte popisky nebo třídy, které bude model předpovídat. Tento model předpovídá 20 tříd, což je podmnožina celkového počtu tříd předpovídaných původním modelem YOLOv2.

Přidejte seznam štítků `anchors`pod .

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Ke každé třídě jsou přidruženy barvy. Přiřaďte barvy `labels`třídy pod :

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Vytváření pomocné funkce

Ve fázi následného zpracování je zapojena řada kroků. Na pomoc s tím lze použít několik pomocných metod.

Pomocné metody používané analyzátorem jsou:

- `Sigmoid`použije sigmoidní funkci, která vypisuje číslo mezi 0 a 1.
- `Softmax`normalizuje vstupní vektor do rozdělení pravděpodobnosti.
- `GetOffset`mapuje prvky v jednorozměrném výstupu modelu `125 x 13 x 13` do odpovídající polohy v tenzoru.
- `ExtractBoundingBoxes`extrahuje kóty ohraničovacího rámečku `GetOffset` metodou z výstupu modelu.
- `GetConfidence`extrahuje hodnotu spolehlivosti, která uvádí, jak jistý je `Sigmoid` model, že detekoval objekt a používá funkci k jeho přeměně na procento.
- `MapBoundingBoxToCell`použije rozměry ohraničovacího rámečku a mapuje je na příslušnou buňku v obraze.
- `ExtractClasses`extrahuje předpovědi třídy pro ohraničovací `GetOffset` rámeček z výstupu modelu pomocí `Softmax` metody a změní je na rozdělení pravděpodobnosti pomocí metody.
- `GetTopResult`vybere třídu ze seznamu předpovídaných tříd s nejvyšší pravděpodobností.
- `IntersectionOverUnion`filtruje překrývající se ohraničovací pole s nižší pravděpodobností.

Přidejte kód pro všechny pomocné metody `classColors`pod seznam .

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Jakmile definujete všechny pomocné metody, je čas je použít ke zpracování výstupu modelu.

Pod `IntersectionOverUnion` metodou vytvořte `ParseOutputs` metodu pro zpracování výstupu generovaného modelem.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Vytvořte seznam pro uložení ohraničovacích `ParseOutputs` rámečků a definování proměnných uvnitř metody.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Každý obrázek je rozdělen `13 x 13` do mřížky buněk. Každá buňka obsahuje pět ohraničovacích rámečků. Pod `boxes` proměnnou přidejte kód pro zpracování všech polí v každé z buněk.

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

Uvnitř smyčky zcela uvnitř vypočítejte počáteční pozici aktuálního pole v rámci výstupu jednorozměrného modelu.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Přímo pod tím `ExtractBoundingBoxDimensions` použijte metodu k získání rozměrů aktuálního ohraničovacího rámečku.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Potom použijte `GetConfidence` metodu k získání jistoty pro aktuální ohraničovací rámeček.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Poté použijte metodu `MapBoundingBoxToCell` k mapování aktuálního ohraničovacího rámečku na aktuální zpracovávanou buňku.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Před dalším zpracováním zkontrolujte, zda je hodnota spolehlivosti větší než stanovená prahová hodnota. Pokud ne, zpracujte další ohraničovací rámeček.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

V opačném případě pokračujte ve zpracování výstupu. Dalším krokem je získání rozdělení pravděpodobnosti předpovídané třídy pro aktuální `ExtractClasses` ohraničovací rámeček pomocí metody.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Potom použijte `GetTopResult` metodu k získání hodnoty a indexu třídy s nejvyšší pravděpodobností pro aktuální pole a vypočítat jeho skóre.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Použijte `topScore` chcete znovu zachovat pouze ty ohraničovací pole, které jsou nad zadanou prahovou hodnotu.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Nakonec, pokud aktuální ohraničovací rámeček `BoundingBox` překročí prahovou hodnotu, vytvořte nový objekt a přidejte jej do `boxes` seznamu.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Po zpracování všech buněk v obraze vraťte `boxes` seznam. Přidejte následující příkaz return pod vnější nejvíce `ParseOutputs` pro smyčku v metodě.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Filtrování překrývajících se polí

Nyní, když byly z výstupu modelu extrahovány všechny vysoce sebevědomé ohraničovací rámečky, je třeba provést další filtrování, aby se odstranily překrývající se obrazy. Přidejte metodu `FilterBoundingBoxes` `ParseOutputs` volanou pod metodu:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Uvnitř `FilterBoundingBoxes` metody začněte vytvořením pole rovnajícímse velikosti zjištěných polí a označením všech slotů jako aktivních nebo připravených ke zpracování.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Potom seřaďte seznam obsahující ohraničovací rámečky v sestupném pořadí na základě spolehlivosti.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Poté vytvořte seznam pro uložení filtrovaných výsledků.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Začněte zpracovávat každý ohraničovací rámeček iteracem nad každým z ohraničovacích rámečků.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Uvnitř tohoto for-loop zkontrolujte, zda lze zpracovat aktuální ohraničovací rámeček.

```csharp
if (isActiveBoxes[i])
{

}
```

Pokud ano, přidejte ohraničovací rámeček do seznamu výsledků. Pokud výsledky překročí stanovený limit krabic, které mají být extrahovány, vylomte ze smyčky. Do příkazu if přidejte následující kód.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

V opačném případě se podívejte na sousední ohraničovací rámečky. Pod zaškrtnutí políčka přidejte následující kód.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Stejně jako první pole, pokud je sousední pole aktivní `IntersectionOverUnion` nebo připraveno ke zpracování, použijte metodu ke kontrole, zda první a druhé pole překračují zadanou prahovou hodnotu. Přidejte následující kód do nejvnitřnější ho smyčky.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Mimo vnitřní nejvíce for-loop, který kontroluje sousední ohraničovací rámečky, zjistěte, zda existují zbývající ohraničovací rámečky, které mají být zpracovány. Pokud ne, vypukne z vnější smyčky.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Nakonec mimo počáteční for-loop `FilterBoundingBoxes` metody vrátí výsledky:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Výborně! Nyní je čas použít tento kód spolu s modelem pro bodování.

## <a name="use-the-model-for-scoring"></a>Použití modelu pro vyhodnocování

Stejně jako u post-processing, existuje několik kroků v bodování kroky. Chcete-li pomoci s tím, přidejte třídu, která bude obsahovat logiku hodnocení do projektu.

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *OnnxModelScorer.cs*. Potom vyberte tlačítko **Přidat.**

    V editoru kódu se otevře *OnnxModelScorer.cs* soubor. Na začátek `using` *OnnxModelScorer.cs*přidejte následující příkaz :

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Uvnitř `OnnxModelScorer` definice třídy přidejte následující proměnné.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Přímo pod tím vytvořte konstruktor pro třídu, `OnnxModelScorer` která inicializuje dříve definované proměnné.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Po vytvoření konstruktoru definujte několik struktur, které obsahují proměnné související s nastavením obrazu a modelu. Vytvořte strukturu `ImageNetSettings` volanou tak, aby obsahovala očekávanou výšku a šířku jako vstup pro model.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Poté vytvořte další strukturu `TinyYoloModelSettings` nazvanou, která obsahuje názvy vstupních a výstupních vrstev modelu. Chcete-li vizualizovat název vstupních a výstupních vrstev modelu, můžete použít nástroj, jako je [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Dále vytvořte první sadu metod, které se používají pro vyhodnocování. Vytvořte `LoadModel` metodu `OnnxModelScorer` uvnitř třídy.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Uvnitř `LoadModel` metody přidejte následující kód pro protokolování.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET kanály potřebují znát schéma dat pracovat, když [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) je volána metoda. V tomto případě bude použit proces podobný tréninku. Protože se však neprovádí žádné skutečné školení, [`IDataView`](xref:Microsoft.ML.IDataView)je přijatelné použít prázdný . Vytvořte [`IDataView`](xref:Microsoft.ML.IDataView) nový pro kanál z prázdného seznamu.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Pod tím definujte kanál. Kanál se bude skládat ze čtyř transformací.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)načte obraz jako bitmapu.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)změní měřítko obrázku na zadanou velikost `416 x 416`(v tomto případě).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)změní reprezentaci obrazu obrazových bodů z bitmapy na číselný vektor.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)načte model ONNX a použije jej ke skóre na poskytnutých datech.

    Definujte kanál `LoadModel` v metodě pod proměnnou. `data`

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Nyní je čas na vytvoření instance modelu pro bodování. Volání [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metody na kanálu a vrátit ji k dalšímu zpracování.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Jakmile je model načten, lze jej potom použít k předpovědi. Chcete-li tento proces usnadnit, vytvořte metodu volanou `PredictDataUsingModel` pod `LoadModel` metodou.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

Uvnitř `PredictDataUsingModel`, přidejte následující kód pro protokolování.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Potom použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu k skóre dat.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Extrahujte předpokládané pravděpodobnosti a vraťte je pro další zpracování.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Nyní, když jsou nastaveny oba kroky, zkombinujte je do jedné metody. Pod `PredictDataUsingModel` metodu přidejte novou `Score`metodu nazvanou .

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Už jsem skoro tam! Nyní je čas, aby to všechno k použití.

## <a name="detect-objects"></a>Detekce objektů

Nyní, když je všechna instalace dokončena, je čas zjistit některé objekty. Začněte přidáním odkazů na střelce a analyzátor ve vaší *třídě Program.cs.*

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Skóre a analyzovat výstupy modelu

Uvnitř `Main` metody *Program.cs* třídy přidejte příkaz try-catch.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

Uvnitř `try` bloku začněte implementovat logiku detekce objektů. Nejprve načtěte [`IDataView`](xref:Microsoft.ML.IDataView)data do .

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Potom vytvořte instanci `OnnxModelScorer` a použijte ji k skóre načtených dat.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Nyní je čas na post-processing krok. Vytvořte instanci `YoloOutputParser` a použijte ji ke zpracování výstupu modelu.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Jakmile je výstup modelu zpracován, je čas nakreslit ohraničovací rámečky na obrázcích.

### <a name="visualize-predictions"></a>Vizualizace předpovědí

Poté, co model zaznamenal obrázky a výstupy byly zpracovány, ohraničovací rámečky musí být nakresleny na obrázku. Chcete-li tak učinit, `DrawBoundingBox` přidejte metodu volanou pod metodu `GetAbsolutePath` uvnitř *Program.cs*.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Nejprve načtěte obrázek a získejte `DrawBoundingBox` rozměry výšky a šířky v metodě.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Potom vytvořte smyčku for-each, která bude iterátovat každý z ohraničovacích rámečků zjištěných modelem.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

Uvnitř smyčky pro každý získáte rozměry ohraničovacího rámečku.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Vzhledem k tomu, že rozměry ohraničovacího rámečku `416 x 416`odpovídají vstupu modelu , změňte měřítko rozměrů ohraničovacího rámečku tak, aby odpovídaly skutečné velikosti obrazu.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Potom definujte šablonu pro text, který se zobrazí nad každým ohraničovacím rámečkem. Text bude obsahovat třídu objektu uvnitř příslušného ohraničovacího rámečku a také spolehlivost.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Chcete-li kreslit na obrázek, [`Graphics`](xref:System.Drawing.Graphics) převeďte jej na objekt.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Uvnitř `using` bloku kódu vylaďte [`Graphics`](xref:System.Drawing.Graphics) nastavení objektu grafiky.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Pod tím nastavte volby písma a barev pro text a ohraničovací rámeček.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Vytvořte a vyplňte obdélník nad ohraničovacím rámečkem, [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) aby obsahoval text pomocí metody. To pomůže kontrast textu a zlepšit čitelnost.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Potom nakreslete text a ohraničovací rámeček na obrázek pomocí metod [`DrawString`](xref:System.Drawing.Graphics.DrawString*) a. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

Mimo smyčku for-each přidejte kód pro `outputDirectory`uložení obrázků v .

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Pro další zpětnou vazbu, že aplikace je vytváření předpovědi podle očekávání za běhu, přidejte metodu volanou `LogDetectedObjects` pod `DrawBoundingBox` metodou v *souboru Program.cs* k výstupu zjištěných objektů do konzoly.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Nyní, když máte pomocné metody k vytvoření vizuální zpětné vazby z předpovědi, přidejte for-loop iterovat přes každý z skórované obrázky.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

Uvnitř for-loop získáte název souboru obrázku a ohraničovací chodnících, které jsou s ním spojené.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Pod tím použijte `DrawBoundingBox` metodu k nakreslení ohraničovacích rámečků na obrázku.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Nakonec použijte metodu `LogDetectedObjects` k výstupu předpovědi do konzoly.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Po try-catch prohlášení, přidejte další logiku označující proces probíhá.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

A to je vše!

## <a name="results"></a>Výsledky

Po provedení předchozích kroků spusťte konzolovou aplikaci (Ctrl + F5). Výsledky by měly být podobné následujícímu výstupu. Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.

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

Chcete-li zobrazit obrázky s ohraničovacími rámečky, přejděte do `assets/images/output/` adresáře. Níže je ukázka z jednoho ze zpracovaných obrázků.

![Ukázkový zpracovaný obraz jídelny](./media/object-detection-onnx/dinning-room-table-chairs.png)

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro detekci `ONNX` objektů opětovným použitím předem trénovaného modelu v ML.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Pochopení problému
> - Zjistěte, co je ONNX a jak funguje s ML.NET
> - Porozumět modelu
> - Opětovné použití předem trénovaného modelu
> - Detekce objektů s načteným modelem

Podívejte se na ukázky Machine Learning úložiště GitHub prozkoumat rozbalené ukázky detekce objektů.
> [!div class="nextstepaction"]
> [úložiště GitHub u dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
