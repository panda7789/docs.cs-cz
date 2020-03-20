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
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Kurz: Strukturované streamování s rozhraním .NET pro Apache Spark

Tento kurz vás naučí, jak vyvolat strukturované streamování Spark pomocí rozhraní .NET pro Apache Spark. Spark Structured Streaming je podpora Apache Spark pro zpracování datových toků v reálném čase. Zpracování datového proudu znamená analýzu živých dat při jejich výrobě.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvoření a spuštění rozhraní .NET pro aplikaci Apache Spark
> * Vytvoření datového proudu pomocí netcatu
> * Použití uživatelem definovaných funkcí a SparkSQL k analýze streamovaných dat

## <a name="prerequisites"></a>Požadavky

Pokud se jedná o první rozhraní .NET pro aplikaci Apache Spark, začněte [s kurzem Začínáme,](get-started.md) abyste se seznámili se základy.

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. V příkazovém řádku vytvořte novou konzolovou aplikaci následujícím příkazem:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   Příkaz `dotnet` vytvoří `new` aplikaci `console` typu pro vás. Parametr `-o` vytvoří adresář s názvem *mySparkStreamingApp,* kde je vaše aplikace uložena a naplní ji požadovanými soubory. Příkaz `cd mySparkStreamingApp` změní adresář na adresář aplikace, který jste právě vytvořili.

1. Chcete-li v aplikaci použít rozhraní .NET pro Apache Spark, nainstalujte balíček Microsoft.Spark. V konzoli spusťte následující příkaz:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Vytvoření datového proudu a připojení k němu

Jeden populární způsob, jak otestovat zpracování datového proudu je prostřednictvím **netcat**. netcat (také známý jako *nc*) umožňuje číst a zapisovat do síťových připojení. Navážete síťové připojení s netcat prostřednictvím okna terminálu.

### <a name="create-a-data-stream-with-netcat"></a>Vytvoření datového proudu pomocí netcatu

1. [Stáhnout netcat](https://sourceforge.net/projects/nc110/files/). Potom extrahujte soubor ze stažení zip a přidejte adresář, který jste extrahovali, do proměnné prostředí PATH.

2. Chcete-li spustit nové připojení, otevřete novou konzolu a spusťte následující příkaz, který se připojuje k localhost na portu 9999.

   Ve Windows:

   ```console
   nc -vvv -l -p 9999
   ```

   Na Linuxu:

   ```console
   nc -lk 9999
   ```

   Program Spark naslouchá zadání, které zadáte do tohoto příkazového řádku.

### <a name="create-a-sparksession"></a>Vytvoření sparksession

1. Přidejte následující `using` další příkazy do horní části *souboru Program.cs* v *aplikaci mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Přidejte do metody `Main` následující kód `SparkSession`a vytvořte nový . Relace Spark je vstupním bodem k programování Spark s datovou sadou a rozhraním DataFrame API.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Volání výše vytvořeného *objektu spark* umožňuje přístup k funkcím Spark a DataFrame v celém programu.

### <a name="connect-to-a-stream-with-readstream"></a>Připojení k datovému proudu pomocí služby ReadStream()

Metoda `ReadStream()` vrátí, `DataStreamReader` které lze použít ke čtení `DataFrame`dat streamování v jako . Zahrňte informace o hostiteli a portu a řekněte aplikaci Spark, kde má očekávat streamovaná data.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Registrace uživatelem definované funkce

K provádění výpočtů a analýz na datech můžete v aplikacích Spark použít uontové soubory, *uživatelem definované funkce*.

Přidejte do `Main` metody následující kód pro `udfArray`registraci udf s názvem .

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Tento UDF zpracovává každý řetězec, který obdrží z terminálu netcat, aby vytvořil pole, které obsahuje původní řetězec (obsažený v *str*), následovaný původním řetězcem zřetězeným s délkou původního řetězce.

Například zadání *Hello world* v terminálu netcat vytváří pole, kde:

* pole\[0] = Hello world
* pole\[1] = Hello world 11

## <a name="use-sparksql"></a>Použití SparkSQL

SparkSQL slouží k provádění různých funkcí na datech uložených v datovém rámci. Je běžné kombinovat UDF a SparkSQL použít UDF pro každý řádek DataFrame.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Tento fragment kódu použije *udfArray* na každou hodnotu v datovém rámci, která představuje každý řetězec přečtený z terminálu netcat. Použijte metodu <xref:Microsoft.Spark.Sql.Functions.Explode%2A> SparkSQL, aby každá položka vašeho pole ve svém vlastním řádku. Nakonec můžete <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> umístit sloupce, které jste vytvořili, do nového *arrayDF DataFrame.*

## <a name="display-your-stream"></a>Zobrazení streamu

Slouží <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> k určení charakteristik výstupu, jako je například tisk výsledků do konzoly a zobrazení pouze nejnovějšího výstupu.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Spuštění kódu

Strukturované streamování v Spark zpracovává data prostřednictvím řady malých **dávek**.  Při spuštění programu vám příkazový řádek, na kterém navážete připojení netcat, umožňuje začít psát. Pokaždé, když po zadání dat do příkazového řádku stisknete klávesu Enter, Spark považuje vaši položku za dávku a spustí UDF.

### <a name="use-spark-submit-to-run-your-app"></a>Spuštění aplikace pomocí spark-submit

Po spuštění nové relace netcat otevřete nový `spark-submit` terminál a spusťte příkaz, podobně jako následující příkaz:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Nezapomeňte aktualizovat výše uvedený příkaz se skutečnou cestou k vašemu souboru Microsoft Spark jar. Výše uvedený příkaz také předpokládá, že váš server netcat běží na portu localhost 9999.

## <a name="get-the-code"></a>Získání kódu

Tento kurz používá [příklad StructuredNetworkCharacterCount.cs,](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) ale existují tři další příklady zpracování celého datového proudu na GitHubu:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): počet slov na data streamovaná z libovolného zdroje
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): počet slov na datech s logikou oken
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): počet slov na data streamovaná z Kafky

## <a name="next-steps"></a>Další kroky

Přejdete k dalšímu článku, kde se dozvíte, jak nasadit .NET pro aplikaci Apache Spark do Databricks.
> [!div class="nextstepaction"]
> [Kurz: Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks](databricks-deployment.md)
