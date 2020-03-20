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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Kurz: Dávkové zpracování s rozhraním .NET pro Apache Spark

V tomto kurzu se dozvíte, jak provést dávkové zpracování pomocí rozhraní .NET pro Apache Spark. Dávkové zpracování je transformace dat v klidovém stavu, což znamená, že zdrojová data již byla načtena do úložiště dat.

Dávkové zpracování se obvykle provádí přes velké, ploché datové sady, které je třeba připravit pro další analýzu. Zpracování protokolů a ukládání dat jsou běžné scénáře dávkového zpracování. V tomto scénáři analyzovat informace o projektech GitHub, jako je například počet, kdy byly rozdvojené různé projekty nebo jak nedávno byly aktualizovány projekty.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvoření a spuštění rozhraní .NET pro aplikaci Apache Spark
> * Čtení dat do datového rámce a jejich příprava na analýzu
> * Zpracování dat pomocí Spark SQL

## <a name="prerequisites"></a>Požadavky

Pokud používáte rozhraní .NET pro Apache Spark poprvé, podívejte se na kurz [Začínáme s rozhraním .NET pro Apache Spark,](../tutorials/get-started.md) kde se dozvíte, jak připravit prostředí a spustit první .NET pro aplikaci Apache Spark.

## <a name="download-the-sample-data"></a>Stažení ukázkových dat

[GHTorrent](http://ghtorrent.org/) monitoruje všechny veřejné události GitHub, jako jsou informace o projektech, potvrzeních a pozorovatelích, a ukládá události a jejich strukturu do databází. Údaje shromážděné v různých časových obdobích jsou k dispozici jako archivy ke stažení. Vzhledem k tomu, že soubory s výpisem stavu paměti jsou velmi velké, tato příručka používá [zkrácenou verzi souboru s výpisem stavu paměti,](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) kterou lze stáhnout z GitHubu.

> [!NOTE]
> Datový soubor GHTorrent je distribuován v rámci dvojího licenčního systému ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)). Pro nekomerční použití (mimo jiné včetně vzdělávacího, výzkumného nebo osobního použití) je datová sada distribuována pod [licencí CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. V příkazovém řádku vytvořte novou konzolovou aplikaci následujícím příkazem:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   Příkaz `dotnet` vytvoří `new` aplikaci `console` typu pro vás. Parametr `-o` vytvoří adresář s názvem *mySparkBatchApp,* kde je vaše aplikace uložena a naplní ji požadovanými soubory. Příkaz `cd mySparkBatchApp` změní adresář na adresář aplikace, který jste právě vytvořili.

1. Chcete-li v aplikaci použít rozhraní .NET pro Apache Spark, nainstalujte balíček Microsoft.Spark. V konzoli spusťte následující příkaz:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Vytvoření sparksession

1. Přidejte následující `using` další příkazy do horní části *souboru Program.cs* v *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Přidejte následující kód do oboru názvů projektu. *s_referenceData* se později v programu používá k filtrování podle data.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Přidejte následující kód uvnitř hlavní metody vytvořit novou SparkSession. SparkSession je vstupní bod pro programování Spark s datovou sadou a rozhraním DataFrame API. Voláním `spark` objektu můžete přistupovat k funkcím Spark a DataFrame v celém programu.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Příprava dat

1. Přečtěte si vstupní `DataFrame`soubor do , což je distribuovaná kolekce dat uspořádaných do pojmenovaných sloupců. Sloupce pro data můžete nastavit <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>prostřednictvím aplikace . Pomocí <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> metody můžete zobrazit data v datovém rámci. Nezapomeňte aktualizovat cestu k souboru CSV do umístění stažených dat GitHubu.

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

1. Pomocí <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> metody můžete vyřadit řádky s <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> hodnotami NA (null) a metodu k odebrání určitých sloupců z dat. To pomáhá zabránit chybám, pokud se pokusíte analyzovat nulová data nebo sloupce, které nejsou relevantní pro konečnou analýzu.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analýza dat

Spark SQL umožňuje provádět volání SQL na vaše data. Je běžné kombinovat uživatelem definované funkce a Spark SQL použít uživatelem definovanou funkci na všechny řádky datového rámce.

Můžete konkrétně `spark.Sql` volat napodobovat standardní volání SQL vidět v jiných typech aplikací. Můžete také volat <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> metody, jako je a <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> konkrétně kombinovat, filtrovat a provádět výpočty na data.

Cílem této aplikace je získat nějaké poznatky o datech projektů GitHub. Přidejte do programu následující fragmenty kódu a analyzujte data.

1. Přidejte následující blok kódu vyhledá počet, kolikrát byl každý jazyk rozdvojený. Nejprve jsou data seskupena podle jazyka. Potom je přijata průměrný počet vidliček z každého jazyka.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Přidejte následující blok kódu, chcete-li seřadit průměrný počet rozdvojených výrazů v sestupném pořadí, abyste zjistili, které jazyky jsou nejvíce rozdvojené. To znamená, že největší počet vidliček se objeví jako první.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. Další blok kódu ukazuje, jak nedávno byly aktualizovány projekty. Zaregistrujete novou uživatelem definovanou funkci s názvem *MyUDF* a porovnáte ji s *datem, s_referenceDate*, který byl deklarován na začátku kurzu. Datum pro každý projekt je porovnáno s referenčním datem. Potom Spark SQL se používá k volání UDF na každém řádku dat k analýze každého projektu v datové sadě.

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

1. Volání `spark.Stop()` ukončení SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Spuštění aplikace pomocí spark-submit

1. K vytvoření aplikace .NET použijte následující příkaz:

   ```dotnetcli
   dotnet build
   ```

1. Spusťte `spark-submit`aplikaci s aplikací . Nezapomeňte aktualizovat následující příkaz o skutečné cesty k souboru Microsoft Spark jar.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Získání kódu

Můžete vidět [úplné řešení](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) na GitHubu.

## <a name="next-steps"></a>Další kroky

Přejdete k dalšímu článku, kde se dozvíte, jak zpracovávat streamovaná data pomocí rozhraní .NET pro Apache Spark.
> [!div class="nextstepaction"]
> [Kurz: Strukturované streamování s rozhraním .NET pro Apache Spark](streaming.md)
