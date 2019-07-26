---
title: Co je ML.NET a jak to funguje?
description: ML.NET poskytuje možnost Přidat strojové učení do aplikací .NET v online nebo offline scénáři. Díky této funkci můžete automaticky předpovědi používat data dostupná pro vaši aplikaci, aniž by bylo nutné je připojit k síti, aby používala ML.NET. Tento článek vysvětluje základy strojového učení v ML.NET.
ms.date: 07/17/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 23e71e86b75854042068b6a68f90cf995749ee58
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331578"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="70a33-105">Co je ML.NET a jak to funguje?</span><span class="sxs-lookup"><span data-stu-id="70a33-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="70a33-106">ML.NET poskytuje možnost Přidat strojové učení do aplikací .NET v online nebo offline scénáři.</span><span class="sxs-lookup"><span data-stu-id="70a33-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="70a33-107">Díky této funkci můžete automaticky předpovědi používat data dostupná pro vaši aplikaci, aniž by bylo nutné je připojit k síti.</span><span class="sxs-lookup"><span data-stu-id="70a33-107">With this capability, you can make automatic predictions using the data available to your application without having to be connected to a network.</span></span> <span data-ttu-id="70a33-108">Tento článek vysvětluje základy strojového učení v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="70a33-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="70a33-109">Příklady typů předpovědi, které můžete provést pomocí ML.NET, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="70a33-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="70a33-110">Klasifikace/kategorizace</span><span class="sxs-lookup"><span data-stu-id="70a33-110">Classification/Categorization</span></span>|<span data-ttu-id="70a33-111">Automatické rozdělení zpětné vazby od zákazníků do pozitivních a záporných kategorií</span><span class="sxs-lookup"><span data-stu-id="70a33-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="70a33-112">Regrese/předpověď souvislých hodnot</span><span class="sxs-lookup"><span data-stu-id="70a33-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="70a33-113">Předpověď ceny na pracoviště na základě velikosti a umístění</span><span class="sxs-lookup"><span data-stu-id="70a33-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="70a33-114">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="70a33-114">Anomaly Detection</span></span>|<span data-ttu-id="70a33-115">Rozpoznat podvodné bankovní transakce</span><span class="sxs-lookup"><span data-stu-id="70a33-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="70a33-116">Doporučení</span><span class="sxs-lookup"><span data-stu-id="70a33-116">Recommendations</span></span>|<span data-ttu-id="70a33-117">Návrhy produktů, které online nakupující může chtít koupit, na základě jejich předchozích nákupů</span><span class="sxs-lookup"><span data-stu-id="70a33-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="70a33-118">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="70a33-118">Hello ML.NET World</span></span>

<span data-ttu-id="70a33-119">Kód v následujícím fragmentu kódu demonstruje nejjednodušší aplikaci ML.NET.</span><span class="sxs-lookup"><span data-stu-id="70a33-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="70a33-120">V tomto příkladu se vytvoří model lineární regrese, který bude předpovídat ceny za domácnosti pomocí velikosti domu a dat o cenách.</span><span class="sxs-lookup"><span data-stu-id="70a33-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="70a33-121">Vaše data a model budou v aplikacích v reálném čase mnohem složitější.</span><span class="sxs-lookup"><span data-stu-id="70a33-121">In your real-life applications, your data and model will be much more complex.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="70a33-122">Pracovní postup kódu</span><span class="sxs-lookup"><span data-stu-id="70a33-122">Code workflow</span></span>

