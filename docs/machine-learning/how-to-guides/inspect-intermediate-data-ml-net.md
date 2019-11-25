---
title: Kontrola zprostředkujících dat během zpracování ML.NET
description: Naučte se kontrolovat data během ml.NET nahrávání kanálu, zpracování a modelování kroků školení v ml.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977088"
---
# <a name="inspect-intermediate-data-during-processing"></a>Kontrolovat mezilehlé údaje během zpracování

Naučte se kontrolovat mezilehlé údaje během nasazování, zpracování a postupu přípravy modelů v ML.NET. Mezilehlé údaje jsou výstupem každé fáze v kanálu strojového učení.

Mezilehlé údaje, jako je ta, která je reprezentovaná níže, která se načtou do [`IDataView`](xref:Microsoft.ML.IDataView) , se dají v ml.NET kontrolovat různými způsoby.

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a>Převést IDataView na IEnumerable

Jedním z nejrychlejších způsobů, jak zkontrolovat [`IDataView`](xref:Microsoft.ML.IDataView) , je převést ho na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601). Chcete-li převést [`IDataView`](xref:Microsoft.ML.IDataView) pro [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) použijte metodu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

Pokud chcete optimalizovat výkon, nastavte `reuseRowObject` na `true`. Tím se laxně vytvářená naplní stejný objekt daty aktuálního řádku, protože se vyhodnocuje jako protiklad k vytvoření nového objektu pro každý řádek v datové sadě.

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

## <a name="accessing-specific-indices-with-ienumerable"></a>Přístup ke specifickým indexům pomocí IEnumerable

Pokud potřebujete přístup pouze k částem dat nebo konkrétním indexům, použijte [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a nastavte hodnotu parametru `reuseRowObject` na `false`, takže se vytvoří nový objekt pro každý z požadovaných řádků v datové sadě. Pak převeďte [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) na pole nebo seznam.

> [!WARNING]
> Převod výsledku [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) na pole nebo seznam načte všechny požadované [`IDataView`](xref:Microsoft.ML.IDataView) řádky do paměti, což může mít vliv na výkon.

Po vytvoření kolekce můžete provádět operace s daty. Následující fragment kódu přebírá první tři řádky v datové sadě a vypočítá průměrnou aktuální cenu.

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
```

## <a name="inspect-values-in-a-single-column"></a>Kontrola hodnot v jednom sloupci

V každém okamžiku procesu vytváření modelu lze k hodnotám v jednom sloupci [`IDataView`](xref:Microsoft.ML.IDataView) přicházet pomocí metody [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) . Metoda [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) vrátí všechny hodnoty v jednom sloupci jako [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Kontrolovat IDataView hodnoty po jednotlivých řádcích

vyhodnocený [`IDataView`](xref:Microsoft.ML.IDataView) je laxně vytvářená. Chcete-li iterovat řádky [`IDataView`](xref:Microsoft.ML.IDataView) bez převodu na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) jak je znázorněno v předchozích částech tohoto dokumentu, vytvořte [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) pomocí metody [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) a předejte [DataViewSchema](xref:Microsoft.ML.DataViewSchema) [`IDataView`](xref:Microsoft.ML.IDataView) jako parametr. Chcete-li iterovat řádky, použijte metodu [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) kurzoru společně s [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegáty k extrakci příslušných hodnot z každého sloupce.

> [!IMPORTANT]
> Pro účely výkonu vektory v ML.NET používají [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) namísto nativních typů kolekcí (to znamená `Vector``float[]`).

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);

    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Náhled výsledku předběžného zpracování nebo školení pro podmnožinu dat

> [!WARNING]
> Nepoužívejte `Preview` v produkčním kódu, protože je určen pro ladění a může snížit výkon.

Proces sestavení modelu je experimentální a iterativní. Chcete-li zobrazit náhled toho, jaká data by vypadala po předběžném zpracování nebo školení modelu strojového učení pro podmnožinu dat, použijte metodu [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) , která vrací [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview). Výsledkem je objekt s `ColumnView` a `RowView` vlastností, které jsou [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) a obsahují hodnoty z konkrétního sloupce nebo řádku. Zadejte počet řádků, na které se má transformace použít s parametrem `maxRows`.

![Objekt náhledu data debuggeru](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Výsledek kontroly [`IDataView`](xref:Microsoft.ML.IDataView) by vypadal podobně jako v následujícím příkladu:

![Zobrazení řádku náhledu data debuggeru](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
