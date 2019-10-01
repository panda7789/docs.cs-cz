---
title: 'Kurz: analýza komentářů webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárních souborů používá C# v aplikaci Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: c6b9d51a8ab91b4365c909993211f11ab3436808
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700862"
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
> - Zobrazit výsledky

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy

- [Mínění – datová sada vět s popisky](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** . Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček. Totéž udělejte pro balíček NuGet **Microsoft. ml. FastTree** .

## <a name="prepare-your-data"></a>Příprava dat

> [!NOTE]
> Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et. Al,. KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017). UCI Machine Learning úložiště [http://archive.ics.uci.edu/ml ]. Irvine, CA: University of California, školní informace a počítačové vědy.

1. Stáhněte [soubor zip datové sady mínění s popiskem](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.

2. Zkopírujte soubor `yelp_labelled.txt` do adresáře *dat* , který jste vytvořili.

3. V Průzkumník řešení klikněte pravým tlačítkem na soubor `yelp_labeled.txt` a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. Do horní části souboru *program.cs* přidejte následující dodatečné příkazy `using`:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. Vytvořte dvě globální pole, která budou uchovávat nedávno staženou cestu k souboru datové sady a uloženou cestu k souboru modelu:

    - `_dataPath` má cestu k datové sadě, která se používá ke výukě modelu.
    - `_modelPath` má cestu, kde je uložený model trained.

3. Přidejte následující kód na řádek vpravo nad metodu `Main` pro určení cest:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Dále vytvořte třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

    - V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **přidat** **novou položku** > .

    - V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** .

5. V editoru kódu se otevře soubor *SentimentData.cs* . Přidejte následující příkaz `using` do horní části *SentimentData.cs*:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do souboru *SentimentData.cs* :

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Způsob přípravy dat
Vstupní datová třída `SentimentData` má `string` pro komentáře uživatele (`SentimentText`) a hodnotu `bool` (`Sentiment`) pro mínění (kladné) nebo 0 (negativní). Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.  Kromě toho vlastnost `Sentiment` má atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) , který ho určí jako pole `Label`. Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:

|SentimentText                         |Mínění (popisek) |
|--------------------------------------|----------|
|Waitress bylo v provozu trochu pomalé.|    0,8     |
|Crust není dobrá.                    |    0,8     |
|Wow... Tohle místo.              |    první     |
|Služba byla velmi výzvou.              |    první     |

`SentimentPrediction` je třída předpovědi, která se používá po školení modelu. Dědí z `SentimentData`, takže vstupní `SentimentText` lze zobrazit spolu s předpovědí výstupu. Logická hodnota `Prediction` je hodnota, kterou model předpovídá, když je zadaný s novým vstupem `SentimentText`.

Třída Output `SentimentPrediction` obsahuje dvě další vlastnosti, které jsou vypočítány modelem: `Score` – nezpracované skóre počítané modelem a `Probability` – skóre, které má kladný mínění.

V tomto kurzu je nejdůležitější vlastnost `Prediction`.

## <a name="load-the-data"></a>Načtení dat
Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView` je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu @no__t 0.

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET. Inicializace `mlContext` vytvoří nové prostředí ML.NET, které se dá sdílet napříč objekty pracovního postupu vytváření modelů. Je podobné, koncepčně, `DBContext` v Entity Framework.

Aplikaci připravíte a pak načtěte data:

1. Nahraďte řádek `Console.WriteLine("Hello World!")` v metodě `Main` následujícím kódem pro deklaraci a inicializaci proměnné mlContext:

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. Přidejte následující jako další řádek kódu do metody `Main()`:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

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

4. Do prvního řádku metody `LoadData()` přidejte následující kód:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro školení modelů a testování

Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.

1. Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v metodě `LoadData()`:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení do třídy [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) . Zadejte procento testovací sady dat pomocí `testFraction`parameter. Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.

2. Vrátí `splitDataView` na konci metody `LoadData()`:

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Sestavování a výuka modelu

1. Přidejte následující volání do `BuildAndTrainModel`method jako další řádek kódu v metodě `Main()`:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

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

1. Jako další řádek kódu volejte `FeaturizeText`:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    Metoda `FeaturizeText()` v předchozím kódu převede sloupec text (`SentimentText`) na číselný typ klíče `Features`, který používá algoritmus strojového učení, a přidá ho jako sloupec nové datové sady:

    |SentimentText                         |mínění |Funkce              |
    |--------------------------------------|----------|----------------------|
    |Waitress bylo v provozu trochu pomalé.|    0,8     |[0,76, 0,65, 0,44,...] |
    |Crust není dobrá.                    |    0,8     |[0,98, 0,43, 0,54,...] |
    |Wow... Tohle místo.              |    první     |[0,35, 0,73, 0,46,...] |
    |Služba byla velmi výzvou.              |    první     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Přidání sledovacího algoritmu

Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat. Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.

Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus. Tato hodnota je připojená k `estimator` a přijímá natrénuje `SentimentText` (`Features`) a vstupní parametry `Label` k získání informací z historických dat.

### <a name="train-the-model"></a>Výuka modelu

Přizpůsobit model na data `splitTrainSet` a vrátit vyškolený model přidáním následujícího jako další řádek kódu v metodě `BuildAndTrainModel()`:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí vyškolený model, který se má použít pro vyhodnocení.

 Vrátí model na konci metody `BuildAndTrainModel()`:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.

1. Vytvořte metodu `Evaluate()` hned za `BuildAndTrainModel()` s následujícím kódem:

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

2. Přidejte volání do nové metody z metody `Main()` přímo pod voláním metody `BuildAndTrainModel()` pomocí následujícího kódu:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformujte data `splitTestSet` přidáním následujícího kódu do `Evaluate()`:

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.

4. Vyhodnoťte model přidáním následujícího jako další řádek kódu v metodě `Evaluate()`:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Jakmile máte předpověď sady (`predictions`), metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrátí objekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) podle toho, jak model provádí.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověřování modelu

K zobrazení metrik použijte následující kód:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- Metrika `Accuracy` získá přesnost modelu, což je poměr správných předpovědi v sadě testů.

- Metrika `AreaUnderRocCurve` označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy. Chcete `AreaUnderRocCurve` co nejblíže k jednomu.

- Metrika `F1Score` získá skóre modelu F1, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).  Chcete `F1Score` co nejblíže k jednomu.

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

2. Přidejte volání do nové metody z metody `Main()` přímo pod voláním metody `Evaluate()` pomocí následujícího kódu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Přidejte následující kód, který chcete vytvořit jako první řádek v metodě `UseModelWithSingleItem()`:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci. V této příručce najdete informace o [použití `PredictionEnginePool` v ASP.NET Core webovém rozhraní API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) .

    > [!NOTE]
    > rozšíření služby `PredictionEnginePool` je nyní ve verzi Preview.
    
4. Přidejte komentář k otestování předpovědi vyškolených modelů v metodě `UseModelWithSingleItem()` vytvořením instance `SentimentData`:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Předání dat testovacích komentářů do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) přidáním následujícího jako další řádky kódu v metodě `UseModelWithSingleItem()`:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.

6. Zobrazit `SentimentText` a odpovídající předpověď mínění pomocí následujícího kódu:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

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

2. Přidejte volání do nové metody z metody `Main` přímo pod voláním metody `UseModelWithSingleItem()` pomocí následujícího kódu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů v metodě `UseModelWithBatchItems()`:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Předpověď komentáře mínění

Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Kombinování a zobrazení předpovědi

Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Vzhledem k tomu, že `SentimentPrediction` se dědí z `SentimentData`, metoda `Transform()` naplněná `SentimentText` s předpokládanými poli. Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:

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

V tomto kurzu jste zjistili, jak:
> [!div class="checklist"]
>
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
