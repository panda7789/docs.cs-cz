---
title: Kontrola mezilehlých dat během zpracování ML.NET
description: Zjistěte, jak kontrolovat zprostředkující data během ML.NET načtení, zpracování, zpracování a školení modelu v ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977088"
---
# <a name="inspect-intermediate-data-during-processing"></a>Kontrola mezilehlých dat během zpracování

Zjistěte, jak kontrolovat zprostředkující data během načítání, zpracování a kroky školení modelu v ML.NET. Mezilehlá data jsou výstupem každé fáze kanálu strojového učení.

Mezilehlá data, jako je ta, která jsou znázorněna níže, která je načtena do, [`IDataView`](xref:Microsoft.ML.IDataView) mohou být kontrolována různými způsoby v ML.NET.

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

## <a name="convert-idataview-to-ienumerable"></a>Převést zobrazení IDataView na ienumerable

Jedním z nejrychlejších způsobů, [`IDataView`](xref:Microsoft.ML.IDataView) jak zkontrolovat, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)je převést na . Chcete-li [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) převést [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) použít metodu.

Chcete-li optimalizovat `reuseRowObject` `true`výkon, nastavte na . Tím se líně naplní stejný objekt s daty aktuálního řádku, jak je vyhodnocován na rozdíl od vytvoření nového objektu pro každý řádek v datové sadě.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>Přístup ke konkrétním indexům s početně spořitelnou

Pokud potřebujete přístup pouze k části dat nebo ke [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) konkrétním indexům, použijte a nastavte hodnotu `reuseRowObject` parametru tak, aby `false` byl vytvořen nový objekt pro každý z požadovaných řádků v datové sadě. Potom převeďte na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pole nebo seznam.

> [!WARNING]
> Převod výsledku [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) na pole nebo seznam načte [`IDataView`](xref:Microsoft.ML.IDataView) všechny požadované řádky do paměti, což může ovlivnit výkon.

Po vytvoření kolekce můžete provádět operace s daty. Fragment kódu níže trvá první tři řádky v datové sadě a vypočítá průměrnou aktuální cenu.

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

V libovolném bodě procesu vytváření modelu hodnoty [`IDataView`](xref:Microsoft.ML.IDataView) v jednom sloupci [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) modelu lze přistupovat pomocí metody. Metoda [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) vrátí všechny hodnoty v jednom sloupci [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)jako .

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Kontrola hodnot IDataView po jednom řádku

[`IDataView`](xref:Microsoft.ML.IDataView)je líně hodnocena. Chcete-li iterate přes [`IDataView`](xref:Microsoft.ML.IDataView) řádky bez [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) převodu na jak je znázorněno [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) v předchozích částech tohoto dokumentu, vytvořte [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) pomocí [`IDataView`](xref:Microsoft.ML.IDataView) metody a předávání [dataViewSchema](xref:Microsoft.ML.DataViewSchema) vašeho jako parametr. Potom iterát přes řádky, [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) použijte metodu [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) kurzor spolu s delegáty extrahovat příslušné hodnoty z každého sloupce.

> [!IMPORTANT]
> Pro účely výkonu vektory [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) v ML.NET místo nativních `Vector``float[]`typů kolekcí (tj. ).

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Náhled výsledku předběžného zpracování nebo trénování na podmnožině dat

> [!WARNING]
> Nepoužívejte `Preview` v produkčním kódu, protože je určen pro ladění a může snížit výkon.

Proces vytváření modelů je experimentální a iterativní. Chcete-li zobrazit náhled, jak by data vypadala po předběžném zpracování nebo trénování modelu strojového učení v podmnožině dat, použijte metodu, [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) která vrátí [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview). Výsledkem je objekt `ColumnView` `RowView` s vlastnostmi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) a vlastnosti, které jsou a obsahují hodnoty v určitém sloupci nebo řádku. Zadejte počet řádků, na které `maxRows` se má transformace použít s parametrem.

![Objekt náhledu ladicího programu dat](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Výsledek kontroly [`IDataView`](xref:Microsoft.ML.IDataView) by vypadat podobně jako následující:

![Zobrazení náhledu řádku ladicího programu dat](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
