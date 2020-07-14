---
title: 'Kurz: vytvoření faktoru pro vystavení filmů – vytváření matic'
description: V tomto kurzu se dozvíte, jak v konzolové aplikaci .NET Core sestavit doporučení pro film pomocí ML.NET. Postup používá jazyk C# a Visual Studio 2019.
author: briacht
ms.date: 06/30/2020
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 39c4aeef0b02a6bf47d78e6bf53cd42b4f592946
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282096"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Kurz: sestavení doporučení pro film pomocí vytváření matic s ML.NET

V tomto kurzu se dozvíte, jak v konzolové aplikaci .NET Core sestavit doporučení pro film pomocí ML.NET. Postup používá jazyk C# a Visual Studio 2019.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> * Vyberte algoritmus strojového učení.
> * Příprava a načtení dat
> * Sestavování a výuka modelu
> * Vyhodnocení modelu
> * Nasazení a využití modelu

Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .

## <a name="machine-learning-workflow"></a>Pracovní postup strojového učení

Pomocí následujících kroků můžete provést úlohu a také všechny další úlohy ML.NET:

1. [Načtení dat](#load-your-data)
2. [Sestavování a výuka modelu](#build-and-train-your-model)
3. [Vyhodnocení modelu](#evaluate-your-model)
4. [Použití modelu](#use-your-model)

## <a name="prerequisites"></a>Požadavky

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo visual Studio 2017 verze 15,6 nebo novější s nainstalovanou úlohou nasazení .NET Core pro různé platformy.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte příslušný úkol strojového učení.

Existuje několik způsobů, jak získat přístup k potížím s doporučeními, jako je například doporučený seznam filmů nebo doporučený seznam souvisejících produktů, ale v tomto případě budete předpovídat, jaké hodnocení (1-5) bude uživatel podávat konkrétnímu videu, a doporučit tento film, pokud je vyšší než definovaná prahová hodnota (čím vyšší je pravděpodobnost, že uživatel míru určitý film).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete sadu Visual Studio 2017. Z řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt** . V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core** . Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** . Do textového pole **název** zadejte "MovieRecommender" a pak vyberte tlačítko **OK** .

2. Vytvořte v projektu adresář s názvem *data* pro uložení datové sady:

    V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat**  >  **novou složku**. Zadejte "data" a stiskněte ENTER.

3. Nainstalujte balíčky NuGet **Microsoft.ml** a **Microsoft. ml. doporučování** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**. Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** . Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** . Opakujte tento postup pro **Microsoft. ml. doporučuje**se.

4. Do `using` horní části souboru *program.cs* přidejte následující příkazy:

    [!code-csharp[UsingStatements](./snippets/movie-recommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Stažení vašich dat

1. Stáhněte dvě datové sady a uložte je do složky *dat* , kterou jste vytvořili dříve:

   * Klikněte pravým tlačítkem na [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte Uložit odkaz (nebo cíl) jako...
   * Klikněte pravým tlačítkem na [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte Uložit odkaz (nebo cíl) jako...

     Ujistěte se \* , že soubory. csv ukládáte do složky *data* nebo když je uložíte jinam, přesuňte \* soubory. CSV do složky *data* .

2. V Průzkumník řešení klikněte pravým tlačítkem na každý ze \* souborů. csv a vyberte **vlastnosti**. V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

   ![GIF uživatele, který vybírá kopii, pokud je novější v VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Načtení dat

Prvním krokem v procesu ML.NET je příprava a načtení modelu školení a testování dat.

Data hodnocení doporučení jsou rozdělena do `Train` datových `Test` sad a. `Train`Data se používají k přizpůsobení modelu. `Test`Data se používají k zajištění předpovědiy s vyškolenou modelem a vyhodnocení výkonu modelu. Je běžné mít 80/20 rozdělení s `Train` `Test` daty a.

Níže je zobrazená ukázka dat z vašich \* souborů. CSV:

![Snímek obrazovky s náhledem datové sady CVS](./media/movie-recommendation/csv-file-dataset-preview.png)

V \* souborech. CSV jsou čtyři sloupce:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Ve službě Machine Learning se ve sloupcích, které se používají k vytvoření předpovědi, říká [funkce](../resources/glossary.md#feature)a sloupec s vrácenou předpověď se nazývá [popisek](../resources/glossary.md#label).

Chcete odhadnout hodnocení filmů, takže sloupec hodnocení je `Label` . Další tři sloupce,, `userId` `movieId` a `timestamp` jsou `Features` použity k předpovědi `Label` .

| Funkce      | Popisek         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Je až na to, abyste se rozhodli, které `Features` se použijí k předpovědi `Label` . Můžete také použít metody, jako je například [funkce permutace důležitost](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) , pro usnadnění výběru nejlepšího `Features` .

V takovém případě byste měli sloupec eliminovat, `timestamp` `Feature` protože časové razítko ve skutečnosti neovlivňuje způsob, jakým se uživatel podílí na videu, a proto by nebyl přispívat k zajištění přesnější předpovědi:

| Funkce      | Popisek         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Dále musíte definovat datovou strukturu pro vstupní třídu.

Přidejte do projektu novou třídu:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > nová položka**.

2. V **dialogovém okně Přidat novou položku**vyberte **třída** a změňte pole **název** na *MovieRatingData.cs*. Pak vyberte tlačítko **Přidat** .

V editoru kódu se otevře soubor *MovieRatingData.cs* . `using`Do horní části *MovieRatingData.cs*přidejte následující příkaz:

```csharp
using Microsoft.ML.Data;
```

Vytvořte třídu s názvem `MovieRating` odebráním existující definice třídy a přidáním následujícího kódu do *MovieRatingData.cs*:

[!code-csharp[MovieRatingClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`Určuje vstupní datovou třídu. Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny. `userId`Sloupce a `movieId` jsou vaše `Features` (vstupy, které model poskytnete k předpovídání `Label` ), a sloupec hodnocení je `Label` , který budete předpovídat (výstup modelu).

Vytvořte další třídu, `MovieRatingPrediction` pro reprezentaci předpokládaných výsledků přidáním následujícího kódu za `MovieRating` třídu v *MovieRatingData.cs*:

[!code-csharp[PredictionClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

V *program.cs*nahraďte `Console.WriteLine("Hello World!")` následující kód následujícím kódem `Main()` :

[!code-csharp[MLContext](./snippets/movie-recommendation/csharp/Program.cs#MLContext "Add MLContext")]

[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů. Je podobný, koncepčně, na `DBContext` v Entity Framework.

Poté `Main()` Vytvořte metodu s názvem `LoadData()` :

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Tato metoda vám poskytne chybu, dokud nepřidáte příkaz return v následujících krocích.

Inicializujte proměnné cesty k datům, načtěte data ze \* souborů. csv a vraťte `Train` `Test` data a jako `IDataView` objekty přidáním následujícího jako další řádek kódu v `LoadData()` :

[!code-csharp[LoadData](./snippets/movie-recommendation/csharp/Program.cs#LoadData "Load data from data paths")]

Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView). `IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text). Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.

[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru. Převezme proměnné cesty k datům a vrátí `IDataView` . V takovém případě zadáte cestu k `Test` souborům a a `Train` určíte hlavičku textového souboru (takže může použít názvy sloupců správně) a oddělovač dat znaků čárky (výchozí oddělovač je karta).

Do metody přidejte následující kód `Main()` pro volání `LoadData()` metody a vraťte `Train` `Test` data a:

[!code-csharp[LoadDataMain](./snippets/movie-recommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Sestavování a výuka modelu

Existují tři hlavní koncepty v ML.NET: [data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer)a [odhady](../resources/glossary.md#estimator).

Školicí algoritmy Machine Learning vyžadují data v určitém formátu. `Transformers`slouží k transformaci tabulkových dat do kompatibilního formátu.

![Diagram toku dat transformátoru](./media/movie-recommendation/data-transformer-transformed.png)

Vytvoříte `Transformers` v ml.NET vytvořením `Estimators` . `Estimators`Převezměte data a vraťte se `Transformers` .

![Diagram toku dat Estimator](./media/movie-recommendation/data-estimator-transformer.png)

Vzorový algoritmus pro školení, který použijete pro školení modelu, je příkladem `Estimator` .

Vytvořte `Estimator` pomocí následujících kroků:

Vytvořte `BuildAndTrainModel()` metodu hned za `LoadData()` metodou pomocí následujícího kódu:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Tato metoda vám poskytne chybu, dokud nepřidáte příkaz return v následujících krocích.

Definujte transformace dat přidáním následujícího kódu do `BuildAndTrainModel()` :

[!code-csharp[DataTransformations](./snippets/movie-recommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

Vzhledem k tomu, že `userId` a `movieId` zastupují uživatele a názvy filmů, ne reálné hodnoty, použijte metodu [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pro transformaci každého `userId` a každého `movieId` na sloupec číselného typu klíče `Feature` (formát přijatý pomocí algoritmů doporučení) a přidejte je jako nové sloupce datové sady:

| userId | movieId | Popisek | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Vyberte algoritmus strojového učení a přidejte ho k definicím transformace dat. Přidejte následující kód jako další řádek kódu v `BuildAndTrainModel()` :

[!code-csharp[AddAlgorithm](./snippets/movie-recommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je váš školicí algoritmus pro doporučení.  Vytváření [matic](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je obvyklým přístupem k doporučením, když máte data o tom, jak uživatelé mají v minulosti hodnocené produkty, což je případ datových sad v tomto kurzu. Existují i další algoritmy doporučení, pokud máte dostupná jiná data (Další informace najdete v části [ostatní algoritmy doporučení](#other-recommendation-algorithms) níže).

V takovém případě `Matrix Factorization` algoritmus používá metodu nazvanou "filtrování spolupráce", což předpokládá, že pokud uživatel 1 má stejné stanovisko jako uživatel 2 k určitému problému, pak uživatel 1 je pravděpodobnější, že uživatel 2 má stejný dojem jako uživatel 2 o jiném problému.

Například pokud uživatel 1 a uživatel 2 znamená filmy podobně, je pravděpodobnější, že uživatel 2 požívá film, který uživatel 1 sledoval a hodnotil vysoce:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Uživatel 1 | Sledovaný a nelíbí se film | Sledovaný a nelíbí se film | Sledovaný a nelíbí se film |
| Uživatel 2 | Sledovaný a nelíbí se film | Sledovaný a nelíbí se film | Nesledováno – doporučit video |

`Matrix Factorization`Trainer má několik [možností](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), které si můžete přečíst v části s [parametry algoritmu](#algorithm-hyperparameters) níže.

Přizpůsobte si model `Train` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu v `BuildAndTrainModel()` metodě:

[!code-csharp[FitModel](./snippets/movie-recommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

Metoda [přizpůsobení ():](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) nahlaste svůj model pomocí poskytnuté datové sady školení. Technicky, provede `Estimator` definice transformací dat a používáním školení a vrátí zpět školicí model, který je `Transformer` .

Přidejte následující jako další řádek kódu v `Main()` metodě pro volání vaší `BuildAndTrainModel()` metody a vraťte školený model:

[!code-csharp[BuildTrainModelMain](./snippets/movie-recommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Vyhodnocení modelu

Jakmile svůj model provedete, použijte k vyhodnocení způsobu provádění modelu testovací data.

Vytvořte `EvaluateModel()` metodu hned za `BuildAndTrainModel()` metodou pomocí následujícího kódu:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Transformujte `Test` data přidáním následujícího kódu do `EvaluateModel()` :

[!code-csharp[Transform](./snippets/movie-recommendation/csharp/Program.cs#Transform "Transform the test data")]

Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro více zadaných vstupních řádků testovací sady dat.

Vyhodnoťte model přidáním následujícího jako další řádek kódu v `EvaluateModel()` metodě:

[!code-csharp[Evaluate](./snippets/movie-recommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.

Vytiskněte metriky vyhodnocení do konzoly přidáním následujícího jako další řádek kódu v `EvaluateModel()` metodě:

[!code-csharp[PrintMetrics](./snippets/movie-recommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

Přidejte následující jako další řádek kódu v `Main()` metodě pro volání `EvaluateModel()` metody:

[!code-csharp[EvaluateModelMain](./snippets/movie-recommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Výstup by měl vypadat podobně jako v následujícím textu:

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

V tomto výstupu existují 20 iterací. V každé iteraci se míra chyb zmenší a konverguje blíž a blíže k hodnotě 0.

`root of mean squared error`(RMS nebo RMSE) slouží k měření rozdílů mezi předpokládanými hodnotami modelu a datovou sadou testů, které byly pozorovány. Technicky je to druhá odmocnina průměru průměrných čtverců chyb. Čím nižší je, tím lepší je model.

`R Squared`Určuje, jak dobře data vyhovují modelu. Rozsah od 0 do 1. Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu. Hodnota 1 znamená, že model přesně odpovídá datům. Chcete, `R Squared` aby vaše skóre bylo co nejblíže k 1.

Sestavování úspěšných modelů je iterativní proces. Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady. Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými parametry Hyper-v pro každý algoritmus. Další informace najdete v části [vylepšení modelu](#improve-your-model) níže.

## <a name="use-your-model"></a>Použití modelu

Nyní můžete použít svůj vycvičený model k vytvoření předpovědi pro nová data.

Vytvořte `UseModelForSinglePrediction()` metodu hned za `EvaluateModel()` metodou pomocí následujícího kódu:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Použijte `PredictionEngine` pro předpověď hodnocení přidáním následujícího kódu do `UseModelForSinglePrediction()` :

[!code-csharp[PredictionEngine](./snippets/movie-recommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken. Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem. Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte `PredictionEnginePool` službu, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objekty pro použití v celé aplikaci. V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ASP.NET Core webového rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozšíření služby je momentálně ve verzi Preview.

Vytvořte instanci s `MovieRating` názvem `testInput` a předejte ji do modulu předpovědi přidáním následujícího jako další řádky kódu v `UseModelForSinglePrediction()` metodě:

[!code-csharp[MakeSinglePrediction](./snippets/movie-recommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden sloupec dat.

Pak můžete použít `Score` nebo předpovězené hodnocení, abyste zjistili, jestli chcete pro uživatele 6 doporučit video s movieId 10. Čím vyšší je `Score` pravděpodobnost, že uživatel míru konkrétní film. V takovém případě řekněme, že doporučujeme filmy s předpokládaným hodnocením > 3,5.

Chcete-li vytisknout výsledky, přidejte následující jako další řádky kódu v `UseModelForSinglePrediction()` metodě:

[!code-csharp[PrintResults](./snippets/movie-recommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

Přidejte následující jako další řádek kódu v `Main()` metodě pro volání `UseModelForSinglePrediction()` metody:

[!code-csharp[UseModelMain](./snippets/movie-recommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Výstup této metody by měl vypadat podobně jako následující text:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Uložení modelu

Pokud chcete model použít k tomu, aby předpovědi aplikace pro koncové uživatele, musíte nejdřív model Uložit.

Vytvořte `SaveModel()` metodu hned za `UseModelForSinglePrediction()` metodou pomocí následujícího kódu:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Uložte svůj vycvičený model přidáním následujícího kódu do `SaveModel()` metody:

[!code-csharp[SaveModel](./snippets/movie-recommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Tato metoda uloží váš vyškolený model do souboru. zip (do složky "data"), který pak můžete použít v jiných aplikacích .NET k vytvoření předpovědi.

Přidejte následující jako další řádek kódu v `Main()` metodě pro volání `SaveModel()` metody:

[!code-csharp[SaveModelMain](./snippets/movie-recommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Použití uloženého modelu

Po uložení svého vyučeného modelu můžete model využívat v různých prostředích. Další informace o tom, jak zprovoznění model strojového učení v aplikacích, najdete v tématu [ukládání a načítání](../how-to-guides/save-load-machine-learning-models-ml-net.md) školicích modelů.

## <a name="results"></a>Výsledky

Po provedení kroků uvedených výše spusťte konzolovou aplikaci (CTRL + F5). Vaše výsledky z jedné předpovědi výše by měly být podobné následujícímu. Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.

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

Blahopřejeme! Teď jste úspěšně vytvořili model strojového učení pro doporučování filmů. Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .

## <a name="improve-your-model"></a>Vylepšení modelu

Existuje několik způsobů, jak můžete zlepšit výkon modelu, abyste mohli získat přesnější předpovědi.

### <a name="data"></a>Data

Přidání dalších školicích dat, která mají dostatek ukázek pro každého uživatele a ID filmu, může pomoci zlepšit kvalitu modelu doporučení.

[Mezi ověřováním](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) je metoda pro vyhodnocování modelů, které náhodně rozdělí data do podmnožiny (místo extrakce testovacích dat z datové sady, jako jste to udělali v tomto kurzu), a jako testovací data převezme některé skupiny jako data výukového programu. Tato metoda vykonává rozdělení výukového testu z hlediska kvality modelu.

### <a name="features"></a>Funkce

V tomto kurzu použijete pouze tři `Features` ( `user id` , `movie id` , a `rating` ), které jsou poskytovány datovou sadou.

I když je to dobrý začátek, možná budete chtít přidat další atributy nebo `Features` (například věk, pohlaví, geografické umístění atd.), pokud jsou zahrnuté v datové sadě. Přidání relevantních `Features` výsledků může pomoci zlepšit výkon vašeho modelu doporučení.

Pokud si nejste jistí `Features` , které z nich může být pro úlohu strojového učení nejrelevantnější, můžete také využít důležitost funkcí pro výpočet příspěvků (FCC) a [funkce permutace](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), které ml.NET poskytuje k tomu, abyste zjistili, co je v nejvyšší míře `Features` .

### <a name="algorithm-hyperparameters"></a>Parametry algoritmu

I když ML.NET poskytuje dobré výchozí algoritmy pro školení, můžete ještě více ladit výkon změnou [parametrů](../resources/glossary.md#hyperparameter)algoritmu.

Pro můžete `Matrix Factorization` experimentovat s parametry, jako je [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , abyste viděli, jestli vám dává lepší výsledky.

Například v tomto kurzu jsou k disřadě možnosti algoritmu:

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

### <a name="other-recommendation-algorithms"></a>Další algoritmy doporučení

Algoritmus vyfaktoringu matice s filtrováním pro spolupráci je jediným řešením pro provádění doporučení filmu. V mnoha případech možná nemáte dostupná data hodnocení a k dispozici máte jenom historii filmů od uživatelů. V jiných případech možná budete mít více než jenom data hodnocení uživatele.

| Algoritmus       | Scénář           | Ukázka  |
| ------------- |:-------------:| -----:|
| Faktor vytváření matic třídy | Toto použijte, když máte jenom userId a movieId. Tento styl doporučení je založen na scénáři společného nákupu, nebo na produktech, které se často kupují, což znamená, že zákazníkům doporučí sadu produktů na základě vlastní historie nákupních objednávek. | [>vyzkoušet](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Počítače pro vytváření faktoringu s podporou polí | Použijte k tomu doporučení, když máte víc funkcí nad ID uživatele, productId a hodnocení (například popis produktu nebo cena produktu). Tato metoda také používá přístup pro filtrování spolupráce. | [>vyzkoušet](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Scénář nového uživatele

Jedním z běžných potíží při filtrování spolupráce je problém s studeným startem, který je v případě, že máte nového uživatele, který nemá žádná předchozí data pro vykreslování odvození z. Tento problém se často vyřeší tím, že požádá nového uživatele, aby vytvořil profil a například rychlost, jakou videa viděli v minulosti. I když tato metoda přináší uživateli určitou režii, poskytuje několik počátečních dat pro nové uživatele bez historie hodnocení.

## <a name="resources"></a>Zdroje a prostředky

Data použitá v tomto kurzu jsou odvozena z [datové sady MovieLens](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:

> [!div class="checklist"]
>
> * Vyberte algoritmus strojového učení.
> * Příprava a načtení dat
> * Sestavování a výuka modelu
> * Vyhodnocení modelu
> * Nasazení a využití modelu

Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.
> [!div class="nextstepaction"]
> [Analýza mínění](sentiment-analysis.md)
