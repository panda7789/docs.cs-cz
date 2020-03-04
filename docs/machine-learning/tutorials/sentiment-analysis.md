---
title: 'Kurz: analýza komentářů webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241127"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Kurz: analýza mínění komentářů k webu pomocí binární klasifikace v ML.NET

V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvoření konzolové aplikace
> - Příprava dat
> - Načtení dat
> - Sestavování a výuka modelu
> - Vyhodnocení modelu
> - Použití modelu k vytvoření předpovědi
> - Zobrazení výsledků

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="prerequisites"></a>Předpoklady

- [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy

- [Mínění – datová sada vět s popisky](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** . Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček. Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-your-data"></a>Příprava dat

> [!NOTE]
> Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et. Al,. KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017). UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, školní informace a počítačové vědy.

1. Stáhněte [soubor zip datové sady mínění s popiskem](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.

2. Zkopírujte soubor `yelp_labelled.txt` do adresáře *dat* , který jste vytvořili.

3. V Průzkumník řešení klikněte pravým tlačítkem na soubor `yelp_labeled.txt` a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. Do horní části souboru *program.cs* přidejte následující další příkazy `using`:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Přidejte následující kód na řádek vpravo nad `Main` metodou, chcete-li vytvořit pole pro uchování nedávno stažené cesty souboru datové sady:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Dále vytvořte třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

    - V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**.

    - V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** .

1. V editoru kódu se otevře soubor *SentimentData.cs* . Do horní části *SentimentData.cs*přidejte následující příkaz `using`:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do souboru *SentimentData.cs* :

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Způsob přípravy dat

Vstupní datová třída, `SentimentData`, má `string` pro komentáře uživatele (`SentimentText`) a hodnotu `bool` (`Sentiment`) pro hodnotu 1 (kladné) nebo 0 (negativní) pro mínění. Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.  Kromě toho vlastnost `Sentiment` má atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) k označení jako pole `Label`. Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:

|SentimentText                         |Mínění (popisek) |
|--------------------------------------|----------|
|Waitress bylo v provozu trochu pomalé.|    0     |
|Crust není dobrá.                    |    0     |
|Wow... Tohle místo.              |    1     |
|Služba byla velmi výzvou.              |    1     |

`SentimentPrediction` je třída předpovědi, která se používá po školení modelu. Dědí z `SentimentData` tak, aby se vstupní `SentimentText` mohl zobrazit společně s předpovědí výstupu. `Prediction` Boolean je hodnota, kterou model předpovídá, pokud je zadán s novým vstupním `SentimentText`.

Výstupní třída `SentimentPrediction` obsahuje dvě další vlastnosti, které jsou vypočítány modelem: `Score`-nezpracované skóre počítané modelem a `Probability` – skóre kalibrované na pravděpodobnost textu, který má kladný mínění.

V tomto kurzu je nejdůležitější vlastností `Prediction`.

## <a name="load-the-data"></a>Načtení dat

Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView` je flexibilní a efektivní způsob popisující tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu `IDataView`.

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET. Inicializuje se `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu pro vytváření modelů. Je podobný a koncepčně `DBContext` v Entity Framework.

Aplikaci připravíte a pak načtěte data:

1. Nahraďte `Console.WriteLine("Hello World!")` řádek v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné mlContext:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Jako další řádek kódu v metodě `Main()` přidejte následující:

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Vytvořte metodu `LoadData()` hned za metodou `Main()` pomocí následujícího kódu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Metoda `LoadData()` provádí následující úlohy:

    - Načte data.
    - Rozdělí načtenou datovou sadu do sady výukových a testovacích datových sad.
    - Vrátí rozdělený vlak a testovací datové sady.

4. Do prvního řádku `LoadData()` metody přidejte následující kód:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro školení modelů a testování

Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.

1. Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v metodě `LoadData()`:

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení do třídy [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) . Zadejte procento testovací sady dat s parametrem `testFraction`. Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.

2. Vraťte `splitDataView` na konci `LoadData()` metody:

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Sestavování a výuka modelu

1. Přidejte následující volání metody `BuildAndTrainModel`jako další řádek kódu v metodě `Main()`:

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Metoda `BuildAndTrainModel()` provádí následující úlohy:

    - Extrahuje a transformuje data.
    - Navlakuje model.
    - Předpovídá mínění na základě testovacích dat.
    - Vrátí model.

2. Vytvořte metodu `BuildAndTrainModel()` hned za metodou `Main()` pomocí následujícího kódu:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Extrakce a transformace dat

1. Zavolejte `FeaturizeText` jako další řádek kódu:

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Metoda `FeaturizeText()` v předchozím kódu převede textový sloupec (`SentimentText`) na typ číselného klíče `Features` sloupec používaný algoritmem strojového učení a přidá ho jako sloupec nové datové sady:

    |SentimentText                         |Mínění |Funkce              |
    |--------------------------------------|----------|----------------------|
    |Waitress bylo v provozu trochu pomalé.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust není dobrá.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Tohle místo.              |    1     |[0,35, 0,73, 0,46,...] |
    |Služba byla velmi výzvou.              |    1     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Přidání sledovacího algoritmu

Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat. Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.

Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus. Tento údaj je připojen k `estimator` a přijímá natrénuje `SentimentText` (`Features`) a vstupní parametry `Label` pro další informace z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Přizpůsobit model na `splitTrainSet`á data a vrátit vyškolený model přidáním následujícího jako další řádek kódu v metodě `BuildAndTrainModel()`:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí vyškolený model, který se má použít pro vyhodnocení.

 Vrátí model na konci `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.

1. Vytvořte metodu `Evaluate()` hned po `BuildAndTrainModel()`s následujícím kódem:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Metoda `Evaluate()` provádí následující úlohy:

    - Načte testovací datovou sadu.
    - Vytvoří vyhodnocovací filtr BinaryClassification.
    - Vyhodnotí model a vytvoří metriky.
    - Zobrazí metriky.

2. Přidejte volání do nové metody z metody `Main()`, přímo pod voláním metody `BuildAndTrainModel()`, pomocí následujícího kódu:

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformujte data `splitTestSet` přidáním následujícího kódu do `Evaluate()`:

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.

4. Vyhodnoťte model přidáním následujícího jako další řádek kódu v metodě `Evaluate()`:

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Jakmile máte sadu předpovědi (`predictions`), metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovná předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrátí objekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) , jak model provádí.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověřování modelu

K zobrazení metrik použijte následující kód:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- Metrika `Accuracy` získá přesnost modelu, což je poměr správných předpovědi v sadě testů.

- Metrika `AreaUnderRocCurve` označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy. Chcete, aby `AreaUnderRocCurve` co nejblíže k jednomu.

- Metrika `F1Score` získá skóre modelu F1, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).  Chcete, aby `F1Score` co nejblíže k jednomu.

### <a name="predict-the-test-data-outcome"></a>Předpověď výsledku testovacích dat

1. Vytvořte metodu `UseModelWithSingleItem()` hned za metodou `Evaluate()` pomocí následujícího kódu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithSingleItem()` provádí následující úlohy:

    - Vytvoří jeden komentář testovacích dat.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpovězené výsledky.

2. Přidejte volání do nové metody z metody `Main()`, přímo pod voláním metody `Evaluate()`, pomocí následujícího kódu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Přidejte následující kód, který chcete vytvořit jako první řádek v metodě `UseModelWithSingleItem()`:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.

4. Přidejte komentář k otestování předpovědi vyškolených modelů v metodě `UseModelWithSingleItem()` vytvořením instance `SentimentData`:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Předání dat testovacích komentářů do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) přidáním následujícího jako další řádky kódu v metodě `UseModelWithSingleItem()`:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.

