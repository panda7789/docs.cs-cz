---
title: Příprava dat pro vytvoření modelu
description: Naučte se používat transformace v ML.NET k manipulaci a přípravě dat pro další zpracování nebo vytváření modelů.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452984"
---
# <a name="prepare-data-for-building-a-model"></a>Příprava dat pro vytvoření modelu

Naučte se používat ML.NET k přípravě dat pro další zpracování nebo vytvoření modelu.

Data často nejsou čistá a zhuštěná. Algoritmy strojového učení ML.NET očekávají zadání nebo funkce v jednom numerickém vektoru. Podobně hodnota pro předpověď (Label), zejména v případě, že je kategorií data, musí být kódována. Proto je jedním z cílů přípravy dat získat data do formátu očekávaného ML.NET algoritmy.

## <a name="filter-data"></a>Filtrovat data

V některých případech nejsou všechna data v datové sadě relevantní pro účely analýzy. Přístup k odebrání nerelevantních dat je filtrování. [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) obsahuje sadu operací filtrování, které přebírají [`IDataView`](xref:Microsoft.ML.IDataView) obsahující všechna data a vracejí [IDataView](xref:Microsoft.ML.IDataView) obsahující jenom datové body, které vás zajímají. Je důležité si uvědomit, že protože operace filtru nejsou [`IEstimator`](xref:Microsoft.ML.IEstimator%601) nebo [`ITransformer`](xref:Microsoft.ML.ITransformer) jako ty v [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), nedají se zahrnout jako součást [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) kanálu pro přípravu dat.

Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:

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

Chcete-li filtrovat data na základě hodnoty sloupce, použijte metodu [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) .

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Výše uvedená ukázka v datové sadě bere řádky s cenou mezi 200000 a 1000000. Výsledek použití tohoto filtru vrátí jenom poslední dva řádky v datech a vyloučí první řádek, protože jeho cena je 100000 a ne mezi zadaným rozsahem.

## <a name="replace-missing-values"></a>Nahradit chybějící hodnoty

Chybějící hodnoty jsou běžné výskyty v datových sadách. Jediným způsobem, jak řešit chybějící hodnoty, je nahradit je výchozí hodnotou pro daný typ, pokud kteroukoli nebo jinou smysluplnou hodnotu, například střední hodnotu v datech.

Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:

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

