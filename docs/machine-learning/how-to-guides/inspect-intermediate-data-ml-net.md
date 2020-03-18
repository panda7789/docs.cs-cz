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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="ff2f0-103">Kontrola mezilehlých dat během zpracování</span><span class="sxs-lookup"><span data-stu-id="ff2f0-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="ff2f0-104">Zjistěte, jak kontrolovat zprostředkující data během načítání, zpracování a kroky školení modelu v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="ff2f0-105">Mezilehlá data jsou výstupem každé fáze kanálu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="ff2f0-106">Mezilehlá data, jako je ta, která jsou znázorněna níže, která je načtena do, [`IDataView`](xref:Microsoft.ML.IDataView) mohou být kontrolována různými způsoby v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="ff2f0-107">Převést zobrazení IDataView na ienumerable</span><span class="sxs-lookup"><span data-stu-id="ff2f0-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="ff2f0-108">Jedním z nejrychlejších způsobů, [`IDataView`](xref:Microsoft.ML.IDataView) jak zkontrolovat, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)je převést na .</span><span class="sxs-lookup"><span data-stu-id="ff2f0-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="ff2f0-109">Chcete-li [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) převést [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) použít metodu.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="ff2f0-110">Chcete-li optimalizovat `reuseRowObject` `true`výkon, nastavte na .</span><span class="sxs-lookup"><span data-stu-id="ff2f0-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="ff2f0-111">Tím se líně naplní stejný objekt s daty aktuálního řádku, jak je vyhodnocován na rozdíl od vytvoření nového objektu pro každý řádek v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="ff2f0-112">Přístup ke konkrétním indexům s početně spořitelnou</span><span class="sxs-lookup"><span data-stu-id="ff2f0-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="ff2f0-113">Pokud potřebujete přístup pouze k části dat nebo ke [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) konkrétním indexům, použijte a nastavte hodnotu `reuseRowObject` parametru tak, aby `false` byl vytvořen nový objekt pro každý z požadovaných řádků v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="ff2f0-114">Potom převeďte na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pole nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="ff2f0-115">Převod výsledku [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) na pole nebo seznam načte [`IDataView`](xref:Microsoft.ML.IDataView) všechny požadované řádky do paměti, což může ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="ff2f0-116">Po vytvoření kolekce můžete provádět operace s daty.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="ff2f0-117">Fragment kódu níže trvá první tři řádky v datové sadě a vypočítá průměrnou aktuální cenu.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="ff2f0-118">Kontrola hodnot v jednom sloupci</span><span class="sxs-lookup"><span data-stu-id="ff2f0-118">Inspect values in a single column</span></span>

<span data-ttu-id="ff2f0-119">V libovolném bodě procesu vytváření modelu hodnoty [`IDataView`](xref:Microsoft.ML.IDataView) v jednom sloupci [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) modelu lze přistupovat pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="ff2f0-120">Metoda [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) vrátí všechny hodnoty v jednom sloupci [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)jako .</span><span class="sxs-lookup"><span data-stu-id="ff2f0-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="ff2f0-121">Kontrola hodnot IDataView po jednom řádku</span><span class="sxs-lookup"><span data-stu-id="ff2f0-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="ff2f0-122">[`IDataView`](xref:Microsoft.ML.IDataView)je líně hodnocena.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="ff2f0-123">Chcete-li iterate přes [`IDataView`](xref:Microsoft.ML.IDataView) řádky bez [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) převodu na jak je znázorněno [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) v předchozích částech tohoto dokumentu, vytvořte [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) pomocí [`IDataView`](xref:Microsoft.ML.IDataView) metody a předávání [dataViewSchema](xref:Microsoft.ML.DataViewSchema) vašeho jako parametr.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="ff2f0-124">Potom iterát přes řádky, [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) použijte metodu [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) kurzor spolu s delegáty extrahovat příslušné hodnoty z každého sloupce.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff2f0-125">Pro účely výkonu vektory [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) v ML.NET místo nativních `Vector``float[]`typů kolekcí (tj. ).</span><span class="sxs-lookup"><span data-stu-id="ff2f0-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="ff2f0-126">Náhled výsledku předběžného zpracování nebo trénování na podmnožině dat</span><span class="sxs-lookup"><span data-stu-id="ff2f0-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="ff2f0-127">Nepoužívejte `Preview` v produkčním kódu, protože je určen pro ladění a může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="ff2f0-128">Proces vytváření modelů je experimentální a iterativní.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="ff2f0-129">Chcete-li zobrazit náhled, jak by data vypadala po předběžném zpracování nebo trénování modelu strojového učení v podmnožině dat, použijte metodu, [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) která vrátí [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="ff2f0-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="ff2f0-130">Výsledkem je objekt `ColumnView` `RowView` s vlastnostmi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) a vlastnosti, které jsou a obsahují hodnoty v určitém sloupci nebo řádku.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="ff2f0-131">Zadejte počet řádků, na které `maxRows` se má transformace použít s parametrem.</span><span class="sxs-lookup"><span data-stu-id="ff2f0-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Objekt náhledu ladicího programu dat](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="ff2f0-133">Výsledek kontroly [`IDataView`](xref:Microsoft.ML.IDataView) by vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="ff2f0-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Zobrazení náhledu řádku ladicího programu dat](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
