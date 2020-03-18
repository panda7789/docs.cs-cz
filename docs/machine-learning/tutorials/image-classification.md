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
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Kurz: Generování modelu klasifikace obrazu ML.NET z předem vytrénovaného modelu TensorFlow

Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace obrázků ML.NET.

Model TensorFlow byl trénován tak, aby klasifikoval obrázky do tisíce kategorií. Model ML.NET využívá část modelu TensorFlow ve svém potrubí k trénování modelu pro klasifikaci obrázků do 3 kategorií.

Trénování modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tuny označených trénovacích dat a obrovské množství výpočetních prostředků (stovky hodin GPU). I když není tak efektivní jako školení vlastní model od nuly, přenos učení vám umožní zástupce tohoto procesu tím, že pracuje s tisíci obrázků vs miliony označených obrázků a vybudovat vlastní model poměrně rychle (do hodiny na stroji bez GPU). Tento kurz škáluje tento proces ještě dále, pomocí pouze tucet tréninkových obrázků.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Pochopení problému
> * Začleňte předem vyškolený model TensorFlow do ML.NET potrubí
> * Trénování a hodnocení ML.NET modelu
> * Klasifikace testovacího obrázku

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) Všimněte si, že ve výchozím nastavení konfigurace projektu .NET pro tento kurz cíle .NET jádro 2.2.

## <a name="what-is-transfer-learning"></a>Co je učení přenosu?

Transfer learning je proces využití získaných znalostí při řešení jednoho problému a jeho uplatnění na jiný, ale související problém.

