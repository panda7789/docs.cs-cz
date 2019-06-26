---
title: Načtení dat ze souborů a dalších zdrojů
description: Tento návod ukazuje, jak načíst data pro zpracování a školení do ML.NET. Jsou data původně uložená v souborech nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.
ms.date: 06/25/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: fafbe3fed9e3f0b509eda4f9d8967965bde19767
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397748"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="f8321-104">Načtení dat ze souborů a dalších zdrojů</span><span class="sxs-lookup"><span data-stu-id="f8321-104">Load data from files and other sources</span></span>

<span data-ttu-id="f8321-105">Tento návod ukazuje, jak načíst data pro zpracování a školení do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f8321-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="f8321-106">Jsou data původně uložená v souborech nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="f8321-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="f8321-107">Vytvoření datového modelu</span><span class="sxs-lookup"><span data-stu-id="f8321-107">Create the data model</span></span>

<span data-ttu-id="f8321-108">ML.NET slouží k definování datových modelů prostřednictvím třídy.</span><span class="sxs-lookup"><span data-stu-id="f8321-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="f8321-109">Mějme například následující vstupní data:</span><span class="sxs-lookup"><span data-stu-id="f8321-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="f8321-110">Vytvoření datového modelu, který představuje následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="f8321-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="f8321-111">Zadávání poznámek do datového modelu s atributy sloupce</span><span class="sxs-lookup"><span data-stu-id="f8321-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="f8321-112">Atributy poskytují další informace o zdroji dat a modelu dat ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f8321-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="f8321-113">[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Atribut určuje vlastnosti indexy sloupců.</span><span class="sxs-lookup"><span data-stu-id="f8321-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8321-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) je potřeba, pouze pokud načítání dat ze souboru.</span><span class="sxs-lookup"><span data-stu-id="f8321-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="f8321-115">Načíst sloupce jako:</span><span class="sxs-lookup"><span data-stu-id="f8321-115">Load columns as:</span></span> 
- <span data-ttu-id="f8321-116">Jednotlivé sloupce, jako jsou `Size` a `CurrentPrices` v `HousingData` třídy.</span><span class="sxs-lookup"><span data-stu-id="f8321-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="f8321-117">Několik sloupců najednou ve formuláři vektoru, jako jsou `HistoricalPrices` v `HousingData` třídy.</span><span class="sxs-lookup"><span data-stu-id="f8321-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="f8321-118">Je-li vlastnost vektoru, použije [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut vlastnosti v datovém modelu.</span><span class="sxs-lookup"><span data-stu-id="f8321-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="f8321-119">Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f8321-119">It's important to note that all of the elements in the vector need to be the same type.</span></span>

<span data-ttu-id="f8321-120">ML.NET Operates prostřednictvím názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="f8321-120">ML.NET Operates through column names.</span></span> <span data-ttu-id="f8321-121">Pokud chcete změnit název sloupce na jinou hodnotu než název vlastnosti, použijte [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="f8321-121">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="f8321-122">Při vytváření objektů v paměti, stále vytvořit objekty pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f8321-122">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="f8321-123">Ale pro sestavování modelů strojového učení a zpracování dat, ML.NET přepsání a odkazuje na vlastnost s hodnotou součástí [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="f8321-123">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="f8321-124">Načtení dat z jednoho souboru</span><span class="sxs-lookup"><span data-stu-id="f8321-124">Load data from a single file</span></span>

<span data-ttu-id="f8321-125">K načtení dat z použití souborů [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metoda spolu s datový model pro data, která mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f8321-125">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="f8321-126">Protože `separatorChar` tabulátory ve výchozím nastavení je parametr, podle potřeby ho změňte pro datový soubor.</span><span class="sxs-lookup"><span data-stu-id="f8321-126">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="f8321-127">Pokud váš soubor má záhlaví, nastavit `hasHeader` parametr `true` ignorovat první řádek v souboru a začněte k načtení dat z na druhém řádku.</span><span class="sxs-lookup"><span data-stu-id="f8321-127">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="f8321-128">Načtení dat z více souborů</span><span class="sxs-lookup"><span data-stu-id="f8321-128">Load data from multiple files</span></span>

<span data-ttu-id="f8321-129">V případě, že vaše data jsou uložená ve více souborech, jako schéma dat je stejný, ML.NET vám umožní načíst dat z více souborů, které jsou buď ve stejném adresáři, nebo více adresářů.</span><span class="sxs-lookup"><span data-stu-id="f8321-129">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="f8321-130">Načíst ze souborů v jednom adresáři</span><span class="sxs-lookup"><span data-stu-id="f8321-130">Load from files in a single directory</span></span>

<span data-ttu-id="f8321-131">Když jsou všechny datové soubory ve stejném adresáři, použít zástupné znaky v [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody.</span><span class="sxs-lookup"><span data-stu-id="f8321-131">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="f8321-132">Načíst ze souborů ve více adresářů</span><span class="sxs-lookup"><span data-stu-id="f8321-132">Load from files in multiple directories</span></span>

<span data-ttu-id="f8321-133">Chcete-li načíst data z více adresářů, použijte [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) metodu pro vytvoření [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="f8321-133">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="f8321-134">Potom použijte [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a zadejte cesty jednotlivých souborů (zástupné znaky nelze použít).</span><span class="sxs-lookup"><span data-stu-id="f8321-134">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="f8321-135">Načtení dat z jiných zdrojů</span><span class="sxs-lookup"><span data-stu-id="f8321-135">Load data from other sources</span></span>

<span data-ttu-id="f8321-136">Kromě načítání dat, které jsou uloženy v souborech, ML.NET podporuje načítání dat ze zdroje, které patří, ale nejsou omezeni na:</span><span class="sxs-lookup"><span data-stu-id="f8321-136">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="f8321-137">Kolekce v paměti</span><span class="sxs-lookup"><span data-stu-id="f8321-137">In-memory collections</span></span>
- <span data-ttu-id="f8321-138">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="f8321-138">JSON/XML</span></span>
- <span data-ttu-id="f8321-139">Databáze</span><span class="sxs-lookup"><span data-stu-id="f8321-139">Databases</span></span>

<span data-ttu-id="f8321-140">Všimněte si, že při práci se streamováním zdroje ML.NET očekává, že vstupem bude ve formuláři kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="f8321-140">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="f8321-141">Proto při práci se zdroji, jako je JSON nebo XML, ujistěte se, že pro zobrazení dat v kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="f8321-141">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="f8321-142">Daný následující kolekce v paměti:</span><span class="sxs-lookup"><span data-stu-id="f8321-142">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="f8321-143">Načtení kolekce v paměti do [ `IDataView` ](xref:Microsoft.ML.IDataView) s [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody:</span><span class="sxs-lookup"><span data-stu-id="f8321-143">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
