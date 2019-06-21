---
title: Příprava dat
description: Další informace o použití transformace v ML.NET k manipulaci a připravit data pro další zpracování nebo model vytváření.
author: luisquintanilla
ms.author: luquinta
ms.date: 05/03/2019
ms.custom: mvc, how-to
ms.openlocfilehash: abf43260a438c9b1febffc77cf39e7328e0377ee
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268245"
---
# <a name="prepare-data"></a><span data-ttu-id="41994-103">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="41994-103">Prepare Data</span></span>

<span data-ttu-id="41994-104">Další informace o použití ML.NET připravit data pro další zpracování nebo vytváření modelu.</span><span class="sxs-lookup"><span data-stu-id="41994-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="41994-105">Data jsou často musí provést a zhuštěné.</span><span class="sxs-lookup"><span data-stu-id="41994-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="41994-106">Kromě toho algoritmů strojového učení ML.NET očekávat, že vstup nebo funkce, které chcete být v jedné číselné vektoru.</span><span class="sxs-lookup"><span data-stu-id="41994-106">Additionally, ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="41994-107">Proto je jedním z cílů přípravu dat jak dostat data do formátu očekávaném ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="41994-107">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span> 

## <a name="filter-data"></a><span data-ttu-id="41994-108">Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="41994-108">Filter data</span></span>

<span data-ttu-id="41994-109">V některých případech je relevantní pro analýzu nejsou všechna data v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="41994-109">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="41994-110">Přístup k odebrání nahromadění irelevantních dat je filtrování.</span><span class="sxs-lookup"><span data-stu-id="41994-110">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="41994-111">[ `DataOperationsCatalog` ](xref:Microsoft.ML.DataOperationsCatalog) Obsahuje sadu filtr operací, které trvat, než se [ `IDataView` ](xref:Microsoft.ML.IDataView) obsahující všechny data a vraťte se [IDataView](xref:Microsoft.ML.IDataView) obsahující pouze datové body, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="41994-111">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="41994-112">Je důležité si uvědomit, že vzhledem k tomu, že operace filtru nejsou [ `IEstimator` ](xref:Microsoft.ML.IEstimator%601) nebo [ `ITransformer` ](xref:Microsoft.ML.ITransformer) jako ty v [ `TransformsCatalog` ](xref:Microsoft.ML.TransformsCatalog), nemůže být zahrnutý jako součást [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) nebo [ `TransformerChain` ](xref:Microsoft.ML.Data.TransformerChain%601) datovým kanálem přípravy.</span><span class="sxs-lookup"><span data-stu-id="41994-112">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span> 

<span data-ttu-id="41994-113">Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="41994-113">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="41994-114">Chcete-li filtrovat data na základě hodnoty sloupce, použijte [ `FilterRowsByColumn` ](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metody.</span><span class="sxs-lookup"><span data-stu-id="41994-114">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="41994-115">Příkladu výše má řádky v datové sadě s cenou mezi 200000 až 1 000 000.</span><span class="sxs-lookup"><span data-stu-id="41994-115">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="41994-116">Výsledek použití tohoto filtru by vrátit pouze poslední dva řádky v datech a vyloučit první řádek vzhledem k tomu, že cena je 100000 a není mezi zadaného rozsahu.</span><span class="sxs-lookup"><span data-stu-id="41994-116">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="41994-117">Nahraďte chybějící hodnoty</span><span class="sxs-lookup"><span data-stu-id="41994-117">Replace missing values</span></span>

<span data-ttu-id="41994-118">Chybějící hodnoty jsou společného výskytu v datových sadách.</span><span class="sxs-lookup"><span data-stu-id="41994-118">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="41994-119">Je jedním z přístupů k práci s chybějící hodnoty nahradit výchozí hodnotu pro daný typ, pokud všechny nebo jiné smysluplnou hodnotu, jako je střední hodnota v datech.</span><span class="sxs-lookup"><span data-stu-id="41994-119">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span> 

<span data-ttu-id="41994-120">Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="41994-120">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="41994-121">Všimněte si, že po posledním prvku v seznamu má chybí hodnota pro `Price`.</span><span class="sxs-lookup"><span data-stu-id="41994-121">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="41994-122">Nahradit chybějící hodnoty v `Price` sloupců, použijte [ `ReplaceMissingValues` ](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) metoda vyplnit tento chybí hodnota.</span><span class="sxs-lookup"><span data-stu-id="41994-122">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41994-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) fungují jenom s číselnými daty.</span><span class="sxs-lookup"><span data-stu-id="41994-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="41994-124">ML.NET podporuje různé [nahrazení režimy](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="41994-124">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="41994-125">Ukázka výše používá `Mean` nahrazení režimu, který vyplní chybějící hodnoty s průměrnou hodnotu tohoto sloupce.</span><span class="sxs-lookup"><span data-stu-id="41994-125">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="41994-126">Vyplní výsledek nahrazení `Price` vlastnost po posledním prvku v našich dat s 200 000, protože je průměrem 100 000 a 300 000.</span><span class="sxs-lookup"><span data-stu-id="41994-126">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span> 

