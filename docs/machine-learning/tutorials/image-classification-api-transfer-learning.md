---
title: 'Kurz: automatizované vizuální prověřování pomocí učení přenosu'
description: V tomto kurzu se dozvíte, jak pomocí funkce Transfer Learning vytvořit TensorFlow model hloubkového učení v ML.NET pomocí rozhraní API pro detekci imagí pro klasifikaci imagí konkrétních ploch jako prasklé nebo neprasklé.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/14/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 443f9e9a83ebf31bb6c62323015af4a554323b67
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205059"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Kurz: automatizované vizuální prověřování pomocí přenosu přenosu s rozhraním API pro klasifikaci imagí ML.NET

Naučte se naučit vlastní model hloubkového učení s využitím učení přenosu, předTensorFlowho modelu a rozhraní API pro klasifikaci imagí ml.NET pro klasifikaci imagí konkrétních povrchů jako prasklé nebo prolomené.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Pochopení problému
> - Další informace o rozhraní API pro klasifikaci imagí ML.NET
> - Pochopení předvýukového modelu
> - Použití učení transferu k výuce vlastního modelu klasifikace imagí TensorFlow
> - Klasifikace imagí pomocí vlastního modelu

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

## <a name="image-classification-transfer-learning-sample-overview"></a>Přehled výukového kurzu přenosu klasifikace obrázků

Tato ukázka je Konzolová aplikace C# .NET Core, která klasifikuje Image pomocí předvýukového modelu TensorFlow hloubkového učení. Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) na GitHubu.

## <a name="understand-the-problem"></a>Pochopení problému

Klasifikace obrázku je problém počítačové vize. Klasifikace obrázku bere jako vstup obrázek a zařadí ho do předepsané třídy. Některé scénáře, kde je klasifikace obrázku užitečná, zahrnují:

- Rozpoznávání obličeje
- Detekce emoce
- Lékařské diagnostiky
- Detekce orientačních bodů

V tomto kurzu se nasazuje model klasifikace vlastních imagí, který provede automatizovanou vizuální kontrolu balíčku mostu a identifikuje tak struktury, které jsou poškozené prasklinami.

## <a name="mlnet-image-classification-api"></a>Rozhraní API pro klasifikaci imagí ML.NET

ML.NET poskytuje různé způsoby provádění klasifikace imagí. Tento kurz se týká učení přenosu pomocí rozhraní API klasifikace imagí. Rozhraní API pro klasifikaci imagí využívá [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)knihovnu nižší úrovně, která poskytuje C# vazby pro rozhraní TensorFlow C++ API.

## <a name="what-is-transfer-learning"></a>Co je učení přenosu?

Učení pro přenos používá znalostní bázi získaná od řešení jednoho problému s jiným souvisejícím problémem.

Školení modelu hloubkového učení od začátku vyžaduje nastavení několika parametrů, velkého množství podrobných školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU). Použití předzpracovaného modelu spolu s učením přenosu vám umožní zástupce školicího procesu.

## <a name="training-process"></a>Školicí proces

Rozhraní API klasifikace imagí spustí školicí proces načtením předinstalovaného modelu TensorFlow. Školicí proces se skládá ze dvou kroků:

1. Fáze kritického bodu
2. Fáze školení

