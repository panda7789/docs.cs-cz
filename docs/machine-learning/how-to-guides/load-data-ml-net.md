---
title: Načtení dat ze souborů a jiných zdrojů
description: V tomto postupu se dozvíte, jak načíst data pro zpracování a školení do ML.NET. Data se původně ukládají do souborů nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 4008f38bf4a20113a3f5c865e38222e5b82f2acc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991367"
---
# <a name="load-data-from-files-and-other-sources"></a>Načtení dat ze souborů a jiných zdrojů

V tomto postupu se dozvíte, jak načíst data pro zpracování a školení do ML.NET. Data se původně ukládají do souborů nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.

## <a name="create-the-data-model"></a>Vytvoření datového modelu

ML.NET umožňuje definovat datové modely prostřednictvím tříd. Například s ohledem na následující vstupní data:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Vytvořte datový model, který představuje následující fragment kódu:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Přidání poznámek k datovému modelu pomocí atributů sloupce

Atributy poskytují ML.NET více informací o datovém modelu a zdroji dat.

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) Atribut určuje vlastnosti ' indexy sloupců '.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)je vyžadován pouze při načítání dat ze souboru.

Načíst sloupce jako:

- Jednotlivé sloupce jako `Size` a `CurrentPrices` ve `HousingData` třídě.
- Více sloupců v čase ve formě vektoru, jako `HistoricalPrices` `HousingData` ve třídě.

Máte-li vlastnost Vector, použijte [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut na vlastnost v datovém modelu. Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu. Udržování sloupců s oddělovači umožňuje snadnou a flexibilitu funkcí, ale pro velmi velký počet sloupců, který pracuje na jednotlivých sloupcích, způsobuje vliv na rychlost školení.

ML.NET funguje prostřednictvím názvů sloupců. Pokud chcete změnit název sloupce na jinou hodnotu než název vlastnosti, použijte [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut. Při vytváření objektů v paměti stále vytváříte objekty pomocí názvu vlastnosti. Pro zpracování dat a vytváření modelů strojového učení však ml.NET Přepisuje a odkazuje na vlastnost s hodnotou poskytnutou v [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atributu.

## <a name="load-data-from-a-single-file"></a>Načtení dat z jednoho souboru

Chcete-li načíst data ze souboru, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) použijte metodu spolu s datovým modelem pro načtení dat. Vzhledem `separatorChar` k tomu, že parametr je ve výchozím nastavení oddělený tabulátorem, změňte ho podle potřeby na datový soubor. Pokud má soubor záhlaví, nastavte `hasHeader` parametr na `true` hodnotu pro ignorování prvního řádku v souboru a začněte načítat data z druhého řádku.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Načtení dat z více souborů

V případě, že jsou vaše data uložená ve více souborech, pokud je schéma dat stejné, ML.NET umožňuje načíst data z několika souborů, které jsou buď ve stejném adresáři, nebo ve více adresářích.

### <a name="load-from-files-in-a-single-directory"></a>Načtení ze souborů v jednom adresáři

Pokud jsou všechny datové soubory ve stejném adresáři, použijte zástupné znaky v [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metodě.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Načtení ze souborů ve více adresářích

Chcete-li načíst data z více adresářů, [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) použijte metodu pro [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)vytvoření. Pak použijte [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a určete jednotlivé cesty k souboru (zástupné znaky nelze použít).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Načtení dat z relační databáze

> [!NOTE]
> DatabaseLoader je aktuálně ve verzi Preview. Dá se použít na základě odkazů na balíčky NuGet [Microsoft. ml. experimentální](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) a [System. data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) .

ML.NET podporuje načítání dat z nejrůznějších relačních databází [`System.Data`](xref:System.Data) , které podporuje, mezi které patří SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, pokrok, IBM DB2 a spousta dalších.

Pro databázi s tabulkou s názvem `House` a následujícím schématem:

```SQL
CREATE TABLE [House] (
    [HouseId] int NOT NULL IDENTITY,
    [Size] real NOT NULL,
    [Price] real NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Data je možné modelovat podle třídy, jako `HouseData`je.

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float Price { get; set; }
}
```

Potom v rámci aplikace vytvořte `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Definujte připojovací řetězec a příkaz SQL, který se má spustit v databázi, a vytvořte `DatabaseSource` instanci. V této ukázce se používá databáze LocalDB SQL Server s cestou k souboru. DatabaseLoader však podporuje jakýkoli jiný platný připojovací řetězec pro databáze v místním prostředí i v cloudu.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size,Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance,connectionString,sqlCommand);
```

Nakonec pomocí `Load` metody načtěte data [`IDataView`](xref:Microsoft.ML.IDataView)do.

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Načtení dat z jiných zdrojů

Kromě načítání dat uložených v souborech podporuje ML.NET načítání dat ze zdrojů, které zahrnují, ale nejsou omezeny na:

- Kolekce v paměti
- JSON/XML

Všimněte si, že při práci se zdroji streamování očekává ML.NET, že vstup bude ve formě kolekce v paměti. Proto při práci se zdroji, jako je JSON nebo XML, nezapomeňte data formátovat do kolekce v paměti.

S ohledem na následující kolekci v paměti:

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

Načtěte kolekci v paměti do [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) s metodou:

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)předpokládá, že [`IEnumerable`](xref:System.Collections.IEnumerable) se načte z aplikace je bezpečná pro přístup z více vláken.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
