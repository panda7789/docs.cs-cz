---
title: Použití ML.NET ve scénáři binární klasifikace analýzy mínění
description: Objevte, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí mínění předpovědi proveďte příslušnou akci.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: dec44bf114472e19fdac131e0af6c13854957fe3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745525"
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
> * Předpověď výsledků dat testu s modelem

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
2. **Zpracování příjmu dat**
3. **Předběžné zpracování dat a návrh funkcí**
4. **Trénování a předpověď modelu**
5. **Vyhodnocení modelu**
6. **Operacionalizace modelu**

### <a name="understand-the-problem"></a>Pochopení problému

Je nutné nejprve porozumět danému problému, takže ho můžete rozdělit na části, které podporují vytváření a trénování modelu. Zásadní potíže dolů můžete předpovídat a vyhodnoťte výsledky.

Problém pro účely tohoto kurzu je pochopit příchozí subjektivního hodnocení webu komentář, proveďte příslušnou akci.

Problém můžete rozdělit mínění textu a mínění hodnotu pro data chcete trénování modelu s a předpokládané mínění hodnotu, kterou můžete vyhodnotit a pak použít provozně.

Potom budete potřebovat **určit** subjektivního hodnocení, které vám pomůžou s strojového učení výběr úkolů.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

Tento problém víte, k následujícím skutečnostem:

Cvičná data: komentáře web může být kladná nebo záporná (**mínění**).
Předpověď **mínění** nový web komentáře, kladná nebo záporná, jako například v následujících příkladech:

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

Je potřeba vytvořit tři globální pole pro uložení cest k naposledy stažené soubory:

* `_dataPath` obsahuje cestu k datové sadě využívají k tréninku modelu.
* `_testDataPath` obsahuje cestu k datové sadě k vyhodnocení modelu.
* `_modelPath` obsahuje cestu k uložení naučeného modelu.

Přidejte následující kód na řádku vpravo nahoře `Main` metoda zadat tyto cesty:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Je potřeba vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **třídy** a změnit **název** pole *SentimentData.cs*. Vyberte **přidat** tlačítko.

    *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, možnosti *SentimentData.cs* souboru:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` je třída vstupní datová sada a má `float` (`Sentiment`), který má hodnotu pro pozitivní nebo negativní zabarvení a řetězec pro komentář (`SentimentText`). Obě pole mají `Column` atributy připojené k nim. Popisuje pořadí každé pole v datovém souboru a které je tento atribut `Label` pole. `SentimentPrediction` Třída slouží k předpovědi po model se trénuje. Má jeden datový typ boolean (`Sentiment`) a `PredictedLabel` `ColumnName` atribut. `Label` Slouží k vytvoření a trénování modelu a jeho datové sady druhé použít také k vyhodnocení modelu. `PredictedLabel` Se používá při předpovědi a vyhodnocení. Pro vyhodnocení se používají vstupní trénovací data, předpovězeným hodnotám a model.

V *Program.cs* změňte `Main` podpis metody tak, že nahradíte `void` s `async Task`, jako v následujícím příkladu:

```csharp
static async Task Main(string[] args) 
{

}
```

Přidáte `async` k `Main` s <xref:System.Threading.Tasks.Task> návratový typ, protože ukládání modelu do souboru zip později, a program musí počkat až do dokončení této úlohy externí.

> [!NOTE]
> *Asynchronní funkce main* metoda vám umožňuje používat `await` ve vaší `Main` metoda. Další informace najdete v tématu [asynchronní funkce main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) v Průvodci programovacího jazyka C#.

Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` Metoda spustí následující úlohy:

* Načte nebo ingestuje data.
* Předzpracuje a featurizes data.
* Trénovat modelu.
* Předpovídá subjektivního hodnocení na základě dat testu.

Vytvořte `Train` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a>Zpracování příjmu dat

Inicializuje novou instanci třídy <xref:Microsoft.ML.LearningPipeline> , který bude obsahovat načítání dat, zpracování dat a snadné a modelu. Přidejte následující kód jako první řádek `Train` metody:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.Data.TextLoader> Objektu je první částí kanálu a načte soubor trénovací data.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Předběžné zpracování dat a návrh funkcí

Předběžné zpracování a čištění dat jsou důležité úkoly, ke kterým dochází před použitím datové sady je efektivní pro machine learning. Nezpracovaná data se často aktivní nebo nespolehlivé a může být chybějící hodnoty. Pomocí data, aniž by tyto úlohy modelování můžete vytvářet zavádějící výsledky. ML. NET pro transformace kanály umožňují napsat vlastní sadu transformací, které se použijí pro vaše data před trénování a testování. Hlavním účelem transformace je pro snadné data. Výhodou transformace kanálu, který je po definici kanál transformace, uložit kanálu, který má být použit testovací data.

