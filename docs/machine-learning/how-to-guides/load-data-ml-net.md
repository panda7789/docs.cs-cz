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
# <a name="load-data-from-file-and-in-memory-sources"></a>Načtení dat ze zdroje souborů a v paměti

Tento návod ukazuje, jak načíst data pro zpracování a školení do ML.NET. Jsou data původně uložená v souborech nebo zdroje dat v reálném čase nebo datové proudy.

## <a name="create-the-data-model"></a>Vytvoření datového modelu

ML.NET slouží k definování datových modelů prostřednictvím třídy. Mějme například následující vstupní data:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Vytvoření datového modelu, který představuje následujícím fragmentu kódu:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Zadávání poznámek do datového modelu s atributy sloupce

Atributy poskytují další informace o zdroji dat a modelu dat ML.NET.

[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Atribut určuje vlastnosti indexy sloupců.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) je potřeba, pouze pokud načítání dat ze souboru.

Načíst sloupce jako: 
- Jednotlivé sloupce, jako jsou `Size` a `CurrentPrices` v `HousingData` třídy.
- Několik sloupců najednou ve formuláři vektoru, jako jsou `HistoricalPrices` v `HousingData` třídy.

Je-li vlastnost vektoru, použije [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut vlastnosti v datovém modelu. Je důležité si uvědomit, že všechny prvky ve vektoru musí být stejného typu.

ML.NET Operates prostřednictvím názvy sloupců. Pokud chcete změnit název sloupce na jinou hodnotu než název vlastnosti, použijte [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut. Při vytváření objektů v paměti, stále vytvořit objekty pomocí názvu vlastnosti. Ale pro sestavování modelů strojového učení a zpracování dat, ML.NET přepsání a odkazuje na vlastnost s hodnotou součástí [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut.

## <a name="load-data-from-a-single-file"></a>Načtení dat z jednoho souboru

K načtení dat z použití souborů [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metoda spolu s datový model pro data, která mají být načteny. Protože `separatorChar` tabulátory ve výchozím nastavení je parametr, podle potřeby ho změňte pro datový soubor. Pokud váš soubor má záhlaví, nastavit `hasHeader` parametr `true` ignorovat první řádek v souboru a začněte k načtení dat z na druhém řádku.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Načtení dat z více souborů

V případě, že vaše data jsou uložená ve více souborech, jako schéma dat je stejný, ML.NET vám umožní načíst dat z více souborů, které jsou buď ve stejném adresáři, nebo více adresářů.

### <a name="load-from-files-in-a-single-directory"></a>Načíst ze souborů v jednom adresáři

Když jsou všechny datové soubory ve stejném adresáři, použít zástupné znaky v [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Načíst ze souborů ve více adresářů

Chcete-li načíst data z více adresářů, použijte [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) metodu pro vytvoření [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader). Potom použijte [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) metodu a zadejte cesty jednotlivých souborů (zástupné znaky nelze použít).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-streaming-source"></a>Načtení dat z datových proudů zdroje

Kromě načítají se data uložená na disku, ML.NET podporuje načítání dat z různých datových proudů zdrojů, které patří, ale nejsou omezeni na:

- Kolekce v paměti
- JSON/XML
- Databáze

> [!IMPORTANT]
> Všimněte si, že při práci se streamováním zdroje ML.NET očekává, že vstupem bude ve formuláři kolekci v paměti. Proto při práci se zdroji, jako je JSON nebo XML, ujistěte se, že pro zobrazení dat v kolekci v paměti.

Daný následující kolekce v paměti:

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

Načtení kolekce v paměti do [ `IDataView` ](xref:Microsoft.ML.IDataView) s [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
