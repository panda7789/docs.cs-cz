---
title: Strukturované streamování s rozhraním .NET pro kurz Apache Spark
description: V tomto kurzu se dozvíte, jak používat rozhraní .NET pro Apache Spark pro strukturované streamování Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186514"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="cfc53-103">Kurz: Strukturované streamování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="cfc53-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="cfc53-104">Tento kurz vás naučí, jak vyvolat strukturované streamování Spark pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="cfc53-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="cfc53-105">Spark Structured Streaming je podpora Apache Spark pro zpracování datových toků v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="cfc53-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="cfc53-106">Zpracování datového proudu znamená analýzu živých dat při jejich výrobě.</span><span class="sxs-lookup"><span data-stu-id="cfc53-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="cfc53-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="cfc53-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="cfc53-108">Vytvoření a spuštění rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="cfc53-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="cfc53-109">Vytvoření datového proudu pomocí netcatu</span><span class="sxs-lookup"><span data-stu-id="cfc53-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="cfc53-110">Použití uživatelem definovaných funkcí a SparkSQL k analýze streamovaných dat</span><span class="sxs-lookup"><span data-stu-id="cfc53-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cfc53-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfc53-111">Prerequisites</span></span>

<span data-ttu-id="cfc53-112">Pokud se jedná o první rozhraní .NET pro aplikaci Apache Spark, začněte [s kurzem Začínáme,](get-started.md) abyste se seznámili se základy.</span><span class="sxs-lookup"><span data-stu-id="cfc53-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="cfc53-113">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="cfc53-113">Create a console application</span></span>

1. <span data-ttu-id="cfc53-114">V příkazovém řádku vytvořte novou konzolovou aplikaci následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="cfc53-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="cfc53-115">Příkaz `dotnet` vytvoří `new` aplikaci `console` typu pro vás.</span><span class="sxs-lookup"><span data-stu-id="cfc53-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="cfc53-116">Parametr `-o` vytvoří adresář s názvem *mySparkStreamingApp,* kde je vaše aplikace uložena a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="cfc53-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="cfc53-117">Příkaz `cd mySparkStreamingApp` změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="cfc53-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="cfc53-118">Chcete-li v aplikaci použít rozhraní .NET pro Apache Spark, nainstalujte balíček Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="cfc53-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="cfc53-119">V konzoli spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="cfc53-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="cfc53-120">Vytvoření datového proudu a připojení k němu</span><span class="sxs-lookup"><span data-stu-id="cfc53-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="cfc53-121">Jeden populární způsob, jak otestovat zpracování datového proudu je prostřednictvím **netcat**.</span><span class="sxs-lookup"><span data-stu-id="cfc53-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="cfc53-122">netcat (také známý jako *nc*) umožňuje číst a zapisovat do síťových připojení.</span><span class="sxs-lookup"><span data-stu-id="cfc53-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="cfc53-123">Navážete síťové připojení s netcat prostřednictvím okna terminálu.</span><span class="sxs-lookup"><span data-stu-id="cfc53-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="cfc53-124">Vytvoření datového proudu pomocí netcatu</span><span class="sxs-lookup"><span data-stu-id="cfc53-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="cfc53-125">[Stáhnout netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="cfc53-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="cfc53-126">Potom extrahujte soubor ze stažení zip a přidejte adresář, který jste extrahovali, do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="cfc53-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="cfc53-127">Chcete-li spustit nové připojení, otevřete novou konzolu a spusťte následující příkaz, který se připojuje k localhost na portu 9999.</span><span class="sxs-lookup"><span data-stu-id="cfc53-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="cfc53-128">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="cfc53-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="cfc53-129">Na Linuxu:</span><span class="sxs-lookup"><span data-stu-id="cfc53-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="cfc53-130">Program Spark naslouchá zadání, které zadáte do tohoto příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cfc53-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="cfc53-131">Vytvoření sparksession</span><span class="sxs-lookup"><span data-stu-id="cfc53-131">Create a SparkSession</span></span>

1. <span data-ttu-id="cfc53-132">Přidejte následující `using` další příkazy do horní části *souboru Program.cs* v *aplikaci mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="cfc53-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="cfc53-133">Přidejte do metody `Main` následující kód `SparkSession`a vytvořte nový .</span><span class="sxs-lookup"><span data-stu-id="cfc53-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="cfc53-134">Relace Spark je vstupním bodem k programování Spark s datovou sadou a rozhraním DataFrame API.</span><span class="sxs-lookup"><span data-stu-id="cfc53-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="cfc53-135">Volání výše vytvořeného *objektu spark* umožňuje přístup k funkcím Spark a DataFrame v celém programu.</span><span class="sxs-lookup"><span data-stu-id="cfc53-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="cfc53-136">Připojení k datovému proudu pomocí služby ReadStream()</span><span class="sxs-lookup"><span data-stu-id="cfc53-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="cfc53-137">Metoda `ReadStream()` vrátí, `DataStreamReader` které lze použít ke čtení `DataFrame`dat streamování v jako .</span><span class="sxs-lookup"><span data-stu-id="cfc53-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="cfc53-138">Zahrňte informace o hostiteli a portu a řekněte aplikaci Spark, kde má očekávat streamovaná data.</span><span class="sxs-lookup"><span data-stu-id="cfc53-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="cfc53-139">Registrace uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="cfc53-139">Register a user-defined function</span></span>

