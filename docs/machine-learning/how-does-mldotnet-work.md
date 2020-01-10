---
title: Co je ML.NET a jak to funguje?
description: ML.NET poskytuje možnost Přidat strojové učení do aplikací .NET v online nebo offline scénáři. Díky této funkci můžete automaticky předpovědi používat data dostupná pro vaši aplikaci, aniž by bylo nutné je připojit k síti, aby používala ML.NET. Tento článek vysvětluje základy strojového učení v ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 98251c39a4bdaba8203c26c6a781a86efc46efa4
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740092"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Co je ML.NET a jak to funguje?

ML.NET poskytuje možnost Přidat strojové učení do aplikací .NET v online nebo offline scénáři. Díky této funkci můžete automaticky předpovědi používat data dostupná pro vaši aplikaci.

Central to ML.NET je **model**strojového učení. Model určuje kroky potřebné k transformaci vstupních dat do předpovědi. Pomocí ML.NET můžete vytvořit vlastní model zadáním algoritmu, nebo můžete importovat předem připravené modely TensorFlow a ONNX.

Jakmile máte model, můžete ho přidat do aplikace, aby se předpovědi.

ML.NET běží na Windows, Linux a macOS pomocí .NET Core nebo Windows pomocí .NET Framework. bit 64 se podporuje na všech platformách. ve Windows se podporuje bit 32 s výjimkou funkcí TensorFlow, LightGBM a ONNX.

Příklady typů předpovědi, které můžete vytvořit pomocí ML.NET:

|||
|-|-|
|Klasifikace/kategorizace|Automatické rozdělení zpětné vazby od zákazníků do pozitivních a záporných kategorií|
|Regrese/předpověď souvislých hodnot|Předpověď ceny na pracoviště na základě velikosti a umístění|
|Detekce anomálií|Rozpoznat podvodné bankovní transakce |
|Doporučení|Návrhy produktů, které online nakupující může chtít koupit, na základě jejich předchozích nákupů|
|Časová řada/sekvenční data|Předpověď počasí nebo prodeje produktů|
|Klasifikace obrázků|Kategorizace pathologies v lékařských imagích|

## <a name="hello-mlnet-world"></a>Hello ML.NET World

Kód v následujícím fragmentu kódu demonstruje nejjednodušší aplikaci ML.NET. V tomto příkladu se vytvoří model lineární regrese, který bude předpovídat ceny za domácnosti pomocí velikosti domu a dat o cenách. 

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a>Pracovní postup kódu

Následující diagram představuje strukturu kódu aplikace a také iterativní proces vývoje modelu:

- Shromažďování a načítání školicích dat do objektu **IDataView**
- Zadejte kanál operací pro extrakci funkcí a použití algoritmu strojového učení.
- Výuka modelu voláním **přizpůsobení ()** na kanálu
- Vyhodnocení modelu a iterace pro zlepšení
- Uložit model do binárního formátu pro použití v aplikaci
- Načtení modelu zpátky do objektu **ITransformer**
- Vytvoření předpovědi voláním **CreatePredictionEngine. předpověď ()**

![ML.NET Flow pro vývoj aplikací, včetně komponent pro generování dat, vývoj kanálů, školení modelů, hodnocení modelů a využití modelu](./media/mldotnet-annotated-workflow.png)

Pojďme se do těchto konceptů dig trochu hlubší.

## <a name="machine-learning-model"></a>Model strojového učení

Model ML.NET je objekt, který obsahuje transformace, které se mají provést na vašich vstupních datech, aby bylo možné dorazit na předpokládaný výstup.

### <a name="basic"></a>Základní

Nejzákladnější model je dvourozměrná lineární regrese, kde jedno průběžné množství je úměrné jinému, jako v příkladu ceny za domu.

![Model lineární regrese s parametry bias a váhy](./media/linear-regression-model.svg)

Model je jednoduchý: $Price = b + velikost * w $. Parametry $b $ a $w $ jsou odhadované vytvořením řádku na základě množiny párů (Size, Price). Data, která se používají k vyhledání parametrů modelu, se nazývají **školicí data**. Vstupy modelu strojového učení se nazývají **funkce**. V tomto příkladu je jedinou funkcí $Size $. Hodnoty terénu používané k výuce modelu Machine Learning se nazývají **popisky**. Tady jsou popisky. hodnoty $Price $ v sadě školicích dat.

### <a name="more-complex"></a>Složitější

Složitější model klasifikuje finanční transakce do kategorií pomocí popisu textu transakce.

Každý popis transakce je rozdělen do sady funkcí odebráním redundantních slov a znaků a spočítá kombinace slov a znaků. Sada funkcí slouží ke výukě lineárního modelu na základě sady kategorií v školicích datech. Podobně jako nový popis patří na ty, které jsou v sadě školení. pravděpodobnější je, že bude přiřazen ke stejné kategorii.