<span data-ttu-id="70a33-123">Následující diagram představuje strukturu kódu aplikace a také iterativní proces vývoje modelu:</span><span class="sxs-lookup"><span data-stu-id="70a33-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>
- <span data-ttu-id="70a33-124">Shromažďování a načítání školicích dat do objektu **IDataView**</span><span class="sxs-lookup"><span data-stu-id="70a33-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="70a33-125">Zadejte kanál operací pro extrakci funkcí a použití algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="70a33-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="70a33-126">Výuka modelu voláním **přizpůsobení ()** na kanálu</span><span class="sxs-lookup"><span data-stu-id="70a33-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="70a33-127">Vyhodnocení modelu a iterace pro zlepšení</span><span class="sxs-lookup"><span data-stu-id="70a33-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="70a33-128">Uložit model do binárního formátu pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="70a33-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="70a33-129">Načtení modelu zpátky do objektu **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="70a33-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="70a33-130">Vytvoření předpovědi voláním **CreatePredictionEngine. předpověď ()**</span><span class="sxs-lookup"><span data-stu-id="70a33-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET Flow pro vývoj aplikací, včetně komponent pro generování dat, vývoj kanálů, školení modelů, hodnocení modelů a využití modelu](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="70a33-132">Pojďme se do těchto konceptů dig trochu hlubší.</span><span class="sxs-lookup"><span data-stu-id="70a33-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="70a33-133">Model strojového učení</span><span class="sxs-lookup"><span data-stu-id="70a33-133">Machine learning model</span></span>

<span data-ttu-id="70a33-134">Model ML.NET je objekt, který obsahuje transformace, které se mají provést na vašich vstupních datech, aby bylo možné dorazit na předpokládaný výstup.</span><span class="sxs-lookup"><span data-stu-id="70a33-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="70a33-135">Základní</span><span class="sxs-lookup"><span data-stu-id="70a33-135">Basic</span></span>

<span data-ttu-id="70a33-136">Nejzákladnější model je dvourozměrná lineární regrese, kde jedno průběžné množství je úměrné jinému, jako v příkladu ceny za domu.</span><span class="sxs-lookup"><span data-stu-id="70a33-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Model lineární regrese s parametry bias a váhy](./media/linear-regression-model.svg)

<span data-ttu-id="70a33-138">Model je jednoduchý: $Price = b + velikost \* w $.</span><span class="sxs-lookup"><span data-stu-id="70a33-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="70a33-139">Parametry $b $ a $w $ jsou odhadované vytvořením řádku na základě množiny párů (Size, Price).</span><span class="sxs-lookup"><span data-stu-id="70a33-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="70a33-140">Data, která se používají k vyhledání parametrů modelu, se nazývají **školicí data**.</span><span class="sxs-lookup"><span data-stu-id="70a33-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="70a33-141">Vstupy modelu strojového učení se nazývají **funkce**.</span><span class="sxs-lookup"><span data-stu-id="70a33-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="70a33-142">V tomto příkladu je jedinou funkcí $Size $.</span><span class="sxs-lookup"><span data-stu-id="70a33-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="70a33-143">Hodnoty terénu používané k výuce modelu Machine Learning se nazývají **popisky**.</span><span class="sxs-lookup"><span data-stu-id="70a33-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="70a33-144">Tady jsou popisky. hodnoty $Price $ v sadě školicích dat.</span><span class="sxs-lookup"><span data-stu-id="70a33-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="70a33-145">Složitější</span><span class="sxs-lookup"><span data-stu-id="70a33-145">More complex</span></span>

<span data-ttu-id="70a33-146">Složitější model klasifikuje finanční transakce do kategorií pomocí popisu textu transakce.</span><span class="sxs-lookup"><span data-stu-id="70a33-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="70a33-147">Každý popis transakce je rozdělen do sady funkcí odebráním redundantních slov a znaků a spočítá kombinace slov a znaků.</span><span class="sxs-lookup"><span data-stu-id="70a33-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="70a33-148">Sada funkcí slouží ke výukě lineárního modelu na základě sady kategorií v školicích datech.</span><span class="sxs-lookup"><span data-stu-id="70a33-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="70a33-149">Podobně jako nový popis patří na ty, které jsou v sadě školení. pravděpodobnější je, že bude přiřazen ke stejné kategorii.</span><span class="sxs-lookup"><span data-stu-id="70a33-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Model klasifikace textu](./media/text-classification-model.svg)

