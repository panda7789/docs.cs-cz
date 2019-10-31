---
title: 'Kurz: generování modelu klasifikace imagí ML.NET z předem připraveného modelu TensorFlow'
description: Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace imagí ML.NET. Model TensorFlow byl vyškolen pro klasifikaci imagí do tisíc kategorií. Model ML.NET využívá učení přenosu pro klasifikaci imagí do méně širších kategorií.
ms.date: 10/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: bd25a24e467148c46958b6e7ce7b18e181dab5fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129605"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Kurz: generování modelu klasifikace imagí ML.NET z předem připraveného modelu TensorFlow

Přečtěte si, jak přenést znalosti z existujícího modelu TensorFlow do nového modelu klasifikace imagí ML.NET.

Model TensorFlow byl vyškolen pro klasifikaci imagí do tisíc kategorií. Model ML.NET využívá část modelu TensorFlow ve svém kanálu k vytvoření modelu pro klasifikaci imagí do 3 kategorií.

Školení modelu [klasifikace obrázků](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od začátku vyžaduje nastavení milionů parametrů, tunu školicích dat a obrovského množství výpočetních prostředků (stovky hodin GPU). I když není tak efektivní jako školení vlastního modelu od začátku, pomůže vám tento proces zástupcem pracovat s tisíci imagí. miliony imagí s popisky a sestavování vlastního modelu je poměrně rychlé (během hodiny na počítači bez GPU). Tento kurz škáluje ještě více procesů a používá jenom spoustu školicích imagí.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Pochopení problému
> * Zahrňte předem vyškolený model TensorFlow do kanálu ML.NET
> * Výuka a vyhodnocení modelu ML.NET
> * Klasifikace testovací image

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) . Všimněte si, že ve výchozím nastavení je konfigurace projektu .NET pro tento kurz určena pro .NET Core 2,2.

## <a name="what-is-transfer-learning"></a>Co je učení přenosu?

Učení přenosu je proces použití znalostí získaných při řešení jednoho problému a jeho použití na jiný, ale související problém.

Pro účely tohoto kurzu použijete část TensorFlow modelu vyškolená pro klasifikaci imagí do tisíc kategorií – v modelu ML.NET, který klasifikuje obrázky do 3 kategorií.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.

* Balíček NuGet pro Microsoft.ML 1.3.1
* Balíček NuGet pro Microsoft. ML. ImageAnalytics 1.3.1
* Balíček NuGet pro Microsoft. ML. TensorFlow 1.3.1

* [Adresář assetů tutorial Soubor ZIP](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)