![Postup školení](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Fáze kritického bodu

Během fáze kritických míst se načte sada školicích imagí a jako vstup a funkce se použijí pixelové hodnoty pro zmrazené vrstvy předinstalovaného modelu. Zmrazené vrstvy zahrnují všechny vrstvy v neuronové síti až do poslední vrstvy, která je Poznáma jako kritická vrstva. Tyto vrstvy se označují jako zmrazené, protože na těchto vrstvách a operacích neproběhne žádné školení. Je v těchto zmrazených vrstvách, kde jsou vypočítány vzory nižší úrovně, které usnadňují model odlišení různých tříd. Čím větší je počet vrstev, tím více výpočetně náročné je tento krok. Naštěstí, protože se jedná o jednorázový výpočet, mohou být výsledky uloženy do mezipaměti a použity v pozdějších spuštěních při experimentování s různými parametry.

### <a name="training-phase"></a>Fáze školení

Až budou výstupní hodnoty z kritické fáze vypočítány, používají se jako vstup k přeškolování finální vrstvy modelu. Tento proces je iterativní a spouští se v počtu pokusů určených parametry modelu. Během každého spuštění jsou vyhodnocovány ztráty a přesnost. Pak jsou provedeny příslušné úpravy pro zlepšení modelu s cílem minimalizovat ztrátu a maximalizovat přesnost. Po dokončení školení jsou výstupem dva formáty modelů. Jednou z nich je `.pb` verze modelu a druhá je serializovaná verze modelu `.zip` ML.NET. Při práci v prostředích podporovaných aplikací ML.NET se doporučuje použít verzi modelu `.zip`. V prostředích, kde ML.NET není podporovaný, máte ale možnost použít verzi `.pb`.

## <a name="understand-the-pretrained-model"></a>Pochopení předvýukového modelu

Předem vydaný model použitý v tomto kurzu je 101 varianta modelu zbytkové sítě (ResNet) v2. Původní model je vyškolen pro klasifikaci imagí do tisíc kategorií. Model bere jako vstup obrázek o velikosti 224 × 224 a vypisuje pravděpodobnosti třídy pro každou třídu, na které je technologie IT vyškolená. Součástí tohoto modelu je vyučování nového modelu pomocí vlastních imagí, aby bylo možné předpovědi mezi dvěma třídami.

## <a name="create-console-application"></a>Vytvoření konzolové aplikace

Teď, když máte obecné znalosti o učení přenosů a rozhraní API klasifikace imagí, je čas sestavování aplikace.

1. Vytvořte  **C# konzolovou aplikaci .NET Core** nazvanou "DeepLearning_ImageClassification_Binary".
1. Nainstalujte balíček NuGet verze **Microsoft.ml** **1.4.0** :
    1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.
    1. Jako zdroj balíčku vyberte "nuget.org".
    1. Vyberte kartu **Procházet** .
    1. Zaškrtněte políčko **zahrnout předběžné verze** .
    1. Vyhledejte **Microsoft.ml**.
    1. Vyberte tlačítko **instalovat** .
    1. Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .
    1. Opakujte tyto kroky pro balíček **Microsoft. ml. Vision** verze **1.4.0**, **SciSharp. TensorFlow. Redist** verze **1.15.0**a **Microsoft. ml. ImageAnalytics** verze **1.4.0** NuGet Packages.

### <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

> [!NOTE]
> Datové sady pro tento kurz jsou z Maguire, matolin; Dorafshan, Sattar; a Tomáš, Robert J., "SDNET2018: konkrétní datová sada obrázku trhlin pro aplikace pro strojové učení" (2018). Procházet všechny datové sady. Papír 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 je datová sada obrázků, která obsahuje poznámky pro neprasklé a neprasklé konkrétní struktury (balíčky mostů, stěny a Pavement).

![Ukázky balíčku pro přemostění datových sad SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Data jsou uspořádaná ve třech podadresářích:

- D obsahuje obrázky na balíčku mostu.
- P obsahuje image Pavement
- W obsahuje obrázky na zdi

Každý z těchto podadresářů obsahuje dva další předem opravené podadresáře:

- C je předpona používaná pro prasklé povrchy
- U je předpona používaná pro prolomené povrchy.

V tomto kurzu se používají jenom balíčky balíčku mostu.

1. Stáhněte si [datovou sadu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) a rozbalte ji.
1. Vytvořte ve svém projektu adresář s názvem "assety" a uložte soubory DataSet.
1. Zkopírujte podadresáře *CD* a *ud* z naposledy nekomprimovaného adresáře do adresáře *assety* .

### <a name="create-input-and-output-classes"></a>Vytvoření vstupní a výstupní třídy

1. Otevřete soubor *program.cs* a nahraďte existující příkazy `using` v horní části souboru následujícím způsobem:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Pod třídou `Program` v *program.cs*vytvořte třídu s názvem `ImageData`. Tato třída slouží k reprezentaci počátečních načtených dat.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData` obsahuje následující vlastnosti:

    - `ImagePath` je plně kvalifikovaná cesta, kde je obrázek uložený.
    - `Label` je kategorie, do které patří obrázek. Toto je hodnota, která se má předpovědět.

1. Vytváření tříd pro vstupní a výstupní data

    1. Pod `ImageData` třídou definujte schéma vstupních dat v nové třídě s názvem `ModelInput`.

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput` obsahuje následující vlastnosti:

        - `ImagePath` je plně kvalifikovaná cesta, kde je obrázek uložený.
        - `Label` je kategorie, do které patří obrázek. Toto je hodnota, která se má předpovědět.
        - `Image` je `byte[]` reprezentace obrázku. Model očekává, že budou data obrázku tohoto typu pro účely školení.
        - `LabelAsKey` je numerická reprezentace `Label`.

        Pro výuku modelu a předpovědi se používají jenom `Image` a `LabelAsKey`. Vlastnosti `ImagePath` a `Label` jsou pro usnadnění přístupu k původnímu názvu souboru bitové kopie a kategorii zachovány.

    1. Pak pod `ModelInput` třídy definujte schéma výstupních dat v nové třídě s názvem `ModelOutput`.

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput` obsahuje následující vlastnosti:

        - `ImagePath` je plně kvalifikovaná cesta, kde je obrázek uložený.
        - `Label` je původní kategorie, do které patří obrázek. Toto je hodnota, která se má předpovědět.
        - `PredictedLabel` je hodnota předpokládaná modelem.

        Podobně jako u `ModelInput`se vyžaduje jenom `PredictedLabel` k předpovědi, protože obsahuje předpovědi vytvořenou modelem. Vlastnosti `ImagePath` a `Label` jsou pro usnadnění přístupu k původnímu názvu souboru bitové kopie a kategorii zachovány.

### <a name="create-workspace-directory"></a>Vytvořit adresář pracovního prostoru

Když se data o školení a ověřování často nemění, je vhodné při dalších spuštěních ukládat do mezipaměti vypočtené kritické hodnoty.

1. V projektu vytvořte nový adresář s názvem *pracovní prostor* pro uložení vypočítaných kritických hodnot a `.pb` verze modelu.

### <a name="define-paths-and-initialize-variables"></a>Definování cest a inicializovat proměnné

1. V rámci metody `Main` definujte umístění vašich assetů, vypočtených kritických hodnot a `.pb` verze modelu.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Pak inicializujte `mlContext` proměnnou novou instancí třídy [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    Třída [MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje MLContext vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu pro vytváření modelů. Je podobný a koncepčně `DBContext` v Entity Framework.

## <a name="load-the-data"></a>Načtení dat

### <a name="create-data-loading-utility-method"></a>Metoda vytvoření nástroje pro načítání dat

Bitové kopie jsou uloženy ve dvou podadresářích. Před načtením dat je třeba ji naformátovat na seznam `ImageData` objektů. Provedete to tak, že vytvoříte metodu `LoadImagesFromDirectory` pod metodou `Main`.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Uvnitř `LoadImagesDirectory` přidejte následující kód pro získání všech cest k souborům z podadresářů:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Potom Iterujte každý ze souborů pomocí příkazu `foreach`.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. V rámci příkazu `foreach` ověřte, zda jsou přípony souborů podporovány. Rozhraní API klasifikace obrázků podporuje formáty JPEG a PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Pak Získejte popisek pro soubor. Je-li parametr `useFolderNameAsLabel` nastaven na hodnotu `true`, bude jako popisek použit nadřazený adresář, kde je soubor uložen. V opačném případě očekává, že popisek bude prefixem názvu souboru nebo samotného názvu souboru.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Nakonec vytvořte novou instanci `ModelInput`.

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Příprava dat

1. Zpět v metodě `Main` použijte metodu `LoadFromDirectory` Utility k získání seznamu imagí použitých pro školení.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Pak načtěte obrázky do [`IDataView`](xref:Microsoft.ML.IDataView) pomocí metody [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Data se načítají v pořadí, v jakém byla načtena z adresářů. Chcete-li vyrovnávat data, přemístěte je pomocí metody [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Modely strojového učení očekávají, že vstup bude v číselném formátu. Proto je nutné před školením provést některé předzpracování dat. Vytvoří [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) tvořená [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) a `LoadRawImageBytes`mi transformacemi. `MapValueToKey` transformace přebírá hodnotu kategorií ve sloupci `Label`, převede ji na číselnou `KeyType` hodnotu a uloží ji do nového sloupce s názvem `LabelAsKey`. `LoadImages` přebírá hodnoty z `ImagePath` sloupce spolu s parametrem `imageFolder` pro načtení imagí pro školení.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Použijte metodu [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) pro použití dat na `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) následovaný metodou [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , která vrací [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předem zpracovaná data.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Pro výuku modelu je důležité, abyste měli školicí datovou sadu i ověřovací datovou sadu. Model je vyškolený v sadě školení. Jak dobře je předpovědi na nezpracovaných datech, je měřeno výkonem proti sadě ověřování. V závislosti na výsledcích tohoto výkonu model provádí úpravy podle toho, co se naučilo ve snaze zlepšit. Sada ověření může pocházet z rozdělení původní datové sady nebo z jiného zdroje, který již byl pro tento účel vyhrazen. V tomto případě je předem zpracovaná datová sada rozdělena do školicích, ověřovacích a testovacích sad.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Výše uvedený vzor kódu provádí dvě rozdělení. Předem zpracovaná data jsou nejprve rozdělena a 70% se používá pro školení, zatímco se k ověřování používá zbývajících 30%. Potom je 30% ověřovací sada dále rozdělena na ověřování a sady testů, kde se pro ověřování používá 90% a pro testování se používá 10%.

    Způsob, jak se zamyslet na účel těchto datových oddílů, je provedení zkoušky. Při studiu pro zkoušku si Projděte poznámky, knihy nebo jiné prostředky, abyste získali informace o konceptech, které se na této zkoušce nacházejí. To je to, pro který je vlaková sada. Pak můžete pořizovat napodobnou zkoušku k ověření vašeho vědomí. Tady se objeví ověřovací sada. Chcete před provedením samotné zkoušky ověřit, zda máte dobré pojetí konceptů. Na základě těchto výsledků si poznamenejte, co se vám nepovedlo nebo nerozumělo, a zahrňte své změny do kontroly skutečné zkoušky. Nakonec můžete provést zkoušku. To je to, co je testovací sada používána pro. Nikdy jste neviděli otázky, které se týkají zkoušky, a teď pomocí toho, co jste se naučili při školení a ověřování, abyste mohli vaše znalosti na úkol použít.

1. Přiřaďte oddíly jejich příslušné hodnoty pro data vlaku, ověřování a testování.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Definování školicího kanálu

Školení modelů se skládá z několika kroků. Rozhraní API pro klasifikaci imagí slouží jako první, používá se k učení modelu. Zakódované popisky ve sloupci `PredictedLabel` se pak převádějí zpátky na původní hodnotu kategorií pomocí `MapKeyToValue` transformaci.

1. Vytvořte novou proměnnou pro uložení sady požadovaných a volitelných parametrů pro `ImageClassificationTrainer`. 

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    `ImageClassificationTrainer` přebírá několik volitelných parametrů:

    - `FeatureColumnName` je sloupec, který se používá jako vstup pro model.
    - `LabelColumnName` je sloupec, jehož hodnota se má předpovědět.
    - `ValidationSet` je [`IDataView`](xref:Microsoft.ML.IDataView) obsahující ověřovací data.
    - `Arch` definuje, které z předdefinovaných architektur modelů se mají použít. V tomto kurzu použijeme 101 variant modelu ResNetv2.
    - `MetricsCallback` váže funkci, aby sledovala průběh během školení.
    - `TestOnTrainSet` oznamuje modelu, aby měřil výkon proti školicí sadě, když není k dispozici žádná ověřovací sada.
    - `ReuseTrainSetBottleneckCachedValues` instruuje model, zda se mají v následných fázích použít hodnoty uložené v mezipaměti z fáze kritického bodu. Kritická fáze je jednorázové výpočtu předávacího přenosu, který je výpočetně náročný při prvním provedení. Pokud se školicí data nezmění a chcete experimentovat s jiným počtem epochs nebo dávky, použití hodnot uložených v mezipaměti významně zkracuje dobu potřebnou k výuce modelu.
    - `ReuseValidationSetBottleneckCachedValues` je podobná `ReuseTrainSetBottleneckCachedValues` pouze v tomto případě je to pro datovou sadu ověřování.
    - `WorkspacePath` definuje adresář, kam se mají ukládat vypočítané kritické hodnoty a `.pb` verze modelu.

1. Definujte kanál školení [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) , který se skládá z `mapLabelEstimator` a `ImageClassificationTrainer`.

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Pro výuku modelu použijte metodu [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Použití modelu

Teď, když jste si proškole svůj model, je čas ho použít ke klasifikaci imagí.

Pod metodou `Main` vytvořte novou metodu Utility nazvanou `OutputPrediction`, která zobrazí informace o předpovědi v konzole nástroje.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Klasifikace jednoho obrázku

1. Přidejte novou metodu nazvanou `ClassifySingleImage` pod `Main` metodu pro vytvoření a výstup jedné předpovědi imagí.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. V rámci metody `ClassifySingleImage` vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Chcete-li získat přístup k jedné instanci `ModelInput`, převeďte [`IDataView`](xref:Microsoft.ML.IDataView) `data` na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a poté Získejte první sledování.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. K klasifikaci obrázku použijte metodu [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) .

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Výstup předpovědi do konzoly s metodou `OutputPrediction`.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Uvnitř metody `Main` volejte `ClassifySingleImage` pomocí testovací sady imagí.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Klasifikace více imagí

1. Přidejte novou metodu nazvanou `ClassifyImages` pod `ClassifySingleImage` metodu pro vytvoření a výstup více předpovědi obrázků.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Vytvořte [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předpovědi pomocí metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) . Do metody `ClassifyImages` přidejte následující kód.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Chcete-li iterovat přes předpovědi, převeďte `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a potom Získejte prvních 10 pozorování.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Iterujte a navýstupujte původní a předpovězené popisky pro předpovědi.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Nakonec v rámci metody `Main` volejte `ClassifyImages` pomocí testovací sady imagí.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Spuštění aplikace

Spusťte konzolovou aplikaci. Výstup by měl vypadat podobně jako na následujícím obrázku. Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti. V případě zkrácení byl výstup zúžený.

**Fáze kritického bodu**

Pro název Image se nevytiskne žádná hodnota, protože image jsou načtené jako `byte[]` proto, že není k dispozici žádný název Image k zobrazení.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Fáze školení**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Klasifikovat výstup imagí**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Po kontrole obrázku *7001 -220. jpg* vidíte, že ve skutečnosti není prasklý.

![Obrázek datové sady SDNET2018 použité pro předpověď](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Blahopřejeme! Teď jste úspěšně vytvořili model hloubkového učení pro klasifikaci imagí.

### <a name="improve-the-model"></a>Zlepšení modelu

Pokud nejste spokojeni s výsledky modelu, můžete se pokusit zvýšit jeho výkon tak, že zkusíte některé z následujících přístupů:

- **Další data**: Další příklady, ze kterých se model učí, je lepší. Stáhněte si úplnou [datovou sadu SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) a využijte ji ke školení.
- **Rozšíření dat**: běžnou technikou pro přidání různých druhů dat je rozšíření dat pomocí obrázku a použití různých transformací (otočení, překlopení, posunutí a oříznutí). Tím se přidá více různých příkladů modelu, ze kterého se naučíte.
- **Školení pro delší dobu**: čím delší je, tím bude model lépe vyladěný. Zvýšení počtu epochs může zlepšit výkon modelu.
- **Experiment s parametrem Hyper-Parameters**: Kromě parametrů používaných v tomto kurzu můžete další parametry vyladit tak, aby potenciálně vylepšily výkon. Změna studijní frekvence, která určuje velikost aktualizací v modelu po každém epocha, může zlepšit výkon.
- **Použití jiné architektury modelů**: v závislosti na tom, jak vaše data vypadají, se může model, který se nejlépe učí jeho funkcí, lišit. Pokud nejste spokojeni s výkonem modelu, zkuste změnit architekturu.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- [Obsáhlý Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak vytvořit vlastní model hloubkového učení s využitím učení přenosu, předTensorFlowho modelu klasifikace imagí a rozhraní API pro klasifikaci ml.NET pro klasifikaci imagí konkrétních povrchů jako prasklé nebo prolomené.

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Detekce objektu](object-detection-onnx.md)
