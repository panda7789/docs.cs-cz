---
title: 'Kurz: Vytvoření faktoru pro vystavování filmů – vytváření matic'
description: V tomto kurzu se dozvíte, jak v konzolové aplikaci .NET Core sestavit doporučení pro film pomocí ML.NET. Postup používá C# a Visual Studio 2019.
author: briacht
ms.date: 08/26/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 4f80ebad0a280040e9f3329dc7b647bd53a48fa0
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929483"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="bc720-104">Kurz: Vytvoření doporučení pro film pomocí Matrix factorizaton s ML.NET</span><span class="sxs-lookup"><span data-stu-id="bc720-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="bc720-105">V tomto kurzu se dozvíte, jak v konzolové aplikaci .NET Core sestavit doporučení pro film pomocí ML.NET.</span><span class="sxs-lookup"><span data-stu-id="bc720-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="bc720-106">Postup používá C# a Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="bc720-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="bc720-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="bc720-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="bc720-108">Vyberte algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="bc720-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="bc720-109">Příprava a načtení dat</span><span class="sxs-lookup"><span data-stu-id="bc720-109">Prepare and load your data</span></span>
> * <span data-ttu-id="bc720-110">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-110">Build and train a model</span></span>
> * <span data-ttu-id="bc720-111">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-111">Evaluate a model</span></span>
> * <span data-ttu-id="bc720-112">Nasazení a využití modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-112">Deploy and consume a model</span></span>

<span data-ttu-id="bc720-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .</span><span class="sxs-lookup"><span data-stu-id="bc720-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="bc720-114">Pracovní postup strojového učení</span><span class="sxs-lookup"><span data-stu-id="bc720-114">Machine learning workflow</span></span>

<span data-ttu-id="bc720-115">Pomocí následujících kroků můžete provést úlohu a také všechny další úlohy ML.NET:</span><span class="sxs-lookup"><span data-stu-id="bc720-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="bc720-116">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="bc720-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="bc720-117">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="bc720-118">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="bc720-119">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="bc720-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc720-120">Prerequisites</span></span>

* <span data-ttu-id="bc720-121">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="bc720-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="bc720-122">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="bc720-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="bc720-123">Existuje několik způsobů, jak získat přístup k problémům s doporučeními, jako je například doporučený seznam filmů nebo doporučený seznam souvisejících produktů, ale v tomto případě budete předpovídat, jaké hodnocení (1-5) bude uživatel podávat konkrétnímu videu, a doporučit ho, pokud je vyšší než definovaná prahová hodnota (čím vyšší je hodnocení, tím větší je pravděpodobnost, že uživatel míru konkrétní film).</span><span class="sxs-lookup"><span data-stu-id="bc720-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="bc720-124">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="bc720-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="bc720-125">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="bc720-125">Create a project</span></span>

1. <span data-ttu-id="bc720-126">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bc720-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="bc720-127">Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="bc720-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="bc720-128">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="bc720-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="bc720-129">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="bc720-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="bc720-130">Do textového pole **název** zadejte "MovieRecommender" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="bc720-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="bc720-131">Vytvořte v projektu adresář s názvem *data* pro uložení datové sady:</span><span class="sxs-lookup"><span data-stu-id="bc720-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="bc720-132">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="bc720-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="bc720-133">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="bc720-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="bc720-134">Nainstalujte balíčky NuGet **Microsoft.ml** a **Microsoft. ml. doporučování** :</span><span class="sxs-lookup"><span data-stu-id="bc720-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="bc720-135">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="bc720-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="bc720-136">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="bc720-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="bc720-137">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="bc720-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="bc720-138">Opakujte tento postup pro **Microsoft. ml. doporučuje**se.</span><span class="sxs-lookup"><span data-stu-id="bc720-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="bc720-139">Do horní části `using` souboru *program.cs* přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="bc720-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="bc720-140">Stažení dat</span><span class="sxs-lookup"><span data-stu-id="bc720-140">Download your data</span></span>

