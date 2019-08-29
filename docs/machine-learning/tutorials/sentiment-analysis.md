---
title: 'Kurz: Analyzovat komentáře webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 4daa7734f12c57a177fab3c62fdd96bda22838af
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107169"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Kurz: Analýza mínění komentářů k webu pomocí binární klasifikace v ML.NET

V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Vytvoření konzolové aplikace
> - Příprava dat
> - Načtení dat
> - Sestavování a výuka modelu
> - Vyhodnocení modelu
> - Použití modelu k vytvoření předpovědi
> - Zobrazit výsledky

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy

- [Datová sada vět mínění](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) s popiskem (Soubor ZIP)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **instalovat** . Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček. Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-your-data"></a>Příprava dat

> [!NOTE]
> Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et. Al,. KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017). UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml ]. Irvine, certifikační autorita: University of California, školní informace a počítačové vědy.

1. Stáhněte [soubor zip datové sady mínění](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)s popiskem a rozbalte ho.

2. Zkopírujte soubor do adresáře dat, který jste vytvořili. `yelp_labelled.txt`

3. V Průzkumník řešení klikněte pravým tlačítkem na `yelp_labeled.txt` soubor a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. Do horní části souboru `using` *program.cs* přidejte následující dodatečné příkazy:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. Vytvořte dvě globální pole, která budou uchovávat nedávno staženou cestu k souboru datové sady a uloženou cestu k souboru modelu:

    - `_dataPath`má cestu k datové sadě, která se používá ke výukě modelu.
    - `_modelPath`má cestu, kde je uložený model trained.

3. Přidejte následující kód na řádek přímo nad `Main` metodu pro určení cest:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Dále vytvořte třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

    - V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat** > **novou položku**.

    - V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** .

5. V editoru kódu se otevře soubor *SentimentData.cs* . Do horní části `using` *SentimentData.cs*přidejte následující příkaz:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do souboru *SentimentData.cs* :

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Způsob přípravy dat
Vstupní třída datové sady, `SentimentData` `string` má hodnotu pro `bool` komentáře uživatele (`SentimentText`) a hodnotu (`Sentiment`) pro mínění (kladné) nebo 0 (negativní). Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.  Kromě toho `Sentiment` má vlastnost atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) k `Label` označení jako pole. Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:

|SentimentText                         |Mínění (popisek) |
|--------------------------------------|----------|
|Waitress bylo v provozu trochu pomalé.|    0     |
|Crust není dobrá.                    |    0     |
|Wow... Tohle místo.              |    1     |
|Služba byla velmi výzvou.              |    1     |

`SentimentPrediction`je třída předpovědi, která se používá po školení modelu. Dědí z `SentimentData` , aby se vstup `SentimentText` mohl zobrazit společně s předpovědí výstupu. Logická hodnota je hodnota, kterou model předpovídá, pokud je zadán s novým vstupem `SentimentText`. `Prediction`

Třída `SentimentPrediction` Output obsahuje dvě další vlastnosti, které jsou vypočítány `Score` modelem: – nezpracované skóre počítané modelem a `Probability` – skóre, které se kalibruje na pravděpodobnost textu s kladným míněníem.

V tomto kurzu je `Prediction`nejdůležitější vlastností.

## <a name="load-the-data"></a>Načtení dat
Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET. Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

Aplikaci připravíte a pak načtěte data:

1. Nahraďte `Main` řádek v metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext: `Console.WriteLine("Hello World!")`

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. Přidejte následující jako další řádek kódu v `Main()` metodě:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. Vytvořte metodu hned `Main()` za metodou pomocí následujícího kódu: `LoadData()`

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()` Metoda provádí následující úlohy:

    - Načte data.
    - Rozdělí načtenou datovou sadu do sady výukových a testovacích datových sad.
    - Vrátí rozdělený vlak a testovací datové sady.

4. Do prvního řádku `LoadData()` metody přidejte následující kód:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro školení modelů a testování

Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.

1. Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v `LoadData()` metodě:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení do třídy [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) . Zadejte procento testovací sady dat s `testFraction`parametrem. Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.

2. Vraťte se `splitDataView` na konec `LoadData()` metody:

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Sestavování a výuka modelu

1. Do metody přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu `Main()` v metodě:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()` Metoda provádí následující úlohy:

    - Extrahuje a transformuje data.
    - Navlakuje model.
    - Předpovídá mínění na základě testovacích dat.
    - Vrátí model.

2. Vytvořte metodu hned `Main()` za metodou pomocí následujícího kódu: `BuildAndTrainModel()`

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Extrakce a transformace dat

