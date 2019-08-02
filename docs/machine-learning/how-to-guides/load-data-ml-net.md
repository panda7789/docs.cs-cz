---
title: Načtení dat ze souborů a jiných zdrojů
description: V tomto postupu se dozvíte, jak načíst data pro zpracování a školení do ML.NET. Data se původně ukládají do souborů nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.
ms.date: 08/01/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: d5f3aab14a60a8c9860dc67f1cc98f3b1b3188ed
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733373"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="2a1f0-104">Načtení dat ze souborů a jiných zdrojů</span><span class="sxs-lookup"><span data-stu-id="2a1f0-104">Load data from files and other sources</span></span>

<span data-ttu-id="2a1f0-105">V tomto postupu se dozvíte, jak načíst data pro zpracování a školení do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="2a1f0-106">Data se původně ukládají do souborů nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="2a1f0-107">Vytvoření datového modelu</span><span class="sxs-lookup"><span data-stu-id="2a1f0-107">Create the data model</span></span>

<span data-ttu-id="2a1f0-108">ML.NET umožňuje definovat datové modely prostřednictvím tříd.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="2a1f0-109">Například s ohledem na následující vstupní data:</span><span class="sxs-lookup"><span data-stu-id="2a1f0-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="2a1f0-110">Vytvořte datový model, který představuje následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="2a1f0-110">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="2a1f0-111">Přidání poznámek k datovému modelu pomocí atributů sloupce</span><span class="sxs-lookup"><span data-stu-id="2a1f0-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="2a1f0-112">Atributy poskytují ML.NET více informací o datovém modelu a zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="2a1f0-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) Atribut určuje vlastnosti ' indexy sloupců '.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a1f0-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)je vyžadován pouze při načítání dat ze souboru.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="2a1f0-115">Načíst sloupce jako:</span><span class="sxs-lookup"><span data-stu-id="2a1f0-115">Load columns as:</span></span> 
- <span data-ttu-id="2a1f0-116">Jednotlivé sloupce jako `Size` a `CurrentPrices` ve `HousingData` třídě.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="2a1f0-117">Více sloupců v čase ve formě vektoru, jako `HistoricalPrices` `HousingData` ve třídě.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="2a1f0-118">Máte-li vlastnost Vector, použijte [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut na vlastnost v datovém modelu.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="2a1f0-119">Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="2a1f0-120">Udržování sloupců s oddělovači umožňuje snadnou a flexibilitu funkcí, ale pro velmi velký počet sloupců, který pracuje na jednotlivých sloupcích, způsobuje vliv na rychlost školení.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="2a1f0-121">ML.NET funguje prostřednictvím názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="2a1f0-122">Pokud chcete změnit název sloupce na jinou hodnotu než název vlastnosti, použijte [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="2a1f0-123">Při vytváření objektů v paměti stále vytváříte objekty pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="2a1f0-124">Pro zpracování dat a vytváření modelů strojového učení však ml.NET Přepisuje a odkazuje na vlastnost s hodnotou poskytnutou v [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atributu.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="2a1f0-125">Načtení dat z jednoho souboru</span><span class="sxs-lookup"><span data-stu-id="2a1f0-125">Load data from a single file</span></span>

<span data-ttu-id="2a1f0-126">Chcete-li načíst data ze souboru, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) použijte metodu spolu s datovým modelem pro načtení dat.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="2a1f0-127">Vzhledem `separatorChar` k tomu, že parametr je ve výchozím nastavení oddělený tabulátorem, změňte ho podle potřeby na datový soubor.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="2a1f0-128">Pokud má soubor záhlaví, nastavte `hasHeader` parametr na `true` hodnotu pro ignorování prvního řádku v souboru a začněte načítat data z druhého řádku.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="2a1f0-129">Načtení dat z více souborů</span><span class="sxs-lookup"><span data-stu-id="2a1f0-129">Load data from multiple files</span></span>

<span data-ttu-id="2a1f0-130">V případě, že jsou vaše data uložená ve více souborech, pokud je schéma dat stejné, ML.NET umožňuje načíst data z několika souborů, které jsou buď ve stejném adresáři, nebo ve více adresářích.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="2a1f0-131">Načtení ze souborů v jednom adresáři</span><span class="sxs-lookup"><span data-stu-id="2a1f0-131">Load from files in a single directory</span></span>

<span data-ttu-id="2a1f0-132">Pokud jsou všechny datové soubory ve stejném adresáři, použijte zástupné znaky v [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metodě.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="2a1f0-133">Načtení ze souborů ve více adresářích</span><span class="sxs-lookup"><span data-stu-id="2a1f0-133">Load from files in multiple directories</span></span>

<span data-ttu-id="2a1f0-134">Chcete-li načíst data z více adresářů, [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) použijte metodu pro [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)vytvoření.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="2a1f0-135">Pak použijte [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a určete jednotlivé cesty k souboru (zástupné znaky nelze použít).</span><span class="sxs-lookup"><span data-stu-id="2a1f0-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="2a1f0-136">Načtení dat z jiných zdrojů</span><span class="sxs-lookup"><span data-stu-id="2a1f0-136">Load data from other sources</span></span>

<span data-ttu-id="2a1f0-137">Kromě načítání dat uložených v souborech podporuje ML.NET načítání dat ze zdrojů, které zahrnují, ale nejsou omezeny na:</span><span class="sxs-lookup"><span data-stu-id="2a1f0-137">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="2a1f0-138">Kolekce v paměti</span><span class="sxs-lookup"><span data-stu-id="2a1f0-138">In-memory collections</span></span>
- <span data-ttu-id="2a1f0-139">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="2a1f0-139">JSON/XML</span></span>
- <span data-ttu-id="2a1f0-140">Databáze</span><span class="sxs-lookup"><span data-stu-id="2a1f0-140">Databases</span></span>

<span data-ttu-id="2a1f0-141">Všimněte si, že při práci se zdroji streamování očekává ML.NET, že vstup bude ve formě kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-141">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="2a1f0-142">Proto při práci se zdroji, jako je JSON nebo XML, nezapomeňte data formátovat do kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-142">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="2a1f0-143">S ohledem na následující kolekci v paměti:</span><span class="sxs-lookup"><span data-stu-id="2a1f0-143">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="2a1f0-144">Načtěte kolekci v paměti do [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) s metodou:</span><span class="sxs-lookup"><span data-stu-id="2a1f0-144">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a1f0-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)předpokládá, že [`IEnumerable`](xref:System.Collections.IEnumerable) se načte z aplikace je bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2a1f0-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span> 

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