Použít <xref:Microsoft.ML.Transforms.TextFeaturizer> převést `SentimentText` sloupec [číselné vektoru](../resources/glossary.md#numerical-feature-vector) volá `Features` používá algoritmus strojového učení. Jedná se o krok předběžného zpracování a snadné. Pomocí dalších komponent, které jsou k dispozici v ML.NET můžete povolit lepší výsledky obsahující váš model. Přidat `TextFeaturizer` do kanálu jako další řádek kódu:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Je objekt learner stromu rozhodnutí v tomto kanálu použijete. Podobně jako v kroku snadné, vyzkoušejte si různé inteligentních algoritmů k dispozici v ML.NET a změna jejich parametrů vede k jiné výsledky. Pro ladění, můžete nastavit [hyperparameters](../resources/glossary.md#hyperparameter) jako <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, a <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Tyto hyperparameters nastavují před nic ovlivňuje modelu a jsou specifické pro model. Slouží k vyladění rozhodovací strom pro výkon, takže vyšší hodnoty může mít negativní vliv na výkon.

Přidejte následující kód, který `Train` metody:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Trénování modelu

Trénování modelu, <xref:Microsoft.ML.PredictionModel%602>založená na datovou sadu, která má načíst a transformovat. `pipeline.Train<SentimentData, SentimentPrediction>()` trénovat kanálu (načítá data, železniční featurizer a learner). Experiment není spuštěn, dokud k tomu dojde.

Přidejte následující kód, který `Train` metody:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Uložte a vraťte se model se trénuje má použít pro hodnocení

V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET. Chcete-li uložit model do souboru ZIP a teprve potom se informuje, přidejte následující kód na další řádek v `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Model na konci vrátit `Train` metody.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když máte vytvořený a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro kontroly kvality a ověřování. V `Evaluate` metody, vytvořené v modelu `Train` předaný k vyhodnocení. Vytvořte `Evaluate` metoda, hned za `Train`, jako v následujícím kódu:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` Metoda spustí následující úlohy:

* Načte datovou sadu testů.
* Vytvoří binární Chyba při vyhodnocování.
* Vyhodnotí modelu a vytvoření metriky.
* Zobrazuje metriky.

Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.Data.TextLoader> Třídy načte nová datová sada testů s stejné schéma. Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality. Přidejte následující kód, který `Evaluate` metody:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Vypočítá metrik kvality pro objekt `PredictionModel` pomocí zadané datové sady. Pokud chcete zobrazit tyto metriky, přidejte Chyba při vyhodnocování jako na další řádek v `Evaluate` metodu s následujícím kódem:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> Obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení binární klasifikace. Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první. Přidejte následující kód:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metrik pro ověření modelu

Zobrazit metriky, sdílet výsledky a pak s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Předpověď výsledků dat testu s modelem

Vytvořte `Predict` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` Metoda spustí následující úlohy:

* Vytvoří testovací data.
* Předpovídá subjektivního hodnocení na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Přidat nějaké komentáře k otestování trénovaného modelu prognózy v `Predict` metody:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Teď, když máte model, vám pomůže, která předvídat pozitivní nebo negativní zabarvení komentář dat pomocí <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metody. Chcete-li získat predikcí, použijte `Predict` na nová data. Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné. Kanálu se synchronizuje během trénování a predikcí. Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Operacionalizace modelu: předpověď

Zobrazení `SentimentText` a odpovídající mínění předpovědí, aby bylo možné sdílet výsledky a příslušně na ně reagovat na ně. Tomu se říká operacionalizace, pomocí vrácená data jako součást zkontrolovala zásady. Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Před zobrazením předpokládané výsledky, kombinovat mínění a predikcí společně zobrazíte původním komentářem s jeho predikované mínění. Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda docílit, vedle proto přidejte tento kód:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Teď, když jste kombinovat `SentimentText` a `Sentiment` do třídy, můžete zobrazit výsledky pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metody:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

Protože odvozené názvy elementů řazené kolekce členů se, že je nová funkce v jazyce C# 7.1 a výchozí jazyková verze projektu C# 7.0, potřebujete změnit verzi jazyka C# 7.1 nebo novější.
To mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**. Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze). Vyberte **OK** tlačítko.

## <a name="results"></a>výsledky

Výsledky by měl vypadat přibližně takto. Při zpracování kanálu zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Ty se odebraly z následujících výsledků pro přehlednost.

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

Blahopřejeme! Teď jste úspěšně sestaven model strojového učení pro klasifikaci a předvídat zprávy mínění. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak:
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
