---
title: Co je ML.NET a jak to funguje?
description: ML.NET dává možnost Přidat strojového učení pro aplikace .NET. Díky této funkci můžete vytvářet automatické predikce data dostupná pro vaše aplikace. Tento článek vysvětluje základy strojového učení v ML.NET.
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 054fa0e1d9d8cc0d7c32efd4a9e8c81b91cb1335
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960425"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Co je ML.NET a jak to funguje?

ML.NET dává možnost Přidat strojového učení pro aplikace .NET. Díky této funkci můžete vytvářet automatické predikce data dostupná pro vaše aplikace. Tento článek vysvětluje základy strojového učení v ML.NET. 

Mezi příklady typu predikcí, které můžete použít s ML.NET patří:

|||
|-|-|
|Klasifikace a kategorizaci|Automaticky dělit zpětné vazby od zákazníků do kladnou a zápornou kategorií|
|Regrese/Predict průběžné hodnoty|Odhadnout cenu na základě velikosti a umístění Domů|
|Detekce anomálií|Zjištění podvodné bankovních transakcí |
|Doporučení|Navrhnout produktů, které si chcete koupit, může být vhodné nakupující online podle jejich předchozí nákupů|

## <a name="hello-mlnet-world"></a>Hello ML.NET World

Kódu následující fragment kódu ukazuje nejjednodušší ML.NET aplikaci. Tento příklad vytvoří model lineární regrese k předvídání cen house pomocí velikosti a ceny dat organizace. V reálné aplikace data a model bude mnohem složitější.

 ```csharp
    using System;
    using System.IO;
    using Microsoft.Data.DataView;
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

## <a name="code-workflow"></a>Kód pracovního postupu

Následující diagram představuje strukturu kódu aplikace a také iterativní proces vývoje modelu:
- Shromažďování a načíst trénovacích dat do **IDataView** objektu
- Zadat kanál operací pro extrakci funkce a použití algoritmu strojového učení
- Trénování modelu voláním **Fit()** ke kanálu
- Vyhodnocení modelu a iterovat ke zlepšení
- Uložit model do binárního formátu pro použití v aplikaci
- Načtení modelu zpět do **ITransformer** objektu
- Predikci voláním **CreatePredictionEngine.Predict()**

![Běh vývoj aplikace ML.NET včetně komponent pro generování dat, vývoj kanálu, model školení, vyhodnocení modelu a využití modelu](./media/mldotnet-annotated-workflow.png) 

Pojďme se podívat trochu hlouběji do těchto konceptů.

## <a name="machine-learning-model"></a>Model strojového učení

ML.NET model je objekt, který obsahuje transformace provádět na vstupní data můžete přejít na výstup předpokládaná.

### <a name="basic"></a>Základní

Základní model je dvojrozměrné lineární regrese, kde je úměrný do jiného, stejně jako v výše uvedený příklad ceny uložení jednoho průběžné množství. 

![Lineární regrese Model s parametry posun a váhy záznamu](./media/linear-regression-model.svg)

Model je jednoduše: $Price = b + velikost * w$. Posunout řádek na spektru jsou odhady parametry $b$ a $w$ (velikost, cena) dvojice. Data použitá k vyhledání parametrů model se nazývá **trénovacích dat**. Vstupy modelu strojového učení se nazývají **funkce**. V tomto příkladu je $Size$ pouze funkce. Hodnoty základu pravdy využívají k tréninku modelu strojového učení se nazývají **popisky**. Tady hodnoty $ $Price v trénovací datové sady jsou popisky.

### <a name="more-complex"></a>Složitější

Složitější modelu klasifikuje finanční transakce do kategorií pomocí textový popis transakce.

Popis každého transakce je rozdělena do sadu funkcí odebráním redundantní slova a znaků a počítání kombinace aplikace word a znaků. Sada funkcí se používá pro trénování modelu lineární na základě sady kategorií v trénovací data. Čím více podobně jako nový popis v cvičnou sadou, tím spíše se přiřadí do stejné kategorie. 

![Model klasifikace textu](./media/text-classification-model.svg)

Cenový model house i textový model klasifikace jsou **lineární** modely. V závislosti na povaze vašich dat a jsou řešení problému, můžete také použít **rozhodovací strom** modely, **zobecněný additive** modely a další. Můžete najít další informace o modelů v [úlohy](./resources/tasks.md).

## <a name="data-preparation"></a>Příprava dat

Ve většině případů se data, že máte k dispozici není vhodný pro použití přímo k natrénování modelu strojového učení. Nezpracovaná data musí být připravené nebo předem zpracovaných předtím, než je možné najít parametry modelu. Vaše data potřebovat pro převod z řetězcových hodnot na číselné vyjádření. Nadbytečné informace pravděpodobně ve vstupní data. Potřebujete omezit nebo rozšířit dimenze vstupní data. Normalizovaná nebo škálování může být potřeba data.

[ML.NET kurzy](./tutorials/index.md) naučit vás o kanálů jiné zpracování dat pro text, image, číselná a časových řad dat pro úlohy konkrétních strojového učení.

[Postup přípravy dat](./how-to-guides/prepare-data-ml-net.md) vám ukáže, jak na použita přípravu dat obecně.

Dodatek všech můžete najít [dostupných transformací](./resources/transforms.md) v části prostředky.

## <a name="model-evaluation"></a>Vyhodnocení modelu

Jakmile máte Trénink modelu, jak poznáte, jak dobře budou předpovědi budoucích? S ML.NET můžete si vyzkoušet model pro některé nové testovací data. 

Každý typ úlohy machine learning má metriky k vyhodnocení, přesnost a přesnost modelu proti testovací datové sady.

V našem příkladu cena house jsme použili **regrese** úloh. K vyhodnocení modelu, přidejte následující kód k původní ukázce.

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

Metrik hodnocení říct, že chyba je low-ish a této korelace mezi výstup předpokládaná a výstup testu je vysoká. To bylo snadné! V reálné příkladech trvá další ladění k dosažení dobré modelu metriky.

## <a name="mlnet-architecture"></a>Architektura ML.NET

V této části jsme projít architektury vzory ML.NET. Pokud jste vývojáři .NET, některé z těchto vzorců se se známými a některé budou méně známé. Podržte vysoké, můžeme začít!

Aplikace ML.NET začíná <xref:Microsoft.ML.MLContext> objektu. Tento objekt typu singleton obsahuje **katalogy**. Katalog je objekt pro vytváření dat, načítání a transformace, školitelé a součástí modelu operace ukládání. Každý objekt katalogu má metody k vytvoření různých typů komponent:

||||
|-|-|-|
|Ukládání a načítání dat||<xref:Microsoft.ML.DataOperationsCatalog>|
|Příprava dat||<xref:Microsoft.ML.TransformsCatalog>|
|Trénování algoritmů|Binární klasifikace|<xref:Microsoft.ML.BinaryClassificationCatalog>|
||Klasifikace víc tříd|<xref:Microsoft.ML.MulticlassClassificationCatalog>|
||Detekce anomálií|<xref:Microsoft.ML.AnomalyDetectionCatalog>|
||Hodnocení|<xref:Microsoft.ML.RankingCatalog>|
||Regrese|<xref:Microsoft.ML.RegressionCatalog>|
||Doporučení|<xref:Microsoft.ML.RecommendationCatalog>|
|Využití modelu ||<xref:Microsoft.ML.ModelOperationsCatalog>|

Můžete přejít do metod vytváření v každé z výše uvedených kategoriích. Pomocí sady Visual Studio, katalogy zobrazí prostřednictvím technologie IntelliSense.

   ![Technologie IntelliSense pro školitele regrese](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Vytvoření kanálu

V každé katalogu je sadu rozšiřujících metod. Podívejme se na použití rozšiřující metody k vytvoření kanálu školení.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

V tomto fragmentu kódu `Concatenate` a `Sdca` jsou obě metody v katalogu. Každá vytvořit [IEstimator](xref:Microsoft.ML.IEstimator%601) objekt, který se připojí k kanálu.

Objekty v tomto okamžiku se vytvoří pouze. Žádná spuštění se stalo.

### <a name="train-the-model"></a>Trénování modelu

Po vytvoření objektů v kanálu dat je možné pro trénování modelu.

```csharp
    var model = pipeline.Fit(trainingData);
