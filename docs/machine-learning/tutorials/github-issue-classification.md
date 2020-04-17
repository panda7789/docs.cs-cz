---
title: 'Kurz: Kategorizace problémů s podporou – klasifikace více tříd'
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace více tříd ke klasifikaci githubu a přiřadit je k dané oblasti.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fc0e935a36c52627903dac2a7b29d6f534695ea0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608059"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Kurz: Kategorizovat problémy s podporou pomocí klasifikace více tříd s ML.NET

Tento ukázkový kurz ilustruje použití ML.NET k vytvoření klasifikátoru problémů GitHub utrénovat model, který klasifikuje a předpovídá popisek Area pro problém GitHub prostřednictvím aplikace konzoly .NET Core pomocí Jazyka C# v sadě Visual Studio.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Předvídejte pomocí trénovaného modelu
> * Nasazení a předvídání s načteným modelem

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".
* [Github problémy kartu oddělený soubor (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Github vydává soubor oddělený testovací kartou (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete sadu Visual Studio 2017. Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.** V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core.** Pak vyberte šablonu projektu **Konzola Aplikace (.NET Core).** Do textového pole **Název** zadejte "GitHubIssueClassification" a pak vyberte tlačítko **OK.**

2. Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat:

    V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte enter.

3. Vytvořte adresář s názvem *Modely* v projektu pro uložení modelu:

    V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Zadejte "Modely" a stiskněte enter.

4. Nainstalujte **balíček nuget Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu Procházet, vyhledejte **Microsoft.ML** a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si datové sady [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) a uložte je do dříve vytvořené složky *Data.* První datová sada trénuje model strojového učení a druhá slouží k vyhodnocení, jak přesný je váš model.

2. V Průzkumníku řešení klepněte \*pravým tlačítkem myši na jednotlivé soubory tsv a vyberte příkaz **Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definování cest

Do horní `using` části *Program.cs* souboru přidejte následující další příkazy:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

Vytvořte tři globální pole pro uložení cest k nedávno staženým `MLContext`souborům a globálních proměnných pro ,`DataView`a `PredictionEngine`:

* `_trainDataPath`má cestu k datové sadě použité k trénování modelu.
* `_testDataPath`má cestu k datové sadě použité k vyhodnocení modelu.
* `_modelPath`má cestu, kde je trénovaný model uložen.
* `_mlContext`<xref:Microsoft.ML.MLContext> je, který poskytuje kontext zpracování.
* `_trainingDataView`<xref:Microsoft.ML.IDataView> slouží ke zpracování trénovací datové sady.
* `_predEngine`je <xref:Microsoft.ML.PredictionEngine%602> používá pro jednotlivé předpovědi.

Přidejte následující kód na řádek `Main` přímo nad metodou, abyste určili tyto cesty a další proměnné:

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

Vytvořte některé třídy pro vaše vstupní data a předpovědi. Přidání nové třídy do projektu:

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a potom vyberte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Třídu** a změňte pole **Název** na *GitHubIssueData.cs*. Potom vyberte tlačítko **Přidat.**

    V editoru kódu se otevře *soubor GitHubIssueData.cs.* Na začátek `using` *GitHubIssueData.cs*přidejte následující příkaz :

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

Odeberte existující definici třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, do souboru *GitHubIssueData.cs:*

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

Je `label` sloupec, který chcete předpovědět. Identifikované `Features` jsou vstupy, které dáte modelu předpovědět Label.

Pomocí [atributu LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) určete indexy zdrojových sloupců v datové sadě.

`GitHubIssue`je vstupní třída datové sady <xref:System.String> a má následující pole:

* první sloupec `ID` (ID problému GitHub)
* druhý sloupec `Area` (předpověď pro trénink)
* třetí sloupec `Title` (název problému GitHub) `feature` je první použitý pro předvídání`Area`
* čtvrtý sloupec `Description` je `feature` druhý, který se používá pro předvídání`Area`

`IssuePrediction`je třída použitá pro předpověď po trénovaném modelu. Má jeden `string` (`Area`) `PredictedLabel` `ColumnName` a atribut.  Používá `PredictedLabel` se při predikci a vyhodnocení. Pro vyhodnocení se používá vstup s trénovacími daty, předpovídanými hodnotami a modelem.

Všechny operace ML.NET spustit ve třídě [MLContext.](xref:Microsoft.ML.MLContext) Inicializace `mlContext` vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, do `DBContext` . `Entity Framework`

### <a name="initialize-variables-in-main"></a>Inicializovat proměnné v hlavní

Inicializovat `_mlContext` globální proměnnou s `MLContext` novou instancí`seed: 0`s náhodným osivem ( ) pro opakovatelné/deterministické výsledky napříč více tréninky.  Nahraďte `Console.WriteLine("Hello World!")` řádek následujícím kódem v metodě: `Main`

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Načtení dat

ML.NET používá [třídu IDataView](xref:Microsoft.ML.IDataView) jako flexibilní a efektivní způsob popisu číselných nebo textových tabulkových dat. `IDataView`můžete načíst textové soubory nebo v reálném čase (například SQL database nebo log files).

Chcete-li inicializovat a načíst `_trainingDataView` globální proměnnou, abyste ji `mlContext` mohli použít pro kanál, přidejte po inicializaci následující kód:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru. Přebírá proměnné cesty dat a vrátí `IDataView`.

Jako další řádek kódu v metodě přidejte `Main` následující:

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

Metoda `ProcessData` provádí následující úkoly:

* Extrahuje a transformuje data.
* Vrátí kanál zpracování.

Vytvořte `ProcessData` metodu, `Main` hned za metodou, pomocí následujícího kódu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Extrahování prvků a transformace dat

Chcete-li předpovědět popisek Area GitHub `GitHubIssue`pro , použijte metodu [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) k transformaci `Area` sloupce do sloupce číselného typu `Label` klíče (formát přijatý klasifikačními algoritmy) a přidejte jej jako nový sloupec datové sady:

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

Dále volání, `mlContext.Transforms.Text.FeaturizeText` které transformuje text (`Title` a `Description`) `TitleFeaturized` sloupce `DescriptionFeaturized`do číselného vektoru pro každý volal a . Připojit featurization pro oba sloupce do kanálu s následujícím kódem:

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

Poslední krok v přípravě dat kombinuje všechny sloupce funkce do sloupce **Funkce** pomocí metody [Concatenate().](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) Ve výchozím nastavení algoritmus učení zpracovává pouze funkce ze sloupce **Funkce.** Připojit tuto transformaci do kanálu s následujícím kódem:

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 Dále připojit <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do mezipaměti DataView, takže při iterát přes data vícekrát pomocí mezipaměti může získat lepší výkon, jako s následujícím kódem:

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Použijte AppendCacheCheckpoint pro malé a střední datové sady snížit dobu trénování. Nepoužívejte jej (odstraňte . AppendCacheCheckpoint()) při zpracování velmi velké datové sady.

Vrátit potrubí na konci `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

Tento krok zpracovává předběžné zpracování/featurization. Použití dalších součástí dostupných v ML.NET může umožnit lepší výsledky s modelem.

## <a name="build-and-train-the-model"></a>Sestavení a trénování modelu

Přidejte následující volání `BuildAndTrainModel`metody jako další řádek `Main` kódu v metodě:

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

Metoda `BuildAndTrainModel` provádí následující úkoly:

* Vytvoří třídu trénovacího algoritmu.
* Trénuje model.
* Předpovídá oblast na základě trénovacích dat.
* Vrátí model.

Vytvořte `BuildAndTrainModel` metodu, `Main` hned za metodou, pomocí následujícího kódu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>O úkolu klasifikace

Klasifikace je úloha strojového učení, která používá data k **určení** kategorie, typu nebo třídy položky nebo řádku dat a je často jedním z následujících typů:

* Binární: buď A nebo B.
* Vícetřídy: více kategorií, které lze předpovědět pomocí jednoho modelu.

Pro tento typ problému použijte algoritmus učení klasifikace více tříd, protože předpověď kategorie problému může být jedna z více kategorií (více tříd) spíše než pouze dvě (binární).

Přidejte algoritmus strojového učení k definicím transformace dat přidáním `BuildAndTrainModel()`následujícího jako první řádek kódu v aplikaci :

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) je váš vícetřídní algoritmus klasifikace školení. To je připojen `pipeline` k a přijímá `Title` featurized a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.

### <a name="train-the-model"></a>Trénování modelu

Připevněte model `splitTrainSet` k datům a vraťte trénovaný model `BuildAndTrainModel()` přidáním následujícího jako následující řádek kódu v metodě:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

Metoda `Fit()`trénuje váš model transformací datové sady a použitím školení.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje předat a potom provést předpověď na jednu instanci dat. Přidejte to jako další `BuildAndTrainModel()` řádek v metodě:

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Předvídejte pomocí trénovaného modelu

Přidejte problém GitHub k testování predikce `Predict` trénovaného `GitHubIssue`modelu v metodě vytvořením instance :

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

Použití [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce provede předpověď na jeden řádek dat:

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Použití modelu: predikce výsledků

Zobrazit `GitHubIssue` a `Area` odpovídající popisek predikce s cílem sdílet výsledky a jednat podle nich odpovídajícím způsobem.  Vytvořte zobrazení výsledků pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> následujícího kódu:

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátit model vyškolený k použití pro hodnocení

Vrátit model na konci `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když jste vytvořili a trénovali model, musíte ho vyhodnotit pomocí jiné datové sady pro zajištění kvality a ověření. V `Evaluate` metodě je model `BuildAndTrainModel` vytvořený v aplikaci předán k vyhodnocení. Vytvořte `Evaluate` metodu, `BuildAndTrainModel`těsně po , jako v následujícím kódu:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

Metoda `Evaluate` provádí následující úkoly:

* Načte testovací datovou sadu.
* Vytvoří vícetřídní vyhodnocení.
* Vyhodnotí model a vytvoří metriky.
* Zobrazí metriky.

Přidejte volání nové metody `Main` z metody, `BuildAndTrainModel` přímo pod volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

Stejně jako dříve s trénovací datovou sadou načtěte testovací datovou sadu přidáním následujícího kódu k metodě: `Evaluate`

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

[Metoda Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) vypočítá metriky kvality pro model pomocí zadané datové sady. Vrátí <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> objekt, který obsahuje celkové metriky vypočítané vyhodnocením klasifikace více tříd.
Chcete-li zobrazit metriky k určení kvality modelu, musíte je nejprve získat.
Všimněte si použití [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda `_trainedModel` globální proměnné strojového učení [(ITransformer)](xref:Microsoft.ML.ITransformer)pro zadání funkcí a vrátí předpovědi. Jako další řádek `Evaluate` přidejte do metody následující kód:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

Následující metriky jsou vyhodnocovány pro klasifikaci více tříd:

* Mikropřesnost - Každý pár třídy vzorků přispívá stejnou měrou k metrike přesnosti.  Chcete, aby mikro přesnost byla co nejblíže k jednomu.

* Přesnost maker – každá třída přispívá stejnou měrou k metrike přesnosti. Menšinové třídy mají stejnou váhu jako větší třídy. Chcete, aby přesnost maker byla co nejblíže jedné.

* Log-loss - viz [Ztráta protokolu](../resources/glossary.md#log-loss). Chcete, aby ztráta protokolu byla co nejblíže nule.

* Snížení ztráty protokolu - rozsahy od [-inf, 1.00], kde 1.00 je perfektní předpovědi a 0 označuje střední předpovědi. Chcete, aby snížení ztráty protokolu bylo co nejblíže k jednomu.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Pomocí následujícího kódu můžete zobrazit metriky, sdílet výsledky a pak s nimi jednat:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Uložení modelu do souboru

Po splnění modelu jej uložte do souboru a vytvořte předpovědi později nebo v jiné aplikaci. Do metody `Evaluate` přidejte následující kód.

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

Vytvořte `SaveModelAsFile` metodu `Evaluate` pod metodou.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Přidejte do `SaveModelAsFile` metody následující kód. Tento kód [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) používá metodu serializovat a uložit trénovaný model jako soubor zip.

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Nasazení a předvídání pomocí modelu

Přidejte volání nové metody `Main` z metody, `Evaluate` přímo pod volání metody, pomocí následujícího kódu:

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

Vytvořte `PredictIssue` metodu, `Evaluate` těsně po metodě `SaveModelAsFile` (a těsně před metodou), pomocí následujícího kódu:

```csharp
private static void PredictIssue()
{

}
```

Metoda `PredictIssue` provádí následující úkoly:

* Načte uložený model
* Vytvoří jeden problém testovacích dat.
* Předpovídá oblast na základě testovacích dat.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí předpokládané výsledky.

Načtěte uložený model do aplikace přidáním následujícího kódu k metodě: `PredictIssue`

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

Přidejte problém GitHub k testování predikce `Predict` trénovaného `GitHubIssue`modelu v metodě vytvořením instance :

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

Stejně jako dříve `PredictionEngine` vytvořte instanci s následujícím kódem:

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

Použijte `PredictionEngine` k předvídání popisek Oblasti GitHub `PredictIssue` přidáním následujícího kódu k metodě pro předpověď:

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Použití načteného modelu pro předpověď

Zobrazit, `Area` aby bylo možné problém kategorizovat a podle toho jednat. Vytvořte zobrazení výsledků pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> následujícího kódu:

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Výsledky

Vaše výsledky by měly být podobné následujícímu. Jako procesy kanálu se zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Tyto zprávy byly odebrány z následujících výsledků pro přehlednost.

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

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a předvídání popisek oblasti pro problém GitHub. Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Předvídejte pomocí trénovaného modelu
> * Nasazení a předvídání s načteným modelem

Přejdete k dalšímu kurzu, abyste se dozvěděli více
> [!div class="nextstepaction"]
> [Prediktor jízdného taxi](predict-prices.md)
