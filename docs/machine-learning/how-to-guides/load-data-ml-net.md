---
title: Načítání dat ze souborů a jiných zdrojů
description: Zjistěte, jak načíst data pro zpracování a školení do ML.NET pomocí rozhraní API. Data jsou uložena v souborech, databázích, JSON, XML nebo in-memory sbírkách.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344758"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="6646f-104">Načítání dat ze souborů a jiných zdrojů</span><span class="sxs-lookup"><span data-stu-id="6646f-104">Load data from files and other sources</span></span>

<span data-ttu-id="6646f-105">Zjistěte, jak načíst data pro zpracování a školení do ML.NET pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6646f-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="6646f-106">Data jsou původně uložena v souborech nebo jiných zdrojích dat, jako jsou databáze, JSON, XML nebo in-memory kolekce.</span><span class="sxs-lookup"><span data-stu-id="6646f-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="6646f-107">Pokud používáte Model Builder, najdete v [tématu Načítání trénovacích dat do Tvůrce modelů](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="6646f-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="6646f-108">Vytvoření datového modelu</span><span class="sxs-lookup"><span data-stu-id="6646f-108">Create the data model</span></span>

<span data-ttu-id="6646f-109">ML.NET umožňuje definovat datové modely pomocí tříd.</span><span class="sxs-lookup"><span data-stu-id="6646f-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="6646f-110">Například vzhledem k následujícím vstupním datům:</span><span class="sxs-lookup"><span data-stu-id="6646f-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="6646f-111">Vytvořte datový model, který představuje fragment níže:</span><span class="sxs-lookup"><span data-stu-id="6646f-111">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="6646f-112">Anotace datového modelu s atributy sloupce</span><span class="sxs-lookup"><span data-stu-id="6646f-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="6646f-113">Atributy poskytují ML.NET další informace o datovém modelu a zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6646f-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="6646f-114">Atribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) určuje indexy sloupců vlastností.</span><span class="sxs-lookup"><span data-stu-id="6646f-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6646f-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)je vyžadována pouze při načítání dat ze souboru.</span><span class="sxs-lookup"><span data-stu-id="6646f-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="6646f-116">Načíst sloupce jako:</span><span class="sxs-lookup"><span data-stu-id="6646f-116">Load columns as:</span></span>

- <span data-ttu-id="6646f-117">Jednotlivé sloupce `Size` `CurrentPrices` jako `HousingData` a ve třídě.</span><span class="sxs-lookup"><span data-stu-id="6646f-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="6646f-118">Více sloupců najednou ve formě vektoru `HistoricalPrices` `HousingData` jako ve třídě.</span><span class="sxs-lookup"><span data-stu-id="6646f-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="6646f-119">Pokud máte vlastnost vector, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) aplikujte atribut na vlastnost v datovém modelu.</span><span class="sxs-lookup"><span data-stu-id="6646f-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="6646f-120">Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="6646f-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="6646f-121">Udržování oddělených sloupů umožňuje snadnost a flexibilitu konstrukce prvků, ale pro velmi velký počet sloupců, provoz na jednotlivých sloupech má vliv na rychlost tréninku.</span><span class="sxs-lookup"><span data-stu-id="6646f-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="6646f-122">ML.NET pracuje prostřednictvím názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="6646f-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="6646f-123">Pokud chcete změnit název sloupce na něco jiného než název [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) vlastnosti, použijte atribut.</span><span class="sxs-lookup"><span data-stu-id="6646f-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="6646f-124">Při vytváření objektů v paměti stále vytváříte objekty pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6646f-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="6646f-125">Pro zpracování dat a vytváření modelů strojového učení však ML.NET přepíše a [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) odkazuje na vlastnost s hodnotou uvedenou v atributu.</span><span class="sxs-lookup"><span data-stu-id="6646f-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="6646f-126">Načtení dat z jednoho souboru</span><span class="sxs-lookup"><span data-stu-id="6646f-126">Load data from a single file</span></span>

<span data-ttu-id="6646f-127">Chcete-li načíst data [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) ze souboru, použijte metodu spolu s datovým modelem pro načtení dat.</span><span class="sxs-lookup"><span data-stu-id="6646f-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="6646f-128">Vzhledem k tomu, že `separatorChar` parametr je ve výchozím nastavení oddělen tabulátorem, změňte jej pro datový soubor podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6646f-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="6646f-129">Pokud má váš soubor záhlaví, nastavte `hasHeader` parametr tak, aby `true` ignoroval první řádek v souboru a začal načítat data z druhého řádku.</span><span class="sxs-lookup"><span data-stu-id="6646f-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="6646f-130">Načtení dat z více souborů</span><span class="sxs-lookup"><span data-stu-id="6646f-130">Load data from multiple files</span></span>

<span data-ttu-id="6646f-131">V případě, že jsou data uložena ve více souborech, pokud je schéma dat stejné, ML.NET umožňuje načíst data z více souborů, které jsou buď ve stejném adresáři, nebo ve více adresářích.</span><span class="sxs-lookup"><span data-stu-id="6646f-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="6646f-132">Načtení ze souborů v jednom adresáři</span><span class="sxs-lookup"><span data-stu-id="6646f-132">Load from files in a single directory</span></span>

