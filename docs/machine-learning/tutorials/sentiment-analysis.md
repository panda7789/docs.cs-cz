---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d94e254f0cdf56c21c94012f824f05a550e4da2f
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788463"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Kurz: Použití ML.NET ve scénáři binární klasifikace analýzy mínění

Tento ukázkový kurz ukazuje vytvoření klasifikátoru subjektivního hodnocení pro předpověď pozitivní nebo negativní zabarvení prostřednictvím using aplikace konzoly .NET Core pomocí ML.NET C# v sadě Visual Studio 2017. Ve světě služby machine learning tohoto typu predikcí se nazývá binární klasifikace.

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz a související ukázkové právě používáte **ML.NET verze 0,11**. Další informace najdete v tématu poznámky k verzi v [dotnet/machinelearning úložiště GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte algoritmus učení příslušný počítač
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Predikce v trénovaného modelu
> * Nasazení a predikce v načíst model

## <a name="sentiment-analysis-sample-overview"></a>Přehled ukázky analýzy mínění

Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje mínění jako kladné nebo záporné. Tato datová sada Yelp mínění je z University of California, Irvine (UCI), který je rozdělený do datové sady pro trénování a datové sady testů. Ukázka vyhodnotí model s testovací datové analýzy kvality. 

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

* [Soubor zip UCI subjektivního hodnocení s popiskem věty datové sady](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

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
4. **Nasazení modelu**
   * **Použijte Model k predikci**

### <a name="understand-the-problem"></a>Pochopení problému

Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu. Rozdělení problému můžete předpovídat a vyhodnoťte výsledky.

Problém pro účely tohoto kurzu je pochopit příchozí subjektivního hodnocení webu komentář, proveďte příslušnou akci.

Problém můžete rozdělit mínění textu a mínění hodnotu pro data chcete trénování modelu s a předpokládané mínění hodnotu, kterou můžete vyhodnotit a pak použít provozně.

Potom budete potřebovat **určit** subjektivního hodnocení, které vám pomůžou s strojového učení výběr úkolů.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Vyberte algoritmus učení příslušný počítač

Tento problém víte, k následujícím skutečnostem:

Cvičná data: komentáře web může být kladná (1) nebo záporná (0) (**mínění**).

Předpověď **mínění** nový web komentáře, kladná nebo záporná, jako například v následujících příkladech:

* Mám rád číšníky tady. Že jdeme na to.
* Toto umístění má nejhorší polévky.

Algoritmu strojového učení klasifikace je nejvhodnější pro tento scénář.

### <a name="about-the-classification-algorithm"></a>O klasifikační algoritmus

Klasifikace je algoritmus strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky. Například můžete použít klasifikace:

* Zjistit mínění jako kladné nebo záporné.
* E-mailu klasifikujte jako spam nevyžádané nebo funkční.
* Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.
* Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.

Algoritmy klasifikace jsou často jedním z následujících typů:

* Binární soubor: buď A a B.
* Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.

Protože webu komentáře zapotřebí klasifikováno jako kladné nebo záporné, použít binární klasifikační algoritmus. 

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si [soubor zip The UCI subjektivního hodnocení s popiskem věty datové sady (viz citace v následující poznámce)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)a rozbalte ho.

2. Kopírovat `yelp_labelled.txt` soubor do *Data* adresáře, které jste vytvořili.

> [!NOTE]
> Tento kurz používá datové sady jsou z "From skupina na jednotlivé popisky pomocí podrobné funkce", Kotzias et. al,. Konference KDD 2015 a hostované v UCI Machine Learning úložiště – Dua, D. a Karra Taniskidou, E. (2017). UCI strojového učení úložiště [http://archive.ics.uci.edu/ml]. Irvine, certifikační Autorita: University of California, z informací o škole a počítačových věd.

3. V Průzkumníku řešení klikněte pravým tlačítkem myši `yelp_labeled.txt` a vyberte možnost **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

Je potřeba vytvořit dvě globální pole pro uložení naposledy stažené datovou sadu cesta k souboru a cesta k souboru uloženého modelu:

* `_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
* `_modelPath` obsahuje cestu k uložení naučeného modelu.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko.

    *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

Třída vstupní datová sada `SentimentData`, má `string` pro komentář (`SentimentText`) a `bool` (`Sentiment`), který má hodnotu pro pozitivní nebo negativní zabarvení. Obě pole mají <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> atributy připojené k nim. Tento atribut popisuje pořadí každé pole v datovém souboru služby.  Kromě toho `Sentiment` má vlastnost <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> nastavit jako `Label` pole. `SentimentPrediction` Třída slouží k předpovědi po model se trénuje. Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut. `Label` Slouží k vytvoření a trénování modelu a jeho rozdělení na testovací datové použít také k vyhodnocení modelu. `PredictedLabel` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.

Při vytváření modelu s ML.NET začnete vytvořením <xref:Microsoft.ML.MLContext>. `MLContext` je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework. Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Vytvořte proměnnou s názvem `mlContext` a inicializujte novou instanci třídy `MLContext`.  Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

Přidejte následující položky jako další řádek kódu `Main` metody:

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData` Metoda spustí následující úlohy:

* Načte data.
* Rozdělí načíst datovou sadu na trénování a testování datových sad.
* Vrátí hodnotu rozdělení trénují a testují datové sady.

Vytvořte `LoadData` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>Načtení dat

Od dříve vytvořeného `SentimentData` typ modelu dat odpovídá schématu datové sady, můžete kombinovat inicializace, mapování a datovou sadu na jeden řádek kódu pomocí načítání `MLContext.Data.ReadFromTextFile` obálky pro <xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29>. Vrátí <xref:Microsoft.Data.DataView.IDataView>. 

 Jako vstup a výstup `Transforms`, `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.

Data jsou v ML.NET, podobně jako zobrazení SQL. Je laxně Vyhodnocená schematizovanými a heterogenní. Objekt představuje první část kanálu a načte data. Pro účely tohoto kurzu načte datovou sadu s komentáři a odpovídající toxické nebo jiných toxické mínění. Slouží k vytvoření modelu a jeho trénování.

 Přidejte následující kód jako první řádek `LoadData` metody:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>Rozdělení datové sady pro trénování a testování modelu

Dále je třeba trénovací datové sady pro trénování modelu a datové sady testů k vyhodnocení modelu. Použití `MLContext.BinaryClassification.TrainTestSplit` která zabalí <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> rozdělit načíst datovou sadu na trénování a testování datových sad a vrátit je uvnitř <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>. Část dat můžete zadat nastavení testu s `testFraction`parametru. Výchozí hodnota je 10 %, ale v tomto případě použijte 20 % používat další data pro vyhodnocení.  

Načtená data rozdělením potřebné datové sady, přidejte následující kód jako další řádek `LoadData` metody:

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

Vrátit `splitDataView` na konci `LoadData` metody:

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Vytvoření a trénování modelu

Přidejte následující volání `BuildAndTrainModel`metody jako další řádek kódu v `Main` metody:

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Metoda spustí následující úlohy:

* Extrahuje a transformuje data.
* Trénovat modelu.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Vrátí hodnotu modelu.

Vytvořte `BuildAndTrainModel` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

Všimněte si, že dva parametry jsou předány do metody trénování; `MLContext` kontextu (`mlContext`) a `IDataView`pro trénovací datové sady (`splitTrainSet`). 

## <a name="extract-and-transform-the-data"></a>Extrahovat a transformaci dat

Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning. Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty. Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.

ML. Kanály transformace vaší sítě vytvořit vlastní sadu transformací, které se použijí pro vaše data před trénování a testování. Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering). Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data. Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).

Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` které featurizes textového sloupce (`SentimentText`) sloupec jako číselný vektor nazývá `Features` používá algoritmus strojového učení. Toto je obálka volání, které se vrátí <xref:Microsoft.ML.Data.EstimatorChain%601> efektivně, který bude kanál. Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`. Přidáte jako další řádek kódu:

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> ML.NET verze 0.10 změnit pořadí parametrů transformace. Tímto krokem se nevygeneruje chybu, dokud při spuštění aplikace a vytváření modelu. Použijte názvy parametrů transformací, jak je znázorněno v předchozím fragmentu kódu.

Jedná se o krok předběžného zpracování a snadné. Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Přidáte školitele volání `mlContext.BinaryClassification.Trainers.FastTree` obalující metodu, která vrátí hodnotu <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> objektu. Toto je learner stromu rozhodnutí, které budete používat v tomto kanálu. `FastTreeBinaryClassificationTrainer` Se připojí `pipeline` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.

Přidejte následující kód, který `BuildAndTrainModel` metody:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Trénování modelu, <xref:Microsoft.ML.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat. Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> metoda současně už načtený trénovací data. Vrátí model pro předpovědi. `pipeline.Fit()` trénovat kanálu a vrátí `Transformer` na základě `DataView` předán. Dokud není spuštěn experimentu `.Fit()` metoda spuštění.

Přidejte následující kód, který `BuildAndTrainModel` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Uložte a vraťte se model se trénuje má použít pro hodnocení

V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET. Model na konci vrátit `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování. V `Evaluate` metody, vytvořené v modelu `BuildAndTrainModel` předaný k vyhodnocení. Vytvořte `Evaluate` metoda, hned za `BuildAndTrainModel`, jako v následujícím kódu:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate` Metoda spustí následující úlohy:

* Načte datovou sadu testů.
* Chyba při vyhodnocování binaryclassification vytvoří.
* Vyhodnotí modelu a vytvoří metriky.
* Zobrazuje metriky.

Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

V dalším kroku budete pomocí machine learning `model` parametr (transformace) a `splitTestSet` parametr pro vstup funkce a vrátí předpovědi. Přidejte následující kód, který `Evaluate` metody jako další řádek:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

`mlContext.BinaryClassification.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení binární klasifikace. Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první. Přidejte následující kód jako další řádek `Evaluate` metody:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

Pokud chcete uložit model do souboru ZIP a teprve potom se informuje, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `Evaluate`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a>Uložit jako soubor a.zip model

Vytvořte `SaveModelAsFile` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda spustí následující úlohy:

* Uloží modelu ve formě souboru .zip.

Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích. `ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>. Uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody. Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Nasazení a predikce v načíst model

Může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Předpověď data výsledek testu s modelem uložené

Vytvořte `UseModelWithSingleItem` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem` Metoda spustí následující úlohy:

* Vytvoří jeden komentář testovací data.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí. <xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody. Přidejte následující kód k vytvoření `PredictionEngine` jako první řádek `Predict` metody:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 Který můžete použít k predikci kladné nebo záporné mínění jednu instanci data komentáře. Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data. Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>Použití modelu: předpověď

Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně. Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady. Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Nasazení a predikce v načíst model

Vytvořte `UseLoadedModelWithBatchItems` metoda, těsně před `SaveModelAsFile` metodu, pomocí následujícího kódu:

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

`UseLoadedModelWithBatchItems` Metoda spustí následující úlohy:

* Vytvoří služby batch testovací data.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `UseModelWithSingleItem` volání metody, pomocí následujícího kódu:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `UseLoadedModelWithBatchItems` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

Načíst model

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

Teď, když máte model, vám pomůže, která předvídat toxické nebo jiných toxické mínění komentář dat pomocí <xref:Microsoft.ML.ITransformer.Transform%2A> metody. Chcete-li získat predikcí, použijte `Predict` na nová data. Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi. Přidejte následující kód, který `UseLoadedModelWithBatchItems` metodu předpovědí:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>Použít načíst model pro předpověď

Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně. Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady. Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Před zobrazením předpokládané výsledky, kombinovat mínění a predikcí společně zobrazíte původním komentářem s jeho predikované mínění. Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda docílit, vedle proto přidejte tento kód:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

Teď, když jste kombinovat `SentimentText` a `Sentiment` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

Protože odvozené názvy elementů řazené kolekce členů se, že je nová funkce v jazyce C# 7.1 a výchozí jazyková verze projektu C# 7.0, potřebujete změnit verzi jazyka C# 7.1 nebo novější.
To mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**. Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze). Vyberte tlačítko **OK**.

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto. Při zpracování kanálu zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Ty se odebraly z následujících výsledků pro přehlednost.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Blahopřejeme! Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění. 

Vytváření modelů po úspěšné je iterativní proces. Tento model má nižší počáteční kvalita jako kurz používá malé datové sady poskytují rychlý model školení. Pokud si nejste spokojeni s kvalitou modelu, můžete ho vylepšit tím, že poskytuje větší cvičných datových sad nebo výběrem jiné školení algoritmy s jinou hyperparametry pro jednotlivé algoritmy.

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte algoritmus učení příslušný počítač
> * Příprava dat
> * Transformace dat
> * Trénování modelu
> * Vyhodnocení modelu
> * Predikce v trénovaného modelu
> * Nasazení a predikce v načíst model

Přejděte k dalšímu kurzu, kde Další informace
> [!div class="nextstepaction"]
> [Klasifikace problému](github-issue-classification.md)
