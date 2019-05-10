---
title: Načtení dat
description: Načtení datového souboru a Streamovat data do ML.NET
ms.date: 05/03/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 6edcc92b610e2e1f5e21c371b9f0aefd0b216d31
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063648"
---
# <a name="load-data-from-file-and-in-memory-sources"></a><span data-ttu-id="32500-103">Načtení dat ze zdroje souborů a v paměti</span><span class="sxs-lookup"><span data-stu-id="32500-103">Load data from file and in-memory sources</span></span>

<span data-ttu-id="32500-104">Tento návod ukazuje, jak načíst data pro zpracování a školení do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="32500-104">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="32500-105">Jsou data původně uložená v souborech nebo zdroje dat v reálném čase nebo datové proudy.</span><span class="sxs-lookup"><span data-stu-id="32500-105">The data is originally stored in files or real-time / streaming data sources.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="32500-106">Vytvoření datového modelu</span><span class="sxs-lookup"><span data-stu-id="32500-106">Create the data model</span></span>

<span data-ttu-id="32500-107">ML.NET slouží k definování datových modelů prostřednictvím třídy.</span><span class="sxs-lookup"><span data-stu-id="32500-107">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="32500-108">Mějme například následující vstupní data:</span><span class="sxs-lookup"><span data-stu-id="32500-108">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="32500-109">Vytvoření datového modelu, který představuje následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="32500-109">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="32500-110">Zadávání poznámek do datového modelu s atributy sloupce</span><span class="sxs-lookup"><span data-stu-id="32500-110">Annotating the data model with column attributes</span></span>

<span data-ttu-id="32500-111">Atributy poskytují další informace o zdroji dat a modelu dat ML.NET.</span><span class="sxs-lookup"><span data-stu-id="32500-111">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="32500-112">[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Atribut určuje vlastnosti indexy sloupců.</span><span class="sxs-lookup"><span data-stu-id="32500-112">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32500-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) je potřeba, pouze pokud načítání dat ze souboru.</span><span class="sxs-lookup"><span data-stu-id="32500-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="32500-114">Načíst sloupce jako:</span><span class="sxs-lookup"><span data-stu-id="32500-114">Load columns as:</span></span> 
- <span data-ttu-id="32500-115">Jednotlivé sloupce, jako jsou `Size` a `CurrentPrices` v `HousingData` třídy.</span><span class="sxs-lookup"><span data-stu-id="32500-115">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="32500-116">Několik sloupců najednou ve formuláři vektoru, jako jsou `HistoricalPrices` v `HousingData` třídy.</span><span class="sxs-lookup"><span data-stu-id="32500-116">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="32500-117">Je-li vlastnost vektoru, použije [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut vlastnosti v datovém modelu.</span><span class="sxs-lookup"><span data-stu-id="32500-117">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="32500-118">Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="32500-118">It's important to note that all of the elements in the vector need to be the same type.</span></span>

<span data-ttu-id="32500-119">ML.NET Operates prostřednictvím názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="32500-119">ML.NET Operates through column names.</span></span> <span data-ttu-id="32500-120">Pokud chcete změnit název sloupce na jinou hodnotu než název vlastnosti, použijte [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="32500-120">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="32500-121">Při vytváření objektů v paměti, stále vytvořit objekty pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="32500-121">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="32500-122">Ale pro sestavování modelů strojového učení a zpracování dat, ML.NET přepsání a odkazuje na vlastnost s hodnotou součástí [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="32500-122">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="32500-123">Načtení dat z jednoho souboru</span><span class="sxs-lookup"><span data-stu-id="32500-123">Load data from a single file</span></span>

<span data-ttu-id="32500-124">K načtení dat z použití souborů [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metoda spolu s datový model pro data, která mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="32500-124">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="32500-125">Protože `separatorChar` tabulátory ve výchozím nastavení je parametr, podle potřeby ho změňte pro datový soubor.</span><span class="sxs-lookup"><span data-stu-id="32500-125">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="32500-126">Pokud váš soubor má záhlaví, nastavit `hasHeader` parametr `true` ignorovat první řádek v souboru a začněte k načtení dat z na druhém řádku.</span><span class="sxs-lookup"><span data-stu-id="32500-126">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="32500-127">Načtení dat z více souborů</span><span class="sxs-lookup"><span data-stu-id="32500-127">Load data from multiple files</span></span>

<span data-ttu-id="32500-128">V případě, že vaše data jsou uložená ve více souborech, jako schéma dat je stejný, ML.NET vám umožní načíst dat z více souborů, které jsou buď ve stejném adresáři, nebo více adresářů.</span><span class="sxs-lookup"><span data-stu-id="32500-128">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="32500-129">Načíst ze souborů v jednom adresáři</span><span class="sxs-lookup"><span data-stu-id="32500-129">Load from files in a single directory</span></span>

<span data-ttu-id="32500-130">Když jsou všechny datové soubory ve stejném adresáři, použít zástupné znaky v [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody.</span><span class="sxs-lookup"><span data-stu-id="32500-130">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="32500-131">Načíst ze souborů ve více adresářů</span><span class="sxs-lookup"><span data-stu-id="32500-131">Load from files in multiple directories</span></span>

<span data-ttu-id="32500-132">Chcete-li načíst data z více adresářů, použijte [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) metodu pro vytvoření [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="32500-132">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="32500-133">Potom použijte [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a zadejte cesty jednotlivých souborů (zástupné znaky nelze použít).</span><span class="sxs-lookup"><span data-stu-id="32500-133">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-streaming-source"></a><span data-ttu-id="32500-134">Načtení dat z datových proudů zdroje</span><span class="sxs-lookup"><span data-stu-id="32500-134">Load data from a streaming source</span></span>

<span data-ttu-id="32500-135">Kromě načítají se data uložená na disku, ML.NET podporuje načítání dat z různých datových proudů zdrojů, které patří, ale nejsou omezeni na:</span><span class="sxs-lookup"><span data-stu-id="32500-135">In addition to loading data stored on disk, ML.NET supports loading data from various streaming sources that include but are not limited to:</span></span>

- <span data-ttu-id="32500-136">Kolekce v paměti</span><span class="sxs-lookup"><span data-stu-id="32500-136">In-memory collections</span></span>
- <span data-ttu-id="32500-137">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="32500-137">JSON/XML</span></span>
- <span data-ttu-id="32500-138">Databáze</span><span class="sxs-lookup"><span data-stu-id="32500-138">Databases</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32500-139">Všimněte si, že při práci se streamováním zdroje ML.NET očekává, že vstupem bude ve formuláři kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="32500-139">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="32500-140">Proto při práci se zdroji, jako je JSON nebo XML, ujistěte se, že pro zobrazení dat v kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="32500-140">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="32500-141">Daný následující kolekce v paměti:</span><span class="sxs-lookup"><span data-stu-id="32500-141">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="32500-142">Načtení kolekce v paměti do [ `IDataView` ](xref:Microsoft.ML.IDataView) s [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody:</span><span class="sxs-lookup"><span data-stu-id="32500-142">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