```

Volání `Fit()` používá vstupní trénovacích dat k odhadu parametry modelu. To se označuje jako trénování modelu. Nezapomeňte, že výše uvedené trénování modelu lineární regrese má dva parametry modelu: **posun** a **váha**. Po `Fit()` volání, jsou známé hodnoty parametrů. Většina modely mají mnoho dalších parametrů, než to.

Další informace o tréninku modelu v [trénování modelu](./how-to-guides/train-machine-learning-model-ml-net.md)

Výsledný objekt modelu implementuje <xref:Microsoft.ML.ITransformer> rozhraní. To znamená, že model transformuje vstupní data do predikce.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Použití modelu

Najednou můžete transformovat vstupní data do predikce v hromadné nebo jeden vstup. V příkladu cena house jsme to udělali obojí: hromadné pro účely vyhodnocení modelu a jeden po druhém vytvoří předpověď nového. Podívejme se na provedení jednoho předpovědi.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = model.CreatePredictionEngine<HouseData, Prediction>(mlContext);
    var price = predEngine.Predict(size);
```
 
`CreatePredictionEngine()` Metoda přijímá vstupní třídy a výstupu. Názvy polí a/nebo atributy kódu určete názvy sloupců dat, použita během cvičení modelu a předpovědi. Informace o [jak jeden předpověď](./how-to-guides/single-predict-model-ml-net.md) v části s postupy.

