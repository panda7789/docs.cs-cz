---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 11/06/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: cffce6258685502191e1dd33ef8282d664ea2d4c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149650"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Kurz: Použití ML.NET ve scénáři binární klasifikace analýzy mínění

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento ukázkový kurz ukazuje použití ML.NET vytvoření klasifikátoru mínění prostřednictvím aplikace konzoly .NET Core pomocí jazyka C# v sadě Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava dat
> * Vytvoření kanálu učení
> * Načíst třídění
> * Trénování modelu
> * Vyhodnocení modelu s jinou datovou sadu
> * Předpověď jednu instanci data výsledek testu s modelem
> * Předpověď výsledků dat testu se načíst model

## <a name="sentiment-analysis-sample-overview"></a>Přehled ukázky analýzy mínění

Vzorek je konzolová aplikace, které používá ML.NET pro trénování modelu, která klasifikuje a predikuje mínění jako kladné nebo záporné. Vyhodnocuje také model s druhou datové sady pro analýzy kvality. Datové sady subjektivního hodnocení jsou z WikiDetox projektu.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

* [Souboru (wikiPedia – detox – 250řádku data.tsv) s daty oddělenými tabulátory data řádku detox Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Souboru (wikipedia – detox – 250řádku test.tsv) s daty oddělenými tabulátory test řádku detox Wikipedia](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

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

Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu. Rozdělení problému můžete předpovídat a vyhodnoťte výsledky.

Problém pro účely tohoto kurzu je pochopit příchozí subjektivního hodnocení webu komentář, proveďte příslušnou akci.

Problém můžete rozdělit mínění textu a mínění hodnotu pro data chcete trénování modelu s a předpokládané mínění hodnotu, kterou můžete vyhodnotit a pak použít provozně.

Potom budete potřebovat **určit** subjektivního hodnocení, které vám pomůžou s strojového učení výběr úkolů.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

Tento problém víte, k následujícím skutečnostem:

Cvičná data: komentáře web může být toxické (1) nebo ne toxické (0) (**mínění**).
Předpověď **mínění** nový web komentáře, toxické nebo není toxické, jako například v následujících příkladech:

* Nepřidávejte nesmysl na wikipedii.
* Je to nejlepší a článek, který by mělo být uvedeno.

Úloha klasifikace machine learning je nejvhodnější pro tento scénář.

### <a name="about-the-classification-task"></a>O úloze klasifikace

Klasifikace je úloha strojového učení, který používá data **určit** kategorie, typ nebo třída řádek dat nebo položky. Například můžete použít klasifikace:

* Zjistit mínění jako kladné nebo záporné.
* E-mailu klasifikujte jako spam nevyžádané nebo funkční.
* Zjistit, zda je cancerous ukázka pacienta testovacího prostředí.
* Kategorizace zákazníci podle svých tendence k reakci na prodejní kampaně.

Úlohy klasifikace jsou často jedním z následujících typů:

* Binární soubor: buď A a B.
* Multiclass: více kategorií, které lze předpovídat pomocí jednoho modelu.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář *Data* ve vašem projektu a uložte soubory datové sady:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, Hledat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhněte si [WikiPedia detox – 250řádku data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) a [wikipedia – detox – 250řádku test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) dat nastaví a uloží je do *Data* dříve vytvořená složka. První datovou sadu trénovat modelu strojového učení a druhý je možné vyhodnotit, jak přesný je váš model.

2. V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*TSV souborů a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Je potřeba vytvořit tři globální pole pro uložení cest k naposledy stažené soubory a globální proměnné pro `TextLoader`:

* `_trainDataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
* `_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k uložení naučeného modelu.
* `_reader` je <xref:Microsoft.ML.Runtime.Data.TextLoader> lze načíst a transformovat datové sady.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty a `_textLoader` proměnné:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko.

    *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` je třída vstupní datová sada a má `float` (`Sentiment`), který má hodnotu pro pozitivní nebo negativní zabarvení a řetězec pro komentář (`SentimentText`). Obě pole mají `Column` atributy připojené k nim. Popisuje pořadí každé pole v datovém souboru a které je tento atribut `Label` pole. `SentimentPrediction` Třída slouží k předpovědi po model se trénuje. Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut. `Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu. `PredictedLabel` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.

Při vytváření modelu s ML.NET začnete vytvořením `MLContext`. Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework. Prostředí poskytuje kontext pro vaši úlohu ML, který lze použít pro sledování a protokolování výjimek.

### <a name="initialize-variables-in-main"></a>Inicializace proměnné ve funkci Main

Vytvořte proměnnou s názvem `mlContext` a inicializujte novou instanci třídy `MLContext`.  Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

Další nastavení pro načítání inicializace dat `_textLoader` globální proměnné, aby bylo možné znovu použít.  Všimněte si, že používáte `TextReader`. Při vytváření `TextLoader` pomocí `TextReader`, předáte v souvislosti potřebné a <xref:Microsoft.ML.Runtime.Data.TextLoader.Arguments> třída, která umožňuje přizpůsobení.

 Zadejte schéma dat předáním pole <xref:Microsoft.ML.Runtime.Data.TextLoader.Column> zavaděč obsahující všechny názvy sloupců a jejich typy objektů. Definujete schéma dat dříve při vytváření naše `SentimentData` třídy. Pro naše schéma z prvního sloupce (popisek) je <xref:System.Boolean> (předpověď) a druhý sloupec (SentimentText) je funkce typu text/řetězec použitý pro predikci mínění.
`TextReader` Třídy vrátí plně inicializován <xref:Microsoft.ML.Runtime.Data.TextLoader>  

Inicializovat `_textLoader` globální proměnné, aby bylo možné znovu použít pro potřeby datové sady, přidejte následující kód za `mlContext` inicializace:

[!code-csharp[initTextReader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextReader")]

Přidejte následující položky jako další řádek kódu `Main` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

`Train` Metoda spustí následující úlohy:

* Načte data.
* Extrahuje a transformuje data.
* Trénovat modelu.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Vrátí hodnotu modelu.

Vytvořte `Train` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

Všimněte si, že dva parametry jsou předány do metody trénování; `MLContext` kontextu (`mlContext`) a <xref:System.String> pro cestu k datové sadě (`dataPath`). Chystáte se tuto metodu použít více než jednou pro trénování a testování.

## <a name="load-the-data"></a>Načtení dat

Budete nahrajte data s využitím `_textLoader` globální proměnné `dataPath` parametru. Vrátí <xref:Microsoft.ML.Runtime.Data.IDataView>. Jako vstup a výstup `Transforms`, `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.

Data jsou v ML.NET, podobně jako zobrazení SQL. Je laxně Vyhodnocená schematizovanými a heterogenní. Objekt představuje první část kanálu a načte data. Pro účely tohoto kurzu načte datovou sadu s komentáři a odpovídající toxické nebo jiných toxické mínění. Slouží k vytvoření modelu a jeho trénování.

 Přidejte následující kód jako první řádek `Train` metody:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a>Extrahovat a transformaci dat

Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning. Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty. Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky.

ML. Kanály transformace vaší sítě vytvořit vlastní sadu transformací, které se použijí pro vaše data před trénování a testování. Hlavním účelem transformace jsou data [snadné](../resources/glossary.md#feature-engineering). Vysvětlení algoritmů strojového učení [natrénuje](../resources/glossary.md#feature) data, abyste dalším krokem je získat z našich algoritmů ML rozpoznat formát naše textová data. Tento formát je [číselné vektoru](../resources/glossary.md#numerical-feature-vector).

Pak zavolejte `mlContext.Transforms.Text.FeaturizeText` které featurizes textového sloupce (`SentimentText`) sloupec jako číselný vektor nazývá `Features` používá algoritmus strojového učení. Toto je obálka volání, které se vrátí <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601> efektivně, který bude kanál. Pojmenujte toto `pipeline` jako se pak připojí trainer k `EstimatorChain`. Přidáte jako další řádek kódu:

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

Jedná se o krok předběžného zpracování a snadné. Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model.

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

Přidáte školitele volání `mlContext.Transforms.Text.FeaturizeText` obalující metodu, která vrátí hodnotu <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> objektu. Toto je learner stromu rozhodnutí, které budete používat v tomto kanálu. `FastTreeBinaryClassificationTrainer` Se připojí `pipeline` a přijímá natrénuje `SentimentText` (`Features`) a `Label` vstupní parametry učit se z historických dat.

Přidejte následující kód, který `Train` metody:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Trénování modelu

Trénování modelu, <xref:Microsoft.ML.Runtime.Data.TransformerChain%601>založená na datovou sadu, která má načíst a transformovat. Po definování odhadu tréninku modelu pomocí <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601.Fit%2A> současně už načtený trénovací data. Vrátí model pro předpovědi. `pipeline.Fit()` trénovat kanálu a vrátí `Transformer` na základě `DataView` předán. Experiment není spuštěn, dokud k tomu dojde.

Přidejte následující kód, který `Train` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Uložte a vraťte se model se trénuje má použít pro hodnocení

V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain%601> , který je možné integrovat do všech existujících nebo nových aplikací .NET. Model na konci vrátit `Train` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování. V `Evaluate` metody, vytvořené v modelu `Train` předaný k vyhodnocení. Vytvořte `Evaluate` metoda, hned za `Train`, jako v následujícím kódu:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` Metoda spustí následující úlohy:

* Načte datovou sadu testů.
* Vytvoří binární Chyba při vyhodnocování.
* Vyhodnotí modelu a vytvoření metriky.
* Zobrazuje metriky.

Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

Budete načíst datovou sadu testů pomocí dříve inicializován `_textLoader` globální proměnné `_testDataPath` globální pole. Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality. Přidejte následující kód, který `Evaluate` metody:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

V dalším kroku budete pomocí machine learning `model` parametr (transformace) pro vstup funkce a vrátí předpovědi. Přidejte následující kód, který `Evaluate` metody jako další řádek:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

`BinaryClassificationContext.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady. Vrátí `BinaryClassificationEvaluator.CalibratedResult` objekt obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení binární klasifikace. Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první. Přidejte následující kód jako další řádek `Evaluate` metody:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

Pokud chcete uložit model do souboru ZIP a teprve potom se informuje, přidejte následující kód k volání `SaveModelAsFile` metody jako další řádek v `TrainFinalModel`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a>Uložit jako soubor a.zip model

Vytvořte `SaveModelAsFile` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda spustí následující úlohy:

* Uloží modelu ve formě souboru .zip.

Dále vytvořte metodu k uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích. `ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.Runtime.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>. Uložit jako soubor zip, vytvoříte `FileStream` bezprostředně před volání `SaveTo` metody. Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]

Může také zobrazit, kde soubor byl zapsán napsáním zprávu konzoly `_modelPath`, pomocí následujícího kódu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>Předpověď data výsledek testu s modelem a jednoho komentáře

Vytvořte `Predict` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

`Predict` Metoda spustí následující úlohy:

* Vytvoří jeden komentář testovací data.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí. <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> Představuje obálku, která je vrácena z `MakePredictionFunction` metody. Přidejte následující kód k vytvoření PredictionFunction jako první řádek `Predict` metody:

[!code-csharp[MakePredictionFunction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionFunction")]
  
Přidejte komentář k otestování trénovaného modelu předpovědi v `Predict` metodu tak, že vytvoříte instanci `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]


 Který můžete použít k predikci toxické nebo jiných toxické mínění jednu instanci data komentáře. Chcete-li získat predikcí, použijte <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602.Predict(%600)> na data. Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="model-operationalization-prediction"></a>Operacionalizace modelu: předpověď

Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně. Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady. Vytvoření zobrazení pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="predict-the-test-data-outcomes-with-the-saved-model"></a>Předpověď výsledků dat testu s modelem uložené

Vytvořte `PredictWithModelLoadedFromFile` metoda, těsně před `SaveModelAsFile` metodu, pomocí následujícího kódu:

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

`PredictWithModelLoadedFromFile` Metoda spustí následující úlohy:

* Vytvoří služby batch testovací data.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `Predict` volání metody, pomocí následujícího kódu:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `PredictWithModelLoadedFromFile` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

Načíst model [!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

Teď, když máte model, vám pomůže, která předvídat toxické nebo jiných toxické mínění komentář dat pomocí <xref:Microsoft.ML.Core.Data.ITransformer.Transform(Microsoft.ML.Runtime.Data.IDataView)> metody. Chcete-li získat predikcí, použijte `Predict` na nová data. Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi. Přidejte následující kód, který `PredictWithModelLoadedFromFile` metodu předpovědí:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Operacionalizace modelu: předpověď

Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně. Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady. Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

Před zobrazením předpokládané výsledky, kombinovat mínění a predikcí společně zobrazíte původním komentářem s jeho predikované mínění. Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda docílit, vedle proto přidejte tento kód:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

Teď, když jste kombinovat `SentimentText` a `Sentiment` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

Protože odvozené názvy elementů řazené kolekce členů se, že je nová funkce v jazyce C# 7.1 a výchozí jazyková verze projektu C# 7.0, potřebujete změnit verzi jazyka C# 7.1 nebo novější.
To mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**. Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze). Vyberte tlačítko **OK**.

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto. Při zpracování kanálu zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Ty se odebraly z následujících výsledků pro přehlednost.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.0\Data\Model.zip

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: He is the best, and the article should say that. | Prediction: Not Toxic | Probability: 0.9924279

```

Blahopřejeme! Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava dat
> * Vytvoření kanálu učení
> * Načíst třídění
> * Trénování modelu
> * Vyhodnocení modelu s jinou datovou sadu
> * Předpověď výsledků dat testu s modelem

Přejděte k dalšímu kurzu, kde Další informace
> [!div class="nextstepaction"]
> [Prediktivní tarif taxislužby města](taxi-fare.md)
