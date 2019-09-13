---
title: Příprava dat pro vytvoření modelu
description: Naučte se používat transformace v ML.NET k manipulaci a přípravě dat pro další zpracování nebo vytváření modelů.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4452aef351f33df532f3c673307dedbbf71631b8
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929375"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="c419f-103">Příprava dat pro vytvoření modelu</span><span class="sxs-lookup"><span data-stu-id="c419f-103">Prepare data for building a model</span></span>

<span data-ttu-id="c419f-104">Naučte se používat ML.NET k přípravě dat pro další zpracování nebo vytvoření modelu.</span><span class="sxs-lookup"><span data-stu-id="c419f-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="c419f-105">Data často nejsou čistá a zhuštěná.</span><span class="sxs-lookup"><span data-stu-id="c419f-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="c419f-106">Algoritmy strojového učení ML.NET očekávají zadání nebo funkce v jednom numerickém vektoru.</span><span class="sxs-lookup"><span data-stu-id="c419f-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="c419f-107">Podobně hodnota pro předpověď (Label), zejména v případě, že je kategorií data, musí být kódována.</span><span class="sxs-lookup"><span data-stu-id="c419f-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="c419f-108">Proto je jedním z cílů přípravy dat získat data do formátu očekávaného ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="c419f-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span> 

## <a name="filter-data"></a><span data-ttu-id="c419f-109">Filtrovat data</span><span class="sxs-lookup"><span data-stu-id="c419f-109">Filter data</span></span>

<span data-ttu-id="c419f-110">V některých případech nejsou všechna data v datové sadě relevantní pro účely analýzy.</span><span class="sxs-lookup"><span data-stu-id="c419f-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="c419f-111">Přístup k odebrání nerelevantních dat je filtrování.</span><span class="sxs-lookup"><span data-stu-id="c419f-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="c419f-112">Obsahuje sadu operací filtru, které [`IDataView`](xref:Microsoft.ML.IDataView) obsahují všechna data a vracejí [IDataView](xref:Microsoft.ML.IDataView) obsahující pouze datové body, které mají zájem. [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog)</span><span class="sxs-lookup"><span data-stu-id="c419f-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="c419f-113">Je důležité si uvědomit, že vzhledem k tomu [`IEstimator`](xref:Microsoft.ML.IEstimator%601) [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), že operace filtru [`ITransformer`](xref:Microsoft.ML.ITransformer) nejsou ani jako ty v, nelze je zahrnout jako součást [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) kanálu nebo [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) přípravku pro přípravu dat.</span><span class="sxs-lookup"><span data-stu-id="c419f-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span> 

<span data-ttu-id="c419f-114">Pomocí následujících vstupních dat, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="c419f-114">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="c419f-115">Chcete-li filtrovat data na základě hodnoty sloupce, použijte [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) metodu.</span><span class="sxs-lookup"><span data-stu-id="c419f-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="c419f-116">Výše uvedená ukázka v datové sadě bere řádky s cenou mezi 200000 a 1000000.</span><span class="sxs-lookup"><span data-stu-id="c419f-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="c419f-117">Výsledek použití tohoto filtru vrátí jenom poslední dva řádky v datech a vyloučí první řádek, protože jeho cena je 100000 a ne mezi zadaným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="c419f-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="c419f-118">Nahradit chybějící hodnoty</span><span class="sxs-lookup"><span data-stu-id="c419f-118">Replace missing values</span></span>

<span data-ttu-id="c419f-119">Chybějící hodnoty jsou běžné výskyty v datových sadách.</span><span class="sxs-lookup"><span data-stu-id="c419f-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="c419f-120">Jediným způsobem, jak řešit chybějící hodnoty, je nahradit je výchozí hodnotou pro daný typ, pokud kteroukoli nebo jinou smysluplnou hodnotu, například střední hodnotu v datech.</span><span class="sxs-lookup"><span data-stu-id="c419f-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span> 