## <a name="use-normalizers"></a><span data-ttu-id="41994-127">Použití normalizers</span><span class="sxs-lookup"><span data-stu-id="41994-127">Use normalizers</span></span>

<span data-ttu-id="41994-128">[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) jsou data předběžného zpracování techniku použít ke standardizaci funkce, které nejsou ve stejném měřítku, která pomáhá algoritmy sloučit rychleji.</span><span class="sxs-lookup"><span data-stu-id="41994-128">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="41994-129">Například rozsahy pro hodnoty jako věku a příjmů výrazně liší stářím obecně se v rozsahu od 0 do 100 a příjmu, obecně je v rozsahu 0 až po tisíce.</span><span class="sxs-lookup"><span data-stu-id="41994-129">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="41994-130">Přejděte [transformace stránky](../resources/transforms.md) podrobnější seznam a popis normalizace transformací.</span><span class="sxs-lookup"><span data-stu-id="41994-130">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span> 

### <a name="min-max-normalization"></a><span data-ttu-id="41994-131">Normalizace maximálních</span><span class="sxs-lookup"><span data-stu-id="41994-131">Min-Max normalization</span></span>

<span data-ttu-id="41994-132">Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="41994-132">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="41994-133">Normalizaci lze použít pro sloupce s jednu číselnou hodnotu, jakož i vektorů.</span><span class="sxs-lookup"><span data-stu-id="41994-133">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="41994-134">Normalizovat data v `Price` sloupce pomocí maximálních normalizace s [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) metody.</span><span class="sxs-lookup"><span data-stu-id="41994-134">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="41994-135">Původní hodnoty cena `[200000,100000]` jsou převedeny na `[ 1, 0.5 ]` pomocí `MinMax` normalizace vzorec, který generuje výstupní hodnoty v rozmezí 0 – 1.</span><span class="sxs-lookup"><span data-stu-id="41994-135">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="41994-136">Binning</span><span class="sxs-lookup"><span data-stu-id="41994-136">Binning</span></span>

