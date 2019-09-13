---
title: 'Kurz: Rozpoznávání objektů pomocí hloubkového učení s ONNX a ML.NET'
description: V tomto kurzu se dozvíte, jak pomocí předem připraveného modelu ONNX hloubkového učení v ML.NET detekovat objekty v obrázcích.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 956cbedd7e354b36c447bdc06ea996948c745264
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929095"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Kurz: Rozpoznávání objektů pomocí ONNX v ML.NET

Naučte se používat předem vyškolený model ONNX v ML.NET ke zjišťování objektů v obrázcích.

Školení modelu detekce objektu od začátku vyžaduje nastavení milionů parametrů, velké množství označených školicích dat a obrovské množství výpočetních prostředků (stovky hodin GPU). Použití předem připraveného modelu vám umožní zástupce školicího procesu.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Pochopení problému
> - Zjistěte, co je ONNX a jak funguje s ML.NET
> - Pochopení modelu
> - Opakované použití předem připraveného modelu
> - Detekovat objekty s načteným modelem

## <a name="pre-requisites"></a>Požadavky

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.
- [Balíček NuGet Microsoft.ML](https://www.nuget.org/packages/Microsoft.ML/)
- [Balíček NuGet Microsoft. ML. ImageAnalytics](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Balíček NuGet Microsoft. ML. OnnxTransformer](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [YOLOv2 předučený model s drobnými verzemi](https://github.com/onnx/models/tree/master/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) volitelné

## <a name="onnx-object-detection-sample-overview"></a>Přehled ukázky rozpoznávání objektů ONNX

Tato ukázka vytvoří konzolovou aplikaci .NET Core, která detekuje objekty v rámci Image pomocí předem připraveného modelu ONNX hloubkového učení. Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) na GitHubu.

## <a name="what-is-object-detection"></a>Co je rozpoznávání objektů?

Detekce objektu je problém počítačové vize. V úzce souvisejícím s klasifikací imagí provádí detekce objektů klasifikaci obrázků v podrobnějším měřítku. Detekce objektů vyhledává _a_ kategorizuje entity v rámci imagí. Použijte detekci objektů, pokud obrázky obsahují více objektů různých typů.

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

Mezi případy použití při detekci objektu patří:

- Osobní hnací automobily
- Robotika
- Rozpoznávání tváře
- Bezpečnost na pracovišti
- Počítání objektů
- Rozpoznávání aktivit

## <a name="select-a-deep-learning-model"></a>Vyberte model hloubkového učení.

Obsáhlý Learning je podmnožinou strojového učení. Aby bylo možné naučit modely hloubkového učení, jsou potřeba velké množství dat. Vzory v datech jsou reprezentovány řadou vrstev. Vztahy v datech jsou kódovány jako připojení mezi vrstvami, které obsahují váhy. Čím vyšší je váha, tím silnější je vztah. Souhrnně je tato série vrstev a připojení známá jako umělá neuronové síť. Více vrstev v síti, "hlubší", je díky tomu rozsáhlá neuronové síť.

Existují různé typy sítí neuronové, nejběžnější jsou vícevrstvé Perceptron (MLP), konvoluční neuronové Network (CNN) a znovu aktuální neuronové síť (RNN). Nejzákladnější je MLP, který mapuje sadu vstupů na sadu výstupů. Tato neuronové síť je dobrá, pokud data neobsahují prostorová nebo časová komponenta. CNN využívá vrstvy konvoluční ke zpracování prostorových informací obsažených v datech. Dobrým případem použití pro DNN je zpracování obrazu k detekci přítomnosti funkce v oblasti obrázku (například je tam uprostřed obrázku nějaký nos?). Nakonec RNN umožní, aby se jako vstup použila trvalá stavová nebo paměť. RNN se používají pro analýzu časových řad, kde je důležité sekvenční řazení a kontext událostí.

### <a name="understand-the-model"></a>Pochopení modelu

Detekce objektu je úloha zpracování obrázku. Proto se většina modelů hloubkového učení, které jsou vyškolené k vyřešení tohoto problému, DNN. Model použitý v tomto kurzu je malý model YOLOv2, což je kompaktnější verze modelu YOLOv2 popsané v dokumentu: ["YOLO9000: Lepší, rychlejší a silnější "od Redmon a Fadhari](https://arxiv.org/pdf/1612.08242.pdf). Drobný YOLOv2 je vyškolená pro datovou sadu Pascal a skládá se z 15 vrstev, které mohou odhadnout 20 různých tříd objektů. Vzhledem k tomu, že malá YOLOv2 je Zhuštěná verze původního modelu YOLOv2, je mezi rychlostí a přesností provedeno kompromis. Různé vrstvy, které tvoří model, lze vizuálně vymezit pomocí nástrojů, jako je Netron. Kontrola modelu by způsobila mapování propojení mezi všemi vrstvami tvořící neuronové síť, kde každá z vrstev obsahuje název vrstvy spolu s rozměry příslušného vstupu/výstupu. Datové struktury používané k popisu vstupů a výstupů modelu jsou známé jako modely. Křížové procesory si můžete představit jako kontejnery, které ukládají data v N-dimenzích. V případě malých YOLOv2 je `image` název vstupní vrstvy a očekává se tensor dimenzí. `3 x 416 x 416` Název výstupní vrstvy je `grid` a generuje výstupní tensor dimenzí. `125 x 13 x 13`

![](./media/object-detection-onnx/netron-model-map.png)

Model YOLO přebírá obrázek `3(RGB) x 416px x 416px`. Model provede tento vstup a předá jej prostřednictvím různých vrstev a vytvoří výstup. Výstup rozdělí vstupní obrázek do `13 x 13` mřížky, přičemž každou buňku v mřížce `125` tvoří hodnoty.

### <a name="what-is-an-onnx-model"></a>Co je model ONNX?

Open neuronové Network Exchange (ONNX) je open source formát pro modely AI. ONNX podporuje interoperabilitu mezi platformami. To znamená, že můžete model vytvořit v jedné z mnoha oblíbených rozhraní pro strojové učení, jako je PyTorch, převést ho do formátu ONNX a spotřebovat model ONNX v jiném rozhraní jako ML.NET. Další informace najdete na [webu ONNX](https://onnx.ai/).

![](./media/object-detection-onnx/onnx-frameworks.png)

Předem vyškolený neYOLOv2 model je uložený ve formátu ONNX, serializovaná reprezentace vrstev a zjištěné vzory těchto vrstev. V ml.NET se vzájemná spolupráce s ONNX dosahuje [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) pomocí [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) balíčků NuGet a. [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) Balíček obsahuje řadu transformací, které přijímají obrázek a zakódují je do numerických hodnot, které lze použít jako vstup do předpovědi nebo školicího kanálu. [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) Balíček využívá modul runtime ONNX k načtení modelu ONNX a použije ho k tomu, aby předpovědi na základě poskytnutého vstupu.

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Nastavení projektu .NET Core

Teď, když máte obecné informace o tom, co ONNX je a jak malý YOLOv2 funguje, je čas sestavit aplikaci.

### <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "ObjectDetection".

1. Nainstalujte **balíček NuGet Microsoft.ml**:

    - V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.
    - Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**.
    - Vyberte tlačítko **instalovat** .
    - Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .
    - Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics** a **Microsoft. ml. OnnxTransformer**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Příprava dat a předem vyškoleného modelu

1. Stáhněte si [soubor zip adresáře prostředků projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) a rozbalte ho.

1. Zkopírujte adresář do adresáře projektu *ObjectDetection.* `assets` Tento adresář a jeho podadresáře obsahují soubory obrázků (kromě nemalého modelu YOLOv2, který si stáhnete a přidáte v dalším kroku) potřebného pro tento kurz.

1. Stáhněte si [malý YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [modelu ONNX pro zoologickéii](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)a rozbalte ho.

    Otevřete příkazový řádek a zadejte následující příkaz:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Zkopírujte extrahovaný `model.onnx` soubor z adresáře a pak ho přejmenujte do adresáře `assets\Model` projektu ObjectDetection a přejmenujte ho na. `TinyYolo2_model.onnx` Tento adresář obsahuje model potřebný pro tento kurz.

1. V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

Otevřete soubor *program.cs* a na začátek souboru přidejte následující `using` další příkazy:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Dále definujte cesty různých prostředků.

1. Nejprve do `Program` třídy přidejte `GetAbsolutePath` metodu `Main` pod metodu.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Pak uvnitř `Main` metody vytvořte pole pro uložení umístění vašich assetů.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Přidejte do projektu nový adresář, do kterého se budou ukládat vstupní data a třídy předpovědi.

V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak vyberte **Přidat** > **novou složku**. Když se nová složka zobrazí v Průzkumník řešení, pojmenujte ji "datastructures".

Vytvořte vstupní datovou třídu v nově vytvořených adresářích *Datastrukturas* .

1. V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *datastrukturas* a pak vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *ImageNetData.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *ImageNetData.cs* . Do horní části `using` *ImageNetData.cs*přidejte následující příkaz:

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Odeberte existující definici třídy a přidejte následující kód pro `ImageNetData` třídu do souboru *ImageNetData.cs* :

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`je třída vstupních dat obrázku a obsahuje následující <xref:System.String> pole:

    - `ImagePath`obsahuje cestu, kde je obrázek uložen.
    - `Label`obsahuje název souboru.

    Kromě toho `ImageNetData` obsahuje metodu `ReadFromFile` , která načte více souborů `imageFolder` obrázků uložených v `ImageNetData` zadané cestě a vrátí je jako kolekci objektů.

Vytvořte třídu předpovědi v adresáři *datastruktuře* .

1. V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *datastrukturas* a pak vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *ImageNetPrediction.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *ImageNetPrediction.cs* . Do horní části `using` *ImageNetPrediction.cs*přidejte následující příkaz:

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Odeberte existující definici třídy a přidejte následující kód pro `ImageNetPrediction` třídu do souboru *ImageNetPrediction.cs* :

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`je třída dat předpovědi a má následující `float[]` pole:

    - `PredictedLabel`obsahuje rozměry, skóre objektů a pravděpodobnosti třídy pro každé z ohraničujících polí zjištěných v obrázku.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

`Main` `MLContext` `outputFolder` Inicializujte proměnnou s novou instancí přidáním následujícího řádku do metody program.cs pod polem. `mlContext`

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Vytvoření analyzátoru pro výstupy modelu po zpracování

Model segmentuje obrázek do `13 x 13` mřížky, kde je `32px x 32px`každá buňka mřížky. Každá buňka mřížky obsahuje 5 potenciálních ohraničovacích rámečků objektů. Ohraničující rámeček má 25 prvků:

![](./media/object-detection-onnx/model-output-description.png)

- `x`pozice x středu ohraničovacího boxu vzhledem k buňce mřížky, ke které je přidružena.
- `y`pozice y ohraničovacího boxu v středu vzhledem k buňce mřížky, ke které je přidružena.
- `w`Šířka ohraničovacího rámečku
- `h`Výška ohraničovacího rámečku
- `o`Hodnota spolehlivosti, kterou objekt existuje v ohraničujícím poli, označované také jako skóre objektu.
- `p1-p20`pravděpodobnost třídy pro každou 20 tříd, které jsou předpovězeny modelem.

Celkem 25 prvků popisujících každé 5 ohraničujících polí tvoří prvky 125 obsažené v každé buňce mřížky.

Výstup generovaný předučeným ONNX modelem je float Array Length `21125`, který představuje prvky tensor s rozměry. `125 x 13 x 13` Aby bylo možné transformovat předpovědi generované modelem na tensor, je nutné provést některé práce po zpracování. Provedete to tak, že vytvoříte sadu tříd, které vám pomůžou analyzovat výstup.

Přidáním nového adresáře do projektu můžete uspořádat sadu tříd analyzátoru.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak vyberte **Přidat** > **novou složku**. Když se nová složka zobrazí v Průzkumník řešení, pojmenujte ji "YoloParser".

### <a name="create-bounding-boxes-and-dimensions"></a>Vytváření ohraničovacích rámečků a dimenzí

Výstup dat modelu obsahuje souřadnice a rozměry ohraničujících polí objektů v rámci obrázku. Vytvořte základní třídu pro dimenze.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *YoloParser* a pak vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *DimensionsBase.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *DimensionsBase.cs* . Odeberte všechny `using` příkazy a existující definici třídy.

    Do souboru DimensionsBase.cs přidejte následující kód `DimensionsBase` pro třídu:

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`má následující `float` pole:

    - `X`obsahuje pozici objektu podél osy x.
    - `Y`obsahuje pozici objektu podél osy y.
    - `Height`obsahuje výšku objektu.
    - `Width`obsahuje šířku objektu.

Dále vytvořte třídu pro vaše ohraničovací rámečky.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *YoloParser* a pak vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *YoloBoundingBox.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *YoloBoundingBox.cs* . Do horní části `using` *YoloBoundingBox.cs*přidejte následující příkaz:

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Hned nad existující definicí třídy přidejte novou definici třídy s názvem `BoundingBoxDimensions` , která dědí `DimensionsBase` z třídy, aby obsahovala rozměry příslušného ohraničovacího rámečku.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Odeberte existující `YoloBoundingBox` definici třídy a přidejte následující kód `YoloBoundingBox` pro třídu do souboru *YoloBoundingBox.cs* :

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`má následující pole:

    - `Dimensions`obsahuje rozměry ohraničovacího rámečku.
    - `Label`obsahuje třídu objektu zjištěnou v ohraničujícím poli.
    - `Confidence`obsahuje jistotu třídy.
    - `Rect`obsahuje obdélníkové vyjádření rozměrů ohraničovacího rámečku.
    - `BoxColor`obsahuje barvu spojenou s příslušnou třídou použitou k vykreslení na obrázku.

### <a name="create-the-parser"></a>Vytvoření analyzátoru

Nyní, když jsou vytvořeny třídy dimenzí a ohraničujících polí, je čas vytvořit analyzátor.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na adresář *YoloParser* a pak vyberte **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *YoloOutputParser.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *YoloOutputParser.cs* . Do horní části `using` *YoloOutputParser.cs*přidejte následující příkaz:

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Uvnitř definice existující `YoloOutputParser` třídy přidejte vnořenou třídu, která obsahuje rozměry každé buňky v obrázku. Přidejte následující kód pro `CellDimensions` třídu, která dědí `DimensionsBase` z třídy `YoloOutputParser` v horní části definice třídy.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Uvnitř definice `YoloOutputParser` třídy přidejte následující konstantu a pole.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`je počet řádků v mřížce, na který je obrázek rozdělen.
    - `COL_COUNT`je počet sloupců v mřížce, na který je obrázek rozdělen.
    - `CHANNEL_COUNT`je celkový počet hodnot obsažených v jedné buňce mřížky.
    - `BOXES_PER_CELL`je počet ohraničujících polí v buňce,
    - `BOX_INFO_FEATURE_COUNT`je počet funkcí obsažených v rámci pole (x, y, Výška, Šířka, spolehlivost).
    - `CLASS_COUNT`je počet tříd předpovědi obsažených v každém ohraničujícím poli.
    - `CELL_WIDTH`je šířka jedné buňky v mřížce obrázku.
    - `CELL_HEIGHT`je výška jedné buňky v mřížce obrázku.
    - `channelStride`je počáteční pozice aktuální buňky v mřížce.

    Když model vytvoří předpověď, označovanou také jako bodování, rozdělí `416px x 416px` vstupní obrázek do mřížky buněk `13 x 13`velikosti. Každá buňka obsahuje hodnotu `32px x 32px`. V každé buňce jsou 5 ohraničujících polí, z nichž každý obsahuje 5 funkcí (x, y, Šířka, Výška, spolehlivost). Kromě toho každý ohraničovací rámeček obsahuje pravděpodobnost každé třídy, která v tomto případě je 20. Každá buňka proto obsahuje 125 informací (5 funkcí + 20 pravděpodobností třídy).

`channelStride` Pro všechna 5 ohraničovacích rámečků vytvořte seznam ukotvení:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Kotvy jsou předem definované poměry výšky a šířky ohraničujících polí. Většina objektů nebo tříd zjištěných modelem má podobné poměry. To je výhodné při vytváření ohraničujících rámečků. Místo předpovědi ohraničujících polí se počítá posun z předdefinovaných dimenzí a proto se zkrátí výpočet vyžadovaný pro předpověď ohraničovacího rámečku. Tyto poměry kotvy jsou obvykle počítány na základě použité datové sady. V tomto případě, protože je známá datová sada a hodnoty byly předem vypočítány, kotvy mohou být pevně kódované.

Dále definujte popisky nebo třídy, které bude model předpovědět. Tento model předpovídá 20 tříd, které jsou podmnožinou celkového počtu tříd předpokládaných původním YOLOv2m modelem.

Přidejte seznam popisků pod `anchors`.

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Ke každé z těchto tříd jsou přiřazeny barvy. Přiřaďte barvy vaší třídy pod `labels`vaše:

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Vytváření pomocných funkcí

Ve fázi následného zpracování se účastní řada kroků. V takovém případě je možné využít několik pomocných metod.

Pomocné metody používané v analyzátoru jsou:

- `Sigmoid`použije funkci sigmoid, která vypíše číslo mezi 0 a 1.
- `Softmax`normalizuje vstupní vektor na rozdělení pravděpodobnosti.
- `GetOffset`mapuje prvky ve výstupu jednorozměrného modelu na odpovídající pozici v `125 x 13 x 13` tensor.
- `ExtractBoundingBoxes`extrahuje dimenze ohraničovacího rámečku pomocí `GetOffset` metody z výstupu modelu.
- `GetConfidence`extrahuje hodnotu spolehlivosti, která určuje, jak se v modelu zjistilo, že byl zjištěn objekt a `Sigmoid` pomocí funkce jej zapíná na procento.
- `MapBoundingBoxToCell`používá rozměry ohraničovacího boxu a mapuje je na příslušnou buňku v rámci obrázku.
- `ExtractClasses`extrahuje třídu předpovědi pro ohraničující rámeček z výstupu modelu pomocí `GetOffset` metody a převede je na rozdělení pravděpodobnosti `Softmax` pomocí metody.
- `GetTopResult`vybere třídu ze seznamu předpokládaných tříd s nejvyšší pravděpodobností.
- `IntersectionOverUnion`filtry překrývající ohraničovací rámečky s nižší pravděpodobností.

Přidejte kód pro všechny pomocné metody pod seznam `classColors`.

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Po definování všech pomocných metod je čas je použít ke zpracování výstupu modelu.

`IntersectionOverUnion` Pod metodou`ParseOutputs` vytvořte metodu pro zpracování výstupu generovaného modelem.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Vytvořte seznam pro ukládání ohraničujících polí a definujte proměnné uvnitř `ParseOutputs` metody.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Každý obrázek je rozdělen do mřížky `13 x 13` buněk. Každá buňka obsahuje pět ohraničujících rámečků. `boxes` Pod proměnnou přidejte kód pro zpracování všech polí v každé z buněk.

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

Uvnitř cyklické smyčky Vypočítejte počáteční pozici aktuálního pole ve výstupu jednorozměrného modelu.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Přímo pod ním použijte `ExtractBoundingBoxDimensions` metodu k získání rozměrů aktuálního ohraničovacího boxu.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Pak použijte `GetConfidence` metodu k získání důvěry pro aktuální ohraničovací rámeček.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Potom použijte `MapBoundingBoxToCell` metodu k namapování aktuálního ohraničovacího boxu na aktuálně zpracovávanou buňku.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Před provedením dalšího zpracování ověřte, zda je hodnota spolehlivosti větší, než je zadaná prahová hodnota. Pokud ne, zpracujte další ohraničovací rámeček.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

V opačném případě pokračujte ve zpracování výstupu. Dalším krokem je získání pravděpodobnosti rozdělení předpokládaných tříd pro aktuální ohraničovací rámeček pomocí `ExtractClasses` metody.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Pak použijte `GetTopResult` metodu k získání hodnoty a indexu třídy s nejvyšší pravděpodobností pro aktuální pole a výpočet svého skóre.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

`topScore` Použijte k opětovnému zadání jenom těch ohraničujících rámečků, které jsou nad určenou prahovou hodnotou.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Nakonec, pokud aktuální ohraničující rámeček překračuje prahovou hodnotu, vytvořte nový `BoundingBox` objekt a přidejte ho `boxes` do seznamu.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Po zpracování všech buněk v imagi vrátí `boxes` seznam. Do `ParseOutputs` metody přidejte následující návratový příkaz pod nejvíce vnější smyčka for-Loop.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Filtrovat překrývající se rámečky

Teď, když se všechna vysoce důvěrně ohraničená pole extrahují z výstupu modelu, je potřeba provést další filtrování, aby se překrývající image odebraly. Přidejte metodu nazvanou `FilterBoundingBoxes` `ParseOutputs` pod metodu:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

`FilterBoundingBoxes` Uvnitř metody Začněte tím, že vytvoříte pole, které se rovná velikosti zjištěných polí, a označíte všechny sloty jako aktivní nebo připravené ke zpracování.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Pak seřaďte seznam obsahující vaše ohraničující pole v sestupném pořadí na základě jistoty.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Potom vytvořte seznam pro ukládání filtrovaných výsledků.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Zahajte zpracování každého ohraničovacího rámečku tak, že do každého ohraničovacího pole zahájíte iteraci.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Uvnitř tohoto cyklu for-Loop ověřte, zda je možné zpracovat aktuální ohraničovací rámeček.

```csharp
if (isActiveBoxes[i])
{

}
```

Pokud ano, přidejte ohraničovací rámeček do seznamu výsledků. Pokud výsledky překročí zadaný limit pro extrakci, zrušte rozdělení smyčky. Do příkazu if-přidejte následující kód.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

V opačném případě se podívejte na sousedící ohraničovací rámečky. Pod kontrolu limitu pole přidejte následující kód.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Podobně jako v prvním poli, pokud je sousední pole aktivní nebo připravené ke zpracování, použijte `IntersectionOverUnion` metodu ke kontrole, zda první pole a druhé pole překročí zadanou prahovou hodnotu. Přidejte následující kód do vnitřní smyčky for Loop.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Mimo vnitřní smyčku for-Loop, která kontroluje sousední ohraničená pole, se podívejte, zda existují zbývající ohraničovací rámečky, které mají být zpracovány. Pokud ne, přerušte vnější smyčka for-Loop.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Nakonec, mimo počáteční cyklus smyčky `FilterBoundingBoxes` pro metodu, vrátí výsledky:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Výborně! Nyní je čas použít tento kód spolu s modelem pro bodování.

## <a name="use-the-model-for-scoring"></a>Použití modelu pro bodování

Stejně jako u následného zpracování je několik kroků v postupu hodnocení. K tomu je potřeba přidat třídu, která bude obsahovat logiku bodování pro váš projekt.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.
1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *OnnxModelScorer.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *OnnxModelScorer.cs* . Do horní části `using` *OnnxModelScorer.cs*přidejte následující příkaz:

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Do definice `OnnxModelScorer` třídy přidejte následující proměnné.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Přímo pod tím vytvořte konstruktor pro `OnnxModelScorer` třídu, která bude inicializovat dříve definované proměnné.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Po vytvoření konstruktoru definujte několik struktur, které obsahují proměnné související s nastavením obrázku a modelu. Vytvořte strukturu s názvem `ImageNetSettings` , aby obsahovala výšku a šířku očekávanou jako vstup pro model.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Potom vytvořte další strukturu s názvem `TinyYoloModelSettings` , která obsahuje názvy vstupní a výstupní vrstvy modelu. Chcete-li vizualizovat název vstupní a výstupní vrstvy modelu, můžete použít nástroj, jako je [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Dále vytvořte první sadu metod, které se použijí pro bodování. Vytvořte metodu uvnitř vaší `OnnxModelScorer` třídy. `LoadModel`

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    `LoadModel` Uvnitř metody přidejte následující kód pro protokolování.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    Kanály ml.NET musí znát schéma dat, aby fungovalo při [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) volání metody. V takovém případě se použije proces podobný školení. Vzhledem k tomu, že nedojde k žádnému skutečnému školení, je přijatelné použít [`IDataView`](xref:Microsoft.ML.IDataView)prázdné. Vytvořte nový [`IDataView`](xref:Microsoft.ML.IDataView) pro kanál z prázdného seznamu.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Níže definujte kanál. Kanál se skládá ze čtyř transformací.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)načte obrázek jako rastrový obrázek.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)změní měřítko obrázku na zadanou velikost (v tomto případě `416 x 416`).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)změní reprezentace obrázku z rastrového obrázku na číselný vektor.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)Načte model ONNX a použije ho ke stanovení skóre z poskytnutých dat.

    V `LoadModel` metodě`data` pod proměnnou definujte svůj kanál.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Nyní je čas vytvořit instanci modelu pro bodování. [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) Zavolejte metodu na kanálu a vraťte ji k dalšímu zpracování.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Po načtení modelu je možné ho použít k vytvoření předpovědi. Pro usnadnění tohoto procesu vytvořte metodu nazvanou `PredictDataUsingModel` `LoadModel` pod metodou.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

Dovnitř do `PredictDataUsingModel`přidejte následující kód pro protokolování.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Pak použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu k vyhodnocení dat.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Extrakce předpokládaných pravděpodobností a jejich vrácení pro další zpracování.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Teď, když jsou oba kroky nastavené, je zkombinovat do jediné metody. Pod metodou přidejte novou metodu s názvem `Score`. `PredictDataUsingModel`

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Už to skoro je! Teď je čas na to, aby se všechno používalo.

## <a name="detect-objects"></a>Detekovat objekty

Po dokončení celého nastavení je čas detekovat některé objekty. Začněte tím, že přidáte odkazy na skore a analyzátor ve vaší třídě *program.cs* .

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Skóre a analýza výstupů modelu

V rámci metody třídy program.cs přidejte příkaz try-catch. `Main`

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

`try` Uvnitř bloku začněte implementací logiky detekce objektů. Nejdřív načtěte data do [`IDataView`](xref:Microsoft.ML.IDataView).

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Pak vytvořte instanci `OnnxModelScorer` a použijte ji k vyhodnocení načtených dat.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Nyní je čas pro krok po zpracování. Vytvořte instanci `YoloOutputParser` a použijte ji ke zpracování výstupu modelu.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Až se výstup modelu zpracuje, je čas vykreslit ohraničovací rámečky na obrázcích.

### <a name="visualize-predictions"></a>Vizualizovat předpovědi

Poté, co model vyhodnotí obrázky a byly zpracovány výstupy, musí být ohraničovací pole vykreslena na obrázku. Uděláte to tak, že do *program.cs*přidáte `DrawBoundingBox` metodu, `GetAbsolutePath` která je volána pod metodou.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Nejdřív načtěte obrázek a v `DrawBoundingBox` metodě Získejte rozměry výšky a šířky.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Pak vytvořte smyčku For-Each k iterování každého ohraničovacího pole zjištěného modelem.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

Uvnitř smyčky for-each Získejte rozměry ohraničovacího rámečku.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Vzhledem k tomu, že rozměry ohraničovacího rámečku odpovídají vstupnímu typu `416 x 416`, Škálujte rozměry ohraničovacího pole tak, aby odpovídaly skutečné velikosti obrázku.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Pak definujte šablonu pro text, který se zobrazí nad každým ohraničujícím polem. Text bude obsahovat třídu objektu uvnitř příslušného ohraničovacího rámečku a také jistotu.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Chcete-li kreslit na obrázek, převeďte jej na [`Graphics`](xref:System.Drawing.Graphics) objekt.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

[`Graphics`](xref:System.Drawing.Graphics) V bloku `using` kódu vyladění nastavení objektu grafiky.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Níže můžete nastavit možnosti písma a barvy pro text a ohraničovací rámeček.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Vytvořte a vyplňte obdélník nad ohraničujícím polem, který bude obsahovat text pomocí [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) metody. To vám pomůže kontrastovat text a zlepšit čitelnost.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Pak nakreslete text a ohraničovací rámeček na obrázku pomocí [`DrawString`](xref:System.Drawing.Graphics.DrawString*) metod a. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

Mimo smyčku For-Each přidejte kód pro uložení obrázků v `outputDirectory`.

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Pro další zpětnou vazbu, kterou aplikace provádí předpovědi podle očekávání za běhu, přidejte metodu, `LogDetectedObjects` která je `DrawBoundingBox` volána pod metodou v souboru *program.cs* pro výstup zjištěných objektů do konzoly.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Teď, když máte pomocné metody k vytvoření vizuální zpětné vazby z předpovědi, přidejte smyčku for-Loop k iterování všech imagí s hodnocením.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

Uvnitř smyčky for-Loop Získá název souboru obrázku a ohraničená pole, která jsou k němu přidružená.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Níže použijte `DrawBoundingBox` metodu pro vykreslení ohraničujících polí na obrázku.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Nakonec použijte `LogDetectedObjects` metodu pro výstup předpovědi do konzoly.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Po příkazu try-catch přidejte další logiku, která indikuje, že proces je spuštěný.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

A to je vše!

## <a name="results"></a>Výsledky

Po provedení předchozích kroků spusťte konzolovou aplikaci (CTRL + F5). Výsledky by měly být podobné následujícímu výstupu. Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.

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

Chcete-li zobrazit obrázky s ohraničujícími poli, přejděte do `assets/images/output/` adresáře. Níže je ukázka z jedné ze zpracovaných imagí.

![](./media/object-detection-onnx/image3.jpg)

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro detekci objektů opětovným použitím předem připraveného `ONNX` modelu v ml.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Pochopení problému
> - Zjistěte, co je ONNX a jak funguje s ML.NET
> - Pochopení modelu
> - Opakované použití předem připraveného modelu
> - Detekovat objekty s načteným modelem

Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku detekce rozbaleného objektu.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-Samples – úložiště GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
