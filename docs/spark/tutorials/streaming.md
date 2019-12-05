---
title: Kurz strukturovaného streamování s .NET for Apache Spark
description: V tomto kurzu se naučíte používat rozhraní .NET pro Apache Spark pro strukturované streamování Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: d0fe79ef79125c06be9acd8ba80001a33e150adb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802845"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="7e39e-103">Kurz: strukturované streamování s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7e39e-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span> 

<span data-ttu-id="7e39e-104">V tomto kurzu se naučíte vyvolat strukturované streamování Sparku pomocí rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="7e39e-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="7e39e-105">Strukturované streamování Sparku je Apache Spark podpora pro zpracování datových proudů v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="7e39e-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="7e39e-106">Zpracování datových proudů znamená analýzu živých dat při jejich vyprodukování.</span><span class="sxs-lookup"><span data-stu-id="7e39e-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="7e39e-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="7e39e-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7e39e-108">Vytvoření a spuštění rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="7e39e-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="7e39e-109">Vytvoření datového proudu pomocí NetCat</span><span class="sxs-lookup"><span data-stu-id="7e39e-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="7e39e-110">Použití uživatelsky definovaných funkcí a SparkSQL k analýze dat streamování</span><span class="sxs-lookup"><span data-stu-id="7e39e-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e39e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e39e-111">Prerequisites</span></span>

<span data-ttu-id="7e39e-112">Pokud je to vaše první rozhraní .NET pro Apache Spark aplikaci, začněte v [kurzu Začínáme](get-started.md) , kde se seznámíte se základy.</span><span class="sxs-lookup"><span data-stu-id="7e39e-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7e39e-113">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="7e39e-113">Create a console application</span></span>

