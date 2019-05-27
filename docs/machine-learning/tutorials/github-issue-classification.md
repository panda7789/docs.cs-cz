---
title: 'Kurz: Kategorizace problémy podpory – klasifikace víc tříd'
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy Githubu pro jejich přiřazení k dané oblasti.
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: da4f82c1b2c4ebdc8ccc8f307722c2719909cf56
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195576"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a>Kurz: Kategorizace problémů pomocí klasifikace víc tříd ML .NET

Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru problém Githubu pro trénování modelu, který klasifikuje a predikuje popisek oblasti pro problém na Githubu prostřednictvím aplikace konzoly .NET Core using C# v sadě Visual Studio.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Predikce v trénovaného modelu
> * Nasazení a predikce v načíst model

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

* [Githubu problémy s daty oddělenými tabulátory souboru (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Problémy Githubu testovací soubor oddělených tabulátory (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "GitHubIssueClassification" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Vytvořte adresář *modely* ve vašem projektu a uložit model:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Modely" a stiskněte Enter.

4. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte **v 1.0.0** balíčků v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka. První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.

2. V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Vytvořte tři globální pole pro uložení cest k naposledy stažené soubory a globálních proměnných pro `MLContext`,`DataView`, a `PredictionEngine`:

* `_trainDataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
* `_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k uložení naučeného modelu.
* `_mlContext` je <xref:Microsoft.ML.MLContext> , která poskytuje kontext zpracování.
* `_trainingDataView` je <xref:Microsoft.ML.IDataView> používají ke zpracování trénovací datové sady.
* `_predEngine` je <xref:Microsoft.ML.PredictionEngine%602> používá pro jeden předpovědi.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Vytvořte některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *GitHubIssueData.cs*. Vyberte **přidat** tlačítko.

    *GitHubIssueData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, možnosti *GitHubIssueData.cs* souboru:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`label` Je sloupec, který chcete předpovědět. Identifikovanou `Features` jsou vstupy, poskytují model k predikci popisek.

Použití [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) k určení indexů zdrojových sloupců v datové sadě.

`GitHubIssue` je třída vstupní datová sada a má následující <xref:System.String> pole:

* první sloupec `ID` (ID problému Githubu)
* druhý sloupec `Area` (Předpověď pro školení)
* třetí sloupec `Title` (název problému Githubu) je prvním `feature` používá pro predikci `Area`
* čtvrtý sloupec `Description` tím dokončím `feature` používá pro predikci `Area`

`IssuePrediction` Třída slouží k předpovědi po model se trénuje. Má jediný `string` (`Area`) a `PredictedLabel` `ColumnName` atribut.  `PredictedLabel` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.

Všechny operace ML.NET spustit v [MLContext](xref:Microsoft.ML.MLContext) třídy. Inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně `DBContext` v `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Inicializovat `_mlContext` globální proměnnou s novou instanci třídy `MLContext` s náhodná počáteční hodnota (`seed: 0`) pro opakovatelné/deterministické výsledky napříč více školení.  Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Načtení dat

Používá ML.NET [IDataView třídy](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob, jak popisují číselné nebo text tabulková data. `IDataView` můžete načíst buď textové soubory nebo v reálném čase (například SQL databázi nebo soubory protokolů).

K inicializaci a načíst `_trainingDataView` globální proměnné, aby bylo možné používat pro kanál, přidejte následující kód za `mlContext` inicializace:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru. Přijímá proměnné cesty dat a vrátí `IDataView`.

Přidejte následující položky jako další řádek kódu `Main` metody:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` Metoda spustí následující úlohy:

* Extrahuje a transformuje data.
* Vrátí kanálu zpracování.

Vytvořte `ProcessData` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Extrakce funkce a transformaci dat

Jak chcete předpovědět popisek oblasti Githubu `GitHubIssue`, použít [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody k transformaci `Area` sloupců na číselný typ klíče `Label` sloupec (formát přijal algoritmy klasifikace ) a přidejte ho jako nový sloupec datové sady:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` která transformuje text (`Title` a `Description`) sloupce jako číselné vektor pro každou volá `TitleFeaturized` a `DescriptionFeaturized`. Snadné pro oba sloupce pro přidání do kanálu s následujícím kódem:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody. Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce. Připojte tuto transformaci na kanál s následujícím kódem:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 V dalším kroku připojit <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pro ukládání do mezipaměti DataView, takže při iteraci přes data s využitím více než jednou mezipaměti může dosahovat vyšších výkonů, stejně jako u následujícího kódu:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Můžete snížit dobu výuky AppendCacheCheckpoint pro malé a střední datové sady. Nepoužívejte ho (odebrat. AppendCacheCheckpoint()) při zpracování velmi velkých datových sad.

Kanál na konci vrátit `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Tento krok zpracovává předběžného zpracování a snadné. Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.

## <a name="build-and-train-the-model"></a>Vytvoření a trénování modelu

Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Metoda spustí následující úlohy:

* Vytvoří třídu algoritmus školení.
* Trénovat modelu.
* Předpovídá oblasti založené na trénovací data.
* Vrátí hodnotu modelu.

Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>O úloze klasifikace

Klasifikace je úloha strojového učení, který používá data **určit** kategorie, typ nebo třída položky nebo řádek dat a je často jedním z následujících typů:

* Binární soubor: buď A a B.
* Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.

Pro tento typ problému používejte klasifikaci Multiclass učení algoritmu, protože predikci kategorii problému může být jeden z více kategorií (multiclass) místo jen dvou (binární).

Připojení algoritmu strojového učení do definice transformace dat přidáním následujícího kódu jako první řádek kódu v `BuildAndTrainModel()`:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je algoritmus školení klasifikace víc tříd. To se připojí `pipeline` a přijímá natrénuje `Title` a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Přizpůsobit modelu, který má `splitTrainSet` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

`Fit()`Metoda trénovat modelu transformace datové sady a aplikováním školení.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je vhodné rozhraní API, což vám umožní předat a pak proveďte predikcí na jednu instanci data. Přidat jako na následující řádek `BuildAndTrainModel()` metody:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Predikce v trénovaného modelu

Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Použití [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce díky predikcí na jednom řádku dat:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Pomocí modelu: předpověď výsledků

Zobrazení `GitHubIssue` a odpovídající `Area` popisek predikcí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.  Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí že model se trénuje má použít pro hodnocení

Model na konci vrátit `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování. V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení. Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

`Evaluate` Metoda spustí následující úlohy:

* Načte datovou sadu testů.
* Vytvoří víc tříd Chyba při vyhodnocování.
* Vyhodnotí modelu a vytvoření metriky.
* Zobrazuje metriky.

Přidejte volání do nové metody z `Main` metody, v rámci `BuildAndTrainModel` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Stejně jako dříve trénovací datové sady, načíst datovou sadu testů tak, že přidáte následující kód, který `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) metoda vypočítá metrik kvality pro model pomocí zadaného objektu dataset. Vrátí <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení klasifikace víc tříd.
Pokud chcete zobrazit metriky pro určení kvality tohoto modelu, musíte je získat první.
Použití Všimněte si, že [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda služby machine learning `_trainedModel` globální proměnné ( [ITransformer](xref:Microsoft.ML.ITransformer)) k zadání funkce a vrátí předpovědi. Přidejte následující kód, který `Evaluate` metody jako další řádek:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Klasifikace víc tříd, se vyhodnotí následující metriky:

* Micro přesnost – každá dvojice ukázkovou třídu přispívá stejně metriky přesnosti.  Chcete, aby Micro přesnost, aby byly co nejblíže 1 nejvíce.

* Přesnost – makro – každá třída přispívá stejně metriky přesnosti. Třídy minority disponují stejnou váhu jako větší třídy. Chcete, aby byly co nejblíže 1 nejvíce přesnost – makro.

* Protokol ztrát – naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss). Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.

* Od ztráty protokolu snížení - [-inf, 100], kde 100 je ideální předpovědi a 0 označuje střední předpovědi. Chcete, aby omezení ztráty protokolu bude co nejblíže nuly nejvíce.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a>Nasazení a predikce v modelu

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Vytvořit `PredictIssue` metoda, hned za `Evaluate` – metoda (a těsně před `SaveModelAsFile` metoda), pomocí následujícího kódu:

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` Metoda spustí následující úlohy:

* Vytvoří jen jeden problém testovací data.
* Předpovídá oblasti na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Stejně jako dříve, vytvořit `PredictionEngine` instance s následujícím kódem:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Použití `PredictionEngine` předpovědět popisek oblasti Githubu přidáním následujícího kódu `PredictIssue` metodu pro předpověď:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Použití načíst model pro předpověď

Zobrazení `Area` kategorizace problém a příslušně na ně reagovat na něj. Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto. Při zpracování kanálu zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Tyto zprávy se odebraly z následujících výsledků pro přehlednost.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Blahopřejeme! Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat popisek oblasti pro problém na Githubu. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Predikce v trénovaného modelu
> * Nasazení a predikce v načíst model

Přejděte k dalšímu kurzu, kde Další informace
> [!div class="nextstepaction"]
> [Prediktivní tarif taxislužby města](taxi-fare.md)
