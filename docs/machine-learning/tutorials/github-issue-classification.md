---
title: 'Kurz: zařazení do kategorií – problémy s podporou – klasifikace s více třídami'
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace s více třídami ke klasifikaci problémů GitHubu, aby je bylo možné přiřadit k dané oblasti.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: d4ab7f0fcc6b582e74f54d3f0e60032696277249
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051542"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Kurz: kategorizace problémů podpory pomocí klasifikace s více třídami s ML.NET

Tento vzorový kurz ilustruje použití ML.NET k vytvoření klasifikátoru problémů GitHubu pro výuku modelu, který klasifikuje a odhadne popisek oblasti pro problém na GitHubu prostřednictvím konzolové aplikace .NET Core využívající C# v aplikaci Visual Studio.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Předpověď s vycvičeným modelem
> * Nasazení a předpověď pomocí načteného modelu

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .

## <a name="prerequisites"></a>Požadavky

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.
* [Soubor s oddělovači (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv)se zastavuje na kartě GitHubu.
* [Soubor s oddělovači (issues_test. TSV) problému GitHubu](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete sadu Visual Studio 2017. Z řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt** . V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core** . Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** . Do textového pole **název** zadejte "GitHubIssueClassification" a pak vyberte tlačítko **OK** .

2. Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady:

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **novou složku**. Zadejte "data" a stiskněte ENTER.

3. Vytvořte v projektu adresář s názvem *Models* a uložte svůj model:

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **novou složku**. Zadejte "modely" a stiskněte ENTER.

4. Nainstalujte **balíček NuGet Microsoft.ml**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ml** a vyberte tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte sady dat [issues_train. TSV](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test. TSV](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) a uložte je do složky *data* , která byla dříve vytvořena. První datová sada Vlaks model strojového učení a druhá se dá použít k vyhodnocení toho, jak přesný je váš model.

2. V Průzkumník řešení klikněte pravým tlačítkem na každý ze \* souborů. TSV a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

`using`Do horní části souboru *program.cs* přidejte následující dodatečné příkazy:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

Vytvořte tři globální pole pro uchování cest ke nedávno staženým souborům a globální proměnné pro `MLContext` , `DataView` a `PredictionEngine` :

* `_trainDataPath`má cestu k datové sadě, která se používá ke výukě modelu.
* `_testDataPath`má cestu k datové sadě, která se používá k vyhodnocení modelu.
* `_modelPath`má cestu, kde je uložený model trained.
* `_mlContext`je rozhraní <xref:Microsoft.ML.MLContext> , které poskytuje kontext zpracování.
* `_trainingDataView`<xref:Microsoft.ML.IDataView>slouží ke zpracování datové sady školení.
* `_predEngine`je <xref:Microsoft.ML.PredictionEngine%602> použit pro jeden předpovědi.

Přidejte následující kód na řádek přímo nad `Main` metodu pro určení těchto cest a dalších proměnných:

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

Vytvořte některé třídy pro vstupní data a předpovědi. Přidejte do projektu novou třídu:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **třída** a změňte pole **název** na *GitHubIssueData.cs*. Pak vyberte tlačítko **Přidat** .

    V editoru kódu se otevře soubor *GitHubIssueData.cs* . `using`Do horní části *GitHubIssueData.cs*přidejte následující příkaz:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction` , do souboru *GitHubIssueData.cs* :

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

`label`Je sloupec, který chcete předpovědět. Identifikované `Features` jsou vstupy, které modelu přiřadíte pro předpověď popisku.

Pomocí [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v sadě dat.

`GitHubIssue`je vstupní datovou třídou a má následující <xref:System.String> pole:

* první sloupec `ID` (ID problému GitHubu)
* druhý sloupec `Area` (předpověď pro školení)
* třetí sloupec `Title` (název problému GitHubu) je první, který se `feature` používá pro předpověď`Area`
* čtvrtý sloupec `Description` je druhým `feature` použitým pro předpověď`Area`

`IssuePrediction`je třída použitá pro předpověď po vyškolení modelu. Má jeden `string` ( `Area` ) a `PredictedLabel` `ColumnName` atribut.  `PredictedLabel`Je používán během předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupy s daty o školení, předpovězené hodnoty a model.

Všechny operace ML.NET začínají ve třídě [MLContext](xref:Microsoft.ML.MLContext) . Inicializace `mlContext` vytvoří nové prostředí ml.NET, které se dá sdílet v rámci objektů pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v `Entity Framework` .

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v Main

Inicializovat `_mlContext` globální proměnnou s novou instancí `MLContext` s náhodným osivem ( `seed: 0` ) pro opakované nebo deterministické výsledky v rámci více školení.  Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v `Main` metodě:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Načtení dat

ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisující číselná nebo textová tabulková data. `IDataView`může načíst buď textové soubory, nebo v reálném čase (například databáze SQL nebo soubory protokolu).

Chcete-li inicializovat a načíst `_trainingDataView` globální proměnnou, aby ji bylo možné použít pro kanál, přidejte po inicializaci následující kód `mlContext` :

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView` .

Přidejte následující jako další řádek kódu v `Main` metodě:

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

`ProcessData`Metoda provádí následující úlohy:

* Extrahuje a transformuje data.
* Vrátí kanál zpracování.

Vytvořte `ProcessData` metodu hned za `Main` metodou pomocí následujícího kódu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Extrakce funkcí a transformace dat

Vzhledem k tomu, že chcete předpovědět popisek GitHubu oblasti pro `GitHubIssue` , použijte metodu [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pro transformaci `Area` sloupce do sloupce typu numerický klíč `Label` (formát přijatý algoritmy klasifikace) a přidejte ho jako sloupec nové datové sady:

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

Dále zavolejte `mlContext.Transforms.Text.FeaturizeText` , které transformuje sloupce textu ( `Title` a `Description` ) na číselné vektory pro každý z nich `TitleFeaturized` a `DescriptionFeaturized` . Přidejte featurization pro oba sloupce do kanálu s následujícím kódem:

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

Poslední krok v přípravě dat kombinuje všechny sloupce funkcí do sloupce **funkce** pomocí metody [CONCATENATE ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) . Ve výchozím nastavení se pro vzdělávací algoritmus zpracovávají jenom funkce ze sloupce **funkce** . Přidejte tuto transformaci do kanálu s následujícím kódem:

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 V dalším kroku přidejte objekt, <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> aby se zobrazila mezipaměť, takže když provedete iteraci dat víckrát pomocí mezipaměti, může dorazit k vyššímu výkonu, jako u následujícího kódu:

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Použijte AppendCacheCheckpoint pro malé nebo střední datové sady k nižšímu času školení. Nepoužívejte ho (odebrat. AppendCacheCheckpoint ()) při zpracování velmi rozsáhlých datových sad.

Vrátí kanál na konci `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

Tento krok zpracovává předzpracování/featurization. Použití dalších součástí dostupných v ML.NET může mít za následek lepší výsledky v modelu.

## <a name="build-and-train-the-model"></a>Sestavování a výuka modelu

Do metody přidejte následující volání `BuildAndTrainModel` metody jako další řádek kódu v `Main` metodě:

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel`Metoda provádí následující úlohy:

* Vytvoří třídu školicího algoritmu.
* Navlakuje model.
* Odhadne oblast na základě školicích dat.
* Vrátí model.

Vytvořte `BuildAndTrainModel` metodu hned za `Main` metodou pomocí následujícího kódu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>O úloze klasifikace

Klasifikace je úloha strojového učení, která používá data k **určení** kategorie, typu nebo třídy položky nebo řádku dat a je často jedním z následujících typů:

* Binární: buď A nebo B.
* Více tříd: více kategorií, které mohou být předpovězeny pomocí jednoho modelu.

Pro tento typ problému použijte algoritmus učení s více třídami, protože předpověď kategorie problému může být jednou z více kategorií (více tříd), nikoli jenom dvou (binární).

Přidejte algoritmus Machine Learning do definice transformace dat tak, že do prvního řádku kódu přidáte následující `BuildAndTrainModel()` :

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je váš algoritmus školicích kurzů pro klasifikace více tříd. Tento údaj je připojen k `pipeline` a přijímá natrénuje `Title` a `Description` ( `Features` ) a `Label` vstupní parametry pro získání informací z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Přizpůsobte si model `splitTrainSet` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `BuildAndTrainModel()` metodě:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

`Fit()`Metoda navlakuje váš model transformací datové sady a použitím školení.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat a následně provést předpovědi pro jednu instanci dat. Přidejte toto jako další řádek v `BuildAndTrainModel()` metodě:

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Předpověď s vycvičeným modelem

Přidejte problém GitHubu pro otestování předpovědi vyškolených modelů v `Predict` metodě vytvořením instance `GitHubIssue` :

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

Použití funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden řádek dat:

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Použití modelu: předpověď výsledků

Zobrazit `GitHubIssue` a odpovídající `Area` předpověď popisku, aby bylo možné sdílet výsledky a odpovídajícím způsobem je zpracovat.  Pomocí následujícího kódu vytvořte zobrazení výsledků <xref:System.Console.WriteLine?displayProperty=nameWithType> :

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí vyškolený model, který se má použít pro vyhodnocení.

Vrátí model na konci `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když jste vytvořili a naučili model, je nutné ho vyhodnotit s jinou datovou sadou pro zajištění a ověření kvality. V `Evaluate` metodě je model vytvořen v nástroji `BuildAndTrainModel` předán k vyhodnocení. Vytvořte `Evaluate` metodu hned po `BuildAndTrainModel` , jako v následujícím kódu:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

`Evaluate`Metoda provádí následující úlohy:

* Načte testovací datovou sadu.
* Vytvoří filtr s více třídami.
* Vyhodnotí model a vytvoří metriky.
* Zobrazí metriky.

Přidejte volání do metody New z `Main` metody přímo pod `BuildAndTrainModel` voláním metody pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

Stejně jako v případě, že jste použili datovou sadu školení, načtěte testovací datovou sadu přidáním následujícího kódu do `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

Metoda [Evaluate ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) počítá metriky kvality pro model používající zadanou datovou sadu. Vrátí <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> objekt, který obsahuje celkové metriky vypočítané filtry klasifikace s více třídami.
Chcete-li zobrazit metriky pro určení kvality modelu, je nutné je nejprve získat.
Všimněte si použití metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) `_trainedModel` globální proměnné Machine Learning ( [ITransformer](xref:Microsoft.ML.ITransformer)) k zadání funkcí a vrácení předpovědi. Do metody přidejte následující kód `Evaluate` jako další řádek:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

Pro klasifikaci s více třídami jsou vyhodnocovány následující metriky:

* Mikropřesnost – každá dvojice vzorových tříd přispívá stejně jako metrika přesnosti.  Chcete, aby byla mikropřesnost co nejblíže k jednomu.

* Přesnost makra – každá třída přispívá stejně jako metrika přesnosti. Minoritní třídy mají stejnou váhu jako větší třídy. Chcete, aby byla přesnost makra co nejblíže k jednomu.

* Protokolová ztráta – viz [ztráta protokolu](../resources/glossary.md#log-loss). Chcete, aby byla ztráta protokolu co nejblíže k nule.

* Omezení ztrát v protokolu – rozsahy od [-INF, 1,00], kde 1,00 je perfektní předpovědi a 0 označuje střední hodnotu předpovědi. Je třeba co nejblíže omezit ztrátu protokolu.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověřování modelu

Použijte následující kód k zobrazení metrik, sdílení výsledků a pak jejich fungování:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Uložení modelu do souboru

Jakmile se model splní, uložte ho do souboru, aby se předpovědi později nebo v jiné aplikaci. Do metody `Evaluate` přidejte následující kód.

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

Vytvořte `SaveModelAsFile` metodu pod vaší `Evaluate` metodou.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Do metody přidejte následující kód `SaveModelAsFile` . Tento kód používá [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metodu k serializaci a uložení výukového modelu jako souboru ZIP.

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Nasazení a předpověď pomocí modelu

Přidejte volání do metody New z `Main` metody přímo pod `Evaluate` voláním metody pomocí následujícího kódu:

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

Vytvořte `PredictIssue` metodu hned za `Evaluate` metodou (a těsně před `SaveModelAsFile` metodou) pomocí následujícího kódu:

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue`Metoda provádí následující úlohy:

* Načte uložený model.
* Vytvoří jeden problém testovacích dat.
* Odhadne oblast na základě testovacích dat.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí předpovězené výsledky.

Načtěte uložený model do aplikace přidáním následujícího kódu do `PredictIssue` metody:

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

Přidejte problém GitHubu pro otestování předpovědi vyškolených modelů v `Predict` metodě vytvořením instance `GitHubIssue` :

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

Jak jste předtím pracovali, vytvořte `PredictionEngine` instanci s následujícím kódem:

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.

Použijte `PredictionEngine` pro předpověď popisku oblasti GitHub přidáním následujícího kódu do `PredictIssue` metody pro předpověď:

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Použití načteného modelu pro předpověď

Zobrazí se, aby `Area` se problém kategorizoval, a podle toho ho zařadí. Pomocí následujícího kódu vytvořte zobrazení výsledků <xref:System.Console.WriteLine?displayProperty=nameWithType> :

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Výsledky

Výsledky by měly vypadat podobně jako následující. V průběhu procesu kanálu se zobrazí zprávy. Můžou se zobrazovat upozornění nebo zpracovávat zprávy. Tyto zprávy byly pro přehlednost odebrány z následujících výsledků.

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

Gratulujeme! Teď jste úspěšně vytvořili model strojového učení pro klasifikaci a předpověď popisku oblasti pro problém GitHubu. Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) .

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Předpověď s vycvičeným modelem
> * Nasazení a předpověď pomocí načteného modelu

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.
> [!div class="nextstepaction"]
> [Předpovídání tarifů taxislužby](predict-prices.md)