1. <span data-ttu-id="7e39e-114">Na příkazovém řádku spusťte následující příkazy k vytvoření nové konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="7e39e-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```console
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="7e39e-115">Příkaz `dotnet` vytvoří pro vás `new`ou aplikaci typu `console`.</span><span class="sxs-lookup"><span data-stu-id="7e39e-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="7e39e-116">Parametr `-o` vytvoří adresář s názvem *mySparkStreamingApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="7e39e-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="7e39e-117">Příkaz `cd mySparkStreamingApp` změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="7e39e-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="7e39e-118">Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark.</span><span class="sxs-lookup"><span data-stu-id="7e39e-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="7e39e-119">V konzole spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7e39e-119">In your console, run the following command:</span></span>

   ```console
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="7e39e-120">Vytvoření datového proudu a připojení k němu</span><span class="sxs-lookup"><span data-stu-id="7e39e-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="7e39e-121">Jedním z oblíbených způsobů testování zpracování streamu je prostřednictvím **NetCat**.</span><span class="sxs-lookup"><span data-stu-id="7e39e-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="7e39e-122">NetCat (označované také jako *NC*) umožňuje číst síťová připojení a zapisovat do nich.</span><span class="sxs-lookup"><span data-stu-id="7e39e-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="7e39e-123">Připojení k síti pomocí NetCat můžete vytvořit prostřednictvím okna terminálu.</span><span class="sxs-lookup"><span data-stu-id="7e39e-123">You establish a network connection with netcat through a terminal window.</span></span> 

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="7e39e-124">Vytvoření datového proudu pomocí NetCat</span><span class="sxs-lookup"><span data-stu-id="7e39e-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="7e39e-125">[Stáhněte si NetCat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="7e39e-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="7e39e-126">Pak extrahujte soubor ze staženého souboru zip a připojíte extrahovaný adresář do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="7e39e-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="7e39e-127">Chcete-li spustit nové připojení, otevřete novou konzolu a spusťte následující příkaz, který se připojí k localhost na portu 9999.</span><span class="sxs-lookup"><span data-stu-id="7e39e-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="7e39e-128">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="7e39e-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="7e39e-129">V Linuxu:</span><span class="sxs-lookup"><span data-stu-id="7e39e-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="7e39e-130">Váš program Spark čeká na vstup, který zadáte do tohoto příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7e39e-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="7e39e-131">Vytvoření SparkSession</span><span class="sxs-lookup"><span data-stu-id="7e39e-131">Create a SparkSession</span></span>

1. <span data-ttu-id="7e39e-132">Do horní části souboru *program.cs* přidejte následující další příkazy `using` v *mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="7e39e-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="7e39e-133">Přidejte následující kód do metody `Main` pro vytvoření nové `SparkSession`.</span><span class="sxs-lookup"><span data-stu-id="7e39e-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="7e39e-134">Relace Spark je vstupním bodem pro programování Sparku s využitím datové sady a rozhraní API dataframe.</span><span class="sxs-lookup"><span data-stu-id="7e39e-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="7e39e-135">Volání objektu *Spark* , který jste vytvořili výše, vám umožní přístup k funkcím Sparku a dataframe v celém programu.</span><span class="sxs-lookup"><span data-stu-id="7e39e-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="7e39e-136">Připojení ke streamu pomocí ReadStream ()</span><span class="sxs-lookup"><span data-stu-id="7e39e-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="7e39e-137">Metoda `ReadStream()` vrátí `DataStreamReader`, která se dá použít ke čtení streamových dat v podobě `DataFrame`.</span><span class="sxs-lookup"><span data-stu-id="7e39e-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="7e39e-138">Zahrňte informace o hostiteli a portu k informování aplikace Spark, kde očekávat jejich streamovaná data.</span><span class="sxs-lookup"><span data-stu-id="7e39e-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="7e39e-139">Registrovat uživatelsky definovanou funkci</span><span class="sxs-lookup"><span data-stu-id="7e39e-139">Register a user-defined function</span></span>

<span data-ttu-id="7e39e-140">UDF, *uživatelsky definované funkce*v aplikacích Spark můžete použít k provádění výpočtů a analýz vašich dat.</span><span class="sxs-lookup"><span data-stu-id="7e39e-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="7e39e-141">Přidejte následující kód do metody `Main` k registraci systému souborů UDF s názvem `udfArray`.</span><span class="sxs-lookup"><span data-stu-id="7e39e-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span> 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="7e39e-142">Tato UDF zpracuje každý řetězec, který obdrží od terminálu netcat, a vytvoří pole, které obsahuje původní řetězec (obsažený v *str*) následovaný původním řetězcem, který je zřetězený s délkou původního řetězce.</span><span class="sxs-lookup"><span data-stu-id="7e39e-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span> 

<span data-ttu-id="7e39e-143">Pokud například zadáte *Hello World* v terminálu netcat, vytvoří se pole, kde:</span><span class="sxs-lookup"><span data-stu-id="7e39e-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="7e39e-144">Array\[0] = Hello World</span><span class="sxs-lookup"><span data-stu-id="7e39e-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="7e39e-145">Array\[1] = Hello World 11</span><span class="sxs-lookup"><span data-stu-id="7e39e-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="7e39e-146">Použití SparkSQL</span><span class="sxs-lookup"><span data-stu-id="7e39e-146">Use SparkSQL</span></span>

<span data-ttu-id="7e39e-147">Pomocí SparkSQL můžete provádět různé funkce s daty uloženými v datovém rámci.</span><span class="sxs-lookup"><span data-stu-id="7e39e-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="7e39e-148">Je běžné kombinovat UDF a SparkSQL pro použití UDF na každý řádek datového rámce.</span><span class="sxs-lookup"><span data-stu-id="7e39e-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="7e39e-149">Tento fragment kódu aplikuje *udfArray* na každou hodnotu v dataframe, která představuje každý řetězec načtený z terminálu NetCat.</span><span class="sxs-lookup"><span data-stu-id="7e39e-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="7e39e-150">Použijte metodu SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> pro vložení každého záznamu pole do vlastního řádku.</span><span class="sxs-lookup"><span data-stu-id="7e39e-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="7e39e-151">Nakonec použijte <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> k umístění sloupců, které jste vytvořili v novém *arrayDFi* dataframe.</span><span class="sxs-lookup"><span data-stu-id="7e39e-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="7e39e-152">Zobrazit datový proud</span><span class="sxs-lookup"><span data-stu-id="7e39e-152">Display your stream</span></span>

<span data-ttu-id="7e39e-153">Použijte <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> k navázání vlastností výstupu, jako je například tisk výsledků do konzoly a zobrazení pouze nejaktuálnějšího výstupu.</span><span class="sxs-lookup"><span data-stu-id="7e39e-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="7e39e-154">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="7e39e-154">Run your code</span></span>

<span data-ttu-id="7e39e-155">Strukturované streamování ve Sparku zpracovává data prostřednictvím řady malých **dávek**.</span><span class="sxs-lookup"><span data-stu-id="7e39e-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="7e39e-156">Když spustíte program, příkazový řádek, kde vytvoříte připojení netcat, vám umožní začít psát.</span><span class="sxs-lookup"><span data-stu-id="7e39e-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="7e39e-157">Pokaždé, když stisknete klávesu ENTER po zadání dat v příkazovém řádku, Spark považuje vaši položku za datovou dávku a spustí systém souborů UDF.</span><span class="sxs-lookup"><span data-stu-id="7e39e-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="7e39e-158">Spuštění aplikace pomocí Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="7e39e-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="7e39e-159">Po spuštění nové relace NetCat otevřete nový terminál a spusťte příkaz `spark-submit`, podobně jako v následujícím příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e39e-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="7e39e-160">Nezapomeňte aktualizovat výše uvedený příkaz o skutečnou cestu k vašemu souboru Microsoft Spark jar.</span><span class="sxs-lookup"><span data-stu-id="7e39e-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="7e39e-161">Výše uvedený příkaz také předpokládá, že váš server NetCat běží na místním počítači s portem 9999.</span><span class="sxs-lookup"><span data-stu-id="7e39e-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="7e39e-162">Získat kód</span><span class="sxs-lookup"><span data-stu-id="7e39e-162">Get the code</span></span>

<span data-ttu-id="7e39e-163">V tomto kurzu se používá příklad [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , ale na GitHubu existují tři další příklady zpracování úplných datových proudů:</span><span class="sxs-lookup"><span data-stu-id="7e39e-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="7e39e-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): počet slov pro datový proud z libovolného zdroje</span><span class="sxs-lookup"><span data-stu-id="7e39e-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="7e39e-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): počet slov pro data s logikou okna</span><span class="sxs-lookup"><span data-stu-id="7e39e-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="7e39e-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): počet slov pro datový proud z Kafka</span><span class="sxs-lookup"><span data-stu-id="7e39e-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="7e39e-167">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7e39e-167">Next steps</span></span>

<span data-ttu-id="7e39e-168">V dalším článku se dozvíte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.</span><span class="sxs-lookup"><span data-stu-id="7e39e-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7e39e-169">Kurz: nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="7e39e-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
