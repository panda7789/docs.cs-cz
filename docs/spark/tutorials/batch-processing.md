---
title: Kurz dávkového zpracování pomocí .NET pro Apache Spark
description: Naučte se provádět dávkové zpracování pomocí .NET pro Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: b00f560317c085058d791e17954603670fccf60f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594514"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Kurz: zpracování služby Batch pomocí rozhraní .NET pro Apache Spark

V tomto kurzu se naučíte, jak provádět dávkové zpracování pomocí .NET pro Apache Spark. Dávkové zpracování je transformační data v klidovém režimu, což znamená, že zdrojová data již byla načtena do úložiště dat.

Dávkové zpracování se obvykle provádí přes velké ploché datové sady, které je potřeba připravit k další analýze. Zpracování protokolů a datové sklady jsou běžné scénáře dávkového zpracování. V tomto scénáři analyzujete informace o projektech GitHubu, jako je počet rozvětvených různých projektů nebo jejich poslední aktualizace.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvoření a spuštění rozhraní .NET pro Apache Spark aplikaci
> * Čtení dat do datového rámce a příprava na analýzu
> * Zpracování dat pomocí Spark SQL

## <a name="prerequisites"></a>Požadavky

Pokud používáte rozhraní .NET pro Apache Spark poprvé, přečtěte si kurz [Začínáme s rozhraním .NET for Apache Spark](get-started.md) , kde se dozvíte, jak připravit prostředí a spustit první .net pro Apache Spark aplikaci.

## <a name="download-the-sample-data"></a>Stažení ukázkových dat

[GHTorrent](http://ghtorrent.org/) sleduje všechny veřejné události GitHubu, například informace o projektech, potvrzeních a sledovacích procesech a ukládá události a jejich strukturu do databází. Data shromážděná v různých časových obdobích jsou k dispozici jako archivy ke stažení. Vzhledem k tomu, že jsou soubory s výpisem paměti velmi velké, používá tato příručka [zkrácenou verzi souboru s výpisem paměti](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) , kterou je možné stáhnout z GitHubu.

> [!NOTE]
> Datová sada GHTorrent je distribuována v rámci duálního licenčního schématu ([Creative) +](https://wiki.creativecommons.org/wiki/CCPlus)). V případě nekomerčních použití (včetně, ale ne výhradně pro vzdělávací, výzkumné nebo osobní použití) je datová sada distribuována v rámci [licence CC-by-sa](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

1. Na příkazovém řádku spusťte následující příkazy k vytvoření nové konzolové aplikace:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   `dotnet`Příkaz vytvoří `new` aplikaci typu `console` pro vás. `-o`Parametr vytvoří adresář s názvem *mySparkBatchApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory. `cd mySparkBatchApp`Příkaz změní adresář na adresář aplikace, který jste právě vytvořili.

1. Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark. V konzole spusťte následující příkaz:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Vytvoření SparkSession

1. Přidejte následující další `using` příkazy do horní části souboru *program.cs* v *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Do oboru názvů projektu přidejte následující kód. *s_referenceData* se později v programu používá k filtrování podle data.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Do metody Main přidejte následující kód, který vytvoří nový SparkSession. SparkSession je vstupním bodem pro programování Sparku s využitím datové sady a rozhraní API dataframe. Voláním `spark` objektu můžete získat přístup k funkcím Spark a dataframe v celém programu.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Příprava dat

1. Přečtěte si vstupní soubor do `DataFrame` , což je distribuovaná kolekce dat uspořádaných do pojmenovaných sloupců. Sloupce pro data můžete nastavit prostřednictvím <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> . Použijte <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> metodu k zobrazení dat v datovém rámci. Nezapomeňte aktualizovat cestu k souboru CSV na umístění dat GitHubu, která jste stáhli.

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

1. Použijte <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> metodu pro odtažení řádků s hodnotami na (null) a <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> metodu pro odebrání určitých sloupců z dat. To pomáhá předcházet chybám při pokusu o analýzu dat nebo sloupců s hodnotou null, které nejsou relevantní pro vaši konečnou analýzu.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analýza dat

Spark SQL umožňuje provádět volání SQL na vašich datech. Je běžné kombinovat uživatelsky definované funkce a Spark SQL pro aplikování uživatelsky definované funkce na všechny řádky vašeho datového rámce.

Konkrétně můžete zavolat `spark.Sql` na podobná standardní volání SQL zjištěná v jiných typech aplikací. Můžete také volat metody jako <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> a <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> k konkrétně kombinování, filtrování a provádění výpočtů s daty.

Cílem této aplikace je získat další přehledy o datech projektů GitHubu. Přidejte následující fragmenty kódu do programu pro analýzu dat.

1. Přidat následující blok kódu najde počet rozvětvení jednotlivých jazyků. Nejprve se data seskupují podle jazyka. Pak se vybere průměrný počet rozvětvení z jednotlivých jazyků.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Přidejte následující blok kódu pro seřazení průměrného počtu rozvětvení v sestupném pořadí, abyste viděli, které jazyky jsou nejvíce rozvětvené. To znamená, že se jako první zobrazí největší počet rozvětvení.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. Další blok kódu ukazuje, jak se nedávno aktualizovaly projekty. Zaregistrujete novou uživatelsky definovanou funkci s názvem *MyUDF* a porovnejte ji s datem, *s_referenceDate*, který byl deklarován na začátku kurzu. Datum pro každý projekt je porovnáno s referenčním datem. Spark SQL se pak používá k volání UDF na každém řádku dat k analýze každého projektu v sadě dat.

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

1. Zavolejte `spark.Stop()` na konec SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Spuštění aplikace pomocí Spark-Submit

1. K sestavení aplikace .NET použijte následující příkaz:

   ```dotnetcli
   dotnet build
   ```

1. Spusťte aplikaci pomocí `spark-submit` . Nezapomeňte aktualizovat následující příkaz se skutečnými cestami k vašemu souboru Microsoft Spark jar.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Získání kódu

[Kompletní řešení](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) můžete zobrazit na GitHubu.

## <a name="next-steps"></a>Další kroky

V dalším článku se dozvíte, jak zpracovávat streamovaná data pomocí .NET pro Apache Spark.
> [!div class="nextstepaction"]
> [Kurz: strukturované streamování s rozhraním .NET pro Apache Spark](streaming.md)
