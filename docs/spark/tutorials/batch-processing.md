---
title: Kurz dávkového zpracování pomocí .NET pro Apache Spark
description: Naučte se provádět dávkové zpracování pomocí .NET pro Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: bd91fb401b9beb6ae74c4599b25e43284473f8b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75466411"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="f2a3a-103">Kurz: zpracování služby Batch pomocí rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f2a3a-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="f2a3a-104">V tomto kurzu se naučíte, jak provádět dávkové zpracování pomocí .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="f2a3a-105">Dávkové zpracování je transformační data v klidovém režimu, což znamená, že zdrojová data již byla načtena do úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span> 

<span data-ttu-id="f2a3a-106">Dávkové zpracování se obvykle provádí přes velké ploché datové sady, které je potřeba připravit k další analýze.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="f2a3a-107">Zpracování protokolů a datové sklady jsou běžné scénáře dávkového zpracování.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="f2a3a-108">V tomto scénáři analyzujete informace o projektech GitHubu, jako je počet rozvětvených různých projektů nebo jejich poslední aktualizace.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span> 

<span data-ttu-id="f2a3a-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="f2a3a-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f2a3a-110">Vytvoření a spuštění rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="f2a3a-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="f2a3a-111">Čtení dat do datového rámce a příprava na analýzu</span><span class="sxs-lookup"><span data-stu-id="f2a3a-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="f2a3a-112">Zpracování dat pomocí Spark SQL</span><span class="sxs-lookup"><span data-stu-id="f2a3a-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2a3a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2a3a-113">Prerequisites</span></span> 

<span data-ttu-id="f2a3a-114">Pokud používáte rozhraní .NET pro Apache Spark poprvé, přečtěte si kurz [Začínáme s rozhraním .NET for Apache Spark](../tutorials/get-started.md) , kde se dozvíte, jak připravit prostředí a spustit první .net pro Apache Spark aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="f2a3a-115">Stažení ukázkových dat</span><span class="sxs-lookup"><span data-stu-id="f2a3a-115">Download the sample data</span></span>

