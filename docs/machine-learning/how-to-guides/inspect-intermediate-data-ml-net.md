---
title: Zkontrolovat hodnoty dočasných dat během zpracování ML.NET
description: Zjistěte, jak zkontrolovat hodnoty skutečné dočasných dat během ML.NET strojového učení zpracování kanálu
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 06c4a473841db62a10dfc24025f842df7ae2c583
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063521"
---
# <a name="inspect-intermediate-data-values-during-processing"></a><span data-ttu-id="f8b8e-103">Zkontrolovat hodnoty dočasných dat během zpracování</span><span class="sxs-lookup"><span data-stu-id="f8b8e-103">Inspect intermediate data values during processing</span></span>

<span data-ttu-id="f8b8e-104">Zjistěte, jak zkontrolovat hodnoty během zpracování a kroky školení v ML.NET načítání.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-104">Learn how to inspect values during loading, processing and training steps in ML.NET.</span></span>

<span data-ttu-id="f8b8e-105">Data, jako je ten reprezentované níže, který je načten do [ `IDataView` ](xref:Microsoft.ML.IDataView) můžete prozkoumat v ML.NET různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-105">Data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>
 
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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="f8b8e-106">Převést na typ IEnumerable IDataView</span><span class="sxs-lookup"><span data-stu-id="f8b8e-106">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="f8b8e-107">Jedním z nejrychleji způsobů ke kontrole hodnoty [ `IDataView` ](xref:Microsoft.ML.IDataView) je převeďte ho na [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="f8b8e-107">One of the quickest ways to inspect the values of an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="f8b8e-108">Převést [ `IDataView` ](xref:Microsoft.ML.IDataView) k [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) použít [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metoda.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-108">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span> 

<span data-ttu-id="f8b8e-109">K zajištění optimálního výkonu nastavte hodnotu `reuseRowObject` k `true`.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-109">To optimize performance, set the value of `reuseRowObject` to `true`.</span></span> <span data-ttu-id="f8b8e-110">Tím se laxně vyplňte na stejný objekt s daty na aktuálním řádku, jak se vyhodnocuje na rozdíl od vytvoření nového objektu pro každý řádek v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-110">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

<span data-ttu-id="f8b8e-111">Pokud potřebujete jenom přístup k část dat nebo konkrétní indexy, použijte [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a nastavit `reuseRowObject` pro parametr `false` tak, že je vytvořen nový objekt pro každou z požadovaných řádků v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-111">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="f8b8e-112">Poté převeďte [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) pole nebo seznamu.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-112">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="f8b8e-113">Výsledek převodu [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pole nebo seznamu se načtou všechny požadované [ `IDataView` ](xref:Microsoft.ML.IDataView) řádků do paměti, což může mít vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-113">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="f8b8e-114">Po vytvoření kolekce můžete provádět operace s daty.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-114">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="f8b8e-115">Následující fragment kódu přijímá první tři řádky v datové sadě a vypočítá průměrná aktuální cena.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-115">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="f8b8e-116">Zkontrolujte hodnoty v jednom sloupci</span><span class="sxs-lookup"><span data-stu-id="f8b8e-116">Inspect values in a single column</span></span>

<span data-ttu-id="f8b8e-117">Kdykoli v modelu procesu, vytváření hodnoty v jednom sloupci z [ `IDataView` ](xref:Microsoft.ML.IDataView) lze přistupovat pomocí [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-117">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="f8b8e-118">[ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Metoda vrátí všechny hodnoty v jednom sloupci jako [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="f8b8e-118">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="f8b8e-119">Kontrola IDataView hodnoty jeden řádek v čase</span><span class="sxs-lookup"><span data-stu-id="f8b8e-119">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="f8b8e-120">[`IDataView`](xref:Microsoft.ML.IDataView) laxně vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-120">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="f8b8e-121">K iteraci přes řádky [ `IDataView` ](xref:Microsoft.ML.IDataView) bez převodu do [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) jak je ukázáno v předchozích částech tohoto dokumentu, vytvoření [ `DataViewRowCursor` ](xref:Microsoft.ML.DataViewRowCursor) pomocí [ `GetRowCursor` ](xref:Microsoft.ML.IDataView.GetRowCursor*) metoda a předání [DataViewSchema](xref:Microsoft.ML.DataViewSchema) z vaší [ `IDataView` ](xref:Microsoft.ML.IDataView) jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-121">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="f8b8e-122">Potom k iteraci přes řádků, použijte [ `MoveNext` ](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) kurzor metoda spolu s [ `ValueGetter` ](xref:Microsoft.ML.ValueGetter%601) delegáty k extrakci příslušných hodnot ze všech sloupců.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-122">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8b8e-123">Z důvodů výkonu vektory ML.NET používá [ `VBuffer` ](xref:Microsoft.ML.Data.VBuffer%601) místo nativní kolekci typů (to znamená `Vector`,`float[]`).</span><span class="sxs-lookup"><span data-stu-id="f8b8e-123">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span> 

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="f8b8e-124">Ve verzi Preview výsledek předběžného zpracování nebo školení na podmnožinu dat.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-124">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="f8b8e-125">Nepoužívejte `Preview` v produkčním kódu, protože je určena pro ladění a může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-125">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="f8b8e-126">Proces vytváření modelu je experimentální a iterační.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-126">The model building process is experimental and iterative.</span></span> <span data-ttu-id="f8b8e-127">Náhled, co by data vypadat po předběžném zpracování nebo cvičení modelu strojového učení na podmnožinu dat, použijte [ `Preview` ](xref:Microsoft.ML.DebuggerExtensions.Preview*) metodu, která vrátí [ `DataDebuggerPreview` ](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="f8b8e-127">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="f8b8e-128">Výsledkem je objekt s `ColumnView` a `RowView` vlastnosti, které jsou [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) a obsahují hodnoty v určitém sloupci nebo řádku.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-128">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="f8b8e-129">Zadejte počet řádků, které mají transformace, která se vztahují `maxRows` parametru.</span><span class="sxs-lookup"><span data-stu-id="f8b8e-129">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Datový objekt ve verzi Preview ladicího programu](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="f8b8e-131">Výsledek kontroly [ `IDataView` ](xref:Microsoft.ML.IDataView) by vypadalo podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="f8b8e-131">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Zobrazení dat ladicího programu řádku ve verzi Preview](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
