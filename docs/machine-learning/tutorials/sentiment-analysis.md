---
title: 'Kurz: analýza komentářů webu – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárního prostředí používá jazyk C# v aplikaci Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: de8ea511b3d421e391b182a6de079b854d3f2390
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281750"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Kurz: analýza mínění komentářů k webu pomocí binární klasifikace v ML.NET

V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Mínění třídění binárního prostředí používá jazyk C# v aplikaci Visual Studio 2017.

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

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou vývoj .NET Core pro různé platformy

- [Mínění – datová sada vět s popisky](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **konzolovou aplikaci .NET Core** nazvanou "SentimentAnalysis".

2. Vytvořte v projektu adresář s názvem *data* a uložte soubory sady dat.

3. Nainstalujte **balíček NuGet Microsoft.ml**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet** . Vyhledejte **Microsoft.ml**, vyberte požadovaný balíček a pak vyberte tlačítko **nainstalovat** . Pokračujte v instalaci tak, že souhlasíte s licenčními podmínkami pro zvolený balíček.

## <a name="prepare-your-data"></a>Příprava dat

> [!NOTE]
> Datové sady pro tento kurz jsou ze skupiny "z" na jednotlivé štítky pomocí hlubokých funkcí, Kotzias et. Al,. KONFERENCE KDD 2015 a hostuje se v úložišti UCI Machine Learning – Dua, D. a Karra Taniskidou, E. (2017). UCI Machine Learning úložiště [ http://archive.ics.uci.edu/ml ]. Irvine, CA: University of California, školní informace a počítačové vědy.

1. Stáhněte [soubor zip datové sady mínění s popiskem](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.

2. Zkopírujte `yelp_labelled.txt` soubor do adresáře *dat* , který jste vytvořili.

3. V Průzkumník řešení klikněte pravým tlačítkem na `yelp_labeled.txt` soubor a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. `using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Přidejte následující kód na řádek vpravo nad `Main` metodou, chcete-li vytvořit pole, které bude uchovávat nedávno staženou cestu k souboru datové sady:

    [!code-csharp[Declare global variables](./snippets/sentiment-analysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Dále vytvořte třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

    - V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.

    - V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *SentimentData.cs*. Pak vyberte tlačítko **Přidat** .

1. V editoru kódu se otevře soubor *SentimentData.cs* . `using`Do horní části *SentimentData.cs*přidejte následující příkaz:

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction` , do souboru *SentimentData.cs* :

    [!code-csharp[DeclareTypes](./snippets/sentiment-analysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Způsob přípravy dat

Vstupní třída datové sady, `SentimentData` má `string` hodnotu pro komentáře uživatele ( `SentimentText` ) a `bool` `Sentiment` hodnotu () pro mínění (kladné) nebo 0 (negativní). Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy, které jsou k nim připojeny, což popisuje pořadí datových souborů jednotlivých polí.  Kromě toho `Sentiment` má vlastnost atribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) k označení jako `Label` pole. Následující ukázkový soubor neobsahuje řádek záhlaví a vypadá takto:

|SentimentText                         |Mínění (popisek) |
|--------------------------------------|----------|
|Waitress bylo v provozu trochu pomalé.|    0     |
|Crust není dobrá.                    |    0     |
|Wow... Tohle místo.              |    1     |
|Služba byla velmi výzvou.              |    1     |

`SentimentPrediction`je třída předpovědi, která se používá po školení modelu. Dědí z `SentimentData` , aby se vstup `SentimentText` mohl zobrazit společně s předpovědí výstupu. `Prediction`Logická hodnota je hodnota, kterou model předpovídá, pokud je zadán s novým vstupem `SentimentText` .

Třída Output `SentimentPrediction` obsahuje dvě další vlastnosti, které jsou vypočítány modelem: `Score` – nezpracované skóre počítané modelem a `Probability` – skóre, které se kalibruje na pravděpodobnost textu s kladným míněníem.

V tomto kurzu je nejdůležitější vlastností `Prediction` .

## <a name="load-the-data"></a>Načtení dat

Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET. Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

Aplikaci připravíte a pak načtěte data:

1. Nahraďte `Console.WriteLine("Hello World!")` řádek v `Main` metodě následujícím kódem pro deklaraci a inicializaci proměnné mlContext:

    [!code-csharp[CreateMLContext](./snippets/sentiment-analysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Přidejte následující jako další řádek kódu v `Main()` metodě:

    [!code-csharp[CallLoadData](./snippets/sentiment-analysis/csharp/Program.cs#CallLoadData)]

3. Vytvořte `LoadData()` metodu hned za `Main()` metodou pomocí následujícího kódu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()`Metoda provádí následující úlohy:

    - Načte data.
    - Rozdělí načtenou datovou sadu do sady výukových a testovacích datových sad.
    - Vrátí rozdělený vlak a testovací datové sady.

4. Do prvního řádku metody přidejte následující kód `LoadData()` :

    [!code-csharp[LoadData](./snippets/sentiment-analysis/csharp/Program.cs#LoadData "loading dataset")]

    Metoda [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView` .

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro školení modelů a testování

Při přípravě modelu použijete část datové sady ke školení a část datové sady k otestování přesnosti modelu.

1. Chcete-li rozdělit načtená data do potřebných datových sad, přidejte následující kód jako další řádek v `LoadData()` metodě:

    [!code-csharp[SplitData](./snippets/sentiment-analysis/csharp/Program.cs#SplitData "Split the Data")]

    Předchozí kód používá metodu [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pro rozdělení načtené datové sady do vlakových a testovacích datových sad a jejich vrácení ve <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> třídě. Zadejte procento testovací sady dat s `testFraction` parametrem. Výchozí hodnota je 10%, v tomto případě použijete 20% k vyhodnocení více dat.

2. Vraťte se na `splitDataView` konec `LoadData()` metody:

    [!code-csharp[ReturnSplitData](./snippets/sentiment-analysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Sestavování a výuka modelu

1. Do metody přidejte následující volání `BuildAndTrainModel` metody jako další řádek kódu v `Main()` metodě:

    [!code-csharp[CallBuildAndTrainModel](./snippets/sentiment-analysis/csharp/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()`Metoda provádí následující úlohy:

    - Extrahuje a transformuje data.
    - Navlakuje model.
    - Předpovídá mínění na základě testovacích dat.
    - Vrátí model.

2. Vytvořte `BuildAndTrainModel()` metodu hned za `Main()` metodou pomocí následujícího kódu:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Extrakce a transformace dat

1. Zavolat `FeaturizeText` jako další řádek kódu:

    [!code-csharp[FeaturizeText](./snippets/sentiment-analysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    `FeaturizeText()`Metoda v předchozím kódu převede textový sloupec ( `SentimentText` ) na sloupec typu číselného klíče, který `Features` používá algoritmus strojového učení, a přidá ho jako sloupec nové datové sady:

    |SentimentText                         |Mínění |Funkce              |
    |--------------------------------------|----------|----------------------|
    |Waitress bylo v provozu trochu pomalé.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust není dobrá.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Tohle místo.              |    1     |[0,35, 0,73, 0,46,...] |
    |Služba byla velmi výzvou.              |    1     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Přidání sledovacího algoritmu

Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat. Aplikace rozděluje komentáře k webu buď jako kladné, nebo záporné, takže použijte úlohu binární klasifikace.

Přidejte úlohu Machine Learning do definice transformace dat tak, že přidáte následující kód jako další řádek kódu v `BuildAndTrainModel()` :

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](./snippets/sentiment-analysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš vyhodnocovací školicí algoritmus. Tento údaj je připojen k `estimator` a přijímá natrénuje `SentimentText` ( `Features` ) a `Label` vstupní parametry pro získání informací z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Přizpůsobte si model `splitTrainSet` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `BuildAndTrainModel()` metodě:

[!code-csharp[TrainModel](./snippets/sentiment-analysis/csharp/Program.cs#TrainModel "Train the model")]

Metoda [přizpůsobení () nasadí](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) váš model pomocí transformace datové sady a použití školení.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí vyškolený model, který se má použít pro vyhodnocení.

 Vrátí model na konci `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](./snippets/sentiment-analysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Po vyzkoušení modelu použijte data testu a ověřte výkon modelu.

1. Vytvořte `Evaluate()` metodu, hned po `BuildAndTrainModel()` , s následujícím kódem:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()`Metoda provádí následující úlohy:

    - Načte testovací datovou sadu.
    - Vytvoří vyhodnocovací filtr BinaryClassification.
    - Vyhodnotí model a vytvoří metriky.
    - Zobrazí metriky.

2. Přidejte volání do metody New z `Main()` metody přímo pod `BuildAndTrainModel()` voláním metody pomocí následujícího kódu:

    [!code-csharp[CallEvaluate](./snippets/sentiment-analysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformujte `splitTestSet` data přidáním následujícího kódu do `Evaluate()` :

    [!code-csharp[PredictWithTransformer](./snippets/sentiment-analysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Předchozí kód používá metodu [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) k vytvoření předpovědi pro více zadaných vstupních řádků testovací sady dat.

4. Vyhodnoťte model přidáním následujícího jako další řádek kódu v `Evaluate()` metodě:

    [!code-csharp[ComputeMetrics](./snippets/sentiment-analysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Jakmile máte nastavení předpovědi ( `predictions` ), metoda [Evaluate ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací datové sadě a vrátí objekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) , jak model provádí.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověřování modelu

K zobrazení metrik použijte následující kód:

[!code-csharp[DisplayMetrics](./snippets/sentiment-analysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- `Accuracy`Metrika získá přesnost modelu, což je poměr správných předpovědi v sadě testů.

- `AreaUnderRocCurve`Metrika označuje, jak jistotu model správně klasifikuje pozitivní a negativní třídy. Chcete, aby byl co `AreaUnderRocCurve` nejblíže k jednomu.

- `F1Score`Metrika získá skóre modelu F1, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).  Chcete, aby byl co `F1Score` nejblíže k jednomu.

### <a name="predict-the-test-data-outcome"></a>Předpověď výsledku testovacích dat

1. Vytvořte `UseModelWithSingleItem()` metodu hned za `Evaluate()` metodou pomocí následujícího kódu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()`Metoda provádí následující úlohy:

    - Vytvoří jeden komentář testovacích dat.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpovězené výsledky.

2. Přidejte volání do metody New z `Main()` metody přímo pod `Evaluate()` voláním metody pomocí následujícího kódu:

    [!code-csharp[CallUseModelWithSingleItem](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Přidejte následující kód, který chcete vytvořit jako první řádek v `UseModelWithSingleItem()` metodě:

    [!code-csharp[CreatePredictionEngine](./snippets/sentiment-analysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.

4. Přidejte komentář k otestování předpovědi vyškolených modelů v `UseModelWithSingleItem()` metodě vytvořením instance `SentimentData` :

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Předání dat testovacích komentářů do do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) přidejte následujícím způsobem jako další řádky kódu v `UseModelWithSingleItem()` metodě:

    [!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat.

6. Zobrazit `SentimentText` a odpovídající předpovědi mínění pomocí následujícího kódu:

    [!code-csharp[OutputPrediction](./snippets/sentiment-analysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Použití modelu předpovědi

### <a name="deploy-and-predict-batch-items"></a>Nasazení a předpověď položek Batch

1. Vytvořte `UseModelWithBatchItems()` metodu hned za `UseModelWithSingleItem()` metodou pomocí následujícího kódu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithBatchItems()`Metoda provádí následující úlohy:

    - Vytvoří data dávkového testu.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpovězené výsledky.

2. Přidejte volání do metody New z `Main` metody přímo pod `UseModelWithSingleItem()` voláním metody pomocí následujícího kódu:

    [!code-csharp[CallPredictModelBatchItems](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Přidejte některé komentáře, abyste otestovali předpovědi vyškolených modelů v `UseModelWithBatchItems()` metodě:

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Předpověď komentáře mínění

Pomocí modelu předpovědět data komentáře mínění pomocí metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Kombinování a zobrazení předpovědi

Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:

[!code-csharp[OutputHeaders](./snippets/sentiment-analysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Vzhledem k tomu `SentimentPrediction` , že je zděděn z `SentimentData` , `Transform()` Metoda naplněná `SentimentText` předpovězenými poli. Jako procesy procesu ML.NET jednotlivé komponenty přidávají sloupce a díky tomu je snadné zobrazit výsledky:

[!code-csharp[DisplayPredictions](./snippets/sentiment-analysis/csharp/Program.cs#DisplayResults "Display the predictions")]

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