<span data-ttu-id="f2a3a-116">[GHTorrent](http://ghtorrent.org/) sleduje všechny veřejné události GitHubu, například informace o projektech, potvrzeních a sledovacích procesech a ukládá události a jejich strukturu do databází.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="f2a3a-117">Data shromážděná v různých časových obdobích jsou k dispozici jako archivy ke stažení.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="f2a3a-118">Vzhledem k tomu, že jsou soubory s výpisem paměti velmi velké, používá tato příručka [zkrácenou verzi souboru s výpisem paměti](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) , kterou je možné stáhnout z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="f2a3a-119">Datová sada GHTorrent je distribuována v rámci duálního licenčního schématu ([Creative) +](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="f2a3a-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="f2a3a-120">V případě nekomerčních použití (včetně, ale ne výhradně pro vzdělávací, výzkumné nebo osobní použití) je datová sada distribuována v rámci [licence CC-by-sa](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="f2a3a-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f2a3a-121">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="f2a3a-121">Create a console application</span></span>

1. <span data-ttu-id="f2a3a-122">Na příkazovém řádku spusťte následující příkazy k vytvoření nové konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="f2a3a-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="f2a3a-123">Příkaz `dotnet` vytvoří pro vás `new`ou aplikaci typu `console`.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="f2a3a-124">Parametr `-o` vytvoří adresář s názvem *mySparkBatchApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="f2a3a-125">Příkaz `cd mySparkBatchApp` změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="f2a3a-126">Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="f2a3a-127">V konzole spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f2a3a-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="f2a3a-128">Vytvoření SparkSession</span><span class="sxs-lookup"><span data-stu-id="f2a3a-128">Create a SparkSession</span></span>

1. <span data-ttu-id="f2a3a-129">Přidejte následující další příkazy `using` do horní části souboru *program.cs* v *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="f2a3a-130">Do oboru názvů projektu přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="f2a3a-131">*s_referenceData* se později v programu používá k filtrování podle data.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="f2a3a-132">Do metody Main přidejte následující kód, který vytvoří nový SparkSession.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="f2a3a-133">SparkSession je vstupním bodem pro programování Sparku s využitím datové sady a rozhraní API dataframe.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="f2a3a-134">Voláním objektu `spark` máte přístup k funkcím Spark a dataframe v celém programu.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="f2a3a-135">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="f2a3a-135">Prepare the data</span></span>

1. <span data-ttu-id="f2a3a-136">Přečtěte si vstupní soubor do `DataFrame`, což je distribuovaná kolekce dat uspořádaných do pojmenovaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="f2a3a-137">Sloupce pro data můžete nastavit prostřednictvím <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="f2a3a-138">K zobrazení dat v datovém rámečku použijte metodu <xref:Microsoft.Spark.Sql.DataFrame.Show%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="f2a3a-139">Nezapomeňte aktualizovat cestu k souboru CSV na umístění dat GitHubu, která jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. <span data-ttu-id="f2a3a-140">Použijte metodu <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> pro odtažení řádků s hodnotami NEDEF (null) a metodu <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> k odebrání určitých sloupců z dat.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="f2a3a-141">To pomáhá předcházet chybám při pokusu o analýzu dat nebo sloupců s hodnotou null, které nejsou relevantní pro vaši konečnou analýzu.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="f2a3a-142">Analýza dat</span><span class="sxs-lookup"><span data-stu-id="f2a3a-142">Analyze the data</span></span>

<span data-ttu-id="f2a3a-143">Spark SQL umožňuje provádět volání SQL na vašich datech.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="f2a3a-144">Je běžné kombinovat uživatelsky definované funkce a Spark SQL pro aplikování uživatelsky definované funkce na všechny řádky vašeho datového rámce.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="f2a3a-145">Můžete konkrétně volat `spark.Sql` pro napodobování standardních volání SQL zjištěných v jiných typech aplikací.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="f2a3a-146">Můžete také volat metody jako <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> a <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> a konkrétně kombinovat, filtrovat a provádět výpočty s daty.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="f2a3a-147">Cílem této aplikace je získat další přehledy o datech projektů GitHubu.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="f2a3a-148">Přidejte následující fragmenty kódu do programu pro analýzu dat.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="f2a3a-149">Přidat následující blok kódu najde počet rozvětvení jednotlivých jazyků.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="f2a3a-150">Nejprve se data seskupují podle jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-150">First, the data is grouped by language.</span></span> <span data-ttu-id="f2a3a-151">Pak se vybere průměrný počet rozvětvení z jednotlivých jazyků.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="f2a3a-152">Přidejte následující blok kódu pro seřazení průměrného počtu rozvětvení v sestupném pořadí, abyste viděli, které jazyky jsou nejvíce rozvětvené.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="f2a3a-153">To znamená, že se jako první zobrazí největší počet rozvětvení.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show(); 
   ```

1. <span data-ttu-id="f2a3a-154">Další blok kódu ukazuje, jak se nedávno aktualizovaly projekty.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="f2a3a-155">Zaregistrujete novou uživatelsky definovanou funkci s názvem *MyUDF* a porovnejte ji s datem, *s_referenceDate*, který byl deklarován na začátku kurzu.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="f2a3a-156">Datum pro každý projekt je porovnáno s referenčním datem.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="f2a3a-157">Spark SQL se pak používá k volání UDF na každém řádku dat k analýze každého projektu v sadě dat.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);   
   cleanedProjects.CreateOrReplaceTempView("dateView"); 

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. <span data-ttu-id="f2a3a-158">Zavolejte `spark.Stop()` pro ukončení SparkSession.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="f2a3a-159">Spuštění aplikace pomocí Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="f2a3a-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="f2a3a-160">K sestavení aplikace .NET použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f2a3a-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="f2a3a-161">Spusťte aplikaci pomocí `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="f2a3a-162">Nezapomeňte aktualizovat následující příkaz se skutečnými cestami k vašemu souboru Microsoft Spark jar.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="f2a3a-163">Získat kód</span><span class="sxs-lookup"><span data-stu-id="f2a3a-163">Get the code</span></span>

<span data-ttu-id="f2a3a-164">[Kompletní řešení](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) můžete zobrazit na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2a3a-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f2a3a-165">Next steps</span></span>

<span data-ttu-id="f2a3a-166">V dalším článku se dozvíte, jak zpracovávat streamovaná data pomocí .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f2a3a-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f2a3a-167">Kurz: strukturované streamování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f2a3a-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
