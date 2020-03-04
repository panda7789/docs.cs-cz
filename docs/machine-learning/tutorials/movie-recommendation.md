---
title: 'Kurz: vytvoření faktoru pro vystavení filmů – vytváření matic'
description: V tomto kurzu se dozvíte, jak v konzolové aplikaci .NET Core sestavit doporučení pro film pomocí ML.NET. Postup používá C# a Visual Studio 2019.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a221289d0c232863f03a275c26dce835f2878bf7
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241101"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a><span data-ttu-id="10e21-104">Kurz: sestavení doporučení pro film pomocí vytváření matic s ML.NET</span><span class="sxs-lookup"><span data-stu-id="10e21-104">Tutorial: Build a movie recommender using matrix factorization with ML.NET</span></span>

<span data-ttu-id="10e21-105">V tomto kurzu se dozvíte, jak v konzolové aplikaci .NET Core sestavit doporučení pro film pomocí ML.NET.</span><span class="sxs-lookup"><span data-stu-id="10e21-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="10e21-106">Postup používá C# a Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="10e21-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="10e21-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="10e21-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="10e21-108">Vyberte algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="10e21-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="10e21-109">Příprava a načtení dat</span><span class="sxs-lookup"><span data-stu-id="10e21-109">Prepare and load your data</span></span>
> * <span data-ttu-id="10e21-110">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-110">Build and train a model</span></span>
> * <span data-ttu-id="10e21-111">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-111">Evaluate a model</span></span>
> * <span data-ttu-id="10e21-112">Nasazení a využití modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-112">Deploy and consume a model</span></span>

<span data-ttu-id="10e21-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .</span><span class="sxs-lookup"><span data-stu-id="10e21-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="10e21-114">Pracovní postup strojového učení</span><span class="sxs-lookup"><span data-stu-id="10e21-114">Machine learning workflow</span></span>

<span data-ttu-id="10e21-115">Pomocí následujících kroků můžete provést úlohu a také všechny další úlohy ML.NET:</span><span class="sxs-lookup"><span data-stu-id="10e21-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="10e21-116">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="10e21-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="10e21-117">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="10e21-118">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="10e21-119">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="10e21-120">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="10e21-120">Prerequisites</span></span>

* <span data-ttu-id="10e21-121">[Visual Studio 2017 verze 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) s nainstalovanou úlohou vývoj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="10e21-121">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="10e21-122">Vyberte příslušný úkol strojového učení.</span><span class="sxs-lookup"><span data-stu-id="10e21-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="10e21-123">Existuje několik způsobů, jak získat přístup k problémům s doporučeními, jako je například doporučený seznam filmů nebo doporučený seznam souvisejících produktů, ale v tomto případě budete předpovídat, jaké hodnocení (1-5) bude uživatel podávat konkrétnímu videu, a doporučit ho, pokud je vyšší než definovaná prahová hodnota (čím vyšší je hodnocení, tím větší je pravděpodobnost, že uživatel míru konkrétní film).</span><span class="sxs-lookup"><span data-stu-id="10e21-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="10e21-124">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="10e21-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="10e21-125">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="10e21-125">Create a project</span></span>

1. <span data-ttu-id="10e21-126">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="10e21-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="10e21-127">Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="10e21-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="10e21-128">V dialogovém okně **Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="10e21-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="10e21-129">Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="10e21-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="10e21-130">Do textového pole **název** zadejte "MovieRecommender" a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="10e21-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="10e21-131">Vytvořte v projektu adresář s názvem *data* pro uložení datové sady:</span><span class="sxs-lookup"><span data-stu-id="10e21-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="10e21-132">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová složka**.</span><span class="sxs-lookup"><span data-stu-id="10e21-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="10e21-133">Zadejte "data" a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="10e21-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="10e21-134">Nainstalujte balíčky NuGet **Microsoft.ml** a **Microsoft. ml. doporučování** :</span><span class="sxs-lookup"><span data-stu-id="10e21-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="10e21-135">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="10e21-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="10e21-136">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet** , vyhledejte **Microsoft.ml**, vyberte balíček v seznamu a klikněte na tlačítko **nainstalovat** .</span><span class="sxs-lookup"><span data-stu-id="10e21-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="10e21-137">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, klikněte na tlačítko **OK** v dialogovém okně **Náhled změn** a potom v dialogovém okně pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="10e21-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="10e21-138">Opakujte tento postup pro **Microsoft. ml. doporučuje**se.</span><span class="sxs-lookup"><span data-stu-id="10e21-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="10e21-139">Do horní části souboru *program.cs* přidejte následující příkazy `using`:</span><span class="sxs-lookup"><span data-stu-id="10e21-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="10e21-140">Stažení dat</span><span class="sxs-lookup"><span data-stu-id="10e21-140">Download your data</span></span>

