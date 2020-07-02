---
title: Kurz analýzy mínění s rozhraním .NET pro Apache Spark a ML.NET
description: V tomto kurzu se naučíte používat ML.NET s .NET pro Apache Spark pro analýzu mínění.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 69deb30419b98536fa309547d94f59bb266e413c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617574"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="070f4-103">Kurz: analýza mínění pomocí technologie .NET pro Apache Spark a ML.NET</span><span class="sxs-lookup"><span data-stu-id="070f4-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="070f4-104">V tomto kurzu se naučíte, jak provádět analýzu online recenzí mínění pomocí ML.NET a .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="070f4-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="070f4-105">[Ml.NET](http://dot.net/ml) je bezplatná platforma pro strojové učení open source pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="070f4-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="070f4-106">ML.NET můžete použít s rozhraním .NET pro Apache Spark ke škálování školení a předpovědi algoritmů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="070f4-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="070f4-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="070f4-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="070f4-108">Vytvoření modelu analýzy mínění pomocí Tvůrce modelů ML.NET v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="070f4-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="070f4-109">Vytvořte aplikaci pro konzolu .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="070f4-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="070f4-110">Zápis a implementace uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="070f4-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="070f4-111">Spusťte konzolovou aplikaci .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="070f4-111">Run a .NET for Apache Spark console app.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="070f4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="070f4-112">Prerequisites</span></span>