![Model klasifikace textu](./media/text-classification-model.svg)

Model cen domu i model klasifikace textu jsou **lineární** modely. V závislosti na povaze vašich dat a problému, který řešíte, můžete také použít modely **rozhodovacích stromů** , **generalizované doplňkové** modely a další. Další informace o modelech v [úlohách](./resources/tasks.md)najdete v části.

## <a name="data-preparation"></a>Příprava dat

Ve většině případů data, která máte k dispozici, nejsou vhodná pro použití přímo k výuce modelu Machine Learning. Nezpracovaná data musí být připravena nebo předem zpracována před tím, než je možné ji použít k vyhledání parametrů modelu. Vaše data možná budete muset převést z řetězcových hodnot na číselné znázornění. Vstupní data mohou obsahovat redundantní informace. Možná budete muset zmenšit nebo rozšířit rozměry vstupních dat. Vaše data možná budete muset normalizovat nebo škálovat.

[Výukové kurzy ml.NET](./tutorials/index.md) vás seznámí s různými kanály pro zpracování dat pro text, obrázky, numerické a časové řady, které se používají pro konkrétní úkoly strojového učení.

[Postup přípravy dat](./how-to-guides/prepare-data-ml-net.md) vám ukáže, jak se obecně aplikuje Příprava dat.

Přílohu všech [dostupných transformací](./resources/transforms.md) najdete v části Resources (prostředky).

## <a name="model-evaluation"></a>Vyhodnocení modelu

Jakmile svůj model provedete, dozvíte se, jak dobře bude předpovědi budoucí? Pomocí ML.NET můžete svůj model vyhodnotit před některými novými testovacími daty.

Každý typ úlohy strojového učení obsahuje metriky, které vyhodnocuje přesnost a přesnost modelu proti sadě testovacích dat.

Pro náš příklad ceny za dům jsme použili **regresní** úlohu. Chcete-li tento model vyhodnotit, přidejte následující kód do původní ukázky.

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

Metriky vyhodnocení vám sdělí, že chyba je nízká-delšími a že korelace mezi předpokládaným výstupem a výstupem testu je vysoká. To bylo snadné. V reálných příkladech je větší optimalizace, aby se dosáhlo dobré metriky modelu.

## <a name="mlnet-architecture"></a>Architektura ML.NET

V této části projdeme vzory architektury ML.NET. Pokud jste zkušený vývojář .NET, budete znát některé z těchto vzorů a některé z nich budou méně známé. Držte se těsně, zatímco jsme podrobněi.

Aplikace ML.NET začíná objektem <xref:Microsoft.ML.MLContext>. Tento objekt typu Singleton obsahuje **katalogy**. Katalog je továrna pro načítání dat a ukládání, transformaci, školitele a součásti operací s modelem. Každý objekt katalogu obsahuje metody pro vytvoření různých typů komponent:

|||||
|-|-|-|-|
|Načítání a ukládání dat||<xref:Microsoft.ML.DataOperationsCatalog>||
|Příprava dat||<xref:Microsoft.ML.TransformsCatalog>||
|Školicí algoritmy|Binární klasifikace|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Klasifikace s více třídami|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Detekce anomálií|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Clustering|<xref:Microsoft.ML.ClusteringCatalog>||
||Prognózování|<xref:Microsoft.ML.ForecastingCatalog>||
||Nejlepší hodnocení|<xref:Microsoft.ML.RankingCatalog>||
||Regrese|<xref:Microsoft.ML.RegressionCatalog>||
||Doporučení|<xref:Microsoft.ML.RecommendationCatalog>|Přidat `Microsoft.ML.Recommender` balíček NuGet|
||Časové řady|<xref:Microsoft.ML.TimeSeriesCatalog>|Přidat `Microsoft.ML.TimeSeries` balíček NuGet|
|Využití modelu ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Můžete přejít na metody vytváření v každé z výše uvedených kategorií. Pomocí sady Visual Studio se katalogy zobrazují prostřednictvím technologie IntelliSense.

   ![IntelliSense pro regresní školitele](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Vytvoření kanálu

Uvnitř každého katalogu je sada rozšiřujících metod. Pojďme se podívat, jak metody rozšíření slouží k vytvoření školicího kanálu.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Ve fragmentu kódu `Concatenate` a `Sdca` obě metody v katalogu. Každý z nich vytvoří objekt [IEstimator](xref:Microsoft.ML.IEstimator%601) , který je připojen k kanálu.

V tomto okamžiku jsou objekty vytvořeny pouze. Nedošlo k žádnému spuštění.

### <a name="train-the-model"></a>Trénování modelu

Jakmile se objekty v kanálu vytvoří, dají se data využít ke školení modelu.

```csharp
    var model = pipeline.Fit(trainingData);
```

Volání `Fit()` používá vstupní školicí data k odhadování parametrů modelu. To se označuje jako školení modelu. Mějte na paměti, že výše uvedený model lineární regrese měl dva parametry modelu: **bias** a **váhy**. Po volání `Fit()` jsou známy hodnoty parametrů. Většina modelů bude mít mnoho dalších parametrů než toto.

Další informace o školení modelů najdete v tématu [postup](./how-to-guides/train-machine-learning-model-ml-net.md)při výuce modelu.

Výsledný objekt modelu implementuje rozhraní <xref:Microsoft.ML.ITransformer>. To znamená, že model transformuje vstupní data do předpovědi.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Použití modelu

Vstupní data můžete transformovat do předpovědi hromadně nebo v jednom vstupním čase. V příkladu ceny na pracovišti jsme obě: hromadně vyhodnotili model a v jednu chvíli udělali novou předpověď. Pojďme se podívat, jak se na jeden předpovědi.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

Metoda `CreatePredictionEngine()` přebírá vstupní třídu a třídu Output. Názvy polí nebo atributy kódu určují názvy datových sloupců použitých během školení modelů a předpovědi. Informace o tom, [Jak udělat jednu předpověď](./how-to-guides/single-predict-model-ml-net.md) , najdete v části postupy.

### <a name="data-models-and-schema"></a>Datové modely a schéma

V jádru kanálu strojového učení ML.NET jsou objekty [DataView](xref:Microsoft.ML.IDataView) .

Každá transformace v kanálu má vstupní schéma (názvy dat, typy a velikost, které transformace očekává, aby se na jejím vstupu zobrazila); a výstupní schéma (názvy dat, typy a velikosti, které transformace vytvoří po transformaci). Následující dokument poskytuje podrobné vysvětlení [rozhraní IDataView a jeho typu systému](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).

Pokud výstupní schéma z jedné transformace v kanálu neodpovídá vstupnímu schématu další transformace, ML.NET vyvolá výjimku.

Objekt zobrazení dat obsahuje sloupce a řádky. Každý sloupec má název a typ a délku. Například vstupní sloupce v ceně za domu jsou **Velikost** a **Cena**. Jsou oba typy a jsou skalární množství namísto vektorů.

   ![Příklad zobrazení dat ML.NET s daty předpovědi ceny domu](./media/ml-net-dataview.png)

Všechny algoritmy ML.NET hledají vstupní sloupec, který je vektorem. Ve výchozím nastavení se tento vektorový sloupec nazývá **funkce**. Z tohoto důvodu jsme ve sloupci velikost zřetězi sloupec **Size** na nový sloupec s názvem **funkce** v našem příkladu ceny za dům.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Všechny algoritmy také vytvoří nové sloupce poté, co provedou předpovědi. Pevné názvy těchto nových sloupců závisí na typu algoritmu strojového učení. Pro úlohu regrese se jeden z nových sloupců nazývá **skóre**. Proto jsme s tímto názvem pojmenoval naše cenové údaje.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

Další informace o výstupních sloupcích různých úloh strojového učení najdete v průvodci [Machine Learning úkoly](resources/tasks.md) .

Důležitou vlastností objektů DataView je, že jsou vyhodnoceny jako **laxně vytvářená**. Zobrazení dat jsou načítána a provozována pouze při výuce a vyhodnocování modelů a předpovědi dat. Při psaní a testování aplikace ML.NET můžete použít ladicí program sady Visual Studio k prohlížení libovolného objektu zobrazení dat voláním metody [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) .

```csharp
    var debug = testPriceDataView.Preview();
```

Můžete sledovat `debug` proměnnou v ladicím programu a prozkoumávat její obsah. Nepoužívejte metodu Preview v produkčním kódu, protože významně snižuje výkon.

### <a name="model-deployment"></a>Nasazení modelu

V aplikacích pracujících v reálném čase bude váš kód pro školení a vyhodnocení vašeho modelu oddělen od předpovědi. Ve skutečnosti tyto dvě aktivity často provádí samostatné týmy. Vývojový tým modelu může uložit model pro použití v aplikaci předpovědi.

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a>Další kroky

* Naučte se sestavovat aplikace pomocí různých úloh strojového učení s více realistickými datovými sadami v [kurzech](./tutorials/index.md).

* Další informace o konkrétních tématech podrobněji [najdete v tématu návody.](./how-to-guides/index.md)

* Pokud jste nás, můžete podrobně přímo do [Referenční dokumentace k rozhraní API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).
