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
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="e0a4e-103">Příprava dat pro vytvoření modelu</span><span class="sxs-lookup"><span data-stu-id="e0a4e-103">Prepare data for building a model</span></span>

<span data-ttu-id="e0a4e-104">Naučte se používat ML.NET k přípravě dat pro další zpracování nebo vytvoření modelu.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="e0a4e-105">Data často nejsou čistá a zhuštěná.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="e0a4e-106">Algoritmy strojového učení ML.NET očekávají zadání nebo funkce v jednom numerickém vektoru.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="e0a4e-107">Podobně hodnota pro předpověď (Label), zejména v případě, že je kategorií data, musí být kódována.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="e0a4e-108">Proto je jedním z cílů přípravy dat získat data do formátu očekávaného ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="e0a4e-109">Filtrovat data</span><span class="sxs-lookup"><span data-stu-id="e0a4e-109">Filter data</span></span>

<span data-ttu-id="e0a4e-110">V některých případech nejsou všechna data v datové sadě relevantní pro účely analýzy.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="e0a4e-111">Přístup k odebrání nerelevantních dat je filtrování.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="e0a4e-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) obsahuje sadu operací filtrování, které přebírají [`IDataView`](xref:Microsoft.ML.IDataView) obsahující všechna data a vracejí [IDataView](xref:Microsoft.ML.IDataView) obsahující jenom datové body, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="e0a4e-113">Je důležité si uvědomit, že protože operace filtru nejsou [`IEstimator`](xref:Microsoft.ML.IEstimator%601) nebo [`ITransformer`](xref:Microsoft.ML.ITransformer) jako ty v [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), nedají se zahrnout jako součást [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) kanálu pro přípravu dat.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="e0a4e-114">Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:</span><span class="sxs-lookup"><span data-stu-id="e0a4e-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e0a4e-115">Chcete-li filtrovat data na základě hodnoty sloupce, použijte metodu [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) .</span><span class="sxs-lookup"><span data-stu-id="e0a4e-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="e0a4e-116">Výše uvedená ukázka v datové sadě bere řádky s cenou mezi 200000 a 1000000.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="e0a4e-117">Výsledek použití tohoto filtru vrátí jenom poslední dva řádky v datech a vyloučí první řádek, protože jeho cena je 100000 a ne mezi zadaným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="e0a4e-118">Nahradit chybějící hodnoty</span><span class="sxs-lookup"><span data-stu-id="e0a4e-118">Replace missing values</span></span>

