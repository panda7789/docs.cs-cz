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
# <a name="tutorial-create-a-movie-recommender-with-mlnet"></a><span data-ttu-id="521c6-103">Kurz: Vytvoření doporučené video s ML.NET</span><span class="sxs-lookup"><span data-stu-id="521c6-103">Tutorial: Create a Movie Recommender with ML.NET</span></span>

<span data-ttu-id="521c6-104">Tento ukázkový kurz ukazuje použití ML.NET sestavit doporučené video přes using aplikace konzoly .NET Core C# v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="521c6-104">This sample tutorial illustrates using ML.NET to build a movie recommender via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="521c6-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="521c6-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="521c6-106">Vyberte algoritmu strojového učení</span><span class="sxs-lookup"><span data-stu-id="521c6-106">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="521c6-107">Příprava a načítání dat</span><span class="sxs-lookup"><span data-stu-id="521c6-107">Prepare and load your data</span></span>
> * <span data-ttu-id="521c6-108">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-108">Build and train a model</span></span>
> * <span data-ttu-id="521c6-109">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-109">Evaluate a model</span></span>
> * <span data-ttu-id="521c6-110">Nasazení a používání modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-110">Deploy and consume a model</span></span>

> [!NOTE]
> <span data-ttu-id="521c6-111">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="521c6-111">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="521c6-112">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="521c6-112">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="521c6-113">Tento kurz a související ukázkové právě používáte **ML.NET verze 0,11**.</span><span class="sxs-lookup"><span data-stu-id="521c6-113">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="521c6-114">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="521c6-114">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="521c6-115">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) úložiště.</span><span class="sxs-lookup"><span data-stu-id="521c6-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="521c6-116">Pracovní postup Machine learning</span><span class="sxs-lookup"><span data-stu-id="521c6-116">Machine learning workflow</span></span>
<span data-ttu-id="521c6-117">K provedení úlohy, stejně jako jakoukoliv jinou úlohu ML.NET použijete následující kroky:</span><span class="sxs-lookup"><span data-stu-id="521c6-117">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="521c6-118">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="521c6-118">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="521c6-119">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-119">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="521c6-120">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-120">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="521c6-121">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-121">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="521c6-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="521c6-122">Prerequisites</span></span>

* <span data-ttu-id="521c6-123">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="521c6-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="521c6-124">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="521c6-124">Select the appropriate machine learning task</span></span>

<span data-ttu-id="521c6-125">Existuje několik způsobů, jak přistupovat ke doporučení problémy, třeba doporučování filmů seznam nebo doporučující seznam souvisejících produktů, ale v tomto případě se předpovědět, jaké (1-5) hodnocení uživatele bude uživatelům k konkrétního videa a doporučujeme tento film, pokud je vyšší než definovanou prahovou hodnotu (vyšší hodnocení, tím pravděpodobněji budou přesně konkrétního videa uživatele).</span><span class="sxs-lookup"><span data-stu-id="521c6-125">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="521c6-126">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="521c6-126">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="521c6-127">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="521c6-127">Create a project</span></span>

1. <span data-ttu-id="521c6-128">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="521c6-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="521c6-129">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="521c6-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="521c6-130">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="521c6-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="521c6-131">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="521c6-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="521c6-132">V **název** textového pole zadejte "MovieRecommender" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="521c6-132">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="521c6-133">Vytvořte adresář *Data* ve vašem projektu a uložení datové sady:</span><span class="sxs-lookup"><span data-stu-id="521c6-133">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="521c6-134">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="521c6-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="521c6-135">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="521c6-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="521c6-136">Nainstalujte **Microsoft.ML** a **Microsoft.ML.Recommender** balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="521c6-136">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="521c6-137">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="521c6-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="521c6-138">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="521c6-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="521c6-139">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="521c6-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="521c6-140">Opakujte tyto kroky pro **Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="521c6-140">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

  > [!NOTE]
  > <span data-ttu-id="521c6-141">Tento kurz používá **Microsoft.ML v0.11.0** a **Microsoft.ML.Recommender v0.11.0**.</span><span class="sxs-lookup"><span data-stu-id="521c6-141">This tutorial uses **Microsoft.ML v0.11.0** and **Microsoft.ML.Recommender v0.11.0**.</span></span>
    
4. <span data-ttu-id="521c6-142">Přidejte následující `using` příkazů v horní části vašeho *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="521c6-142">Add the following `using` statements at the top of your *Program.cs* file:</span></span>
    
    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="521c6-143">Stáhněte si vaše data</span><span class="sxs-lookup"><span data-stu-id="521c6-143">Download your data</span></span>