Všimněte si, že poslední prvek v našem seznamu má chybějící hodnotu pro `Price`. Chcete-li nahradit chybějící hodnoty ve sloupci `Price`, použijte metodu [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) k vyplnění chybějící hodnoty.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) funguje pouze s numerickými daty.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET podporuje různé [režimy nahrazení](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Výše uvedená ukázka používá režim nahrazení `Mean`, který v chybějící hodnotě vyplní průměrnou hodnotu tohoto sloupce. Výsledek nahrazení vyplní vlastnost `Price` pro poslední prvek v datech s 200 000, protože se jedná o průměr 100 000 a 300 000.

## <a name="use-normalizers"></a>Použít normalizy

[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) je postup předběžného zpracování dat, který se používá k horizontálnímu navýšení kapacity funkcí, a to obvykle mezi 0 a 1, aby bylo možné přesněji zpracovat algoritmus strojového učení. Například rozsahy pro věk a příjem se výrazně liší v rozsahu 0-100 a výnosy se obecně nacházejí v rozsahu od 0 do tisíců. Podrobnější seznam a popis transformací normalizace najdete na [stránce transformace](../resources/transforms.md) .

### <a name="min-max-normalization"></a>Normalizace min-max

Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:

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

Normalizace se dá použít na sloupce s jednou číselnou hodnotou i vektory. Normalizuje data ve sloupci `Price` pomocí normalizace min-max s metodou [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) .

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

Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:

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

Normalizuje data do přihrádek pomocí metody [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) . Parametr `maximumBinCount` umožňuje zadat počet přihrádek potřebných ke klasifikaci vašich dat. V tomto příkladu budou data vložena do dvou přihrádek.

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

Jedním z nejběžnějších typů dat je kategorií dat. Data kategorií mají omezený počet kategorií. Například stavy USA nebo seznam typů zvířat, které se nacházejí v sadě obrázků. Bez ohledu na to, jestli kategorií data jsou funkce nebo popisky, musí být namapovány na číselnou hodnotu, aby se mohly použít k vygenerování modelu Machine Learning. Existuje mnoho způsobů, jak v ML.NET pracovat s kategorií daty v závislosti na zjištěném problému.

### <a name="key-value-mapping"></a>Mapování hodnot klíčů

V ML.NET je klíč celočíselná hodnota, která představuje kategorii. Mapování hodnot klíče se nejčastěji používá k mapování popisků řetězců na jedinečné celočíselné hodnoty pro školení a pak k jejich řetězcovým hodnotám, když se model používá k vytvoření předpovědi.

Transformace používané k mapování hodnot klíčů jsou [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) a [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey` přidá do modelu slovník mapování, aby `MapKeyToValue` při vytváření předpovědi mohl provést zpětnou transformaci.

### <a name="one-hot-encoding"></a>Jedno horké kódování

Jedno horké kódování používá konečnou sadu hodnot a mapuje je na celá čísla, jejichž binární reprezentace má jednu `1` hodnotu v jedinečných pozicích v řetězci. Pokud není k dispozici žádné implicitní řazení dat kategorií, může být jedním z aktivních kódování nejlepší volbou. Následující tabulka ukazuje příklad s PSČ jako nezpracované hodnoty.

|Nezpracovaná hodnota|Jedna Hot kódovaná hodnota|
|---------|---------------------|
|98052|00... 01|
|98100|00... 10|
|Tlačítka ...|Tlačítka ...|
|98109|10... 00|

Transformace, která převádí kategorií data na číslo s jednou horkou, je [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).

### <a name="hashing"></a>Hash

Generování hodnoty hash je další způsob, jak převést data kategorií na čísla. Funkce hash mapuje data libovolné velikosti (například řetězec textu) na číslo s pevným rozsahem. Hashování může být rychlý a prostorově efektivní způsob funkcí vektorizace. Mezi významné příklady hashování ve službě Machine Learning je e-mailové filtrování nevyžádané pošty tam, kde místo udržování slovníku známých slov se pro každé slovo v e-mailu používá hash a přidávají se k velkému vektoru funkcí. Pomocí hashování tímto způsobem se vyhnete problému obcházení škodlivého filtru nevyžádané pošty pomocí slov, která nejsou ve slovníku.

ML.NET poskytuje transformaci [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) k provádění hashování pro text, kalendářní data a číselná data. Podobně jako mapování klíče hodnoty jsou výstupy transformace hash typy klíčů.

## <a name="work-with-text-data"></a>Práce s textovými daty

Podobně jako kategorií data je třeba textová data transformovat na číselné funkce, než je použijete k sestavení modelu Machine Learning. Podrobnější seznam a popis transformací textu najdete na [stránce transformace](../resources/transforms.md) .

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

ML.NET poskytuje [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformaci, která přebírá řetězcovou hodnotu textu a vytváří sadu funkcí z textu, a to použitím řady jednotlivých transformací.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Výsledná transformace převede textové hodnoty ve sloupci `Description` na číselný vektor, který vypadá podobně jako výstup níže:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Transformace, které tvoří `FeaturizeText`, se dají použít i samostatně pro lepší kontrolu nad generováním funkcí.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` obsahuje podmnožinu operací prováděných metodou [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) . Výhodou složitějšího kanálu je řízení a viditelnost při transformaci aplikovaných na data.

Pomocí první položky jako příklad se jedná o podrobný popis výsledků vyprodukovaných kroky transformace, které definuje `textEstimator`:

**Původní text: Jedná se o dobrý produkt.**

|Transformace | Popis | Výsledek
|--|--|--|
|1. NormalizeText | Ve výchozím nastavení převede všechna písmena na malá. | Toto je dobrý produkt
|2. TokenizeWords | Rozdělí řetězec na jednotlivá slova. | ["This", "is", "a", "Dobrá", "Product"]
|3. RemoveDefaultStopWords | Odebere stopslova jako *je* a *.* | ["dobré", "produkt"]
|4. MapValueToKey | Mapuje hodnoty na klíče (kategorie) na základě vstupních dat. |  [1,2]
|5. ProduceNGrams | Transformuje text na posloupnost po sobě jdoucích slov. | [1,1,1,0,0]
|6. NormalizeLpNorm | Škálování vstupů podle jejich LP-normy | [0,577350529, 0,577350529, 0,577350529, 0, 0]
