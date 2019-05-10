---
title: 'Kurz: Analýza webu komentáře – binární klasifikace'
description: V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z webu komentářů a provede příslušnou akci. Používá klasifikátor binární mínění C# v sadě Visual Studio 2017.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 1989a11a2f06ce4d713d6c3ecc70de0da606604e
ms.sourcegitcommit: 438824ff21f77c4301c6ba8a89a106114aa27bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/09/2019
ms.locfileid: "65462231"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Kurz: Analýza sentimentu komentářů k webu pomocí binární klasifikace ML.NET

V tomto kurzu se dozvíte, jak vytvořit konzolovou aplikaci .NET Core, která klasifikuje mínění z webu komentářů a provede příslušnou akci. Používá klasifikátor binární mínění C# v sadě Visual Studio 2017. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření konzolové aplikace
> * Příprava dat
> * Načtení dat
> * Vytvoření a trénování modelu
> * Vyhodnocení modelu
> * Použití modelu vytvoří předpověď
> * Zobrazit výsledky

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalovaná

* [Datová sada UCI subjektivního hodnocení s popiskem věty](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (soubor ZIP)

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Vytvoření **konzolovou aplikaci .NET Core** nazývá "SentimentAnalysis".

2. Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku a pak vyberte **Procházet** kartu. Vyhledejte **Microsoft.ML**, vyberte balíček a pak vyberte **nainstalovat** tlačítko. Pokračovat v instalaci souhlasí s licenční podmínky pro balíček, který si zvolíte. Totéž proveďte pro **Microsoft.ML.FastTree** balíček NuGet.

## <a name="prepare-your-data"></a>Příprava dat

> [!NOTE]
> Datové sady pro účely tohoto kurzu jsou ze "From skupiny na jednotlivé popisky pomocí podrobné funkce" Kotzias et. al,. Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017). UCI strojového učení úložiště [http://archive.ics.uci.edu/ml]. Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.

1. Stáhněte si [soubor ZIP datové sady UCI subjektivního hodnocení s popiskem věty](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.

2. Kopírovat `yelp_labelled.txt` soubor do *Data* adresáře, které jste vytvořili.

3. V Průzkumníku řešení klikněte pravým tlačítkem myši `yelp_labeled.txt` a vyberte možnost **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

1. Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. Vytvořte dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:

    * `_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
    * `_modelPath` obsahuje cestu k uložení naučeného modelu.

3. Přidejte následující kód na řádku vpravo nahoře `Main` metodu pro zadání cesty:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Dále vytvořte třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

    - V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

    - V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko.

    
5. *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *SentimentData.cs*:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Jak se připravit data
Třída vstupní datová sada `SentimentData`, má `string` pro komentáře uživatelů (`SentimentText`) a `bool` (`Sentiment`) hodnotu 1 (pozitivní) nebo 0 (negativní) mínění. Obě pole mají [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atributy připojené k nim, který popisuje soubor pořadí dat u každého pole.  Kromě toho `Sentiment` má vlastnost [Názevsloupce](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atribut nastavit jako `Label` pole. Následující příklad souboru nemá řádek záhlaví a vypadá takto:

|SentimentText                         |Mínění (popisek) |
|--------------------------------------|----------|
|Waitress pomalý trochu ve službě.|    0     |
|Povrch ovšem není vhodné.                    |    0     |
|WOW... Miluju toto místo.              |    1     |
|Služba se velmi výzvy.              |    1     |

`SentimentPrediction` je třída předpovědi používá po cvičení modelu. Dědí z `SentimentData` pro zobrazení `SentimentText` s předpovědí. `SentimentPrediction` má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut. `Label` Slouží k vytvoření a trénování modelu a jeho rozdělení na testovací datové použít také k vyhodnocení modelu. `PredictedLabel` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají trénovací data, předpovězeným hodnotám a model.

[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ML.NET. Inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně `DBContext` v Entity Framework.

## <a name="load-the-data"></a>Načtení dat
Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.ML.IDataView). `IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové). Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.

Příprava aplikace a pak načíst data:

1. Nahraďte `Console.WriteLine("Hello World!")` řádku v `Main` metodu, jak deklarovat a inicializovat proměnnou mlContext následujícím kódem:

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. Přidejte následující položky jako další řádek kódu `Main()` metody:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. Vytvořte `LoadData()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()` Metoda spustí následující úlohy:

    * Načte data.
    *  Rozdělí načíst datovou sadu na trénování a testování datových sad.
    * Vrátí hodnotu rozdělení trénují a testují datové sady.

4. Přidejte následující kód jako první řádek `LoadData()` metody:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru. Přijímá proměnné cesty dat a vrátí `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro trénování a testování modelu

Při přípravě na model, použijte část datové sady pro trénování a část datové sady, testování přesnosti modelu.  

1. Načtená data rozdělením potřebné datové sady, přidejte následující kód jako další řádek `LoadData()` metody:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Předchozí kód používá [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metodu rozdělit načíst datovou sadu na trénování a testování datových sad a vrátit je do [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) třídy. Zadejte procento dat pomocí nastavení testu `testFraction`parametru. Výchozí hodnota je 10 %, v tomto případě je použít 20 % k vyhodnocení další data.  

2. Vrátit `splitDataView` na konci `LoadData()` metody:

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Vytvoření a trénování modelu

1. Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main()` metody:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()` Metoda spustí následující úlohy:

    * Extrahuje a transformuje data.
    * Trénovat modelu.
    * Předpovídá subjektivního hodnocení na základě dat testu.
    * Vrátí hodnotu modelu.

2. Vytvořte `BuildAndTrainModel()` metoda, hned za `Main()` metodu, pomocí následujícího kódu:
    
    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Extrahovat a transformaci dat

1. Volání `FeaturizeText` jako další řádek kódu:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    `FeaturizeText()` Metoda v předchozím kódu převede textový sloupec (`SentimentText`) na číselný typ klíče `Features` sloupec používá algoritmu strojového učení a přidá ho jakou novou datovou sadu sloupce:

    |SentimentText                         |Mínění |Funkce              |
    |--------------------------------------|----------|----------------------|
    |Waitress pomalý trochu ve službě.|    0     |[0.76, 0.65, 0.44, …] |
    |Povrch ovšem není vhodné.                    |    0     |[0.98, 0.43, 0.54, …] |
    |WOW... Miluju toto místo.              |    1     |[0.35, 0.73, 0.46, …] |
    |Služba se velmi výzvy.              |    1     |[0.39, 0, 0.75, …]    |

### <a name="add-a-learning-algorithm"></a>Přidat algoritmu učení

Tato aplikace používá klasifikační algoritmus, který slouží ke kategorizaci položky nebo řádky s daty. Aplikace slouží ke kategorizaci komentáře webu jako kladné nebo záporné, takže pomocí binární klasifikace úlohy.

Přidat úlohy strojového učení do definice transformace dat přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()`:

    
[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

    
[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) je vaše klasifikace cvičení algoritmu. To se připojí `estimator` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Přizpůsobit modelu, který má `splitTrainSet` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda trénovat modelu transformace datové sady a aplikováním školení.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí že model se trénuje má použít pro hodnocení

 Model na konci vrátit `BuildAndTrainModel()` metody:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Poté, co váš model se trénuje, použijte test ověřit data výkonu modelu. 

1. Vytvořte `Evaluate()` metoda, hned za `BuildAndTrainModel()`, následujícím kódem:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()` Metoda spustí následující úlohy:

    * Načte datovou sadu testů.
    * Chyba při vyhodnocování BinaryClassification vytvoří.
    * Vyhodnotí modelu a vytvoří metriky.
    * Zobrazuje metriky.

2. Přidejte volání do nové metody z `Main()` metody, v rámci `BuildAndTrainModel()` volání metody, pomocí následujícího kódu:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformace `splitTestSet` data přidáním následujícího kódu do `Evaluate()`:

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Předchozí kód používá [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda k následné predikci pro více poskytuje vstupní řádky z datové sady testů.

4. Přidáním následujícího kódu jako další řádek kódu ve vyhodnocení modelu `Evaluate()` metody:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Jakmile budete mít do predikce. Nastavte (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` datovou sadu testů a vrátí [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) objektu, na jaký je výkon modelu.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Použijte následující kód k zobrazení metriky:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* `Accuracy` Metrika získá přesnost modelu, který je poměr správné predikce v testovací sadě.

* `AreaUnderRocCurve` Metrika vyjadřuje důvěru modelu je správně klasifikace třídy kladné a záporné. Chcete, aby `AreaUnderRocCurve` bude blízko jeden nejvíce.

* `F1Score` Metrika získá modelu F1 skóre, které je míra rovnováhu mezi [přesnost](../resources/glossary.md#precision) a [spojené s vracením](../resources/glossary.md#recall).  Chcete, aby `F1Score` bude blízko jeden nejvíce.

### <a name="predict-the-test-data-outcome"></a>Předpověď data výsledek testu

1. Vytvořte `UseModelWithSingleItem()` metoda, hned za `Evaluate()` metodu, pomocí následujícího kódu:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()` Metoda spustí následující úlohy:

    * Vytvoří jeden komentář testovací data.
    * Předpovídá subjektivního hodnocení na základě dat testu.
    * Kombinuje testovací data a předpovědi pro vytváření sestav.
    * Zobrazí predikované výsledky.

2. Přidejte volání do nové metody z `Main()` metody, v rámci `Evaluate()` volání metody, pomocí následujícího kódu:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Přidejte následující kód k vytvoření jako první řádek `Predict()` metody:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je vhodné rozhraní API, což vám umožní předat a pak proveďte predikcí na jednu instanci data.
  
4. Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict()` metodu tak, že vytvoříte instanci `SentimentData`:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Předání dat komentář test `Prediction Engine` přidáním následujícího kódu jako další řádky kódu ve `UseModelWithSingleItem()` metody:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) predikcí na jednom řádku dat díky funkce.

6. Zobrazení `SentimentText` a odpovídající předpovědí mínění pomocí následujícího kódu:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Použití modelu pro předpověď

### <a name="deploy-and-predict-batch-items"></a>Nasazení a předvídání položky služby batch

1. Vytvořte `UseModelWithBatchItems()` metoda, hned za `UseModelWithSingleItem()` metodu, pomocí následujícího kódu:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext)
    {

    }
    ```

    `UseModelWithBatchItems()` Metoda spustí následující úlohy:

    * Vytvoří služby batch testovací data.
    * Předpovídá subjektivního hodnocení na základě dat testu.
    * Kombinuje testovací data a předpovědi pro vytváření sestav.
    * Zobrazí predikované výsledky.

2. Přidejte volání do nové metody z `Main` metody, v rámci `UseModelWithSingleItem()` volání metody, pomocí následujícího kódu:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `UseModelWithBatchItems()` metody:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Předpověď mínění komentář

Použít model k predikci komentář data subjektivního hodnocení s využitím [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Spojit a zobrazit předpovědi

Vytvořte hlavičku pro předpovědi pomocí následujícího kódu:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Protože `SentimentPrediction` je zděděno od `SentimentData`, `Transform()` metoda vyplní `SentimentText` s předpokládanou pole. Procesu ML.NET zpracovává, jednotlivé komponenty přidá sloupce, a to usnadňuje zobrazení výsledků:

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto. Během zpracování zprávy se zobrazují. Může se zobrazit upozornění nebo zpracování zpráv. Ty se odebraly z následujících výsledků pro přehlednost.

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

Blahopřejeme! Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění.

Vytváření modelů po úspěšné je iterativní proces. Tento model má nižší počáteční kvalita jako kurz používá malé datové sady poskytují rychlý model školení. Pokud si nejste spokojeni s kvalitou modelu, můžete zkusit ho vylepšit tím, že poskytuje větší cvičných datových sad nebo výběrem jiné trénování algoritmů s různými [hyperparametry](../resources/glossary.md##hyperparameter) pro jednotlivé algoritmy.

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Vytvoření konzolové aplikace
> * Příprava dat
> * Načtení dat
> * Vytvoření a trénování modelu
> * Vyhodnocení modelu
> * Použití modelu vytvoří předpověď
> * Zobrazit výsledky

Přejděte k dalšímu kurzu, kde Další informace
> [!div class="nextstepaction"]
> [Klasifikace problému](github-issue-classification.md)