* <span data-ttu-id="070f4-113">Pokud jste ještě nevyvinuli rozhraní .NET pro Apache Spark aplikaci, začněte pomocí [Začínáme kurzu](get-started.md) , kde se seznámíte se základy.</span><span class="sxs-lookup"><span data-stu-id="070f4-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="070f4-114">Před pokračováním v tomto kurzu dokončete všechny požadavky pro Začínáme kurz.</span><span class="sxs-lookup"><span data-stu-id="070f4-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="070f4-115">V tomto kurzu se používá k dispozici vizuální rozhraní tvůrce modelů ML.NET (Preview), které je dostupné v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="070f4-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="070f4-116">Pokud ještě nemáte Visual Studio, můžete [si zdarma stáhnout verzi sady Visual Studio pro komunitu](https://visualstudio.microsoft.com/downloads/) .</span><span class="sxs-lookup"><span data-stu-id="070f4-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="070f4-117">[Stáhnout a nainstalovat](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET model Builder (Preview).</span><span class="sxs-lookup"><span data-stu-id="070f4-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="070f4-118">Stáhněte [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) a [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp zkontrolovat datové sady.</span><span class="sxs-lookup"><span data-stu-id="070f4-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="070f4-119">Kontrola dat</span><span class="sxs-lookup"><span data-stu-id="070f4-119">Review the data</span></span>

<span data-ttu-id="070f4-120">Datová sada Yelp Reviews obsahuje online Yelp recenze o různých službách.</span><span class="sxs-lookup"><span data-stu-id="070f4-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="070f4-121">Otevřete [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) a Všimněte si struktury dat.</span><span class="sxs-lookup"><span data-stu-id="070f4-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="070f4-122">První sloupec obsahuje text Revize a druhý sloupec obsahuje mínění skóre.</span><span class="sxs-lookup"><span data-stu-id="070f4-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="070f4-123">Pokud je mínění skóre 1, je kontrola kladná a pokud je skóre mínění 0, kontrola je záporná.</span><span class="sxs-lookup"><span data-stu-id="070f4-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="070f4-124">Následující tabulka obsahuje ukázková data:</span><span class="sxs-lookup"><span data-stu-id="070f4-124">The following table contains sample data:</span></span>

|<span data-ttu-id="070f4-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="070f4-125">ReviewText</span></span>|<span data-ttu-id="070f4-126">Mínění</span><span class="sxs-lookup"><span data-stu-id="070f4-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="070f4-127">Wow... Tohle místo.</span><span class="sxs-lookup"><span data-stu-id="070f4-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="070f4-128">1</span><span class="sxs-lookup"><span data-stu-id="070f4-128">1</span></span>|
|<span data-ttu-id="070f4-129">Crust není dobrá.</span><span class="sxs-lookup"><span data-stu-id="070f4-129">Crust is not good.</span></span>|    <span data-ttu-id="070f4-130">0</span><span class="sxs-lookup"><span data-stu-id="070f4-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="070f4-131">Sestavení modelu Machine Learning</span><span class="sxs-lookup"><span data-stu-id="070f4-131">Build your machine learning model</span></span>

1. <span data-ttu-id="070f4-132">Otevřete Visual Studio a vytvořte novou konzolovou aplikaci v jazyce C# (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="070f4-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="070f4-133">Pojmenujte projekt *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="070f4-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="070f4-134">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *MLSparkModel* .</span><span class="sxs-lookup"><span data-stu-id="070f4-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="070f4-135">Pak vyberte **přidat > Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="070f4-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="070f4-136">V Tvůrci modelů ML.NET vyberte dlaždici **Analýza mínění** scénář.</span><span class="sxs-lookup"><span data-stu-id="070f4-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="070f4-137">Na stránce **Přidat data** nahrajte *yelptrain.csv* datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="070f4-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="070f4-138">Vyberte *mínění* ze **sloupců k předpovědi** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="070f4-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="070f4-139">Na stránce **vlak** nastavte čas na vlak na *60 sekund* a vyberte **Spustit školení**.</span><span class="sxs-lookup"><span data-stu-id="070f4-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="070f4-140">V části **průběh**si všimněte stavu školení.</span><span class="sxs-lookup"><span data-stu-id="070f4-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="070f4-141">Po dokončení školení pro tvůrce modelů **vyhodnoťte** výsledky školení.</span><span class="sxs-lookup"><span data-stu-id="070f4-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="070f4-142">Do textového pole níže můžete zadat fráze a **vyzkoušet** si tak výstup a pak vybrat **předpověď** .</span><span class="sxs-lookup"><span data-stu-id="070f4-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="070f4-143">Vyberte **kód** a pak vyberte **Přidat projekty** a přidejte do řešení model ml.</span><span class="sxs-lookup"><span data-stu-id="070f4-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="070f4-144">Všimněte si, že do řešení jsou přidány dva projekty: **MLSparkModelML. ConsoleApp** a **MLSparkModelML. model**.</span><span class="sxs-lookup"><span data-stu-id="070f4-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="070f4-145">Dvakrát klikněte na projekt C# *MLSpark* a Všimněte si, že byl přidán následující odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="070f4-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="070f4-146">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="070f4-146">Create a console app</span></span>

<span data-ttu-id="070f4-147">Tvůrce modelů vytvoří pro vás konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="070f4-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="070f4-148">V Průzkumník řešení klikněte pravým tlačítkem na **MLSparkModelML. Console** a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="070f4-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="070f4-149">Vyhledejte **Microsoft. Spark** a nainstalujte balíček.</span><span class="sxs-lookup"><span data-stu-id="070f4-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="070f4-150">**Microsoft.ml** se automaticky nainstaluje pomocí Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="070f4-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="070f4-151">Vytvoření SparkSession</span><span class="sxs-lookup"><span data-stu-id="070f4-151">Create a SparkSession</span></span>

1. <span data-ttu-id="070f4-152">Otevřete soubor *program.cs* pro **MLSparkModelML. ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="070f4-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="070f4-153">Tento soubor byl automaticky vygenerován pomocí Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="070f4-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="070f4-154">Odstraňte `using` příkazy, obsah metody Main () a `CreateSingleDataSample` oblast.</span><span class="sxs-lookup"><span data-stu-id="070f4-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="070f4-155">`using`Do horní části *program.cs*přidejte následující dodatečné příkazy:</span><span class="sxs-lookup"><span data-stu-id="070f4-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="070f4-156">Změňte na `DATA_FILEPATH` cestu k vašemu *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="070f4-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="070f4-157">Přidejte následující kód do `Main` metody pro vytvoření nového `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="070f4-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="070f4-158">Relace Spark je vstupním bodem pro programování Sparku s využitím datové sady a rozhraní API dataframe.</span><span class="sxs-lookup"><span data-stu-id="070f4-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="070f4-159">Volání objektu *Spark* , který jste vytvořili výše, vám umožní přístup k funkcím Sparku a dataframe v celém programu.</span><span class="sxs-lookup"><span data-stu-id="070f4-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="070f4-160">Vytvoření datového rámce a tisk do konzoly</span><span class="sxs-lookup"><span data-stu-id="070f4-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="070f4-161">Přečtěte si v Yelp data ze souboru *yelptest.csv* jako `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="070f4-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="070f4-162">Zahrnutí `header` a `inferSchema` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="070f4-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="070f4-163">`header`Možnost načte první řádek *yelptest.csv* jako názvy sloupců místo dat.</span><span class="sxs-lookup"><span data-stu-id="070f4-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="070f4-164">`inferSchema`Možnost odvodí typy sloupců na základě dat.</span><span class="sxs-lookup"><span data-stu-id="070f4-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="070f4-165">Registrovat uživatelsky definovanou funkci</span><span class="sxs-lookup"><span data-stu-id="070f4-165">Register a user-defined function</span></span>

<span data-ttu-id="070f4-166">UDF, *uživatelsky definované funkce*v aplikacích Spark můžete použít k výpočtům a analýzám vašich dat.</span><span class="sxs-lookup"><span data-stu-id="070f4-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="070f4-167">V tomto kurzu použijete ML.NET se systémem souborů UDF k vyhodnocení každé kontroly Yelp.</span><span class="sxs-lookup"><span data-stu-id="070f4-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="070f4-168">Přidejte následující kód do `Main` metody pro registraci volání UDF `MLudf` .</span><span class="sxs-lookup"><span data-stu-id="070f4-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="070f4-169">Tato UDF přebírá řetězec Yelp revize jako vstup a výstupy hodnot true nebo false pro kladné nebo záporné zabarvení, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="070f4-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="070f4-170">Používá metodu *předpověď ()* , kterou definujete v pozdějším kroku.</span><span class="sxs-lookup"><span data-stu-id="070f4-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="070f4-171">Použití Spark SQL pro volání UDF</span><span class="sxs-lookup"><span data-stu-id="070f4-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="070f4-172">Teď, když jste si přečetli svoje data a zahrnuli ML, použijte Spark SQL pro volání UDF, který spustí analýzu mínění na každém řádku vašeho datového rámce.</span><span class="sxs-lookup"><span data-stu-id="070f4-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="070f4-173">Do metody přidejte následující kód `Main` :</span><span class="sxs-lookup"><span data-stu-id="070f4-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="070f4-174">Create prediktivní () – metoda</span><span class="sxs-lookup"><span data-stu-id="070f4-174">Create predict() method</span></span>

<span data-ttu-id="070f4-175">Do své metody přidejte následující kód `Main()` .</span><span class="sxs-lookup"><span data-stu-id="070f4-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="070f4-176">Tento kód je podobný tomu, co je vytvořeno tvůrcem modelů v *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="070f4-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="070f4-177">Přesunutím této metody do konzoly načtete model načítání při každém spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="070f4-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="070f4-178">Přidání modelu do aplikace konzoly</span><span class="sxs-lookup"><span data-stu-id="070f4-178">Add the model to your console app</span></span>

<span data-ttu-id="070f4-179">V Průzkumník řešení zkopírujte *MLModel.zip* soubor z projektu **MLSparkModelML. model** a vložte ho do projektu **MLSparkModelML. ConsoleApp** .</span><span class="sxs-lookup"><span data-stu-id="070f4-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="070f4-180">Odkaz je automaticky přidán do *MLSparkModelML. ConsoleApp. csproj*.</span><span class="sxs-lookup"><span data-stu-id="070f4-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="070f4-181">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="070f4-181">Run your code</span></span>

<span data-ttu-id="070f4-182">Použijte `spark-submit` ke spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="070f4-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="070f4-183">Pomocí příkazového řádku přejděte do kořenové složky vaší aplikace konzoly a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="070f4-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="070f4-184">Nejdřív aplikaci vyčistěte a publikujte.</span><span class="sxs-lookup"><span data-stu-id="070f4-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="070f4-185">Pak přejděte do složky pro publikování konzolové aplikace a spusťte následující `spark-submit` příkaz.</span><span class="sxs-lookup"><span data-stu-id="070f4-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="070f4-186">Nezapomeňte aktualizovat příkaz o skutečnou cestu k vašemu souboru Microsoft Spark jar.</span><span class="sxs-lookup"><span data-stu-id="070f4-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="070f4-187">Získání kódu</span><span class="sxs-lookup"><span data-stu-id="070f4-187">Get the code</span></span>

<span data-ttu-id="070f4-188">Tento kurz je podobný kódu z příkladu [Analýza mínění s velkými](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) objemy dat.</span><span class="sxs-lookup"><span data-stu-id="070f4-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="070f4-189">Další kroky</span><span class="sxs-lookup"><span data-stu-id="070f4-189">Next steps</span></span>

<span data-ttu-id="070f4-190">V dalším článku se dozvíte, jak provádět strukturované streamování pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="070f4-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="070f4-191">Kurz: strukturované streamování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="070f4-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
