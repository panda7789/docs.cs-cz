---
title: Načtení dat ze souborů a jiných zdrojů
description: V tomto postupu se dozvíte, jak načíst data pro zpracování a školení do ML.NET. Data se původně ukládají do souborů nebo jiných zdrojů dat, jako jsou databáze, JSON, XML nebo kolekce v paměti.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 07b3e7f5302a03f5fa4c936679c8a3c00d19a7b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740547"
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

Atribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) určuje vlastnosti indexy sloupců.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) se vyžaduje jenom při načítání dat ze souboru.

Načíst sloupce jako:

- Jednotlivé sloupce, například `Size` a `CurrentPrices` ve třídě `HousingData`.
- Více sloupců v čase ve formě vektoru, jako je `HistoricalPrices` ve třídě `HousingData`.

Máte-li vlastnost Vector, použijte atribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) na vlastnost v datovém modelu. Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu. Udržování sloupců s oddělovači umožňuje snadnou a flexibilitu funkcí, ale pro velmi velký počet sloupců, který pracuje na jednotlivých sloupcích, způsobuje vliv na rychlost školení.

ML.NET funguje prostřednictvím názvů sloupců. Chcete-li změnit název sloupce na jinou hodnotu než název vlastnosti, použijte atribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) . Při vytváření objektů v paměti stále vytváříte objekty pomocí názvu vlastnosti. Pro zpracování dat a vytváření modelů strojového učení však ML.NET Přepisuje a odkazuje na vlastnost s hodnotou poskytnutou v atributu [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) .

## <a name="load-data-from-a-single-file"></a>Načtení dat z jednoho souboru

Chcete-li načíst data ze souboru, použijte metodu [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) společně s datovým modelem pro načtení dat. Vzhledem k tomu, že parametr `separatorChar` je ve výchozím nastavení oddělený tabulátorem, změňte ho podle potřeby na datový soubor. Pokud má soubor záhlaví, nastavte parametr `hasHeader` na `true` tak, aby ignoroval první řádek v souboru a začal načíst data z druhého řádku.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Načtení dat z více souborů

V případě, že jsou vaše data uložená ve více souborech, pokud je schéma dat stejné, ML.NET umožňuje načíst data z několika souborů, které jsou buď ve stejném adresáři, nebo ve více adresářích.

### <a name="load-from-files-in-a-single-directory"></a>Načtení ze souborů v jednom adresáři

Pokud jsou všechny datové soubory ve stejném adresáři, použijte zástupné znaky v metodě [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) .

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Načtení ze souborů ve více adresářích

Chcete-li načíst data z více adresářů, vytvořte [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)pomocí metody [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) . Pak použijte metodu [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) a určete jednotlivé cesty k souboru (zástupné znaky nelze použít).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Načtení dat z relační databáze

ML.NET podporuje načítání dat z nejrůznějších relačních databází, které podporuje [`System.Data`](xref:System.Data) , které zahrnují SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, pokrok, IBM DB2 a mnoho dalších.

> [!NOTE]
> Pokud chcete použít `DatabaseLoader`, odkazujte na balíček NuGet [System. data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .

Pro databázi s tabulkou s názvem `House` a následujícím schématem:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Data je možné modelovat podle třídy, jako je `HouseData`.

```csharp
public class HouseData
{
    public float Size { get; set; }
    
    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Potom v rámci aplikace vytvořte `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Definujte připojovací řetězec a příkaz SQL, který se má spustit v databázi, a vytvořte instanci `DatabaseSource`. V této ukázce se používá databáze LocalDB SQL Server s cestou k souboru. DatabaseLoader však podporuje jakýkoli jiný platný připojovací řetězec pro databáze v místním prostředí i v cloudu.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Číselná data, která nejsou typu [`Real`](xref:System.Data.SqlDbType) musí být převedena na [`Real`](xref:System.Data.SqlDbType). Typ [`Real`](xref:System.Data.SqlDbType) je reprezentován jako hodnota s jednoduchou přesností a plovoucí desetinnou čárkou, nebo [`Single`](xref:System.Single), vstupní typ očekávaný algoritmem ml.NET. V této ukázce je sloupec `NumBed` v databázi celé číslo. Pomocí `CAST` integrované funkce se převede na [`Real`](xref:System.Data.SqlDbType). Vzhledem k tomu, že vlastnost `Price` je již typu [`Real`](xref:System.Data.SqlDbType) je načtena tak, jak je.

K načtení dat do [`IDataView`](xref:Microsoft.ML.IDataView)použijte metodu `Load`.

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

Načtěte kolekci v paměti do [`IDataView`](xref:Microsoft.ML.IDataView) s metodou [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) předpokládá, že [`IEnumerable`](xref:System.Collections.IEnumerable) , ze kterého se načítá, je bezpečný pro přístup z více vláken.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Další kroky

Pokud ke výukovém modelu Machine Learning používáte tvůrce modelů, přečtěte si téma [načtení dat o školení do konfigurátoru modelu](load-data-model-builder.md).
