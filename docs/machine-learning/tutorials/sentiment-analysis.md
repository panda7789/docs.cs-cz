---
title: 'Kurz: Analýza komentářů na webových stránkách - binární klasifikace'
description: Tento kurz ukazuje, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů na webu a provede příslušnou akci. Binární třídění mínění používá C# v sadě Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6e13cfca93c54648b1a0423c5983013d3e2a1a0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243294"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Kurz: Analýza mínění komentářů na webových stránkách s binární klasifikací v ML.NET

Tento kurz ukazuje, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z komentářů na webu a provede příslušnou akci. Binární třídění mínění používá C# v sadě Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvoření konzolové aplikace
> - Příprava dat
> - Načtení dat
> - Sestavení a trénování modelu
> - Vyhodnocení modelu
> - Pomocí modelu proveďte předpověď
> - Zobrazení výsledků

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2017 verze 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou pro vývoj napříč platformami ".NET Core"

- [Datová sada vět mínění UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvořte **aplikaci .NET Core Console** s názvem "SentimentAnalysis".

2. Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.

3. Nainstalujte **balíček nuget Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org" a pak vyberte kartu **Procházet.** **Vyhledejte Microsoft.ML**, vyberte požadovaný balíček a pak vyberte tlačítko **Instalovat.** Pokračujte v instalaci souhlasem s licenčními podmínkami pro vámi zvolené balíček. Proveďte totéž pro balíček **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-your-data"></a>Příprava dat

> [!NOTE]
> Datové sady pro tento kurz jsou ze skupiny na jednotlivé popisky pomocí deep funkce, Kotzias et. Al. KDD 2015 a hostované v Úložišti strojového učení UCI - Dua, D. a Karra Taniskidou, E. (2017). Úložiště strojového učeníhttp://archive.ics.uci.edu/mlUCI [ ]. Irvine, KALIFORNIE: Kalifornská univerzita, Škola informací a informatiky.

1. Stáhnout [UCI Sentiment označené věty soubor ZIP](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)soubor zip a rozbalit.

2. Zkopírujte `yelp_labelled.txt` soubor do *datového adresáře,* který jste vytvořili.

3. V Průzkumníku řešení klepněte pravým tlačítkem `yelp_labeled.txt` myši na soubor a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

1. Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Přidejte následující kód na řádek `Main` přímo nad metodou, chcete-li vytvořit pole pro uložení nedávno stažené cesty souboru datové sady:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Dále vytvořte třídy pro vstupní data a předpovědi. Přidání nové třídy do projektu:

    - V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.

    - V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *SentimentData.cs*. Potom vyberte tlačítko **Přidat.**

1. Soubor *SentimentData.cs* se otevře v editoru kódu. Na začátek `using` *SentimentData.cs*přidejte následující příkaz :

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, do *souboru SentimentData.cs:*

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Jak byla data připravena

Vstupní třída datové `SentimentData`sady , `string` má pro`SentimentText`komentáře `bool` uživatele`Sentiment`( ) a ( ) hodnotu buď 1 (kladné) nebo 0 (negativní) pro mínění. K oběma polím jsou připojeny atributy [LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) které popisují pořadí datových souborů každého pole.  Kromě toho `Sentiment` vlastnost má [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atribut k `Label` označení jako pole. Následující ukázkový soubor nemá řádek záhlaví a vypadá takto:

|SentimentText                         |Mínění (popisek) |
|--------------------------------------|----------|
|Servírka byla trochu pomalá ve službě.|    0     |
|Kůrka není dobrá.                    |    0     |
|Wow... Miloval toto místo.              |    1     |
|Služba byla velmi rychlá.              |    1     |

`SentimentPrediction`je třída předpověď použitá po trénování modelu. Dědí z `SentimentData` tak, `SentimentText` aby vstup lze zobrazit spolu s předpovědí výstupu. Logická `Prediction` hodnota je hodnota, kterou model předpovídá `SentimentText`při dodání s novým vstupem .

Výstupní třída `SentimentPrediction` obsahuje dvě další vlastnosti `Score` vypočítané podle modelu: - `Probability` nezpracované skóre vypočítané modelem a - skóre kalibrované podle pravděpodobnosti, že text bude mít kladný názor.

Pro tento kurz je `Prediction`nejdůležitější vlastností .

## <a name="load-the-data"></a>Načtení dat

Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových). Data lze načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu. `IDataView`

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET. Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

Připravíte aplikaci a pak načtete data:

1. Nahraďte `Console.WriteLine("Hello World!")` řádek `Main` v metodě následujícím kódem pro deklarování a inicializaci proměnné mlContext:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Jako další řádek kódu v metodě přidejte `Main()` následující:

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Vytvořte `LoadData()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Metoda `LoadData()` provádí následující úkoly:

    - Načte data.
    - Rozdělí načtenou datovou sadu na datové sady train a test.
    - Vrátí rozdělený vlak a testovací datové sady.

4. Jako první řádek `LoadData()` metody přidejte následující kód:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    Metoda [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru. Přebírá proměnné cesty dat a vrátí `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro trénování a testování modelu

Při přípravě modelu použijete část datové sady k jeho trénování a část datové sady k testování přesnosti modelu.

1. Chcete-li načtená data rozdělit do potřebných datových sad, `LoadData()` přidejte následující kód jako další řádek metody:

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Předchozí kód používá [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metoda rozdělit načtené datové sady do datových <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> sad train a test a vrátit je ve třídě. Zadejte procento dat testovací `testFraction`sady s parametrem. Výchozí hodnota je 10 %, v tomto případě použijete 20 % k vyhodnocení více dat.

2. Vraťte `splitDataView` na konci `LoadData()` metody:

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Sestavení a trénování modelu

1. Přidejte následující volání `BuildAndTrainModel`metody jako další řádek `Main()` kódu v metodě:

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Metoda `BuildAndTrainModel()` provádí následující úkoly:

    - Extrahuje a transformuje data.
    - Trénuje model.
    - Předpovídá mínění na základě testovacích dat.
    - Vrátí model.

2. Vytvořte `BuildAndTrainModel()` metodu, `Main()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Extrahování a transformace dat

1. Volání `FeaturizeText` jako další řádek kódu:

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Metoda `FeaturizeText()` v předchozím kódu převede textový`SentimentText`sloupec ( ) `Features` na sloupec číselného typu klíče, který používá algoritmus strojového učení, a přidá jej jako nový sloupec datové sady:

    |SentimentText                         |Mínění |Funkce              |
    |--------------------------------------|----------|----------------------|
    |Servírka byla trochu pomalá ve službě.|    0     |[0.76, 0.65, 0.44, ...] |
    |Kůrka není dobrá.                    |    0     |[0.98, 0.43, 0.54, ...] |
    |Wow... Miloval toto místo.              |    1     |[0.35, 0.73, 0.46, ...] |
    |Služba byla velmi rychlá.              |    1     |[0.39, 0, 0.75, ...]    |

### <a name="add-a-learning-algorithm"></a>Přidání algoritmu učení

Tato aplikace používá klasifikační algoritmus, který kategorizuje položky nebo řádky dat. Aplikace kategorizuje komentáře webu jako kladné nebo záporné, proto použijte úlohu binární klasifikace.

Přidejte úlohu strojového učení k definicím transformace dat přidáním `BuildAndTrainModel()`následujícího jako následující řádek kódu v aplikaci :

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je váš algoritmus školení klasifikace. To je připojen `estimator` k a přijímá featurized `SentimentText` ( `Label` `Features`) a vstupní parametry učit se z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Připevněte model `splitTrainSet` k datům a vraťte trénovaný model `BuildAndTrainModel()` přidáním následujícího jako následující řádek kódu v metodě:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

[Metoda Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trénuje váš model transformací datové sady a použitím školení.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátit model vyškolený k použití pro hodnocení

 Vraťte model na konci `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Po tréninek modelu použijte testovací data ověřit výkon modelu.

1. Vytvořte `Evaluate()` metodu, `BuildAndTrainModel()`těsně po , s následujícím kódem:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Metoda `Evaluate()` provádí následující úkoly:

    - Načte testovací datovou sadu.
    - Vytvoří hodnotitel binární klasifikace.
    - Vyhodnotí model a vytvoří metriky.
    - Zobrazí metriky.

2. Přidejte volání nové metody `Main()` z metody, `BuildAndTrainModel()` přímo pod volání metody, pomocí následujícího kódu:

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformace `splitTestSet` dat přidáním následujícího `Evaluate()`kódu do aplikace :

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda, aby předpovědi pro více zapředpokladu vstupní řádky testovací datové sady.

4. Vyhodnoťte model přidáním následujícího `Evaluate()` jako následující řádek kódu v metodě:

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Jakmile máte předpověď set`predictions`( ), [Assess()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda vyhodnotí model, který porovná `Labels` předpovídané hodnoty s aktuální v testovací datové sady a vrátí [KalibrdBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objekt o tom, jak model funguje.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

K zobrazení metrik použijte následující kód:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- Metrika `Accuracy` získá přesnost modelu, což je podíl správné předpovědi v testovací sadě.

- Metrika `AreaUnderRocCurve` označuje, jak jistý model je správně klasifikovat kladné a záporné třídy. Chcete, `AreaUnderRocCurve` aby byl co nejblíže k jednomu, jak je to možné.

- Metrika `F1Score` získá skóre F1 modelu, což je míra rovnováhy mezi [přesností](../resources/glossary.md#precision) a [odvoláním](../resources/glossary.md#recall).  Chcete, `F1Score` aby byl co nejblíže k jednomu, jak je to možné.

### <a name="predict-the-test-data-outcome"></a>Předpovědět výsledek testovacích dat

1. Vytvořte `UseModelWithSingleItem()` metodu, `Evaluate()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithSingleItem()` provádí následující úkoly:

    - Vytvoří jeden komentář testovacích dat.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpokládané výsledky.

2. Přidejte volání nové metody `Main()` z metody, `Evaluate()` přímo pod volání metody, pomocí následujícího kódu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Přidejte následující kód, který chcete `UseModelWithSingleItem()` vytvořit jako první řádek metody:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

    > [!NOTE]
    > `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

4. Přidejte komentář k testování predikce `UseModelWithSingleItem()` trénovaného modelu `SentimentData`v metodě vytvořením instance :

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Předat data testovacíkomentář [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do následující ho přidáním následující jako `UseModelWithSingleItem()` další řádky kódu v metodě:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jeden řádek dat.

6. Zobrazení `SentimentText` a odpovídající předpověď mínění pomocí následujícího kódu:

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Použití modelu pro předpověď

### <a name="deploy-and-predict-batch-items"></a>Nasazení a předvídání dávkových položek

1. Vytvořte `UseModelWithBatchItems()` metodu, `UseModelWithSingleItem()` hned za metodou, pomocí následujícího kódu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Metoda `UseModelWithBatchItems()` provádí následující úkoly:

    - Vytvoří data dávkového testu.
    - Předpovídá mínění na základě testovacích dat.
    - Kombinuje testovací data a předpovědi pro vytváření sestav.
    - Zobrazí předpokládané výsledky.

2. Přidejte volání nové metody `Main` z metody, `UseModelWithSingleItem()` přímo pod volání metody, pomocí následujícího kódu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Přidejte některé komentáře k testování předpovědi `UseModelWithBatchItems()` trénovaného modelu v metodě:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Předpovídat mínění komentářů

Model slouží k předvídání mínění dat komentáře pomocí metody [Transform():](xref:Microsoft.ML.ITransformer.Transform%2A)

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Zkombinujte a zobrazte předpovědi

Vytvořte záhlaví pro předpovědi pomocí následujícího kódu:

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Protože `SentimentPrediction` je zděděna z `SentimentData`, `Transform()` metoda naplněná `SentimentText` předpovídanými poli. Při procesu procesu ML.NET každá komponenta přidává sloupce, což usnadňuje zobrazení výsledků:

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Výsledky

Vaše výsledky by měly být podobné následujícímu. Během zpracování se zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Ty byly odstraněny z následujících výsledků pro přehlednost.

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

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předvídání mínění zpráv.

Vytváření úspěšných modelů je iterativní proces. Tento model má počáteční nižší kvalitu jako kurz používá malé datové sady poskytovat rychlé školení modelu. Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit vylepšit tím, že poskytuje větší trénovací datové sady nebo výběrem různých trénovacích algoritmů s různými hyperparametry pro každý [algoritmus.](../resources/glossary.md#hyperparameter)

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvoření konzolové aplikace
> - Příprava dat
> - Načtení dat
> - Sestavení a trénování modelu
> - Vyhodnocení modelu
> - Pomocí modelu proveďte předpověď
> - Zobrazení výsledků

Přejdete k dalšímu kurzu, abyste se dozvěděli více
> [!div class="nextstepaction"]
> [Klasifikace problémů](github-issue-classification.md)
