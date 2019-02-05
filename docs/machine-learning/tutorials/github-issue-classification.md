---
title: V případě GitHub problém klasifikace víc tříd použít ML.NET
description: Zjistěte, jak používat ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy Githubu pro jejich přiřazení k dané oblasti.
ms.date: 02/01/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 79c0ae1ba38b410c0709659a4e5ee1ac2308b983
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739420"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>Kurz: Použití ML.NET ve scénáři klasifikace víc tříd ke klasifikaci problémy s úložištěm GitHub

Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru problém Githubu prostřednictvím aplikace konzoly .NET Core using C# v sadě Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte algoritmus učení příslušný počítač
> * Příprava dat
> * Extrakce funkce a transformaci dat
> * Trénování modelu
> * Vyhodnocení modelu s jinou datovou sadu
> * Předpověď jednu instanci data výsledek testu s trénovaného modelu
> * Předpověď jednu instanci s modelem načíst testovací data

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

## <a name="github-issue-sample-overview"></a>Přehled ukázky problém Githubu

Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje popisek oblasti pro problém na Githubu. Vyhodnocuje také model s druhou datové sady pro analýzy kvality. Problém datové sady jsou v úložišti dotnet/corefx Githubu.

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

* [Githubu problémy s daty oddělenými tabulátory souboru (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Problémy Githubu testovací soubor oddělených tabulátory (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="machine-learning-workflow"></a>Pracovní postup Machine learning

V tomto kurzu se řídí strojového učení pracovního postupu, který umožňuje přesunout řádný proces.

Fáze pracovního postupu jsou následující:

1. **Pochopení problému**
2. **Příprava dat**
   * **Načtení dat**
   * **Extrakce funkce (transformovat data)**
3. **Sestavení a trénování** 
   * **Trénování modelu**
   * **Vyhodnocení modelu**
4. **Spuštění**
   * **Využití modelu**

### <a name="understand-the-problem"></a>Pochopení problému

Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu. Popis vnitřních principů problému můžete předpovídat a vyhodnoťte výsledky.

Problém pro účely tohoto kurzu je pochopit, co příchozí problémy Githubu oblasti patří aby bylo možné správně popisek pro stanovení priorit a plánování.

Problém můžete rozdělit do následujících částí:

* text nadpisu problém
* popis problému
* hodnotu oblasti pro trénovací data modelu
* Předpokládaná oblasti hodnotu, kterou můžete vyhodnotit a pak použít provozně

Potom budete potřebovat **určit** oblast, která vám pomůže s strojového učení výběr úkolů.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Vyberte algoritmus učení příslušný počítač

Tento problém víte, k následujícím skutečnostem:

Cvičná data:

Problémy Githubu můžete označené v několika oblastech (**oblasti**) jako v následujících příkladech:

* area-System.Numerics
* area-System.Xml
* oblasti infrastruktury
* area-System.Linq
* System.IO oblasti

Předpověď **oblasti** z nový problém Githubu například v následujících příkladech:

* Vs Contract.Assert Debug.Assert –
* Nastavte pole jen pro čtení v System.Xml

Algoritmu strojového učení klasifikace je nejvhodnější pro tento scénář.

### <a name="about-the-classification-learning-algorithm"></a>O algoritmu učení klasifikace

Klasifikace je algoritmus strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky. Například můžete použít klasifikace:

* Zjistit mínění jako kladné nebo záporné.
* E-mailu klasifikujte jako spam nevyžádané nebo funkční.
* Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.
* Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.

Použití algoritmu učení klasifikace případy jsou často jedním z následujících typů:

* Binární soubor: buď A a B.
* Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.

Pro tento typ problému používejte klasifikaci Multiclass učení algoritmu, protože predikci kategorii problému může být jeden z více kategorií (multiclass) místo jen dvou (binární).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Vytvořte adresář *modely* ve vašem projektu a uložit model:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Modely" a stiskněte Enter.

4. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) a [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka. První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.

2. V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Vytvořte tři globální pole pro uložení cest k naposledy stažené soubory a globálních proměnných pro `MLContext`,`DataView`, `PredictionEngine`, a `TextLoader`:

* `_trainDataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
* `_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k uložení naučeného modelu.
* `_mlContext` je <xref:Microsoft.ML.MLContext> , která poskytuje kontext zpracování.
* `_trainingDataView` je <xref:Microsoft.ML.Data.IDataView> používají ke zpracování trénovací datové sady.
* `_predEngine` je <xref:Microsoft.ML.PredictionEngine%602> používá pro jeden předpovědi.
* `_reader` je <xref:Microsoft.ML.Data.TextLoader> lze načíst a transformovat datové sady.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat další proměnné a tyto cesty:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Vytvořte některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *GitHubIssueData.cs*. Vyberte **přidat** tlačítko.

    *GitHubIssueData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *GitHubIssueData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `GitHubIssue` a `IssuePrediction`, možnosti *GitHubIssueData.cs* souboru:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` je třída vstupní datová sada a má následující <xref:System.String> pole:

* `ID` obsahuje hodnotu pro ID problému Githubu
* `Area` obsahuje hodnotu `Area` popisek
* `Title` obsahuje název problému Githubu
* `Description` obsahuje popis problému Githubu

`IssuePrediction` Třída slouží k předpovědi po model se trénuje. Má jediný `string` (`Area`) a `PredictedLabel` `ColumnName` atribut. `Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu. `PredictedLabel` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.

Při vytváření modelu s ML.NET, začněte vytvořením <xref:Microsoft.ML.MLContext>. `MLContext` je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework. Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Inicializovat `_mlContext` globální proměnnou s novou instanci třídy `MLContext` s náhodná počáteční hodnota (`seed: 0`) pro opakovatelné/deterministické výsledky napříč více školení.  Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Načtení dat

V dalším kroku inicializovat `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> globální proměnné a načtení dat pomocí `_trainDataPath` parametru.

 Jako vstup a výstup [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.

Data jsou v ML.NET, podobně jako `SQL view`. Je laxně Vyhodnocená schematizovanými a heterogenní. Objekt představuje první část kanálu a načte data. Pro účely tohoto kurzu načte datovou sadu s problém názvy, popisy a odpovídající oblasti Githubu popisek. `DataView` Slouží k vytvoření a trénování modelu.

Od dříve vytvořeného `GitHubIssue` typ modelu dat odpovídá schématu datové sady, inicializace, mapování a datová sada načítání do jednoho řádku kódu lze kombinovat.

První část řádku (`CreateTextReader<GitHubIssue>(hasHeader: true)`) vytvoří <xref:Microsoft.ML.Data.TextLoader> podle odvození schématu datové sady z `GitHubIssue` datového modelu, typu a pomocí hlavičky datové sady.

Definujete schéma dat dříve při vytváření `GitHubIssue` třídy. Pro schéma:

* první sloupec `ID` (ID problému Githubu)
* druhý sloupec `Area` (Předpověď pro školení)
* třetí sloupec `Title` (název problému Githubu) je prvním [funkce](../resources/glossary.md##feature) používá pro predikci `Area`
* čtvrtý sloupec `Description` je druhá funkce používá pro predikci `Area`

Druhá část řádku (`.Read(_trainDataPath)`) používá <xref:Microsoft.ML.Data.TextLoader.Read%2A> metoda načíst text školení soubor pomocí `_trainDataPath` do `IDataView` (`_trainingDataView`) globální proměnné.  

K inicializaci a načíst `_trainingDataView` globální proměnné, aby bylo možné používat pro kanál, přidejte následující kód za `mlContext` inicializace:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


Přidejte následující položky jako další řádek kódu `Main` metody:

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` Metoda spustí následující úlohy:

* Extrahuje a transformuje data.
* Vrátí kanálu zpracování.

Vytvořte `ProcessData` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Extrakce funkce a transformaci dat

Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning. Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty. Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.

ML. Kanály transformace vaší NET napsat vlastní `transforms`sada, která se použije pro vaše data před trénování a testování. Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering). Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data. Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).

V dalších krocích, budeme odkazovat na sloupce pomocí názvy definované v `GitHubIssue` třídy.

Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat. Jelikož chceme předpovědět popisek oblasti Githubu pro `GitHubIssue`, kopie `Area` sloupce do **popisek** sloupec. Chcete-li to mohli udělat, použijte `MLContext.Transforms.Conversion.MapValueToKey`, který tvoří obálku pro <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> třídy transformace.  `MapValueToKey` Vrátí <xref:Microsoft.ML.Data.EstimatorChain%601> efektivně, který bude kanál. Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`. Přidáte další řádek kódu:

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 Featurizing přiřadí různé číselné hodnoty klíče na různé hodnoty v každém sloupci a je používán algoritmu strojového učení. Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` které featurizes text (`Title` a `Description`) sloupce jako číselné vektor pro každou volá `TitleFeaturized` a `DescriptionFeaturized`. Snadné pro oba sloupce pro přidání do kanálu s následujícím kódem:

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `Concatenate` třídy transformace. Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce. Připojte tuto transformaci na kanál s následujícím kódem:

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 V dalším kroku připojit <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> pro ukládání do mezipaměti DataView, takže při iteraci přes data s využitím více než jednou mezipaměti může dosahovat vyšších výkonů, stejně jako u následujícího kódu:

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

Kanál na konci vrátit `ProcessData` metody.

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Tento krok zpracovává předběžného zpracování a snadné. Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.

## <a name="build-and-train-the-model"></a>Vytvoření a trénování modelu

Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Metoda spustí následující úlohy:

* Vytvoří třídu algoritmus školení.
* Trénovat modelu.
* Předpovídá oblasti založené na trénovací data.
* Uloží model, který má `.zip` souboru.
* Vrátí hodnotu modelu.

Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static EstimatorChain<KeyToValueMappingTransformer> BuildAndTrainModel(IDataView trainingDataView, EstimatorChain<ITransformer> pipeline)
{

}
```

Všimněte si, že dva parametry jsou předány do metody BuildAndTrainModel; `IDataView` pro trénovací datové sady (`trainingDataView`) a <xref:Microsoft.ML.Data.EstimatorChain%601> pro zpracování kanálu, který vytvořili v ProcessData (`pipeline`).

 Přidejte následující kód jako první řádek `BuildAndTrainModel` metody:

### <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Chcete-li přidat algoritmu učení, použijte <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> objektu.  `SdcaMultiClassTrainer` Se připojí `pipeline` a přijímá natrénuje `Title` a `Description` (`Features`) a `Label` vstupní parametry učit se z historických dat.

Přidejte následující kód, který `BuildAndTrainModel` metody:

[!code-csharp[SdcaMultiClassTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SdcaMultiClassTrainer)]

Teď, když jste vytvořili algoritmu učení, připojte ho k `pipeline`. Potřebujete také mapovat popisku na hodnotu, která vrátí k původnímu čitelné. Proveďte obě tyto akce s následujícím kódem:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a>Trénování modelu

Trénování modelu, <xref:Microsoft.ML.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat. Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> současně už načtený trénovací data. Tato metoda vrátí model pro předpovědi. `trainingPipeline.Fit()` trénovat kanálu a vrátí `Transformer` na základě `DataView` předán. Dokud není spuštěn experimentu `.Fit()` metoda spuštění.

Přidejte následující kód, který `BuildAndTrainModel` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, třeba k předpovědím na jednotlivé příklady je běžný scénář produkčního prostředí. <xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody. Přidejte následující kód k vytvoření `PredictionEngine` jako další řádek `BuildAndTrainModel` metody:

[!code-csharp[CreatePredictionEngine1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Který můžete použít k předpovědi `Area` popisek jednu instanci data problém. Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data. Vstupní data je řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction"></a>Pomocí modelu: předpověď

Zobrazení `GitHubIssue` a odpovídající `Area` popisek predikcí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně.  Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Vrátí že model se trénuje má použít pro hodnocení

Model na konci vrátit `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování. V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení. Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:

```csharp
public static void Evaluate()
{

}
```

`Evaluate` Metoda spustí následující úlohy:

* Načte datovou sadu testů.
* Vytvoří víc tříd Chyba při vyhodnocování.
* Vyhodnotí modelu a vytvoření metriky.
* Zobrazuje metriky.

Přidejte volání do nové metody z `Main` metody, v rámci `BuildAndTrainModel` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Stejně jako dříve trénovací datové sady, můžete kombinovat inicializace, mapování a otestovat datovou sadu načítání do jednoho řádku kódu. Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality. Přidejte následující kód, který `Evaluate` metody:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

`MulticlassClassificationContext.Evaluate` Tvoří obálku pro <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> metodu, která vypočítá metrik kvality pro model pomocí zadaného objektu dataset. Vrátí <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení klasifikace víc tříd.
Pokud chcete zobrazit metriky pro určení kvality tohoto modelu, musíte je získat první.
Všimněte si použití `Transform` metoda služby machine learning `_trainedModel` globální proměnné (transformace) k zadání funkce a vrátí předpovědi. Přidejte následující kód, který `Evaluate` metody jako další řádek:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Klasifikace víc tříd, se vyhodnotí následující metriky:

* Micro přesnost – každá dvojice ukázkovou třídu přispívá stejně metriky přesnosti.  Chcete, aby Micro přesnost, aby byly co nejblíže 1 nejvíce.

* Přesnost – makro – každá třída přispívá stejně metriky přesnosti. Třídy minority disponují stejnou váhu jako větší třídy. Chcete, aby byly co nejblíže 1 nejvíce přesnost – makro.

* Protokol ztrát – naleznete v tématu [protokolu ztráty](../resources/glossary.md#log-loss). Chcete ztrátě protokolu bude co nejblíže nuly nejvíce.

* Od ztráty protokolu snížení - [-inf, 100], kde 100 je ideální předpovědi a 0 označuje střední předpovědi. Chcete, aby omezení ztráty protokolu bude co nejblíže nuly nejvíce.

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a>Uložení natrénovaného a vyhodnocené modelu

V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET. Uložte soubor .zip trénovaného modelu, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `BuildAndTrainModel`:

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a>Model uložit jako soubor ZIP

Vytvořte `SaveModelAsFile` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda spustí následující úlohy:

* Uloží modelu ve formě souboru .zip.

Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích. `ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>. Model uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody. Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

Může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Předpověď data výsledek testu s modelem uložené

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

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

Nejdřív načtěte model, který jste si předtím uložili následujícím kódem:

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

Přidejte problém na Githubu k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `GitHubIssue`:

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Teď, když máte model, který můžete použít k predikci popisek oblasti Githubu jedné instance dat problém Githubu. Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data. Vstupní data je řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi. Přidejte následující kód, který `PredictIssue` metodu předpovědí:

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Použití načíst model pro předpověď

Zobrazení `Area` kategorizace problém a příslušně na ně reagovat na něj. Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto. Při zpracování kanálu zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Tyto zprávy se odebraly z následujících výsledků pro přehlednost.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Blahopřejeme! Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat popisek oblasti pro problém na Githubu. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte algoritmus učení příslušný počítač
> * Příprava dat
> * Extrakce funkce a transformaci dat
> * Trénování modelu
> * Vyhodnocení modelu s jinou datovou sadu
> * Předpověď jednu instanci data výsledek testu s trénovaného modelu
> * Předpověď jednu instanci s modelem načíst testovací data

Přejděte k dalšímu kurzu, kde Další informace
> [!div class="nextstepaction"]
> [Prediktivní tarif taxislužby města](taxi-fare.md)
