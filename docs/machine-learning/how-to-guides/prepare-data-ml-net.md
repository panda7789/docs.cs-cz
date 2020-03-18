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
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="2e8b2-103">Příprava dat pro sestavení modelu</span><span class="sxs-lookup"><span data-stu-id="2e8b2-103">Prepare data for building a model</span></span>

<span data-ttu-id="2e8b2-104">Přečtěte si, jak pomocí ML.NET připravit data pro další zpracování nebo sestavení modelu.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="2e8b2-105">Data jsou často nečistá a řídká.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="2e8b2-106">ML.NET algoritmy strojového učení očekávají, že vstup nebo funkce budou v jediném číselném vektoru.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="2e8b2-107">Podobně hodnota předpovědět (popisek), zejména pokud je kategorická data, musí být kódována.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="2e8b2-108">Proto je jedním z cílů přípravy dat dostat data do formátu očekávaného ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="2e8b2-109">Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="2e8b2-109">Filter data</span></span>

<span data-ttu-id="2e8b2-110">Někdy nejsou všechna data v datové sadě relevantní pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="2e8b2-111">Přístup k odstranění irelevantní data je filtrování.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="2e8b2-112">Obsahuje [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) sadu operací filtru, které [`IDataView`](xref:Microsoft.ML.IDataView) se v obsahující všechna data a vrátit [IDataView](xref:Microsoft.ML.IDataView) obsahující pouze datové body zájmu.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="2e8b2-113">Je důležité si uvědomit, [`IEstimator`](xref:Microsoft.ML.IEstimator%601) že vzhledem [`ITransformer`](xref:Microsoft.ML.ITransformer) k tomu, že operace filtru nejsou nebo se jim líbí v [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)aplikaci , nemohou být zahrnuty jako součást kanálu přípravy dat [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) jejich příprava.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="2e8b2-114">Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:</span><span class="sxs-lookup"><span data-stu-id="2e8b2-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="2e8b2-115">Chcete-li filtrovat data na základě [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) hodnoty sloupce, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="2e8b2-116">Výše uvedená ukázka přebírá řádky v datové sadě s cenou mezi 200000 a 1000000.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="2e8b2-117">Výsledek použití tohoto filtru by vrátil pouze poslední dva řádky v datech a vyloučil první řádek, protože jeho cena je 100000 a nikoli mezi zadaným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="2e8b2-118">Nahradit chybějící hodnoty</span><span class="sxs-lookup"><span data-stu-id="2e8b2-118">Replace missing values</span></span>

