---
title: Co je ML.NET a jak funguje?
description: ML.NET vám dává možnost přidat strojové učení do aplikací .NET, a to buď v režimech online nebo offline. Pomocí této funkce můžete automaticky předpovídat pomocí dat k dispozici pro vaši aplikaci, aniž by bylo třeba připojení k síti používat ML.NET. Tento článek vysvětluje základy strojového učení v ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 0929005e02ad9b43636213735f8c7232aa6d4f42
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607768"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="7ec86-105">Co je ML.NET a jak funguje?</span><span class="sxs-lookup"><span data-stu-id="7ec86-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="7ec86-106">ML.NET vám dává možnost přidat strojové učení do aplikací .NET, a to buď v režimech online nebo offline.</span><span class="sxs-lookup"><span data-stu-id="7ec86-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="7ec86-107">Pomocí této funkce můžete provádět automatické předpovědi pomocí dat, která jsou k dispozici pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7ec86-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="7ec86-108">Aplikace strojového učení využívají vzory v datech k předpovědi, spíše než je třeba explicitně naprogramovat.</span><span class="sxs-lookup"><span data-stu-id="7ec86-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="7ec86-109">Ústředním bodem ML.NET je **model**strojového učení .</span><span class="sxs-lookup"><span data-stu-id="7ec86-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="7ec86-110">Model určuje kroky potřebné k transformaci vstupních dat do předpověď.</span><span class="sxs-lookup"><span data-stu-id="7ec86-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="7ec86-111">Pomocí ML.NET můžete trénovat vlastní model zadáním algoritmu nebo můžete importovat předem vycvičené modely TensorFlow a ONNX.</span><span class="sxs-lookup"><span data-stu-id="7ec86-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="7ec86-112">Jakmile máte model, můžete jej přidat do aplikace, aby předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7ec86-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="7ec86-113">ML.NET běží na Windows, Linux a macOS pomocí .NET Core nebo Windows pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ec86-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="7ec86-114">64 bitů je podporováno na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="7ec86-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="7ec86-115">32 bitje podporována v systému Windows, s výjimkou funkce související s TensorFlow, LightGBM a ONNX.</span><span class="sxs-lookup"><span data-stu-id="7ec86-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="7ec86-116">Příklady typu předpovědi, které můžete provést s ML.NET:</span><span class="sxs-lookup"><span data-stu-id="7ec86-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="7ec86-117">Klasifikace/kategorizace</span><span class="sxs-lookup"><span data-stu-id="7ec86-117">Classification/Categorization</span></span>|<span data-ttu-id="7ec86-118">Automatické rozdělení zpětné vazby od zákazníků do pozitivních a záporných kategorií</span><span class="sxs-lookup"><span data-stu-id="7ec86-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="7ec86-119">Regresní/prediktivní spojité hodnoty</span><span class="sxs-lookup"><span data-stu-id="7ec86-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="7ec86-120">Předpovědět cenu domů na základě velikosti a umístění</span><span class="sxs-lookup"><span data-stu-id="7ec86-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="7ec86-121">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="7ec86-121">Anomaly Detection</span></span>|<span data-ttu-id="7ec86-122">Detekce podvodných bankovních transakcí</span><span class="sxs-lookup"><span data-stu-id="7ec86-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="7ec86-123">Doporučení</span><span class="sxs-lookup"><span data-stu-id="7ec86-123">Recommendations</span></span>|<span data-ttu-id="7ec86-124">Navrhněte produkty, které mohou online zákazníci chtít koupit na základě svých předchozích nákupů</span><span class="sxs-lookup"><span data-stu-id="7ec86-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="7ec86-125">Časová řada/sekvenční data</span><span class="sxs-lookup"><span data-stu-id="7ec86-125">Time series/sequential data</span></span>|<span data-ttu-id="7ec86-126">Předpověď prodeje počasí/produktu</span><span class="sxs-lookup"><span data-stu-id="7ec86-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="7ec86-127">Klasifikace obrázků</span><span class="sxs-lookup"><span data-stu-id="7ec86-127">Image classification</span></span>|<span data-ttu-id="7ec86-128">Kategorizovat patologie v lékařských obrazech</span><span class="sxs-lookup"><span data-stu-id="7ec86-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="7ec86-129">Dobrý den, ML.NET Svět</span><span class="sxs-lookup"><span data-stu-id="7ec86-129">Hello ML.NET World</span></span>

