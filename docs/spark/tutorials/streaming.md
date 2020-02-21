---
title: Kurz strukturovaného streamování s .NET for Apache Spark
description: V tomto kurzu se naučíte používat rozhraní .NET pro Apache Spark pro strukturované streamování Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 83d44af080d95ab6f9311ddd3ca4860806757436
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504039"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Kurz: strukturované streamování s rozhraním .NET pro Apache Spark 

V tomto kurzu se naučíte vyvolat strukturované streamování Sparku pomocí rozhraní .NET pro Apache Spark. Strukturované streamování Sparku je Apache Spark podpora pro zpracování datových proudů v reálném čase. Zpracování datových proudů znamená analýzu živých dat při jejich vyprodukování.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvoření a spuštění rozhraní .NET pro Apache Spark aplikaci
> * Vytvoření datového proudu pomocí NetCat
> * Použití uživatelsky definovaných funkcí a SparkSQL k analýze dat streamování

## <a name="prerequisites"></a>Předpoklady

Pokud je to vaše první rozhraní .NET pro Apache Spark aplikaci, začněte v [kurzu Začínáme](get-started.md) , kde se seznámíte se základy.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Na příkazovém řádku spusťte následující příkazy k vytvoření nové konzolové aplikace:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   Příkaz `dotnet` vytvoří pro vás `new`ou aplikaci typu `console`. Parametr `-o` vytvoří adresář s názvem *mySparkStreamingApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory. Příkaz `cd mySparkStreamingApp` změní adresář na adresář aplikace, který jste právě vytvořili.

1. Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark. V konzole spusťte následující příkaz:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Vytvoření datového proudu a připojení k němu

Jedním z oblíbených způsobů testování zpracování streamu je prostřednictvím **NetCat**. NetCat (označované také jako *NC*) umožňuje číst síťová připojení a zapisovat do nich. Připojení k síti pomocí NetCat můžete vytvořit prostřednictvím okna terminálu. 

### <a name="create-a-data-stream-with-netcat"></a>Vytvoření datového proudu pomocí NetCat

1. [Stáhněte si NetCat](https://sourceforge.net/projects/nc110/files/). Pak extrahujte soubor ze staženého souboru zip a připojíte extrahovaný adresář do proměnné prostředí PATH.

2. Chcete-li spustit nové připojení, otevřete novou konzolu a spusťte následující příkaz, který se připojí k localhost na portu 9999.

   Ve Windows:

   ```console
   nc -vvv -l -p 9999
   ```

   V Linuxu:

   ```console
   nc -lk 9999
   ```

   Váš program Spark čeká na vstup, který zadáte do tohoto příkazového řádku.

### <a name="create-a-sparksession"></a>Vytvoření SparkSession

1. Do horní části souboru *program.cs* přidejte následující další příkazy `using` v *mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Přidejte následující kód do metody `Main` pro vytvoření nové `SparkSession`. Relace Spark je vstupním bodem pro programování Sparku s využitím datové sady a rozhraní API dataframe.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Volání objektu *Spark* , který jste vytvořili výše, vám umožní přístup k funkcím Sparku a dataframe v celém programu.

### <a name="connect-to-a-stream-with-readstream"></a>Připojení ke streamu pomocí ReadStream ()

Metoda `ReadStream()` vrátí `DataStreamReader`, která se dá použít ke čtení streamových dat v podobě `DataFrame`. Zahrňte informace o hostiteli a portu k informování aplikace Spark, kde očekávat jejich streamovaná data.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Registrovat uživatelsky definovanou funkci

UDF, *uživatelsky definované funkce*v aplikacích Spark můžete použít k provádění výpočtů a analýz vašich dat.

Přidejte následující kód do metody `Main` k registraci systému souborů UDF s názvem `udfArray`. 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Tato UDF zpracuje každý řetězec, který obdrží od terminálu netcat, a vytvoří pole, které obsahuje původní řetězec (obsažený v *str*) následovaný původním řetězcem, který je zřetězený s délkou původního řetězce. 

Pokud například zadáte *Hello World* v terminálu netcat, vytvoří se pole, kde:

* Array\[0] = Hello World
* Array\[1] = Hello World 11

## <a name="use-sparksql"></a>Použití SparkSQL

Pomocí SparkSQL můžete provádět různé funkce s daty uloženými v datovém rámci. Je běžné kombinovat UDF a SparkSQL pro použití UDF na každý řádek datového rámce.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Tento fragment kódu aplikuje *udfArray* na každou hodnotu v dataframe, která představuje každý řetězec načtený z terminálu NetCat. Použijte metodu SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> pro vložení každého záznamu pole do vlastního řádku. Nakonec použijte <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> k umístění sloupců, které jste vytvořili v novém *arrayDFi* dataframe.

## <a name="display-your-stream"></a>Zobrazit datový proud

Použijte <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> k navázání vlastností výstupu, jako je například tisk výsledků do konzoly a zobrazení pouze nejaktuálnějšího výstupu.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Spuštění kódu

Strukturované streamování ve Sparku zpracovává data prostřednictvím řady malých **dávek**.  Když spustíte program, příkazový řádek, kde vytvoříte připojení netcat, vám umožní začít psát. Pokaždé, když stisknete klávesu ENTER po zadání dat v příkazovém řádku, Spark považuje vaši položku za datovou dávku a spustí systém souborů UDF.

### <a name="use-spark-submit-to-run-your-app"></a>Spuštění aplikace pomocí Spark-Submit

Po spuštění nové relace NetCat otevřete nový terminál a spusťte příkaz `spark-submit`, podobně jako v následujícím příkazu:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Nezapomeňte aktualizovat výše uvedený příkaz o skutečnou cestu k vašemu souboru Microsoft Spark jar. Výše uvedený příkaz také předpokládá, že váš server NetCat běží na místním počítači s portem 9999.

## <a name="get-the-code"></a>Získání kódu

V tomto kurzu se používá příklad [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , ale na GitHubu existují tři další příklady zpracování úplných datových proudů:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): počet slov pro datový proud z libovolného zdroje
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): počet slov pro data s logikou okna
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): počet slov pro datový proud z Kafka

## <a name="next-steps"></a>Další kroky

V dalším článku se dozvíte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.
> [!div class="nextstepaction"]
> [Kurz: nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů](databricks-deployment.md)
