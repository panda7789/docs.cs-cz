---
title: Základní koncepty k tréninku modelu v ML.NET
description: Tento článek vysvětluje základní koncepty pokrývající *model školení* scénáře v ML.NET. Ne všechny koncepty jsou relevantní pro více jednoduchého scénáře *půjček s využitím existující model*.
ms.date: 03/05/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: d29f6b901b0296f4d9a75b470a84dc087fb50e5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973834"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="67a2f-104">Základní koncepty k tréninku modelu v ML.NET</span><span class="sxs-lookup"><span data-stu-id="67a2f-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="67a2f-105">Tento článek vysvětluje základní koncepty pokrývající *model školení* scénáře v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="67a2f-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="67a2f-106">Ne všechny koncepty jsou relevantní pro více jednoduchého scénáře *půjček s využitím existující model*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-106">Not all concepts are relevant to the more simple scenario of *prediction with an existing model*.</span></span>

<span data-ttu-id="67a2f-107">Tento článek a související ukázkové právě používáte **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="67a2f-107">This article and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="67a2f-108">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="67a2f-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="67a2f-109">Koncepty trénování modelu</span><span class="sxs-lookup"><span data-stu-id="67a2f-109">Model training concepts</span></span>

<span data-ttu-id="67a2f-110">Tento dokument popisuje tyto koncepty související s cvičení modelu v ML.NET:</span><span class="sxs-lookup"><span data-stu-id="67a2f-110">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="67a2f-111">[*Data* ](#data) reprezentovaná jako `IDataView` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-111">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="67a2f-112">Data jsou v ML.NET, podobně jako zobrazení SQL: Je laxně Vyhodnocená, nezměnitelný, cursorable, heterogenní, schematizovanými datové sady.</span><span class="sxs-lookup"><span data-stu-id="67a2f-112">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="67a2f-113">Je vynikající dokumentu o rozhraní data [Principy návrhu IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="67a2f-113">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="67a2f-114">[*Transformer* ](#transformer) reprezentovaná jako `ITransformer` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-114">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="67a2f-115">Transformátoru je komponenta, která přijímá data, některé funguje na něj a vrátí nový Transformovaná data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-115">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="67a2f-116">Můžete například představit model strojového učení jako transformátoru, která přijímá funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="67a2f-116">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="67a2f-117">Další příklad, text tokenizátor přijímá jeden textový sloupec a vypíše vektoru sloupec s jednotlivá slova extrahovaná z texty.</span><span class="sxs-lookup"><span data-stu-id="67a2f-117">Another example, text tokenizer takes a single text column and outputs a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="67a2f-118">[*Čtecí modul dat* ](#data-reader) reprezentovaná jako `IDataReader<T>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-118">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="67a2f-119">Čtecí modul dat není ML.NET komponentu data vytváří.</span><span class="sxs-lookup"><span data-stu-id="67a2f-119">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="67a2f-120">Použije instanci `T` a vrátí data z ní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-120">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="67a2f-121">Například *TextLoader* je `IDataReader<IMultiStreamSource>`.</span><span class="sxs-lookup"><span data-stu-id="67a2f-121">For example, a *TextLoader* is an `IDataReader<IMultiStreamSource>`.</span></span> <span data-ttu-id="67a2f-122">Vezme zdroji a vytvoří data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-122">It takes the source and produces data.</span></span> 
- <span data-ttu-id="67a2f-123">[*Odhad* ](#estimator) reprezentovaná jako `IEstimator<T>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-123">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="67a2f-124">Toto je objekt, který zjistí od data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-124">This is an object that learns from data.</span></span> <span data-ttu-id="67a2f-125">Výsledek Learning *transformer*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-125">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="67a2f-126">Si můžete představit služby machine learning *algoritmus* jako odhad, který učí s daty a machine learningu vytváří *modelu*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-126">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="67a2f-127">[*Funkce předpovědi* ](#prediction-function) vyjádřené `PredictionEngine<TSrc, TDst>` třídy.</span><span class="sxs-lookup"><span data-stu-id="67a2f-127">[*Prediction function*](#prediction-function) represented as a `PredictionEngine<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="67a2f-128">Funkce předpovědi se dají považovat za počítač, který se vztahuje na jeden řádek, transformátoru, jako v době předpovědi.</span><span class="sxs-lookup"><span data-stu-id="67a2f-128">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="67a2f-129">Data</span><span class="sxs-lookup"><span data-stu-id="67a2f-129">Data</span></span> 

<span data-ttu-id="67a2f-130">Data jsou v ML.NET, podobně jako zobrazení SQL: Jde laxně Vyhodnocená, schematizovanými cursorable heterogenní, datové sady.</span><span class="sxs-lookup"><span data-stu-id="67a2f-130">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="67a2f-131">Má *schématu* (instance `ISchema` rozhraní), který obsahuje informace o zobrazení dat sloupce.</span><span class="sxs-lookup"><span data-stu-id="67a2f-131">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="67a2f-132">Má každý sloupec *název*, *typ*a libovolné sady *metadat* s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="67a2f-132">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="67a2f-133">Sloupce *metadat* obsahují informace jako slotu názvy sloupců vektoru a podobně.</span><span class="sxs-lookup"><span data-stu-id="67a2f-133">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="67a2f-134">Metadata samotného je reprezentována jako jiný jeden řádek *data* , který je jedinečný pro každý sloupec.</span><span class="sxs-lookup"><span data-stu-id="67a2f-134">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="67a2f-135">Zobrazení dat se zdrojem *kurzory*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-135">The data view is a source of *cursors*.</span></span> <span data-ttu-id="67a2f-136">Představte si, že kurzory SQL: Kurzor je objekt, který Iteruje přes data, jeden řádek v době a zobrazí dostupná data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-136">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="67a2f-137">Přirozeně dat může mít libovolný počet aktivních ukazatele nad ním podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="67a2f-137">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="67a2f-138">Vlastní data je neměnný, jsou skutečně nezávislé kurzory.</span><span class="sxs-lookup"><span data-stu-id="67a2f-138">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="67a2f-139">Kurzory obvykle přístupu pouze podmnožinu sloupců: Z důvodu efektivity vypočítá ML.NET pouze hodnoty sloupce, které jsou vyžadované kurzor.</span><span class="sxs-lookup"><span data-stu-id="67a2f-139">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="67a2f-140">Transformer</span><span class="sxs-lookup"><span data-stu-id="67a2f-140">Transformer</span></span>

<span data-ttu-id="67a2f-141">Transformátoru je komponenta, která přijímá data, některé funguje na něj a vrátí nový Transformovaná data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-141">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>

<span data-ttu-id="67a2f-142">Většina transformátory v ML.NET mají tendenci provozovat na jednom *vstupní sloupec* v době a vytvoří *výstupní sloupec*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-142">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="67a2f-143">Například `new HashTransformer("bar", "foo")` vezme hodnoty ze sloupce "foo", hash je a umístí je do sloupce "panel".</span><span class="sxs-lookup"><span data-stu-id="67a2f-143">For example, a `new HashTransformer("bar", "foo")` takes the values from column "foo", hashes them, and puts them into column "bar".</span></span> 

<span data-ttu-id="67a2f-144">Také je běžné, že názvy sloupců vstupních a výstupních jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="67a2f-144">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="67a2f-145">V takovém případě staré sloupce se nahradí novým.</span><span class="sxs-lookup"><span data-stu-id="67a2f-145">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="67a2f-146">Například `new HashTransformer("foo")` vezme hodnoty ze sloupce "foo", je hash a vrátí zpět do "foo".</span><span class="sxs-lookup"><span data-stu-id="67a2f-146">For example, a `new HashTransformer("foo")` takes the values from column "foo", hashes them, and puts them back into "foo".</span></span> 

<span data-ttu-id="67a2f-147">Všechny transformace, vytvoří nová data zobrazit při `Transform` je volána.</span><span class="sxs-lookup"><span data-stu-id="67a2f-147">Any transformer, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="67a2f-148">Mějte na paměti, data zobrazení jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="67a2f-148">Remember, data views are immutable.</span></span>

<span data-ttu-id="67a2f-149">Další důležitý aspekt spočívá, protože laxně vyhodnocení dat *transformátory jsou příliš opožděné*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-149">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="67a2f-150">V podstatě po volání</span><span class="sxs-lookup"><span data-stu-id="67a2f-150">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="67a2f-151">žádný skutečný výpočtu se stane.</span><span class="sxs-lookup"><span data-stu-id="67a2f-151">no actual computation happens.</span></span> <span data-ttu-id="67a2f-152">Až poté, co se zobrazí kurzor z `newData` a provede počáteční hodnota využívání `newData` vyvolat `transformer` logiku transformace (a dokonce i pak ji pouze se stane, když `transformer` dotyčný je potřeba k vytvoření požadované sloupce).</span><span class="sxs-lookup"><span data-stu-id="67a2f-152">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even then, it only happens if the `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="67a2f-153">Transformace řetězců</span><span class="sxs-lookup"><span data-stu-id="67a2f-153">Transformer chains</span></span>

<span data-ttu-id="67a2f-154">Je užitečné vlastnost transformátoru *můžete vytvářet aplikace sekvenčního transformátorů zatím jiné transformer*:</span><span class="sxs-lookup"><span data-stu-id="67a2f-154">A useful property of a transformer is that *you can build a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="67a2f-155">Tato vlastnost se běžně používá v ML.NET: obvykle trénovaného modelu ML.NET je řetězec transformátory, což je pro veškeré záměry a úmysly, *transformer*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-155">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span>

## <a name="data-reader"></a><span data-ttu-id="67a2f-156">Čtecí modul dat</span><span class="sxs-lookup"><span data-stu-id="67a2f-156">Data reader</span></span>

<span data-ttu-id="67a2f-157">Čtecí modul dat je ML.NET součást pro vytváření dat: použije instanci `T` a vrátí data z ní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-157">The data reader is an ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="67a2f-158">Zajímavé vlastnost si je, že můžete vytvořit čtecí modul dat transformátoru připojením k existující čtecí modul dat.</span><span class="sxs-lookup"><span data-stu-id="67a2f-158">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="67a2f-159">Tímto způsobem může mít čtečku s vloženými chování transformace:</span><span class="sxs-lookup"><span data-stu-id="67a2f-159">This way you can have a reader with transformation behavior baked in:</span></span>

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="67a2f-160">Jiné podobnosti transformátory je, že od laxně vyhodnocení dat *čtenáři jsou opožděná*: žádný (nebo minimální) skutečné "čtení" se stane, když voláte `reader.Read()`: pouze pokud je požadováno kurzor na Výsledná data se Čtečka začít pracovat.</span><span class="sxs-lookup"><span data-stu-id="67a2f-160">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `reader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="67a2f-161">Odhad</span><span class="sxs-lookup"><span data-stu-id="67a2f-161">Estimator</span></span>

<span data-ttu-id="67a2f-162">*Estimator* je objekt, který zjistí od data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-162">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="67a2f-163">Výsledek Learning *transformer*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-163">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="67a2f-164">V ML.NET lze tuto vlastnost použijte k vytvoření kanálů učení, které zřetězit různých odhady:</span><span class="sxs-lookup"><span data-stu-id="67a2f-164">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

<span data-ttu-id="67a2f-165">Důležité vlastnictví odhady je, že *odhady se nemůžou dočkat, až, ne opožděné*: všechna volání `Fit` způsobuje learning a, která je potenciálně časově náročná operace.</span><span class="sxs-lookup"><span data-stu-id="67a2f-165">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="67a2f-166">Funkce předpovědi</span><span class="sxs-lookup"><span data-stu-id="67a2f-166">Prediction function</span></span>

<span data-ttu-id="67a2f-167">Funkce předpovědi se dají považovat za součást, která transformátoru se vztahuje na jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="67a2f-167">The prediction function can be seen as a component that applies a transformer to one row.</span></span>

<span data-ttu-id="67a2f-168">Po načtení modelu ( *transformer* buď školení prostřednictvím `Fit()`, nebo načíst z oblasti), ve kterém můžete vytvářet predikce na normální volání `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="67a2f-168">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="67a2f-169">Ale při použití tohoto modelu v reálné situaci často není nutné mnoho příkladů k předpovědi na.</span><span class="sxs-lookup"><span data-stu-id="67a2f-169">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="67a2f-170">Místo toho jste jedním z příkladů v čase a je třeba provést včas predikcí okamžitě s nimi.</span><span class="sxs-lookup"><span data-stu-id="67a2f-170">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="67a2f-171">Samozřejmě to můžete snížit na predikce služby batch:</span><span class="sxs-lookup"><span data-stu-id="67a2f-171">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="67a2f-172">Vytvoření zobrazení dat se přesně jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="67a2f-172">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="67a2f-173">Volání `model.Transform(data)` zobrazíte předpokládané dat zobrazení.</span><span class="sxs-lookup"><span data-stu-id="67a2f-173">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="67a2f-174">Získejte kurzoru přes Výsledná data.</span><span class="sxs-lookup"><span data-stu-id="67a2f-174">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="67a2f-175">Předem jeden krok kurzor na řádek prvnímu (zároveň jedinému).</span><span class="sxs-lookup"><span data-stu-id="67a2f-175">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="67a2f-176">Extrahujte predikované hodnoty z ní.</span><span class="sxs-lookup"><span data-stu-id="67a2f-176">Extract the predicted values out of it.</span></span>

<span data-ttu-id="67a2f-177">Předchozí algoritmus je možné implementovat pomocí [pochopení schématu](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), s dvěma uživatelem definované objekty `InputExample` a `OutputPrediction` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="67a2f-177">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

<span data-ttu-id="67a2f-178">Ale to je náročné a má za následek nákladů na výkon.</span><span class="sxs-lookup"><span data-stu-id="67a2f-178">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="67a2f-179">Místo toho objekt funkce předpovědi provádí stejný pracovní, ale rychleji a efektivněji pomocí metody rozšíření `CreatePredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="67a2f-179">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `CreatePredictionEngine`:</span></span>

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

<span data-ttu-id="67a2f-180">Funkce předpovědi je *není vícenásobně / bezpečné pro vlákna*.</span><span class="sxs-lookup"><span data-stu-id="67a2f-180">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="67a2f-181">Pokud chcete provádět předpovědi současně s více vlákny, musíte mít funkci předpovědi na vlákno.</span><span class="sxs-lookup"><span data-stu-id="67a2f-181">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