1. <span data-ttu-id="bc720-141">Stáhněte dvě datové sady a uložte je do složky *dat* , kterou jste vytvořili dříve:</span><span class="sxs-lookup"><span data-stu-id="bc720-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="bc720-142">Klikněte pravým tlačítkem na [*Recommendation-ratings-Train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte Uložit odkaz (nebo cíl) jako...</span><span class="sxs-lookup"><span data-stu-id="bc720-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="bc720-143">Klikněte pravým tlačítkem na [*Recommendation-ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte Uložit odkaz (nebo cíl) jako...</span><span class="sxs-lookup"><span data-stu-id="bc720-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="bc720-144">Ujistěte se, že \*soubory. csv ukládáte do složky *data* nebo když je uložíte \*jinam, přesuňte soubory. CSV do složky *data* .</span><span class="sxs-lookup"><span data-stu-id="bc720-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="bc720-145">V Průzkumník řešení klikněte pravým tlačítkem na každý ze \*souborů. csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="bc720-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="bc720-146">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="bc720-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![kopírovat, pokud je novější ve VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="bc720-148">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="bc720-148">Load your data</span></span>

<span data-ttu-id="bc720-149">Prvním krokem v procesu ML.NET je příprava a načtení modelu školení a testování dat.</span><span class="sxs-lookup"><span data-stu-id="bc720-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="bc720-150">Data hodnocení doporučení jsou rozdělena do `Train` datových `Test` sad a.</span><span class="sxs-lookup"><span data-stu-id="bc720-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="bc720-151">`Train` Data se používají k přizpůsobení modelu.</span><span class="sxs-lookup"><span data-stu-id="bc720-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="bc720-152">`Test` Data se používají k zajištění předpovědiy s vyškolenou modelem a vyhodnocení výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="bc720-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="bc720-153">Je běžné mít 80/20 rozdělení s `Train` daty a. `Test`</span><span class="sxs-lookup"><span data-stu-id="bc720-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="bc720-154">Níže je zobrazená ukázka dat z vašich \*souborů. CSV:</span><span class="sxs-lookup"><span data-stu-id="bc720-154">Below is a preview of the data from your \*.csv files:</span></span>

![Náhled dat](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="bc720-156">V souborech \*. CSV jsou čtyři sloupce:</span><span class="sxs-lookup"><span data-stu-id="bc720-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="bc720-157">Ve službě Machine Learning se ve sloupcích, které se používají k vytvoření předpovědi, říká [funkce](../resources/glossary.md#feature)a sloupec s vrácenou předpověď se nazývá [popisek](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="bc720-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="bc720-158">Chcete odhadnout hodnocení filmů, takže sloupec hodnocení je `Label`.</span><span class="sxs-lookup"><span data-stu-id="bc720-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="bc720-159">Další tři `userId`sloupce, `movieId`, a `timestamp` jsou `Features` použity k předpovědi `Label`.</span><span class="sxs-lookup"><span data-stu-id="bc720-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="bc720-160">Funkce</span><span class="sxs-lookup"><span data-stu-id="bc720-160">Features</span></span>      | <span data-ttu-id="bc720-161">Popisek</span><span class="sxs-lookup"><span data-stu-id="bc720-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="bc720-162">Je až na to, abyste se rozhodli `Features` , které se použijí k `Label`předpovědi.</span><span class="sxs-lookup"><span data-stu-id="bc720-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="bc720-163">Pomocí metod, jako je třeba [funkce permutace](../how-to-guides/determine-global-feature-importance-in-model.md) , můžete také využít k výběru `Features`nejlepšího řešení.</span><span class="sxs-lookup"><span data-stu-id="bc720-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="bc720-164">V takovém případě byste měli `timestamp` sloupec `Feature` eliminovat, protože časové razítko ve skutečnosti neovlivňuje způsob, jakým se uživatel podílí na videu, a proto by nebyl přispívat k zajištění přesnější předpovědi:</span><span class="sxs-lookup"><span data-stu-id="bc720-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="bc720-165">Funkce</span><span class="sxs-lookup"><span data-stu-id="bc720-165">Features</span></span>      | <span data-ttu-id="bc720-166">Popisek</span><span class="sxs-lookup"><span data-stu-id="bc720-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="bc720-167">Dále musíte definovat datovou strukturu pro vstupní třídu.</span><span class="sxs-lookup"><span data-stu-id="bc720-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="bc720-168">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="bc720-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="bc720-169">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="bc720-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="bc720-170">V **dialogovém okně Přidat novou položku**vyberte **třída** a změňte pole **název** na *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="bc720-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="bc720-171">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="bc720-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="bc720-172">V editoru kódu se otevře soubor *MovieRatingData.cs* .</span><span class="sxs-lookup"><span data-stu-id="bc720-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="bc720-173">Do horní části `using` *MovieRatingData.cs*přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="bc720-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="bc720-174">Vytvořte třídu s názvem `MovieRating` odebráním existující definice třídy a přidáním následujícího kódu do *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="bc720-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="bc720-175">`MovieRating`Určuje vstupní datovou třídu.</span><span class="sxs-lookup"><span data-stu-id="bc720-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="bc720-176">Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny.</span><span class="sxs-lookup"><span data-stu-id="bc720-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="bc720-177">`Label` `Label` Sloupce a jsou`movieId` vaše`Features` (vstupy, které model poskytnete k předpovídání), a sloupec hodnocení je, který budete předpovídat (výstup modelu). `userId`</span><span class="sxs-lookup"><span data-stu-id="bc720-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="bc720-178">Vytvořte další třídu, `MovieRatingPrediction`pro reprezentaci předpokládaných výsledků přidáním následujícího kódu `MovieRating` za třídu v *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="bc720-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="bc720-179">V *program.cs*nahraďte `Console.WriteLine("Hello World!")` následující kód následujícím kódem `Main()`:</span><span class="sxs-lookup"><span data-stu-id="bc720-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="bc720-180">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializace `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="bc720-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="bc720-181">Je podobný, koncepčně, na `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bc720-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="bc720-182">Poté `Main()`vytvořte metodu s názvem `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="bc720-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="bc720-183">Tato metoda vám poskytne chybu, dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="bc720-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="bc720-184">Inicializujte proměnné cesty k datům, načtěte data ze \*souborů. csv a `Train` vraťte data a `Test` jako `IDataView` objekty přidáním následujícího jako další řádek kódu v `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="bc720-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="bc720-185">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="bc720-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="bc720-186">`IDataView`je flexibilní a efektivní způsob, jak popsat tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="bc720-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="bc720-187">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="bc720-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="bc720-188">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="bc720-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="bc720-189">Převezme proměnné cesty k datům a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="bc720-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="bc720-190">V takovém případě zadáte cestu k `Test` souborům a `Train` a určíte hlavičku textového souboru (takže může použít názvy sloupců správně) a oddělovač dat znaků čárky (výchozí oddělovač je karta).</span><span class="sxs-lookup"><span data-stu-id="bc720-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="bc720-191">Do `Main()` metody přidejte následující kód pro `LoadData()` volání metody a vraťte `Train` data a `Test` :</span><span class="sxs-lookup"><span data-stu-id="bc720-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="bc720-192">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-192">Build and train your model</span></span>

<span data-ttu-id="bc720-193">ML.NET jsou tři hlavní koncepty: [Data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer)a [odhady](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="bc720-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="bc720-194">Školicí algoritmy Machine Learning vyžadují data v určitém formátu.</span><span class="sxs-lookup"><span data-stu-id="bc720-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="bc720-195">`Transformers`slouží k transformaci tabulkových dat do kompatibilního formátu.</span><span class="sxs-lookup"><span data-stu-id="bc720-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Obrázek transformátoru](./media/movie-recommendation/transformer.png)

<span data-ttu-id="bc720-197">Vytvoříte `Transformers` v ml.NET vytvořením `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="bc720-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="bc720-198">`Estimators`Převezměte data a vraťte `Transformers`se.</span><span class="sxs-lookup"><span data-stu-id="bc720-198">`Estimators` take in data and return `Transformers`.</span></span>

![Obrázek Estimator](./media/movie-recommendation/estimator.png)

<span data-ttu-id="bc720-200">Vzorový algoritmus pro školení, který použijete pro školení modelu, je příkladem `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="bc720-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="bc720-201">`Estimator` Vytvořte pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="bc720-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="bc720-202">Vytvořte metodu hned `LoadData()` za metodou pomocí následujícího kódu: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="bc720-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="bc720-203">Tato metoda vám poskytne chybu, dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="bc720-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="bc720-204">Definujte transformace dat přidáním následujícího kódu do `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="bc720-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="bc720-205">Vzhledem `userId` k `movieId` tomu, že a zastupují uživatele a názvy filmů, ne reálné hodnoty, použijete metodu [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) k `movieId` transformaci každého `userId` a každého `Feature` na sloupec typu numerický klíč (formát přijatý pomocí algoritmů doporučení) a přidejte je jako nové sloupce datové sady:</span><span class="sxs-lookup"><span data-stu-id="bc720-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="bc720-206">userId</span><span class="sxs-lookup"><span data-stu-id="bc720-206">userId</span></span> | <span data-ttu-id="bc720-207">movieId</span><span class="sxs-lookup"><span data-stu-id="bc720-207">movieId</span></span> | <span data-ttu-id="bc720-208">Popisek</span><span class="sxs-lookup"><span data-stu-id="bc720-208">Label</span></span> | <span data-ttu-id="bc720-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="bc720-209">userIdEncoded</span></span> | <span data-ttu-id="bc720-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="bc720-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="bc720-211">1</span><span class="sxs-lookup"><span data-stu-id="bc720-211">1</span></span> | <span data-ttu-id="bc720-212">1</span><span class="sxs-lookup"><span data-stu-id="bc720-212">1</span></span> | <span data-ttu-id="bc720-213">4</span><span class="sxs-lookup"><span data-stu-id="bc720-213">4</span></span> | <span data-ttu-id="bc720-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="bc720-214">userKey1</span></span> | <span data-ttu-id="bc720-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="bc720-215">movieKey1</span></span> |
| <span data-ttu-id="bc720-216">1</span><span class="sxs-lookup"><span data-stu-id="bc720-216">1</span></span> | <span data-ttu-id="bc720-217">3</span><span class="sxs-lookup"><span data-stu-id="bc720-217">3</span></span> | <span data-ttu-id="bc720-218">4</span><span class="sxs-lookup"><span data-stu-id="bc720-218">4</span></span> | <span data-ttu-id="bc720-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="bc720-219">userKey1</span></span> | <span data-ttu-id="bc720-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="bc720-220">movieKey2</span></span> |
| <span data-ttu-id="bc720-221">1</span><span class="sxs-lookup"><span data-stu-id="bc720-221">1</span></span> | <span data-ttu-id="bc720-222">6</span><span class="sxs-lookup"><span data-stu-id="bc720-222">6</span></span> | <span data-ttu-id="bc720-223">4</span><span class="sxs-lookup"><span data-stu-id="bc720-223">4</span></span> | <span data-ttu-id="bc720-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="bc720-224">userKey1</span></span> | <span data-ttu-id="bc720-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="bc720-225">movieKey3</span></span> |

<span data-ttu-id="bc720-226">Vyberte algoritmus strojového učení a přidejte ho k definicím transformace dat. Přidejte následující kód jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="bc720-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="bc720-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je váš školicí algoritmus pro doporučení.</span><span class="sxs-lookup"><span data-stu-id="bc720-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="bc720-228">Vytváření [matic](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je obvyklým přístupem k doporučením, když máte data o tom, jak uživatelé mají v minulosti hodnocené produkty, což je případ datových sad v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="bc720-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="bc720-229">Existují i další algoritmy doporučení, pokud máte dostupná jiná data (Další informace najdete v části [ostatní algoritmy doporučení](#other-recommendation-algorithms) níže).</span><span class="sxs-lookup"><span data-stu-id="bc720-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="bc720-230">V takovém případě `Matrix Factorization` algoritmus používá metodu nazvanou "filtrování spolupráce", což předpokládá, že pokud uživatel 1 má stejné stanovisko jako uživatel 2 k určitému problému, pak uživatel 1 je pravděpodobnější, že uživatel 2 má stejný dojem jako uživatel 2 o jiném problému.</span><span class="sxs-lookup"><span data-stu-id="bc720-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="bc720-231">Například pokud uživatel 1 a uživatel 2 znamená filmy podobně, je pravděpodobnější, že uživatel 2 požívá film, který uživatel 1 sledoval a hodnotil vysoce:</span><span class="sxs-lookup"><span data-stu-id="bc720-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="bc720-232">Uživatel 1</span><span class="sxs-lookup"><span data-stu-id="bc720-232">User 1</span></span> | <span data-ttu-id="bc720-233">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="bc720-233">Watched and liked movie</span></span> | <span data-ttu-id="bc720-234">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="bc720-234">Watched and liked movie</span></span> | <span data-ttu-id="bc720-235">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="bc720-235">Watched and liked movie</span></span> |
| <span data-ttu-id="bc720-236">Uživatel 2</span><span class="sxs-lookup"><span data-stu-id="bc720-236">User 2</span></span> | <span data-ttu-id="bc720-237">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="bc720-237">Watched and liked movie</span></span> | <span data-ttu-id="bc720-238">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="bc720-238">Watched and liked movie</span></span> | <span data-ttu-id="bc720-239">Nesledováno – doporučit video</span><span class="sxs-lookup"><span data-stu-id="bc720-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="bc720-240">Trainer má několik [možností](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), které si můžete přečíst v části s [parametry algoritmu](#algorithm-hyperparameters) níže. `Matrix Factorization`</span><span class="sxs-lookup"><span data-stu-id="bc720-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="bc720-241">Přizpůsobte si model `Train` datům a vraťte vyškolený model přidáním následujícího jako další řádek kódu `BuildAndTrainModel()` v metodě:</span><span class="sxs-lookup"><span data-stu-id="bc720-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="bc720-242">Metoda [přizpůsobení ():](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) nahlaste svůj model pomocí poskytnuté datové sady školení.</span><span class="sxs-lookup"><span data-stu-id="bc720-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="bc720-243">Technicky, provede `Estimator` definice transformací dat a používáním školení a vrátí zpět školicí model, který `Transformer`je.</span><span class="sxs-lookup"><span data-stu-id="bc720-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="bc720-244">Přidejte následující jako další řádek kódu v `Main()` metodě pro volání vaší `BuildAndTrainModel()` metody a vraťte školený model:</span><span class="sxs-lookup"><span data-stu-id="bc720-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="bc720-245">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-245">Evaluate your model</span></span>

<span data-ttu-id="bc720-246">Jakmile svůj model provedete, použijte k vyhodnocení způsobu provádění modelu testovací data.</span><span class="sxs-lookup"><span data-stu-id="bc720-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="bc720-247">Vytvořte metodu hned `BuildAndTrainModel()` za metodou pomocí následujícího kódu: `EvaluateModel()`</span><span class="sxs-lookup"><span data-stu-id="bc720-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="bc720-248">Transformujte `EvaluateModel()`data přidáním následujícího kódu do: `Test`</span><span class="sxs-lookup"><span data-stu-id="bc720-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="bc720-249">Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro více zadaných vstupních řádků testovací sady dat.</span><span class="sxs-lookup"><span data-stu-id="bc720-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="bc720-250">Vyhodnoťte model přidáním následujícího jako další řádek kódu v `EvaluateModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="bc720-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="bc720-251">Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.</span><span class="sxs-lookup"><span data-stu-id="bc720-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="bc720-252">Vytiskněte metriky vyhodnocení do konzoly přidáním následujícího jako další řádek kódu v `EvaluateModel()` metodě:</span><span class="sxs-lookup"><span data-stu-id="bc720-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="bc720-253">Přidejte následující jako další řádek kódu v `Main()` metodě pro `EvaluateModel()` volání metody:</span><span class="sxs-lookup"><span data-stu-id="bc720-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="bc720-254">Výstup by měl vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="bc720-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="bc720-255">V tomto výstupu existují 20 iterací.</span><span class="sxs-lookup"><span data-stu-id="bc720-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="bc720-256">V každé iteraci se míra chyb zmenší a konverguje blíž a blíže k hodnotě 0.</span><span class="sxs-lookup"><span data-stu-id="bc720-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="bc720-257">`root of mean squared error` (RMS nebo RMSE) slouží k měření rozdílů mezi předpokládanými hodnotami modelu a datovou sadou testů, které byly pozorovány.</span><span class="sxs-lookup"><span data-stu-id="bc720-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="bc720-258">Technicky je to druhá odmocnina průměru průměrných čtverců chyb.</span><span class="sxs-lookup"><span data-stu-id="bc720-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="bc720-259">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="bc720-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="bc720-260">`R Squared`Určuje, jak dobře data vyhovují modelu.</span><span class="sxs-lookup"><span data-stu-id="bc720-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="bc720-261">Rozsah od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="bc720-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="bc720-262">Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu.</span><span class="sxs-lookup"><span data-stu-id="bc720-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="bc720-263">Hodnota 1 znamená, že model přesně odpovídá datům.</span><span class="sxs-lookup"><span data-stu-id="bc720-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="bc720-264">Chcete, aby `R Squared` vaše skóre bylo co nejblíže k 1.</span><span class="sxs-lookup"><span data-stu-id="bc720-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="bc720-265">Sestavování úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="bc720-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="bc720-266">Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady.</span><span class="sxs-lookup"><span data-stu-id="bc720-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="bc720-267">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými parametry Hyper-v pro každý algoritmus.</span><span class="sxs-lookup"><span data-stu-id="bc720-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="bc720-268">Další informace najdete v části [vylepšení modelu](#improve-your-model) níže.</span><span class="sxs-lookup"><span data-stu-id="bc720-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="bc720-269">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-269">Use your model</span></span>

<span data-ttu-id="bc720-270">Nyní můžete použít svůj vycvičený model k vytvoření předpovědi pro nová data.</span><span class="sxs-lookup"><span data-stu-id="bc720-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="bc720-271">Vytvořte metodu hned `EvaluateModel()` za metodou pomocí následujícího kódu: `UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="bc720-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="bc720-272">Použijte pro předpověď hodnocení přidáním následujícího kódu do `UseModelForSinglePrediction()`: `PredictionEngine`</span><span class="sxs-lookup"><span data-stu-id="bc720-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="bc720-273">[Třída PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje předat jednu instanci dat a potom provést předpovědi pro tuto jedinou instanci dat.</span><span class="sxs-lookup"><span data-stu-id="bc720-273">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="bc720-274">Vytvořte instanci `MovieRating` s názvem `testInput` a předejte ji do modulu předpovědi přidáním následujícího jako další `UseModelForSinglePrediction()` řádky kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="bc720-274">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="bc720-275">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden sloupec dat.</span><span class="sxs-lookup"><span data-stu-id="bc720-275">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="bc720-276">Pak můžete použít `Score`nebo předpovězené hodnocení, abyste zjistili, jestli chcete pro uživatele 6 doporučit video s movieId 10.</span><span class="sxs-lookup"><span data-stu-id="bc720-276">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="bc720-277">Čím vyšší `Score`je pravděpodobnost, že uživatel míru konkrétní film.</span><span class="sxs-lookup"><span data-stu-id="bc720-277">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="bc720-278">V takovém případě řekněme, že doporučujeme filmy s předpokládaným hodnocením > 3,5.</span><span class="sxs-lookup"><span data-stu-id="bc720-278">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="bc720-279">Chcete-li vytisknout výsledky, přidejte následující jako další řádky kódu v `UseModelForSinglePrediction()` metodě:</span><span class="sxs-lookup"><span data-stu-id="bc720-279">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="bc720-280">Přidejte následující jako další řádek kódu v `Main()` metodě pro `UseModelForSinglePrediction()` volání metody:</span><span class="sxs-lookup"><span data-stu-id="bc720-280">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="bc720-281">Výstup této metody by měl vypadat podobně jako následující text:</span><span class="sxs-lookup"><span data-stu-id="bc720-281">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="bc720-282">Uložení modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-282">Save your model</span></span>

<span data-ttu-id="bc720-283">Pokud chcete model použít k tomu, aby předpovědi aplikace pro koncové uživatele, musíte nejdřív model Uložit.</span><span class="sxs-lookup"><span data-stu-id="bc720-283">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="bc720-284">Vytvořte metodu hned `UseModelForSinglePrediction()` za metodou pomocí následujícího kódu: `SaveModel()`</span><span class="sxs-lookup"><span data-stu-id="bc720-284">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="bc720-285">Uložte svůj vycvičený model přidáním následujícího kódu do `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="bc720-285">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="bc720-286">Tato metoda uloží váš vyškolený model do souboru. zip (do složky "data"), který pak můžete použít v jiných aplikacích .NET k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="bc720-286">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="bc720-287">Přidejte následující jako další řádek kódu v `Main()` metodě pro `SaveModel()` volání metody:</span><span class="sxs-lookup"><span data-stu-id="bc720-287">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="bc720-288">Použití uloženého modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-288">Use your saved model</span></span>

<span data-ttu-id="bc720-289">Po uložení proučeného modelu můžete model využívat v různých prostředích (Další informace najdete v [příručce "Návod"](../how-to-guides/consuming-model-ml-net.md) ), kde se dozvíte, jak zprovoznění model strojového učení v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="bc720-289">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="bc720-290">Výsledky</span><span class="sxs-lookup"><span data-stu-id="bc720-290">Results</span></span>

<span data-ttu-id="bc720-291">Po provedení kroků uvedených výše spusťte konzolovou aplikaci (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="bc720-291">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="bc720-292">Vaše výsledky z jedné předpovědi výše by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="bc720-292">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="bc720-293">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="bc720-293">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="bc720-294">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="bc720-294">Congratulations!</span></span> <span data-ttu-id="bc720-295">Teď jste úspěšně vytvořili model strojového učení pro doporučování filmů.</span><span class="sxs-lookup"><span data-stu-id="bc720-295">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="bc720-296">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .</span><span class="sxs-lookup"><span data-stu-id="bc720-296">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="bc720-297">Vylepšení modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-297">Improve your model</span></span>

<span data-ttu-id="bc720-298">Existuje několik způsobů, jak můžete zlepšit výkon modelu, abyste mohli získat přesnější předpovědi.</span><span class="sxs-lookup"><span data-stu-id="bc720-298">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="bc720-299">Data</span><span class="sxs-lookup"><span data-stu-id="bc720-299">Data</span></span>

<span data-ttu-id="bc720-300">Přidání dalších školicích dat, která mají dostatek ukázek pro každého uživatele a ID filmu, může pomoci zlepšit kvalitu modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="bc720-300">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="bc720-301">[Mezi ověřováním](../how-to-guides/train-cross-validation-ml-net.md) je metoda pro vyhodnocování modelů, které náhodně rozdělí data do podmnožiny (místo extrakce testovacích dat z datové sady, jako jste to udělali v tomto kurzu), a jako testovací data převezme některé skupiny jako data výukového programu.</span><span class="sxs-lookup"><span data-stu-id="bc720-301">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="bc720-302">Tato metoda vykonává rozdělení výukového testu z hlediska kvality modelu.</span><span class="sxs-lookup"><span data-stu-id="bc720-302">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="bc720-303">Funkce</span><span class="sxs-lookup"><span data-stu-id="bc720-303">Features</span></span>

<span data-ttu-id="bc720-304">V tomto `Features` kurzu použijete pouze tři (`user id`, `movie id`, a `rating`), které jsou poskytovány datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="bc720-304">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="bc720-305">I když je to dobrý začátek, možná budete chtít přidat další atributy nebo `Features` (například věk, pohlaví, geografické umístění atd.), pokud jsou zahrnuté v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="bc720-305">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="bc720-306">Přidání relevantních `Features` výsledků může pomoci zlepšit výkon vašeho modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="bc720-306">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="bc720-307">Pokud si nejste jistí, `Features` které z nich může být pro úlohu strojového učení nejrelevantnější, můžete také využít výpočet příspěvků funkcí a [důležitost permutací funkcí](../how-to-guides/determine-global-feature-importance-in-model.md), který ml.NET poskytuje k tomu, aby co nejvíce zjistilo. influent `Features`.</span><span class="sxs-lookup"><span data-stu-id="bc720-307">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="bc720-308">Parametry algoritmu</span><span class="sxs-lookup"><span data-stu-id="bc720-308">Algorithm hyperparameters</span></span>

<span data-ttu-id="bc720-309">I když ML.NET poskytuje dobré výchozí algoritmy pro školení, můžete ještě více ladit výkon změnou [parametrů](../resources/glossary.md#hyperparameter)algoritmu.</span><span class="sxs-lookup"><span data-stu-id="bc720-309">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="bc720-310">Pro `Matrix Factorization`můžete experimentovat s parametry, jako je [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , abyste viděli, jestli vám dává lepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="bc720-310">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="bc720-311">Například v tomto kurzu jsou k disřadě možnosti algoritmu:</span><span class="sxs-lookup"><span data-stu-id="bc720-311">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="bc720-312">Další algoritmy doporučení</span><span class="sxs-lookup"><span data-stu-id="bc720-312">Other Recommendation Algorithms</span></span>

<span data-ttu-id="bc720-313">Algoritmus vyfaktoringu matice s filtrováním pro spolupráci je jediným řešením pro provádění doporučení filmu.</span><span class="sxs-lookup"><span data-stu-id="bc720-313">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="bc720-314">V mnoha případech možná nemáte dostupná data hodnocení a k dispozici máte jenom historii filmů od uživatelů.</span><span class="sxs-lookup"><span data-stu-id="bc720-314">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="bc720-315">V jiných případech možná budete mít více než jenom data hodnocení uživatele.</span><span class="sxs-lookup"><span data-stu-id="bc720-315">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="bc720-316">Algoritmus</span><span class="sxs-lookup"><span data-stu-id="bc720-316">Algorithm</span></span>       | <span data-ttu-id="bc720-317">Scénář</span><span class="sxs-lookup"><span data-stu-id="bc720-317">Scenario</span></span>           | <span data-ttu-id="bc720-318">Ukázka</span><span class="sxs-lookup"><span data-stu-id="bc720-318">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="bc720-319">Faktor vytváření matic třídy</span><span class="sxs-lookup"><span data-stu-id="bc720-319">One Class Matrix Factorization</span></span> | <span data-ttu-id="bc720-320">Toto použijte, když máte jenom userId a movieId.</span><span class="sxs-lookup"><span data-stu-id="bc720-320">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="bc720-321">Tento styl doporučení je založen na scénáři společného nákupu, nebo na produktech, které se často kupují, což znamená, že zákazníkům doporučí sadu produktů na základě vlastní historie nákupních objednávek.</span><span class="sxs-lookup"><span data-stu-id="bc720-321">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="bc720-322">> vyzkoušet</span><span class="sxs-lookup"><span data-stu-id="bc720-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="bc720-323">Počítače pro vytváření faktoringu s podporou polí</span><span class="sxs-lookup"><span data-stu-id="bc720-323">Field Aware Factorization Machines</span></span> | <span data-ttu-id="bc720-324">Použijte k tomu doporučení, když máte víc funkcí nad ID uživatele, productId a hodnocení (například popis produktu nebo cena produktu).</span><span class="sxs-lookup"><span data-stu-id="bc720-324">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="bc720-325">Tato metoda také používá přístup pro filtrování spolupráce.</span><span class="sxs-lookup"><span data-stu-id="bc720-325">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="bc720-326">> vyzkoušet</span><span class="sxs-lookup"><span data-stu-id="bc720-326">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="bc720-327">Scénář nového uživatele</span><span class="sxs-lookup"><span data-stu-id="bc720-327">New user scenario</span></span>

<span data-ttu-id="bc720-328">Jedním z běžných potíží při filtrování spolupráce je problém s studeným startem, který je v případě, že máte nového uživatele, který nemá žádná předchozí data pro vykreslování odvození z.</span><span class="sxs-lookup"><span data-stu-id="bc720-328">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="bc720-329">Tento problém se často vyřeší tím, že požádá nového uživatele, aby vytvořil profil a například rychlost, jakou videa viděli v minulosti.</span><span class="sxs-lookup"><span data-stu-id="bc720-329">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="bc720-330">I když tato metoda přináší uživateli určitou režii, poskytuje několik počátečních dat pro nové uživatele bez historie hodnocení.</span><span class="sxs-lookup"><span data-stu-id="bc720-330">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="bc720-331">Prostředky</span><span class="sxs-lookup"><span data-stu-id="bc720-331">Resources</span></span>

<span data-ttu-id="bc720-332">Data použitá v tomto kurzu jsou odvozena z [datové sady MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="bc720-332">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bc720-333">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bc720-333">Next steps</span></span>

<span data-ttu-id="bc720-334">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="bc720-334">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="bc720-335">Vyberte algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="bc720-335">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="bc720-336">Příprava a načtení dat</span><span class="sxs-lookup"><span data-stu-id="bc720-336">Prepare and load your data</span></span>
> * <span data-ttu-id="bc720-337">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-337">Build and train a model</span></span>
> * <span data-ttu-id="bc720-338">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-338">Evaluate a model</span></span>
> * <span data-ttu-id="bc720-339">Nasazení a využití modelu</span><span class="sxs-lookup"><span data-stu-id="bc720-339">Deploy and consume a model</span></span>

<span data-ttu-id="bc720-340">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="bc720-340">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="bc720-341">Analýza subjektivního hodnocení</span><span class="sxs-lookup"><span data-stu-id="bc720-341">Sentiment Analysis</span></span>](sentiment-analysis.md)
