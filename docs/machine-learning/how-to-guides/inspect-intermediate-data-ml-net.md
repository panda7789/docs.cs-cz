---
title: Kontrola dočasných dat během zpracování ML.NET
description: Zjistěte, jak kontrolovat dočasných dat během ML.NET strojového učení kanálu načítání, zpracování a kroky ML.NET cvičení modelu.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: d6ddeb523fb229eb0ebc9c2f22809312060e4266
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402391"
---
# <a name="inspect-intermediate-data-during-processing"></a>Kontrola dočasných dat během zpracování

Zjistěte, jak kontrolovat dočasných dat během načítání, zpracování a kroky trénování modelu v ML.NET. Dočasných dat je výstup každou z fází strojového učení kanálu.

Dočasných dat, jako je ten reprezentované níže, který je načten do [ `IDataView` ](xref:Microsoft.ML.IDataView) můžete prozkoumat v ML.NET různými způsoby.
 
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

## <a name="convert-idataview-to-ienumerable"></a>Převést na typ IEnumerable IDataView

Jedním z nejrychleji způsobů ke kontrole [ `IDataView` ](xref:Microsoft.ML.IDataView) je převeďte ho na [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601). Převést [ `IDataView` ](xref:Microsoft.ML.IDataView) k [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) použít [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metoda. 

Chcete-li optimalizovat výkon, nastavte `reuseRowObject` k `true`. Tím se laxně vyplňte na stejný objekt s daty na aktuálním řádku, jak se vyhodnocuje na rozdíl od vytvoření nového objektu pro každý řádek v datové sadě.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>Přístup k určité indexy s IEnumerable

Pokud potřebujete jenom přístup k část dat nebo konkrétní indexy, použijte [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a nastavit `reuseRowObject` pro parametr `false` tak, že je vytvořen nový objekt pro každou z požadovaných řádků v datové sadě. Poté převeďte [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) pole nebo seznamu.

> [!WARNING]
> Výsledek převodu [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pole nebo seznamu se načtou všechny požadované [ `IDataView` ](xref:Microsoft.ML.IDataView) řádků do paměti, což může mít vliv na výkon.

Po vytvoření kolekce můžete provádět operace s daty. Následující fragment kódu přijímá první tři řádky v datové sadě a vypočítá průměrná aktuální cena.

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

## <a name="inspect-values-in-a-single-column"></a>Zkontrolujte hodnoty v jednom sloupci

Kdykoli v modelu procesu, vytváření hodnoty v jednom sloupci z [ `IDataView` ](xref:Microsoft.ML.IDataView) lze přistupovat pomocí [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody. [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Metoda vrátí všechny hodnoty v jednom sloupci jako [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Kontrola IDataView hodnoty jeden řádek v čase

[`IDataView`](xref:Microsoft.ML.IDataView) laxně vyhodnocena. K iteraci přes řádky [ `IDataView` ](xref:Microsoft.ML.IDataView) bez převodu do [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) jak je ukázáno v předchozích částech tohoto dokumentu, vytvoření [ `DataViewRowCursor` ](xref:Microsoft.ML.DataViewRowCursor) pomocí [ `GetRowCursor` ](xref:Microsoft.ML.IDataView.GetRowCursor*) metoda a předání [DataViewSchema](xref:Microsoft.ML.DataViewSchema) z vaší [ `IDataView` ](xref:Microsoft.ML.IDataView) jako parametr. Potom k iteraci přes řádků, použijte [ `MoveNext` ](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) kurzor metoda spolu s [ `ValueGetter` ](xref:Microsoft.ML.ValueGetter%601) delegáty k extrakci příslušných hodnot ze všech sloupců.

> [!IMPORTANT]
> Z důvodů výkonu vektory ML.NET používá [ `VBuffer` ](xref:Microsoft.ML.Data.VBuffer%601) místo nativní kolekci typů (to znamená `Vector`,`float[]`). 

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Ve verzi Preview výsledek předběžného zpracování nebo školení na podmnožinu dat.

> [!WARNING]
> Nepoužívejte `Preview` v produkčním kódu, protože je určena pro ladění a může snížit výkon.

Proces vytváření modelu je experimentální a iterační. Náhled, co by data vypadat po předběžném zpracování nebo cvičení modelu strojového učení na podmnožinu dat, použijte [ `Preview` ](xref:Microsoft.ML.DebuggerExtensions.Preview*) metodu, která vrátí [ `DataDebuggerPreview` ](xref:Microsoft.ML.Data.DataDebuggerPreview). Výsledkem je objekt s `ColumnView` a `RowView` vlastnosti, které jsou [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) a obsahují hodnoty v určitém sloupci nebo řádku. Zadejte počet řádků, které mají transformace, která se vztahují `maxRows` parametru.

![Datový objekt ve verzi Preview ladicího programu](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Výsledek kontroly [ `IDataView` ](xref:Microsoft.ML.IDataView) by vypadalo podobně jako následující:

![Zobrazení dat ladicího programu řádku ve verzi Preview](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