<span data-ttu-id="70a33-151">Model cen domu i model klasifikace textu jsou **lineární** modely.</span><span class="sxs-lookup"><span data-stu-id="70a33-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="70a33-152">V závislosti na povaze vašich dat a problému, který řešíte, můžete také použít modely **rozhodovacích stromů** , **generalizované doplňkové** modely a další.</span><span class="sxs-lookup"><span data-stu-id="70a33-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="70a33-153">Další informace o modelech v úlohách najdete [](./resources/tasks.md)v části.</span><span class="sxs-lookup"><span data-stu-id="70a33-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="70a33-154">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="70a33-154">Data preparation</span></span>

<span data-ttu-id="70a33-155">Ve většině případů data, která máte k dispozici, nejsou vhodná pro použití přímo k výuce modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="70a33-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="70a33-156">Nezpracovaná data musí být připravena nebo předem zpracována před tím, než je možné ji použít k vyhledání parametrů modelu.</span><span class="sxs-lookup"><span data-stu-id="70a33-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="70a33-157">Vaše data možná budete muset převést z řetězcových hodnot na číselné znázornění.</span><span class="sxs-lookup"><span data-stu-id="70a33-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="70a33-158">Vstupní data mohou obsahovat redundantní informace.</span><span class="sxs-lookup"><span data-stu-id="70a33-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="70a33-159">Možná budete muset zmenšit nebo rozšířit rozměry vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="70a33-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="70a33-160">Vaše data možná budete muset normalizovat nebo škálovat.</span><span class="sxs-lookup"><span data-stu-id="70a33-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="70a33-161">[Výukové kurzy ml.NET](./tutorials/index.md) vás seznámí s různými kanály pro zpracování dat pro text, obrázky, numerické a časové řady, které se používají pro konkrétní úkoly strojového učení.</span><span class="sxs-lookup"><span data-stu-id="70a33-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="70a33-162">[Postup přípravy dat](./how-to-guides/prepare-data-ml-net.md) vám ukáže, jak se obecně aplikuje Příprava dat.</span><span class="sxs-lookup"><span data-stu-id="70a33-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="70a33-163">Přílohu všech [dostupných transformací](./resources/transforms.md) najdete v části Resources (prostředky).</span><span class="sxs-lookup"><span data-stu-id="70a33-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="70a33-164">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="70a33-164">Model evaluation</span></span>

<span data-ttu-id="70a33-165">Jakmile svůj model provedete, dozvíte se, jak dobře bude předpovědi budoucí?</span><span class="sxs-lookup"><span data-stu-id="70a33-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="70a33-166">Pomocí ML.NET můžete svůj model vyhodnotit před některými novými testovacími daty.</span><span class="sxs-lookup"><span data-stu-id="70a33-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="70a33-167">Každý typ úlohy strojového učení obsahuje metriky, které vyhodnocuje přesnost a přesnost modelu proti sadě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="70a33-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="70a33-168">Pro náš příklad ceny za dům jsme použili **regresní** úlohu.</span><span class="sxs-lookup"><span data-stu-id="70a33-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="70a33-169">Chcete-li tento model vyhodnotit, přidejte následující kód do původní ukázky.</span><span class="sxs-lookup"><span data-stu-id="70a33-169">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="70a33-170">Metriky vyhodnocení vám sdělí, že chyba je nízká-delšími a že korelace mezi předpokládaným výstupem a výstupem testu je vysoká.</span><span class="sxs-lookup"><span data-stu-id="70a33-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="70a33-171">To bylo snadné.</span><span class="sxs-lookup"><span data-stu-id="70a33-171">That was easy!</span></span> <span data-ttu-id="70a33-172">V reálných příkladech je větší optimalizace, aby se dosáhlo dobré metriky modelu.</span><span class="sxs-lookup"><span data-stu-id="70a33-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="70a33-173">Architektura ML.NET</span><span class="sxs-lookup"><span data-stu-id="70a33-173">ML.NET architecture</span></span>

