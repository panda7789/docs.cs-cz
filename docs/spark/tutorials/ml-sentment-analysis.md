---
title: Analýza mínění s rozhraním .NET pro Apache Spark a kurz ML.NET
description: V tomto kurzu se dozvíte, jak používat ML.NET s rozhraním .NET pro Apache Spark pro analýzu mínění.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345339"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="3e31a-103">Kurz: Analýza mínění s rozhraním .NET pro Apache Spark a ML.NET</span><span class="sxs-lookup"><span data-stu-id="3e31a-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="3e31a-104">Tento kurz vás naučí, jak provést analýzu mínění online recenzí pomocí ML.NET a .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3e31a-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="3e31a-105">[ML.NET](http://dot.net/ml) je bezplatný, multiplatformní rámec strojového učení s otevřeným zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="3e31a-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="3e31a-106">Můžete použít ML.NET s .NET pro Apache Spark škálovat školení a predikce algoritmů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="3e31a-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="3e31a-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="3e31a-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="3e31a-108">Vytvořte model analýzy mínění pomocí ML.NET Tvůrce modelů v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e31a-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="3e31a-109">Vytvořte rozhraní .NET pro konzolovou aplikaci Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3e31a-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="3e31a-110">Zapište a implementujte uživatelem definovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="3e31a-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="3e31a-111">Spusťte rozhraní .NET pro konzolovou aplikaci Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3e31a-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e31a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e31a-112">Prerequisites</span></span>

* <span data-ttu-id="3e31a-113">Pokud jste nevyvinuli .NET pro aplikaci Apache Spark dříve, začněte s [kurzem Začínáme,](get-started.md) abyste se seznámili se základy.</span><span class="sxs-lookup"><span data-stu-id="3e31a-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="3e31a-114">Než budete pokračovat v tomto kurzu, dokončete všechny předpoklady pro kurz Začínáme.</span><span class="sxs-lookup"><span data-stu-id="3e31a-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="3e31a-115">Tento kurz používá ML.NET Tvůrce modelů (preview), vizuální rozhraní dostupné v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e31a-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="3e31a-116">Pokud ještě visual studio nemáte, můžete si zdarma stáhnout verzi sady Visual Studio ve [verzi Visual Studia.](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="3e31a-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="3e31a-117">[Stažení a instalace](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Tvůrce modelů (náhled).</span><span class="sxs-lookup"><span data-stu-id="3e31a-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="3e31a-118">Stáhněte si datové sady [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) a [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.</span><span class="sxs-lookup"><span data-stu-id="3e31a-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="3e31a-119">Kontrola údajů</span><span class="sxs-lookup"><span data-stu-id="3e31a-119">Review the data</span></span>

<span data-ttu-id="3e31a-120">Dataset recenzí Yelpu obsahuje online recenze Yelpu o různých službách.</span><span class="sxs-lookup"><span data-stu-id="3e31a-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="3e31a-121">Otevřete [soubor yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) a všimněte si struktury dat.</span><span class="sxs-lookup"><span data-stu-id="3e31a-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="3e31a-122">První sloupec obsahuje text recenze a druhý sloupec obsahuje skóre mínění.</span><span class="sxs-lookup"><span data-stu-id="3e31a-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="3e31a-123">Pokud je skóre mínění 1, recenze je kladná a pokud je skóre mínění 0, je recenze záporná.</span><span class="sxs-lookup"><span data-stu-id="3e31a-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="3e31a-124">Následující tabulka obsahuje ukázková data:</span><span class="sxs-lookup"><span data-stu-id="3e31a-124">The following table contains sample data:</span></span>

|<span data-ttu-id="3e31a-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="3e31a-125">ReviewText</span></span>|<span data-ttu-id="3e31a-126">Mínění</span><span class="sxs-lookup"><span data-stu-id="3e31a-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="3e31a-127">Wow... Miloval toto místo.</span><span class="sxs-lookup"><span data-stu-id="3e31a-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="3e31a-128">1</span><span class="sxs-lookup"><span data-stu-id="3e31a-128">1</span></span>|
|<span data-ttu-id="3e31a-129">Kůrka není dobrá.</span><span class="sxs-lookup"><span data-stu-id="3e31a-129">Crust is not good.</span></span>|    <span data-ttu-id="3e31a-130">0</span><span class="sxs-lookup"><span data-stu-id="3e31a-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="3e31a-131">Sestavte si svůj model strojového učení</span><span class="sxs-lookup"><span data-stu-id="3e31a-131">Build your machine learning model</span></span>

1. <span data-ttu-id="3e31a-132">Otevřete Visual Studio a vytvořte novou aplikaci konzoly C# (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="3e31a-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="3e31a-133">Název projektu *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="3e31a-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="3e31a-134">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *MLSparkModel.*</span><span class="sxs-lookup"><span data-stu-id="3e31a-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="3e31a-135">Pak vyberte **Přidat > strojové učení**.</span><span class="sxs-lookup"><span data-stu-id="3e31a-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="3e31a-136">V ML.NET Tvůrce modelů vyberte dlaždici **scénáře Analýzy mínění.**</span><span class="sxs-lookup"><span data-stu-id="3e31a-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="3e31a-137">Na stránce **Přidat data** nahrajte datovou sadu *yelptrain.csv.*</span><span class="sxs-lookup"><span data-stu-id="3e31a-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="3e31a-138">Z rozbalovací nabídky **Sloupce k předvídání** zvolte *Mínění.*</span><span class="sxs-lookup"><span data-stu-id="3e31a-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="3e31a-139">Na stránce **Vlak** nastavte čas tréninku na *60 sekund* a vyberte **Spustit trénink**.</span><span class="sxs-lookup"><span data-stu-id="3e31a-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="3e31a-140">Všimněte si stavu tréninku v části **Průběh**.</span><span class="sxs-lookup"><span data-stu-id="3e31a-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="3e31a-141">Po dokončení školení Builder, **Vyhodnotit** výsledky školení.</span><span class="sxs-lookup"><span data-stu-id="3e31a-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="3e31a-142">Do textového pole pod položkou **Vyzkoušejte model** a výběrem **možnosti Předpovědět** můžete zadat fráze, chcete-li zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="3e31a-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="3e31a-143">Vyberte **Kód** a pak vyberte **Přidat projekty** a přidejte model ML do řešení.</span><span class="sxs-lookup"><span data-stu-id="3e31a-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="3e31a-144">Všimněte si, že do vašich řešení jsou přidány dva projekty: **MLSparkModelML.ConsoleApp** a **MLSparkModelML.Model**.</span><span class="sxs-lookup"><span data-stu-id="3e31a-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="3e31a-145">Poklepejte na projektu *MLSpark* C# a všimněte si, že byl přidán následující odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="3e31a-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="3e31a-146">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="3e31a-146">Create a console app</span></span>

<span data-ttu-id="3e31a-147">Tvůrce modelů pro vás vytvoří konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e31a-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="3e31a-148">Klepněte pravým tlačítkem myši na **mlstovam v** Průzkumníku řešení a vyberte **příkaz Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e31a-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="3e31a-149">Vyhledejte **Microsoft.Spark** a nainstalujte balíček.</span><span class="sxs-lookup"><span data-stu-id="3e31a-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="3e31a-150">**Microsoft.ML** je automaticky nainstalován pro vás Builder.</span><span class="sxs-lookup"><span data-stu-id="3e31a-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="3e31a-151">Vytvoření sparksession</span><span class="sxs-lookup"><span data-stu-id="3e31a-151">Create a SparkSession</span></span>

1. <span data-ttu-id="3e31a-152">Otevřete soubor *Program.cs* pro **soubor MLSparkModelML.ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="3e31a-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="3e31a-153">Tento soubor byl automaticky generován tvůrcem modelů.</span><span class="sxs-lookup"><span data-stu-id="3e31a-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="3e31a-154">Odstraňte `using` příkazy, obsah Main() metoda `CreateSingleDataSample` a oblast.</span><span class="sxs-lookup"><span data-stu-id="3e31a-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="3e31a-155">Na začátek `using` *Program.cs*přidejte následující další příkazy :</span><span class="sxs-lookup"><span data-stu-id="3e31a-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="3e31a-156">Změňte `DATA_FILEPATH` cestu *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="3e31a-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="3e31a-157">Přidejte do metody `Main` následující kód `SparkSession`a vytvořte nový .</span><span class="sxs-lookup"><span data-stu-id="3e31a-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="3e31a-158">Relace Spark je vstupním bodem k programování Spark s datovou sadou a rozhraním DataFrame API.</span><span class="sxs-lookup"><span data-stu-id="3e31a-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="3e31a-159">Volání výše vytvořeného *objektu spark* umožňuje přístup k funkcím Spark a DataFrame v celém programu.</span><span class="sxs-lookup"><span data-stu-id="3e31a-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="3e31a-160">Vytvoření datového rámečku a tisk na konzolu</span><span class="sxs-lookup"><span data-stu-id="3e31a-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="3e31a-161">Přečtěte si v yelp recenzi data ze souboru `DataFrame` *yelptest.csv* jako .</span><span class="sxs-lookup"><span data-stu-id="3e31a-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="3e31a-162">Zahrnout `header` `inferSchema` a možnosti.</span><span class="sxs-lookup"><span data-stu-id="3e31a-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="3e31a-163">Možnost `header` přečte první řádek *yelptest.csv* jako názvy sloupců namísto dat.</span><span class="sxs-lookup"><span data-stu-id="3e31a-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="3e31a-164">Tato `inferSchema` možnost odvodí typy sloupců na základě dat.</span><span class="sxs-lookup"><span data-stu-id="3e31a-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="3e31a-165">Registrace uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="3e31a-165">Register a user-defined function</span></span>

<span data-ttu-id="3e31a-166">K provádění výpočtů a analýz na datech můžete použít uontové soubory, *uživatelem definované funkce*, v aplikacích Spark.</span><span class="sxs-lookup"><span data-stu-id="3e31a-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="3e31a-167">V tomto kurzu použijete ML.NET s UDF k vyhodnocení každé recenze Yelpu.</span><span class="sxs-lookup"><span data-stu-id="3e31a-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="3e31a-168">Přidejte do `Main` metody následující kód pro `MLudf`registraci udf s názvem .</span><span class="sxs-lookup"><span data-stu-id="3e31a-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="3e31a-169">Tento UDF bere řetězec yelpu recenzi jako vstup a výstupy true nebo false pro pozitivní nebo negativní pocity, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3e31a-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="3e31a-170">Používá *predict()* metodu, kterou definujete v pozdějším kroku.</span><span class="sxs-lookup"><span data-stu-id="3e31a-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="3e31a-171">Volání UDF pomocí Spark SQL</span><span class="sxs-lookup"><span data-stu-id="3e31a-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="3e31a-172">Teď, když jste si přečetli data a začlenili ML, použijte Spark SQL k volání UDF, který spustí analýzu mínění na každém řádku datového rámce.</span><span class="sxs-lookup"><span data-stu-id="3e31a-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="3e31a-173">Do metody přidejte `Main` následující kód:</span><span class="sxs-lookup"><span data-stu-id="3e31a-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="3e31a-174">Vytvořit metodu predict()</span><span class="sxs-lookup"><span data-stu-id="3e31a-174">Create predict() method</span></span>

<span data-ttu-id="3e31a-175">Před `Main()` metodu přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3e31a-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="3e31a-176">Tento kód je podobný tomu, co je produkován Model Builder v *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="3e31a-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="3e31a-177">Přesunutím této metody do konzole načtete model načítání při každém spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e31a-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="3e31a-178">Přidání modelu do konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="3e31a-178">Add the model to your console app</span></span>

<span data-ttu-id="3e31a-179">V Průzkumníku řešení zkopírujte soubor *MLModel.zip* z projektu **MLSparkModelML.Model** a vložte jej do projektu **MLSparkModelML.ConsoleApp.**</span><span class="sxs-lookup"><span data-stu-id="3e31a-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="3e31a-180">Odkaz je automaticky přidán do *MLSToModelML.ConsoleApp.csproj*.</span><span class="sxs-lookup"><span data-stu-id="3e31a-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="3e31a-181">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="3e31a-181">Run your code</span></span>

<span data-ttu-id="3e31a-182">Slouží `spark-submit` ke spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="3e31a-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="3e31a-183">Přejděte do kořenové složky aplikace konzoly pomocí příkazového řádku a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="3e31a-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="3e31a-184">Nejprve vyčistěte a publikujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e31a-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="3e31a-185">Potom přejděte do složky publikování aplikace `spark-submit` konzoly a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="3e31a-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="3e31a-186">Nezapomeňte aktualizovat příkaz se skutečnou cestou vašeho souboru Microsoft Spark jar.</span><span class="sxs-lookup"><span data-stu-id="3e31a-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="3e31a-187">Získání kódu</span><span class="sxs-lookup"><span data-stu-id="3e31a-187">Get the code</span></span>

<span data-ttu-id="3e31a-188">Tento kurz je podobný kódu z analýzy mínění s velkým [objemem dat.](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)</span><span class="sxs-lookup"><span data-stu-id="3e31a-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3e31a-189">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3e31a-189">Next steps</span></span>

<span data-ttu-id="3e31a-190">Přejdete k dalšímu článku, kde se dozvíte, jak provést strukturované streamování pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3e31a-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3e31a-191">Kurz: Strukturované streamování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3e31a-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
