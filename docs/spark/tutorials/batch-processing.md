---
title: Dávkové zpracování s rozhraním .NET pro kurz Apache Spark
description: Přečtěte si, jak dávkové zpracování pomocí rozhraní .NET pro Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187556"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="34297-103">Kurz: Dávkové zpracování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34297-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="34297-104">V tomto kurzu se dozvíte, jak provést dávkové zpracování pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="34297-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="34297-105">Dávkové zpracování je transformace dat v klidovém stavu, což znamená, že zdrojová data již byla načtena do úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="34297-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="34297-106">Dávkové zpracování se obvykle provádí přes velké, ploché datové sady, které je třeba připravit pro další analýzu.</span><span class="sxs-lookup"><span data-stu-id="34297-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="34297-107">Zpracování protokolů a ukládání dat jsou běžné scénáře dávkového zpracování.</span><span class="sxs-lookup"><span data-stu-id="34297-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="34297-108">V tomto scénáři analyzovat informace o projektech GitHub, jako je například počet, kdy byly rozdvojené různé projekty nebo jak nedávno byly aktualizovány projekty.</span><span class="sxs-lookup"><span data-stu-id="34297-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="34297-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="34297-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="34297-110">Vytvoření a spuštění rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34297-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="34297-111">Čtení dat do datového rámce a jejich příprava na analýzu</span><span class="sxs-lookup"><span data-stu-id="34297-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="34297-112">Zpracování dat pomocí Spark SQL</span><span class="sxs-lookup"><span data-stu-id="34297-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34297-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34297-113">Prerequisites</span></span>

<span data-ttu-id="34297-114">Pokud používáte rozhraní .NET pro Apache Spark poprvé, podívejte se na kurz [Začínáme s rozhraním .NET pro Apache Spark,](../tutorials/get-started.md) kde se dozvíte, jak připravit prostředí a spustit první .NET pro aplikaci Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="34297-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="34297-115">Stažení ukázkových dat</span><span class="sxs-lookup"><span data-stu-id="34297-115">Download the sample data</span></span>