<span data-ttu-id="6646f-133">Pokud jsou všechny datové soubory ve stejném adresáři, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) použijte v metodě zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="6646f-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="6646f-134">Načtení ze souborů ve více adresářích</span><span class="sxs-lookup"><span data-stu-id="6646f-134">Load from files in multiple directories</span></span>

<span data-ttu-id="6646f-135">Chcete-li načíst data z [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) více adresářů, použijte metodu k [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)vytvoření .</span><span class="sxs-lookup"><span data-stu-id="6646f-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="6646f-136">Potom použijte [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a zadejte jednotlivé cesty k souborům (zástupné znaky nelze použít).</span><span class="sxs-lookup"><span data-stu-id="6646f-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="6646f-137">Načtení dat z relační databáze</span><span class="sxs-lookup"><span data-stu-id="6646f-137">Load data from a relational database</span></span>

<span data-ttu-id="6646f-138">ML.NET podporuje načítání dat z různých relačních databází podporovaných, [`System.Data`](xref:System.Data) které zahrnují SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 a mnoho dalších.</span><span class="sxs-lookup"><span data-stu-id="6646f-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="6646f-139">Chcete-li použít `DatabaseLoader`, odkaz [na Balíček System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet.</span><span class="sxs-lookup"><span data-stu-id="6646f-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="6646f-140">Vzhledem k tomu, `House` databáze s názvem tabulky a následující schéma:</span><span class="sxs-lookup"><span data-stu-id="6646f-140">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="6646f-141">Data mohou být modelována `HouseData`podle třídy, jako je .</span><span class="sxs-lookup"><span data-stu-id="6646f-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="6646f-142">Potom uvnitř aplikace vytvořte `DatabaseLoader`.</span><span class="sxs-lookup"><span data-stu-id="6646f-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="6646f-143">Definujte připojovací řetězec a příkaz SQL, který má `DatabaseSource` být proveden v databázi, a vytvořte instanci.</span><span class="sxs-lookup"><span data-stu-id="6646f-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="6646f-144">Tato ukázka používá databázi localdb SQL Server s cestou k souboru.</span><span class="sxs-lookup"><span data-stu-id="6646f-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="6646f-145">DatabaseLoader však podporuje všechny ostatní platné připojovací řetězec pro databáze v místním prostředí a v cloudu.</span><span class="sxs-lookup"><span data-stu-id="6646f-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="6646f-146">Číselná data, která [`Real`](xref:System.Data.SqlDbType) nejsou typu, musí [`Real`](xref:System.Data.SqlDbType)být převedena na .</span><span class="sxs-lookup"><span data-stu-id="6646f-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="6646f-147">Typ [`Real`](xref:System.Data.SqlDbType) je reprezentován jako hodnota s plovoucí [`Single`](xref:System.Single)desetinnou čárkou s jednou přesností nebo typ vstupu očekávaný ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="6646f-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="6646f-148">V této ukázce je `NumBed` sloupec celé číslo v databázi.</span><span class="sxs-lookup"><span data-stu-id="6646f-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="6646f-149">Pomocí `CAST` vestavěné funkce se převede [`Real`](xref:System.Data.SqlDbType)na .</span><span class="sxs-lookup"><span data-stu-id="6646f-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="6646f-150">Vzhledem `Price` k tomu, [`Real`](xref:System.Data.SqlDbType) že vlastnost je již typu je načten a je.</span><span class="sxs-lookup"><span data-stu-id="6646f-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="6646f-151">Pomocí `Load` metody načíst data [`IDataView`](xref:Microsoft.ML.IDataView)do .</span><span class="sxs-lookup"><span data-stu-id="6646f-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="6646f-152">Načtení dat z jiných zdrojů</span><span class="sxs-lookup"><span data-stu-id="6646f-152">Load data from other sources</span></span>

<span data-ttu-id="6646f-153">Kromě načítání dat uložených v souborech podporuje ML.NET načítání dat ze zdrojů, které zahrnují, ale nejsou omezeny na:</span><span class="sxs-lookup"><span data-stu-id="6646f-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="6646f-154">Kolekce v paměti</span><span class="sxs-lookup"><span data-stu-id="6646f-154">In-memory collections</span></span>
- <span data-ttu-id="6646f-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="6646f-155">JSON/XML</span></span>

<span data-ttu-id="6646f-156">Všimněte si, že při práci se zdroji streamování ML.NET očekává, že vstup bude ve formě kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="6646f-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="6646f-157">Proto při práci se zdroji, jako je JSON/XML, ujistěte se, že formátování dat do kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="6646f-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="6646f-158">Vzhledem k následujícímu shromažďování v paměti:</span><span class="sxs-lookup"><span data-stu-id="6646f-158">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="6646f-159">Načtěte kolekci v [`IDataView`](xref:Microsoft.ML.IDataView) paměti [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) do metody:</span><span class="sxs-lookup"><span data-stu-id="6646f-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6646f-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)předpokládá, [`IEnumerable`](xref:System.Collections.IEnumerable) že se načte z je bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="6646f-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="6646f-161">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6646f-161">Next steps</span></span>

- <span data-ttu-id="6646f-162">Informace o čištění nebo jiném zpracování dat naleznete v [tématu Příprava dat pro sestavení modelu](prepare-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="6646f-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="6646f-163">Až budete připraveni vytvořit model, přečtěte si informace [o tom, jak model trénovat a vyhodnocovat](train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="6646f-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
