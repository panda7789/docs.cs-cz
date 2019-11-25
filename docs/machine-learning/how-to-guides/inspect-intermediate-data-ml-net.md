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
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="cceb7-103">Kontrolovat mezilehlé údaje během zpracování</span><span class="sxs-lookup"><span data-stu-id="cceb7-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="cceb7-104">Naučte se kontrolovat mezilehlé údaje během nasazování, zpracování a postupu přípravy modelů v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="cceb7-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="cceb7-105">Mezilehlé údaje jsou výstupem každé fáze v kanálu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="cceb7-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="cceb7-106">Mezilehlé údaje, jako je ta, která je reprezentovaná níže, která se načtou do [`IDataView`](xref:Microsoft.ML.IDataView) , se dají v ml.NET kontrolovat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="cceb7-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="cceb7-107">Převést IDataView na IEnumerable</span><span class="sxs-lookup"><span data-stu-id="cceb7-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="cceb7-108">Jedním z nejrychlejších způsobů, jak zkontrolovat [`IDataView`](xref:Microsoft.ML.IDataView) , je převést ho na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="cceb7-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="cceb7-109">Chcete-li převést [`IDataView`](xref:Microsoft.ML.IDataView) pro [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) použijte metodu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="cceb7-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="cceb7-110">Pokud chcete optimalizovat výkon, nastavte `reuseRowObject` na `true`.</span><span class="sxs-lookup"><span data-stu-id="cceb7-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="cceb7-111">Tím se laxně vytvářená naplní stejný objekt daty aktuálního řádku, protože se vyhodnocuje jako protiklad k vytvoření nového objektu pro každý řádek v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="cceb7-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="cceb7-112">Přístup ke specifickým indexům pomocí IEnumerable</span><span class="sxs-lookup"><span data-stu-id="cceb7-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="cceb7-113">Pokud potřebujete přístup pouze k částem dat nebo konkrétním indexům, použijte [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a nastavte hodnotu parametru `reuseRowObject` na `false`, takže se vytvoří nový objekt pro každý z požadovaných řádků v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="cceb7-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="cceb7-114">Pak převeďte [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) na pole nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="cceb7-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="cceb7-115">Převod výsledku [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) na pole nebo seznam načte všechny požadované [`IDataView`](xref:Microsoft.ML.IDataView) řádky do paměti, což může mít vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="cceb7-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="cceb7-116">Po vytvoření kolekce můžete provádět operace s daty.</span><span class="sxs-lookup"><span data-stu-id="cceb7-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="cceb7-117">Následující fragment kódu přebírá první tři řádky v datové sadě a vypočítá průměrnou aktuální cenu.</span><span class="sxs-lookup"><span data-stu-id="cceb7-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="cceb7-118">Kontrola hodnot v jednom sloupci</span><span class="sxs-lookup"><span data-stu-id="cceb7-118">Inspect values in a single column</span></span>

<span data-ttu-id="cceb7-119">V každém okamžiku procesu vytváření modelu lze k hodnotám v jednom sloupci [`IDataView`](xref:Microsoft.ML.IDataView) přicházet pomocí metody [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) .</span><span class="sxs-lookup"><span data-stu-id="cceb7-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="cceb7-120">Metoda [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) vrátí všechny hodnoty v jednom sloupci jako [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="cceb7-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="cceb7-121">Kontrolovat IDataView hodnoty po jednotlivých řádcích</span><span class="sxs-lookup"><span data-stu-id="cceb7-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="cceb7-122">vyhodnocený [`IDataView`](xref:Microsoft.ML.IDataView) je laxně vytvářená.</span><span class="sxs-lookup"><span data-stu-id="cceb7-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="cceb7-123">Chcete-li iterovat řádky [`IDataView`](xref:Microsoft.ML.IDataView) bez převodu na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) jak je znázorněno v předchozích částech tohoto dokumentu, vytvořte [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) pomocí metody [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) a předejte [DataViewSchema](xref:Microsoft.ML.DataViewSchema) [`IDataView`](xref:Microsoft.ML.IDataView) jako parametr.</span><span class="sxs-lookup"><span data-stu-id="cceb7-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="cceb7-124">Chcete-li iterovat řádky, použijte metodu [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) kurzoru společně s [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegáty k extrakci příslušných hodnot z každého sloupce.</span><span class="sxs-lookup"><span data-stu-id="cceb7-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cceb7-125">Pro účely výkonu vektory v ML.NET používají [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) namísto nativních typů kolekcí (to znamená `Vector``float[]`).</span><span class="sxs-lookup"><span data-stu-id="cceb7-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="cceb7-126">Náhled výsledku předběžného zpracování nebo školení pro podmnožinu dat</span><span class="sxs-lookup"><span data-stu-id="cceb7-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="cceb7-127">Nepoužívejte `Preview` v produkčním kódu, protože je určen pro ladění a může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="cceb7-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="cceb7-128">Proces sestavení modelu je experimentální a iterativní.</span><span class="sxs-lookup"><span data-stu-id="cceb7-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="cceb7-129">Chcete-li zobrazit náhled toho, jaká data by vypadala po předběžném zpracování nebo školení modelu strojového učení pro podmnožinu dat, použijte metodu [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) , která vrací [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="cceb7-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="cceb7-130">Výsledkem je objekt s `ColumnView` a `RowView` vlastností, které jsou [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) a obsahují hodnoty z konkrétního sloupce nebo řádku.</span><span class="sxs-lookup"><span data-stu-id="cceb7-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="cceb7-131">Zadejte počet řádků, na které se má transformace použít s parametrem `maxRows`.</span><span class="sxs-lookup"><span data-stu-id="cceb7-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Objekt náhledu data debuggeru](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="cceb7-133">Výsledek kontroly [`IDataView`](xref:Microsoft.ML.IDataView) by vypadal podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cceb7-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Zobrazení řádku náhledu data debuggeru](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
