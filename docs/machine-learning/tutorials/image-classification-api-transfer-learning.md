---
title: 'Kurz: Automatická vizuální kontrola pomocí přenosu učení'
description: Tento kurz ukazuje, jak pomocí přenosu učení trénovat TensorFlow hluboké učení model v ML.NET pomocí rozhraní API pro detekci obrázků klasifikovat obrazy betonových povrchů jako popraskané nebo nepopraskané.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607555"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Kurz: Automatická vizuální kontrola pomocí přenosu učení s ML.NET image klasifikace API

Naučte se trénovat vlastní model hlubokého učení pomocí přenosu učení, předem natrénovaný tentenzorflow model a ML.NET Image Classification API klasifikovat obrazy betonových povrchů jako popraskané nebo uncracked.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Pochopení problému
> - Informace o rozhraní API pro klasifikaci obrázků ML.NET
> - Pochopte předem vytrénovaný model
> - Použití transferového učení k trénování vlastního modelu klasifikace obrázků TensorFlow
> - Klasifikovat obrázky s vlastním modelem

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".

## <a name="image-classification-transfer-learning-sample-overview"></a>Přehled ukázky učení přenosu klasifikace obrázků

Tato ukázka je aplikace konzoly C# .NET Core, která klasifikuje obrazy pomocí předem trénovaného modelu TensorFlow s hloubkovým učením. Kód pro tuto ukázku najdete v [úložišti dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) na GitHubu.

## <a name="understand-the-problem"></a>Pochopení problému

Klasifikace obrázků je problém počítačového vidění. Klasifikace obrázků převezme obraz jako vstup a kategorizuje jej do předepsané třídy. Některé scénáře, kde je užitečná klasifikace bitových obrázků, zahrnují:

- Rozpoznávání obličeje
- Detekce emocí
- Lékařská diagnóza
- Detekce orientačních bodů

Tento kurz trénuje vlastní model klasifikace obrázků k provedení automatizované vizuální kontroly mostních palub k identifikaci struktur, které jsou poškozeny prasklinami.

## <a name="mlnet-image-classification-api"></a>rozhraní API pro klasifikaci obrázků ML.NET

ML.NET poskytuje různé způsoby provádění klasifikace obrázků. Tento kurz se vztahuje na učení přenosu pomocí rozhraní API klasifikace obrázků. Rozhraní API klasifikace obrázků využívá [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), nízkoúrovňové knihovny, která poskytuje vazby Jazyka C# pro rozhraní API Tentenflow C++.

## <a name="what-is-transfer-learning"></a>Co je učení přenosu?

Transfer learning aplikuje znalosti získané z řešení jednoho problému na jiný související problém.

Školení modelu hlubokého učení od začátku vyžaduje nastavení několika parametrů, velké množství označených trénovacích dat a obrovské množství výpočetních prostředků (stovky hodin GPU). Použití předem trénovaného modelu spolu s učením přenosu umožňuje zkrátit proces školení.

## <a name="training-process"></a>Tréninkový proces

Rozhraní API klasifikace obrázků spustí proces školení načtením předem trénovaného modelu TensorFlow. Proces školení se skládá ze dvou kroků:

1. Fáze kritického místa
2. Tréninková fáze

