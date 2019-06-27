---
title: Příprava dat pro vytvoření modelu
description: Další informace o použití transformace v ML.NET k manipulaci a připravit data pro další zpracování nebo model vytváření.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/25/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4b7d5a09044e49f1b57b8276b893e0fc962a3be2
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397723"
---
# <a name="prepare-data-for-building-a-model"></a>Příprava dat pro vytvoření modelu

Další informace o použití ML.NET připravit data pro další zpracování nebo vytváření modelu.

Data jsou často musí provést a zhuštěné. Kromě toho algoritmů strojového učení ML.NET očekávat, že vstup nebo funkce, které chcete být v jedné číselné vektoru. Proto je jedním z cílů přípravu dat jak dostat data do formátu očekávaném ML.NET algoritmy. 

## <a name="filter-data"></a>Filtrování dat

V některých případech je relevantní pro analýzu nejsou všechna data v datové sadě. Přístup k odebrání nahromadění irelevantních dat je filtrování. [ `DataOperationsCatalog` ](xref:Microsoft.ML.DataOperationsCatalog) Obsahuje sadu filtr operací, které trvat, než se [ `IDataView` ](xref:Microsoft.ML.IDataView) obsahující všechny data a vraťte se [IDataView](xref:Microsoft.ML.IDataView) obsahující pouze datové body, které vás zajímají. Je důležité si uvědomit, že vzhledem k tomu, že operace filtru nejsou [ `IEstimator` ](xref:Microsoft.ML.IEstimator%601) nebo [ `ITransformer` ](xref:Microsoft.ML.ITransformer) jako ty v [ `TransformsCatalog` ](xref:Microsoft.ML.TransformsCatalog), nemůže být zahrnutý jako součást [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [ `TransformerChain` ](xref:Microsoft.ML.Data.TransformerChain%601) datovým kanálem přípravy. 

Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Chcete-li filtrovat data na základě hodnoty sloupce, použijte [ `FilterRowsByColumn` ](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metody.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Příkladu výše má řádky v datové sadě s cenou mezi 200000 až 1 000 000. Výsledek použití tohoto filtru by vrátit pouze poslední dva řádky v datech a vyloučit první řádek vzhledem k tomu, že cena je 100000 a není mezi zadaného rozsahu.

## <a name="replace-missing-values"></a>Nahraďte chybějící hodnoty

Chybějící hodnoty jsou společného výskytu v datových sadách. Je jedním z přístupů k práci s chybějící hodnoty nahradit výchozí hodnotu pro daný typ, pokud všechny nebo jiné smysluplnou hodnotu, jako je střední hodnota v datech. 

Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Všimněte si, že po posledním prvku v seznamu má chybí hodnota pro `Price`. Nahradit chybějící hodnoty v `Price` sloupců, použijte [ `ReplaceMissingValues` ](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) metoda vyplnit tento chybí hodnota.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) fungují jenom s číselnými daty.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET podporuje různé [nahrazení režimy](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Ukázka výše používá `Mean` nahrazení režimu, který vyplní chybějící hodnoty s průměrnou hodnotu tohoto sloupce. Vyplní výsledek nahrazení `Price` vlastnost po posledním prvku v našich dat s 200 000, protože je průměrem 100 000 a 300 000. 

## <a name="use-normalizers"></a>Použití normalizers

[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) jsou data předběžného zpracování techniku použít ke standardizaci funkce, které nejsou ve stejném měřítku, která pomáhá algoritmy sloučit rychleji. Například rozsahy pro hodnoty jako věku a příjmů výrazně liší stářím obecně se v rozsahu od 0 do 100 a příjmu, obecně je v rozsahu 0 až po tisíce. Přejděte [transformace stránky](../resources/transforms.md) podrobnější seznam a popis normalizace transformací. 

### <a name="min-max-normalization"></a>Normalizace maximálních

Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Normalizaci lze použít pro sloupce s jednu číselnou hodnotu, jakož i vektorů. Normalizovat data v `Price` sloupce pomocí maximálních normalizace s [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) metody.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Původní hodnoty cena `[200000,100000]` jsou převedeny na `[ 1, 0.5 ]` pomocí `MinMax` normalizace vzorec, který generuje výstupní hodnoty v rozmezí 0 – 1.

### <a name="binning"></a>Binning

[Binning](https://en.wikipedia.org/wiki/Data_binning) převede průběžné hodnoty na samostatných reprezentace vstupu. Předpokládejme například, že jednou z vašich funkcí je věk. Místo hodnoty skutečné stáří binning vytvoří rozsahy pro tuto hodnotu. 0 – 18 může být jeden bin, jiné mohou být 19 35 a tak dále. 

Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Normalizovat data do přihrádek pomocí [ `NormalizeBinning` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody. `maximumBinCount` Parametr umožňuje určit počet intervalů, které jsou potřeba ke klasifikaci dat. V tomto příkladu data zařadí do dva přihrádky.  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Vytvoří výsledek binning bin hranice `[0,200000,Infinity]`. Proto je výsledný přihrádky `[0,1,1]` protože první zjišťování je mezi 0-200000 a ostatní jsou větší než 200 000, ale menší než nekonečno.

## <a name="work-with-categorical-data"></a>Práce s data zařazená do kategorií

Data zařazená do kategorií nečíselné musí být převeden na číslo před použitím sestavit model strojového učení. 

Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Kategorií `VehicleType` vlastnosti mohou být převedeny na čísla pomocí [ `OneHotEncoding` ](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) metody. 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

Výsledný transformace převede textovou hodnotu `VehicleType` na číslo. Položky `VehicleType` sloupce se následující, když je použita transformace: 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Práce s daty text

Textová data nutné transformovat na čísla před sestavením model strojového učení. Přejděte [transformace stránky](../resources/transforms.md) podrobnější seznam a popis transformace textu.

Pomocí dat, jako je následující, která data se načetl do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Minimální krokem pro převod textu na reprezentace číselné vektoru je použití [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody. S použitím [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) vstupního textového sloupce, výsledkem je číselná vektor představující lp normalized slovo, znak ngrams je použita transformace, řadu transformací. 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Výsledný transformace textové hodnoty v převede `Description` sloupců na číselný vektoru, který vypadá podobně jako následující výstup:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Kroky zpracování složitých text se sloučí do [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) odebrat šumu a potenciálně snížili množství množství požadovaný výpočetní prostředky podle potřeby.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` obsahuje podmnožinu operace provedené [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody. Výhodou složitější kanálu je řízení a viditelnost přes transformaci na data. 

Jako příklad použijeme první položka, tady je podrobný popis výsledky vytvořené metodou kroky transformace určené `textEstimator`:

**Původní Text: To je dobrý produktu**

|Transformace | Popis | Výsledek
|--|--|--|
|1. NormalizeText | Převede všechna písmena na malá písmena ve výchozím nastavení | To je dobrý produktu
|2. TokenizeWords | Rozdělí řetězec do jednotlivých slov | ["Tento", "je", "";"Dobrá","produkt"]
|3. RemoveDefaultStopWords | Odebere stopword jako *je* *a*. | ["good","product"]
|4. MapValueToKey | Mapuje hodnoty klíče (kategorie) na základě vstupních dat |  [1,2]
|5. ProduceNGrams | Transformuje text do sekvence po sobě jdoucích slov | [1,1,1,0,0]
|6. NormalizeLpNorm | Vstupy škálování podle jejich lp norm | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
