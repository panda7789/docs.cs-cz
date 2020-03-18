---
title: Co je ML.NET a jak funguje?
description: ML.NET vám dává možnost přidat strojové učení do aplikací .NET, a to buď v režimech online nebo offline. Pomocí této funkce můžete automaticky předpovídat pomocí dat k dispozici pro vaši aplikaci, aniž by bylo třeba připojení k síti používat ML.NET. Tento článek vysvětluje základy strojového učení v ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 169250adf81992ad0025e78eb9c8f151107bcf40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185854"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Co je ML.NET a jak funguje?

ML.NET vám dává možnost přidat strojové učení do aplikací .NET, a to buď v režimech online nebo offline. Pomocí této funkce můžete provádět automatické předpovědi pomocí dat, která jsou k dispozici pro vaši aplikaci. Aplikace strojového učení využívají vzory v datech k předpovědi, spíše než je třeba explicitně naprogramovat.

Ústředním bodem ML.NET je **model**strojového učení . Model určuje kroky potřebné k transformaci vstupních dat do předpověď. Pomocí ML.NET můžete trénovat vlastní model zadáním algoritmu nebo můžete importovat předem vycvičené modely TensorFlow a ONNX.

Jakmile máte model, můžete jej přidat do aplikace, aby předpovědi.

ML.NET běží na Windows, Linux a macOS pomocí .NET Core nebo Windows pomocí rozhraní .NET Framework. 64 bitů je podporováno na všech platformách. 32 bitje podporována v systému Windows, s výjimkou funkce související s TensorFlow, LightGBM a ONNX.

Příklady typu předpovědi, které můžete provést s ML.NET:

|||
|-|-|
|Klasifikace/kategorizace|Automatické rozdělení zpětné vazby od zákazníků do pozitivních a záporných kategorií|
|Regresní/prediktivní spojité hodnoty|Předpovědět cenu domů na základě velikosti a umístění|
|Detekce anomálií|Detekce podvodných bankovních transakcí |
|Doporučení|Navrhněte produkty, které mohou online zákazníci chtít koupit na základě svých předchozích nákupů|
|Časová řada/sekvenční data|Předpověď prodeje počasí/produktu|
|Klasifikace obrázků|Kategorizovat patologie v lékařských obrazech|

## <a name="hello-mlnet-world"></a>Dobrý den, ML.NET Svět

Kód v následujícím fragmentu ukazuje nejjednodušší ML.NET aplikace. Tento příklad vytváří lineární regresní model pro předpovídání cen domů pomocí údajů o velikosti domu a cenách.

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

Následující diagram představuje strukturu kódu aplikace, stejně jako iterativní proces vývoje modelu:

- Shromažďování a načítání trénovacích dat do objektu **IDataView**
- Určení kanálu operací pro extrahování prvků a použití algoritmu strojového učení
- Trénování modelu voláním **Fit()** na potrubí
- Vyhodnoťte model a iterátte, abyste zlepšili
- Uložení modelu do binárního formátu pro použití v aplikaci
- Načtení modelu zpět do objektu **ITransformer**
- Provést předpovědi voláním **CreatePredictionEngine.Predict()**

![ML.NET tok vývoje aplikací včetně komponent pro generování dat, vývoj potrubí, trénování modelů, vyhodnocení modelu a využití modelu](./media/mldotnet-annotated-workflow.png)

Pojďme se hlouběji ponořit do těchto pojmů.

## <a name="machine-learning-model"></a>Model strojového učení

Model ML.NET je objekt, který obsahuje transformace k provedení na vstupní data k dosažení předpokládaného výstupu.

### <a name="basic"></a>Basic

Nejzákladnějším modelem je dvourozměrná lineární regrese, kde jedno souvislé množství je úměrné jinému, jako ve výše uvedeném příkladu ceny domu.

![Lineární regresní model s parametry zkreslení a hmotnosti](./media/linear-regression-model.svg)

Model je jednoduše: $Price = b + Velikost * w$. Parametry $b$ a $w$ se odhadují montáží řádku na sadu (velikost, cena) párů. Data použitá k nalezení parametrů modelu se nazývají **trénovací data**. Vstupy modelu strojového učení se nazývají **funkce**. V tomto příkladu je pouze funkce $Size$. Hodnoty základní pravdy používané k trénování modelu strojového učení se nazývají **popisky**. Zde jsou hodnoty $Price$ v sadě trénovacích dat popisky.

### <a name="more-complex"></a>Složitější

Složitější model klasifikuje finanční transakce do kategorií pomocí textového popisu transakce.

