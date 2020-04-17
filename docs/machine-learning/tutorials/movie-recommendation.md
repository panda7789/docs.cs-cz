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
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a><span data-ttu-id="dded6-104">Kurz: Vytvořte film doporučující pomocí matice faktorizace s ML.NET</span><span class="sxs-lookup"><span data-stu-id="dded6-104">Tutorial: Build a movie recommender using matrix factorization with ML.NET</span></span>

<span data-ttu-id="dded6-105">Tento kurz ukazuje, jak vytvořit doporučujefilm s ML.NET v aplikaci konzoly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dded6-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="dded6-106">Kroky používají C# a Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="dded6-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="dded6-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="dded6-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="dded6-108">Výběr algoritmu strojového učení</span><span class="sxs-lookup"><span data-stu-id="dded6-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="dded6-109">Příprava a načtení dat</span><span class="sxs-lookup"><span data-stu-id="dded6-109">Prepare and load your data</span></span>
> * <span data-ttu-id="dded6-110">Sestavení a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-110">Build and train a model</span></span>
> * <span data-ttu-id="dded6-111">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-111">Evaluate a model</span></span>
> * <span data-ttu-id="dded6-112">Nasazení a využití modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-112">Deploy and consume a model</span></span>

<span data-ttu-id="dded6-113">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)</span><span class="sxs-lookup"><span data-stu-id="dded6-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="dded6-114">Pracovní postup strojového učení</span><span class="sxs-lookup"><span data-stu-id="dded6-114">Machine learning workflow</span></span>

<span data-ttu-id="dded6-115">K dokončení úkolu a všech dalších ML.NET úkolu použijete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="dded6-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="dded6-116">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="dded6-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="dded6-117">Sestavte a trénujte svůj model</span><span class="sxs-lookup"><span data-stu-id="dded6-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="dded6-118">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="dded6-119">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="dded6-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dded6-120">Prerequisites</span></span>

* <span data-ttu-id="dded6-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější nebo Visual Studio 2017 verze 15.6 nebo novější s nainstalovanou úlohou "Vývoj napříč platformami..NET Core cross-platform".</span><span class="sxs-lookup"><span data-stu-id="dded6-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="dded6-122">Výběr příslušného úkolu strojového učení</span><span class="sxs-lookup"><span data-stu-id="dded6-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="dded6-123">Existuje několik způsobů, jak přistupovat k problémům s doporučeními, jako je například doporučení seznamu filmů nebo doporučení seznamu souvisejících produktů, ale v tomto případě předevíte, jaké hodnocení (1-5) uživatel poskytne určitému filmu, a doporučí tento film, pokud je vyšší než definovaná prahová hodnota (čím vyšší je hodnocení, tím vyšší je pravděpodobnost, že uživatel bude mít rád konkrétní film).</span><span class="sxs-lookup"><span data-stu-id="dded6-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="dded6-124">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="dded6-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="dded6-125">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="dded6-125">Create a project</span></span>

1. <span data-ttu-id="dded6-126">Otevřete sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="dded6-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="dded6-127">Na řádku nabídek vyberte **Soubor** > **nového** > **projektu.**</span><span class="sxs-lookup"><span data-stu-id="dded6-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="dded6-128">V dialogovém okně **Nový projekt** vyberte uzel **Visual C#** následovaný uzlem **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="dded6-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="dded6-129">Pak vyberte šablonu projektu **Konzola Aplikace (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="dded6-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="dded6-130">Do textového pole **Název** zadejte "MovieRecommender" a pak vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="dded6-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="dded6-131">Vytvořte adresář s názvem *Data* v projektu pro uložení datové sady:</span><span class="sxs-lookup"><span data-stu-id="dded6-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="dded6-132">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="dded6-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="dded6-133">Zadejte "Data" a stiskněte enter.</span><span class="sxs-lookup"><span data-stu-id="dded6-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="dded6-134">Nainstalujte **balíčky NuGet Microsoft.ML** a **Microsoft.ML.Recommender:**</span><span class="sxs-lookup"><span data-stu-id="dded6-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="dded6-135">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="dded6-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dded6-136">Jako zdroj balíčku zvolte "nuget.org", vyberte kartu **Procházet,** vyhledejte **Microsoft.ML**, vyberte balíček v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="dded6-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dded6-137">V dialogovém okně **Náhled změn** vyberte tlačítko **Ok** a pak v dialogovém okně **Přijetí licence** vyberte tlačítko **Přijmout,** pokud souhlasíte s licenčními podmínkami pro uvedené balíčky.</span><span class="sxs-lookup"><span data-stu-id="dded6-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="dded6-138">Opakujte tento postup pro **Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="dded6-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="dded6-139">V horní `using` části *Program.cs* souboru přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="dded6-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="dded6-140">Stažení dat</span><span class="sxs-lookup"><span data-stu-id="dded6-140">Download your data</span></span>