<span data-ttu-id="70a33-174">V této části projdeme vzory architektury ML.NET.</span><span class="sxs-lookup"><span data-stu-id="70a33-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="70a33-175">Pokud jste zkušený vývojář .NET, budete znát některé z těchto vzorů a některé z nich budou méně známé.</span><span class="sxs-lookup"><span data-stu-id="70a33-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="70a33-176">Držte se těsně, zatímco jsme podrobněi.</span><span class="sxs-lookup"><span data-stu-id="70a33-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="70a33-177">Aplikace ml.NET začíná <xref:Microsoft.ML.MLContext> objektem.</span><span class="sxs-lookup"><span data-stu-id="70a33-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="70a33-178">Tento objekt typu Singleton obsahuje katalogy.</span><span class="sxs-lookup"><span data-stu-id="70a33-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="70a33-179">Katalog je továrna pro načítání dat a ukládání, transformaci, školitele a součásti operací s modelem.</span><span class="sxs-lookup"><span data-stu-id="70a33-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="70a33-180">Každý objekt katalogu obsahuje metody pro vytvoření různých typů komponent:</span><span class="sxs-lookup"><span data-stu-id="70a33-180">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="70a33-181">Načítání a ukládání dat</span><span class="sxs-lookup"><span data-stu-id="70a33-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="70a33-182">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="70a33-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="70a33-183">Školicí algoritmy</span><span class="sxs-lookup"><span data-stu-id="70a33-183">Training algorithms</span></span>|<span data-ttu-id="70a33-184">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="70a33-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="70a33-185">Klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="70a33-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="70a33-186">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="70a33-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="70a33-187">Clustering</span><span class="sxs-lookup"><span data-stu-id="70a33-187">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="70a33-188">Prognózování</span><span class="sxs-lookup"><span data-stu-id="70a33-188">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="70a33-189">Pořadí</span><span class="sxs-lookup"><span data-stu-id="70a33-189">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="70a33-190">Regrese</span><span class="sxs-lookup"><span data-stu-id="70a33-190">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="70a33-191">Doporučení</span><span class="sxs-lookup"><span data-stu-id="70a33-191">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="70a33-192">Přidat balíček `Microsoft.ML.Recommender` NuGet</span><span class="sxs-lookup"><span data-stu-id="70a33-192">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="70a33-193">Časové řady</span><span class="sxs-lookup"><span data-stu-id="70a33-193">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="70a33-194">Přidat balíček `Microsoft.ML.TimeSeries` NuGet</span><span class="sxs-lookup"><span data-stu-id="70a33-194">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="70a33-195">Využití modelu</span><span class="sxs-lookup"><span data-stu-id="70a33-195">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="70a33-196">Můžete přejít na metody vytváření v každé z výše uvedených kategorií.</span><span class="sxs-lookup"><span data-stu-id="70a33-196">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="70a33-197">Pomocí sady Visual Studio se katalogy zobrazují prostřednictvím technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="70a33-197">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![IntelliSense pro regresní školitele](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="70a33-199">Vytvoření kanálu</span><span class="sxs-lookup"><span data-stu-id="70a33-199">Build the pipeline</span></span>

<span data-ttu-id="70a33-200">Uvnitř každého katalogu je sada rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="70a33-200">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="70a33-201">Pojďme se podívat, jak metody rozšíření slouží k vytvoření školicího kanálu.</span><span class="sxs-lookup"><span data-stu-id="70a33-201">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="70a33-202">Ve fragmentu kódu `Concatenate` a `Sdca` jsou obě metody v katalogu.</span><span class="sxs-lookup"><span data-stu-id="70a33-202">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="70a33-203">Každý z nich vytvoří objekt [IEstimator](xref:Microsoft.ML.IEstimator%601) , který je připojen k kanálu.</span><span class="sxs-lookup"><span data-stu-id="70a33-203">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="70a33-204">V tomto okamžiku jsou objekty vytvořeny pouze.</span><span class="sxs-lookup"><span data-stu-id="70a33-204">At this point, the objects are created only.</span></span> <span data-ttu-id="70a33-205">Nedošlo k žádnému spuštění.</span><span class="sxs-lookup"><span data-stu-id="70a33-205">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="70a33-206">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="70a33-206">Train the model</span></span>