### <a name="data-models-and-schema"></a>Datové modely a schématu

V jádru služby kanál ML.NET strojového učení se [DataView](xref:Microsoft.ML.IDataView) objekty.

Každá transformace v kanálu má vstupní schéma (názvy datových typů a velikostí, které transformací, která se očekává, že chcete zobrazit ve vzorci); a výstupní schéma (názvy datových typů a velikostí, mezi které transformací, která se vytváří po transformaci). 

Pokud schéma výstupu z jedna transformace v kanálu neodpovídá schématu vstupu další transformace, ML.NET vyvolá výjimku.

Objekt dat zobrazení obsahuje sloupce a řádky. Název a typ a délku má každý sloupec. Příklad: vstupní sloupce v příkladu cena house **velikost** a **cena**. Jsou obě zadání a že jsou skalární spíše než těch, které jsou vektorové.

   ![Příklad zobrazení dat ML.NET s daty predikce ceny house](./media/ml-net-dataview.png)

Všechny algoritmy ML.NET hledejte vstupní sloupec, který je vektor. Ve výchozím nastavení je volána v tomto sloupci vektoru **funkce**. To je důvod, proč jsme zřetězeny **velikost** názvem sloupce do nového sloupce **funkce** v našem příkladu house cena.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Po provedení predikcí, všechny algoritmy také vytvářet nové sloupce. Oprava názvy těchto nových sloupců závisí na typu algoritmu strojového učení. Pro úlohu regrese jedna nové sloupce se nazývá **skóre**. To je důvod, proč jsme s atributy naší cenové údaje s tímto názvem.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

Můžete najít další informace o výstupní sloupce úloh různých strojového učení v [Machine Learning úlohy](resources/tasks.md) průvodce.

Důležité vlastnost DataView objekty je, že jsou vyhodnocovány **laxně**. Zobrazení dat jsou pouze načíst a zpracovat. během cvičení modelu a vyhodnocení a data předpovědi. Při psaní a testování vaší aplikace ML.NET ladicího programu sady Visual Studio můžete provést náhled na libovolný objekt dat zobrazení pomocí volání [ve verzi Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) metody.

```csharp
    var debug = testPriceDataView.Preview();
```

Můžete se podívat `debug` proměnné v ladicím programu a prozkoumat její obsah. Nepoužívejte metodu ve verzi Preview v produkčním kódu, protože výrazně snižuje výkon.

### <a name="model-deployment"></a>Nasazení modelu

V reálné aplikace bude váš kód trénování a vyhodnocování modelu nezávisle na predikci. Ve skutečnosti, že obě aktivity často provádějí mají samostatné týmy. Váš vývojový tým modelu můžete uložit model pro použití v aplikaci předpovědi.

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a>Kam chcete nyní?

Zjistěte, jak vytvářet aplikace pomocí úlohy různých strojového učení s víc odpovídají realitě datovými sadami v [kurzy](./tutorials/index.md).

Nebo můžete informace o konkrétních tématech v části [příručky a návody](./how-to-guides/index.md).

A pokud je pro vás velmi webu, můžete rovnou přímo do [dokumentaci Reference k rozhraní API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!