<span data-ttu-id="2e8b2-119">Chybějící hodnoty jsou běžným výskytem v datových sadách.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="2e8b2-120">Jedním z přístupů k řešení chybějících hodnot je nahradit je výchozí hodnotou pro daný typ, pokud některá nebo jiná smysluplná hodnota, například střední hodnota v datech.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="2e8b2-121">Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:</span><span class="sxs-lookup"><span data-stu-id="2e8b2-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="2e8b2-122">Všimněte si, že poslední prvek v `Price`našem seznamu má chybějící hodnotu pro .</span><span class="sxs-lookup"><span data-stu-id="2e8b2-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="2e8b2-123">Chcete-li nahradit chybějící `Price` hodnoty ve [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) sloupci, použijte metodu k vyplnění této chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e8b2-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)pracuje pouze s číselnými daty.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="2e8b2-125">ML.NET podporuje různé [režimy výměny](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="2e8b2-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="2e8b2-126">Výše uvedený příklad `Mean` používá režim nahrazení, který vyplní chybějící hodnotu průměrnou hodnotou tohoto sloupce.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="2e8b2-127">Výsledek nahrazení vyplní `Price` vlastnost pro poslední prvek v našich datech 200 000, protože je to průměr 100 000 a 300 000.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="2e8b2-128">Použití normalizátorů</span><span class="sxs-lookup"><span data-stu-id="2e8b2-128">Use normalizers</span></span>

<span data-ttu-id="2e8b2-129">[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) je technika předběžného zpracování dat používaná k škálování prvků ve stejném rozsahu, obvykle mezi 0 a 1, aby mohly být přesněji zpracovány algoritmem strojového učení.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="2e8b2-130">Například, rozsahy pro věk a příjem se výrazně liší s věkem obecně v rozmezí 0-100 a příjem obecně je v rozmezí od nuly do tisíců.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="2e8b2-131">Navštivte [stránku transformací](../resources/transforms.md) pro podrobnější seznam a popis normalizačních transformací.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="2e8b2-132">Normalizace Min-Max</span><span class="sxs-lookup"><span data-stu-id="2e8b2-132">Min-Max normalization</span></span>

<span data-ttu-id="2e8b2-133">Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:</span><span class="sxs-lookup"><span data-stu-id="2e8b2-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="2e8b2-134">Normalizaci lze použít na sloupce s jednotlivými číselnými hodnotami i vektory.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="2e8b2-135">Normalizovat data `Price` ve sloupci pomocí min-max normalizace s [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) metodou.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="2e8b2-136">Původní cenové `[200000,100000]` hodnoty jsou `[ 1, 0.5 ]` převedeny `MinMax` na použití normalizačního vzorce, který generuje výstupní hodnoty v rozsahu 0-1.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="2e8b2-137">Binning</span><span class="sxs-lookup"><span data-stu-id="2e8b2-137">Binning</span></span>

<span data-ttu-id="2e8b2-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) převede spojité hodnoty na diskrétní reprezentaci vstupu.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="2e8b2-139">Předpokládejme například, že jednou z vašich funkcí je věk.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="2e8b2-140">Namísto použití skutečné věkové hodnoty binning vytvoří rozsahy pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="2e8b2-141">0-18 by mohla být jedna nádoba, další by mohla být 19-35 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="2e8b2-142">Vezměte následující vstupní data a [`IDataView`](xref:Microsoft.ML.IDataView) načtěte je do volané `data`:</span><span class="sxs-lookup"><span data-stu-id="2e8b2-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="2e8b2-143">Normalizujte data do [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) přihrádek pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="2e8b2-144">Parametr `maximumBinCount` umožňuje zadat počet přihrádek potřebných ke klasifikaci dat.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="2e8b2-145">V tomto příkladu budou data vložena do dvou přihrádek.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="2e8b2-146">Výsledek binning vytvoří hranice bin `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="2e8b2-147">Výsledné přihrádky `[0,1,1]` jsou proto, že první pozorování je mezi 0-200000 a ostatní jsou větší než 200000, ale menší než nekonečno.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="2e8b2-148">Práce s kategorickými daty</span><span class="sxs-lookup"><span data-stu-id="2e8b2-148">Work with categorical data</span></span>

<span data-ttu-id="2e8b2-149">Jedním z nejběžnějších typů dat jsou kategorická data.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="2e8b2-150">Kategorická data mají konečný počet kategorií.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="2e8b2-151">Například státy USA nebo seznam typů zvířat nalezených v sadě obrázků.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="2e8b2-152">Bez ohledu na to, zda jsou kategorická data prvky nebo popisky, musí být mapována na číselnou hodnotu, aby je bylo možné použít ke generování modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="2e8b2-153">Existuje několik způsobů práce s kategorickými daty v ML.NET, v závislosti na problému, který řešíte.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="2e8b2-154">Mapování klíčových hodnot</span><span class="sxs-lookup"><span data-stu-id="2e8b2-154">Key value mapping</span></span>

<span data-ttu-id="2e8b2-155">V ML.NET je klíč celá hodnota, která představuje kategorii.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="2e8b2-156">Mapování hodnot klíče se nejčastěji používá k mapování popisků řetězců na jedinečné celé hodnoty pro trénování a pak zpět na jejich hodnoty řetězců, když se model používá k vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="2e8b2-157">Transformace používané k provádění mapování hodnot klíče jsou [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) a [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="2e8b2-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="2e8b2-158">`MapValueToKey`přidá slovník mapování v modelu, takže `MapKeyToValue` můžete provést reverzní transformace při vytváření předpověď.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="2e8b2-159">Jedno horké kódování</span><span class="sxs-lookup"><span data-stu-id="2e8b2-159">One hot encoding</span></span>

<span data-ttu-id="2e8b2-160">Jedno horké kódování přebírá omezenou sadu hodnot a mapuje je na celá čísla, jejichž binární reprezentace má jednu `1` hodnotu v jedinečných pozicích v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="2e8b2-161">Jedno horké kódování může být nejlepší volbou, pokud neexistuje žádné implicitní řazení kategorických dat.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="2e8b2-162">V následující tabulce je uveden příklad s PSČ jako nezpracovanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="2e8b2-163">Nezpracovaná hodnota</span><span class="sxs-lookup"><span data-stu-id="2e8b2-163">Raw value</span></span>|<span data-ttu-id="2e8b2-164">Jedna za tepla kódovaná hodnota</span><span class="sxs-lookup"><span data-stu-id="2e8b2-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="2e8b2-165">98052</span><span class="sxs-lookup"><span data-stu-id="2e8b2-165">98052</span></span>|<span data-ttu-id="2e8b2-166">00...01</span><span class="sxs-lookup"><span data-stu-id="2e8b2-166">00...01</span></span>|
|<span data-ttu-id="2e8b2-167">98100</span><span class="sxs-lookup"><span data-stu-id="2e8b2-167">98100</span></span>|<span data-ttu-id="2e8b2-168">00...10</span><span class="sxs-lookup"><span data-stu-id="2e8b2-168">00...10</span></span>|
|<span data-ttu-id="2e8b2-169">...</span><span class="sxs-lookup"><span data-stu-id="2e8b2-169">...</span></span>|<span data-ttu-id="2e8b2-170">...</span><span class="sxs-lookup"><span data-stu-id="2e8b2-170">...</span></span>|
|<span data-ttu-id="2e8b2-171">98109</span><span class="sxs-lookup"><span data-stu-id="2e8b2-171">98109</span></span>|<span data-ttu-id="2e8b2-172">10...00</span><span class="sxs-lookup"><span data-stu-id="2e8b2-172">10...00</span></span>|

<span data-ttu-id="2e8b2-173">Transformace pro převod kategorických dat na jedno-horké kódovaná čísla je [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span><span class="sxs-lookup"><span data-stu-id="2e8b2-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="2e8b2-174">Hash</span><span class="sxs-lookup"><span data-stu-id="2e8b2-174">Hashing</span></span>

<span data-ttu-id="2e8b2-175">Hash je další způsob, jak převést kategorická data na čísla.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="2e8b2-176">Funkce hash mapuje data libovolné velikosti (například řetězec textu) na číslo s pevným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="2e8b2-177">Hash může být rychlý a prostorově efektivní způsob vektorizace prvků.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="2e8b2-178">Jedním z pozoruhodných příkladů hašování ve strojovém učení je filtrování nevyžádané pošty, kde namísto udržování slovníku známých slov je každé slovo v e-mailu zatříděno a přidáno do vektoru velkých funkcí.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="2e8b2-179">Použití hash tímto způsobem se vyhýbá problému škodlivého filtrování nevyžádané pošty obcházení pomocí slov, která nejsou ve slovníku.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="2e8b2-180">ML.NET poskytuje transformaci [hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) k provedení hash na text, data a číselná data.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="2e8b2-181">Podobně jako mapování hodnotového klíče jsou výstupy transformace hash typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="2e8b2-182">Práce s textovými daty</span><span class="sxs-lookup"><span data-stu-id="2e8b2-182">Work with text data</span></span>

<span data-ttu-id="2e8b2-183">Stejně jako kategorická data je třeba textová data transformovat do číselných funkcí před použitím k vytvoření modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="2e8b2-184">Podrobnější seznam a popis textových transformací naleznete na [stránce transformací.](../resources/transforms.md)</span><span class="sxs-lookup"><span data-stu-id="2e8b2-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="2e8b2-185">Použití dat, jako jsou níže uvedená data, která byla načtena do aplikace [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="2e8b2-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="2e8b2-186">ML.NET poskytuje [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformaci, která přebírá hodnotu řetězce textu a vytváří sadu prvků z textu použitím řady jednotlivých transformací.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="2e8b2-187">Výsledná transformace převede textové hodnoty `Description` ve sloupci na číselný vektor, který vypadá podobně jako výstup níže:</span><span class="sxs-lookup"><span data-stu-id="2e8b2-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="2e8b2-188">Transformace, které tvoří `FeaturizeText` lze také použít jednotlivě pro jemnější kontrolu zrnitosti nad generování prvku.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="2e8b2-189">`textEstimator`obsahuje podmnožinu operací [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) prováděných metodou.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="2e8b2-190">Výhodou složitějšího kanálu je řízení a viditelnost nad transformacemi použitými pro data.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="2e8b2-191">Jako příklad použijete první položku a následuje podrobný popis výsledků provedených `textEstimator`transformačními kroky definovanými :</span><span class="sxs-lookup"><span data-stu-id="2e8b2-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="2e8b2-192">**Původní text: Jedná se o dobrý produkt**</span><span class="sxs-lookup"><span data-stu-id="2e8b2-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="2e8b2-193">Transformace</span><span class="sxs-lookup"><span data-stu-id="2e8b2-193">Transform</span></span> | <span data-ttu-id="2e8b2-194">Popis</span><span class="sxs-lookup"><span data-stu-id="2e8b2-194">Description</span></span> | <span data-ttu-id="2e8b2-195">Výsledek</span><span class="sxs-lookup"><span data-stu-id="2e8b2-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="2e8b2-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="2e8b2-196">1. NormalizeText</span></span> | <span data-ttu-id="2e8b2-197">Ve výchozím nastavení převede všechna písmena na malá písmena.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="2e8b2-198">to je dobrý produkt</span><span class="sxs-lookup"><span data-stu-id="2e8b2-198">this is a good product</span></span>
|<span data-ttu-id="2e8b2-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="2e8b2-199">2. TokenizeWords</span></span> | <span data-ttu-id="2e8b2-200">Rozdělí řetězec na jednotlivá slova.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-200">Splits string into individual words</span></span> | <span data-ttu-id="2e8b2-201">["to","je","a",dobré",produkt"]</span><span class="sxs-lookup"><span data-stu-id="2e8b2-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="2e8b2-202">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="2e8b2-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="2e8b2-203">Odstraňuje stopwords jako *je* *a*.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="2e8b2-204">["dobrý",produkt"]</span><span class="sxs-lookup"><span data-stu-id="2e8b2-204">["good","product"]</span></span>
|<span data-ttu-id="2e8b2-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="2e8b2-205">4. MapValueToKey</span></span> | <span data-ttu-id="2e8b2-206">Mapuje hodnoty na klíče (kategorie) na základě vstupních dat</span><span class="sxs-lookup"><span data-stu-id="2e8b2-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="2e8b2-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="2e8b2-207">[1,2]</span></span>
|<span data-ttu-id="2e8b2-208">5. ProduktyNGrams</span><span class="sxs-lookup"><span data-stu-id="2e8b2-208">5. ProduceNGrams</span></span> | <span data-ttu-id="2e8b2-209">Transformuje text do posloupnosti po sobě jdoucích slov.</span><span class="sxs-lookup"><span data-stu-id="2e8b2-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="2e8b2-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="2e8b2-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="2e8b2-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="2e8b2-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="2e8b2-212">Škálování vstupů podle jejich lp-normy</span><span class="sxs-lookup"><span data-stu-id="2e8b2-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="2e8b2-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="2e8b2-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