<span data-ttu-id="70a33-207">Jakmile se objekty v kanálu vytvoří, dají se data využít ke školení modelu.</span><span class="sxs-lookup"><span data-stu-id="70a33-207">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="70a33-208">Volání `Fit()` používá vstupní školicí data k odhadování parametrů modelu.</span><span class="sxs-lookup"><span data-stu-id="70a33-208">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="70a33-209">To se označuje jako školení modelu.</span><span class="sxs-lookup"><span data-stu-id="70a33-209">This is known as training the model.</span></span> <span data-ttu-id="70a33-210">Mějte na paměti, že výše uvedený model lineární regrese měl dva parametry modelu: **bias** a **váhy**.</span><span class="sxs-lookup"><span data-stu-id="70a33-210">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="70a33-211">`Fit()` Po volání jsou známy hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="70a33-211">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="70a33-212">Většina modelů bude mít mnoho dalších parametrů než toto.</span><span class="sxs-lookup"><span data-stu-id="70a33-212">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="70a33-213">Další informace o školení modelů najdete v tématu [postup](./how-to-guides/train-machine-learning-model-ml-net.md) při výuce modelu.</span><span class="sxs-lookup"><span data-stu-id="70a33-213">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="70a33-214">Výsledný objekt modelu implementuje <xref:Microsoft.ML.ITransformer> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70a33-214">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="70a33-215">To znamená, že model transformuje vstupní data do předpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a33-215">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="70a33-216">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="70a33-216">Use the model</span></span>

<span data-ttu-id="70a33-217">Vstupní data můžete transformovat do předpovědi hromadně nebo v jednom vstupním čase.</span><span class="sxs-lookup"><span data-stu-id="70a33-217">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="70a33-218">V příkladu ceny na pracovišti jsme obě: hromadně vyhodnotili model a v jednu chvíli udělali novou předpověď.</span><span class="sxs-lookup"><span data-stu-id="70a33-218">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="70a33-219">Pojďme se podívat, jak se na jeden předpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a33-219">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="70a33-220">`CreatePredictionEngine()` Metoda přebírá vstupní třídu a výstupní třídu.</span><span class="sxs-lookup"><span data-stu-id="70a33-220">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="70a33-221">Názvy polí nebo atributy kódu určují názvy datových sloupců použitých během školení modelů a předpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a33-221">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="70a33-222">Informace o tom, [Jak udělat jednu předpověď](./how-to-guides/single-predict-model-ml-net.md) , najdete v části postupy.</span><span class="sxs-lookup"><span data-stu-id="70a33-222">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="70a33-223">Datové modely a schéma</span><span class="sxs-lookup"><span data-stu-id="70a33-223">Data models and schema</span></span>

<span data-ttu-id="70a33-224">V jádru kanálu strojového učení ML.NET jsou objekty [DataView](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="70a33-224">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="70a33-225">Každá transformace v kanálu má vstupní schéma (názvy dat, typy a velikost, které transformace očekává, aby se na jejím vstupu zobrazila); a výstupní schéma (názvy dat, typy a velikosti, které transformace vytvoří po transformaci).</span><span class="sxs-lookup"><span data-stu-id="70a33-225">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> 

<span data-ttu-id="70a33-226">Pokud výstupní schéma z jedné transformace v kanálu neodpovídá vstupnímu schématu další transformace, ML.NET vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="70a33-226">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="70a33-227">Objekt zobrazení dat obsahuje sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="70a33-227">A data view object has columns and rows.</span></span> <span data-ttu-id="70a33-228">Každý sloupec má název a typ a délku.</span><span class="sxs-lookup"><span data-stu-id="70a33-228">Each column has a name and a type and a length.</span></span> <span data-ttu-id="70a33-229">Například: vstupní sloupce v příkladu ceny na pracovišti mají **Velikost** a **cenu**.</span><span class="sxs-lookup"><span data-stu-id="70a33-229">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="70a33-230">Jsou oba typy a jsou skalární množství namísto vektorů.</span><span class="sxs-lookup"><span data-stu-id="70a33-230">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Příklad zobrazení dat ML.NET s daty předpovědi ceny domu](./media/ml-net-dataview.png)

