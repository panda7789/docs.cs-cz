---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504365"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="ecd68-102">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="ecd68-102">LINQ to DataSet</span></span>
<span data-ttu-id="ecd68-103">Technologie LINQ to DataSet umožňuje jednodušší a rychlejší dotaz na data uložená v mezipaměti <xref:System.Data.DataSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="ecd68-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="ecd68-104">Konkrétně LINQ to DataSet zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy v programovacím jazyce, nikoli pomocí samostatné dotazovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="ecd68-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="ecd68-105">To je užitečné zejména pro Visual Studio získávají vývojáři, kteří můžou využívat kontrola syntaxe v době kompilace, psát statické, a podporu technologie IntelliSense poskytovaný sadou Visual Studio ve svých dotazech.</span><span class="sxs-lookup"><span data-stu-id="ecd68-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="ecd68-106">Technologie LINQ to DataSet lze také použít k dotazu nad daty, který byl sloučen z jednoho nebo více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="ecd68-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="ecd68-107">To umožňuje mnoho scénářů, které potřebují flexibilně jak data jsou reprezentovány a zpracována, jako jsou například dotazování místně agregovaná data a střední vrstvy, ukládání do mezipaměti ve webových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="ecd68-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="ecd68-108">Tato metoda manipulaci s vyžadují zejména obecné vytváření sestav, analýzy a v aplikacích business intelligence.</span><span class="sxs-lookup"><span data-stu-id="ecd68-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="ecd68-109">LINQ to DataSet funkce je k dispozici primárně prostřednictvím metody rozšíření v <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy.</span><span class="sxs-lookup"><span data-stu-id="ecd68-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="ecd68-110">Technologie LINQ to DataSet vychází a používá existující architekturu ADO.NET a není určena k nahrazení technologie ADO.NET v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecd68-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="ecd68-111">Stávající kód technologie ADO.NET bude nadále fungovat v technologii LINQ to DataSet aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecd68-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="ecd68-112">Vztah mezi LINQ to DataSet technologie ADO.NET a úložiště dat je znázorněn v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="ecd68-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagram znázorňující, že LINQ to DataSet je založen na zprostředkovatele rozhraní ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="ecd68-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ecd68-114">In This Section</span></span>  
 [<span data-ttu-id="ecd68-115">Začínáme</span><span class="sxs-lookup"><span data-stu-id="ecd68-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="ecd68-116">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="ecd68-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="ecd68-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ecd68-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="ecd68-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecd68-118">See also</span></span>

- [<span data-ttu-id="ecd68-119">Language-Integrated Query (LINQ) –C#</span><span class="sxs-lookup"><span data-stu-id="ecd68-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="ecd68-120">Language-Integrated Query (LINQ) – Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecd68-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="ecd68-121">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ecd68-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="ecd68-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ecd68-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
