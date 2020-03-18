---
title: Příprava dat pro sestavení modelu
description: Naučte se používat transformace v ML.NET k manipulaci a přípravě dat pro další zpracování nebo vytváření modelů.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452984"
---
# <a name="prepare-data-for-building-a-model"></a>Příprava dat pro sestavení modelu

Přečtěte si, jak pomocí ML.NET připravit data pro další zpracování nebo sestavení modelu.

Data jsou často nečistá a řídká. ML.NET algoritmy strojového učení očekávají, že vstup nebo funkce budou v jediném číselném vektoru. Podobně hodnota předpovědět (popisek), zejména pokud je kategorická data, musí být kódována. Proto je jedním z cílů přípravy dat dostat data do formátu očekávaného ML.NET algoritmy.

## <a name="filter-data"></a>Filtrování dat

Někdy nejsou všechna data v datové sadě relevantní pro analýzu. Přístup k odstranění irelevantní data je filtrování. Obsahuje [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) sadu operací filtru, které [`IDataView`](xref:Microsoft.ML.IDataView) se v obsahující všechna data a vrátit [IDataView](xref:Microsoft.ML.IDataView) obsahující pouze datové body zájmu. Je důležité si uvědomit, [`IEstimator`](xref:Microsoft.ML.IEstimator%601) že vzhledem [`ITransformer`](xref:Microsoft.ML.ITransformer) k tomu, že operace filtru nejsou nebo se jim líbí v [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)aplikaci , nemohou být zahrnuty jako součást kanálu přípravy dat [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) jejich příprava.

Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:

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

Chcete-li filtrovat data na základě [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) hodnoty sloupce, použijte metodu.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Výše uvedená ukázka přebírá řádky v datové sadě s cenou mezi 200000 a 1000000. Výsledek použití tohoto filtru by vrátil pouze poslední dva řádky v datech a vyloučil první řádek, protože jeho cena je 100000 a nikoli mezi zadaným rozsahem.

## <a name="replace-missing-values"></a>Nahradit chybějící hodnoty

Chybějící hodnoty jsou běžným výskytem v datových sadách. Jedním z přístupů k řešení chybějících hodnot je nahradit je výchozí hodnotou pro daný typ, pokud některá nebo jiná smysluplná hodnota, například střední hodnota v datech.

Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:

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

