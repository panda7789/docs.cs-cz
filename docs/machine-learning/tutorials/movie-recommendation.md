---
title: 'Kurz: Postavit film doporučující - matice faktorizace'
description: Tento kurz ukazuje, jak vytvořit doporučujefilm s ML.NET v aplikaci konzoly .NET Core. Kroky používají C# a Visual Studio 2019.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a1d7ef6226580fd3172b5714f9d7358298ba6668
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607994"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Kurz: Vytvořte film doporučující pomocí matice faktorizace s ML.NET

Tento kurz ukazuje, jak vytvořit doporučujefilm s ML.NET v aplikaci konzoly .NET Core. Kroky používají C# a Visual Studio 2019.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Výběr algoritmu strojového učení
> * Příprava a načtení dat
> * Sestavení a trénování modelu
> * Vyhodnocení modelu
> * Nasazení a využití modelu

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)

## <a name="machine-learning-workflow"></a>Pracovní postup strojového učení

K dokončení úkolu a všech dalších ML.NET úkolu použijete následující kroky:

1. [Načtení dat](#load-your-data)
2. [Sestavte a trénujte svůj model](#build-and-train-your-model)
3. [Vyhodnocení modelu](#evaluate-your-model)
4. [Použití modelu](#use-your-model)

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".

## <a name="select-the-appropriate-machine-learning-task"></a>Výběr příslušného úkolu strojového učení

Existuje několik způsobů, jak přistupovat k problémům s doporučeními, jako je například doporučení seznamu filmů nebo doporučení seznamu souvisejících produktů, ale v tomto případě předevíte, jaké hodnocení (1-5) uživatel poskytne určitému filmu, a doporučí tento film, pokud je vyšší než definovaná prahová hodnota (čím vyšší je hodnocení, tím vyšší je pravděpodobnost, že uživatel bude mít rád konkrétní film).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete sadu Visual Studio 2017. Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.** V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core.** Pak vyberte šablonu projektu **Konzola Aplikace (.NET Core).** Do textového pole **Název** zadejte "MovieRecommender" a pak vyberte tlačítko **OK.**

2. Vytvořte adresář s názvem *Data* v projektu pro uložení datové sady:

    V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte enter.

3. Nainstalujte **balíčky NuGet Microsoft.ML** a **Microsoft.ML.Recommender:**

    V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet,** vyhledejte **Microsoft.ML**, vyberte balíček v seznamu a vyberte tlačítko **Instalovat.** V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky. Opakujte tento postup pro **Microsoft.ML.Recommender**.

4. V horní `using` části *Program.cs* souboru přidejte následující příkazy:

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Stažení dat

1. Stáhněte si dvě datové sady a uložte je do dříve vytvořené *datové* složky:

   * Klikněte pravým tlačítkem myši na [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte "Uložit odkaz (nebo cíl) Jako ..."
   * Klikněte pravým tlačítkem myši na [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte "Uložit odkaz (nebo cíl) jako..."

     Ujistěte se, \*že soubory .csv uložíte do složky *Data,* nebo je po uložení jinde přesuňte soubory \*.csv do složky *Data.*

2. V Průzkumníku řešení klepněte \*pravým tlačítkem myši na jednotlivé soubory .csv a vyberte **příkaz Vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

   ![GIF uživatele, který vybírá kopii, pokud je novější ve VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Načtení dat

Prvním krokem v procesu ML.NET je připravit a načíst data školení a testování modelu.

Data hodnocení doporučení jsou `Train` `Test` rozdělena do datových sad a jsou rozdělena. Data `Train` se používají k přizpůsobení modelu. Data `Test` se používá k předpovědi s trénovaný model a vyhodnotit výkon modelu. Je běžné mít 80/20 rozdělit `Train` s `Test` a data.

Níže je náhled dat z \*vašich souborů .csv:

![Snímek obrazovky s náhledem datové sady CVS](./media/movie-recommendation/csv-file-dataset-preview.png)

V \*souborech .csv jsou čtyři sloupce:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Ve strojovém učení se sloupce, které se používají k vytvoření předpovědi, nazývají [Funkce](../resources/glossary.md#feature)a sloupec s vrácenou predikcí se nazývá [Label](../resources/glossary.md#label).

Chcete předpovědět hodnocení filmů, takže sloupec `Label`hodnocení je . Další tři sloupce `userId` `movieId`, `timestamp` , `Features` a všechny `Label`se používají k předvídání .

| Funkce      | Popisek         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Je na vás, rozhodnout, které `Features` se `Label`používají k předvídání . Můžete také použít metody, jako [je důležitost funkce permutace,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) které vám pomohou s výběrem toho nejlepšího `Features`.

V takovém případě byste `timestamp` měli sloupec `Feature` odstranit jako a protože časové razítko ve skutečnosti nemá vliv na to, jak uživatel hodnotí daný film, a proto by nepřispělk přesnější predikci:

| Funkce      | Popisek         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Dále je nutné definovat strukturu dat pro vstupní třídu.

Přidání nové třídy do projektu:

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a potom vyberte **přidat > novou položku**.

2. V **dialogovém okně Přidat novou položku**vyberte **Třídu** a změňte pole **Název** na *MovieRatingData.cs*. Potom vyberte tlačítko **Přidat.**

Soubor *MovieRatingData.cs* se otevře v editoru kódu. Na začátek `using` *MovieRatingData.cs*přidejte následující příkaz :

```csharp
using Microsoft.ML.Data;
```

Vytvořte třídu volanou `MovieRating` odebráním existující definice třídy a přidáním následujícího kódu v *MovieRatingData.cs*:

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`určuje třídu vstupních dat. Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny. Sloupce `userId` `movieId` a jsou `Features` vaše (vstupy, které poskytnete `Label`modelu předpovědět ) `Label` a sloupec hodnocení je ten, který budete předpovídat (výstup modelu).

Vytvořte jinou třídu , `MovieRatingPrediction`chcete-li reprezentovat `MovieRating` předpokládané výsledky přidáním následujícího kódu za třídu v *MovieRatingData.cs*:

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

V *Program.cs*nahraďte `Console.WriteLine("Hello World!")` uvnitř `Main()`následující kód :

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně, v `DBContext` entity frameworku.

Po `Main()`, vytvořte `LoadData()`metodu s názvem :

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Tato metoda vám dá chybu, dokud nepřidáte příkaz return v následujících krocích.

Inicializovat proměnné datové cesty, načíst \*data ze souborů .csv a vrátit data `Train` a `Test` jako `IDataView` objekty `LoadData()`přidáním následujícího jako následující řádek kódu v :

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových). Data lze načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu. `IDataView`

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru. Přebírá proměnné cesty dat a vrátí `IDataView`. V takovém případě zadáte cestu `Test` pro `Train` vaše soubory a soubory a označíte záhlaví textového souboru (aby bylo možné správně používat názvy sloupců) a oddělovač dat znaků čárky (výchozí oddělovač je karta).

Přidejte do metody `Main()` následující kód `LoadData()` pro volání `Train` `Test` metody a vrácení dat a:

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Sestavte a trénujte svůj model

Existují tři hlavní pojmy v ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer)a [Estimators](../resources/glossary.md#estimator).

Algoritmy školení strojového učení vyžadují data v určitém formátu. `Transformers`se používají k transformaci tabulkových dat do kompatibilního formátu.

![Diagram toku dat transformátoru.](./media/movie-recommendation/data-transformer-transformed.png)

`Transformers` Vytvořením souboru `Estimators`ML.NET vytvořit . `Estimators`přijímat údaje a `Transformers`vracet .

![Diagram toku dat odhadu.](./media/movie-recommendation/data-estimator-transformer.png)

Algoritmus školení doporučení, který budete používat pro `Estimator`školení modelu je příkladem .

Vytvořte `Estimator` následující kroky:

Vytvořte `BuildAndTrainModel()` metodu, `LoadData()` hned za metodou, pomocí následujícího kódu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Tato metoda vám dá chybu, dokud nepřidáte příkaz return v následujících krocích.

Definujte transformace dat přidáním následujícího kódu do `BuildAndTrainModel()`aplikace :

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

`userId` Vzhledem `movieId` k tomu, a představují uživatele a názvy filmů, nikoli skutečné hodnoty, použijete `Feature` metodu [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) k transformaci každého `userId` do `movieId` sloupce typu číselného klíče (formát přijatý algoritmy doporučení) a přidáte je jako nové sloupce datové sady:

| userId | movieId | Popisek | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | filmKlíč1 |
| 1 | 3 | 4 | userKey1 | filmKey2 |
| 1 | 6 | 4 | userKey1 | filmKlíč3 |

Zvolte algoritmus strojového učení a přidejte jej k definicím transformace `BuildAndTrainModel()`dat přidáním následujícího jako následující řádek kódu v :

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je vaše doporučení školení algoritmus.  [Faktorizace matice](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je běžný přístup k doporučení, pokud máte data o tom, jak uživatelé hodnotili produkty v minulosti, což je případ datových sad v tomto kurzu. Existují další algoritmy doporučení, pokud máte k dispozici různá data (další informace naleznete v části [Další algoritmy doporučení](#other-recommendation-algorithms) níže).

V tomto případě `Matrix Factorization` algoritmus používá metodu s názvem "kolaborativní filtrování", která předpokládá, že pokud uživatel 1 má stejný názor jako uživatel 2 na určitý problém, pak uživatel 1 je pravděpodobnější, že se bude cítit stejným způsobem jako uživatel 2 o jiném problému.

Například pokud uživatel 1 a uživatel 2 hodnotí filmy podobně, pak uživatel 2 s větší pravděpodobností užije film, který uživatel 1 sledoval a vysoce hodnotil:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Uživatel 1 | Sledoval a líbil film | Sledoval a líbil film | Sledoval a líbil film |
| Uživatel 2 | Sledoval a líbil film | Sledoval a líbil film | Nesledoval - DOPORUČIT film |

Trenér `Matrix Factorization` má několik možností , o [kterých](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)si můžete přečíst více v části [Hyperparameters algoritmus](#algorithm-hyperparameters) níže.

Připevněte model `Train` k datům a vraťte trénovaný model `BuildAndTrainModel()` přidáním následujícího jako následující řádek kódu v metodě:

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Metoda Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trénuje váš model s poskytnutou trénovací datovou sadou. Technicky provede `Estimator` definice transformací dat a použitím trénování a vrátí zpět trénovaný model, což je . `Transformer`

Přidejte následující jako další řádek `Main()` kódu v `BuildAndTrainModel()` metodě volat metodu a vrátit trénovaný model:

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Vyhodnocení modelu

Po trénování modelu použijte testovací data k vyhodnocení toho, jak si model vede.

Vytvořte `EvaluateModel()` metodu, `BuildAndTrainModel()` hned za metodou, pomocí následujícího kódu:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Transformace `Test` dat přidáním následujícího `EvaluateModel()`kódu do aplikace :

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) Metoda umožňuje předpovědi pro více zapředpokladu vstupní řádky testovací datové sady.

Vyhodnoťte model přidáním následujícího `EvaluateModel()` jako následující řádek kódu v metodě:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Jakmile máte předpověď nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda vyhodnotí model, který porovnává předpovídané hodnoty s aktuální `Labels` v testovací datové sady a vrátí metriky o tom, jak model funguje.

Vytiskněte metriky hodnocení do konzoly přidáním následujícího `EvaluateModel()` jako následující řádek kódu v metodě:

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

Přidejte následující jako další řádek `Main()` kódu v `EvaluateModel()` metodě pro volání metody:

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Výstup zatím by měl vypadat podobně jako následující text:

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

V tomto výstupu je 20 iterací. V každé iteraci se míra chyby sníží a sblíží blíže a blíže k 0.

(RMS `root of mean squared error` nebo RMSE) se používá k měření rozdílů mezi modelem předpovídaných hodnot a sledovaných hodnot testovací datové sady. Technicky je to druhá odmocnina průměru čtverců chyb. Čím nižší je, tím lepší je model.

`R Squared`označuje, jak dobře data odpovídají modelu. Rozsah od 0 do 1. Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu. Hodnota 1 znamená, že model přesně odpovídá datům. Chcete, `R Squared` aby vaše skóre bylo co nejblíže k 1, jak je to možné.

Vytváření úspěšných modelů je iterativní proces. Tento model má počáteční nižší kvalitu jako kurz používá malé datové sady poskytovat rychlé školení modelu. Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit vylepšit tím, že poskytuje větší trénovací datové sady nebo výběrem různých trénovacích algoritmů s různými hyperparametry pro každý algoritmus. Další informace najdete v části [Vylepšete model](#improve-your-model) níže.

## <a name="use-your-model"></a>Použití modelu

Nyní můžete použít trénovaný model k předpovědi na nová data.

Vytvořte `UseModelForSinglePrediction()` metodu, `EvaluateModel()` hned za metodou, pomocí následujícího kódu:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Pomocí `PredictionEngine` tohoto slouží k předvídání `UseModelForSinglePrediction()`hodnocení přidáním následujícího kódu do :

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken. Je přijatelné používat v jednovláknových nebo prototypových prostředích. Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci. V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.

Vytvořte instanci volané `MovieRating` `testInput` a předat jej Prediction Engine přidáním následující `UseModelForSinglePrediction()` jako další řádky kódu v metodě:

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jeden sloupec dat.

Potom můžete použít `Score`, nebo předpokládané hodnocení, k určení, zda chcete doporučit film s movieId 10 pro uživatele 6. Čím vyšší `Score`je , tím vyšší je pravděpodobnost, že se uživateli bude určitý film líbit. V tomto případě řekněme, že doporučujete filmy s předpokládaným hodnocením > 3.5.

Chcete-li vytisknout výsledky, přidejte následující jako `UseModelForSinglePrediction()` další řádky kódu v metodě:

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

Přidejte následující jako další řádek `Main()` kódu v `UseModelForSinglePrediction()` metodě pro volání metody:

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Výstup této metody by měl vypadat podobně jako následující text:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Uložení modelu

Chcete-li použít model k předpovědi v aplikacích koncových uživatelů, musíte nejprve uložit model.

Vytvořte `SaveModel()` metodu, `UseModelForSinglePrediction()` hned za metodou, pomocí následujícího kódu:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Uložte trénovaný model přidáním následujícího kódu v metodě: `SaveModel()`

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Tato metoda uloží trénovaný model do souboru ZIP (ve složce "Data"), který pak lze použít v jiných aplikacích .NET k předpovědi.

Přidejte následující jako další řádek `Main()` kódu v `SaveModel()` metodě pro volání metody:

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Použití uloženého modelu

Po uložení trénovaného modelu můžete model využívat v různých prostředích. Informace o tom, jak zprovoznit trénovaný model strojového učení v aplikacích, najdete v tématu [Ukládání a načítání trénovaného modelu.](../how-to-guides/save-load-machine-learning-models-ml-net.md)

## <a name="results"></a>Výsledky

Po provedení výše uvedených kroků spusťte konzolovou aplikaci (Ctrl + F5). Vaše výsledky z výše uvedené predikce by měly být podobné následujícímu. Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

Blahopřejeme! Nyní jste úspěšně vytvořili model strojového učení pro doporučování filmů. Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)

## <a name="improve-your-model"></a>Vylepšení modelu

Existuje několik způsobů, jak můžete zlepšit výkon modelu, takže můžete získat přesnější předpovědi.

### <a name="data"></a>Data

Přidání dalších trénovacích dat, která mají dostatek vzorků pro každého uživatele a id filmu, může pomoci zlepšit kvalitu modelu doporučení.

[Křížové ověření](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) je technika pro vyhodnocení modelů, které náhodně rozdělí data do podmnožiny (namísto extrahování testovacích dat z datové sady, jako jste to udělali v tomto kurzu) a bere některé skupiny jako data vlaku a některé skupiny jako testovací data. Tato metoda překonává rozdělení vlakového testu z hlediska kvality modelu.

### <a name="features"></a>Funkce

V tomto kurzu použijete `Features` pouze`user id` `movie id`tři `rating`( , , a ), které jsou poskytovány datové sady.

I když je to dobrý začátek, ve skutečnosti `Features` můžete chtít přidat další atributy nebo (například věk, pohlaví, geografické umístění atd.), pokud jsou zahrnuty v datové sadě. Přidání relevantnější `Features` může pomoci zlepšit výkon modelu doporučení.

Pokud si nejste `Features` jisti, které by mohly být pro váš úkol strojového učení nejdůležitější, můžete také využít funkce výpočtu (FCC) a [permutace funkce význam](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), který ML.NET poskytuje objevit nejvlivnější `Features`.

### <a name="algorithm-hyperparameters"></a>Hyperparametry algoritmu

Zatímco ML.NET poskytuje dobré výchozí trénovací algoritmy, můžete dále doladit výkon změnou [hyperparametry](../resources/glossary.md#hyperparameter)algoritmu .

Pro `Matrix Factorization`, můžete experimentovat s hyperparameters, jako je [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) chcete-li zjistit, zda to dává lepší výsledky.

Například v tomto kurzu jsou možnosti algoritmu:

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a>Další doporučující algoritmy

Algoritmus faktorizace matice s kolaborativním filtrováním je pouze jedním přístupem pro provádění doporučení filmu. V mnoha případech nemusí být data hodnocení k dispozici a historie filmů je k dispozici pouze od uživatelů. V ostatních případech můžete mít více než jen údaje o hodnocení uživatele.

| Algoritmus       | Scénář           | Ukázka  |
| ------------- |:-------------:| -----:|
| Faktorizace matice jedné třídy | Použijte tuto položku, pokud máte pouze userId a movieId. Tento styl doporučení je založen na scénáři koupě nebo produktech často zakoupených společně, což znamená, že zákazníkům doporučí sadu produktů na základě vlastní historie nákupních objednávek. | [>Vyzkoušejte si to](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Faktorizační stroje s vědomi terénu | Použijte k doporučení, pokud máte více funkcí nad rámec userId, productId a hodnocení (například popis produktu nebo cena produktu). Tato metoda také používá přístup kolaborativní filtrování. | [>Vyzkoušejte si to](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Nový uživatelský scénář

Jedním z běžných problémů při filtrování spolupráce je problém studeného startu, který je, když máte nového uživatele bez předchozích dat, ze kterých by bylo možné vyvodit závěry. Tento problém je často vyřešen tím, že žádá nové uživatele, aby vytvořili profil a například hodnotili filmy, které viděli v minulosti. Zatímco tato metoda klade určitou zátěž pro uživatele, poskytuje některá počáteční data pro nové uživatele bez historie hodnocení.

## <a name="resources"></a>Zdroje a prostředky

Data použitá v tomto kurzu jsou odvozena z [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:

> [!div class="checklist"]
>
> * Výběr algoritmu strojového učení
> * Příprava a načtení dat
> * Sestavení a trénování modelu
> * Vyhodnocení modelu
> * Nasazení a využití modelu

Přejdete k dalšímu kurzu, abyste se dozvěděli více
> [!div class="nextstepaction"]
> [Analýza mínění](sentiment-analysis.md)