1. <span data-ttu-id="521c6-144">Stáhněte si dvě datové sady a uložit je do *Data* dříve vytvořená složka:</span><span class="sxs-lookup"><span data-stu-id="521c6-144">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

*   <span data-ttu-id="521c6-145">Klikněte pravým tlačítkem na [ *doporučení. hodnocení train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."</span><span class="sxs-lookup"><span data-stu-id="521c6-145">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
*   <span data-ttu-id="521c6-146">Klikněte pravým tlačítkem na [ *doporučení. hodnocení test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) a vyberte možnost "Uložit jako odkaz (neboli na cílový)..."</span><span class="sxs-lookup"><span data-stu-id="521c6-146">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="521c6-147">Ujistěte se, že buď uložit \*soubory CSV *Data* složky, nebo poté, co jste jej uložili jinde, přesunout \*soubory CSV *Data* složky.</span><span class="sxs-lookup"><span data-stu-id="521c6-147">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="521c6-148">V Průzkumníku řešení klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="521c6-148">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="521c6-149">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="521c6-149">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![Kopírovat, pokud je novější v sadě Visual Studio](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="521c6-151">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="521c6-151">Load your data</span></span>

<span data-ttu-id="521c6-152">Prvním krokem v procesu ML.NET se můžete připravit a načíst vaše testovací data a cvičení modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-152">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="521c6-153">Data hodnocení doporučení se dělí do `Train` a `Test` datové sady.</span><span class="sxs-lookup"><span data-stu-id="521c6-153">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="521c6-154">`Train` Data slouží k přizpůsobení modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-154">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="521c6-155">`Test` Data slouží k vytváření predikcí trénovaného modelu a vyhodnocení výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-155">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="521c6-156">Je běžné mít 80/20 rozdělení `Train` a `Test` data.</span><span class="sxs-lookup"><span data-stu-id="521c6-156">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="521c6-157">Níže je ve verzi preview data z vašeho \*souborů .csv s daty:</span><span class="sxs-lookup"><span data-stu-id="521c6-157">Below is a preview of the data from your \*.csv files:</span></span>

![Náhled dat](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="521c6-159">V \*soubory .csv, jsou čtyři sloupce:</span><span class="sxs-lookup"><span data-stu-id="521c6-159">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="521c6-160">Ve službě machine learning, se nazývají sloupce, které se používají při předpovědích [funkce](../resources/glossary.md#feature), a sloupec s vrácené predikcí se volá [popisek](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="521c6-160">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="521c6-161">Chcete předpovědět hodnocení filmů, tak, aby sloupec hodnocení `Label`.</span><span class="sxs-lookup"><span data-stu-id="521c6-161">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="521c6-162">Ostatní tři sloupce, `userId`, `movieId`, a `timestamp` jsou všechny `Features` použít k předpovědi `Label`.</span><span class="sxs-lookup"><span data-stu-id="521c6-162">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="521c6-163">Funkce</span><span class="sxs-lookup"><span data-stu-id="521c6-163">Features</span></span>      | <span data-ttu-id="521c6-164">Popisek</span><span class="sxs-lookup"><span data-stu-id="521c6-164">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="521c6-165">Záleží jen na vás, která `Features` se používají k předpovědi `Label`.</span><span class="sxs-lookup"><span data-stu-id="521c6-165">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="521c6-166">Můžete také použít metody, jako je [funkce permutaci význam](../how-to-guides/determine-global-feature-importance-in-model.md) abychom vám pomohli s výběrem nejlepší `Features`.</span><span class="sxs-lookup"><span data-stu-id="521c6-166">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="521c6-167">V takovém případě by odstranění `timestamp` jako sloupec `Feature` protože časové razítko nemá vliv na skutečně jak uživatel sazeb daného videa a proto by přispívat k provedení přesnější předpověď:</span><span class="sxs-lookup"><span data-stu-id="521c6-167">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="521c6-168">Funkce</span><span class="sxs-lookup"><span data-stu-id="521c6-168">Features</span></span>      | <span data-ttu-id="521c6-169">Popisek</span><span class="sxs-lookup"><span data-stu-id="521c6-169">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="521c6-170">Dále je nutné definovat strukturu dat pro třídu vstupu.</span><span class="sxs-lookup"><span data-stu-id="521c6-170">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="521c6-171">Přidejte novou třídu do projektu:</span><span class="sxs-lookup"><span data-stu-id="521c6-171">Add a new class to your project:</span></span>

1. <span data-ttu-id="521c6-172">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **Přidat > Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="521c6-172">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="521c6-173">V **dialogové okno Přidat novou položku**vyberte **třídy** a změnit **název** pole *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="521c6-173">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="521c6-174">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="521c6-174">Then, select the **Add** button.</span></span>

<span data-ttu-id="521c6-175">*MovieRatingData.cs* soubor se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="521c6-175">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="521c6-176">Přidejte následující `using` příkaz do horní části *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="521c6-176">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="521c6-177">Vytvořte třídu s názvem `MovieRating` odebráním stávající definice třídy a přidáním následujícího kódu v *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="521c6-177">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` <span data-ttu-id="521c6-178">Určuje třídu vstupní data.</span><span class="sxs-lookup"><span data-stu-id="521c6-178">specifies an input data class.</span></span> <span data-ttu-id="521c6-179">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atribut určuje, jaké sloupce (podle index sloupce) v datové sadě se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="521c6-179">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="521c6-180">`userId` a `movieId` sloupce jsou vaše `Features` (vstupy vám poskytne model k predikci `Label`), a sloupec hodnocení se `Label` , že bude předpovídat (výstup modelu).</span><span class="sxs-lookup"><span data-stu-id="521c6-180">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="521c6-181">Vytvořit jiné třídy `MovieRatingPrediction`, přidáním následujícího kódu po představující předpokládané výsledky `MovieRating` třídy v *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="521c6-181">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="521c6-182">V *Program.cs*, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem uvnitř `Main()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-182">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="521c6-183">[MLContext třídy](xref:Microsoft.ML.MLContext) je výchozí bod pro všechny operace ML.NET a inicializace `mlContext` vytvoří nové ML.NET prostředí, které mohou být sdíleny napříč objekty pracovního postupu vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-183">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="521c6-184">Je to podobné, koncepčně `DBContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="521c6-184">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="521c6-185">Po `Main()`, vytvořit metodu nazvanou `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-185">After `Main()`, create a method called `LoadData()`:</span></span>
```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{


}
```

> [!NOTE]
> <span data-ttu-id="521c6-186">Tato metoda vám poskytne chybu dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="521c6-186">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="521c6-187">Inicializace proměnných cesty dat, načtení dat ze souborů CSV a vrátit `Train` a `Test` data jako `IDataView` objekty přidáním následujícího kódu jako další řádek kódu v `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-187">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="521c6-188">Data v ML.NET je vyjádřena jako [IDataView třídy](xref:Microsoft.Data.DataView.IDataView).</span><span class="sxs-lookup"><span data-stu-id="521c6-188">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.Data.DataView.IDataView).</span></span> `IDataView` <span data-ttu-id="521c6-189">je flexibilní a efektivní způsob, jak popisují tabulková data (číselné a textové).</span><span class="sxs-lookup"><span data-stu-id="521c6-189">is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="521c6-190">Data je možné načíst z textového souboru nebo v reálném čase (například SQL databázi nebo soubory protokolů) do `IDataView` objektu.</span><span class="sxs-lookup"><span data-stu-id="521c6-190">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="521c6-191">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definuje schéma dat a přečte v souboru.</span><span class="sxs-lookup"><span data-stu-id="521c6-191">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="521c6-192">Přijímá proměnné cesty dat a vrátí `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="521c6-192">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="521c6-193">V takovém případě můžete zadat cestu pro vaše `Test` a `Train` soubory a označte text záhlaví souboru (takže ho můžete použít názvy sloupců správně) a čárky znakový oddělovač data (výchozím oddělovačem je karta).</span><span class="sxs-lookup"><span data-stu-id="521c6-193">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="521c6-194">Přidejte následující položky jako další dva řádky kódu ve `Main()` metodu chce volat vaše `LoadData()` metoda a vraťte se `Train` a `Test` dat:</span><span class="sxs-lookup"><span data-stu-id="521c6-194">Add the following as the next two lines of code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]


## <a name="build-and-train-your-model"></a><span data-ttu-id="521c6-195">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-195">Build and train your model</span></span>

<span data-ttu-id="521c6-196">Existují tři hlavní koncepty v ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [transformátory](../basic-concepts-model-training-in-mldotnet.md#transformer), a [odhady](../basic-concepts-model-training-in-mldotnet.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="521c6-196">There are three major concepts in ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [Transformers](../basic-concepts-model-training-in-mldotnet.md#transformer), and [Estimators](../basic-concepts-model-training-in-mldotnet.md#estimator).</span></span>

<span data-ttu-id="521c6-197">Strojové učení školení algoritmy vyžadují dat v určitém formátu.</span><span class="sxs-lookup"><span data-stu-id="521c6-197">Machine learning training algorithms require data in a certain format.</span></span> `Transformers` <span data-ttu-id="521c6-198">slouží k transformaci tabulkových dat do formátu kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="521c6-198">are used to transform tabular data to a compatible format.</span></span>

![Transformer – obrázek](./media/movie-recommendation/transformer.png)

<span data-ttu-id="521c6-200">Vytvoříte `Transformers` v ML.NET vytvořením `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="521c6-200">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> `Estimators` <span data-ttu-id="521c6-201">vzít data a vrátit `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="521c6-201">take in data and return `Transformers`.</span></span>

![odhad image](./media/movie-recommendation/estimator.png)

<span data-ttu-id="521c6-203">Cvičení algoritmu doporučení budete používat pro trénování modelu je příkladem `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="521c6-203">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="521c6-204">Sestavení `Estimator` pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="521c6-204">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="521c6-205">Vytvořte `BuildAndTrainModel()` metoda, hned za `LoadData()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="521c6-205">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>
```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{


}
```
> [!NOTE]
> <span data-ttu-id="521c6-206">Tato metoda vám poskytne chybu dokud nepřidáte příkaz return v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="521c6-206">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="521c6-207">Definování transformací dat přidáním následujícího kódu `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-207">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>
   
[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="521c6-208">Protože `userId` a `movieId` představují uživatelů a názvy filmů, nikoli skutečné hodnoty, je použít [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metody pro transformaci každého `userId` a každý `movieId` na číselný typ klíče `Feature`sloupec (formát, který přijal algoritmy doporučení) a přidejte je jako nové sloupce datové sady:</span><span class="sxs-lookup"><span data-stu-id="521c6-208">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="521c6-209">userId</span><span class="sxs-lookup"><span data-stu-id="521c6-209">userId</span></span> | <span data-ttu-id="521c6-210">movieId</span><span class="sxs-lookup"><span data-stu-id="521c6-210">movieId</span></span> | <span data-ttu-id="521c6-211">Popisek</span><span class="sxs-lookup"><span data-stu-id="521c6-211">Label</span></span> | <span data-ttu-id="521c6-212">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="521c6-212">userIdEncoded</span></span> | <span data-ttu-id="521c6-213">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="521c6-213">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="521c6-214">1</span><span class="sxs-lookup"><span data-stu-id="521c6-214">1</span></span> | <span data-ttu-id="521c6-215">1</span><span class="sxs-lookup"><span data-stu-id="521c6-215">1</span></span> | <span data-ttu-id="521c6-216">4</span><span class="sxs-lookup"><span data-stu-id="521c6-216">4</span></span> | <span data-ttu-id="521c6-217">userKey1</span><span class="sxs-lookup"><span data-stu-id="521c6-217">userKey1</span></span> | <span data-ttu-id="521c6-218">movieKey1</span><span class="sxs-lookup"><span data-stu-id="521c6-218">movieKey1</span></span> |
| <span data-ttu-id="521c6-219">1</span><span class="sxs-lookup"><span data-stu-id="521c6-219">1</span></span> | <span data-ttu-id="521c6-220">3</span><span class="sxs-lookup"><span data-stu-id="521c6-220">3</span></span> | <span data-ttu-id="521c6-221">4</span><span class="sxs-lookup"><span data-stu-id="521c6-221">4</span></span> | <span data-ttu-id="521c6-222">userKey1</span><span class="sxs-lookup"><span data-stu-id="521c6-222">userKey1</span></span> | <span data-ttu-id="521c6-223">movieKey2</span><span class="sxs-lookup"><span data-stu-id="521c6-223">movieKey2</span></span> |
| <span data-ttu-id="521c6-224">1</span><span class="sxs-lookup"><span data-stu-id="521c6-224">1</span></span> | <span data-ttu-id="521c6-225">6</span><span class="sxs-lookup"><span data-stu-id="521c6-225">6</span></span> | <span data-ttu-id="521c6-226">4</span><span class="sxs-lookup"><span data-stu-id="521c6-226">4</span></span> | <span data-ttu-id="521c6-227">userKey1</span><span class="sxs-lookup"><span data-stu-id="521c6-227">userKey1</span></span> | <span data-ttu-id="521c6-228">movieKey3</span><span class="sxs-lookup"><span data-stu-id="521c6-228">movieKey3</span></span> |


<span data-ttu-id="521c6-229">Zvolte algoritmu strojového učení a přidejte je do definice transformace dat, a to přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-229">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="521c6-230">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) je vaše doporučení cvičení algoritmu.</span><span class="sxs-lookup"><span data-stu-id="521c6-230">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="521c6-231">[Matice Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) je běžný postup k doporučení, když máte data na tom, jak uživatelé ohodnoceni produkty v minulosti se stává třeba u datových sad v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="521c6-231">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="521c6-232">Existují jiné algoritmy doporučení, když máte k dispozici různé data (naleznete v tématu [jiné algoritmy doporučení](#other-recommendation-algorithms) následující další části).</span><span class="sxs-lookup"><span data-stu-id="521c6-232">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span> 

<span data-ttu-id="521c6-233">V takovém případě `Matrix Factorization` algoritmus používá metodu nazvanou "filtrování založeného na spolupráci", což předpokládá, že pokud uživatel 1 má stejný stanovisko jako 2 uživatele na určité problém, pak 1 uživatel má větší pravděpodobnost cítit, že stejným způsobem jako 2 uživatele o jiný problém.</span><span class="sxs-lookup"><span data-stu-id="521c6-233">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="521c6-234">Například pokud uživatel 1 a 2 uživatele hodnocení filmů podobně, pak uživatel 2 má větší pravděpodobnost Užijte si video, které má uživatel 1 sledovali vysílání televizní a velmi ohodnotili:</span><span class="sxs-lookup"><span data-stu-id="521c6-234">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="521c6-235">Uživatel 1</span><span class="sxs-lookup"><span data-stu-id="521c6-235">User 1</span></span> | <span data-ttu-id="521c6-236">Sledované a líbilo movie</span><span class="sxs-lookup"><span data-stu-id="521c6-236">Watched and liked movie</span></span> | <span data-ttu-id="521c6-237">Sledované a líbilo movie</span><span class="sxs-lookup"><span data-stu-id="521c6-237">Watched and liked movie</span></span> | <span data-ttu-id="521c6-238">Sledované a líbilo movie</span><span class="sxs-lookup"><span data-stu-id="521c6-238">Watched and liked movie</span></span> |
| <span data-ttu-id="521c6-239">Uživatel 2</span><span class="sxs-lookup"><span data-stu-id="521c6-239">User 2</span></span> | <span data-ttu-id="521c6-240">Sledované a líbilo movie</span><span class="sxs-lookup"><span data-stu-id="521c6-240">Watched and liked movie</span></span> | <span data-ttu-id="521c6-241">Sledované a líbilo movie</span><span class="sxs-lookup"><span data-stu-id="521c6-241">Watched and liked movie</span></span> | <span data-ttu-id="521c6-242">Nebyl sledované – DOPORUČUJEME movie</span><span class="sxs-lookup"><span data-stu-id="521c6-242">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="521c6-243">`Matrix Factorization` Trainer víme o několika [možnosti](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), které si můžete přečíst více o v [algoritmus hyperparameters](#algorithm-hyperparameters) níže v části.</span><span class="sxs-lookup"><span data-stu-id="521c6-243">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="521c6-244">Přizpůsobit modelu, který má `Train` data a vrátit trénovaného modelu přidáním následujícího kódu jako další řádek kódu v `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-244">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="521c6-245">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) metoda trénovat modelu pomocí zadaného trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="521c6-245">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="521c6-246">Technicky, spustí `Estimator` definice transformace dat a použitím školení a vrátí zpět trénovaného modelu, který je `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="521c6-246">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="521c6-247">Přidejte následující položky jako další řádek kódu `Main()` metodu chce volat vaše `BuildAndTrainModel()` metodu a vrátí trénovaného modelu:</span><span class="sxs-lookup"><span data-stu-id="521c6-247">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="521c6-248">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-248">Evaluate your model</span></span>

<span data-ttu-id="521c6-249">Jakmile máte Trénink modelu, slouží k vyhodnocení, jaký je výkon modelu testovací data.</span><span class="sxs-lookup"><span data-stu-id="521c6-249">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span> 

<span data-ttu-id="521c6-250">Vytvořte `EvaluateModel()` metoda, hned za `BuildAndTrainModel()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="521c6-250">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>
```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{


}
```

<span data-ttu-id="521c6-251">Transformace `Test` data přidáním následujícího kódu do `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-251">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>
[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="521c6-252">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda vytváří předpovědi pro více poskytuje vstupní řádky z datové sady testů.</span><span class="sxs-lookup"><span data-stu-id="521c6-252">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="521c6-253">Přidáním následujícího kódu jako další řádek kódu ve vyhodnocení modelu `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-253">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="521c6-254">Až budete mít předpovědi nastavená, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda vyhodnocuje modelu, který porovnává predikované hodnoty s skutečnou `Labels` v testovací datové sady a vrátí metriky na jaký je výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-254">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="521c6-255">Tisk metrik hodnocení do konzoly přidáním následujícího kódu jako další řádek kódu v `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-255">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="521c6-256">Přidejte následující položky jako další řádek kódu v `Main()` metodu chce volat vaše `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-256">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="521c6-257">Výstup, pokud by měla vypadat podobně jako následující text:</span><span class="sxs-lookup"><span data-stu-id="521c6-257">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="521c6-258">Tento výstup jsou 20 iterací.</span><span class="sxs-lookup"><span data-stu-id="521c6-258">In this output, there are 20 iterations.</span></span> <span data-ttu-id="521c6-259">V každé iteraci míra chyb sníží a sladila blíže a blíže na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="521c6-259">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="521c6-260">`root of mean squared error` (RMS nebo RMSE) se často používá k měření rozdílů mezi hodnoty předpovídané pomocí modelu a hodnotami zjištěnými v datové sadě testů.</span><span class="sxs-lookup"><span data-stu-id="521c6-260">The `root of mean squared error` (RMS or RMSE) is frequently used to measure the differences between values predicted by a model and the values observed in a test dataset.</span></span> <span data-ttu-id="521c6-261">Technicky je druhá odmocnina průměru kvadratických chyb.</span><span class="sxs-lookup"><span data-stu-id="521c6-261">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="521c6-262">Chcete, aby vaše RMSE skóre, aby byly co nejblíže 1 nejvíce.</span><span class="sxs-lookup"><span data-stu-id="521c6-262">You want your RMSE score to be as close to 1 as possible.</span></span>

`R Squared` <span data-ttu-id="521c6-263">je procento variace předpovězené hodnoty vysvětlené modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-263">is the variation percentage in the predicted values explained by your model.</span></span> <span data-ttu-id="521c6-264">Je to hodnota mezi 0 a 1 a užší hodnotu na 0, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="521c6-264">It's a value between 0 and 1, and the closer the value is to 0, the better the model is.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="521c6-265">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-265">Use your model</span></span>

<span data-ttu-id="521c6-266">Nyní můžete trénovaného modelu k vytvoření predikcí nová data.</span><span class="sxs-lookup"><span data-stu-id="521c6-266">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="521c6-267">Vytvořte `UseModelForSinglePrediction()` metoda, hned za `EvaluateModel()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="521c6-267">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>
```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{


}
```

<span data-ttu-id="521c6-268">Použití `PredictionEngine` aby předpovídal hodnocení přidáním následujícího kódu `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="521c6-268">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="521c6-269">[PredictionEngine třídy](xref:Microsoft.ML.PredictionEngine%602) je pohodlné rozhraní API, které vám umožní předat jedna instance data a pak proveďte predikcí na tato jediná instance data.</span><span class="sxs-lookup"><span data-stu-id="521c6-269">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="521c6-270">Vytvoření instance `MovieRating` volá `testInput` a předejte jej do modulu předpovědi přidáním následujícího kódu jako další řádky kódu ve `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-270">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="521c6-271">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkce vytváří predikcí na jeden sloupec data.</span><span class="sxs-lookup"><span data-stu-id="521c6-271">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="521c6-272">Pak můžete použít `Score`, nebo predikované hodnocení určit, jestli chcete pro doporučování filmů s movieId 10 uživateli 6.</span><span class="sxs-lookup"><span data-stu-id="521c6-272">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="521c6-273">Vyšší `Score`, vyšší pravděpodobnost, že uživatel přesně konkrétního videa.</span><span class="sxs-lookup"><span data-stu-id="521c6-273">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="521c6-274">V takovém případě Řekněme, že Doporučujete filmů s predikované hodnocení > 3.5.</span><span class="sxs-lookup"><span data-stu-id="521c6-274">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="521c6-275">Tisk výsledků, přidejte následující položky jako další řádky kódu ve `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-275">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="521c6-276">Přidejte následující položky jako další řádek kódu v `Main()` metodu chce volat vaše `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-276">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="521c6-277">Výstup této metody by měla vypadat podobně jako následující text:</span><span class="sxs-lookup"><span data-stu-id="521c6-277">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="521c6-278">Uložit model</span><span class="sxs-lookup"><span data-stu-id="521c6-278">Save your model</span></span>
<span data-ttu-id="521c6-279">Použití modelu k následné predikci aplikace koncového uživatele, musíte nejprve uložit model.</span><span class="sxs-lookup"><span data-stu-id="521c6-279">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="521c6-280">Vytvořte `SaveModel()` metoda, hned za `UseModelForSinglePrediction()` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="521c6-280">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>
```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{


}
```

<span data-ttu-id="521c6-281">Uložení natrénovaného modelu přidáním následujícího kódu v `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-281">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="521c6-282">Tato metoda šetří trénovaného modelu do souboru ZIP (ve složce "Data"), který lze potom použít v ostatních aplikacích .NET k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="521c6-282">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="521c6-283">Přidejte následující položky jako další řádek kódu v `Main()` metodu chce volat vaše `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="521c6-283">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="521c6-284">Použít uložený model</span><span class="sxs-lookup"><span data-stu-id="521c6-284">Use your saved model</span></span>
<span data-ttu-id="521c6-285">Po uložení natrénovaného modelu můžete využívat model v různých prostředích (najdete v článku ["Příručka"](../how-to-guides/consuming-model-ml-net.md) postup pro zprovoznění modelu trénovaného strojového učení v aplikacích).</span><span class="sxs-lookup"><span data-stu-id="521c6-285">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="521c6-286">Výsledky</span><span class="sxs-lookup"><span data-stu-id="521c6-286">Results</span></span>

<span data-ttu-id="521c6-287">Po provedení výše uvedených kroků, spuštění aplikace konzoly (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="521c6-287">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="521c6-288">Výsledky z jednoho předpovědi výše by měl vypadat přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="521c6-288">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="521c6-289">Může se zobrazit upozornění nebo zpracování zpráv, ale tyto zprávy se odebraly z následujících výsledků pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="521c6-289">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="521c6-290">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="521c6-290">Congratulations!</span></span> <span data-ttu-id="521c6-291">Teď jste úspěšně vytvořili model pro doporučování filmů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="521c6-291">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="521c6-292">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) úložiště.</span><span class="sxs-lookup"><span data-stu-id="521c6-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="521c6-293">Zlepšit váš model</span><span class="sxs-lookup"><span data-stu-id="521c6-293">Improve your model</span></span>

<span data-ttu-id="521c6-294">Existuje několik způsobů, takže můžete získat přesnější předpovědi může zlepšit výkon modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-294">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="521c6-295">Data</span><span class="sxs-lookup"><span data-stu-id="521c6-295">Data</span></span> 

<span data-ttu-id="521c6-296">Přidání další trénovací data, která má dostatek ukázky pro každého uživatele a id video můžete podílet na zlepšování kvality modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="521c6-296">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="521c6-297">[Křížové ověření](../how-to-guides/train-cross-validation-ml-net.md) je technika, který náhodně vyhodnocování modelů rozděluje data do podmnožiny (namísto extrahování testovací data z datové sady, stejně jako v tomto kurzu) a má některé skupiny jako trénování dat a některé skupiny jako test data.</span><span class="sxs-lookup"><span data-stu-id="521c6-297">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="521c6-298">Tato metoda lepší výkon než provádění trénování a testování, rozdělit z hlediska kvality modelu.</span><span class="sxs-lookup"><span data-stu-id="521c6-298">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="521c6-299">Funkce</span><span class="sxs-lookup"><span data-stu-id="521c6-299">Features</span></span>

<span data-ttu-id="521c6-300">V tomto kurzu použijete pouze tři `Features` (`user id`, `movie id`, a `rating`), které jsou k dispozici v objektu DataSet.</span><span class="sxs-lookup"><span data-stu-id="521c6-300">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span> 

<span data-ttu-id="521c6-301">Přestože se jedná o dobrý začátek, ve skutečnosti můžete chtít přidat další atributy nebo `Features` (například věk, pohlaví, geografické umístění atd.) je zahrnuta v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="521c6-301">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="521c6-302">Přidání více odpovídajících `Features` může pomoct zlepšit výkon modelu doporučení.</span><span class="sxs-lookup"><span data-stu-id="521c6-302">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span> 

<span data-ttu-id="521c6-303">Pokud si nejste jisti, o tom, které `Features` může být nejdůležitějších pro úkol machine learning, můžete také využít z funkce příspěvek výpočtu (FCC) a [funkce permutaci význam](../how-to-guides/determine-global-feature-importance-in-model.md), poskytující ML.NET vyhledat největší vliv `Features`.</span><span class="sxs-lookup"><span data-stu-id="521c6-303">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="521c6-304">Algoritmus hyperparameters</span><span class="sxs-lookup"><span data-stu-id="521c6-304">Algorithm hyperparameters</span></span>

<span data-ttu-id="521c6-305">Zatímco ML.NET poskytuje dobré výchozí školení algoritmy, můžete vyladit výkon tak, že změníte tento algoritmus [hyperparameters](../resources/glossary.md#hyperparameter).</span><span class="sxs-lookup"><span data-stu-id="521c6-305">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="521c6-306">Pro `Matrix Factorization`, můžete experimentovat s hyperparameters například [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) a [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) zobrazíte, pokud, která poskytuje lepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="521c6-306">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="521c6-307">Například v tomto kurzu algoritmus možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="521c6-307">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="521c6-308">Jiné algoritmy doporučení</span><span class="sxs-lookup"><span data-stu-id="521c6-308">Other Recommendation Algorithms</span></span>
<span data-ttu-id="521c6-309">Algoritmus factorization matice s filtrování založeného na spolupráci je pouze jedním z přístupů pro provádění filmových doporučení.</span><span class="sxs-lookup"><span data-stu-id="521c6-309">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="521c6-310">V mnoha případech nemusí mít k dispozici data hodnocení a mít jenom historie video k dispozici od uživatelů.</span><span class="sxs-lookup"><span data-stu-id="521c6-310">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="521c6-311">V jiných případech může mít více než jen hodnocení data uživatele.</span><span class="sxs-lookup"><span data-stu-id="521c6-311">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="521c6-312">algoritmus</span><span class="sxs-lookup"><span data-stu-id="521c6-312">Algorithm</span></span>       | <span data-ttu-id="521c6-313">Scénář</span><span class="sxs-lookup"><span data-stu-id="521c6-313">Scenario</span></span>           | <span data-ttu-id="521c6-314">Ukázka</span><span class="sxs-lookup"><span data-stu-id="521c6-314">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="521c6-315">Matice Factorization jedné třídy</span><span class="sxs-lookup"><span data-stu-id="521c6-315">One Class Matrix Factorization</span></span> | <span data-ttu-id="521c6-316">Použijte ho, když máte jen ID uživatele a movieId.</span><span class="sxs-lookup"><span data-stu-id="521c6-316">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="521c6-317">Tento styl doporučení je založeno na společné nákupní scénář nebo produkty často kupované společně, což znamená, že vám doporučí zákazníkům sadu produktů na základě jejich vlastní historii nákupních objednávek.</span><span class="sxs-lookup"><span data-stu-id="521c6-317">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="521c6-318">> vyzkoušejte si to</span><span class="sxs-lookup"><span data-stu-id="521c6-318">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="521c6-319">Počítače používající Factorization pole</span><span class="sxs-lookup"><span data-stu-id="521c6-319">Field Aware Factorization Machines</span></span> | <span data-ttu-id="521c6-320">Používejte to, aby doporučení, pokud máte další funkce nad rámec userId, productId a hodnocení (například popis produktu nebo cena produktu).</span><span class="sxs-lookup"><span data-stu-id="521c6-320">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="521c6-321">Tato metoda také používá filtrování přístup založený na spolupráci.</span><span class="sxs-lookup"><span data-stu-id="521c6-321">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="521c6-322">> vyzkoušejte si to</span><span class="sxs-lookup"><span data-stu-id="521c6-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="521c6-323">Nový uživatelský scénář</span><span class="sxs-lookup"><span data-stu-id="521c6-323">New user scenario</span></span>
<span data-ttu-id="521c6-324">Jeden běžný problém při spolupráci filtrování je problém úplné spuštění, který je v případě nového uživatele bez předchozího dat. Chcete-li nakreslit závěry z.</span><span class="sxs-lookup"><span data-stu-id="521c6-324">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="521c6-325">Tento problém je vyřešen často požádá noví uživatelé k vytvoření profilu a pro instanci míra filmy, jste narazili v minulosti.</span><span class="sxs-lookup"><span data-stu-id="521c6-325">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="521c6-326">Zatímco tato metoda se vloží některé zatížení na uživatele, poskytuje nějaká počáteční data pro nové uživatele bez historie hodnocení.</span><span class="sxs-lookup"><span data-stu-id="521c6-326">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="521c6-327">Prostředky</span><span class="sxs-lookup"><span data-stu-id="521c6-327">Resources</span></span>
<span data-ttu-id="521c6-328">V tomto kurzu používá data jsou odvozena z [datovou sadu MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="521c6-328">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="521c6-329">Další kroky</span><span class="sxs-lookup"><span data-stu-id="521c6-329">Next steps</span></span>
<span data-ttu-id="521c6-330">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="521c6-330">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="521c6-331">Vyberte algoritmu strojového učení</span><span class="sxs-lookup"><span data-stu-id="521c6-331">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="521c6-332">Příprava a načítání dat</span><span class="sxs-lookup"><span data-stu-id="521c6-332">Prepare and load your data</span></span>
> * <span data-ttu-id="521c6-333">Vytvoření a trénování modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-333">Build and train a model</span></span>
> * <span data-ttu-id="521c6-334">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-334">Evaluate a model</span></span>
> * <span data-ttu-id="521c6-335">Nasazení a používání modelu</span><span class="sxs-lookup"><span data-stu-id="521c6-335">Deploy and consume a model</span></span>

<span data-ttu-id="521c6-336">Přejděte k dalšímu kurzu, kde Další informace</span><span class="sxs-lookup"><span data-stu-id="521c6-336">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="521c6-337">Analýza mínění</span><span class="sxs-lookup"><span data-stu-id="521c6-337">Sentiment Analysis</span></span>](sentiment-analysis.md)