* [Model strojového učení InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Vyberte správnou úlohu strojového učení.

### <a name="deep-learning"></a>Obsáhlý Learning

[Obsáhlý Learning](https://en.wikipedia.org/wiki/Deep_learning) je podmnožinou Machine Learning, což jsou revolutionizing oblasti, jako je počítačové zpracování obrazu a rozpoznávání řeči.

Modely hloubkového učení jsou vyškoleny pomocí rozsáhlých sad [dat s popisky](https://en.wikipedia.org/wiki/Labeled_data) a [neuronové sítí](https://en.wikipedia.org/wiki/Artificial_neural_network) , které obsahují více výukových vrstev. Obsáhlý Learning:

* Je lepší pro některé úkoly, jako je Počítačové zpracování obrazu.
* Vyžaduje velké množství školicích dat.

Klasifikace obrázku je běžný Machine Learning úkol, který nám umožňuje automaticky klasifikovat obrázky do kategorií, jako jsou:

* Zjištění lidského obličeje v obrázku nebo ne.
* Detekce koček a psi.

 Nebo jak na následujících obrázcích zjistit, jestli je image a (n) jídla, hračka nebo zařízení:

Obrázek ![Pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Teddy, obrázek informačního](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![zprávy](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Předchozí image patří do Wikimedia a jsou jim tyto atributy:
>
> * Veřejná doména "220px-Pepperoni_pizza. jpg", https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear. jpg" pomocí [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) – s fotografací, CC by-SA 2,0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster. jpg" podle [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) vlastní práce, CC by-sa 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

`Inception model` je vyškolena pro klasifikaci imagí do tisíc kategorií, ale pro tento kurz je potřeba klasifikovat obrázky v menší sadě kategorií a jenom v těchto kategoriích. Zadejte `transfer` část `transfer learning`. Můžete přenést `Inception model`schopnost rozpoznávat a klasifikovat obrázky pro nové kategorie omezené na vlastní třídění imagí.

* Simulant
* Hračk
* Náplně

V tomto kurzu se používá model hloubkového učení [modelu](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) TensorFlow, který je oblíbený pro model rozpoznávání imagí, který je vyškolený pro `ImageNet` datovou sadu. Model TensorFlow klasifikuje celé obrázky do tisíc tříd, například "deštník", "Jersey" a "myčku".

Vzhledem k tomu, že `Inception model` již byl předem vyškolen na tisících různých imagí, interně obsahuje [funkce obrázků](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potřebné pro identifikaci obrázku. Pomocí těchto interních funkcí obrázků v modelu můžete vytvořit nový model s mnohem menším počtem tříd.

Jak je znázorněno v následujícím diagramu, přidáte odkaz na balíčky NuGet ML.NET v aplikacích .NET Core nebo .NET Framework. V rámci zahrnutí ML.NET zahrnuje a odkazuje na nativní knihovnu `TensorFlow`, která umožňuje napsat kód, který načte existující trained `TensorFlow`ový soubor modelu.

![Diagram TensorFlow Transform ML.NET archu](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Klasifikace s více třídami

Po použití modelu TensorFlowho zahájení k extrakci funkcí vhodných jako vstup pro klasický algoritmus strojového učení přidáme ML.NET třídění s [více třídami](../resources/tasks.md#multiclass-classification).

Konkrétní Trainer použitý v tomto případě je [algoritmus MULTINOMIAL logistické regrese](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Algoritmus implementovaný tímto Trainer se dobře hodí v případě problémů s velkým počtem funkcí, což je případ pro model hloubkového učení, který pracuje s daty imagí.

### <a name="data"></a>Data

Existují dva zdroje dat: `.tsv` soubor a soubory obrázků.  `tags.tsv` soubor obsahuje dva sloupce: první z nich je definována jako `ImagePath` a druhá druhá `Label` odpovídající imagi. Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:

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

Obrázky školení a testování se nacházejí ve složkách assetů, které stáhnete do souboru ZIP. Tyto image patří do Wikimedia.
> *[Wikimedia](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), bezplatné úložiště médií.* Načteno 10:48, 17. října 2018 z: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Instalace

### <a name="create-a-project"></a>Vytvoření projektu

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TransferLearningTF".

1. Nainstalujte **balíček NuGet Microsoft.ml**:

    * V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.
    * Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet a vyhledejte **Microsoft.ml**.
    * Klikněte na rozevírací seznam **verze** , v seznamu vyberte balíček **1.3.1** a vyberte tlačítko **nainstalovat** .
    * V dialogovém okně **Náhled změn** vyberte tlačítko **OK** .
    * Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, v dialogu pro **přijetí licence** vyberte tlačítko **přijmout** .
    * Opakujte tyto kroky pro **Microsoft. ml. ImageAnalytics v 1.3.1** a **Microsoft. ml. TensorFlow v 1.3.1**.

### <a name="download-assets"></a>Stažení prostředků

1. Stáhněte si [soubor zip adresáře Project assets](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)a rozbalte ho.

1. Zkopírujte adresář `assets` do adresáře projektu *TransferLearningTF* . Tento adresář a jeho podadresáře obsahují data a podpůrné soubory (s výjimkou modelu zahájení, který si stáhnete a přidáte v dalším kroku) potřebném pro tento kurz.

1. Stáhněte si [model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)zahájení a rozbalte ho.

1. Zkopírujte obsah `inception5h` adresáře do projektu *TransferLearningTF* `assets/inception` Directory. Tento adresář obsahuje model a další podpůrné soubory potřebné pro tento kurz, jak je znázorněno na následujícím obrázku:

   ![Obsah adresáře v adresáři](./media/image-classification/inception-files.png)

1. V Průzkumník řešení klikněte pravým tlačítkem na každý ze souborů v adresáři assetů a podadresářích a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. Do horní části souboru *program.cs* přidejte následující dodatečné příkazy `using`:

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. Přidejte následující kód na řádek vpravo nad `Main` metodou pro určení cest prostředků:

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. Vytvořte třídy pro vstupní data a předpovědi.

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    `ImageData` je vstupní třída dat obrázku a má následující <xref:System.String> pole:

    * `ImagePath` obsahuje název souboru obrázku.
    * `Label` obsahuje hodnotu pro popisek obrázku.

1. Přidejte do projektu novou třídu pro `ImagePrediction`:

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` je třída prediktivních imagí a má následující pole:

    * `Score` obsahuje procento spolehlivosti pro danou klasifikaci obrázku.
    * `PredictedLabelValue` obsahuje hodnotu pro předpovězený popisek klasifikace obrázku.

    `ImagePrediction` je třída použitá pro předpověď po vyškolení modelu. Pro cestu k imagi má `string` (`ImagePath`). `Label` slouží k opakovanému použití a učení modelu. `PredictedLabelValue` se používá během předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

1. Inicializujte `mlContext` proměnnou novou instancí `MLContext`.  Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě `Main`:

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    [Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje se `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů. Je podobné, koncepčně, `DBContext` v Entity Framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Vytvoření struktury pro parametry modelu vytvářené

1. Model zahájení má několik parametrů, které je třeba předat. Vytvořte strukturu pro mapování hodnot parametrů na popisné názvy pomocí následujícího kódu, a to hned za `Main()` metodou:

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Vytvoření metody zobrazovacího nástroje

Vzhledem k tomu, že zobrazíte data obrázku a související předpovědi více než jednou, vytvořte metodu zobrazení nástrojů pro zpracování zobrazení obrázků a výsledků předpovědi.

1. Vytvořte metodu `DisplayResults()` hned po `InceptionSettings` struktuře pomocí následujícího kódu:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Vyplňte text `DisplayResults` metody:

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Vytvoření metody Utility souboru. TSV

1. Vytvořte metodu `ReadFromTsv()` hned za metodou `DisplayResults()` pomocí následujícího kódu:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Vyplňte text `ReadFromTsv` metody:

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    Kód analyzuje soubor `tags.tsv`, aby přidal cestu souboru k názvu souboru obrázku pro vlastnost `ImagePath` a načetl ji a `Label` do objektu `ImageData`.

### <a name="create-a-method-to-make-a-prediction"></a>Vytvoření metody pro předpověď

1. Vytvořte metodu `ClassifySingleImage()` těsně před metodou `DisplayResults()` pomocí následujícího kódu:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Vytvořte objekt `ImageData`, který obsahuje plně kvalifikovanou cestu a název souboru obrázku pro jeden `ImagePath`. Přidejte následující kód jako další řádky v metodě `ClassifySingleImage()`:

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. Udělejte jednu předpověď přidáním následujícího kódu jako další řádek v metodě `ClassifySingleImage`:

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    K získání předpovědi použijte metodu [předpověď ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) . [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.

1. Zobrazit výsledek předpovědi jako další řádek kódu v metodě `ClassifySingleImage()`:

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Vytvoření kanálu modelu ML.NET

Kanál ML.NET modelu je řetězec odhady. Všimněte si, že během vytváření kanálu nedojde k žádnému spuštění. Objekty Estimator jsou vytvořeny, ale nejsou spuštěny.

1. Přidejte metodu pro vytvoření modelu

    Tato metoda je srdcem kurzu. Vytvoří kanál pro model a navlakuje kanál k vytvoření modelu ML.NET. Vyhodnocuje také model proti dříve nezobrazeným datům testu.

    Vytvořte metodu `GenerateModel()` hned po `InceptionSettings` struktuře a těsně před metodou `DisplayResults()` pomocí následujícího kódu:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Přidat odhady pro načtení, změnu velikosti a extrakci pixelů z dat obrázku:

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    Data obrázku musí být zpracována ve formátu, který očekává model TensorFlow. V tomto případě jsou obrázky načteny do paměti, jsou změněna na konzistentní velikost a pixely jsou extrahovány do číselného vektoru.

1. Přidejte Estimator, abyste načetli model TensorFlow, a zadávejte skóre:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    Tato fáze v kanálu načte model TensorFlow do paměti a pak zpracovává vektor hodnot obrazových bodů prostřednictvím sítě modelu TensorFlow. Použití vstupů na model hloubkového učení a generování výstupu pomocí modelu se označuje jako **bodování**. Při použití modelu v celém rozsahu je bodování odvozeno nebo předpověď.

    V tomto případě použijete všechen TensorFlow model kromě poslední vrstvy, což je vrstva, která provádí odvození. Výstup předposlední vrstvy je označený `softmax_2_preactivation`. Výstup této vrstvy je efektivně vektor funkcí, které charakterizují původní vstupní image.

    Tento vektor funkce generovaný modelem TensorFlow se použije jako vstup pro školicí algoritmus ML.NET.

1. Přidejte Estimator k namapování popisků řetězce v školicích datech na hodnoty celočíselného klíče:

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    ML.NET Trainer, který je připojen k dalšímu, vyžaduje, aby popisky byly v `key` formátu místo libovolných řetězců. Klíč je číslo, které má jeden k jednomu mapování na hodnotu řetězce.

1. Přidejte ML.NET školicí algoritmus:

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. Přidejte Estimator k namapování hodnoty předpovězeného klíče zpátky do řetězce:

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Výuka modelu

1. Načtěte školicí data pomocí obálky [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) . Přidejte následující kód jako další řádek v metodě `GenerateModel()`:

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView` je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu `IDataView`.

1. Vyškolit model s daty načtenými výše:

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    Metoda `Fit()` navlakuje váš model použitím školicí datové sady na kanál.

## <a name="evaluate-the-accuracy-of-the-model"></a>Vyhodnotit přesnost modelu

1. Načtěte a Transformujte testovací data přidáním následujícího kódu na další řádek metody `GenerateModel`:

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Existuje několik ukázkových imagí, které můžete použít k vyhodnocení modelu. Podobně jako u školicích dat je potřeba je načíst do `IDataView`, aby je bylo možné transformovat podle modelu.

1. Přidejte následující kód do metody `GenerateModel()` pro vyhodnocení modelu:

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    Jakmile máte předsadu předpovědi, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

    * Vyhodnotí model (porovná předpovězené hodnoty s testovací datovou sadou `labels`).
    * Vrátí metriku výkonu modelu.

1. Zobrazit metriky přesnosti modelu

    Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    Pro klasifikaci imagí jsou vyhodnocovány následující metriky:

    * `Log-loss` – viz [prohra protokolu](../resources/glossary.md#log-loss). Chcete, aby byla ztráta protokolu co nejblíže k nule.
    * `Per class Log-loss`. Požadujete, aby byla ztráta protokolu podle třídy co nejblíže k nule.

1. Přidejte následující kód, který vrátí vycvičený model jako další řádek:

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Spusťte aplikaci!

1. Přidejte volání `GenerateModel` v metodě `Main` po vytvoření třídy MLContext:

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. Přidejte volání metody `ClassifySingleImage()` jako další řádek kódu v metodě `Main`:

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. Spusťte konzolovou aplikaci (CTRL + F5). Výsledky by měly být podobné následujícímu výstupu.  Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.

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

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro klasifikaci imagí tím, že použijete učení přenosu na `TensorFlow` model v ML.NET.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .

V tomto kurzu jste zjistili, jak:
> [!div class="checklist"]
>
> * Pochopení problému
> * Zahrňte předem vyškolený model TensorFlow do kanálu ML.NET
> * Výuka a vyhodnocení modelu ML.NET
> * Klasifikace testovací image

Podívejte se na úložiště GitHub Samples Machine Learning a prozkoumejte ukázku klasifikace rozbalené image.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-Samples – úložiště GitHub](https://github.com/dotnet/machinelearning-samples/)
