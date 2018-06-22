---
title: Použití ML.NET ve scénáři postojích analysis binární klasifikace
description: Zjistit, jak používat ML.NET ve scénáři binární klasifikace pochopit, jak pomocí postojích předpovědi proveďte příslušnou akci.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5194ec8b41304cc06848400607d5d76f288d42e6
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298276"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Kurz: Použití ML.NET ve scénáři postojích analysis binární klasifikace

> [!NOTE]
> Toto téma označuje ML.NET, který je aktuálně ve verzi Preview, a materiálů, mohou se měnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

V tomto kurzu ukázka znázorňuje pomocí ML.NET vytvoření klasifikátoru postojích prostřednictvím aplikace konzoly .NET Core pomocí jazyka C# v Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava dat
> * Vytvoření kanálu učení
> * Načíst třídění
> * Trénování modelu
> * Vyhodnocení modelu s jinou datové sady
> * Předpověď výstupy testovací data s modelem

## <a name="sentiment-analysis-sample-overview"></a>Přehled ukázkové postojích analýzy

Ukázka je konzolovou aplikaci, která používá ML.NET k natrénování modelu, který klasifikuje a předpovídá postojích jako kladné nebo záporné. Vyhodnotí také model s druhou datovou sadu pro analýzu kvality. Datové sady postojích jsou z WikiDetox projektu.

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15,6 nebo novější](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.

* [Karta data řádku detox Wikipedia oddělený soubor (wikiPedia-detox – 250řádku data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Karta testu řádku detox Wikipedia oddělený soubor (wikipedia-detox – 250řádku test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

## <a name="machine-learning-workflow"></a>Pracovní postup Machine learning

V tomto kurzu následuje machine learning pracovního postupu, který umožňuje proces přesunout normálním způsobem.

Fáze pracovního postupu jsou následující:

1. **Porozumět problému**
2. **Zpracování příjmu dat**
3. **Předběžné zpracování dat a konstruování**
4. **Trénování a předpovědi modelu**
5. **Vyhodnocení modelu**
6. **Model operationalization**

### <a name="understand-the-problem"></a>Pochopení problému

Nejdřív musíte pochopit problém, takže lze ho rozdělit na části, které podporují vytváření a cvičení modelu. Pozastavení problém dolů k předvídání a vyhodnoťte výsledky.

Problém pro účely tohoto kurzu je pochopit příchozí postojích webu komentář k proveďte příslušnou akci.

Problém můžete rozdělit postojích text a postojích hodnotu pro data chcete trénování modelu s a předpokládaných postojích hodnotu, která můžete vyhodnotit a pak použít provozně.

Bude potřeba **určit** postojích, který vám pomůže s strojového učení výběr úkolů.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

S tímto problémem znáte tyto skutečnosti:

Cvičení data: komentáře webu může být kladná nebo záporná (**postojích**).
Předpověď **postojích** nové komentáře webu, kladná nebo záporná, například v následujících příkladech:

* Nepoužívejte přidávání nesmysl do Wikipedia.
* Je nejvhodnější a by mělo být uvedeno článek, který.

Úloha klasifikace machine learning je nejvhodnější pro tento scénář.

### <a name="about-the-classification-task"></a>O úloze klasifikace

Klasifikace je strojové učení úkol, který používá data **určit** kategorie, typu nebo třídy řádek dat nebo položky. Například můžete použít klasifikaci pro:

* Identifikujte postojích jako kladné nebo záporné.
* E-mailu klasifikujte jako nevyžádané pošty, nevyžádanou poštou nebo funkční.
* Určete, zda je cancerous ukázka pacientova testovacího prostředí.
* Rozdělit kategorií podle jejich tendenci reagovat na prodejní kampaně.

Klasifikace úlohy jsou často jednu z následujících typů:

* Binární: buď A nebo B.
* Multiclass: více kategorií, které můžete funkci lze použít jeden model.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Otevřete Visual Studio 2017. Vyberte **soubor** > **nový** > **projektu** z řádku nabídek. V *nový projekt** dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu. Vyberte **konzolové aplikace (.NET Core)** šablona projektu. V **název** textového pole zadejte "SentimentAnalysis" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář s názvem *Data* ve vašem projektu a uložte si své soubory datové sady:

    V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Nainstalujte **balíček NuGet Microsoft.ML**:

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte "nuget.org" jako zdroj balíčku, vyberte kartu Procházet, vyhledávat **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **zobrazení náhledu změn** dialogové okno a potom vyberte **souhlasím** na tlačítko **přijetí licence** dialogové okno Pokud jste souhlas s licenčními podmínkami pro balíčky uvedené.

### <a name="prepare-your-data"></a>Příprava dat

1. Stáhnout [WikiPedia detox – 250řádku data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) a [wikipedia-detox – 250řádku test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data nastaví a uložte je do *Data* složku dříve vytvořili. První datovou sadu nastaví model strojového učení a druhý je možné zjistit, jak přesný je váš model.

2. V Průzkumníku řešení klikněte pravým tlačítkem na každý z \*TSV, soubory a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu **kopírovat do výstupního adresáře** k **vždy**.

### <a name="create-classes-and-define-paths"></a>Vytváření tříd a definovat cesty

Přidejte následující další `using` příkazů do horní části *Program.cs* souboru:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Potřebujete vytvořit tři globální proměnné, do kterých cestu k naposledy stažené soubory:

* `_dataPath` nemá cestu k datové sadě použity při cvičení modelu.
* `_testDataPath` nemá cestu k datové sadě používají k vyhodnocení modelu.
* `_modelPath` má cestu k uložení naučeného modelu.

Přidejte následující kód řádku vpravo nahoře `Main` metoda k určení naposledy stažené soubory:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Budete muset vytvořit některé třídy pro vstupní data a předpovědi. Přidejte novou třídu do projektu:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.

1. V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *SentimentData.cs*. Pak vyberte **přidat** tlačítko.

    *SentimentData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `SentimentData` a `SentimentPrediction`, na *SentimentData.cs* souboru:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` je třída vstupní datové sady a `float` (`Sentiment`), má hodnotu pro postojích kladné nebo záporné a řetězec pro komentář (`SentimentText`). Mají obě pole `Column` atributy připojené k nim. Popisuje pořadí každé pole v datovém souboru a který je tento atribut `Label` pole. `SentimentPrediction` Třída slouží k předpovědi po modelu má cvičena. Obsahuje jednu logickou hodnotu (`Sentiment`) a `PredictedLabel` `ColumnName` atribut. `Label` Se používá k vytvoření a cvičení modelu a jeho také používá s druhou datovou sadu k vyhodnocení modelu. `PredictedLabel` Se používá během předpovědi a vyhodnocení. Zkušební verze se používají vstup s Cvičná data, předpovězené hodnoty a modelu.

V *Program.cs* změňte `Main` podpis metody nahrazením `void` s `async Task`, jako v následujícím příkladu:

```csharp
static async Task Main(string[] args) 
{

}
```

Přidání `async` k `Main` s <xref:System.Threading.Tasks.Task> návratový typ, protože ukládání modelu do souboru zip později, a program musí počkat, až po dokončení této úlohy externí.

> [!NOTE]
> *Asynchronní hlavní* metoda umožňuje používat `await` ve vaší `Main` metoda. Další informace najdete v tématu [asynchronní hlavní](../../../docs/csharp/programming-guide/main-and-command-args/index.md) v Průvodci programovacího jazyka C#.

Nahraďte `Console.WriteLine("Hello World!")` řádku v následujícím kódem `Main` metoda:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` Metoda provede následující úlohy:

* Načte nebo ingestuje data.
* Upraví a featurizes data.
* Nastaví model.
* Předpovídá postojích na základě dat testu.

Vytvořte `Train` metoda, hned za `Main` metodu, pomocí následujícího kódu:

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a>Zpracování příjmu dat

Inicializuje novou instanci třídy <xref:Microsoft.ML.LearningPipeline> , bude obsahovat načítání dat, zpracování dat nebo featurization a modelu. Přidejte následující kód jako první řádek `Train` metoda:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.Data.TextLoader> Objekt představuje první část kanálu a načte data souboru školení.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Předběžné zpracování dat a konstruování

Předběžné zpracování a vyčištění dat jsou důležité úkoly, které udělat předtím, než datové sady je využívány efektivně pro machine learning. Nezpracovaná data, je často aktivní nebo nespolehlivé a může být chybějící hodnoty. Pomocí dat bez těchto úloh modelování může vytvářet zavádějící výsledky. ML. Kanály transformace na NET umožňují vytvořit vlastní sadu transformace, které se použijí pro vaše data před cvičení nebo testování. Primárním účelem transformací je data featurization. Transformace kanálu výhod je, že po definice transformace kanálu, uložení kanálu a použijte ji k testování data.

Použít <xref:Microsoft.ML.Transforms.TextFeaturizer> převést `SentimentText` sloupce do [číselné vektoru](../resources/glossary.md#numerical-feature-vector) názvem `Features` používá algoritmus machine learning. Toto je předběžné zpracování nebo featurization krok. Pomocí další součásti, které jsou k dispozici v ML.NET můžete povolit lepší výsledky se svým modelem. Přidat `TextFeaturizer` do kanálu jako dalším řádku kódu:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Vyberte algoritmus učení

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Objekt je student stromu rozhodnutí budete používat v kanálu. Podobně jako v kroku featurization vyzkoušení různých inteligentních algoritmů k dispozici v ML.NET a změna jejich parametrů vede k odlišným výsledkům. Pro ladění, můžete nastavit [hyperparameters](../resources/glossary.md#hyperparameter) jako <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, a <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Tyto hyperparameters jsou nastavené před nic ovlivňuje modelu a jsou specifické pro model. Slouží k vyladění rozhodovací strom pro výkon, takže vyšší hodnoty může mít negativní vliv na výkon.

Přidejte následující kód, který `Train` metoda:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Trénování modelu

Trénování modelu, <xref:Microsoft.ML.PredictionModel%602>, na základě sady dat, která byla načtena a transformovat. `pipeline.Train<SentimentData, SentimentPrediction>()` Nastaví kanál (načte data, vlaky featurizer a Student). Experiment není provést, dokud k tomu dojde.

Přidejte následující kód, který `Train` metoda:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Uložte a vraťte se Trénink modelu pro vyhodnocení

V tuto chvíli máte model, který se dá integrovat do některé z vašich aplikací .NET existující nebo nové. Váš model uložit do souboru ZIP a před vrácením, přidejte následující kód na další řádek v `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Vrátí modelu na konci `Train` metoda.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Teď, když jste vytvořili a natrénovali model, musíte vyhodnotit s jinou datovou sadu pro zajištění kvality a ověření. V `Evaluate` metoda, vytvořené v modelu `Train` je předaná k vyhodnocení. Vytvořte `Evaluate` metoda, hned za `Train`, jako v následujícím kódem:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` Metoda provede následující úlohy:

* Načte testovací datové sady.
* Vytvoří binární vyhodnocování.
* Vyhodnotí modelu a vytvoření metriky.
* Zobrazí metriky.

Přidejte volání do nové metody z `Main` metoda, v rámci `Train` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.Data.TextLoader> Třída načte nová datová sada testů se stejným schématem. Použití této datové sady pro kontrolu kvality modelu můžete vyhodnotit. Přidejte následující kód, který `Evaluate` metoda:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Vypočítá metriky kvality pro objekt `PredictionModel` pomocí zadané sady dat. Pokud chcete zobrazit tyto metriky, přidejte vyhodnocování jako na další řádek v `Evaluate` metoda následujícím kódem:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> Obsahuje metriky celkového vypočítávají podle binární klasifikace vyhodnocovací filtry. Pokud chcete zobrazit tyto k určení kvality modelu, potřebujete získat metriky první. Přidejte následující kód:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Zobrazení metriky pro ověření modelu

Zobrazování metrik, sdílet výsledky a potom s nimi pracovat, použijte následující kód:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Předpověď výstupy testovací data s modelem

Vytvořte `Predict` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` Metoda provede následující úlohy:

* Vytvoří testovací data.
* Předpovídá postojích na základě dat testu.
* Kombinuje testovací data a předpovědi pro vytváření sestav.
* Zobrazí predikované výsledky.

Přidejte volání do nové metody z `Main` metoda, v rámci `Evaluate` volání metody, pomocí následujícího kódu:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Přidání některé komentářů k testování pro cvičný model predikce v `Predict` metoda:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Teď, když máte model, můžete pomocí nich předpovědi kladné a záporné postojích komentář dat pomocí <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> metoda. Chcete-li získat předpovědi, použijte `Predict` na nová data. Upozorňujeme, že se vstupní data je řetězec a tento model zahrnuje featurization. Vaše kanálu se synchronizuje během školení a předpovědi. Neměly napsat kód předběžného zpracování nebo featurization speciálně pro předpovědi a rozhraní API stejné postará batch a jednorázové předpovědi.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Model operationalization: předpovědi

Zobrazení `SentimentText` a odpovídající postojích předpovědi, aby bylo možné sdílet výsledky a s nimi pracovat odpovídajícím způsobem. Tomu se říká operationalization, pomocí vrácená data v rámci provozní zásady. Vytvořit hlavičku pro výsledky pomocí následujících <xref:System.Console.WriteLine?displayProperty=nameWithType> kódu:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Před zobrazením předpokládaných výsledky, zkombinovat postojích předpovědi společně zobrazíte původní komentář s jeho předpokládaných postojích. Následující kód používá <xref:System.Linq.Enumerable.Zip%2A> metoda toho docílit, další proto přidejte tento kód:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Teď, když jste kombinaci `SentimentText` a `Sentiment` do tříd, můžete zobrazit pomocí <xref:System.Console.WriteLine?displayProperty=nameWithType> metoda:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

Protože odvodit, že jsou názvy elementu řazené kolekce členů, že je nová funkce v C# 7.1 a výchozí jazykovou verzi projektu C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.
To lze provést, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**. Vyberte **sestavení** a vyberte **Upřesnit** tlačítko. V rozevírací nabídce, a vyberte **C# 7.1** (nebo vyšší verze). Vyberte **OK** tlačítko.

## <a name="results"></a>Výsledky

Výsledky by měl vypadat přibližně takto. Jako kanálu zpracovává, zobrazí zprávy. Může se zobrazit upozornění nebo zpracování zpráv. Tyto byly odebrány z následující výsledky pro přehlednost.

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

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro klasifikaci a predikci postojích zprávy. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) úložiště.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se dozvěděli, jak:
> [!div class="checklist"]
> * Pochopení problému
> * Vyberte úlohu odpovídající machine learning
> * Příprava dat
> * Vytvoření kanálu učení
> * Načíst třídění
> * Trénování modelu
> * Vyhodnocení modelu s jinou datové sady
> * Předpověď výstupy testovací data s modelem

Přechodu na další informace v dalším kurzu
> [!div class="nextstepaction"]
> [Předpověď taxíkem tarif](taxi-fare.md)