Každý popis transakce je rozdělen do sady funkcí odebráním nadbytečných slov a znaků a počítáním kombinací slov a znaků. Sada funkcí se používá k trénování lineárního modelu na základě sady kategorií v trénovacích datech. Čím více podobný je nový popis těm v tréninkové sadě, tím je pravděpodobnější, že bude přiřazen do stejné kategorie.

![Model klasifikace textu](./media/text-classification-model.svg)

Cenový model domu i model klasifikace textu jsou **lineární** modely. V závislosti na povaze dat a problému, který řešíte, můžete také použít modely **rozhodovacích stromů,** **generalizované aditivní** modely a další. Další informace o modelech naleznete v [části Úkoly](./resources/tasks.md).

## <a name="data-preparation"></a>Příprava dat

Ve většině případů data, která máte k dispozici, není vhodná pro použití přímo k trénování modelu strojového učení. Nezpracovaná data musí být připravena nebo předem zpracována, než je lze použít k nalezení parametrů modelu. Data může být nutné převést z řetězcových hodnot na číselnou reprezentaci. Ve vstupních datech mohou být nadbytečné informace. Možná budete muset zmenšit nebo rozšířit rozměry vstupních dat. Vaše data může být nutné normalizovat nebo škálovat.

V [ML.NET kurzy](./tutorials/index.md) vás naučí o různých kanálech pro zpracování dat pro text, obrázek, numerické a časové řady dat používaných pro konkrétní úlohy strojového učení.

[Jak připravit data,](./how-to-guides/prepare-data-ml-net.md) ukazuje, jak aplikovat přípravu dat obecněji.

Dodatek všech [dostupných transformací](./resources/transforms.md) najdete v části zdroje.

## <a name="model-evaluation"></a>Vyhodnocení modelu

Poté, co jste trénoval svůj model, jak víte, jak dobře to bude dělat budoucí předpovědi? S ML.NET můžete vyhodnotit model proti některé nové testovací data.

Každý typ úlohy strojového učení má metriky používané k vyhodnocení přesnosti a přesnosti modelu oproti sadě testovacích dat.

Pro náš příklad ceny domu jsme použili úkol **regrese.** Chcete-li model vyhodnotit, přidejte do původní ukázky následující kód.

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

Metriky hodnocení vám říct, že chyba je low-ish a že korelace mezi předpokládaný výstup a testovací výstup je vysoká. To bylo snadné! V reálných příkladech je zapotřebí více ladění k dosažení dobrých metrik modelu.

## <a name="mlnet-architecture"></a>ML.NET architektura

V této části procházíme architektonickými vzory ML.NET. Pokud jste zkušený vývojář rozhraní .NET, některé z těchto vzorů vám budou známé a některé budou méně známé. Držte se pevně, zatímco se ponoříme!

Aplikace ML.NET začíná <xref:Microsoft.ML.MLContext> objektem. Tento objekt singleton obsahuje **katalogy**. Katalog je továrna pro načítání a ukládání dat, transformace, školicí prvky a součásti operací modelu. Každý objekt katalogu má metody k vytvoření různých typů součástí:

|||||
|-|-|-|-|
|Načítání a ukládání dat||<xref:Microsoft.ML.DataOperationsCatalog>||
|Příprava dat||<xref:Microsoft.ML.TransformsCatalog>||
|Tréninkové algoritmy|Binární klasifikace|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Klasifikace více tříd|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Detekce anomálií|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Clustering|<xref:Microsoft.ML.ClusteringCatalog>||
||Prognózování|<xref:Microsoft.ML.ForecastingCatalog>||
||Pořadí|<xref:Microsoft.ML.RankingCatalog>||
||Regrese|<xref:Microsoft.ML.RegressionCatalog>||
||Doporučení|<xref:Microsoft.ML.RecommendationCatalog>|přidání `Microsoft.ML.Recommender` balíčku NuGet|
||Časová řada|<xref:Microsoft.ML.TimeSeriesCatalog>|přidání `Microsoft.ML.TimeSeries` balíčku NuGet|
|Použití modelu ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Můžete přejít na metody vytváření v každé z výše uvedených kategorií. Pomocí sady Visual Studio se katalogy zobrazují prostřednictvím technologie IntelliSense.

   ![Intellisense pro regresní školitelů](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Sestavení kanálu

Uvnitř každého katalogu je sada metod rozšíření. Podívejme se na způsob rozšíření metody se používají k vytvoření kanálu školení.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Ve fragmentu a `Concatenate` `Sdca` jsou obě metody v katalogu. Každý z nich vytvořit [objekt IEstimator,](xref:Microsoft.ML.IEstimator%601) který je připojen k kanálu.

V tomto okamžiku jsou objekty vytvořeny pouze. K žádné popravě nedošlo.

### <a name="train-the-model"></a>Trénování modelu

Po vytvoření objektů v kanálu data lze použít k trénování modelu.

```csharp
    var model = pipeline.Fit(trainingData);
```

Volání `Fit()` používá vstupní trénovací data k odhadu parametrů modelu. To se označuje jako trénování modelu. Nezapomeňte, že výše uvedený lineární regresní model měl dva parametry modelu: **zkreslení** a **hmotnost**. Po `Fit()` volání jsou známy hodnoty parametrů. Většina modelů bude mít mnohem více parametrů než toto.

Další informace o trénování modelu najdete v [aplikaci Jak trénovat model](./how-to-guides/train-machine-learning-model-ml-net.md).

Výsledný objekt modelu implementuje <xref:Microsoft.ML.ITransformer> rozhraní. To znamená, že model transformuje vstupní data do předpovědi.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Použití modelu

Vstupní data můžete transformovat do předpovědi hromadně nebo jeden vstup najednou. V příkladu ceny domu jsme udělali obojí: hromadně za účelem vyhodnocení modelu a jeden po druhém, abychom vytvořili novou předpověď. Podívejme se na vytváření jednotlivých předpovědí.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

Metoda `CreatePredictionEngine()` trvá vstupní třídy a výstupní třídy. Názvy polí nebo atributy kódu určují názvy datových sloupců použitých během trénování a predikce modelu. Můžete si přečíst o [Jak provést jednu předpověď](./how-to-guides/single-predict-model-ml-net.md) v části Návody.

### <a name="data-models-and-schema"></a>Datové modely a schémata

Jádrem kanálu ML.NET strojového učení jsou objekty [DataView.](xref:Microsoft.ML.IDataView)

Každá transformace v kanálu má vstupní schéma (názvy dat, typy a velikosti, které transformace očekává, že vidět na jeho vstupu); a výstupní schéma (názvy dat, typy a velikosti, které transformace vytvoří po transformaci). Následující dokument obsahuje podrobné vysvětlení [rozhraní IDataView a jeho typového systému](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).

Pokud výstupní schéma z jedné transformace v kanálu neodpovídá vstupníschéma další transformace, ML.NET vyvolá výjimku.

Objekt zobrazení dat má sloupce a řádky. Každý sloupec má název a typ a délku. Například vstupní sloupce v příkladu ceny domu jsou **Velikost** a **cena**. Oba jsou typ a jsou skalární množství spíše než vektorové.

   ![ML.NET příklad zobrazení dat s údaji o předpovědi cen domů](./media/ml-net-dataview.png)

Všechny ML.NET algoritmy hledají vstupní sloupec, který je vektor. Ve výchozím nastavení se tento vektorový sloupec nazývá **Funkce**. To je důvod, proč jsme zřetězili sloupec **Velikost** do nového sloupce s názvem **Funkce** v našem příkladu ceny domu.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Všechny algoritmy také vytvořit nové sloupce po provedení předpověď. Pevné názvy těchto nových sloupců závisí na typu algoritmu strojového učení. Pro regresní úlohu se jeden z nových sloupců nazývá **Skóre**. To je důvod, proč jsme připisovali naše cenové údaje s tímto názvem.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

Další informace o výstupních sloupcích různých úloh strojového učení najdete v příručce [Úlohy strojového učení.](resources/tasks.md)

Důležitou vlastností objektů DataView je, že jsou vyhodnocovány **líně**. Zobrazení dat jsou načteny a provozovány pouze během trénování a vyhodnocení modelu a predikce dat. Při psaní a testování ML.NET aplikace, můžete použít ladicí program Sady Visual Studio nahlédnout na libovolný objekt zobrazení dat voláním [metody Náhled.](xref:Microsoft.ML.DebuggerExtensions.Preview*)

```csharp
    var debug = testPriceDataView.Preview();
```

Můžete sledovat `debug` proměnnou v ladicím programu a zkoumat její obsah. Nepoužívejte metodu Náhled v produkčním kódu, protože výrazně snižuje výkon.

### <a name="model-deployment"></a>Nasazení modelu

V reálných aplikacích bude váš model školení a hodnocení kód bude oddělena od predikce. Ve skutečnosti jsou tyto dvě činnosti často prováděny samostatnými týmy. Váš tým pro vývoj modelu můžete uložit model pro použití v aplikaci předpověď.

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a>Další kroky

* Naučte se vytvářet aplikace pomocí různých úloh strojového učení s realističtějšími sadami dat v [kurzech](./tutorials/index.md).

* Další informace o konkrétních tématech podrobněji naleznete v příručce [How To Guides](./how-to-guides/index.md).

* Pokud jste super zájem, můžete se ponořit přímo do [referenční dokumentace API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).
