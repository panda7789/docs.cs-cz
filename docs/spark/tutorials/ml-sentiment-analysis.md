---
title: Analýza mínění s rozhraním .NET pro Apache Spark a kurz ML.NET
description: V tomto kurzu se dozvíte, jak používat ML.NET s rozhraním .NET pro Apache Spark pro analýzu mínění.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391256"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Kurz: Analýza mínění s rozhraním .NET pro Apache Spark a ML.NET

Tento kurz vás naučí, jak provést analýzu mínění online recenzí pomocí ML.NET a .NET pro Apache Spark. [ML.NET](http://dot.net/ml) je bezplatný, multiplatformní rámec strojového učení s otevřeným zdrojovým kódem. Můžete použít ML.NET s .NET pro Apache Spark škálovat školení a predikce algoritmů strojového učení.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvořte model analýzy mínění pomocí ML.NET Tvůrce modelů v sadě Visual Studio.
> * Vytvořte rozhraní .NET pro konzolovou aplikaci Apache Spark.
> * Zapište a implementujte uživatelem definovanou funkci.
> * Spusťte rozhraní .NET pro konzolovou aplikaci Apache Spark.

## <a name="prerequisites"></a>Požadavky

* Pokud jste nevyvinuli .NET pro aplikaci Apache Spark dříve, začněte s [kurzem Začínáme,](get-started.md) abyste se seznámili se základy. Než budete pokračovat v tomto kurzu, dokončete všechny předpoklady pro kurz Začínáme.

* Tento kurz používá ML.NET Tvůrce modelů (preview), vizuální rozhraní dostupné v sadě Visual Studio. Pokud ještě visual studio nemáte, můžete si zdarma stáhnout verzi sady Visual Studio ve [verzi Visual Studia.](https://visualstudio.microsoft.com/downloads/)

* [Stažení a instalace](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Tvůrce modelů (náhled).

* Stáhněte si datové sady [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) a [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.

## <a name="review-the-data"></a>Kontrola údajů

Dataset recenzí Yelpu obsahuje online recenze Yelpu o různých službách. Otevřete [soubor yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) a všimněte si struktury dat. První sloupec obsahuje text recenze a druhý sloupec obsahuje skóre mínění. Pokud je skóre mínění 1, recenze je kladná a pokud je skóre mínění 0, je recenze záporná.

Následující tabulka obsahuje ukázková data:

|ReviewText|Mínění|
|-|-|
|Wow... Miloval toto místo.|    1|
|Kůrka není dobrá.|    0|

## <a name="build-your-machine-learning-model"></a>Sestavte si svůj model strojového učení

1. Otevřete Visual Studio a vytvořte novou aplikaci konzoly C# (.NET Core). Název projektu *MLSparkModel*.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *MLSparkModel.* Pak vyberte **Přidat > strojové učení**.

1. V ML.NET Tvůrce modelů vyberte dlaždici **scénáře Analýzy mínění.**

1. Na stránce **Přidat data** nahrajte datovou sadu *yelptrain.csv.*

1. Z rozbalovací nabídky **Sloupce k předvídání** zvolte *Mínění.*

1. Na stránce **Vlak** nastavte čas tréninku na *60 sekund* a vyberte **Spustit trénink**. Všimněte si stavu tréninku v části **Průběh**.

1. Po dokončení školení Builder, **Vyhodnotit** výsledky školení. Do textového pole pod položkou **Vyzkoušejte model** a výběrem **možnosti Předpovědět** můžete zadat fráze, chcete-li zobrazit výstup.

1. Vyberte **Kód** a pak vyberte **Přidat projekty** a přidejte model ML do řešení.

1. Všimněte si, že do vašich řešení jsou přidány dva projekty: **MLSparkModelML.ConsoleApp** a **MLSparkModelML.Model**.

1. Poklepejte na projektu *MLSpark* C# a všimněte si, že byl přidán následující odkaz na projekt.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Vytvoření konzolové aplikace

Tvůrce modelů pro vás vytvoří konzolovou aplikaci.

1. Klepněte pravým tlačítkem myši na **mlstovam v** Průzkumníku řešení a vyberte **příkaz Spravovat balíčky NuGet**.

1. Vyhledejte **Microsoft.Spark** a nainstalujte balíček. **Microsoft.ML** je automaticky nainstalován pro vás Builder.

### <a name="create-a-sparksession"></a>Vytvoření sparksession

1. Otevřete soubor *Program.cs* pro **soubor MLSparkModelML.ConsoleApp**. Tento soubor byl automaticky generován tvůrcem modelů. Odstraňte `using` příkazy, obsah Main() metoda `CreateSingleDataSample` a oblast.

1. Na začátek `using` *Program.cs*přidejte následující další příkazy :

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Změňte `DATA_FILEPATH` cestu *yelptest.csv*.

1. Přidejte do metody `Main` následující kód `SparkSession`a vytvořte nový . Relace Spark je vstupním bodem k programování Spark s datovou sadou a rozhraním DataFrame API.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Volání výše vytvořeného *objektu spark* umožňuje přístup k funkcím Spark a DataFrame v celém programu.

### <a name="create-a-dataframe-and-print-to-console"></a>Vytvoření datového rámečku a tisk na konzolu

Přečtěte si v yelp recenzi data ze souboru `DataFrame` *yelptest.csv* jako . Zahrnout `header` `inferSchema` a možnosti. Možnost `header` přečte první řádek *yelptest.csv* jako názvy sloupců namísto dat. Tato `inferSchema` možnost odvodí typy sloupců na základě dat.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Registrace uživatelem definované funkce

K provádění výpočtů a analýz na datech můžete použít uontové soubory, *uživatelem definované funkce*, v aplikacích Spark. V tomto kurzu použijete ML.NET s UDF k vyhodnocení každé recenze Yelpu.

Přidejte do `Main` metody následující kód pro `MLudf`registraci udf s názvem .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Tento UDF bere řetězec yelpu recenzi jako vstup a výstupy true nebo false pro pozitivní nebo negativní pocity, v uvedeném pořadí. Používá *predict()* metodu, kterou definujete v pozdějším kroku.

### <a name="use-spark-sql-to-call-the-udf"></a>Volání UDF pomocí Spark SQL

Teď, když jste si přečetli data a začlenili ML, použijte Spark SQL k volání UDF, který spustí analýzu mínění na každém řádku datového rámce. Do metody přidejte `Main` následující kód:

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

### <a name="create-predict-method"></a>Vytvořit metodu predict()

Před `Main()` metodu přidejte následující kód. Tento kód je podobný tomu, co je produkován Model Builder v *ConsumeModel.cs*. Přesunutím této metody do konzole načtete model načítání při každém spuštění aplikace.

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

## <a name="add-the-model-to-your-console-app"></a>Přidání modelu do konzolové aplikace

V Průzkumníku řešení zkopírujte soubor *MLModel.zip* z projektu **MLSparkModelML.Model** a vložte jej do projektu **MLSparkModelML.ConsoleApp.** Odkaz je automaticky přidán do *MLSToModelML.ConsoleApp.csproj*.

## <a name="run-your-code"></a>Spuštění kódu

Slouží `spark-submit` ke spuštění kódu. Přejděte do kořenové složky aplikace konzoly pomocí příkazového řádku a spusťte následující příkazy.

Nejprve vyčistěte a publikujte aplikaci.

```dotnetcli
dotnet clean
dotnet publish
```

Potom přejděte do složky publikování aplikace `spark-submit` konzoly a spusťte následující příkaz. Nezapomeňte aktualizovat příkaz se skutečnou cestou vašeho souboru Microsoft Spark jar.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Získání kódu

Tento kurz je podobný kódu z analýzy mínění s velkým [objemem dat.](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)

## <a name="next-steps"></a>Další kroky

Přejdete k dalšímu článku, kde se dozvíte, jak provést strukturované streamování pomocí rozhraní .NET pro Apache Spark.
> [!div class="nextstepaction"]
> [Kurz: Strukturované streamování s rozhraním .NET pro Apache Spark](streaming.md)