<span data-ttu-id="e0a4e-119">Chybějící hodnoty jsou běžné výskyty v datových sadách.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="e0a4e-120">Jediným způsobem, jak řešit chybějící hodnoty, je nahradit je výchozí hodnotou pro daný typ, pokud kteroukoli nebo jinou smysluplnou hodnotu, například střední hodnotu v datech.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="e0a4e-121">Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:</span><span class="sxs-lookup"><span data-stu-id="e0a4e-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e0a4e-122">Všimněte si, že poslední prvek v našem seznamu má chybějící hodnotu pro `Price`.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="e0a4e-123">Chcete-li nahradit chybějící hodnoty ve sloupci `Price`, použijte metodu [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) k vyplnění chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0a4e-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) funguje pouze s numerickými daty.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="e0a4e-125">ML.NET podporuje různé [režimy nahrazení](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="e0a4e-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="e0a4e-126">Výše uvedená ukázka používá režim nahrazení `Mean`, který v chybějící hodnotě vyplní průměrnou hodnotu tohoto sloupce.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="e0a4e-127">Výsledek nahrazení vyplní vlastnost `Price` pro poslední prvek v datech s 200 000, protože se jedná o průměr 100 000 a 300 000.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="e0a4e-128">Použít normalizy</span><span class="sxs-lookup"><span data-stu-id="e0a4e-128">Use normalizers</span></span>

<span data-ttu-id="e0a4e-129">[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) je postup předběžného zpracování dat, který se používá k horizontálnímu navýšení kapacity funkcí, a to obvykle mezi 0 a 1, aby bylo možné přesněji zpracovat algoritmus strojového učení.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="e0a4e-130">Například rozsahy pro věk a příjem se výrazně liší v rozsahu 0-100 a výnosy se obecně nacházejí v rozsahu od 0 do tisíců.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="e0a4e-131">Podrobnější seznam a popis transformací normalizace najdete na [stránce transformace](../resources/transforms.md) .</span><span class="sxs-lookup"><span data-stu-id="e0a4e-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="e0a4e-132">Normalizace min-max</span><span class="sxs-lookup"><span data-stu-id="e0a4e-132">Min-Max normalization</span></span>

<span data-ttu-id="e0a4e-133">Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:</span><span class="sxs-lookup"><span data-stu-id="e0a4e-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e0a4e-134">Normalizace se dá použít na sloupce s jednou číselnou hodnotou i vektory.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="e0a4e-135">Normalizuje data ve sloupci `Price` pomocí normalizace min-max s metodou [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) .</span><span class="sxs-lookup"><span data-stu-id="e0a4e-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="e0a4e-136">Původní cenové hodnoty `[200000,100000]` jsou převedeny na `[ 1, 0.5 ]` pomocí vzorce `MinMax` normalizace, který generuje výstupní hodnoty v rozsahu 0-1.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="e0a4e-137">Binningu</span><span class="sxs-lookup"><span data-stu-id="e0a4e-137">Binning</span></span>

<span data-ttu-id="e0a4e-138">[Binningu](https://en.wikipedia.org/wiki/Data_binning) převádí souvislé hodnoty do diskrétní reprezentace vstupu.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="e0a4e-139">Předpokládejme například, že jedna z vašich funkcí je věková.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="e0a4e-140">Místo použití skutečné věkové hodnoty binningu vytvoří rozsahy pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="e0a4e-141">0-18 může být jedna přihrádka, další by mohla být 19-35 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="e0a4e-142">Proveďte následující vstupní data a načtěte je do [`IDataView`](xref:Microsoft.ML.IDataView) s názvem `data`:</span><span class="sxs-lookup"><span data-stu-id="e0a4e-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e0a4e-143">Normalizuje data do přihrádek pomocí metody [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) .</span><span class="sxs-lookup"><span data-stu-id="e0a4e-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="e0a4e-144">Parametr `maximumBinCount` umožňuje zadat počet přihrádek potřebných ke klasifikaci vašich dat.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="e0a4e-145">V tomto příkladu budou data vložena do dvou přihrádek.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="e0a4e-146">Výsledek binningu vytvoří meze přihrádky `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="e0a4e-147">Proto jsou výsledné přihrádky `[0,1,1]`, protože první pozorování je mezi 0-200000 a ostatní jsou větší než 200000, ale menší než nekonečno.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="e0a4e-148">Práce s kategorií daty</span><span class="sxs-lookup"><span data-stu-id="e0a4e-148">Work with categorical data</span></span>

<span data-ttu-id="e0a4e-149">Jedním z nejběžnějších typů dat je kategorií dat.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="e0a4e-150">Data kategorií mají omezený počet kategorií.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="e0a4e-151">Například stavy USA nebo seznam typů zvířat, které se nacházejí v sadě obrázků.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="e0a4e-152">Bez ohledu na to, jestli kategorií data jsou funkce nebo popisky, musí být namapovány na číselnou hodnotu, aby se mohly použít k vygenerování modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="e0a4e-153">Existuje mnoho způsobů, jak v ML.NET pracovat s kategorií daty v závislosti na zjištěném problému.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="e0a4e-154">Mapování hodnot klíčů</span><span class="sxs-lookup"><span data-stu-id="e0a4e-154">Key value mapping</span></span>

<span data-ttu-id="e0a4e-155">V ML.NET je klíč celočíselná hodnota, která představuje kategorii.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="e0a4e-156">Mapování hodnot klíče se nejčastěji používá k mapování popisků řetězců na jedinečné celočíselné hodnoty pro školení a pak k jejich řetězcovým hodnotám, když se model používá k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="e0a4e-157">Transformace používané k mapování hodnot klíčů jsou [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) a [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="e0a4e-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="e0a4e-158">`MapValueToKey` přidá do modelu slovník mapování, aby `MapKeyToValue` při vytváření předpovědi mohl provést zpětnou transformaci.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="e0a4e-159">Jedno horké kódování</span><span class="sxs-lookup"><span data-stu-id="e0a4e-159">One hot encoding</span></span>

<span data-ttu-id="e0a4e-160">Jedno horké kódování používá konečnou sadu hodnot a mapuje je na celá čísla, jejichž binární reprezentace má jednu `1` hodnotu v jedinečných pozicích v řetězci.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="e0a4e-161">Pokud není k dispozici žádné implicitní řazení dat kategorií, může být jedním z aktivních kódování nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="e0a4e-162">Následující tabulka ukazuje příklad s PSČ jako nezpracované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="e0a4e-163">Nezpracovaná hodnota</span><span class="sxs-lookup"><span data-stu-id="e0a4e-163">Raw value</span></span>|<span data-ttu-id="e0a4e-164">Jedna Hot kódovaná hodnota</span><span class="sxs-lookup"><span data-stu-id="e0a4e-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="e0a4e-165">98052</span><span class="sxs-lookup"><span data-stu-id="e0a4e-165">98052</span></span>|<span data-ttu-id="e0a4e-166">00... 01</span><span class="sxs-lookup"><span data-stu-id="e0a4e-166">00...01</span></span>|
|<span data-ttu-id="e0a4e-167">98100</span><span class="sxs-lookup"><span data-stu-id="e0a4e-167">98100</span></span>|<span data-ttu-id="e0a4e-168">00... 10</span><span class="sxs-lookup"><span data-stu-id="e0a4e-168">00...10</span></span>|
|<span data-ttu-id="e0a4e-169">Tlačítka ...</span><span class="sxs-lookup"><span data-stu-id="e0a4e-169">...</span></span>|<span data-ttu-id="e0a4e-170">Tlačítka ...</span><span class="sxs-lookup"><span data-stu-id="e0a4e-170">...</span></span>|
|<span data-ttu-id="e0a4e-171">98109</span><span class="sxs-lookup"><span data-stu-id="e0a4e-171">98109</span></span>|<span data-ttu-id="e0a4e-172">10... 00</span><span class="sxs-lookup"><span data-stu-id="e0a4e-172">10...00</span></span>|

<span data-ttu-id="e0a4e-173">Transformace, která převádí kategorií data na číslo s jednou horkou, je [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span><span class="sxs-lookup"><span data-stu-id="e0a4e-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="e0a4e-174">Hash</span><span class="sxs-lookup"><span data-stu-id="e0a4e-174">Hashing</span></span>

<span data-ttu-id="e0a4e-175">Generování hodnoty hash je další způsob, jak převést data kategorií na čísla.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="e0a4e-176">Funkce hash mapuje data libovolné velikosti (například řetězec textu) na číslo s pevným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="e0a4e-177">Hashování může být rychlý a prostorově efektivní způsob funkcí vektorizace.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="e0a4e-178">Mezi významné příklady hashování ve službě Machine Learning je e-mailové filtrování nevyžádané pošty tam, kde místo udržování slovníku známých slov se pro každé slovo v e-mailu používá hash a přidávají se k velkému vektoru funkcí.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="e0a4e-179">Pomocí hashování tímto způsobem se vyhnete problému obcházení škodlivého filtru nevyžádané pošty pomocí slov, která nejsou ve slovníku.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="e0a4e-180">ML.NET poskytuje transformaci [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) k provádění hashování pro text, kalendářní data a číselná data.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="e0a4e-181">Podobně jako mapování klíče hodnoty jsou výstupy transformace hash typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="e0a4e-182">Práce s textovými daty</span><span class="sxs-lookup"><span data-stu-id="e0a4e-182">Work with text data</span></span>

<span data-ttu-id="e0a4e-183">Podobně jako kategorií data je třeba textová data transformovat na číselné funkce, než je použijete k sestavení modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="e0a4e-184">Podrobnější seznam a popis transformací textu najdete na [stránce transformace](../resources/transforms.md) .</span><span class="sxs-lookup"><span data-stu-id="e0a4e-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="e0a4e-185">Použití dat, jako jsou následující data, která byla načtena do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="e0a4e-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="e0a4e-186">ML.NET poskytuje [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformaci, která přebírá řetězcovou hodnotu textu a vytváří sadu funkcí z textu, a to použitím řady jednotlivých transformací.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="e0a4e-187">Výsledná transformace převede textové hodnoty ve sloupci `Description` na číselný vektor, který vypadá podobně jako výstup níže:</span><span class="sxs-lookup"><span data-stu-id="e0a4e-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="e0a4e-188">Transformace, které tvoří `FeaturizeText`, se dají použít i samostatně pro lepší kontrolu nad generováním funkcí.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="e0a4e-189">`textEstimator` obsahuje podmnožinu operací prováděných metodou [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) .</span><span class="sxs-lookup"><span data-stu-id="e0a4e-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="e0a4e-190">Výhodou složitějšího kanálu je řízení a viditelnost při transformaci aplikovaných na data.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="e0a4e-191">Pomocí první položky jako příklad se jedná o podrobný popis výsledků vyprodukovaných kroky transformace, které definuje `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="e0a4e-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="e0a4e-192">**Původní text: Jedná se o dobrý produkt.**</span><span class="sxs-lookup"><span data-stu-id="e0a4e-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="e0a4e-193">Transformace</span><span class="sxs-lookup"><span data-stu-id="e0a4e-193">Transform</span></span> | <span data-ttu-id="e0a4e-194">Popis</span><span class="sxs-lookup"><span data-stu-id="e0a4e-194">Description</span></span> | <span data-ttu-id="e0a4e-195">Výsledek</span><span class="sxs-lookup"><span data-stu-id="e0a4e-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="e0a4e-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="e0a4e-196">1. NormalizeText</span></span> | <span data-ttu-id="e0a4e-197">Ve výchozím nastavení převede všechna písmena na malá.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="e0a4e-198">Toto je dobrý produkt</span><span class="sxs-lookup"><span data-stu-id="e0a4e-198">this is a good product</span></span>
|<span data-ttu-id="e0a4e-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="e0a4e-199">2. TokenizeWords</span></span> | <span data-ttu-id="e0a4e-200">Rozdělí řetězec na jednotlivá slova.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-200">Splits string into individual words</span></span> | <span data-ttu-id="e0a4e-201">["This", "is", "a", "Dobrá", "Product"]</span><span class="sxs-lookup"><span data-stu-id="e0a4e-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="e0a4e-202">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="e0a4e-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="e0a4e-203">Odebere stopslova jako *je* a *.*</span><span class="sxs-lookup"><span data-stu-id="e0a4e-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="e0a4e-204">["dobré", "produkt"]</span><span class="sxs-lookup"><span data-stu-id="e0a4e-204">["good","product"]</span></span>
|<span data-ttu-id="e0a4e-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="e0a4e-205">4. MapValueToKey</span></span> | <span data-ttu-id="e0a4e-206">Mapuje hodnoty na klíče (kategorie) na základě vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="e0a4e-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="e0a4e-207">[1,2]</span></span>
|<span data-ttu-id="e0a4e-208">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="e0a4e-208">5. ProduceNGrams</span></span> | <span data-ttu-id="e0a4e-209">Transformuje text na posloupnost po sobě jdoucích slov.</span><span class="sxs-lookup"><span data-stu-id="e0a4e-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="e0a4e-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="e0a4e-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="e0a4e-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="e0a4e-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="e0a4e-212">Škálování vstupů podle jejich LP-normy</span><span class="sxs-lookup"><span data-stu-id="e0a4e-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="e0a4e-213">[0,577350529, 0,577350529, 0,577350529, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="e0a4e-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