![Tréninkové kroky](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Fáze kritického místa

Během fáze kritického bodu se načte sada trénovacích bitových kopií a hodnoty obrazových bodů se použijí jako vstup nebo prvky pro zmrazené vrstvy předem trénovaného modelu. Zmrazené vrstvy zahrnují všechny vrstvy v neuronové síti až do předposlední vrstvy, neformálně známé jako vrstva kritického místa. Tyto vrstvy jsou označovány jako zmrazené, protože žádné školení dojde v těchto vrstvách a operace jsou předávací. Je to v těchto zmrazených vrstev, kde jsou počítány vzorky nižší úrovně, které pomáhají modelu rozlišovat mezi různými třídami. Čím větší je počet vrstev, tím více je tento krok výpočtově náročnější. Naštěstí vzhledem k tomu, že se jedná o jednorázový výpočet, výsledky mohou být uloženy do mezipaměti a použity v pozdějších spuštěních při experimentování s různými parametry.

### <a name="training-phase"></a>Tréninková fáze

Jakmile jsou vypočteny výstupní hodnoty z fáze kritického místa, jsou použity jako vstup pro přeškolit konečnou vrstvu modelu. Tento proces je iterativní a běží pro počet časů určených parametry modelu. Během každého spuštění se vyhodnocuje ztráta a přesnost. Poté jsou provedeny příslušné úpravy pro zlepšení modelu s cílem minimalizovat ztrátu a maximalizovat přesnost. Po dokončení školení jsou výstupem dva formáty modelu. Jedním z nich `.pb` je verze modelu a `.zip` druhý je ML.NET serializovanou verzi modelu. Při práci v prostředích podporovaných ML.NET se `.zip` doporučuje použít verzi modelu. V prostředích, kde není podporována ML.NET, však `.pb` máte možnost použít verzi.

## <a name="understand-the-pretrained-model"></a>Pochopte předem vytrénovaný model

Předem trénovaný model použitý v tomto kurzu je 101vrstvá varianta modelu ResNet (ResNet) v2. Původní model je trénován pro klasifikaci obrázků do tisíce kategorií. Model bere jako vstup obraz o velikosti 224 x 224 a výstupy pravděpodobnosti třídy pro každou třídu, na které je trénovaný. Část tohoto modelu se používá k trénování nového modelu pomocí vlastních bitových kopií k předpovědi mezi dvěma třídami.

## <a name="create-console-application"></a>Vytvoření konzolové aplikace

Teď, když máte obecné znalosti o přenosu učení a rozhraní API klasifikace obrázků, je čas k vytvoření aplikace.

1. Vytvořte **aplikaci základní konzoly C# .NET** s názvem "DeepLearning_ImageClassification_Binary".
1. Nainstalujte **Microsoft.ML** verze **1.4.0** NuGet balíček:
    1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.
    1. Jako zdroj balíčku zvolte "nuget.org".
    1. Vyberte kartu **Procházet**.
    1. Zaškrtněte políčko **Zahrnout předběžnou verzi.**
    1. Vyhledejte **Microsoft.ML**.
    1. Vyberte tlačítko **Instalovat.**
    1. V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.
    1. Opakujte tyto kroky pro balíčky **Microsoft.ML.Vision** verze **1.4.0**, **SciSharp.TensorFlow.Redist** verze **1.15.0**a **Microsoft.ML.ImageAnalytics** verze **1.4.0** NuGet.

### <a name="prepare-and-understand-the-data"></a>Příprava a pochopení dat

> [!NOTE]
> Datové sady pro tento kurz jsou z Maguire, Marc; Dorafshan, Sattar; a Thomas, Robert J., "SDNET2018: Konkrétní datová sada obrazu bez vak pro aplikace strojového učení" (2018). Procházet všechny datové sady. Papír 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 je obrazová datová sada, která obsahuje poznámky pro popraskané a neprasklé betonové konstrukce (mostní paluby, stěny a dlažba).

![Ukázky mostního balíčku datové sady SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Data jsou uspořádána do tří podadresářů:

- D obsahuje obrázky mostní paluby
- P obsahuje obrázky chodníků
- W obsahuje nástěnné obrázky

Každý z těchto podadresářů obsahuje dva další podadresáře s předponou:

- C je předpona používaná pro prasklé povrchy
- U je předpona používaná pro neprasklé povrchy

V tomto kurzu se používají pouze obrazy mostové paluby.

1. Stáhněte si [datovou sadu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) a rozbalte ji.
1. Vytvořte adresář s názvem "datové zdroje" v projektu pro uložení souborů datové sady.
1. Zkopírujte podadresáře *CD* a *UD* z nedávno rozepnutého adresáře do adresáře *datových zdrojů.*

### <a name="create-input-and-output-classes"></a>Vytvoření vstupních a výstupních tříd

1. Otevřete *soubor Program.cs* a `using` nahraďte existující příkazy v horní části souboru následujícími:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Pod `Program` třídou v *Program.cs*vytvořte třídu s názvem `ImageData`. Tato třída se používá k reprezentaci původně načtených dat.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`obsahuje následující vlastnosti:

    - `ImagePath`je plně kvalifikovaná cesta, do které je obraz uložen.
    - `Label`je kategorie, do které obrázek patří. Toto je hodnota předpovědět.

1. Vytváření tříd pro vstupní a výstupní data

    1. Pod `ImageData` třídou definujte schéma vstupních dat v nové `ModelInput`třídě s názvem .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`obsahuje následující vlastnosti:

        - `Image`je `byte[]` reprezentace obrazu. Model očekává, že obrazová data budou tohoto typu pro trénování.
        - `LabelAsKey`je číselná reprezentace `Label`rozhraní .
        - `ImagePath`je plně kvalifikovaná cesta, do které je obraz uložen.
        - `Label`je kategorie, do které obrázek patří. Toto je hodnota předpovědět.

        Pouze `Image` `LabelAsKey` a slouží k trénování modelu a předpovědi. `ImagePath` Vlastnosti `Label` a jsou uchovávány pro usnadnění přístupu k původnímu názvu souboru obrázku a kategorii.

    1. Potom pod `ModelInput` třídou definujte schéma výstupních dat v nové `ModelOutput`třídě s názvem .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`obsahuje následující vlastnosti:

        - `ImagePath`je plně kvalifikovaná cesta, do které je obraz uložen.
        - `Label`je původní kategorie, do které obrázek patří. Toto je hodnota předpovědět.
        - `PredictedLabel`je hodnota předpovězená modelem.

        Podobně `ModelInput`jako , `PredictedLabel` pouze je nutné, aby předpovědi, protože obsahuje předpověď provedené modelem. `ImagePath` Vlastnosti `Label` a jsou zachovány pro usnadnění přístupu k původnímu názvu souboru obrázku a kategorii.

### <a name="create-workspace-directory"></a>Vytvoření adresáře pracovního prostoru

Pokud se data školení a ověření nemění často, je vhodné ukládat do mezipaměti vypočítané hodnoty kritického místa pro další spuštění.

1. V projektu vytvořte nový adresář s názvem *pracovní prostor* pro `.pb` uložení vypočítaných hodnot kritického místa a verze modelu.

### <a name="define-paths-and-initialize-variables"></a>Definování cest a inicializaci proměnných

1. Uvnitř `Main` metody definujte umístění prostředků, vypočítané hodnoty `.pb` kritického místa a verzi modelu.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Inicializovat `mlContext` proměnnou s novou instanci [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    Třída [MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET a inicializace mlContext vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

## <a name="load-the-data"></a>Načtení dat

### <a name="create-data-loading-utility-method"></a>Vytvořit metodu načítání dat

Obrázky jsou uloženy ve dvou podadresářích. Před načtením dat je třeba je naformátovat do seznamu `ImageData` objektů. Chcete-li tak `LoadImagesFromDirectory` učinit, `Main` vytvořte metodu pod metodou.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Uvnitř `LoadImagesDirectory` přidáte následující kód získat všechny cesty k souborům z podadresářů:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Potom iterát prostřednictvím každého ze `foreach` souborů pomocí příkazu.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. Uvnitř `foreach` příkazu zkontrolujte, zda jsou podporovány přípony souborů. Rozhraní API pro klasifikaci obrázků podporuje formáty JPEG a PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Potom získat popisek pro soubor. Pokud `useFolderNameAsLabel` je parametr `true`nastaven na hodnotu , použije se jako popisek nadřazený adresář, do kterého je soubor uložen. V opačném případě očekává, že popisek bude předponou názvu souboru nebo samotného názvu souboru.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Nakonec vytvořte novou `ModelInput`instanci .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Příprava dat

1. Zpět v `Main` metodě, `LoadFromDirectory` použijte metodu utility získat seznam obrázků používaných pro školení.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Potom načtěte obrázky do [`IDataView`](xref:Microsoft.ML.IDataView) pomocí [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Data jsou načtena v pořadí, v jakém byla přečtena z adresářů. Chcete-li data vyvážit, [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) zamíchejte je pomocí metody.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Modely strojového učení očekávají, že vstup bude v číselném formátu. Proto některé předběžné zpracování je třeba provést na data před školení. Vytvořte [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) skládá z [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` a transformuje. Transformace `MapValueToKey` převezme kategorickou hodnotu ve sloupci, `Label` převede ji na číselnou `KeyType` `LabelAsKey`hodnotu a uloží ji do nového sloupce s názvem . Trvá `LoadImages` hodnoty ze `ImagePath` sloupce spolu `imageFolder` s parametrem načíst obrázky pro školení.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Pomocí [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody použijte data následovaný `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) metodou, která vrátí [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předem zpracovaná data.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Chcete-li trénovat model, je důležité mít trénovací datovou sadu, stejně jako ověřovací datovou sadu. Model je trénován na tréninkové sadě. Jak dobře to dělá předpovědi na neviditelná data se měří výkon proti sada ověření. Na základě výsledků tohoto výkonu model provádí úpravy toho, co se naučil ve snaze zlepšit. Ověřovací sada může pocházet buď z rozdělení původní datové sady nebo z jiného zdroje, který již byl vyhrazen pro tento účel. V tomto případě je předzpracovaná datová sada rozdělena na trénovací, ověřovací a testovací sady.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Ukázka kódu výše provede dvě rozdělení. Nejprve jsou předzpracovaná data rozdělena a 70 % se používá pro školení, zatímco zbývajících 30 % se používá k ověření. Potom 30% ověřovací sada je dále rozdělena do validace a testovací sady, kde 90 % se používá pro ověření a 10 % se používá pro testování.

    Způsob, jak přemýšlet o účelu těchto datových oddílů je při zkoušce. Při studiu na zkoušku, můžete zkontrolovat své poznámky, knihy, nebo jiné zdroje, abyste si pochopení pojmů, které jsou na zkoušku. Na tohle je vlaková souprava. Pak můžete udělat falešnou zkoušku, abyste si ověřili své znalosti. To je místo, kde validační sada přijde vhod. Chcete-li zkontrolovat, zda máte dobrý přehled o pojmy před přijetím skutečné zkoušky. Na základě těchto výsledků, budete mít na vědomí, co jste udělali špatně, nebo nerozuměl dobře a začlenit své změny, jak si prohlédnout pro skutečnou zkoušku. Nakonec si udělej zkoušku. To je to, co testovací sada se používá pro. Nikdy jste neviděli otázky, které jsou na zkoušku a nyní používají to, co jste se naučili z tréninku a validace aplikovat své znalosti na úkol po ruce.

1. Přiřaďte oddíly jejich příslušné hodnoty pro data vlaku, ověření a testování.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Definování kanálu školení

Model školení se skládá z několika kroků. Nejprve rozhraní API klasifikace obrázků se používá k trénování modelu. Poté jsou kódované popisky `PredictedLabel` ve sloupci převedeny zpět na `MapKeyToValue` původní kategorickou hodnotu pomocí transformace.

1. Vytvořte novou proměnnou pro uložení sady požadovaných `ImageClassificationTrainer`a volitelných parametrů pro rozhraní .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    A `ImageClassificationTrainer` má několik volitelných parametrů:

    - `FeatureColumnName`je sloupec, který se používá jako vstup pro model.
    - `LabelColumnName`je sloupec pro hodnotu předpovědět.
    - `ValidationSet`je [`IDataView`](xref:Microsoft.ML.IDataView) obsahující ověřovací údaje.
    - `Arch`definuje, které z předem trénovaných architektur modelu použít. Tento kurz používá 101vrstvou variantu modelu ResNetv2.
    - `MetricsCallback`váže funkci ke sledování průběhu během tréninku.
    - `TestOnTrainSet`říká modelu k měření výkonu proti trénovací sady, když není k dispozici žádná sada ověření.
    - `ReuseTrainSetBottleneckCachedValues`říká modelu, zda použít hodnoty uložené v mezipaměti z fáze kritického místa v následných spuštěních. Fáze kritického místa je jednorázový průchozí výpočetní, který je výpočtově náročný při prvním provedení. Pokud se trénovací data nezmění a chcete experimentovat s různým počtem epoch nebo velikostí dávky, použití hodnot uložených v mezipaměti výrazně zkracuje dobu potřebnou k trénování modelu.
    - `ReuseValidationSetBottleneckCachedValues`je podobný `ReuseTrainSetBottleneckCachedValues` pouze tomu, že v tomto případě je pro ověřovací datové sady.
    - `WorkspacePath`definuje adresář, kam se mají ukládat `.pb` vypočítané hodnoty kritického místa a verze modelu.

1. Definujte [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) kanál školení, který `mapLabelEstimator` se `ImageClassificationTrainer`skládá z a .

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Pomocí [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody trénovat model.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Použití modelu

Nyní, když jste vycvičili model, je čas jej použít ke klasifikaci obrázků.

Pod `Main` metodou vytvořte novou metodu nástroje volanou `OutputPrediction` k zobrazení informací o predikci v konzole.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Klasifikace jednoho obrázku

1. Přidejte novou `ClassifySingleImage` metodu `Main` nazývanou pod metodu, aby se a výstup jedné predikce obrazu.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uvnitř `ClassifySingleImage` metody. Je [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) rozhraní API pohodlí, které umožňuje předat a potom provést předpověď na jednu instanci dat.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Chcete-li `ModelInput` získat přístup `data` [`IDataView`](xref:Microsoft.ML.IDataView) k [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) jedné [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) instanci, převeďte na pomocí metody a pak získat první pozorování.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Pomocí [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody klasifikovat obraz.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Výstup předpověď do konzoly `OutputPrediction` s metodou.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Uvnitř `Main` metody volejte `ClassifySingleImage` pomocí testovací sady obrázků.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Klasifikace více obrázků

1. Přidejte novou `ClassifyImages` metodu `ClassifySingleImage` nazývanou pod metodu pro vytvoření a výstup více předpovědí obrázků.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Vytvořte [`IDataView`](xref:Microsoft.ML.IDataView) obsahující předpovědi pomocí [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody. Do `ClassifyImages` metody přidejte následující kód.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Chcete-li itorovat přes předpovědi, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) převést na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocí [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody a pak získat prvních 10 pozorování.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Iterate a výstup původní a předpovídané popisky pro předpovědi.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Nakonec uvnitř `Main` metody volání `ClassifyImages` pomocí testovací sady obrázků.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Spuštění aplikace

Spusťte konzolovou aplikaci. Výstup by měl být podobný tomu níže. Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost. Pro stručnost byl výstup zhuštěn.

**Fáze kritického místa**

Pro název obrázku není vytištěna žádná hodnota, `byte[]` protože obrázky jsou načteny jako a proto není k dispozici žádný název obrázku.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Tréninková fáze**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Klasifikace výstupu obrazů**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Při kontrole *7001-220.jpg* obraz, můžete vidět, že to ve skutečnosti není popraskané.

![Obrázek datové sady SDNET2018 použitý pro předpověď](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Blahopřejeme! Nyní jste úspěšně vytvořili model hlubokého učení pro klasifikaci obrázků.

### <a name="improve-the-model"></a>Zlepšete model

Pokud nejste spokojeni s výsledky modelu, můžete se pokusit zlepšit jeho výkon vyzkoušením některých z následujících přístupů:

- **Více dat**: Čím více příkladů se model naučí, tím lépe se provádí. Stáhněte si úplnou [datovou sadu SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) a použijte ji k trénování.
- **Rozšířit data**: Běžnou technikou pro přidání rozmanitosti k datům je rozšířit data pořízením obrázku a použitím různých transformací (otočení, překlopení, posun, oříznutí). Tím přidáte rozmanitější příklady pro model učit se od.
- **Vlak na delší dobu:** Čím déle budete trénovat, tím více naladěn model bude. Zvýšení počtu epoch může zlepšit výkon modelu.
- **Experimentujte s hyper-parametry**: Kromě parametrů použitých v tomto kurzu lze vyladit další parametry, které potenciálně zlepšují výkon. Změna rychlostučení, která určuje velikost aktualizací provedených v modelu po každé epochy může zlepšit výkon.
- **Použití jiné architektury modelu**: V závislosti na tom, jak data vypadají, se model, který se nejlépe naučí jeho funkce, může lišit. Pokud nejste spokojeni s výkonem modelu, zkuste změnit architekturu.

### <a name="additional-resources"></a>Další zdroje

- [Hloubkové učení vs Strojové učení](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak vytvořit vlastní model hlubokého učení pomocí přenosu učení, předem vycvičené klasifikace obrázků TensorFlow model a ML.NET klasifikace obrázků API pro klasifikaci obrazů betonových povrchů jako popraskané nebo uncracked.

Přejdete k dalšímu kurzu, abyste se dozvěděli více.

> [!div class="nextstepaction"]
> [Detekce objektů](object-detection-onnx.md)
