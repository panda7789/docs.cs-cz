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
# <a name="load-data-from-files-and-other-sources"></a>Načítání dat ze souborů a jiných zdrojů

Zjistěte, jak načíst data pro zpracování a školení do ML.NET pomocí rozhraní API. Data jsou původně uložena v souborech nebo jiných zdrojích dat, jako jsou databáze, JSON, XML nebo in-memory kolekce.

Pokud používáte Model Builder, najdete v [tématu Načítání trénovacích dat do Tvůrce modelů](load-data-model-builder.md).

## <a name="create-the-data-model"></a>Vytvoření datového modelu

ML.NET umožňuje definovat datové modely pomocí tříd. Například vzhledem k následujícím vstupním datům:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Vytvořte datový model, který představuje fragment níže:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Anotace datového modelu s atributy sloupce

Atributy poskytují ML.NET další informace o datovém modelu a zdroji dat.

Atribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) určuje indexy sloupců vlastností.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)je vyžadována pouze při načítání dat ze souboru.

Načíst sloupce jako:

- Jednotlivé sloupce `Size` `CurrentPrices` jako `HousingData` a ve třídě.
- Více sloupců najednou ve formě vektoru `HistoricalPrices` `HousingData` jako ve třídě.

Pokud máte vlastnost vector, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) aplikujte atribut na vlastnost v datovém modelu. Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu. Udržování oddělených sloupů umožňuje snadnost a flexibilitu konstrukce prvků, ale pro velmi velký počet sloupců, provoz na jednotlivých sloupech má vliv na rychlost tréninku.

ML.NET pracuje prostřednictvím názvů sloupců. Pokud chcete změnit název sloupce na něco jiného než název [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) vlastnosti, použijte atribut. Při vytváření objektů v paměti stále vytváříte objekty pomocí názvu vlastnosti. Pro zpracování dat a vytváření modelů strojového učení však ML.NET přepíše a [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) odkazuje na vlastnost s hodnotou uvedenou v atributu.

## <a name="load-data-from-a-single-file"></a>Načtení dat z jednoho souboru

Chcete-li načíst data [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) ze souboru, použijte metodu spolu s datovým modelem pro načtení dat. Vzhledem k tomu, že `separatorChar` parametr je ve výchozím nastavení oddělen tabulátorem, změňte jej pro datový soubor podle potřeby. Pokud má váš soubor záhlaví, nastavte `hasHeader` parametr tak, aby `true` ignoroval první řádek v souboru a začal načítat data z druhého řádku.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Načtení dat z více souborů

V případě, že jsou data uložena ve více souborech, pokud je schéma dat stejné, ML.NET umožňuje načíst data z více souborů, které jsou buď ve stejném adresáři, nebo ve více adresářích.

### <a name="load-from-files-in-a-single-directory"></a>Načtení ze souborů v jednom adresáři

Pokud jsou všechny datové soubory ve stejném adresáři, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) použijte v metodě zástupné znaky.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Načtení ze souborů ve více adresářích

Chcete-li načíst data z [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) více adresářů, použijte metodu k [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)vytvoření . Potom použijte [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a zadejte jednotlivé cesty k souborům (zástupné znaky nelze použít).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Načtení dat z relační databáze

ML.NET podporuje načítání dat z různých relačních databází podporovaných, [`System.Data`](xref:System.Data) které zahrnují SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 a mnoho dalších.

> [!NOTE]
> Chcete-li použít `DatabaseLoader`, odkaz [na Balíček System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet.

Vzhledem k tomu, `House` databáze s názvem tabulky a následující schéma:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Data mohou být modelována `HouseData`podle třídy, jako je .

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Potom uvnitř aplikace vytvořte `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Definujte připojovací řetězec a příkaz SQL, který má `DatabaseSource` být proveden v databázi, a vytvořte instanci. Tato ukázka používá databázi localdb SQL Server s cestou k souboru. DatabaseLoader však podporuje všechny ostatní platné připojovací řetězec pro databáze v místním prostředí a v cloudu.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Číselná data, která [`Real`](xref:System.Data.SqlDbType) nejsou typu, musí [`Real`](xref:System.Data.SqlDbType)být převedena na . Typ [`Real`](xref:System.Data.SqlDbType) je reprezentován jako hodnota s plovoucí [`Single`](xref:System.Single)desetinnou čárkou s jednou přesností nebo typ vstupu očekávaný ML.NET algoritmy. V této ukázce je `NumBed` sloupec celé číslo v databázi. Pomocí `CAST` vestavěné funkce se převede [`Real`](xref:System.Data.SqlDbType)na . Vzhledem `Price` k tomu, [`Real`](xref:System.Data.SqlDbType) že vlastnost je již typu je načten a je.

Pomocí `Load` metody načíst data [`IDataView`](xref:Microsoft.ML.IDataView)do .

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Načtení dat z jiných zdrojů

Kromě načítání dat uložených v souborech podporuje ML.NET načítání dat ze zdrojů, které zahrnují, ale nejsou omezeny na:

- Kolekce v paměti
- JSON/XML

Všimněte si, že při práci se zdroji streamování ML.NET očekává, že vstup bude ve formě kolekce v paměti. Proto při práci se zdroji, jako je JSON/XML, ujistěte se, že formátování dat do kolekce v paměti.

Vzhledem k následujícímu shromažďování v paměti:

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

Načtěte kolekci v [`IDataView`](xref:Microsoft.ML.IDataView) paměti [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) do metody:

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)předpokládá, [`IEnumerable`](xref:System.Collections.IEnumerable) že se načte z je bezpečné pro přístup z více vláken.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Další kroky

- Informace o čištění nebo jiném zpracování dat naleznete v [tématu Příprava dat pro sestavení modelu](prepare-data-ml-net.md).
- Až budete připraveni vytvořit model, přečtěte si informace [o tom, jak model trénovat a vyhodnocovat](train-machine-learning-model-ml-net.md).