<span data-ttu-id="34297-116">[GHTorrent](http://ghtorrent.org/) monitoruje všechny veřejné události GitHub, jako jsou informace o projektech, potvrzeních a pozorovatelích, a ukládá události a jejich strukturu do databází.</span><span class="sxs-lookup"><span data-stu-id="34297-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="34297-117">Údaje shromážděné v různých časových obdobích jsou k dispozici jako archivy ke stažení.</span><span class="sxs-lookup"><span data-stu-id="34297-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="34297-118">Vzhledem k tomu, že soubory s výpisem stavu paměti jsou velmi velké, tato příručka používá [zkrácenou verzi souboru s výpisem stavu paměti,](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) kterou lze stáhnout z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="34297-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="34297-119">Datový soubor GHTorrent je distribuován v rámci dvojího licenčního systému ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="34297-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="34297-120">Pro nekomerční použití (mimo jiné včetně vzdělávacího, výzkumného nebo osobního použití) je datová sada distribuována pod [licencí CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="34297-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="34297-121">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="34297-121">Create a console application</span></span>

1. <span data-ttu-id="34297-122">V příkazovém řádku vytvořte novou konzolovou aplikaci následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="34297-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="34297-123">Příkaz `dotnet` vytvoří `new` aplikaci `console` typu pro vás.</span><span class="sxs-lookup"><span data-stu-id="34297-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="34297-124">Parametr `-o` vytvoří adresář s názvem *mySparkBatchApp,* kde je vaše aplikace uložena a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="34297-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="34297-125">Příkaz `cd mySparkBatchApp` změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="34297-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="34297-126">Chcete-li v aplikaci použít rozhraní .NET pro Apache Spark, nainstalujte balíček Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="34297-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="34297-127">V konzoli spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="34297-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="34297-128">Vytvoření sparksession</span><span class="sxs-lookup"><span data-stu-id="34297-128">Create a SparkSession</span></span>

1. <span data-ttu-id="34297-129">Přidejte následující `using` další příkazy do horní části *souboru Program.cs* v *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="34297-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="34297-130">Přidejte následující kód do oboru názvů projektu.</span><span class="sxs-lookup"><span data-stu-id="34297-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="34297-131">*s_referenceData* se později v programu používá k filtrování podle data.</span><span class="sxs-lookup"><span data-stu-id="34297-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="34297-132">Přidejte následující kód uvnitř hlavní metody vytvořit novou SparkSession.</span><span class="sxs-lookup"><span data-stu-id="34297-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="34297-133">SparkSession je vstupní bod pro programování Spark s datovou sadou a rozhraním DataFrame API.</span><span class="sxs-lookup"><span data-stu-id="34297-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="34297-134">Voláním `spark` objektu můžete přistupovat k funkcím Spark a DataFrame v celém programu.</span><span class="sxs-lookup"><span data-stu-id="34297-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="34297-135">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="34297-135">Prepare the data</span></span>

1. <span data-ttu-id="34297-136">Přečtěte si vstupní `DataFrame`soubor do , což je distribuovaná kolekce dat uspořádaných do pojmenovaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="34297-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="34297-137">Sloupce pro data můžete nastavit <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>prostřednictvím aplikace .</span><span class="sxs-lookup"><span data-stu-id="34297-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="34297-138">Pomocí <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> metody můžete zobrazit data v datovém rámci.</span><span class="sxs-lookup"><span data-stu-id="34297-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="34297-139">Nezapomeňte aktualizovat cestu k souboru CSV do umístění stažených dat GitHubu.</span><span class="sxs-lookup"><span data-stu-id="34297-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="34297-140">Pomocí <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> metody můžete vyřadit řádky s <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> hodnotami NA (null) a metodu k odebrání určitých sloupců z dat.</span><span class="sxs-lookup"><span data-stu-id="34297-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="34297-141">To pomáhá zabránit chybám, pokud se pokusíte analyzovat nulová data nebo sloupce, které nejsou relevantní pro konečnou analýzu.</span><span class="sxs-lookup"><span data-stu-id="34297-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="34297-142">Analýza dat</span><span class="sxs-lookup"><span data-stu-id="34297-142">Analyze the data</span></span>

<span data-ttu-id="34297-143">Spark SQL umožňuje provádět volání SQL na vaše data.</span><span class="sxs-lookup"><span data-stu-id="34297-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="34297-144">Je běžné kombinovat uživatelem definované funkce a Spark SQL použít uživatelem definovanou funkci na všechny řádky datového rámce.</span><span class="sxs-lookup"><span data-stu-id="34297-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="34297-145">Můžete konkrétně `spark.Sql` volat napodobovat standardní volání SQL vidět v jiných typech aplikací.</span><span class="sxs-lookup"><span data-stu-id="34297-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="34297-146">Můžete také volat <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> metody, jako je a <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> konkrétně kombinovat, filtrovat a provádět výpočty na data.</span><span class="sxs-lookup"><span data-stu-id="34297-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="34297-147">Cílem této aplikace je získat nějaké poznatky o datech projektů GitHub.</span><span class="sxs-lookup"><span data-stu-id="34297-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="34297-148">Přidejte do programu následující fragmenty kódu a analyzujte data.</span><span class="sxs-lookup"><span data-stu-id="34297-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="34297-149">Přidejte následující blok kódu vyhledá počet, kolikrát byl každý jazyk rozdvojený.</span><span class="sxs-lookup"><span data-stu-id="34297-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="34297-150">Nejprve jsou data seskupena podle jazyka.</span><span class="sxs-lookup"><span data-stu-id="34297-150">First, the data is grouped by language.</span></span> <span data-ttu-id="34297-151">Potom je přijata průměrný počet vidliček z každého jazyka.</span><span class="sxs-lookup"><span data-stu-id="34297-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="34297-152">Přidejte následující blok kódu, chcete-li seřadit průměrný počet rozdvojených výrazů v sestupném pořadí, abyste zjistili, které jazyky jsou nejvíce rozdvojené.</span><span class="sxs-lookup"><span data-stu-id="34297-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="34297-153">To znamená, že největší počet vidliček se objeví jako první.</span><span class="sxs-lookup"><span data-stu-id="34297-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="34297-154">Další blok kódu ukazuje, jak nedávno byly aktualizovány projekty.</span><span class="sxs-lookup"><span data-stu-id="34297-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="34297-155">Zaregistrujete novou uživatelem definovanou funkci s názvem *MyUDF* a porovnáte ji s *datem, s_referenceDate*, který byl deklarován na začátku kurzu.</span><span class="sxs-lookup"><span data-stu-id="34297-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="34297-156">Datum pro každý projekt je porovnáno s referenčním datem.</span><span class="sxs-lookup"><span data-stu-id="34297-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="34297-157">Potom Spark SQL se používá k volání UDF na každém řádku dat k analýze každého projektu v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="34297-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="34297-158">Volání `spark.Stop()` ukončení SparkSession.</span><span class="sxs-lookup"><span data-stu-id="34297-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="34297-159">Spuštění aplikace pomocí spark-submit</span><span class="sxs-lookup"><span data-stu-id="34297-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="34297-160">K vytvoření aplikace .NET použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="34297-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="34297-161">Spusťte `spark-submit`aplikaci s aplikací .</span><span class="sxs-lookup"><span data-stu-id="34297-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="34297-162">Nezapomeňte aktualizovat následující příkaz o skutečné cesty k souboru Microsoft Spark jar.</span><span class="sxs-lookup"><span data-stu-id="34297-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="34297-163">Získání kódu</span><span class="sxs-lookup"><span data-stu-id="34297-163">Get the code</span></span>

<span data-ttu-id="34297-164">Můžete vidět [úplné řešení](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="34297-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="34297-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="34297-165">Next steps</span></span>

<span data-ttu-id="34297-166">Přejdete k dalšímu článku, kde se dozvíte, jak zpracovávat streamovaná data pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="34297-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="34297-167">Kurz: Strukturované streamování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34297-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