1. <span data-ttu-id="dded6-141">Stáhněte si dvě datové sady a uložte je do dříve vytvořené *datové* složky:</span><span class="sxs-lookup"><span data-stu-id="dded6-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="dded6-142">Klikněte pravým tlačítkem myši na [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte "Uložit odkaz (nebo cíl) Jako ..."</span><span class="sxs-lookup"><span data-stu-id="dded6-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="dded6-143">Klikněte pravým tlačítkem myši na [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte "Uložit odkaz (nebo cíl) jako..."</span><span class="sxs-lookup"><span data-stu-id="dded6-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="dded6-144">Ujistěte se, \*že soubory .csv uložíte do složky *Data,* nebo je po uložení jinde přesuňte soubory \*.csv do složky *Data.*</span><span class="sxs-lookup"><span data-stu-id="dded6-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="dded6-145">V Průzkumníku řešení klepněte \*pravým tlačítkem myši na jednotlivé soubory .csv a vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="dded6-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="dded6-146">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="dded6-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![GIF uživatele, který vybírá kopii, pokud je novější ve VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a><span data-ttu-id="dded6-148">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="dded6-148">Load your data</span></span>

<span data-ttu-id="dded6-149">Prvním krokem v procesu ML.NET je připravit a načíst data školení a testování modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="dded6-150">Data hodnocení doporučení jsou `Train` `Test` rozdělena do datových sad a jsou rozdělena.</span><span class="sxs-lookup"><span data-stu-id="dded6-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="dded6-151">Data `Train` se používají k přizpůsobení modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="dded6-152">Data `Test` se používá k předpovědi s trénovaný model a vyhodnotit výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="dded6-153">Je běžné mít 80/20 rozdělit `Train` s `Test` a data.</span><span class="sxs-lookup"><span data-stu-id="dded6-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="dded6-154">Níže je náhled dat z \*vašich souborů .csv:</span><span class="sxs-lookup"><span data-stu-id="dded6-154">Below is a preview of the data from your \*.csv files:</span></span>

![Snímek obrazovky s náhledem datové sady CVS](./media/movie-recommendation/csv-file-dataset-preview.png)

<span data-ttu-id="dded6-156">V \*souborech .csv jsou čtyři sloupce:</span><span class="sxs-lookup"><span data-stu-id="dded6-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="dded6-157">Ve strojovém učení se sloupce, které se používají k vytvoření předpovědi, nazývají [Funkce](../resources/glossary.md#feature)a sloupec s vrácenou predikcí se nazývá [Label](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="dded6-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="dded6-158">Chcete předpovědět hodnocení filmů, takže sloupec `Label`hodnocení je .</span><span class="sxs-lookup"><span data-stu-id="dded6-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="dded6-159">Další tři sloupce `userId` `movieId`, `timestamp` , `Features` a všechny `Label`se používají k předvídání .</span><span class="sxs-lookup"><span data-stu-id="dded6-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="dded6-160">Funkce</span><span class="sxs-lookup"><span data-stu-id="dded6-160">Features</span></span>      | <span data-ttu-id="dded6-161">Popisek</span><span class="sxs-lookup"><span data-stu-id="dded6-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="dded6-162">Je na vás, rozhodnout, které `Features` se `Label`používají k předvídání .</span><span class="sxs-lookup"><span data-stu-id="dded6-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="dded6-163">Můžete také použít metody, jako [je důležitost funkce permutace,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) které vám pomohou s výběrem toho nejlepšího `Features`.</span><span class="sxs-lookup"><span data-stu-id="dded6-163">You can also use methods like [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="dded6-164">V takovém případě byste `timestamp` měli sloupec `Feature` odstranit jako a protože časové razítko ve skutečnosti nemá vliv na to, jak uživatel hodnotí daný film, a proto by nepřispělk přesnější predikci:</span><span class="sxs-lookup"><span data-stu-id="dded6-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="dded6-165">Funkce</span><span class="sxs-lookup"><span data-stu-id="dded6-165">Features</span></span>      | <span data-ttu-id="dded6-166">Popisek</span><span class="sxs-lookup"><span data-stu-id="dded6-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="dded6-167">Dále je nutné definovat strukturu dat pro vstupní třídu.</span><span class="sxs-lookup"><span data-stu-id="dded6-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="dded6-168">Přidání nové třídy do projektu:</span><span class="sxs-lookup"><span data-stu-id="dded6-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="dded6-169">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a potom vyberte **přidat > novou položku**.</span><span class="sxs-lookup"><span data-stu-id="dded6-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="dded6-170">V **dialogovém okně Přidat novou položku**vyberte **Třídu** a změňte pole **Název** na *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="dded6-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="dded6-171">Potom vyberte tlačítko **Přidat.**</span><span class="sxs-lookup"><span data-stu-id="dded6-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="dded6-172">Soubor *MovieRatingData.cs* se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dded6-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="dded6-173">Na začátek `using` *MovieRatingData.cs*přidejte následující příkaz :</span><span class="sxs-lookup"><span data-stu-id="dded6-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="dded6-174">Vytvořte třídu volanou `MovieRating` odebráním existující definice třídy a přidáním následujícího kódu v *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="dded6-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="dded6-175">`MovieRating`určuje třídu vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="dded6-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="dded6-176">Atribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) určuje, které sloupce (podle indexu sloupce) v datové sadě by měly být načteny.</span><span class="sxs-lookup"><span data-stu-id="dded6-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="dded6-177">Sloupce `userId` `movieId` a jsou `Features` vaše (vstupy, které poskytnete `Label`modelu předpovědět ) `Label` a sloupec hodnocení je ten, který budete předpovídat (výstup modelu).</span><span class="sxs-lookup"><span data-stu-id="dded6-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="dded6-178">Vytvořte jinou třídu , `MovieRatingPrediction`chcete-li reprezentovat `MovieRating` předpokládané výsledky přidáním následujícího kódu za třídu v *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="dded6-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="dded6-179">V *Program.cs*nahraďte `Console.WriteLine("Hello World!")` uvnitř `Main()`následující kód :</span><span class="sxs-lookup"><span data-stu-id="dded6-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="dded6-180">[Třída MLContext](xref:Microsoft.ML.MLContext) je výchozím bodem pro všechny operace `mlContext` ML.NET a inicializace vytvoří nové prostředí ML.NET, které lze sdílet mezi objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="dded6-181">Je to podobné, koncepčně, v `DBContext` entity frameworku.</span><span class="sxs-lookup"><span data-stu-id="dded6-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="dded6-182">Po `Main()`, vytvořte `LoadData()`metodu s názvem :</span><span class="sxs-lookup"><span data-stu-id="dded6-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="dded6-183">Tato metoda vám dá chybu, dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="dded6-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="dded6-184">Inicializovat proměnné datové cesty, načíst \*data ze souborů .csv a vrátit data `Train` a `Test` jako `IDataView` objekty `LoadData()`přidáním následujícího jako následující řádek kódu v :</span><span class="sxs-lookup"><span data-stu-id="dded6-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="dded6-185">Data v ML.NET je reprezentována jako [třída IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="dded6-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="dded6-186">`IDataView`je flexibilní a efektivní způsob popisu tabulkových dat (číselných a textových).</span><span class="sxs-lookup"><span data-stu-id="dded6-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="dded6-187">Data lze načíst z textového souboru nebo v reálném čase (například databáze SQL nebo soubory protokolu) do objektu. `IDataView`</span><span class="sxs-lookup"><span data-stu-id="dded6-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="dded6-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a čte v souboru.</span><span class="sxs-lookup"><span data-stu-id="dded6-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="dded6-189">Přebírá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="dded6-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="dded6-190">V takovém případě zadáte cestu `Test` pro `Train` vaše soubory a soubory a označíte záhlaví textového souboru (aby bylo možné správně používat názvy sloupců) a oddělovač dat znaků čárky (výchozí oddělovač je karta).</span><span class="sxs-lookup"><span data-stu-id="dded6-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="dded6-191">Přidejte do metody `Main()` následující kód `LoadData()` pro volání `Train` `Test` metody a vrácení dat a:</span><span class="sxs-lookup"><span data-stu-id="dded6-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="dded6-192">Sestavte a trénujte svůj model</span><span class="sxs-lookup"><span data-stu-id="dded6-192">Build and train your model</span></span>

<span data-ttu-id="dded6-193">Existují tři hlavní pojmy v ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer)a [Estimators](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="dded6-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="dded6-194">Algoritmy školení strojového učení vyžadují data v určitém formátu.</span><span class="sxs-lookup"><span data-stu-id="dded6-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="dded6-195">`Transformers`se používají k transformaci tabulkových dat do kompatibilního formátu.</span><span class="sxs-lookup"><span data-stu-id="dded6-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Diagram toku dat transformátoru.](./media/movie-recommendation/data-transformer-transformed.png)

<span data-ttu-id="dded6-197">`Transformers` Vytvořením souboru `Estimators`ML.NET vytvořit .</span><span class="sxs-lookup"><span data-stu-id="dded6-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="dded6-198">`Estimators`přijímat údaje a `Transformers`vracet .</span><span class="sxs-lookup"><span data-stu-id="dded6-198">`Estimators` take in data and return `Transformers`.</span></span>

![Diagram toku dat odhadu.](./media/movie-recommendation/data-estimator-transformer.png)

<span data-ttu-id="dded6-200">Algoritmus školení doporučení, který budete používat pro `Estimator`školení modelu je příkladem .</span><span class="sxs-lookup"><span data-stu-id="dded6-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="dded6-201">Vytvořte `Estimator` následující kroky:</span><span class="sxs-lookup"><span data-stu-id="dded6-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="dded6-202">Vytvořte `BuildAndTrainModel()` metodu, `LoadData()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="dded6-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="dded6-203">Tato metoda vám dá chybu, dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="dded6-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="dded6-204">Definujte transformace dat přidáním následujícího kódu do `BuildAndTrainModel()`aplikace :</span><span class="sxs-lookup"><span data-stu-id="dded6-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="dded6-205">`userId` Vzhledem `movieId` k tomu, a představují uživatele a názvy filmů, nikoli skutečné hodnoty, použijete `Feature` metodu [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) k transformaci každého `userId` do `movieId` sloupce typu číselného klíče (formát přijatý algoritmy doporučení) a přidáte je jako nové sloupce datové sady:</span><span class="sxs-lookup"><span data-stu-id="dded6-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="dded6-206">userId</span><span class="sxs-lookup"><span data-stu-id="dded6-206">userId</span></span> | <span data-ttu-id="dded6-207">movieId</span><span class="sxs-lookup"><span data-stu-id="dded6-207">movieId</span></span> | <span data-ttu-id="dded6-208">Popisek</span><span class="sxs-lookup"><span data-stu-id="dded6-208">Label</span></span> | <span data-ttu-id="dded6-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="dded6-209">userIdEncoded</span></span> | <span data-ttu-id="dded6-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="dded6-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="dded6-211">1</span><span class="sxs-lookup"><span data-stu-id="dded6-211">1</span></span> | <span data-ttu-id="dded6-212">1</span><span class="sxs-lookup"><span data-stu-id="dded6-212">1</span></span> | <span data-ttu-id="dded6-213">4</span><span class="sxs-lookup"><span data-stu-id="dded6-213">4</span></span> | <span data-ttu-id="dded6-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="dded6-214">userKey1</span></span> | <span data-ttu-id="dded6-215">filmKlíč1</span><span class="sxs-lookup"><span data-stu-id="dded6-215">movieKey1</span></span> |
| <span data-ttu-id="dded6-216">1</span><span class="sxs-lookup"><span data-stu-id="dded6-216">1</span></span> | <span data-ttu-id="dded6-217">3</span><span class="sxs-lookup"><span data-stu-id="dded6-217">3</span></span> | <span data-ttu-id="dded6-218">4</span><span class="sxs-lookup"><span data-stu-id="dded6-218">4</span></span> | <span data-ttu-id="dded6-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="dded6-219">userKey1</span></span> | <span data-ttu-id="dded6-220">filmKey2</span><span class="sxs-lookup"><span data-stu-id="dded6-220">movieKey2</span></span> |
| <span data-ttu-id="dded6-221">1</span><span class="sxs-lookup"><span data-stu-id="dded6-221">1</span></span> | <span data-ttu-id="dded6-222">6</span><span class="sxs-lookup"><span data-stu-id="dded6-222">6</span></span> | <span data-ttu-id="dded6-223">4</span><span class="sxs-lookup"><span data-stu-id="dded6-223">4</span></span> | <span data-ttu-id="dded6-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="dded6-224">userKey1</span></span> | <span data-ttu-id="dded6-225">filmKlíč3</span><span class="sxs-lookup"><span data-stu-id="dded6-225">movieKey3</span></span> |

<span data-ttu-id="dded6-226">Zvolte algoritmus strojového učení a přidejte jej k definicím transformace `BuildAndTrainModel()`dat přidáním následujícího jako následující řádek kódu v :</span><span class="sxs-lookup"><span data-stu-id="dded6-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="dded6-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je vaše doporučení školení algoritmus.</span><span class="sxs-lookup"><span data-stu-id="dded6-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="dded6-228">[Faktorizace matice](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je běžný přístup k doporučení, pokud máte data o tom, jak uživatelé hodnotili produkty v minulosti, což je případ datových sad v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="dded6-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="dded6-229">Existují další algoritmy doporučení, pokud máte k dispozici různá data (další informace naleznete v části [Další algoritmy doporučení](#other-recommendation-algorithms) níže).</span><span class="sxs-lookup"><span data-stu-id="dded6-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="dded6-230">V tomto případě `Matrix Factorization` algoritmus používá metodu s názvem "kolaborativní filtrování", která předpokládá, že pokud uživatel 1 má stejný názor jako uživatel 2 na určitý problém, pak uživatel 1 je pravděpodobnější, že se bude cítit stejným způsobem jako uživatel 2 o jiném problému.</span><span class="sxs-lookup"><span data-stu-id="dded6-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="dded6-231">Například pokud uživatel 1 a uživatel 2 hodnotí filmy podobně, pak uživatel 2 s větší pravděpodobností užije film, který uživatel 1 sledoval a vysoce hodnotil:</span><span class="sxs-lookup"><span data-stu-id="dded6-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="dded6-232">Uživatel 1</span><span class="sxs-lookup"><span data-stu-id="dded6-232">User 1</span></span> | <span data-ttu-id="dded6-233">Sledoval a líbil film</span><span class="sxs-lookup"><span data-stu-id="dded6-233">Watched and liked movie</span></span> | <span data-ttu-id="dded6-234">Sledoval a líbil film</span><span class="sxs-lookup"><span data-stu-id="dded6-234">Watched and liked movie</span></span> | <span data-ttu-id="dded6-235">Sledoval a líbil film</span><span class="sxs-lookup"><span data-stu-id="dded6-235">Watched and liked movie</span></span> |
| <span data-ttu-id="dded6-236">Uživatel 2</span><span class="sxs-lookup"><span data-stu-id="dded6-236">User 2</span></span> | <span data-ttu-id="dded6-237">Sledoval a líbil film</span><span class="sxs-lookup"><span data-stu-id="dded6-237">Watched and liked movie</span></span> | <span data-ttu-id="dded6-238">Sledoval a líbil film</span><span class="sxs-lookup"><span data-stu-id="dded6-238">Watched and liked movie</span></span> | <span data-ttu-id="dded6-239">Nesledoval - DOPORUČIT film</span><span class="sxs-lookup"><span data-stu-id="dded6-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="dded6-240">Trenér `Matrix Factorization` má několik možností , o [kterých](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)si můžete přečíst více v části [Hyperparameters algoritmus](#algorithm-hyperparameters) níže.</span><span class="sxs-lookup"><span data-stu-id="dded6-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="dded6-241">Připevněte model `Train` k datům a vraťte trénovaný model `BuildAndTrainModel()` přidáním následujícího jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="dded6-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="dded6-242">[Metoda Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trénuje váš model s poskytnutou trénovací datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="dded6-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="dded6-243">Technicky provede `Estimator` definice transformací dat a použitím trénování a vrátí zpět trénovaný model, což je . `Transformer`</span><span class="sxs-lookup"><span data-stu-id="dded6-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="dded6-244">Přidejte následující jako další řádek `Main()` kódu v `BuildAndTrainModel()` metodě volat metodu a vrátit trénovaný model:</span><span class="sxs-lookup"><span data-stu-id="dded6-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="dded6-245">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-245">Evaluate your model</span></span>

<span data-ttu-id="dded6-246">Po trénování modelu použijte testovací data k vyhodnocení toho, jak si model vede.</span><span class="sxs-lookup"><span data-stu-id="dded6-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="dded6-247">Vytvořte `EvaluateModel()` metodu, `BuildAndTrainModel()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="dded6-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="dded6-248">Transformace `Test` dat přidáním následujícího `EvaluateModel()`kódu do aplikace :</span><span class="sxs-lookup"><span data-stu-id="dded6-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="dded6-249">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) Metoda umožňuje předpovědi pro více zapředpokladu vstupní řádky testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="dded6-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="dded6-250">Vyhodnoťte model přidáním následujícího `EvaluateModel()` jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="dded6-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="dded6-251">Jakmile máte předpověď nastavit, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda vyhodnotí model, který porovnává předpovídané hodnoty s aktuální `Labels` v testovací datové sady a vrátí metriky o tom, jak model funguje.</span><span class="sxs-lookup"><span data-stu-id="dded6-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="dded6-252">Vytiskněte metriky hodnocení do konzoly přidáním následujícího `EvaluateModel()` jako následující řádek kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="dded6-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="dded6-253">Přidejte následující jako další řádek `Main()` kódu v `EvaluateModel()` metodě pro volání metody:</span><span class="sxs-lookup"><span data-stu-id="dded6-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="dded6-254">Výstup zatím by měl vypadat podobně jako následující text:</span><span class="sxs-lookup"><span data-stu-id="dded6-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="dded6-255">V tomto výstupu je 20 iterací.</span><span class="sxs-lookup"><span data-stu-id="dded6-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="dded6-256">V každé iteraci se míra chyby sníží a sblíží blíže a blíže k 0.</span><span class="sxs-lookup"><span data-stu-id="dded6-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="dded6-257">(RMS `root of mean squared error` nebo RMSE) se používá k měření rozdílů mezi modelem předpovídaných hodnot a sledovaných hodnot testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="dded6-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="dded6-258">Technicky je to druhá odmocnina průměru čtverců chyb.</span><span class="sxs-lookup"><span data-stu-id="dded6-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="dded6-259">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="dded6-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="dded6-260">`R Squared`označuje, jak dobře data odpovídají modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="dded6-261">Rozsah od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="dded6-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="dded6-262">Hodnota 0 znamená, že data jsou náhodná nebo jinak nelze přizpůsobit modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="dded6-263">Hodnota 1 znamená, že model přesně odpovídá datům.</span><span class="sxs-lookup"><span data-stu-id="dded6-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="dded6-264">Chcete, `R Squared` aby vaše skóre bylo co nejblíže k 1, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="dded6-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="dded6-265">Vytváření úspěšných modelů je iterativní proces.</span><span class="sxs-lookup"><span data-stu-id="dded6-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="dded6-266">Tento model má počáteční nižší kvalitu jako kurz používá malé datové sady poskytovat rychlé školení modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="dded6-267">Pokud nejste spokojeni s kvalitou modelu, můžete se pokusit vylepšit tím, že poskytuje větší trénovací datové sady nebo výběrem různých trénovacích algoritmů s různými hyperparametry pro každý algoritmus.</span><span class="sxs-lookup"><span data-stu-id="dded6-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="dded6-268">Další informace najdete v části [Vylepšete model](#improve-your-model) níže.</span><span class="sxs-lookup"><span data-stu-id="dded6-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="dded6-269">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-269">Use your model</span></span>

<span data-ttu-id="dded6-270">Nyní můžete použít trénovaný model k předpovědi na nová data.</span><span class="sxs-lookup"><span data-stu-id="dded6-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="dded6-271">Vytvořte `UseModelForSinglePrediction()` metodu, `EvaluateModel()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="dded6-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="dded6-272">Pomocí `PredictionEngine` tohoto slouží k předvídání `UseModelForSinglePrediction()`hodnocení přidáním následujícího kódu do :</span><span class="sxs-lookup"><span data-stu-id="dded6-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="dded6-273">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) je rozhraní API pohodlí, které umožňuje provádět předpověď na jednu instanci dat.</span><span class="sxs-lookup"><span data-stu-id="dded6-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="dded6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="dded6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="dded6-275">Je přijatelné používat v jednovláknových nebo prototypových prostředích.</span><span class="sxs-lookup"><span data-stu-id="dded6-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="dded6-276">Pro zlepšení výkonu a bezpečnosti vláken `PredictionEnginePool` v produkčním [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) prostředí [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) použijte službu, která vytvoří objekty pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dded6-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="dded6-277">V této příručce naleznete [informace o tom, `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)jak používat v ASP.NET základní webové rozhraní API .</span><span class="sxs-lookup"><span data-stu-id="dded6-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="dded6-278">`PredictionEnginePool`rozšíření služby je v současné době ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="dded6-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="dded6-279">Vytvořte instanci volané `MovieRating` `testInput` a předat jej Prediction Engine přidáním následující `UseModelForSinglePrediction()` jako další řádky kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="dded6-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="dded6-280">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkce provede předpověď na jeden sloupec dat.</span><span class="sxs-lookup"><span data-stu-id="dded6-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="dded6-281">Potom můžete použít `Score`, nebo předpokládané hodnocení, k určení, zda chcete doporučit film s movieId 10 pro uživatele 6.</span><span class="sxs-lookup"><span data-stu-id="dded6-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="dded6-282">Čím vyšší `Score`je , tím vyšší je pravděpodobnost, že se uživateli bude určitý film líbit.</span><span class="sxs-lookup"><span data-stu-id="dded6-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="dded6-283">V tomto případě řekněme, že doporučujete filmy s předpokládaným hodnocením > 3.5.</span><span class="sxs-lookup"><span data-stu-id="dded6-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="dded6-284">Chcete-li vytisknout výsledky, přidejte následující jako `UseModelForSinglePrediction()` další řádky kódu v metodě:</span><span class="sxs-lookup"><span data-stu-id="dded6-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="dded6-285">Přidejte následující jako další řádek `Main()` kódu v `UseModelForSinglePrediction()` metodě pro volání metody:</span><span class="sxs-lookup"><span data-stu-id="dded6-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="dded6-286">Výstup této metody by měl vypadat podobně jako následující text:</span><span class="sxs-lookup"><span data-stu-id="dded6-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="dded6-287">Uložení modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-287">Save your model</span></span>

<span data-ttu-id="dded6-288">Chcete-li použít model k předpovědi v aplikacích koncových uživatelů, musíte nejprve uložit model.</span><span class="sxs-lookup"><span data-stu-id="dded6-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="dded6-289">Vytvořte `SaveModel()` metodu, `UseModelForSinglePrediction()` hned za metodou, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="dded6-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="dded6-290">Uložte trénovaný model přidáním následujícího kódu v metodě: `SaveModel()`</span><span class="sxs-lookup"><span data-stu-id="dded6-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="dded6-291">Tato metoda uloží trénovaný model do souboru ZIP (ve složce "Data"), který pak lze použít v jiných aplikacích .NET k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="dded6-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="dded6-292">Přidejte následující jako další řádek `Main()` kódu v `SaveModel()` metodě pro volání metody:</span><span class="sxs-lookup"><span data-stu-id="dded6-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="dded6-293">Použití uloženého modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-293">Use your saved model</span></span>

<span data-ttu-id="dded6-294">Po uložení trénovaného modelu můžete model využívat v různých prostředích.</span><span class="sxs-lookup"><span data-stu-id="dded6-294">Once you have saved your trained model, you can consume the model in different environments.</span></span> <span data-ttu-id="dded6-295">Informace o tom, jak zprovoznit trénovaný model strojového učení v aplikacích, najdete v tématu [Ukládání a načítání trénovaného modelu.](../how-to-guides/save-load-machine-learning-models-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="dded6-295">See [Save and load trained models](../how-to-guides/save-load-machine-learning-models-ml-net.md) to learn how to operationalize a trained machine learning model in apps.</span></span>

## <a name="results"></a><span data-ttu-id="dded6-296">Výsledky</span><span class="sxs-lookup"><span data-stu-id="dded6-296">Results</span></span>

<span data-ttu-id="dded6-297">Po provedení výše uvedených kroků spusťte konzolovou aplikaci (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="dded6-297">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="dded6-298">Vaše výsledky z výše uvedené predikce by měly být podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="dded6-298">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="dded6-299">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy byly odebrány z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="dded6-299">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="dded6-300">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="dded6-300">Congratulations!</span></span> <span data-ttu-id="dded6-301">Nyní jste úspěšně vytvořili model strojového učení pro doporučování filmů.</span><span class="sxs-lookup"><span data-stu-id="dded6-301">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="dded6-302">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)</span><span class="sxs-lookup"><span data-stu-id="dded6-302">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="dded6-303">Vylepšení modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-303">Improve your model</span></span>

<span data-ttu-id="dded6-304">Existuje několik způsobů, jak můžete zlepšit výkon modelu, takže můžete získat přesnější předpovědi.</span><span class="sxs-lookup"><span data-stu-id="dded6-304">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="dded6-305">Data</span><span class="sxs-lookup"><span data-stu-id="dded6-305">Data</span></span>

<span data-ttu-id="dded6-306">Přidání dalších trénovacích dat, která mají dostatek vzorků pro každého uživatele a id filmu, může pomoci zlepšit kvalitu modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="dded6-306">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="dded6-307">[Křížové ověření](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) je technika pro vyhodnocení modelů, které náhodně rozdělí data do podmnožiny (namísto extrahování testovacích dat z datové sady, jako jste to udělali v tomto kurzu) a bere některé skupiny jako data vlaku a některé skupiny jako testovací data.</span><span class="sxs-lookup"><span data-stu-id="dded6-307">[Cross validation](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="dded6-308">Tato metoda překonává rozdělení vlakového testu z hlediska kvality modelu.</span><span class="sxs-lookup"><span data-stu-id="dded6-308">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="dded6-309">Funkce</span><span class="sxs-lookup"><span data-stu-id="dded6-309">Features</span></span>

<span data-ttu-id="dded6-310">V tomto kurzu použijete `Features` pouze`user id` `movie id`tři `rating`( , , a ), které jsou poskytovány datové sady.</span><span class="sxs-lookup"><span data-stu-id="dded6-310">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="dded6-311">I když je to dobrý začátek, ve skutečnosti `Features` můžete chtít přidat další atributy nebo (například věk, pohlaví, geografické umístění atd.), pokud jsou zahrnuty v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="dded6-311">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="dded6-312">Přidání relevantnější `Features` může pomoci zlepšit výkon modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="dded6-312">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="dded6-313">Pokud si nejste `Features` jisti, které by mohly být pro váš úkol strojového učení nejdůležitější, můžete také využít funkce výpočtu (FCC) a [permutace funkce význam](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), který ML.NET poskytuje objevit nejvlivnější `Features`.</span><span class="sxs-lookup"><span data-stu-id="dded6-313">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="dded6-314">Hyperparametry algoritmu</span><span class="sxs-lookup"><span data-stu-id="dded6-314">Algorithm hyperparameters</span></span>

<span data-ttu-id="dded6-315">Zatímco ML.NET poskytuje dobré výchozí trénovací algoritmy, můžete dále doladit výkon změnou [hyperparametry](../resources/glossary.md#hyperparameter)algoritmu .</span><span class="sxs-lookup"><span data-stu-id="dded6-315">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="dded6-316">Pro `Matrix Factorization`, můžete experimentovat s hyperparameters, jako je [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) chcete-li zjistit, zda to dává lepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="dded6-316">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="dded6-317">Například v tomto kurzu jsou možnosti algoritmu:</span><span class="sxs-lookup"><span data-stu-id="dded6-317">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="dded6-318">Další doporučující algoritmy</span><span class="sxs-lookup"><span data-stu-id="dded6-318">Other Recommendation Algorithms</span></span>

<span data-ttu-id="dded6-319">Algoritmus faktorizace matice s kolaborativním filtrováním je pouze jedním přístupem pro provádění doporučení filmu.</span><span class="sxs-lookup"><span data-stu-id="dded6-319">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="dded6-320">V mnoha případech nemusí být data hodnocení k dispozici a historie filmů je k dispozici pouze od uživatelů.</span><span class="sxs-lookup"><span data-stu-id="dded6-320">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="dded6-321">V ostatních případech můžete mít více než jen údaje o hodnocení uživatele.</span><span class="sxs-lookup"><span data-stu-id="dded6-321">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="dded6-322">Algoritmus</span><span class="sxs-lookup"><span data-stu-id="dded6-322">Algorithm</span></span>       | <span data-ttu-id="dded6-323">Scénář</span><span class="sxs-lookup"><span data-stu-id="dded6-323">Scenario</span></span>           | <span data-ttu-id="dded6-324">Ukázka</span><span class="sxs-lookup"><span data-stu-id="dded6-324">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="dded6-325">Faktorizace matice jedné třídy</span><span class="sxs-lookup"><span data-stu-id="dded6-325">One Class Matrix Factorization</span></span> | <span data-ttu-id="dded6-326">Použijte tuto položku, pokud máte pouze userId a movieId.</span><span class="sxs-lookup"><span data-stu-id="dded6-326">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="dded6-327">Tento styl doporučení je založen na scénáři koupě nebo produktech často zakoupených společně, což znamená, že zákazníkům doporučí sadu produktů na základě vlastní historie nákupních objednávek.</span><span class="sxs-lookup"><span data-stu-id="dded6-327">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="dded6-328">>Vyzkoušejte si to</span><span class="sxs-lookup"><span data-stu-id="dded6-328">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="dded6-329">Faktorizační stroje s vědomi terénu</span><span class="sxs-lookup"><span data-stu-id="dded6-329">Field Aware Factorization Machines</span></span> | <span data-ttu-id="dded6-330">Použijte k doporučení, pokud máte více funkcí nad rámec userId, productId a hodnocení (například popis produktu nebo cena produktu).</span><span class="sxs-lookup"><span data-stu-id="dded6-330">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="dded6-331">Tato metoda také používá přístup kolaborativní filtrování.</span><span class="sxs-lookup"><span data-stu-id="dded6-331">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="dded6-332">>Vyzkoušejte si to</span><span class="sxs-lookup"><span data-stu-id="dded6-332">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="dded6-333">Nový uživatelský scénář</span><span class="sxs-lookup"><span data-stu-id="dded6-333">New user scenario</span></span>

<span data-ttu-id="dded6-334">Jedním z běžných problémů při filtrování spolupráce je problém studeného startu, který je, když máte nového uživatele bez předchozích dat, ze kterých by bylo možné vyvodit závěry.</span><span class="sxs-lookup"><span data-stu-id="dded6-334">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="dded6-335">Tento problém je často vyřešen tím, že žádá nové uživatele, aby vytvořili profil a například hodnotili filmy, které viděli v minulosti.</span><span class="sxs-lookup"><span data-stu-id="dded6-335">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="dded6-336">Zatímco tato metoda klade určitou zátěž pro uživatele, poskytuje některá počáteční data pro nové uživatele bez historie hodnocení.</span><span class="sxs-lookup"><span data-stu-id="dded6-336">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="dded6-337">Zdroje a prostředky</span><span class="sxs-lookup"><span data-stu-id="dded6-337">Resources</span></span>

<span data-ttu-id="dded6-338">Data použitá v tomto kurzu jsou odvozena z [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="dded6-338">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dded6-339">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dded6-339">Next steps</span></span>

<span data-ttu-id="dded6-340">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="dded6-340">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="dded6-341">Výběr algoritmu strojového učení</span><span class="sxs-lookup"><span data-stu-id="dded6-341">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="dded6-342">Příprava a načtení dat</span><span class="sxs-lookup"><span data-stu-id="dded6-342">Prepare and load your data</span></span>
> * <span data-ttu-id="dded6-343">Sestavení a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-343">Build and train a model</span></span>
> * <span data-ttu-id="dded6-344">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-344">Evaluate a model</span></span>
> * <span data-ttu-id="dded6-345">Nasazení a využití modelu</span><span class="sxs-lookup"><span data-stu-id="dded6-345">Deploy and consume a model</span></span>

<span data-ttu-id="dded6-346">Přejdete k dalšímu kurzu, abyste se dozvěděli více</span><span class="sxs-lookup"><span data-stu-id="dded6-346">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="dded6-347">Analýza mínění</span><span class="sxs-lookup"><span data-stu-id="dded6-347">Sentiment Analysis</span></span>](sentiment-analysis.md)