<span data-ttu-id="41994-137">[Binning](https://en.wikipedia.org/wiki/Data_binning) převede průběžné hodnoty na samostatných reprezentace vstupu.</span><span class="sxs-lookup"><span data-stu-id="41994-137">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="41994-138">Předpokládejme například, že jednou z vašich funkcí je věk.</span><span class="sxs-lookup"><span data-stu-id="41994-138">For example, suppose one of your features is age.</span></span> <span data-ttu-id="41994-139">Místo hodnoty skutečné stáří binning vytvoří rozsahy pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41994-139">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="41994-140">0 – 18 může být jeden bin, jiné mohou být 19 35 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="41994-140">0-18 could be one bin, another could be 19-35 and so on.</span></span> 

<span data-ttu-id="41994-141">Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="41994-141">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="41994-142">Normalizovat data do přihrádek pomocí [ `NormalizeBinning` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody.</span><span class="sxs-lookup"><span data-stu-id="41994-142">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="41994-143">`maximumBinCount` Parametr umožňuje určit počet intervalů, které jsou potřeba ke klasifikaci dat.</span><span class="sxs-lookup"><span data-stu-id="41994-143">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="41994-144">V tomto příkladu data zařadí do dva přihrádky.</span><span class="sxs-lookup"><span data-stu-id="41994-144">In this example, data will be put into two bins.</span></span>  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="41994-145">Vytvoří výsledek binning bin hranice `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="41994-145">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="41994-146">Proto je výsledný přihrádky `[0,1,1]` protože první zjišťování je mezi 0-200000 a ostatní jsou větší než 200 000, ale menší než nekonečno.</span><span class="sxs-lookup"><span data-stu-id="41994-146">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="41994-147">Práce s data zařazená do kategorií</span><span class="sxs-lookup"><span data-stu-id="41994-147">Work with categorical data</span></span>

<span data-ttu-id="41994-148">Data zařazená do kategorií nečíselné musí být převeden na číslo před použitím sestavit model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="41994-148">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span> 

<span data-ttu-id="41994-149">Pomocí následující vstupní data, která je načtena do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="41994-149">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="41994-150">Kategorií `VehicleType` vlastnosti mohou být převedeny na čísla pomocí [ `OneHotEncoding` ](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) metody.</span><span class="sxs-lookup"><span data-stu-id="41994-150">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span> 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="41994-151">Výsledný transformace převede textovou hodnotu `VehicleType` na číslo.</span><span class="sxs-lookup"><span data-stu-id="41994-151">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="41994-152">Položky `VehicleType` sloupce se následující, když je použita transformace:</span><span class="sxs-lookup"><span data-stu-id="41994-152">The entries in the `VehicleType` column become the following when the transform is applied:</span></span> 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="41994-153">Práce s daty text</span><span class="sxs-lookup"><span data-stu-id="41994-153">Work with text data</span></span>

<span data-ttu-id="41994-154">Textová data nutné transformovat na čísla před sestavením model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="41994-154">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="41994-155">Přejděte [transformace stránky](../resources/transforms.md) podrobnější seznam a popis transformace textu.</span><span class="sxs-lookup"><span data-stu-id="41994-155">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="41994-156">Pomocí dat, jako je následující, která data se načetl do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="41994-156">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="41994-157">Minimální krokem pro převod textu na reprezentace číselné vektoru je použití [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody.</span><span class="sxs-lookup"><span data-stu-id="41994-157">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="41994-158">S použitím [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) vstupního textového sloupce, výsledkem je číselná vektor představující lp normalized slovo, znak ngrams je použita transformace, řadu transformací.</span><span class="sxs-lookup"><span data-stu-id="41994-158">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span> 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="41994-159">Výsledný transformace textové hodnoty v převede `Description` sloupců na číselný vektoru, který vypadá podobně jako následující výstup:</span><span class="sxs-lookup"><span data-stu-id="41994-159">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="41994-160">Kroky zpracování složitých text se sloučí do [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) odebrat šumu a potenciálně snížili množství množství požadovaný výpočetní prostředky podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="41994-160">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="41994-161">`textEstimator` obsahuje podmnožinu operace provedené [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody.</span><span class="sxs-lookup"><span data-stu-id="41994-161">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="41994-162">Výhodou složitější kanálu je řízení a viditelnost přes transformaci na data.</span><span class="sxs-lookup"><span data-stu-id="41994-162">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span> 

<span data-ttu-id="41994-163">Jako příklad použijeme první položka, tady je podrobný popis výsledky vytvořené metodou kroky transformace určené `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="41994-163">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="41994-164">**Původní Text: To je dobrý produktu**</span><span class="sxs-lookup"><span data-stu-id="41994-164">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="41994-165">Transformace</span><span class="sxs-lookup"><span data-stu-id="41994-165">Transform</span></span> | <span data-ttu-id="41994-166">Popis</span><span class="sxs-lookup"><span data-stu-id="41994-166">Description</span></span> | <span data-ttu-id="41994-167">Výsledek</span><span class="sxs-lookup"><span data-stu-id="41994-167">Result</span></span>
|--|--|--|
|<span data-ttu-id="41994-168">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="41994-168">1. NormalizeText</span></span> | <span data-ttu-id="41994-169">Převede všechna písmena na malá písmena ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="41994-169">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="41994-170">To je dobrý produktu</span><span class="sxs-lookup"><span data-stu-id="41994-170">this is a good product</span></span>
|<span data-ttu-id="41994-171">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="41994-171">2. TokenizeWords</span></span> | <span data-ttu-id="41994-172">Rozdělí řetězec do jednotlivých slov</span><span class="sxs-lookup"><span data-stu-id="41994-172">Splits string into individual words</span></span> | <span data-ttu-id="41994-173">["Tento", "je", "";"Dobrá","produkt"]</span><span class="sxs-lookup"><span data-stu-id="41994-173">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="41994-174">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="41994-174">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="41994-175">Odebere stopword jako *je* *a*.</span><span class="sxs-lookup"><span data-stu-id="41994-175">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="41994-176">["good","product"]</span><span class="sxs-lookup"><span data-stu-id="41994-176">["good","product"]</span></span>
|<span data-ttu-id="41994-177">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="41994-177">4. MapValueToKey</span></span> | <span data-ttu-id="41994-178">Mapuje hodnoty klíče (kategorie) na základě vstupních dat</span><span class="sxs-lookup"><span data-stu-id="41994-178">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="41994-179">[1,2]</span><span class="sxs-lookup"><span data-stu-id="41994-179">[1,2]</span></span>
|<span data-ttu-id="41994-180">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="41994-180">5. ProduceNGrams</span></span> | <span data-ttu-id="41994-181">Transformuje text do sekvence po sobě jdoucích slov</span><span class="sxs-lookup"><span data-stu-id="41994-181">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="41994-182">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="41994-182">[1,1,1,0,0]</span></span>
|<span data-ttu-id="41994-183">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="41994-183">6. NormalizeLpNorm</span></span> | <span data-ttu-id="41994-184">Vstupy škálování podle jejich lp norm</span><span class="sxs-lookup"><span data-stu-id="41994-184">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="41994-185">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="41994-185">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
