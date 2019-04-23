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
# <a name="basic-concepts-for-model-training-in-mlnet"></a>Základní koncepty k tréninku modelu v ML.NET

Tento článek vysvětluje základní koncepty pokrývající *model školení* scénáře v ML.NET. Ne všechny koncepty jsou relevantní pro více jednoduchého scénáře *půjček s využitím existující model*.

Tento článek a související ukázkové právě používáte **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="model-training-concepts"></a>Koncepty trénování modelu

Tento dokument popisuje tyto koncepty související s cvičení modelu v ML.NET:

- [*Data* ](#data) reprezentovaná jako `IDataView` rozhraní.
  - Data jsou v ML.NET, podobně jako zobrazení SQL: Je laxně Vyhodnocená, nezměnitelný, cursorable, heterogenní, schematizovanými datové sady. 
  - Je vynikající dokumentu o rozhraní data [Principy návrhu IDataView](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).
- [*Transformer* ](#transformer) reprezentovaná jako `ITransformer` rozhraní.
  - Transformátoru je komponenta, která přijímá data, některé funguje na něj a vrátí nový Transformovaná data.
  - Můžete například představit model strojového učení jako transformátoru, která přijímá funkce a vrátí předpovědi.
  - Další příklad, text tokenizátor přijímá jeden textový sloupec a vypíše vektoru sloupec s jednotlivá slova extrahovaná z texty.
- [*Čtecí modul dat* ](#data-reader) reprezentovaná jako `IDataReader<T>` rozhraní.
  - Čtecí modul dat není ML.NET komponentu data vytváří. Použije instanci `T` a vrátí data z ní. 
  - Například *TextLoader* je `IDataReader<IMultiStreamSource>`. Vezme zdroji a vytvoří data. 
- [*Odhad* ](#estimator) reprezentovaná jako `IEstimator<T>` rozhraní.
  - Toto je objekt, který zjistí od data. Výsledek Learning *transformer*.
  - Si můžete představit služby machine learning *algoritmus* jako odhad, který učí s daty a machine learningu vytváří *modelu*.
- [*Funkce předpovědi* ](#prediction-function) vyjádřené `PredictionEngine<TSrc, TDst>` třídy.
  - Funkce předpovědi se dají považovat za počítač, který se vztahuje na jeden řádek, transformátoru, jako v době předpovědi.

## <a name="data"></a>Data 

Data jsou v ML.NET, podobně jako zobrazení SQL: Jde laxně Vyhodnocená, schematizovanými cursorable heterogenní, datové sady.

- Má *schématu* (instance `ISchema` rozhraní), který obsahuje informace o zobrazení dat sloupce.
  - Má každý sloupec *název*, *typ*a libovolné sady *metadat* s ním spojená.
  - Sloupce *metadat* obsahují informace jako slotu názvy sloupců vektoru a podobně. Metadata samotného je reprezentována jako jiný jeden řádek *data* , který je jedinečný pro každý sloupec.
  - Zobrazení dat se zdrojem *kurzory*. Představte si, že kurzory SQL: Kurzor je objekt, který Iteruje přes data, jeden řádek v době a zobrazí dostupná data.
  - Přirozeně dat může mít libovolný počet aktivních ukazatele nad ním podle potřeby. Vlastní data je neměnný, jsou skutečně nezávislé kurzory.
  - Kurzory obvykle přístupu pouze podmnožinu sloupců: Z důvodu efektivity vypočítá ML.NET pouze hodnoty sloupce, které jsou vyžadované kurzor.

## <a name="transformer"></a>Transformer

Transformátoru je komponenta, která přijímá data, některé funguje na něj a vrátí nový Transformovaná data.

Většina transformátory v ML.NET mají tendenci provozovat na jednom *vstupní sloupec* v době a vytvoří *výstupní sloupec*. Například `new HashTransformer("bar", "foo")` vezme hodnoty ze sloupce "foo", hash je a umístí je do sloupce "panel". 

Také je běžné, že názvy sloupců vstupních a výstupních jsou stejné. V takovém případě staré sloupce se nahradí novým. Například `new HashTransformer("foo")` vezme hodnoty ze sloupce "foo", je hash a vrátí zpět do "foo". 

Všechny transformace, vytvoří nová data zobrazit při `Transform` je volána. Mějte na paměti, data zobrazení jsou neměnné.

Další důležitý aspekt spočívá, protože laxně vyhodnocení dat *transformátory jsou příliš opožděné*. V podstatě po volání

```csharp
var newData = transformer.Transform(oldData)
```

žádný skutečný výpočtu se stane. Až poté, co se zobrazí kurzor z `newData` a provede počáteční hodnota využívání `newData` vyvolat `transformer` logiku transformace (a dokonce i pak ji pouze se stane, když `transformer` dotyčný je potřeba k vytvoření požadované sloupce).

### <a name="transformer-chains"></a>Transformace řetězců

Je užitečné vlastnost transformátoru *můžete vytvářet aplikace sekvenčního transformátorů zatím jiné transformer*:

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

Tato vlastnost se běžně používá v ML.NET: obvykle trénovaného modelu ML.NET je řetězec transformátory, což je pro veškeré záměry a úmysly, *transformer*.

## <a name="data-reader"></a>Čtecí modul dat

Čtecí modul dat je ML.NET součást pro vytváření dat: použije instanci `T` a vrátí data z ní.

Zajímavé vlastnost si je, že můžete vytvořit čtecí modul dat transformátoru připojením k existující čtecí modul dat. Tímto způsobem může mít čtečku s vloženými chování transformace:

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

Jiné podobnosti transformátory je, že od laxně vyhodnocení dat *čtenáři jsou opožděná*: žádný (nebo minimální) skutečné "čtení" se stane, když voláte `reader.Read()`: pouze pokud je požadováno kurzor na Výsledná data se Čtečka začít pracovat.

## <a name="estimator"></a>Odhad

*Estimator* je objekt, který zjistí od data. Výsledek Learning *transformer*.

V ML.NET lze tuto vlastnost použijte k vytvoření kanálů učení, které zřetězit různých odhady:

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

Důležité vlastnictví odhady je, že *odhady se nemůžou dočkat, až, ne opožděné*: všechna volání `Fit` způsobuje learning a, která je potenciálně časově náročná operace.

## <a name="prediction-function"></a>Funkce předpovědi

Funkce předpovědi se dají považovat za součást, která transformátoru se vztahuje na jeden řádek.

Po načtení modelu ( *transformer* buď školení prostřednictvím `Fit()`, nebo načíst z oblasti), ve kterém můžete vytvářet predikce na normální volání `model.Transform(data)`. Ale při použití tohoto modelu v reálné situaci často není nutné mnoho příkladů k předpovědi na. Místo toho jste jedním z příkladů v čase a je třeba provést včas predikcí okamžitě s nimi.

Samozřejmě to můžete snížit na predikce služby batch:

- Vytvoření zobrazení dat se přesně jeden řádek.
- Volání `model.Transform(data)` zobrazíte předpokládané dat zobrazení.
- Získejte kurzoru přes Výsledná data.
- Předem jeden krok kurzor na řádek prvnímu (zároveň jedinému).
- Extrahujte predikované hodnoty z ní.

Předchozí algoritmus je možné implementovat pomocí [pochopení schématu](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), s dvěma uživatelem definované objekty `InputExample` a `OutputPrediction` následujícím způsobem:

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

Ale to je náročné a má za následek nákladů na výkon. Místo toho objekt funkce předpovědi provádí stejný pracovní, ale rychleji a efektivněji pomocí metody rozšíření `CreatePredictionEngine`:

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

Funkce předpovědi je *není vícenásobně / bezpečné pro vlákna*. Pokud chcete provádět předpovědi současně s více vlákny, musíte mít funkci předpovědi na vlákno.
