---
title: Použít ve scénáři doporučení film ML.NET
description: Objevte, jak používat ML.NET ve scénáři doporučení pro doporučování filmů uživatelům.
author: briacht
ms.author: johalex
ms.date: 03/08/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 822ad0fc7a0a765fbf8664522a2e23f7aca4ea16
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921257"
---
# <a name="tutorial-create-a-movie-recommender-with-mlnet"></a>Kurz: Vytvoření doporučené video s ML.NET

Tento ukázkový kurz ukazuje použití ML.NET sestavit doporučené video přes using aplikace konzoly .NET Core C# v sadě Visual Studio 2017.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vyberte algoritmu strojového učení
> * Příprava a načítání dat
> * Vytvoření a trénování modelu
> * Vyhodnocení modelu
> * Nasazení a používání modelu

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Tento kurz a související ukázkové právě používáte **ML.NET verze 0,11**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) úložiště.

## <a name="machine-learning-workflow"></a>Pracovní postup Machine learning
K provedení úlohy, stejně jako jakoukoliv jinou úlohu ML.NET použijete následující kroky:

1. [Načtení dat](#load-your-data)
2. [Vytvoření a trénování modelu](#build-and-train-your-model)
3. [Vyhodnocení modelu](#evaluate-your-model)
4. [Použití modelu](#use-your-model)

## <a name="prerequisites"></a>Požadavky

* [Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.

## <a name="select-the-appropriate-machine-learning-task"></a>Vyberte úlohu odpovídající machine learning

Existuje několik způsobů, jak přistupovat ke doporučení problémy, třeba doporučování filmů seznam nebo doporučující seznam souvisejících produktů, ale v tomto případě se předpovědět, jaké (1-5) hodnocení uživatele bude uživatelům k konkrétního videa a doporučujeme tento film, pokud je vyšší než definovanou prahovou hodnotu (vyšší hodnocení, tím pravděpodobněji budou přesně konkrétního videa uživatele).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

### <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "MovieRecommender" a pak vyberte **OK** tlačítko.

2. Vytvořte adresář *Data* ve vašem projektu a uložení datové sady:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**. Zadejte "Data" a stiskněte Enter.

3. Nainstalujte **Microsoft.ML** a **Microsoft.ML.Recommender** balíčky NuGet:

    V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**. Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko. Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené. Opakujte tyto kroky pro **Microsoft.ML.Recommender**.

  > [!NOTE]
  > Tento kurz používá **Microsoft.ML v0.11.0** a **Microsoft.ML.Recommender v0.11.0**.
    
4. Přidejte následující `using` příkazů v horní části vašeho *Program.cs* souboru:
    
    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Stáhněte si vaše data

1. Stáhněte si dvě datové sady a uložit je do *Data* dříve vytvořená složka:

*   Klikněte pravým tlačítkem na [ *doporučení. hodnocení train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."
*   Klikněte pravým tlačítkem na [ *doporučení. hodnocení test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."

     Ujistěte se, že buď uložit \*soubory CSV *Data* složky, nebo poté, co jste jej uložili jinde, přesunout \*soubory CSV *Data* složky.

2. V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**. V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.

   ![Kopírovat, pokud je novější v sadě Visual Studio](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a>Načtení dat

Prvním krokem v procesu ML.NET se můžete připravit a načíst vaše testovací data a cvičení modelu.

Data hodnocení doporučení se dělí do `Train` a `Test` datové sady. `Train` Data slouží k přizpůsobení modelu. `Test` Data slouží k vytváření predikcí trénovaného modelu a vyhodnocení výkonu modelu. Je běžné mít 80/20 rozdělení `Train` a `Test` data.

Níže je ve verzi preview data z vašeho \*souborů .csv s daty:

![Náhled dat](./media/movie-recommendation/csv-dataset-preview.png)

V \*soubory .csv, jsou čtyři sloupce:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Ve službě machine learning, se nazývají sloupce, které se používají při předpovědích [funkce](../resources/glossary.md#feature), a sloupec s vrácené predikcí se volá [popisek](../resources/glossary.md#label).

Chcete předpovědět hodnocení filmů, tak, aby sloupec hodnocení `Label`. Ostatní tři sloupce, `userId`, `movieId`, a `timestamp` jsou všechny `Features` použít k předpovědi `Label`.

| Funkce      | Popisek         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Záleží jen na vás, která `Features` se používají k předpovědi `Label`. Můžete také použít metody, jako je [funkce permutaci význam](../how-to-guides/determine-global-feature-importance-in-model.md) abychom vám pomohli s výběrem nejlepší `Features`.

V takovém případě by odstranění `timestamp` jako sloupec `Feature` protože časové razítko nemá vliv na skutečně jak uživatel sazeb daného videa a proto by přispívat k provedení přesnější předpověď:

| Funkce      | Popisek         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Dále je nutné definovat strukturu dat pro třídu vstupu.

Přidejte novou třídu do projektu:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **Přidat > Nová položka**.

2. V **dialogové okno Přidat novou položku**vyberte **třídy** a změnit **název** pole *MovieRatingData.cs*. Vyberte **přidat** tlačítko.

*MovieRatingData.cs* soubor se otevře v editoru kódu. Přidejte následující `using` příkaz do horní části *MovieRatingData.cs*:

```csharp
using Microsoft.ML.Data;
```

Vytvořte třídu s názvem `MovieRating` odebráním stávající definice třídy a přidáním následujícího kódu v *MovieRatingData.cs*:

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` Určuje třídu vstupní data. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atribut určuje, jaké sloupce (podle index sloupce) v datové sadě se mají načíst. `userId` a `movieId` sloupce jsou vaše `Features` (vstupy vám poskytne model k predikci `Label`), a sloupec hodnocení se `Label` , že bude předpovídat (výstup modelu).

Vytvořit jiné třídy `MovieRatingPrediction`, přidáním následujícího kódu po představující předpokládané výsledky `MovieRating` třídy v *MovieRatingData.cs*:

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

V *Program.cs*, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem uvnitř `Main()`:

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu. Je to podobné, koncepčně `DBContext` v Entity Framework.

Po `Main()`, vytvořit metodu nazvanou `LoadData()`:
```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{


}
```

> [!NOTE]
> Tato metoda vám poskytne chybu dokud nepřidáte příkaz return v následujících krocích.

Inicializace proměnných cesty dat, načtení dat ze souborů CSV a vrátit `Train` a `Test` data jako `IDataView` objekty přidáním následujícího kódu jako další řádek kódu v `LoadData()`:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.Data.DataView.IDataView). `IDataView` je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové). Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru. Přijímá proměnné cesty dat a vrátí `IDataView`. V takovém případě můžete zadat cestu pro vaše `Test` a `Train` soubory a označte text záhlaví souboru (takže ho můžete použít názvy sloupců správně) a čárky znakový oddělovač data (výchozím oddělovačem je karta).

Přidejte následující položky jako další dva řádky kódu ve `Main()` metodu chce volat vaše `LoadData()` metoda a vraťte se `Train` a `Test` dat:

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]


## <a name="build-and-train-your-model"></a>Vytvoření a trénování modelu

Existují tři hlavní koncepty v ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [transformátory](../basic-concepts-model-training-in-mldotnet.md#transformer), a [odhady](../basic-concepts-model-training-in-mldotnet.md#estimator).

Strojové učení školení algoritmy vyžadují dat v určitém formátu. `Transformers` slouží k transformaci tabulkových dat do formátu kompatibilní.

![Transformer – obrázek](./media/movie-recommendation/transformer.png)

Vytvoříte `Transformers` v ML.NET vytvořením `Estimators`. `Estimators` vzít data a vrátit `Transformers`.

![odhad image](./media/movie-recommendation/estimator.png)

Cvičení algoritmu doporučení budete používat pro trénování modelu je příkladem `Estimator`.

Sestavení `Estimator` pomocí následujících kroků:

Vytvořte `BuildAndTrainModel()` metoda, hned za `LoadData()` metodu, pomocí následujícího kódu:
```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{


}
```
> [!NOTE]
> Tato metoda vám poskytne chybu dokud nepřidáte příkaz return v následujících krocích.

Definování transformací dat přidáním následujícího kódu `BuildAndTrainModel()`:
   
[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

Protože `userId` a `movieId` představují uživatelů a názvy filmů, nikoli skutečné hodnoty, je použít [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody pro transformaci každého `userId` a každý `movieId` na číselný typ klíče `Feature`sloupec (formát, který přijal algoritmy doporučení) a přidejte je jako nové sloupce datové sady:

| userId | movieId | Popisek | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |


Zvolte algoritmu strojového učení a přidejte je do definice transformace dat, a to přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()`:

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je vaše doporučení cvičení algoritmu.  [Matice Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je běžný postup k doporučení, když máte data na tom, jak uživatelé ohodnoceni produkty v minulosti se stává třeba u datových sad v tomto kurzu. Existují jiné algoritmy doporučení, když máte k dispozici různé data (naleznete v tématu [jiné algoritmy doporučení](#other-recommendation-algorithms) následující další části). 

V takovém případě `Matrix Factorization` algoritmus používá metodu nazvanou "filtrování založeného na spolupráci", což předpokládá, že pokud uživatel 1 má stejný stanovisko jako 2 uživatele na určité problém, pak 1 uživatel má větší pravděpodobnost cítit, že stejným způsobem jako 2 uživatele o jiný problém.

Například pokud uživatel 1 a 2 uživatele hodnocení filmů podobně, pak uživatel 2 má větší pravděpodobnost Užijte si video, které má uživatel 1 sledovali vysílání televizní a velmi ohodnotili:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Uživatel 1 | Sledované a líbilo movie | Sledované a líbilo movie | Sledované a líbilo movie |
| Uživatel 2 | Sledované a líbilo movie | Sledované a líbilo movie | Nebyl sledované – DOPORUČUJEME movie |

`Matrix Factorization` Trainer víme o několika [možnosti](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), které si můžete přečíst více o v [algoritmus hyperparameters](#algorithm-hyperparameters) níže v části.

Přizpůsobit modelu, který má `Train` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) metoda trénovat modelu pomocí zadaného trénovací datové sady. Technicky, spustí `Estimator` definice transformace dat a použitím školení a vrátí zpět trénovaného modelu, který je `Transformer`.

Přidejte následující položky jako další řádek kódu `Main()` metodu chce volat vaše `BuildAndTrainModel()` metodu a vrátí trénovaného modelu:

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Vyhodnocení modelu

Jakmile máte Trénink modelu, slouží k vyhodnocení, jaký je výkon modelu testovací data. 

Vytvořte `EvaluateModel()` metoda, hned za `BuildAndTrainModel()` metodu, pomocí následujícího kódu:
```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{


}
```

Transformace `Test` data přidáním následujícího kódu do `EvaluateModel()`:
[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda vytváří předpovědi pro více poskytuje vstupní řádky z datové sady testů.

Přidáním následujícího kódu jako další řádek kódu ve vyhodnocení modelu `EvaluateModel()` metody:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Až budete mít předpovědi nastavená, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` v testovací datové sady a vrátí metriky na jaký je výkon modelu.

Tisk metrik hodnocení do konzoly přidáním následujícího kódu jako další řádek kódu v `EvaluateModel()` metody:

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

Přidejte následující položky jako další řádek kódu v `Main()` metodu chce volat vaše `EvaluateModel()` metody:

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Výstup, pokud by měla vypadat podobně jako následující text:

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

Tento výstup jsou 20 iterací. V každé iteraci míra chyb sníží a sladila blíže a blíže na hodnotu 0.

`root of mean squared error` (RMS nebo RMSE) se často používá k měření rozdílů mezi hodnoty předpovídané pomocí modelu a hodnotami zjištěnými v datové sadě testů. Technicky je druhá odmocnina průměru kvadratických chyb. Chcete, aby vaše RMSE skóre, aby byly co nejblíže 1 nejvíce.

`R Squared` je procento variace předpovězené hodnoty vysvětlené modelu. Je to hodnota mezi 0 a 1 a užší hodnotu na 0, tím lepší je model.

## <a name="use-your-model"></a>Použití modelu

Nyní můžete trénovaného modelu k vytvoření predikcí nová data.

Vytvořte `UseModelForSinglePrediction()` metoda, hned za `EvaluateModel()` metodu, pomocí následujícího kódu:
```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{


}
```

Použití `PredictionEngine` aby předpovídal hodnocení přidáním následujícího kódu `UseModelForSinglePrediction()`:

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které vám umožní předat jedna instance data a pak proveďte predikcí na tato jediná instance data.

Vytvoření instance `MovieRating` volá `testInput` a předejte jej do modulu předpovědi přidáním následujícího kódu jako další řádky kódu ve `UseModelForSinglePrediction()` metody:

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce vytváří predikcí na jeden sloupec data.

Pak můžete použít `Score`, nebo predikované hodnocení určit, jestli chcete pro doporučování filmů s movieId 10 uživateli 6. Vyšší `Score`, vyšší pravděpodobnost, že uživatel přesně konkrétního videa. V takovém případě Řekněme, že Doporučujete filmů s predikované hodnocení > 3.5.

Tisk výsledků, přidejte následující položky jako další řádky kódu ve `UseModelForSinglePrediction()` metody:

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

Přidejte následující položky jako další řádek kódu v `Main()` metodu chce volat vaše `UseModelForSinglePrediction()` metody:

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Výstup této metody by měla vypadat podobně jako následující text:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Uložit model
Použití modelu k následné predikci aplikace koncového uživatele, musíte nejprve uložit model.

Vytvořte `SaveModel()` metoda, hned za `UseModelForSinglePrediction()` metodu, pomocí následujícího kódu:
```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{


}
```

Uložení natrénovaného modelu přidáním následujícího kódu v `SaveModel()` metody:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

Tato metoda šetří trénovaného modelu do souboru ZIP (ve složce "Data"), který lze potom použít v ostatních aplikacích .NET k následné predikci.

Přidejte následující položky jako další řádek kódu v `Main()` metodu chce volat vaše `SaveModel()` metody:

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Použít uložený model
Po uložení natrénovaného modelu můžete využívat model v různých prostředích (najdete v článku ["Příručka"](../how-to-guides/consuming-model-ml-net.md) postup pro zprovoznění modelu trénovaného strojového učení v aplikacích).

## <a name="results"></a>Výsledky

Po provedení výše uvedených kroků, spuštění aplikace konzoly (Ctrl + F5). Výsledky z jednoho předpovědi výše by měl vypadat přibližně takto. Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy se odebraly z následujících výsledků pro přehlednost.

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

Blahopřejeme! Teď jste úspěšně vytvořili model pro doporučování filmů strojového učení. Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) úložiště.

## <a name="improve-your-model"></a>Zlepšit váš model

Existuje několik způsobů, takže můžete získat přesnější předpovědi může zlepšit výkon modelu.

### <a name="data"></a>Data 

Přidání další trénovací data, která má dostatek ukázky pro každého uživatele a id video můžete podílet na zlepšování kvality modelu doporučení.

[Křížové ověření](../how-to-guides/train-cross-validation-ml-net.md) je technika, který náhodně vyhodnocování modelů rozděluje data do podmnožiny (namísto extrahování testovací data z datové sady, stejně jako v tomto kurzu) a má některé skupiny jako trénování dat a některé skupiny jako test data. Tato metoda lepší výkon než provádění trénování a testování, rozdělit z hlediska kvality modelu.

### <a name="features"></a>Funkce

V tomto kurzu použijete pouze tři `Features` (`user id`, `movie id`, a `rating`), které jsou k dispozici v objektu DataSet. 

Přestože se jedná o dobrý začátek, ve skutečnosti můžete chtít přidat další atributy nebo `Features` (například věk, pohlaví, geografické umístění atd.) je zahrnuta v datové sadě. Přidání více odpovídajících `Features` může pomoct zlepšit výkon modelu doporučení. 

Pokud si nejste jisti, o tom, které `Features` může být nejdůležitějších pro úkol machine learning, můžete také využít z funkce příspěvek výpočtu (FCC) a [funkce permutaci význam](../how-to-guides/determine-global-feature-importance-in-model.md), poskytující ML.NET vyhledat největší vliv `Features`.

### <a name="algorithm-hyperparameters"></a>Algoritmus hyperparameters

Zatímco ML.NET poskytuje dobré výchozí školení algoritmy, můžete vyladit výkon tak, že změníte tento algoritmus [hyperparameters](../resources/glossary.md#hyperparameter).

Pro `Matrix Factorization`, můžete experimentovat s hyperparameters například [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) zobrazíte, pokud, která poskytuje lepší výsledky.

Například v tomto kurzu algoritmus možnosti jsou:

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

### <a name="other-recommendation-algorithms"></a>Jiné algoritmy doporučení
Algoritmus factorization matice s filtrování založeného na spolupráci je pouze jedním z přístupů pro provádění filmových doporučení. V mnoha případech nemusí mít k dispozici data hodnocení a mít jenom historie video k dispozici od uživatelů. V jiných případech může mít více než jen hodnocení data uživatele.

| algoritmus       | Scénář           | Ukázka  |
| ------------- |:-------------:| -----:|
| Matice Factorization jedné třídy | Použijte ho, když máte jen ID uživatele a movieId. Tento styl doporučení je založeno na společné nákupní scénář nebo produkty často kupované společně, což znamená, že vám doporučí zákazníkům sadu produktů na základě jejich vlastní historii nákupních objednávek. | [> vyzkoušejte si to](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Počítače používající Factorization pole | Používejte to, aby doporučení, pokud máte další funkce nad rámec userId, productId a hodnocení (například popis produktu nebo cena produktu). Tato metoda také používá filtrování přístup založený na spolupráci. | [> vyzkoušejte si to](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Nový uživatelský scénář
Jeden běžný problém při spolupráci filtrování je problém úplné spuštění, který je v případě nového uživatele bez předchozího dat. Chcete-li nakreslit závěry z. Tento problém je vyřešen často požádá noví uživatelé k vytvoření profilu a pro instanci míra filmy, jste narazili v minulosti. Zatímco tato metoda se vloží některé zatížení na uživatele, poskytuje nějaká počáteční data pro nové uživatele bez historie hodnocení.

## <a name="resources"></a>Prostředky
V tomto kurzu používá data jsou odvozena z [datovou sadu MovieLens](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Další kroky
V tomto kurzu jste se naučili:

> [!div class="checklist"]
> * Vyberte algoritmu strojového učení
> * Příprava a načítání dat
> * Vytvoření a trénování modelu
> * Vyhodnocení modelu
> * Nasazení a používání modelu

Přejděte k dalšímu kurzu, kde Další informace
> [!div class="nextstepaction"]
> [Analýza mínění](sentiment-analysis.md)