<span data-ttu-id="7ec86-130">Kód v následujícím fragmentu ukazuje nejjednodušší ML.NET aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ec86-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="7ec86-131">Tento příklad vytváří lineární regresní model pro předpovídání cen domů pomocí údajů o velikosti domu a cenách.</span><span class="sxs-lookup"><span data-stu-id="7ec86-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="7ec86-132">Pracovní postup kódu</span><span class="sxs-lookup"><span data-stu-id="7ec86-132">Code workflow</span></span>

<span data-ttu-id="7ec86-133">Následující diagram představuje strukturu kódu aplikace, stejně jako iterativní proces vývoje modelu:</span><span class="sxs-lookup"><span data-stu-id="7ec86-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="7ec86-134">Shromažďování a načítání trénovacích dat do objektu **IDataView**</span><span class="sxs-lookup"><span data-stu-id="7ec86-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="7ec86-135">Určení kanálu operací pro extrahování prvků a použití algoritmu strojového učení</span><span class="sxs-lookup"><span data-stu-id="7ec86-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="7ec86-136">Trénování modelu voláním **Fit()** na potrubí</span><span class="sxs-lookup"><span data-stu-id="7ec86-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="7ec86-137">Vyhodnoťte model a iterátte, abyste zlepšili</span><span class="sxs-lookup"><span data-stu-id="7ec86-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="7ec86-138">Uložení modelu do binárního formátu pro použití v aplikaci</span><span class="sxs-lookup"><span data-stu-id="7ec86-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="7ec86-139">Načtení modelu zpět do objektu **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="7ec86-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="7ec86-140">Provést předpovědi voláním **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="7ec86-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET tok vývoje aplikací včetně komponent pro generování dat, vývoj potrubí, trénování modelů, vyhodnocení modelu a využití modelu](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="7ec86-142">Pojďme se hlouběji ponořit do těchto pojmů.</span><span class="sxs-lookup"><span data-stu-id="7ec86-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="7ec86-143">Model strojového učení</span><span class="sxs-lookup"><span data-stu-id="7ec86-143">Machine learning model</span></span>

<span data-ttu-id="7ec86-144">Model ML.NET je objekt, který obsahuje transformace k provedení na vstupní data k dosažení předpokládaného výstupu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="7ec86-145">Základní</span><span class="sxs-lookup"><span data-stu-id="7ec86-145">Basic</span></span>

<span data-ttu-id="7ec86-146">Nejzákladnějším modelem je dvourozměrná lineární regrese, kde jedno souvislé množství je úměrné jinému, jako ve výše uvedeném příkladu ceny domu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Lineární regresní model s parametry zkreslení a hmotnosti](./media/linear-regression-model.svg)

<span data-ttu-id="7ec86-148">Model je jednoduše: $Price = b + Velikost \* w$.</span><span class="sxs-lookup"><span data-stu-id="7ec86-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="7ec86-149">Parametry $b$ a $w$ se odhadují montáží řádku na sadu (velikost, cena) párů.</span><span class="sxs-lookup"><span data-stu-id="7ec86-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="7ec86-150">Data použitá k nalezení parametrů modelu se nazývají **trénovací data**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="7ec86-151">Vstupy modelu strojového učení se nazývají **funkce**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="7ec86-152">V tomto příkladu je pouze funkce $Size$.</span><span class="sxs-lookup"><span data-stu-id="7ec86-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="7ec86-153">Hodnoty základní pravdy používané k trénování modelu strojového učení se nazývají **popisky**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="7ec86-154">Zde jsou hodnoty $Price$ v sadě trénovacích dat popisky.</span><span class="sxs-lookup"><span data-stu-id="7ec86-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="7ec86-155">Složitější</span><span class="sxs-lookup"><span data-stu-id="7ec86-155">More complex</span></span>