<span data-ttu-id="70a33-232">Všechny algoritmy ML.NET hledají vstupní sloupec, který je vektorem.</span><span class="sxs-lookup"><span data-stu-id="70a33-232">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="70a33-233">Ve výchozím nastavení se tento vektorový sloupec nazývá **funkce**.</span><span class="sxs-lookup"><span data-stu-id="70a33-233">By default this vector column is called **Features**.</span></span> <span data-ttu-id="70a33-234">Z tohoto důvodu jsme ve sloupci velikost zřetězi sloupec **Size** na nový sloupec s názvem **funkce** v našem příkladu ceny za dům.</span><span class="sxs-lookup"><span data-stu-id="70a33-234">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="70a33-235">Všechny algoritmy také vytvoří nové sloupce poté, co provedou předpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a33-235">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="70a33-236">Pevné názvy těchto nových sloupců závisí na typu algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="70a33-236">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="70a33-237">Pro úlohu regrese se jeden z nových sloupců nazývá **skóre**.</span><span class="sxs-lookup"><span data-stu-id="70a33-237">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="70a33-238">Proto jsme s tímto názvem pojmenoval naše cenové údaje.</span><span class="sxs-lookup"><span data-stu-id="70a33-238">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="70a33-239">Další informace o výstupních sloupcích různých úloh strojového učení najdete v průvodci [Machine Learning úkoly](resources/tasks.md) .</span><span class="sxs-lookup"><span data-stu-id="70a33-239">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="70a33-240">Důležitou vlastností objektů DataView je, že jsou vyhodnoceny jako **laxně vytvářená**.</span><span class="sxs-lookup"><span data-stu-id="70a33-240">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="70a33-241">Zobrazení dat jsou načítána a provozována pouze při výuce a vyhodnocování modelů a předpovědi dat.</span><span class="sxs-lookup"><span data-stu-id="70a33-241">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="70a33-242">Při psaní a testování aplikace ML.NET můžete použít ladicí program sady Visual Studio k prohlížení libovolného objektu zobrazení dat voláním metody [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) .</span><span class="sxs-lookup"><span data-stu-id="70a33-242">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="70a33-243">Můžete sledovat `debug` proměnnou v ladicím programu a prozkoumávat její obsah.</span><span class="sxs-lookup"><span data-stu-id="70a33-243">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="70a33-244">Nepoužívejte metodu Preview v produkčním kódu, protože významně snižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="70a33-244">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="70a33-245">Nasazení modelu</span><span class="sxs-lookup"><span data-stu-id="70a33-245">Model Deployment</span></span>

<span data-ttu-id="70a33-246">V aplikacích pracujících v reálném čase bude váš kód pro školení a vyhodnocení vašeho modelu oddělen od předpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a33-246">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="70a33-247">Ve skutečnosti tyto dvě aktivity často provádí samostatné týmy.</span><span class="sxs-lookup"><span data-stu-id="70a33-247">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="70a33-248">Vývojový tým modelu může uložit model pro použití v aplikaci předpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a33-248">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="70a33-249">Kde začít?</span><span class="sxs-lookup"><span data-stu-id="70a33-249">Where to now?</span></span>

<span data-ttu-id="70a33-250">Informace o tom, jak vytvářet aplikace s využitím různých úloh strojového učení s více realistickými [](./tutorials/index.md)datovými sadami, najdete v těchto kurzech.</span><span class="sxs-lookup"><span data-stu-id="70a33-250">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="70a33-251">Případně si můžete přečíst konkrétní témata podrobněji v tématu [návody.](./how-to-guides/index.md)</span><span class="sxs-lookup"><span data-stu-id="70a33-251">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="70a33-252">A pokud máte Super nás, můžete podrobně přímo do [Referenční dokumentace k rozhraní API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="70a33-252">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