<span data-ttu-id="cfc53-140">K provádění výpočtů a analýz na datech můžete v aplikacích Spark použít uontové soubory, *uživatelem definované funkce*.</span><span class="sxs-lookup"><span data-stu-id="cfc53-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="cfc53-141">Přidejte do `Main` metody následující kód pro `udfArray`registraci udf s názvem .</span><span class="sxs-lookup"><span data-stu-id="cfc53-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="cfc53-142">Tento UDF zpracovává každý řetězec, který obdrží z terminálu netcat, aby vytvořil pole, které obsahuje původní řetězec (obsažený v *str*), následovaný původním řetězcem zřetězeným s délkou původního řetězce.</span><span class="sxs-lookup"><span data-stu-id="cfc53-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="cfc53-143">Například zadání *Hello world* v terminálu netcat vytváří pole, kde:</span><span class="sxs-lookup"><span data-stu-id="cfc53-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="cfc53-144">pole\[0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="cfc53-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="cfc53-145">pole\[1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="cfc53-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="cfc53-146">Použití SparkSQL</span><span class="sxs-lookup"><span data-stu-id="cfc53-146">Use SparkSQL</span></span>

<span data-ttu-id="cfc53-147">SparkSQL slouží k provádění různých funkcí na datech uložených v datovém rámci.</span><span class="sxs-lookup"><span data-stu-id="cfc53-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="cfc53-148">Je běžné kombinovat UDF a SparkSQL použít UDF pro každý řádek DataFrame.</span><span class="sxs-lookup"><span data-stu-id="cfc53-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="cfc53-149">Tento fragment kódu použije *udfArray* na každou hodnotu v datovém rámci, která představuje každý řetězec přečtený z terminálu netcat.</span><span class="sxs-lookup"><span data-stu-id="cfc53-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="cfc53-150">Použijte metodu <xref:Microsoft.Spark.Sql.Functions.Explode%2A> SparkSQL, aby každá položka vašeho pole ve svém vlastním řádku.</span><span class="sxs-lookup"><span data-stu-id="cfc53-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="cfc53-151">Nakonec můžete <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> umístit sloupce, které jste vytvořili, do nového *arrayDF DataFrame.*</span><span class="sxs-lookup"><span data-stu-id="cfc53-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="cfc53-152">Zobrazení streamu</span><span class="sxs-lookup"><span data-stu-id="cfc53-152">Display your stream</span></span>

<span data-ttu-id="cfc53-153">Slouží <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> k určení charakteristik výstupu, jako je například tisk výsledků do konzoly a zobrazení pouze nejnovějšího výstupu.</span><span class="sxs-lookup"><span data-stu-id="cfc53-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="cfc53-154">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="cfc53-154">Run your code</span></span>

<span data-ttu-id="cfc53-155">Strukturované streamování v Spark zpracovává data prostřednictvím řady malých **dávek**.</span><span class="sxs-lookup"><span data-stu-id="cfc53-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="cfc53-156">Při spuštění programu vám příkazový řádek, na kterém navážete připojení netcat, umožňuje začít psát.</span><span class="sxs-lookup"><span data-stu-id="cfc53-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="cfc53-157">Pokaždé, když po zadání dat do příkazového řádku stisknete klávesu Enter, Spark považuje vaši položku za dávku a spustí UDF.</span><span class="sxs-lookup"><span data-stu-id="cfc53-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="cfc53-158">Spuštění aplikace pomocí spark-submit</span><span class="sxs-lookup"><span data-stu-id="cfc53-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="cfc53-159">Po spuštění nové relace netcat otevřete nový `spark-submit` terminál a spusťte příkaz, podobně jako následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="cfc53-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="cfc53-160">Nezapomeňte aktualizovat výše uvedený příkaz se skutečnou cestou k vašemu souboru Microsoft Spark jar.</span><span class="sxs-lookup"><span data-stu-id="cfc53-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="cfc53-161">Výše uvedený příkaz také předpokládá, že váš server netcat běží na portu localhost 9999.</span><span class="sxs-lookup"><span data-stu-id="cfc53-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="cfc53-162">Získání kódu</span><span class="sxs-lookup"><span data-stu-id="cfc53-162">Get the code</span></span>

<span data-ttu-id="cfc53-163">Tento kurz používá [příklad StructuredNetworkCharacterCount.cs,](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) ale existují tři další příklady zpracování celého datového proudu na GitHubu:</span><span class="sxs-lookup"><span data-stu-id="cfc53-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="cfc53-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): počet slov na data streamovaná z libovolného zdroje</span><span class="sxs-lookup"><span data-stu-id="cfc53-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="cfc53-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): počet slov na datech s logikou oken</span><span class="sxs-lookup"><span data-stu-id="cfc53-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="cfc53-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): počet slov na data streamovaná z Kafky</span><span class="sxs-lookup"><span data-stu-id="cfc53-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="cfc53-167">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cfc53-167">Next steps</span></span>

<span data-ttu-id="cfc53-168">Přejdete k dalšímu článku, kde se dozvíte, jak nasadit .NET pro aplikaci Apache Spark do Databricks.</span><span class="sxs-lookup"><span data-stu-id="cfc53-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="cfc53-169">Kurz: Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks</span><span class="sxs-lookup"><span data-stu-id="cfc53-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
