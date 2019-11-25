---
title: Příprava dat pro vytvoření modelu
description: Naučte se používat transformace v ML.NET k manipulaci a přípravě dat pro další zpracování nebo vytváření modelů.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: e9bfad4724b353b0f3bfc615a40f1d72b80a2cd4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976981"
---
# <a name="prepare-data-for-building-a-model"></a>Příprava dat pro vytvoření modelu

Naučte se používat ML.NET k přípravě dat pro další zpracování nebo vytvoření modelu.

Data často nejsou čistá a zhuštěná. Algoritmy strojového učení ML.NET očekávají zadání nebo funkce v jednom numerickém vektoru. Podobně hodnota pro předpověď (Label), zejména v případě, že je kategorií data, musí být kódována. Proto je jedním z cílů přípravy dat získat data do formátu očekávaného ML.NET algoritmy.

## <a name="filter-data"></a>Filtrovat data

V některých případech nejsou všechna data v datové sadě relevantní pro účely analýzy. Přístup k odebrání nerelevantních dat je filtrování. [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) obsahuje sadu operací filtrování, které přebírají [`IDataView`](xref:Microsoft.ML.IDataView) obsahující všechna data a vracejí [IDataView](xref:Microsoft.ML.IDataView) obsahující jenom datové body, které vás zajímají. Je důležité si uvědomit, že protože operace filtru nejsou [`IEstimator`](xref:Microsoft.ML.IEstimator%601) nebo [`ITransformer`](xref:Microsoft.ML.ITransformer) jako ty v [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), nedají se zahrnout jako součást [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) kanálu pro přípravu dat.