<span data-ttu-id="c419f-121">Pomocí následujících vstupních dat, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="c419f-121">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="c419f-122">Všimněte si, že poslední prvek v našem seznamu má chybějící hodnotu pro `Price`.</span><span class="sxs-lookup"><span data-stu-id="c419f-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="c419f-123">Chcete-li nahradit chybějící hodnoty ve `Price` sloupci, [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) použijte metodu k vyplnění chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c419f-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c419f-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*)funguje pouze s numerickými daty.</span><span class="sxs-lookup"><span data-stu-id="c419f-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="c419f-125">ML.NET podporuje různé [režimy nahrazení](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="c419f-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="c419f-126">Výše uvedená ukázka používá `Mean` režim nahrazení, ve kterém se vyplní chybějící hodnota průměrnou hodnotou tohoto sloupce.</span><span class="sxs-lookup"><span data-stu-id="c419f-126">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="c419f-127">Výsledek nahrazení vyplní `Price` vlastnost pro poslední prvek v datech s 200 000, protože se jedná o průměr 100 000 a 300 000.</span><span class="sxs-lookup"><span data-stu-id="c419f-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span> 

## <a name="use-normalizers"></a><span data-ttu-id="c419f-128">Použít normalizy</span><span class="sxs-lookup"><span data-stu-id="c419f-128">Use normalizers</span></span>

<span data-ttu-id="c419f-129">[Normalizace](https://en.wikipedia.org/wiki/Feature_scaling) je metoda předběžného zpracování dat, která slouží ke standardizaci funkcí, které nejsou ve stejném měřítku, což pomáhá zvýšit sblížení algoritmů.</span><span class="sxs-lookup"><span data-stu-id="c419f-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="c419f-130">Například rozsahy pro hodnoty, jako je věk a příjem, se výrazně liší v rozmezí 0-100 a příjem je obecně v rozsahu od 0 do tisíců.</span><span class="sxs-lookup"><span data-stu-id="c419f-130">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="c419f-131">Podrobnější seznam a popis transformací normalizace najdete na [stránce transformace](../resources/transforms.md) .</span><span class="sxs-lookup"><span data-stu-id="c419f-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span> 

### <a name="min-max-normalization"></a><span data-ttu-id="c419f-132">Normalizace min-max</span><span class="sxs-lookup"><span data-stu-id="c419f-132">Min-Max normalization</span></span>

<span data-ttu-id="c419f-133">Pomocí následujících vstupních dat, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="c419f-133">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="c419f-134">Normalizace se dá použít na sloupce s jednou číselnou hodnotou i vektory.</span><span class="sxs-lookup"><span data-stu-id="c419f-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="c419f-135">Normalizuje data ve `Price` sloupci pomocí normalizace min-max [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) s metodou.</span><span class="sxs-lookup"><span data-stu-id="c419f-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="c419f-136">Původní cenové hodnoty `[200000,100000]` se převedou na `[ 1, 0.5 ]` použití `MinMax` vzorce normalizace, který generuje výstupní hodnoty v rozsahu 0-1.</span><span class="sxs-lookup"><span data-stu-id="c419f-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="c419f-137">Binningu</span><span class="sxs-lookup"><span data-stu-id="c419f-137">Binning</span></span>

<span data-ttu-id="c419f-138">[Binningu](https://en.wikipedia.org/wiki/Data_binning) převádí souvislé hodnoty do diskrétní reprezentace vstupu.</span><span class="sxs-lookup"><span data-stu-id="c419f-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="c419f-139">Předpokládejme například, že jedna z vašich funkcí je věková.</span><span class="sxs-lookup"><span data-stu-id="c419f-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="c419f-140">Místo použití skutečné věkové hodnoty binningu vytvoří rozsahy pro tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c419f-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="c419f-141">0-18 může být jedna přihrádka, další by mohla být 19-35 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c419f-141">0-18 could be one bin, another could be 19-35 and so on.</span></span> 

<span data-ttu-id="c419f-142">Pomocí následujících vstupních dat, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="c419f-142">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="c419f-143">Normalizuje data do přihrádek pomocí [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) metody.</span><span class="sxs-lookup"><span data-stu-id="c419f-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="c419f-144">`maximumBinCount` Parametr umožňuje zadat počet přihrádek potřebných ke klasifikaci vašich dat.</span><span class="sxs-lookup"><span data-stu-id="c419f-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="c419f-145">V tomto příkladu budou data vložena do dvou přihrádek.</span><span class="sxs-lookup"><span data-stu-id="c419f-145">In this example, data will be put into two bins.</span></span>  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="c419f-146">Výsledek binningu vytvoří meze přihrádky pro `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="c419f-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="c419f-147">Proto výsledné přihrádky jsou `[0,1,1]` , protože první pozorování je mezi 0-200000 a ostatní jsou větší než 200000, ale menší než nekonečno.</span><span class="sxs-lookup"><span data-stu-id="c419f-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="c419f-148">Práce s kategorií daty</span><span class="sxs-lookup"><span data-stu-id="c419f-148">Work with categorical data</span></span>

<span data-ttu-id="c419f-149">Než se číselné kategorií data musí převést na číslo, než se použije k sestavení modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="c419f-149">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span> 

<span data-ttu-id="c419f-150">Pomocí následujících vstupních dat, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="c419f-150">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="c419f-151">Vlastnost kategorií `VehicleType` lze převést na číslo [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="c419f-151">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span> 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="c419f-152">Výsledná transformace převede textovou hodnotu `VehicleType` na číslo.</span><span class="sxs-lookup"><span data-stu-id="c419f-152">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="c419f-153">Při použití transformace se `VehicleType` položky ve sloupci stanou následujícím:</span><span class="sxs-lookup"><span data-stu-id="c419f-153">The entries in the `VehicleType` column become the following when the transform is applied:</span></span> 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="c419f-154">Práce s textovými daty</span><span class="sxs-lookup"><span data-stu-id="c419f-154">Work with text data</span></span>

<span data-ttu-id="c419f-155">Textová data je potřeba transformovat na čísla, než je použijete k sestavení modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="c419f-155">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="c419f-156">Podrobnější seznam a popis transformací textu najdete na [stránce transformace](../resources/transforms.md) .</span><span class="sxs-lookup"><span data-stu-id="c419f-156">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="c419f-157">Pomocí dat, jako jsou následující data, která byla načtena [`IDataView`](xref:Microsoft.ML.IDataView)do:</span><span class="sxs-lookup"><span data-stu-id="c419f-157">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="c419f-158">Minimální krok pro převod textu na číselnou vektorovou reprezentaci je použití [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metody.</span><span class="sxs-lookup"><span data-stu-id="c419f-158">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="c419f-159">Použijete-li [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transformaci, použije se pro vstupní textový sloupec řada transformací, což má za následek numerické vektory, které představují lineární-normalizované slovo a znak ngrams.</span><span class="sxs-lookup"><span data-stu-id="c419f-159">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span> 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="c419f-160">Výsledná transformace by převedla textové hodnoty ve `Description` sloupci na číselný vektor, který vypadá podobně jako výstup níže:</span><span class="sxs-lookup"><span data-stu-id="c419f-160">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="c419f-161">Kombinací složitých kroků zpracování textu do [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) můžete odebrat šum a případně snížit množství potřebných prostředků pro zpracování podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c419f-161">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="c419f-162">`textEstimator`obsahuje podmnožinu operací provedených [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) metodou.</span><span class="sxs-lookup"><span data-stu-id="c419f-162">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="c419f-163">Výhodou složitějšího kanálu je řízení a viditelnost při transformaci aplikovaných na data.</span><span class="sxs-lookup"><span data-stu-id="c419f-163">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span> 

<span data-ttu-id="c419f-164">Jako příklad používáme první položku, což je podrobný popis výsledků, které byly vytvořeny pomocí kroků transformace definovaných v `textEstimator`následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="c419f-164">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="c419f-165">**Původní text: Toto je dobrý produkt**</span><span class="sxs-lookup"><span data-stu-id="c419f-165">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="c419f-166">Transformace</span><span class="sxs-lookup"><span data-stu-id="c419f-166">Transform</span></span> | <span data-ttu-id="c419f-167">Popis</span><span class="sxs-lookup"><span data-stu-id="c419f-167">Description</span></span> | <span data-ttu-id="c419f-168">Výsledek</span><span class="sxs-lookup"><span data-stu-id="c419f-168">Result</span></span>
|--|--|--|
|<span data-ttu-id="c419f-169">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="c419f-169">1. NormalizeText</span></span> | <span data-ttu-id="c419f-170">Ve výchozím nastavení převede všechna písmena na malá.</span><span class="sxs-lookup"><span data-stu-id="c419f-170">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="c419f-171">Toto je dobrý produkt</span><span class="sxs-lookup"><span data-stu-id="c419f-171">this is a good product</span></span>
|<span data-ttu-id="c419f-172">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="c419f-172">2. TokenizeWords</span></span> | <span data-ttu-id="c419f-173">Rozdělí řetězec na jednotlivá slova.</span><span class="sxs-lookup"><span data-stu-id="c419f-173">Splits string into individual words</span></span> | <span data-ttu-id="c419f-174">["This", "is", "a", "Dobrá", "Product"]</span><span class="sxs-lookup"><span data-stu-id="c419f-174">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="c419f-175">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="c419f-175">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="c419f-176">Odebere stopslova jako *je* a *.*</span><span class="sxs-lookup"><span data-stu-id="c419f-176">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="c419f-177">["dobré", "produkt"]</span><span class="sxs-lookup"><span data-stu-id="c419f-177">["good","product"]</span></span>
|<span data-ttu-id="c419f-178">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="c419f-178">4. MapValueToKey</span></span> | <span data-ttu-id="c419f-179">Mapuje hodnoty na klíče (kategorie) na základě vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="c419f-179">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="c419f-180">[1,2]</span><span class="sxs-lookup"><span data-stu-id="c419f-180">[1,2]</span></span>
|<span data-ttu-id="c419f-181">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="c419f-181">5. ProduceNGrams</span></span> | <span data-ttu-id="c419f-182">Transformuje text na posloupnost po sobě jdoucích slov.</span><span class="sxs-lookup"><span data-stu-id="c419f-182">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="c419f-183">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="c419f-183">[1,1,1,0,0]</span></span>
|<span data-ttu-id="c419f-184">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="c419f-184">6. NormalizeLpNorm</span></span> | <span data-ttu-id="c419f-185">Škálování vstupů podle jejich LP-normy</span><span class="sxs-lookup"><span data-stu-id="c419f-185">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="c419f-186">[0,577350529, 0,577350529, 0,577350529, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="c419f-186">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