<span data-ttu-id="7ec86-156">Složitější model klasifikuje finanční transakce do kategorií pomocí textového popisu transakce.</span><span class="sxs-lookup"><span data-stu-id="7ec86-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="7ec86-157">Každý popis transakce je rozdělen do sady funkcí odebráním nadbytečných slov a znaků a počítáním kombinací slov a znaků.</span><span class="sxs-lookup"><span data-stu-id="7ec86-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="7ec86-158">Sada funkcí se používá k trénování lineárního modelu na základě sady kategorií v trénovacích datech.</span><span class="sxs-lookup"><span data-stu-id="7ec86-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="7ec86-159">Čím více podobný je nový popis těm v tréninkové sadě, tím je pravděpodobnější, že bude přiřazen do stejné kategorie.</span><span class="sxs-lookup"><span data-stu-id="7ec86-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Model klasifikace textu](./media/text-classification-model.svg)

<span data-ttu-id="7ec86-161">Cenový model domu i model klasifikace textu jsou **lineární** modely.</span><span class="sxs-lookup"><span data-stu-id="7ec86-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="7ec86-162">V závislosti na povaze dat a problému, který řešíte, můžete také použít modely **rozhodovacích stromů,** **generalizované aditivní** modely a další.</span><span class="sxs-lookup"><span data-stu-id="7ec86-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="7ec86-163">Další informace o modelech naleznete v [části Úkoly](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="7ec86-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="7ec86-164">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="7ec86-164">Data preparation</span></span>

<span data-ttu-id="7ec86-165">Ve většině případů data, která máte k dispozici, není vhodná pro použití přímo k trénování modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="7ec86-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="7ec86-166">Nezpracovaná data musí být připravena nebo předem zpracována, než je lze použít k nalezení parametrů modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="7ec86-167">Data může být nutné převést z řetězcových hodnot na číselnou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="7ec86-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="7ec86-168">Ve vstupních datech mohou být nadbytečné informace.</span><span class="sxs-lookup"><span data-stu-id="7ec86-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="7ec86-169">Možná budete muset zmenšit nebo rozšířit rozměry vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="7ec86-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="7ec86-170">Vaše data může být nutné normalizovat nebo škálovat.</span><span class="sxs-lookup"><span data-stu-id="7ec86-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="7ec86-171">V [ML.NET kurzy](./tutorials/index.md) vás naučí o různých kanálech pro zpracování dat pro text, obrázek, numerické a časové řady dat používaných pro konkrétní úlohy strojového učení.</span><span class="sxs-lookup"><span data-stu-id="7ec86-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="7ec86-172">[Jak připravit data,](./how-to-guides/prepare-data-ml-net.md) ukazuje, jak aplikovat přípravu dat obecněji.</span><span class="sxs-lookup"><span data-stu-id="7ec86-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="7ec86-173">Dodatek všech [dostupných transformací](./resources/transforms.md) najdete v části zdroje.</span><span class="sxs-lookup"><span data-stu-id="7ec86-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="7ec86-174">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="7ec86-174">Model evaluation</span></span>

<span data-ttu-id="7ec86-175">Poté, co jste trénoval svůj model, jak víte, jak dobře to bude dělat budoucí předpovědi?</span><span class="sxs-lookup"><span data-stu-id="7ec86-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="7ec86-176">S ML.NET můžete vyhodnotit model proti některé nové testovací data.</span><span class="sxs-lookup"><span data-stu-id="7ec86-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="7ec86-177">Každý typ úlohy strojového učení má metriky používané k vyhodnocení přesnosti a přesnosti modelu oproti sadě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="7ec86-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="7ec86-178">Pro náš příklad ceny domu jsme použili úkol **regrese.**</span><span class="sxs-lookup"><span data-stu-id="7ec86-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="7ec86-179">Chcete-li model vyhodnotit, přidejte do původní ukázky následující kód.</span><span class="sxs-lookup"><span data-stu-id="7ec86-179">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="7ec86-180">Metriky hodnocení vám říct, že chyba je low-ish a že korelace mezi předpokládaný výstup a testovací výstup je vysoká.</span><span class="sxs-lookup"><span data-stu-id="7ec86-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="7ec86-181">To bylo snadné!</span><span class="sxs-lookup"><span data-stu-id="7ec86-181">That was easy!</span></span> <span data-ttu-id="7ec86-182">V reálných příkladech je zapotřebí více ladění k dosažení dobrých metrik modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="7ec86-183">ML.NET architektura</span><span class="sxs-lookup"><span data-stu-id="7ec86-183">ML.NET architecture</span></span>

<span data-ttu-id="7ec86-184">V této části procházíme architektonickými vzory ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7ec86-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="7ec86-185">Pokud jste zkušený vývojář rozhraní .NET, některé z těchto vzorů vám budou známé a některé budou méně známé.</span><span class="sxs-lookup"><span data-stu-id="7ec86-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="7ec86-186">Držte se pevně, zatímco se ponoříme!</span><span class="sxs-lookup"><span data-stu-id="7ec86-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="7ec86-187">Aplikace ML.NET začíná <xref:Microsoft.ML.MLContext> objektem.</span><span class="sxs-lookup"><span data-stu-id="7ec86-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="7ec86-188">Tento objekt singleton obsahuje **katalogy**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="7ec86-189">Katalog je továrna pro načítání a ukládání dat, transformace, školicí prvky a součásti operací modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="7ec86-190">Každý objekt katalogu má metody k vytvoření různých typů součástí:</span><span class="sxs-lookup"><span data-stu-id="7ec86-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="7ec86-191">Načítání a ukládání dat</span><span class="sxs-lookup"><span data-stu-id="7ec86-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="7ec86-192">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="7ec86-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="7ec86-193">Tréninkové algoritmy</span><span class="sxs-lookup"><span data-stu-id="7ec86-193">Training algorithms</span></span>|<span data-ttu-id="7ec86-194">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="7ec86-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="7ec86-195">Klasifikace více tříd</span><span class="sxs-lookup"><span data-stu-id="7ec86-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="7ec86-196">Detekce anomálií</span><span class="sxs-lookup"><span data-stu-id="7ec86-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="7ec86-197">Clustering</span><span class="sxs-lookup"><span data-stu-id="7ec86-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="7ec86-198">Prognózování</span><span class="sxs-lookup"><span data-stu-id="7ec86-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="7ec86-199">Pořadí</span><span class="sxs-lookup"><span data-stu-id="7ec86-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="7ec86-200">Regrese</span><span class="sxs-lookup"><span data-stu-id="7ec86-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="7ec86-201">Doporučení</span><span class="sxs-lookup"><span data-stu-id="7ec86-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="7ec86-202">přidání `Microsoft.ML.Recommender` balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="7ec86-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="7ec86-203">Časová řada</span><span class="sxs-lookup"><span data-stu-id="7ec86-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="7ec86-204">přidání `Microsoft.ML.TimeSeries` balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="7ec86-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="7ec86-205">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="7ec86-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="7ec86-206">Můžete přejít na metody vytváření v každé z výše uvedených kategorií.</span><span class="sxs-lookup"><span data-stu-id="7ec86-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="7ec86-207">Pomocí sady Visual Studio se katalogy zobrazují prostřednictvím technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7ec86-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Intellisense pro regresní školitelů](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="7ec86-209">Sestavení kanálu</span><span class="sxs-lookup"><span data-stu-id="7ec86-209">Build the pipeline</span></span>

<span data-ttu-id="7ec86-210">Uvnitř každého katalogu je sada metod rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7ec86-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="7ec86-211">Podívejme se na způsob rozšíření metody se používají k vytvoření kanálu školení.</span><span class="sxs-lookup"><span data-stu-id="7ec86-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="7ec86-212">Ve fragmentu a `Concatenate` `Sdca` jsou obě metody v katalogu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="7ec86-213">Každý z nich vytvořit [objekt IEstimator,](xref:Microsoft.ML.IEstimator%601) který je připojen k kanálu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="7ec86-214">V tomto okamžiku jsou objekty vytvořeny pouze.</span><span class="sxs-lookup"><span data-stu-id="7ec86-214">At this point, the objects are created only.</span></span> <span data-ttu-id="7ec86-215">K žádné popravě nedošlo.</span><span class="sxs-lookup"><span data-stu-id="7ec86-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="7ec86-216">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7ec86-216">Train the model</span></span>

<span data-ttu-id="7ec86-217">Po vytvoření objektů v kanálu data lze použít k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="7ec86-218">Volání `Fit()` používá vstupní trénovací data k odhadu parametrů modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="7ec86-219">To se označuje jako trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-219">This is known as training the model.</span></span> <span data-ttu-id="7ec86-220">Nezapomeňte, že výše uvedený lineární regresní model měl dva parametry modelu: **zkreslení** a **hmotnost**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="7ec86-221">Po `Fit()` volání jsou známy hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="7ec86-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="7ec86-222">Většina modelů bude mít mnohem více parametrů než toto.</span><span class="sxs-lookup"><span data-stu-id="7ec86-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="7ec86-223">Další informace o trénování modelu najdete v [aplikaci Jak trénovat model](./how-to-guides/train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="7ec86-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="7ec86-224">Výsledný objekt modelu implementuje <xref:Microsoft.ML.ITransformer> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7ec86-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="7ec86-225">To znamená, že model transformuje vstupní data do předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7ec86-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="7ec86-226">Použití modelu</span><span class="sxs-lookup"><span data-stu-id="7ec86-226">Use the model</span></span>

<span data-ttu-id="7ec86-227">Vstupní data můžete transformovat do předpovědi hromadně nebo jeden vstup najednou.</span><span class="sxs-lookup"><span data-stu-id="7ec86-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="7ec86-228">V příkladu ceny domu jsme udělali obojí: hromadně za účelem vyhodnocení modelu a jeden po druhém, abychom vytvořili novou předpověď.</span><span class="sxs-lookup"><span data-stu-id="7ec86-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="7ec86-229">Podívejme se na vytváření jednotlivých předpovědí.</span><span class="sxs-lookup"><span data-stu-id="7ec86-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="7ec86-230">Metoda `CreatePredictionEngine()` trvá vstupní třídy a výstupní třídy.</span><span class="sxs-lookup"><span data-stu-id="7ec86-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="7ec86-231">Názvy polí nebo atributy kódu určují názvy datových sloupců použitých během trénování a predikce modelu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="7ec86-232">Další informace naleznete v [tématu Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="7ec86-232">For more information, see [Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="7ec86-233">Datové modely a schémata</span><span class="sxs-lookup"><span data-stu-id="7ec86-233">Data models and schema</span></span>

<span data-ttu-id="7ec86-234">Jádrem kanálu ML.NET strojového učení jsou objekty [DataView.](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="7ec86-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="7ec86-235">Každá transformace v kanálu má vstupní schéma (názvy dat, typy a velikosti, které transformace očekává, že vidět na jeho vstupu); a výstupní schéma (názvy dat, typy a velikosti, které transformace vytvoří po transformaci).</span><span class="sxs-lookup"><span data-stu-id="7ec86-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="7ec86-236">Následující dokument obsahuje podrobné vysvětlení [rozhraní IDataView a jeho typového systému](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span><span class="sxs-lookup"><span data-stu-id="7ec86-236">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="7ec86-237">Pokud výstupní schéma z jedné transformace v kanálu neodpovídá vstupníschéma další transformace, ML.NET vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="7ec86-237">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="7ec86-238">Objekt zobrazení dat má sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="7ec86-238">A data view object has columns and rows.</span></span> <span data-ttu-id="7ec86-239">Každý sloupec má název a typ a délku.</span><span class="sxs-lookup"><span data-stu-id="7ec86-239">Each column has a name and a type and a length.</span></span> <span data-ttu-id="7ec86-240">Například vstupní sloupce v příkladu ceny domu jsou **Velikost** a **cena**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-240">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="7ec86-241">Oba jsou typ a jsou skalární množství spíše než vektorové.</span><span class="sxs-lookup"><span data-stu-id="7ec86-241">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![ML.NET příklad zobrazení dat s údaji o předpovědi cen domů](./media/ml-net-dataview.png)

<span data-ttu-id="7ec86-243">Všechny ML.NET algoritmy hledají vstupní sloupec, který je vektor.</span><span class="sxs-lookup"><span data-stu-id="7ec86-243">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="7ec86-244">Ve výchozím nastavení se tento vektorový sloupec nazývá **Funkce**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-244">By default this vector column is called **Features**.</span></span> <span data-ttu-id="7ec86-245">To je důvod, proč jsme zřetězili sloupec **Velikost** do nového sloupce s názvem **Funkce** v našem příkladu ceny domu.</span><span class="sxs-lookup"><span data-stu-id="7ec86-245">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="7ec86-246">Všechny algoritmy také vytvořit nové sloupce po provedení předpověď.</span><span class="sxs-lookup"><span data-stu-id="7ec86-246">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="7ec86-247">Pevné názvy těchto nových sloupců závisí na typu algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="7ec86-247">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="7ec86-248">Pro regresní úlohu se jeden z nových sloupců nazývá **Skóre**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-248">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="7ec86-249">To je důvod, proč jsme připisovali naše cenové údaje s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="7ec86-249">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="7ec86-250">Další informace o výstupních sloupcích různých úloh strojového učení najdete v příručce [Úlohy strojového učení.](resources/tasks.md)</span><span class="sxs-lookup"><span data-stu-id="7ec86-250">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="7ec86-251">Důležitou vlastností objektů DataView je, že jsou vyhodnocovány **líně**.</span><span class="sxs-lookup"><span data-stu-id="7ec86-251">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="7ec86-252">Zobrazení dat jsou načteny a provozovány pouze během trénování a vyhodnocení modelu a predikce dat.</span><span class="sxs-lookup"><span data-stu-id="7ec86-252">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="7ec86-253">Při psaní a testování ML.NET aplikace, můžete použít ladicí program Sady Visual Studio nahlédnout na libovolný objekt zobrazení dat voláním [metody Náhled.](xref:Microsoft.ML.DebuggerExtensions.Preview*)</span><span class="sxs-lookup"><span data-stu-id="7ec86-253">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="7ec86-254">Můžete sledovat `debug` proměnnou v ladicím programu a zkoumat její obsah.</span><span class="sxs-lookup"><span data-stu-id="7ec86-254">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="7ec86-255">Nepoužívejte metodu Náhled v produkčním kódu, protože výrazně snižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="7ec86-255">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="7ec86-256">Nasazení modelu</span><span class="sxs-lookup"><span data-stu-id="7ec86-256">Model Deployment</span></span>

<span data-ttu-id="7ec86-257">V reálných aplikacích bude váš model školení a hodnocení kód bude oddělena od predikce.</span><span class="sxs-lookup"><span data-stu-id="7ec86-257">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="7ec86-258">Ve skutečnosti jsou tyto dvě činnosti často prováděny samostatnými týmy.</span><span class="sxs-lookup"><span data-stu-id="7ec86-258">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="7ec86-259">Váš tým pro vývoj modelu můžete uložit model pro použití v aplikaci předpověď.</span><span class="sxs-lookup"><span data-stu-id="7ec86-259">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="7ec86-260">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7ec86-260">Next steps</span></span>

* <span data-ttu-id="7ec86-261">Naučte se vytvářet aplikace pomocí různých úloh strojového učení s realističtějšími sadami dat v [kurzech](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ec86-261">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="7ec86-262">Další informace o konkrétních tématech podrobněji naleznete v příručce [How To Guides](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ec86-262">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="7ec86-263">Pokud jste super zájem, můžete se ponořit přímo do [referenční dokumentace API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7ec86-263">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