1. Zavolat `FeaturizeText` jako další řádek kódu:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    Metoda v předchozím kódu převede textový sloupec (`SentimentText`) na sloupec typu `Features` číselného klíče, který používá algoritmus strojového učení, a přidá ho jako sloupec nové datové sady: `FeaturizeText()`

    |SentimentText                         |Mínění |Funkce              |
    |--------------------------------------|----------|----------------------|
    |Waitress bylo v provozu trochu pomalé.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust není dobrá.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Tohle místo.              |    1     |[0,35, 0,73, 0,46,...] |
    |Služba byla velmi výzvou.              |    1     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Přidání sledovacího algoritmu

Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat. Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.

Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus. Tento `estimator` údaj je připojen k a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry pro získání informací z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Přizpůsobte si model `splitTrainSet` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu `BuildAndTrainModel()` v metodě:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí vyškolený model, který se má použít pro vyhodnocení.

 Vrátí model na konci `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.

1. Vytvořte metodu, hned po `BuildAndTrainModel()`, s následujícím kódem: `Evaluate()`

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()` Metoda provádí následující úlohy:

    - Načte testovací datovou sadu.
    - Vytvoří vyhodnocovací filtr BinaryClassification.
    - Vyhodnotí model a vytvoří metriky.
    - Zobrazí metriky.

2. Přidejte volání do metody New z `Main()` metody přímo `BuildAndTrainModel()` pod voláním metody pomocí následujícího kódu:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformujte `Evaluate()`data přidáním následujícího kódu do: `splitTestSet`

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.

4. Vyhodnoťte model přidáním následujícího jako další řádek kódu v `Evaluate()` metodě:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Po nastavení`predictions`předpovědi () Metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečnou `Labels` hodnotou v testovací sadě a vrátí [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objekt, na kterém model probíhá.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověřování modelu

K zobrazení metrik použijte následující kód:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- `Accuracy` Metrika získá přesnost modelu, což je poměr správných předpovědi v sadě testů.

- `AreaUnderRocCurve` Metrika označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy. Chcete, aby `AreaUnderRocCurve` byl co nejblíže k jednomu.

- Metrika získá skóre modelu F1, což je míra rovnováhy mezi přesností a [](../resources/glossary.md#precision) odvoláním. [](../resources/glossary.md#recall) `F1Score`  Chcete, aby `F1Score` byl co nejblíže k jednomu.

### <a name="predict-the-test-data-outcome"></a>Předpověď výsledku testovacích dat

1. Vytvořte metodu hned `Evaluate()` za metodou pomocí následujícího kódu: `UseModelWithSingleItem()`

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()` Metoda provádí následující úlohy:

    - Vytvoří jeden komentář testovacích dat.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpovězené výsledky.

2. Přidejte volání do metody New z `Main()` metody přímo `Evaluate()` pod voláním metody pomocí následujícího kódu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Přidejte následující kód, který chcete vytvořit jako první řádek v `UseModelWithSingleItem()` metodě:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat.

4. Přidejte komentář k otestování předpovědi vyškolených modelů v `UseModelWithSingleItem()` metodě vytvořením `SentimentData`instance:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Předání dat testovacích komentářů do do `Prediction Engine` přidejte následujícím způsobem jako další řádky kódu `UseModelWithSingleItem()` v metodě:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.

6. Zobrazit `SentimentText` a odpovídající předpovědi mínění pomocí následujícího kódu:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Použití modelu předpovědi

### <a name="deploy-and-predict-batch-items"></a>Nasazení a předpověď položek Batch

1. Vytvořte metodu hned `UseModelWithSingleItem()` za metodou pomocí následujícího kódu: `UseModelWithBatchItems()`

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithBatchItems()` Metoda provádí následující úlohy:

    - Vytvoří data dávkového testu.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpovězené výsledky.

2. Přidejte volání do metody New z `Main` metody přímo `UseModelWithSingleItem()` pod voláním metody pomocí následujícího kódu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů `UseModelWithBatchItems()` v metodě:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Předpověď komentáře mínění

Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Kombinování a zobrazení předpovědi

Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Vzhledem `SentimentPrediction` k tomu, `SentimentData`že je `Transform()` zděděn z `SentimentText` , metoda naplněná předpovězenými poli. Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

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

Sestavování úspěšných modelů je iterativní proces. Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady. Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými [parametry Hyper-](../resources/glossary.md##hyperparameter) v pro každý algoritmus.

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Vytvoření konzolové aplikace
> - Příprava dat
> - Načtení dat
> - Sestavování a výuka modelu
> - Vyhodnocení modelu
> - Použití modelu k vytvoření předpovědi
> - Zobrazit výsledky

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.
> [!div class="nextstepaction"]
> [Klasifikace problému](github-issue-classification.md)