Pro účely tohoto kurzu použijete část modelu TensorFlow - trénovaný pro klasifikaci obrázků do tisíce kategorií - v modelu ML.NET, který klasifikuje obrázky do 3 kategorií.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou "Vývoj napříč platformami..NET Core.Core.Platform development".
* [Adresář prostředků kurzu . SOUBOR ZIP](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [Model strojového učení InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Výběr správného úkolu strojového učení

### <a name="deep-learning"></a>Hloubkové učení

[Hluboké učení](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou strojového učení, která přináší revoluci v oblastech, jako je počítačové vidění a rozpoznávání řeči.

Modely hlubokého učení jsou trénované pomocí velkých sad [označených dat](https://en.wikipedia.org/wiki/Labeled_data) a [neuronových sítí,](https://en.wikipedia.org/wiki/Artificial_neural_network) které obsahují více vrstev učení. Hluboké učení:

* Funguje lépe na některé úkoly, jako je počítačové vidění.
* Vyžaduje obrovské množství trénovacích dat.

Klasifikace obrázků je běžný úkol strojového učení, který nám umožňuje automaticky klasifikovat obrázky do kategorií, jako jsou:

* Detekce lidské tváře na obrázku nebo ne.
* Detekce koček vs. psi.

 Nebo jako na následujících obrázcích, určení, zda je obraz a(n) jídlo, toy, nebo zařízení:

![pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![obrázek](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![medvídek obrázek toaster obrázek](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Předchozí obrázky patří do Wikimedia Commons a jsou připisovány takto:
>
> * "220px-Pepperoni_pizza.jpg" Public https://commons.wikimedia.org/w/index.php?curid=79505Domain, ,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" Od [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-fotografoval, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Vlastní práce, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403

Je `Inception model` trénovaný pro klasifikaci obrázků do tisíce kategorií, ale pro tento kurz je třeba klasifikovat obrázky v menší sadě kategorií a pouze v těchto kategoriích. Zadejte `transfer` část `transfer learning`. Schopnost `Inception model`'s rozpoznat a klasifikovat obrázky můžete přenést do nových omezených kategorií vlastního klasifikátoru obrázků.

* Potravin
* Hračka
* Přístroj

Tento kurz používá model hlubokého učení modelu TensorFlow [Inception,](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) což je oblíbený model rozpoznávání obrázků trénovaný v `ImageNet` datové sadě. Model TensorFlow klasifikuje celé obrázky do tisíce tříd, například "Umbrella", "Jersey" a "Myčka nádobí".

Vzhledem `Inception model` k tomu, že již byl předem vyškolen na tisících různých obrázků, interně obsahuje [obrazové funkce](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrazu. Můžeme využít těchto interních obrazových prvků v modelu trénovat nový model s mnohem méně tříd.

Jak je znázorněno v následujícím diagramu, přidáte odkaz na ML.NET balíčky NuGet ve vašich aplikacích .NET Core nebo .NET Framework. Pod kryty ML.NET zahrnuje a `TensorFlow` odkazuje na nativní knihovnu, která `TensorFlow` umožňuje psát kód, který načte existující trénovaný soubor modelu.

![TensorFlow transformace ML.NET Obloukový diagram](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Klasifikace více tříd

Po použití inceptičního modelu TensorFlow k extrahování funkcí vhodných jako vstup pro klasický algoritmus strojového učení přidáme ML.NET [klasifikátor více tříd](../resources/tasks.md#multiclass-classification).

Specifickým trénem používaným v tomto případě je [multinomický logistický regresní algoritmus](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Algoritmus implementovaný tímto trenérem funguje dobře na problémech s velkým počtem funkcí, což je případ modelu hlubokého učení pracujícího na obrazových datech.

### <a name="data"></a>Data

Existují dva zdroje dat: `.tsv` soubor a obrazové soubory.  Soubor `tags.tsv` obsahuje dva sloupce: první je `ImagePath` definován jako a `Label` druhý je odpovídající obrázku. Následující ukázkový soubor nemá řádek záhlaví a vypadá takto:

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

Trénovací a testovací obrázky jsou umístěny ve složkách datových zdrojů, které stáhnete do souboru zip. Tyto obrázky patří Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), úložiště svobodných médií.* Načteno 10:48, říjen 17, 2018 z: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toasterhttps://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Nastavení

### <a name="create-a-project"></a>Vytvoření projektu

1. Vytvořte **aplikaci .NET Core Console** s názvem "TransferLearningTF".

1. Nainstalujte **balíček nuget Microsoft.ML**:

    * V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**.
    * Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ML**.
    * Klikněte na rozevírací **seznam Verze,** vyberte balíček **1.4.0** v seznamu a vyberte tlačítko **Instalovat.**
    * V dialogovém okně **Náhled změn** vyberte tlačítko **OK.**
    * Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, vyberte v dialogovém okně **Přijetí licence** tlačítko **Souhlasím.**
    * Opakujte tyto kroky pro **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** a **Microsoft.ML.TensorFlow v1.4.0**.

### <a name="download-assets"></a>Stažení datových zdrojů

1. Stáhnout [soubor zip adresáře datových zdrojů projektu](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)a rozbalit.

1. Zkopírujte `assets` adresář do adresáře projektu *TransferLearningTF.* Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu Inception, který stáhnete a přidáte v dalším kroku) potřebnýpro tento kurz.

1. Stáhněte si [model Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)a rozbalte.

1. Zkopírujte obsah `inception5h` adresáře, který se právě rozbalil, do adresáře projektu `assets/inception` *TransferLearningTF.* Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:

   ![Obsah adresáře pro počátek](./media/image-classification/inception-files.png)

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na jednotlivé soubory v adresáři datových zdrojů a podadresářích a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. Přidejte následující kód na řádek `Main` přímo nad metodou, abyste určili cesty majetku:

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. Vytvořte třídy pro vaše vstupní data a předpovědi.

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData`je třída vstupních obrazových <xref:System.String> dat a má následující pole:

    * `ImagePath`obsahuje název souboru obrázku.
    * `Label`obsahuje hodnotu popisku obrázku.

1. Přidání nové třídy do `ImagePrediction`projektu pro:

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`je třída predikce obrázku a má následující pole:

    * `Score`obsahuje procento spolehlivosti pro danou klasifikaci obrazu.
    * `PredictedLabelValue`obsahuje hodnotu pro popisek klasifikace předpovídaného obrázku.

    `ImagePrediction`je třída použitá pro předpověď po trénovaném modelu. Má `string` (`ImagePath`) pro cestu obrazu. Používá `Label` se k opětovnému použití a trénování modelu. Používá `PredictedLabelValue` se při predikci a vyhodnocení. Pro vyhodnocení se používá vstup s trénovacími daty, předpovídanými hodnotami a modelem.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v hlavní

1. Inicializovat `mlContext` proměnnou s `MLContext`novou instancí .  Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě: `Main`

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    [Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

### <a name="create-a-struct-for-inception-model-parameters"></a>Vytvoření struktury pro parametry modelu inception

1. Inception model má několik parametrů, které je třeba předat. Vytvořte strukturu pro mapování hodnot parametrů na popisné názvy `Main()` s následujícím kódem, hned za metodou:

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Vytvoření metody nástroje zobrazení

Vzhledem k tomu, že budete zobrazovat obrazová data a související předpovědi více než jednou, vytvořte metodu nástroje zobrazení pro zpracování zobrazení výsledků obrazu a předpovědi.

1. Vytvořte `DisplayResults()` metodu, `InceptionSettings` těsně za struct, pomocí následujícího kódu:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Vyplňte tělo `DisplayResults` metody:

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Vytvoření metody nástroje pro vytvoření souboru TSV

1. Vytvořte `ReadFromTsv()` metodu, `DisplayResults()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Vyplňte tělo `ReadFromTsv` metody:

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    Kód `tags.tsv` analyzuje soubor přidat cestu k názvu souboru obrazu pro `ImagePath` vlastnost a načíst ji a `Label` do objektu. `ImageData`

### <a name="create-a-method-to-make-a-prediction"></a>Vytvoření metody pro vytvoření předpovědi

1. Vytvořte `ClassifySingleImage()` metodu, `DisplayResults()` těsně před metodou, pomocí následujícího kódu:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Vytvořte `ImageData` objekt, který obsahuje plně kvalifikovanou cestu `ImagePath`a název souboru obrázku pro singl . Jako další řádky metody `ClassifySingleImage()` přidejte následující kód:

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. Proveďte jednu předpověď přidáním následujícího kódu `ClassifySingleImage` jako následující řádek v metodě:

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    Chcete-li získat předpověď, použijte [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) metoda. [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

    > [!NOTE]
    > `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

1. Zobrazit výsledek předpovědi jako další řádek `ClassifySingleImage()` kódu v metodě:

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Konstrukce kanálu modelu ML.NET

Potrubí modelu ML.NET je řetězec odhadů. Všimněte si, že žádné spuštění se stane během výstavby kanálu. Objekty odhadu jsou vytvořeny, ale nejsou provedeny.

1. Přidání metody pro generování modelu

    Tato metoda je srdcem výukového programu. Vytvoří kanál pro model a trénuje potrubí k výrobě modelu ML.NET. Také vyhodnotí model proti některé dříve neviditelné testovací data.

    Vytvořte `GenerateModel()` metodu, `InceptionSettings` těsně za strukturou `DisplayResults()` a těsně před metodou pomocí následujícího kódu:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Přidejte odhady k načtení, změně velikosti a extrahování obrazových bodů z obrazových dat:

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    Obrazová data musí být zpracována do formátu, který očekává model TensorFlow. V tomto případě jsou obrazy načteny do paměti, zmenšeny na konzistentní velikost a obrazové body jsou extrahovány do číselného vektoru.

1. Přidejte odhad pro načtení modelu TensorFlow a jeho skóre:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Tato fáze v kanálu načte model TensorFlow do paměti a pak zpracuje vektor hodnot pixelů prostřednictvím sítě modelů TensorFlow. Použití vstupů na model hlubokého učení a generování výstupu pomocí modelu se označuje jako **vyhodnocování**. Při použití modelu v plném rozsahu, bodování provede odvození nebo předpověď.

    V tomto případě použijete celý model TensorFlow s výjimkou poslední vrstvy, což je vrstva, která provádí odvození. Výstup předposlední vrstvy je `softmax_2_preactivation`označen . Výstup této vrstvy je účinně vektor prvků, které charakterizují původní vstupní obrazy.

    Tento vektor funkce generovaný modelem TensorFlow bude použit jako vstup do ML.NET trénovacího algoritmu.

1. Přidejte odhad k mapování popisků řetězců v trénovacích datech na hodnoty celého klíče:

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    ML.NET, který je připojen další vyžaduje, `key` aby jeho popisky být ve formátu, nikoli libovolné řetězce. Klíč je číslo, které má mapování 1:1 na řetězcovou hodnotu.

1. Přidejte ML.NET tréninkový algoritmus:

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. Přidejte odhad, chcete-li předpovědět hodnotu klíče namapovat zpět do řetězce:

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Trénování modelu

1. Načtěte trénovací data pomocí obálky [LoadFromTextFile.](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) Jako další řádek `GenerateModel()` metody přidejte následující kód:

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových). Data lze načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu. `IDataView`

1. Trénování modelu s výše načtenými daty:

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    Metoda `Fit()` trénuje váš model použitím trénovací datové sady na kanál.

## <a name="evaluate-the-accuracy-of-the-model"></a>Vyhodnocení přesnosti modelu

1. Načtěte a transformujte testovací data přidáním následujícího `GenerateModel` kódu do dalšího řádku metody:

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Existuje několik ukázkových obrázků, které můžete použít k vyhodnocení modelu. Stejně jako trénovací data, `IDataView`tyto musí být načteny do , tak, aby mohly být transformovány podle modelu.

1. Přidejte do metody `GenerateModel()` následující kód pro vyhodnocení modelu:

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    Jakmile máte předpověď nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda:

    * Vyhodnotí model (porovná předpovídané hodnoty s `labels`testovací datovou sadou ).
    * Vrátí metriky výkonu modelu.

1. Zobrazení metrik přesnosti modelu

    Pomocí následujícího kódu můžete zobrazit metriky, sdílet výsledky a pak s nimi jednat:

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    Pro klasifikaci obrázků jsou vyhodnoceny následující metriky:

    * `Log-loss`- viz [Ztráta protokolu](../resources/glossary.md#log-loss). Chcete, aby ztráta protokolu byla co nejblíže nule.
    * `Per class Log-loss`. Chcete, aby ztráta protokolu na třídu byla co nejblíže nule.

1. Přidejte následující kód, který vrátí trénovaný model jako další řádek:

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Spusťte aplikaci.

1. Přidejte volání `GenerateModel` do `Main` metody po vytvoření třídy MLContext:

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. Přidejte volání `ClassifySingleImage()` metody jako další řádek kódu `Main` v metodě:

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. Spusťte konzolovou aplikaci (Ctrl + F5). Výsledky by měly být podobné následujícímu výstupu.  Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.

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

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci `TensorFlow` obrázků použitím učení přenosu na model v ML.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Pochopení problému
> * Začleňte předem vyškolený model TensorFlow do ML.NET potrubí
> * Trénování a hodnocení ML.NET modelu
> * Klasifikace testovacího obrázku

Podívejte se na ukázky Machine Learning úložiště GitHub prozkoumat rozbalené ukázky klasifikace obrázků.
> [!div class="nextstepaction"]
> [úložiště GitHub u dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/)