Všimněte si, že poslední prvek v `Price`našem seznamu má chybějící hodnotu pro . Chcete-li nahradit chybějící `Price` hodnoty ve [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) sloupci, použijte metodu k vyplnění této chybějící hodnoty.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)pracuje pouze s číselnými daty.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET podporuje různé [režimy výměny](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Výše uvedený příklad `Mean` používá režim nahrazení, který vyplní chybějící hodnotu průměrnou hodnotou tohoto sloupce. Výsledek nahrazení vyplní `Price` vlastnost pro poslední prvek v našich datech 200 000, protože je to průměr 100 000 a 300 000.

## <a name="use-normalizers"></a>Použití normalizátorů

[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) je technika předběžného zpracování dat používaná k škálování prvků ve stejném rozsahu, obvykle mezi 0 a 1, aby mohly být přesněji zpracovány algoritmem strojového učení. Například, rozsahy pro věk a příjem se výrazně liší s věkem obecně v rozmezí 0-100 a příjem obecně je v rozmezí od nuly do tisíců. Navštivte [stránku transformací](../resources/transforms.md) pro podrobnější seznam a popis normalizačních transformací.

### <a name="min-max-normalization"></a>Normalizace Min-Max

Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:

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

Normalizaci lze použít na sloupce s jednotlivými číselnými hodnotami i vektory. Normalizovat data `Price` ve sloupci pomocí min-max normalizace s [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) metodou.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Původní cenové `[200000,100000]` hodnoty jsou `[ 1, 0.5 ]` převedeny `MinMax` na použití normalizačního vzorce, který generuje výstupní hodnoty v rozsahu 0-1.

### <a name="binning"></a>Binning

[Binning](https://en.wikipedia.org/wiki/Data_binning) převede spojité hodnoty na diskrétní reprezentaci vstupu. Předpokládejme například, že jednou z vašich funkcí je věk. Namísto použití skutečné věkové hodnoty binning vytvoří rozsahy pro tuto hodnotu. 0-18 by mohla být jedna nádoba, další by mohla být 19-35 a tak dále.

Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:

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

Normalizujte data do [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) přihrádek pomocí metody. Parametr `maximumBinCount` umožňuje zadat počet přihrádek potřebných ke klasifikaci dat. V tomto příkladu budou data vložena do dvou přihrádek.

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Výsledek binning vytvoří hranice bin `[0,200000,Infinity]`. Výsledné přihrádky `[0,1,1]` jsou proto, že první pozorování je mezi 0-200000 a ostatní jsou větší než 200000, ale menší než nekonečno.

## <a name="work-with-categorical-data"></a>Práce s kategorickými daty

Jedním z nejběžnějších typů dat jsou kategorická data. Kategorická data mají konečný počet kategorií. Například státy USA nebo seznam typů zvířat nalezených v sadě obrázků. Bez ohledu na to, zda jsou kategorická data prvky nebo popisky, musí být mapována na číselnou hodnotu, aby je bylo možné použít ke generování modelu strojového učení. Existuje několik způsobů práce s kategorickými daty v ML.NET, v závislosti na problému, který řešíte.

### <a name="key-value-mapping"></a>Mapování klíčových hodnot

V ML.NET je klíč celá hodnota, která představuje kategorii. Mapování hodnot klíče se nejčastěji používá k mapování popisků řetězců na jedinečné celé hodnoty pro trénování a pak zpět na jejich hodnoty řetězců, když se model používá k vytvoření předpovědi.

Transformace používané k provádění mapování hodnot klíče jsou [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) a [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey`přidá slovník mapování v modelu, takže `MapKeyToValue` můžete provést reverzní transformace při vytváření předpověď.

### <a name="one-hot-encoding"></a>Jedno horké kódování

Jedno horké kódování přebírá omezenou sadu hodnot a mapuje je na celá čísla, jejichž binární reprezentace má jednu `1` hodnotu v jedinečných pozicích v řetězci. Jedno horké kódování může být nejlepší volbou, pokud neexistuje žádné implicitní řazení kategorických dat. V následující tabulce je uveden příklad s PSČ jako nezpracovanými hodnotami.

|Nezpracovaná hodnota|Jedna za tepla kódovaná hodnota|
|---------|---------------------|
|98052|00...01|
|98100|00...10|
|...|...|
|98109|10...00|

Transformace pro převod kategorických dat na jedno-horké kódovaná čísla je [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).

### <a name="hashing"></a>Hash

Hash je další způsob, jak převést kategorická data na čísla. Funkce hash mapuje data libovolné velikosti (například řetězec textu) na číslo s pevným rozsahem. Hash může být rychlý a prostorově efektivní způsob vektorizace prvků. Jedním z pozoruhodných příkladů hašování ve strojovém učení je filtrování nevyžádané pošty, kde namísto udržování slovníku známých slov je každé slovo v e-mailu zatříděno a přidáno do vektoru velkých funkcí. Použití hash tímto způsobem se vyhýbá problému škodlivého filtrování nevyžádané pošty obcházení pomocí slov, která nejsou ve slovníku.

ML.NET poskytuje transformaci [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) k provedení hash na text, data a číselná data. Podobně jako mapování hodnotového klíče jsou výstupy transformace hash typy klíčů.

## <a name="work-with-text-data"></a>Práce s textovými daty

Stejně jako kategorická data je třeba textová data transformovat do číselných funkcí před použitím k vytvoření modelu strojového učení. Podrobnější seznam a popis textových transformací naleznete na [stránce transformací.](../resources/transforms.md)

Použití dat, jako jsou níže uvedená data, která byla načtena do aplikace [`IDataView`](xref:Microsoft.ML.IDataView):

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

ML.NET poskytuje [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformaci, která přebírá hodnotu řetězce textu a vytváří sadu prvků z textu použitím řady jednotlivých transformací.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Výsledná transformace převede textové hodnoty `Description` ve sloupci na číselný vektor, který vypadá podobně jako výstup níže:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Transformace, které tvoří `FeaturizeText` lze také použít jednotlivě pro jemnější kontrolu zrnitosti nad generování prvku.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`obsahuje podmnožinu operací [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) prováděných metodou. Výhodou složitějšího kanálu je řízení a viditelnost nad transformacemi použitými pro data.

Jako příklad použijete první položku a následuje podrobný popis výsledků provedených `textEstimator`transformačními kroky definovanými :

**Původní text: Jedná se o dobrý produkt**

|Transformace | Popis | Výsledek
|--|--|--|
|1. NormalizeText | Ve výchozím nastavení převede všechna písmena na malá písmena. | to je dobrý produkt
|2. TokenizeWords | Rozdělí řetězec na jednotlivá slova. | ["to","je","a",dobré",produkt"]
|3. RemoveDefaultStopWords | Odstraňuje stopwords jako *je* *a*. | ["dobrý",produkt"]
|4. MapValueToKey | Mapuje hodnoty na klíče (kategorie) na základě vstupních dat |  [1,2]
|5. ProduktyNGrams | Transformuje text do posloupnosti po sobě jdoucích slov. | [1,1,1,0,0]
|6. NormalizeLpNorm | Škálování vstupů podle jejich lp-normy | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
