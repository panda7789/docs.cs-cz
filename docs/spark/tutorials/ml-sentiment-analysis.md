---
title: Kurz analýzy mínění s rozhraním .NET pro Apache Spark a ML.NET
description: V tomto kurzu se naučíte používat ML.NET s .NET pro Apache Spark pro analýzu mínění.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 69deb30419b98536fa309547d94f59bb266e413c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617574"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Kurz: analýza mínění pomocí technologie .NET pro Apache Spark a ML.NET

V tomto kurzu se naučíte, jak provádět analýzu online recenzí mínění pomocí ML.NET a .NET pro Apache Spark. [Ml.NET](http://dot.net/ml) je bezplatná platforma pro strojové učení open source pro různé platformy. ML.NET můžete použít s rozhraním .NET pro Apache Spark ke škálování školení a předpovědi algoritmů strojového učení.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvoření modelu analýzy mínění pomocí Tvůrce modelů ML.NET v aplikaci Visual Studio.
> * Vytvořte aplikaci pro konzolu .NET pro Apache Spark.
> * Zápis a implementace uživatelsky definované funkce.
> * Spusťte konzolovou aplikaci .NET pro Apache Spark.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Požadavky

* Pokud jste ještě nevyvinuli rozhraní .NET pro Apache Spark aplikaci, začněte pomocí [Začínáme kurzu](get-started.md) , kde se seznámíte se základy. Před pokračováním v tomto kurzu dokončete všechny požadavky pro Začínáme kurz.

* V tomto kurzu se používá k dispozici vizuální rozhraní tvůrce modelů ML.NET (Preview), které je dostupné v aplikaci Visual Studio. Pokud ještě nemáte Visual Studio, můžete [si zdarma stáhnout verzi sady Visual Studio pro komunitu](https://visualstudio.microsoft.com/downloads/) .

* [Stáhnout a nainstalovat](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET model Builder (Preview).

* Stáhněte [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) a [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp zkontrolovat datové sady.

## <a name="review-the-data"></a>Kontrola dat

Datová sada Yelp Reviews obsahuje online Yelp recenze o různých službách. Otevřete [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) a Všimněte si struktury dat. První sloupec obsahuje text Revize a druhý sloupec obsahuje mínění skóre. Pokud je mínění skóre 1, je kontrola kladná a pokud je skóre mínění 0, kontrola je záporná.

Následující tabulka obsahuje ukázková data:

|ReviewText|Mínění|
|-|-|
|Wow... Tohle místo.|    1|
|Crust není dobrá.|    0|

## <a name="build-your-machine-learning-model"></a>Sestavení modelu Machine Learning

1. Otevřete Visual Studio a vytvořte novou konzolovou aplikaci v jazyce C# (.NET Core). Pojmenujte projekt *MLSparkModel*.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *MLSparkModel* . Pak vyberte **přidat > Machine Learning**.

1. V Tvůrci modelů ML.NET vyberte dlaždici **Analýza mínění** scénář.

1. Na stránce **Přidat data** nahrajte *yelptrain.csv* datovou sadu.

1. Vyberte *mínění* ze **sloupců k předpovědi** rozevíracího seznamu.

1. Na stránce **vlak** nastavte čas na vlak na *60 sekund* a vyberte **Spustit školení**. V části **průběh**si všimněte stavu školení.

1. Po dokončení školení pro tvůrce modelů **vyhodnoťte** výsledky školení. Do textového pole níže můžete zadat fráze a **vyzkoušet** si tak výstup a pak vybrat **předpověď** .

1. Vyberte **kód** a pak vyberte **Přidat projekty** a přidejte do řešení model ml.

1. Všimněte si, že do řešení jsou přidány dva projekty: **MLSparkModelML. ConsoleApp** a **MLSparkModelML. model**.

1. Dvakrát klikněte na projekt C# *MLSpark* a Všimněte si, že byl přidán následující odkaz na projekt.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Vytvoření konzolové aplikace

Tvůrce modelů vytvoří pro vás konzolovou aplikaci.

1. V Průzkumník řešení klikněte pravým tlačítkem na **MLSparkModelML. Console** a vyberte **Spravovat balíčky NuGet**.

1. Vyhledejte **Microsoft. Spark** a nainstalujte balíček. **Microsoft.ml** se automaticky nainstaluje pomocí Tvůrce modelů.

### <a name="create-a-sparksession"></a>Vytvoření SparkSession

1. Otevřete soubor *program.cs* pro **MLSparkModelML. ConsoleApp**. Tento soubor byl automaticky vygenerován pomocí Tvůrce modelů. Odstraňte `using` příkazy, obsah metody Main () a `CreateSingleDataSample` oblast.

1. `using`Do horní části *program.cs*přidejte následující dodatečné příkazy:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Změňte na `DATA_FILEPATH` cestu k vašemu *yelptest.csv*.

1. Přidejte následující kód do `Main` metody pro vytvoření nového `SparkSession` . Relace Spark je vstupním bodem pro programování Sparku s využitím datové sady a rozhraní API dataframe.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Volání objektu *Spark* , který jste vytvořili výše, vám umožní přístup k funkcím Sparku a dataframe v celém programu.

### <a name="create-a-dataframe-and-print-to-console"></a>Vytvoření datového rámce a tisk do konzoly

Přečtěte si v Yelp data ze souboru *yelptest.csv* jako `DataFrame` . Zahrnutí `header` a `inferSchema` Možnosti. `header`Možnost načte první řádek *yelptest.csv* jako názvy sloupců místo dat. `inferSchema`Možnost odvodí typy sloupců na základě dat.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Registrovat uživatelsky definovanou funkci

UDF, *uživatelsky definované funkce*v aplikacích Spark můžete použít k výpočtům a analýzám vašich dat. V tomto kurzu použijete ML.NET se systémem souborů UDF k vyhodnocení každé kontroly Yelp.

Přidejte následující kód do `Main` metody pro registraci volání UDF `MLudf` .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Tato UDF přebírá řetězec Yelp revize jako vstup a výstupy hodnot true nebo false pro kladné nebo záporné zabarvení, v uvedeném pořadí. Používá metodu *předpověď ()* , kterou definujete v pozdějším kroku.

### <a name="use-spark-sql-to-call-the-udf"></a>Použití Spark SQL pro volání UDF

Teď, když jste si přečetli svoje data a zahrnuli ML, použijte Spark SQL pro volání UDF, který spustí analýzu mínění na každém řádku vašeho datového rámce. Do metody přidejte následující kód `Main` :

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

### <a name="create-predict-method"></a>Create prediktivní () – metoda

Do své metody přidejte následující kód `Main()` . Tento kód je podobný tomu, co je vytvořeno tvůrcem modelů v *ConsumeModel.cs*. Přesunutím této metody do konzoly načtete model načítání při každém spuštění aplikace.

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

## <a name="add-the-model-to-your-console-app"></a>Přidání modelu do aplikace konzoly

V Průzkumník řešení zkopírujte *MLModel.zip* soubor z projektu **MLSparkModelML. model** a vložte ho do projektu **MLSparkModelML. ConsoleApp** . Odkaz je automaticky přidán do *MLSparkModelML. ConsoleApp. csproj*.

## <a name="run-your-code"></a>Spuštění kódu

Použijte `spark-submit` ke spuštění kódu. Pomocí příkazového řádku přejděte do kořenové složky vaší aplikace konzoly a spusťte následující příkazy.

Nejdřív aplikaci vyčistěte a publikujte.

```dotnetcli
dotnet clean
dotnet publish
```

Pak přejděte do složky pro publikování konzolové aplikace a spusťte následující `spark-submit` příkaz. Nezapomeňte aktualizovat příkaz o skutečnou cestu k vašemu souboru Microsoft Spark jar.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Získání kódu

Tento kurz je podobný kódu z příkladu [Analýza mínění s velkými](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) objemy dat.

## <a name="next-steps"></a>Další kroky

V dalším článku se dozvíte, jak provádět strukturované streamování pomocí rozhraní .NET pro Apache Spark.
> [!div class="nextstepaction"]
> [Kurz: strukturované streamování s rozhraním .NET pro Apache Spark](streaming.md)