Pomocí následujících vstupních dat, která se načítají do [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

Chcete-li filtrovat data na základě hodnoty sloupce, použijte metodu [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) .

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Výše uvedená ukázka v datové sadě bere řádky s cenou mezi 200000 a 1000000. Výsledek použití tohoto filtru vrátí jenom poslední dva řádky v datech a vyloučí první řádek, protože jeho cena je 100000 a ne mezi zadaným rozsahem.

## <a name="replace-missing-values"></a>Nahradit chybějící hodnoty

Chybějící hodnoty jsou běžné výskyty v datových sadách. Jediným způsobem, jak řešit chybějící hodnoty, je nahradit je výchozí hodnotou pro daný typ, pokud kteroukoli nebo jinou smysluplnou hodnotu, například střední hodnotu v datech.

Pomocí následujících vstupních dat, která se načítají do [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

Všimněte si, že poslední prvek v našem seznamu má chybějící hodnotu pro `Price`. Chcete-li nahradit chybějící hodnoty ve sloupci `Price`, použijte metodu [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) k vyplnění chybějící hodnoty.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) funguje pouze s numerickými daty.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET podporuje různé [režimy nahrazení](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Výše uvedená ukázka používá režim nahrazení `Mean`, ve kterém se vyplní chybějící hodnota průměrnou hodnotou tohoto sloupce. Výsledek nahrazení vyplní vlastnost `Price` pro poslední prvek v datech s 200 000, protože se jedná o průměr 100 000 a 300 000.

## <a name="use-normalizers"></a>Použít normalizy

[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) je metoda předběžného zpracování dat, která slouží ke standardizaci funkcí, které nejsou ve stejném měřítku, což pomáhá zvýšit sblížení algoritmů. Například rozsahy pro hodnoty, jako je věk a příjem, se výrazně liší v rozmezí 0-100 a příjem je obecně v rozsahu od 0 do tisíců. Podrobnější seznam a popis transformací normalizace najdete na [stránce transformace](../resources/transforms.md) .

### <a name="min-max-normalization"></a>Normalizace min-max

Pomocí následujících vstupních dat, která se načítají do [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

Normalizace se dá použít na sloupce s jednou číselnou hodnotou i vektory. Normalizuje data ve sloupci `Price` pomocí normalizace min-max s metodou [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) .

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Původní cenové hodnoty `[200000,100000]` jsou převedeny na `[ 1, 0.5 ]` pomocí vzorce `MinMax` normalizace, který generuje výstupní hodnoty v rozsahu 0-1.

### <a name="binning"></a>Binningu

[Binningu](https://en.wikipedia.org/wiki/Data_binning) převádí souvislé hodnoty do diskrétní reprezentace vstupu. Předpokládejme například, že jedna z vašich funkcí je věková. Místo použití skutečné věkové hodnoty binningu vytvoří rozsahy pro tuto hodnotu. 0-18 může být jedna přihrádka, další by mohla být 19-35 a tak dále.

Pomocí následujících vstupních dat, která se načítají do [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

Normalizuje data do přihrádek pomocí metody [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) . Parametr `maximumBinCount` umožňuje zadat počet přihrádek potřebných ke klasifikaci vašich dat. V tomto příkladu budou data vložena do dvou přihrádek.

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Výsledek binningu vytvoří meze přihrádky `[0,200000,Infinity]`. Proto jsou výsledné přihrádky `[0,1,1]`, protože první pozorování je mezi 0-200000 a ostatní jsou větší než 200000, ale menší než nekonečno.

## <a name="work-with-categorical-data"></a>Práce s kategorií daty

Než se číselné kategorií data musí převést na číslo, než se použije k sestavení modelu Machine Learning.

Pomocí následujících vstupních dat, která se načítají do [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
CarData[] cars = new CarData[]
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

Vlastnost kategorií `VehicleType` lze převést na číslo pomocí metody [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) .

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

Výsledná transformace převede textovou hodnotu `VehicleType` na číslo. Při použití transformace se položky ve sloupci `VehicleType` stanou následujícím:

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Práce s textovými daty

Textová data je potřeba transformovat na čísla, než je použijete k sestavení modelu Machine Learning. Podrobnější seznam a popis transformací textu najdete na [stránce transformace](../resources/transforms.md) .

Použití dat, jako jsou následující data, která byla načtena do [`IDataView`](xref:Microsoft.ML.IDataView):

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

Minimální krok pro převod textu na číselnou vektorovou reprezentaci je použití metody [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) . Když použijete [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transformaci, na vstupní textový sloupec se aplikuje řada transformací, což má za následek numerické vektory, které představují lineární-normalizované slovo a znak ngrams.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Výsledná transformace by převedla textové hodnoty ve sloupci `Description` na číselný vektor, který vypadá podobně jako výstup níže:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Kombinováním složitých kroků zpracování textu do [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) odebrat šum a případně snížit množství potřebných prostředků pro zpracování podle potřeby.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` obsahuje podmnožinu operací prováděných metodou [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) . Výhodou složitějšího kanálu je řízení a viditelnost při transformaci aplikovaných na data.

Pomocí první položky jako příklad se jedná o podrobný popis výsledků vyprodukovaných kroky transformace, které definuje `textEstimator`:

**Původní text: Jedná se o dobrý produkt.**

|Transformace | Popis | Výsledek
|--|--|--|
|1. NormalizeText | Ve výchozím nastavení převede všechna písmena na malá. | Toto je dobrý produkt
|2. TokenizeWords | Rozdělí řetězec na jednotlivá slova. | ["This", "is", "a", "Dobrá", "Product"]
|3. RemoveDefaultStopWords | Odebere stopslova jako *je* a *.* | ["dobré", "produkt"]
|4. MapValueToKey | Mapuje hodnoty na klíče (kategorie) na základě vstupních dat. |  [1, 2]
|5. ProduceNGrams | Transformuje text na posloupnost po sobě jdoucích slov. | [1, 1, 1, 0, 0]
|6. NormalizeLpNorm | Škálování vstupů podle jejich LP-normy | [0,577350529, 0,577350529, 0,577350529, 0, 0]