1. <span data-ttu-id="10e21-141">Stáhněte dvě datové sady a uložte je do složky *dat* , kterou jste vytvořili dříve:</span><span class="sxs-lookup"><span data-stu-id="10e21-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="10e21-142">Klikněte pravým tlačítkem na [*Recommendation-ratings-Train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte Uložit odkaz (nebo cíl) jako...</span><span class="sxs-lookup"><span data-stu-id="10e21-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="10e21-143">Klikněte pravým tlačítkem na [*Recommendation-ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte Uložit odkaz (nebo cíl) jako...</span><span class="sxs-lookup"><span data-stu-id="10e21-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="10e21-144">Nezapomeňte uložit \*soubory. CSV do složky *data* nebo je po uložení jinam přesunout \*soubory. CSV do složky *data* .</span><span class="sxs-lookup"><span data-stu-id="10e21-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="10e21-145">V Průzkumník řešení klikněte pravým tlačítkem na každý ze \*souborů. csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="10e21-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="10e21-146">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="10e21-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![GIF uživatele, který vybírá kopii, pokud je novější v VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a><span data-ttu-id="10e21-148">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="10e21-148">Load your data</span></span>

<span data-ttu-id="10e21-149">Prvním krokem v procesu ML.NET je příprava a načtení modelu školení a testování dat.</span><span class="sxs-lookup"><span data-stu-id="10e21-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="10e21-150">Data hodnocení doporučení jsou rozdělená na `Train` a `Test` datové sady.</span><span class="sxs-lookup"><span data-stu-id="10e21-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="10e21-151">Data `Train` se používají k přizpůsobení modelu.</span><span class="sxs-lookup"><span data-stu-id="10e21-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="10e21-152">`Test`ová data se používají k zajištění předpovědi s vámi vyškolený model a vyhodnocení výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="10e21-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="10e21-153">Je běžné mít 80/20 rozdělení s `Train` a `Test` data.</span><span class="sxs-lookup"><span data-stu-id="10e21-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="10e21-154">Níže je zobrazená ukázka dat z vašich \*souborů. CSV:</span><span class="sxs-lookup"><span data-stu-id="10e21-154">Below is a preview of the data from your \*.csv files:</span></span>

![Snímek obrazovky s náhledem datové sady CVS](./media/movie-recommendation/csv-file-dataset-preview.png)

<span data-ttu-id="10e21-156">V \*soubory. csv existují čtyři sloupce:</span><span class="sxs-lookup"><span data-stu-id="10e21-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="10e21-157">Ve službě Machine Learning se ve sloupcích, které se používají k vytvoření předpovědi, říká [funkce](../resources/glossary.md#feature)a sloupec s vrácenou předpověď se nazývá [popisek](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="10e21-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="10e21-158">Chcete odhadnout hodnocení filmů, takže sloupec hodnocení je `Label`.</span><span class="sxs-lookup"><span data-stu-id="10e21-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="10e21-159">Další tři sloupce, `userId`, `movieId`a `timestamp`, jsou všechny `Features` použity pro předpověď `Label`.</span><span class="sxs-lookup"><span data-stu-id="10e21-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="10e21-160">Funkce</span><span class="sxs-lookup"><span data-stu-id="10e21-160">Features</span></span>      | <span data-ttu-id="10e21-161">Popisek</span><span class="sxs-lookup"><span data-stu-id="10e21-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="10e21-162">K tomu, abyste se rozhodli, které `Features` se používají k předpovídání `Label`.</span><span class="sxs-lookup"><span data-stu-id="10e21-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="10e21-163">Můžete také použít metody, jako je například [funkce permutace důležitost](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) , k usnadnění výběru nejlepší `Features`.</span><span class="sxs-lookup"><span data-stu-id="10e21-163">You can also use methods like [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="10e21-164">V takovém případě byste měli omezit `timestamp` sloupec jako `Feature`, protože časové razítko skutečně neovlivňuje způsob, jakým se uživatel podílí na videu, a proto by nemohl přispět k přesnější předpovědi:</span><span class="sxs-lookup"><span data-stu-id="10e21-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="10e21-165">Funkce</span><span class="sxs-lookup"><span data-stu-id="10e21-165">Features</span></span>      | <span data-ttu-id="10e21-166">Popisek</span><span class="sxs-lookup"><span data-stu-id="10e21-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="10e21-167">Dále musíte definovat datovou strukturu pro vstupní třídu.</span><span class="sxs-lookup"><span data-stu-id="10e21-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="10e21-168">Přidejte do projektu novou třídu:</span><span class="sxs-lookup"><span data-stu-id="10e21-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="10e21-169">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="10e21-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="10e21-170">V **dialogovém okně Přidat novou položku**vyberte **třída** a změňte pole **název** na *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="10e21-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="10e21-171">Pak vyberte tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="10e21-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="10e21-172">V editoru kódu se otevře soubor *MovieRatingData.cs* .</span><span class="sxs-lookup"><span data-stu-id="10e21-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="10e21-173">Do horní části *MovieRatingData.cs*přidejte následující příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="10e21-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="10e21-174">Vytvořte třídu s názvem `MovieRating` odebráním existující definice třídy a přidáním následujícího kódu do *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="10e21-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="10e21-175">`MovieRating` určuje vstupní datovou třídu.</span><span class="sxs-lookup"><span data-stu-id="10e21-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="10e21-176">Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny.</span><span class="sxs-lookup"><span data-stu-id="10e21-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="10e21-177">Sloupce `userId` a `movieId` jsou vaše `Features` (vstupy, které model udělíte pro předpověď `Label`), a sloupec hodnocení je `Label`, který budete předpovídat (výstup modelu).</span><span class="sxs-lookup"><span data-stu-id="10e21-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="10e21-178">Vytvořte další třídu, `MovieRatingPrediction`, která představuje předpovězené výsledky přidáním následujícího kódu za `MovieRating` třídy v *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="10e21-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="10e21-179">V *program.cs*nahraďte `Console.WriteLine("Hello World!")` následujícím kódem v rámci `Main()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="10e21-180">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace ml.NET a inicializuje `mlContext` vytvoří nové prostředí ml.NET, které lze sdílet napříč objekty pracovního postupu vytváření modelů.</span><span class="sxs-lookup"><span data-stu-id="10e21-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="10e21-181">Je podobný a koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="10e21-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="10e21-182">Po `Main()`vytvořit metodu nazvanou `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="10e21-183">Tato metoda vám poskytne chybu, dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="10e21-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="10e21-184">Inicializujte proměnné cesty k datům, načtěte data ze souborů \*. csv a vraťte `Train` a `Test` data jako objekty `IDataView` přidáním následujícího jako další řádek kódu v `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="10e21-185">Data v ML.NET jsou reprezentována jako [Třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="10e21-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="10e21-186">`IDataView` je flexibilní a efektivní způsob popisující tabulková data (číselná a text).</span><span class="sxs-lookup"><span data-stu-id="10e21-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="10e21-187">Data je možné načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="10e21-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="10e21-188">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte data v souboru.</span><span class="sxs-lookup"><span data-stu-id="10e21-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="10e21-189">Převezme proměnné cesty k datům a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="10e21-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="10e21-190">V takovém případě zadáte cestu pro soubory `Test` a `Train` a naznačíte hlavičku textového souboru (aby bylo možné použít názvy sloupců správně) a oddělovač dat znaků čárky (výchozí oddělovač je karta).</span><span class="sxs-lookup"><span data-stu-id="10e21-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="10e21-191">Do metody `Main()` přidejte následující kód, který volá metodu `LoadData()` a vrátí `Train` a `Test` data:</span><span class="sxs-lookup"><span data-stu-id="10e21-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="10e21-192">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-192">Build and train your model</span></span>

<span data-ttu-id="10e21-193">Existují tři hlavní koncepty v ML.NET: [data](../resources/glossary.md#data), [transformátory](../resources/glossary.md#transformer)a [odhady](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="10e21-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="10e21-194">Školicí algoritmy Machine Learning vyžadují data v určitém formátu.</span><span class="sxs-lookup"><span data-stu-id="10e21-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="10e21-195">`Transformers` slouží k transformaci tabulkových dat do kompatibilního formátu.</span><span class="sxs-lookup"><span data-stu-id="10e21-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Diagram toku dat transformátoru](./media/movie-recommendation/data-transformer-transformed.png)

<span data-ttu-id="10e21-197">`Transformers` vytvoříte v ML.NET vytvořením `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="10e21-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="10e21-198">`Estimators` přebírat data a vracet `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="10e21-198">`Estimators` take in data and return `Transformers`.</span></span>

![Diagram toku dat Estimator](./media/movie-recommendation/data-estimator-transformer.png)

<span data-ttu-id="10e21-200">Příkladem `Estimator`je algoritmus školení doporučení, který budete používat pro školení modelu.</span><span class="sxs-lookup"><span data-stu-id="10e21-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="10e21-201">Sestavte `Estimator` pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="10e21-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="10e21-202">Vytvořte metodu `BuildAndTrainModel()` hned za metodou `LoadData()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="10e21-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="10e21-203">Tato metoda vám poskytne chybu, dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="10e21-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="10e21-204">Definujte transformace dat přidáním následujícího kódu do `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="10e21-205">Vzhledem k tomu, že `userId` a `movieId` reprezentují uživatelské a filmové tituly, ne reálné hodnoty, použijte metodu [MapValueToKey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pro transformaci každého `userId` a každého `movieId` do sloupce číselného klíče `Feature` sloupec (formát přijatý pomocí algoritmů doporučení) a přidejte je jako nové sloupce datové sady:</span><span class="sxs-lookup"><span data-stu-id="10e21-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="10e21-206">userId</span><span class="sxs-lookup"><span data-stu-id="10e21-206">userId</span></span> | <span data-ttu-id="10e21-207">movieId</span><span class="sxs-lookup"><span data-stu-id="10e21-207">movieId</span></span> | <span data-ttu-id="10e21-208">Popisek</span><span class="sxs-lookup"><span data-stu-id="10e21-208">Label</span></span> | <span data-ttu-id="10e21-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="10e21-209">userIdEncoded</span></span> | <span data-ttu-id="10e21-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="10e21-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="10e21-211">1</span><span class="sxs-lookup"><span data-stu-id="10e21-211">1</span></span> | <span data-ttu-id="10e21-212">1</span><span class="sxs-lookup"><span data-stu-id="10e21-212">1</span></span> | <span data-ttu-id="10e21-213">4</span><span class="sxs-lookup"><span data-stu-id="10e21-213">4</span></span> | <span data-ttu-id="10e21-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="10e21-214">userKey1</span></span> | <span data-ttu-id="10e21-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="10e21-215">movieKey1</span></span> |
| <span data-ttu-id="10e21-216">1</span><span class="sxs-lookup"><span data-stu-id="10e21-216">1</span></span> | <span data-ttu-id="10e21-217">3</span><span class="sxs-lookup"><span data-stu-id="10e21-217">3</span></span> | <span data-ttu-id="10e21-218">4</span><span class="sxs-lookup"><span data-stu-id="10e21-218">4</span></span> | <span data-ttu-id="10e21-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="10e21-219">userKey1</span></span> | <span data-ttu-id="10e21-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="10e21-220">movieKey2</span></span> |
| <span data-ttu-id="10e21-221">1</span><span class="sxs-lookup"><span data-stu-id="10e21-221">1</span></span> | <span data-ttu-id="10e21-222">6</span><span class="sxs-lookup"><span data-stu-id="10e21-222">6</span></span> | <span data-ttu-id="10e21-223">4</span><span class="sxs-lookup"><span data-stu-id="10e21-223">4</span></span> | <span data-ttu-id="10e21-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="10e21-224">userKey1</span></span> | <span data-ttu-id="10e21-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="10e21-225">movieKey3</span></span> |

<span data-ttu-id="10e21-226">Vyberte algoritmus strojového učení a přidejte ho k definicím transformace dat. Přidejte následující kód jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="10e21-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je váš školicí algoritmus pro doporučení.</span><span class="sxs-lookup"><span data-stu-id="10e21-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="10e21-228">Vytváření [matic](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je obvyklým přístupem k doporučením, když máte data o tom, jak uživatelé mají v minulosti hodnocené produkty, což je případ datových sad v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="10e21-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="10e21-229">Existují i další algoritmy doporučení, pokud máte dostupná jiná data (Další informace najdete v části [ostatní algoritmy doporučení](#other-recommendation-algorithms) níže).</span><span class="sxs-lookup"><span data-stu-id="10e21-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="10e21-230">V takovém případě používá algoritmus `Matrix Factorization` metodu nazvanou "filtrování spolupráce", což předpokládá, že pokud uživatel 1 má stejné stanovisko jako uživatel 2 k určitému problému, pak uživatel 1 je pravděpodobnější, že uživatel 2 má stejný způsob jako uživatel 2 o jiném problému.</span><span class="sxs-lookup"><span data-stu-id="10e21-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="10e21-231">Například pokud uživatel 1 a uživatel 2 znamená filmy podobně, je pravděpodobnější, že uživatel 2 požívá film, který uživatel 1 sledoval a hodnotil vysoce:</span><span class="sxs-lookup"><span data-stu-id="10e21-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="10e21-232">Uživatel 1</span><span class="sxs-lookup"><span data-stu-id="10e21-232">User 1</span></span> | <span data-ttu-id="10e21-233">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="10e21-233">Watched and liked movie</span></span> | <span data-ttu-id="10e21-234">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="10e21-234">Watched and liked movie</span></span> | <span data-ttu-id="10e21-235">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="10e21-235">Watched and liked movie</span></span> |
| <span data-ttu-id="10e21-236">Uživatel 2</span><span class="sxs-lookup"><span data-stu-id="10e21-236">User 2</span></span> | <span data-ttu-id="10e21-237">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="10e21-237">Watched and liked movie</span></span> | <span data-ttu-id="10e21-238">Sledovaný a nelíbí se film</span><span class="sxs-lookup"><span data-stu-id="10e21-238">Watched and liked movie</span></span> | <span data-ttu-id="10e21-239">Nesledováno – doporučit video</span><span class="sxs-lookup"><span data-stu-id="10e21-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="10e21-240">`Matrix Factorization` Trainer má několik [možností](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), které si můžete přečíst v části s [parametry algoritmu](#algorithm-hyperparameters) níže.</span><span class="sxs-lookup"><span data-stu-id="10e21-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="10e21-241">Přizpůsobit model na `Train`á data a vrátit vyškolený model přidáním následujícího jako další řádek kódu v metodě `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="10e21-242">Metoda [přizpůsobení ():](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) nahlaste svůj model pomocí poskytnuté datové sady školení.</span><span class="sxs-lookup"><span data-stu-id="10e21-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="10e21-243">Technicky, provádí `Estimator` definice pomocí transformace dat a použití školení a vrátí zpět školicí model, což je `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="10e21-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="10e21-244">Přidejte následující jako další řádek kódu v metodě `Main()` pro volání metody `BuildAndTrainModel()` a vraťte si školený model:</span><span class="sxs-lookup"><span data-stu-id="10e21-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="10e21-245">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-245">Evaluate your model</span></span>

<span data-ttu-id="10e21-246">Jakmile svůj model provedete, použijte k vyhodnocení způsobu provádění modelu testovací data.</span><span class="sxs-lookup"><span data-stu-id="10e21-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="10e21-247">Vytvořte metodu `EvaluateModel()` hned za metodou `BuildAndTrainModel()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="10e21-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="10e21-248">Transformujte data `Test` přidáním následujícího kódu do `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="10e21-249">Metoda [Transforming ()](xref:Microsoft.ML.ITransformer.Transform%2A) zpřístupňuje předpovědi pro více zadaných vstupních řádků testovací sady dat.</span><span class="sxs-lookup"><span data-stu-id="10e21-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="10e21-250">Vyhodnoťte model přidáním následujícího jako další řádek kódu v metodě `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="10e21-251">Jakmile máte předpověď nastavenou, metoda [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) posuzuje model, který porovnává předpovězené hodnoty se skutečným `Labels` v testovací sadě a vrací metriky, jak model provádí.</span><span class="sxs-lookup"><span data-stu-id="10e21-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="10e21-252">Vytiskněte metriky vyhodnocení do konzoly přidáním následujícího jako další řádek kódu v metodě `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="10e21-253">Přidejte následující jako další řádek kódu v metodě `Main()` pro volání metody `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="10e21-254">Výstup by měl vypadat podobně jako v následujícím textu:</span><span class="sxs-lookup"><span data-stu-id="10e21-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="10e21-255">V tomto výstupu existují 20 iterací.</span><span class="sxs-lookup"><span data-stu-id="10e21-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="10e21-256">V každé iteraci se míra chyb zmenší a konverguje blíž a blíže k hodnotě 0.</span><span class="sxs-lookup"><span data-stu-id="10e21-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="10e21-257">`root of mean squared error` (RMS nebo RMSE) slouží k měření rozdílů mezi předpovězenými hodnotami modelu a datovou datovou sadou pozorovaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="10e21-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="10e21-258">Technicky je to druhá odmocnina průměru průměrných čtverců chyb.</span><span class="sxs-lookup"><span data-stu-id="10e21-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="10e21-259">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="10e21-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="10e21-260">`R Squared` určuje, jak dobře data vyhovují modelu.</span><span class="sxs-lookup"><span data-stu-id="10e21-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="10e21-261">Rozsah od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="10e21-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="10e21-262">Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu.</span><span class="sxs-lookup"><span data-stu-id="10e21-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="10e21-263">Hodnota 1 znamená, že model přesně odpovídá datům.</span><span class="sxs-lookup"><span data-stu-id="10e21-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="10e21-264">Požadujete, aby se skóre `R Squared` co nejblíže k 1.</span><span class="sxs-lookup"><span data-stu-id="10e21-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="10e21-265">Sestavování úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="10e21-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="10e21-266">Tento model má počáteční nižší kvalitu, protože kurz používá pro zajištění rychlého školení modelů malé datové sady.</span><span class="sxs-lookup"><span data-stu-id="10e21-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="10e21-267">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit ho zlepšit poskytnutím větších školicích datových sad nebo výběrem různých školicích algoritmů s různými parametry Hyper-v pro každý algoritmus.</span><span class="sxs-lookup"><span data-stu-id="10e21-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="10e21-268">Další informace najdete v části [vylepšení modelu](#improve-your-model) níže.</span><span class="sxs-lookup"><span data-stu-id="10e21-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="10e21-269">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-269">Use your model</span></span>

<span data-ttu-id="10e21-270">Nyní můžete použít svůj vycvičený model k vytvoření předpovědi pro nová data.</span><span class="sxs-lookup"><span data-stu-id="10e21-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="10e21-271">Vytvořte metodu `UseModelForSinglePrediction()` hned za metodou `EvaluateModel()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="10e21-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="10e21-272">Pomocí `PredictionEngine` předpovědět hodnocení přidáním následujícího kódu do `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="10e21-273">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je praktické rozhraní API, které umožňuje provádět předpovědi pro jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="10e21-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="10e21-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="10e21-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="10e21-275">Je přijatelné pro použití v prostředích s jedním vláknem nebo prototypem.</span><span class="sxs-lookup"><span data-stu-id="10e21-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="10e21-276">Pro zvýšení výkonu a bezpečnosti vláken v produkčních prostředích použijte službu `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="10e21-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="10e21-277">V této příručce najdete informace o tom, jak [používat `PredictionEnginePool` ve ASP.NET corem webovém rozhraní API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="10e21-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="10e21-278">rozšíření služby `PredictionEnginePool` je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="10e21-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="10e21-279">Vytvořte instanci `MovieRating` nazvanou `testInput` a předejte ji do modulu předpovědi přidáním následujícího jako další řádky kódu v metodě `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="10e21-280">Funkce [prediktivní ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) provede předpověď na jeden sloupec dat.</span><span class="sxs-lookup"><span data-stu-id="10e21-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="10e21-281">Pak můžete použít `Score`nebo předpovězené hodnocení, abyste zjistili, jestli chcete pro uživatele 6 doporučit video s movieId 10.</span><span class="sxs-lookup"><span data-stu-id="10e21-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="10e21-282">Čím vyšší je `Score`, tím větší je pravděpodobnost, že uživatel míru konkrétní film.</span><span class="sxs-lookup"><span data-stu-id="10e21-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="10e21-283">V takovém případě řekněme, že doporučujeme filmy s předpokládaným hodnocením > 3,5.</span><span class="sxs-lookup"><span data-stu-id="10e21-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="10e21-284">Chcete-li vytisknout výsledky, přidejte následující jako další řádky kódu v metodě `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="10e21-285">Přidejte následující jako další řádek kódu v metodě `Main()` pro volání metody `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="10e21-286">Výstup této metody by měl vypadat podobně jako následující text:</span><span class="sxs-lookup"><span data-stu-id="10e21-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="10e21-287">Uložení modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-287">Save your model</span></span>

<span data-ttu-id="10e21-288">Pokud chcete model použít k tomu, aby předpovědi aplikace pro koncové uživatele, musíte nejdřív model Uložit.</span><span class="sxs-lookup"><span data-stu-id="10e21-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="10e21-289">Vytvořte metodu `SaveModel()` hned za metodou `UseModelForSinglePrediction()` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="10e21-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="10e21-290">Uložte svůj vycvičený model přidáním následujícího kódu do metody `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="10e21-291">Tato metoda uloží váš vyškolený model do souboru. zip (do složky "data"), který pak můžete použít v jiných aplikacích .NET k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="10e21-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="10e21-292">Přidejte následující jako další řádek kódu v metodě `Main()` pro volání metody `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="10e21-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="10e21-293">Použití uloženého modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-293">Use your saved model</span></span>

<span data-ttu-id="10e21-294">Po uložení svého vyučeného modelu můžete model využívat v různých prostředích.</span><span class="sxs-lookup"><span data-stu-id="10e21-294">Once you have saved your trained model, you can consume the model in different environments.</span></span> <span data-ttu-id="10e21-295">Další informace o tom, jak zprovoznění model strojového učení v aplikacích, najdete v tématu [ukládání a načítání](../how-to-guides/save-load-machine-learning-models-ml-net.md) školicích modelů.</span><span class="sxs-lookup"><span data-stu-id="10e21-295">See [Save and load trained models](../how-to-guides/save-load-machine-learning-models-ml-net.md) to learn how to operationalize a trained machine learning model in apps.</span></span>

## <a name="results"></a><span data-ttu-id="10e21-296">Výsledky</span><span class="sxs-lookup"><span data-stu-id="10e21-296">Results</span></span>

<span data-ttu-id="10e21-297">Po provedení kroků uvedených výše spusťte konzolovou aplikaci (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="10e21-297">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="10e21-298">Vaše výsledky z jedné předpovědi výše by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="10e21-298">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="10e21-299">Můžou se zobrazovat upozornění nebo zprávy o zpracování, ale tyto zprávy se z následujících výsledků odebraly z důvodu srozumitelnosti.</span><span class="sxs-lookup"><span data-stu-id="10e21-299">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="10e21-300">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="10e21-300">Congratulations!</span></span> <span data-ttu-id="10e21-301">Teď jste úspěšně vytvořili model strojového učení pro doporučování filmů.</span><span class="sxs-lookup"><span data-stu-id="10e21-301">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="10e21-302">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .</span><span class="sxs-lookup"><span data-stu-id="10e21-302">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="10e21-303">Vylepšení modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-303">Improve your model</span></span>

<span data-ttu-id="10e21-304">Existuje několik způsobů, jak můžete zlepšit výkon modelu, abyste mohli získat přesnější předpovědi.</span><span class="sxs-lookup"><span data-stu-id="10e21-304">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="10e21-305">Data</span><span class="sxs-lookup"><span data-stu-id="10e21-305">Data</span></span>

<span data-ttu-id="10e21-306">Přidání dalších školicích dat, která mají dostatek ukázek pro každého uživatele a ID filmu, může pomoci zlepšit kvalitu modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="10e21-306">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="10e21-307">[Mezi ověřováním](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) je metoda pro vyhodnocování modelů, které náhodně rozdělí data do podmnožiny (místo extrakce testovacích dat z datové sady, jako jste to udělali v tomto kurzu), a jako testovací data převezme některé skupiny jako data výukového programu.</span><span class="sxs-lookup"><span data-stu-id="10e21-307">[Cross validation](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="10e21-308">Tato metoda vykonává rozdělení výukového testu z hlediska kvality modelu.</span><span class="sxs-lookup"><span data-stu-id="10e21-308">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="10e21-309">Funkce</span><span class="sxs-lookup"><span data-stu-id="10e21-309">Features</span></span>

<span data-ttu-id="10e21-310">V tomto kurzu použijete jenom tři `Features` (`user id`, `movie id`a `rating`), které jsou k dispozici v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="10e21-310">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="10e21-311">I když je to dobrý začátek, možná budete chtít přidat další atributy nebo `Features` (například věk, pohlaví, geografické umístění atd.), pokud jsou zahrnuté v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="10e21-311">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="10e21-312">Přidání dalších relevantních `Features` může pomoci zlepšit výkon vašeho modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="10e21-312">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="10e21-313">Pokud si nejste jistí, které `Features` můžou být pro úlohu strojového učení nejrelevantnější, můžete také využít [důležitou funkci](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)výpočtu příspěvků funkcí (FCC) a permutace, která ml.NET poskytuje k tomu, co nejvíc nemonitorovaných `Features`.</span><span class="sxs-lookup"><span data-stu-id="10e21-313">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="10e21-314">Parametry algoritmu</span><span class="sxs-lookup"><span data-stu-id="10e21-314">Algorithm hyperparameters</span></span>

<span data-ttu-id="10e21-315">I když ML.NET poskytuje dobré výchozí algoritmy pro školení, můžete ještě více ladit výkon změnou [parametrů](../resources/glossary.md#hyperparameter)algoritmu.</span><span class="sxs-lookup"><span data-stu-id="10e21-315">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="10e21-316">Pro `Matrix Factorization`můžete experimentovat s parametry, jako je [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , abyste viděli, jestli vám dává lepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="10e21-316">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="10e21-317">Například v tomto kurzu jsou k disřadě možnosti algoritmu:</span><span class="sxs-lookup"><span data-stu-id="10e21-317">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="10e21-318">Další algoritmy doporučení</span><span class="sxs-lookup"><span data-stu-id="10e21-318">Other Recommendation Algorithms</span></span>

<span data-ttu-id="10e21-319">Algoritmus vyfaktoringu matice s filtrováním pro spolupráci je jediným řešením pro provádění doporučení filmu.</span><span class="sxs-lookup"><span data-stu-id="10e21-319">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="10e21-320">V mnoha případech možná nemáte dostupná data hodnocení a k dispozici máte jenom historii filmů od uživatelů.</span><span class="sxs-lookup"><span data-stu-id="10e21-320">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="10e21-321">V jiných případech možná budete mít více než jenom data hodnocení uživatele.</span><span class="sxs-lookup"><span data-stu-id="10e21-321">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="10e21-322">Algoritmus</span><span class="sxs-lookup"><span data-stu-id="10e21-322">Algorithm</span></span>       | <span data-ttu-id="10e21-323">Scénář</span><span class="sxs-lookup"><span data-stu-id="10e21-323">Scenario</span></span>           | <span data-ttu-id="10e21-324">Ukázka</span><span class="sxs-lookup"><span data-stu-id="10e21-324">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="10e21-325">Faktor vytváření matic třídy</span><span class="sxs-lookup"><span data-stu-id="10e21-325">One Class Matrix Factorization</span></span> | <span data-ttu-id="10e21-326">Toto použijte, když máte jenom userId a movieId.</span><span class="sxs-lookup"><span data-stu-id="10e21-326">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="10e21-327">Tento styl doporučení je založen na scénáři společného nákupu, nebo na produktech, které se často kupují, což znamená, že zákazníkům doporučí sadu produktů na základě vlastní historie nákupních objednávek.</span><span class="sxs-lookup"><span data-stu-id="10e21-327">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="10e21-328">> vyzkoušet</span><span class="sxs-lookup"><span data-stu-id="10e21-328">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="10e21-329">Počítače pro vytváření faktoringu s podporou polí</span><span class="sxs-lookup"><span data-stu-id="10e21-329">Field Aware Factorization Machines</span></span> | <span data-ttu-id="10e21-330">Použijte k tomu doporučení, když máte víc funkcí nad ID uživatele, productId a hodnocení (například popis produktu nebo cena produktu).</span><span class="sxs-lookup"><span data-stu-id="10e21-330">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="10e21-331">Tato metoda také používá přístup pro filtrování spolupráce.</span><span class="sxs-lookup"><span data-stu-id="10e21-331">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="10e21-332">> vyzkoušet</span><span class="sxs-lookup"><span data-stu-id="10e21-332">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="10e21-333">Scénář nového uživatele</span><span class="sxs-lookup"><span data-stu-id="10e21-333">New user scenario</span></span>

<span data-ttu-id="10e21-334">Jedním z běžných potíží při filtrování spolupráce je problém s studeným startem, který je v případě, že máte nového uživatele, který nemá žádná předchozí data pro vykreslování odvození z.</span><span class="sxs-lookup"><span data-stu-id="10e21-334">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="10e21-335">Tento problém se často vyřeší tím, že požádá nového uživatele, aby vytvořil profil a například rychlost, jakou videa viděli v minulosti.</span><span class="sxs-lookup"><span data-stu-id="10e21-335">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="10e21-336">I když tato metoda přináší uživateli určitou režii, poskytuje několik počátečních dat pro nové uživatele bez historie hodnocení.</span><span class="sxs-lookup"><span data-stu-id="10e21-336">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="10e21-337">Zdroje</span><span class="sxs-lookup"><span data-stu-id="10e21-337">Resources</span></span>

<span data-ttu-id="10e21-338">Data použitá v tomto kurzu jsou odvozena z [datové sady MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="10e21-338">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="10e21-339">Další kroky</span><span class="sxs-lookup"><span data-stu-id="10e21-339">Next steps</span></span>

<span data-ttu-id="10e21-340">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="10e21-340">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="10e21-341">Vyberte algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="10e21-341">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="10e21-342">Příprava a načtení dat</span><span class="sxs-lookup"><span data-stu-id="10e21-342">Prepare and load your data</span></span>
> * <span data-ttu-id="10e21-343">Sestavování a výuka modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-343">Build and train a model</span></span>
> * <span data-ttu-id="10e21-344">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-344">Evaluate a model</span></span>
> * <span data-ttu-id="10e21-345">Nasazení a využití modelu</span><span class="sxs-lookup"><span data-stu-id="10e21-345">Deploy and consume a model</span></span>

<span data-ttu-id="10e21-346">Pokud se chcete dozvědět víc, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="10e21-346">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="10e21-347">Analýza mínění</span><span class="sxs-lookup"><span data-stu-id="10e21-347">Sentiment Analysis</span></span>](sentiment-analysis.md)