6. Zobrazit `SentimentText` a odpovídající předpovědi mínění pomocí následujícího kódu:

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Použití modelu předpovědi

### <a name="deploy-and-predict-batch-items"></a>Nasazení a předpověď položek Batch

1. Vytvořte metodu `UseModelWithBatchItems()` hned za metodou `UseModelWithSingleItem()` pomocí následujícího kódu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithBatchItems()` provádí následující úlohy:

    - Vytvoří data dávkového testu.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpovězené výsledky.

2. Přidejte volání do nové metody z metody `Main`, přímo pod voláním metody `UseModelWithSingleItem()`, pomocí následujícího kódu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů v metodě `UseModelWithBatchItems()`:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Předpověď komentáře mínění

Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Kombinování a zobrazení předpovědi

Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Vzhledem k tomu, že `SentimentPrediction` dědí z `SentimentData`, `Transform()` metoda naplněná `SentimentText` s předpovězenými poli. Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Výsledky

Výsledky by měly vypadat podobně jako následující. Během zpracování se zobrazí zprávy. Můžou se zobrazovat upozornění nebo zpracovávat zprávy. Tyto výsledky byly z důvodu srozumitelnosti odebrány z následujících výsledků.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď zpráv mínění.

Sestavování úspěšných modelů je iterativní proces. Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady. Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými [parametry Hyper-](../resources/glossary.md#hyperparameter) v pro každý algoritmus.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvoření konzolové aplikace
> - Příprava dat
> - Načtení dat
> - Sestavování a výuka modelu
> - Vyhodnocení modelu
> - Použití modelu k vytvoření předpovědi
> - Zobrazení výsledků

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.
> [!div class="nextstepaction"]
> [Klasifikace problému](github-issue-classification.md)
