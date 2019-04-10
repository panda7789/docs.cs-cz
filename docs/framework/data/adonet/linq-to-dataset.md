---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 92be418e38039757437e6e673f39a7baef011528
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221779"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="f0f77-102">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="f0f77-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="f0f77-103">zajišťuje snadnější a rychlejší dotaz data uložená v mezipaměti <xref:System.Data.DataSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="f0f77-103">makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="f0f77-104">Konkrétně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy v programovacím jazyce, nikoli pomocí samostatné dotazovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="f0f77-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="f0f77-105">To je užitečné zejména pro Visual Studio získávají vývojáři, kteří můžou využívat kontrola syntaxe v době kompilace, psát statické, a podporu technologie IntelliSense poskytovaný sadou Visual Studio ve svých dotazech.</span><span class="sxs-lookup"><span data-stu-id="f0f77-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="f0f77-106">Můžete také použít k dotazu nad daty, který byl sloučen z jednoho nebo více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="f0f77-106">can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="f0f77-107">To umožňuje mnoho scénářů, které potřebují flexibilně jak data jsou reprezentovány a zpracována, jako jsou například dotazování místně agregovaná data a střední vrstvy, ukládání do mezipaměti ve webových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="f0f77-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="f0f77-108">Tato metoda manipulaci s vyžadují zejména obecné vytváření sestav, analýzy a v aplikacích business intelligence.</span><span class="sxs-lookup"><span data-stu-id="f0f77-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="f0f77-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkce se zveřejňuje prostřednictvím metody rozšíření v především <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f77-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="f0f77-110">navazuje na a použije existující [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architektury a není určena k nahrazení [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0f77-110">builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="f0f77-111">Stávající kód technologie ADO.NET 2.0 bude i nadále fungovat v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0f77-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="f0f77-112">Vztah mezi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] k [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] a úložiště dat je znázorněn v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="f0f77-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagram znázorňující, že LINQ to DataSet je založen na zprostředkovatele rozhraní ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="f0f77-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f0f77-114">In This Section</span></span>  
 [<span data-ttu-id="f0f77-115">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f0f77-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="f0f77-116">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="f0f77-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="f0f77-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f0f77-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="f0f77-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0f77-118">See also</span></span>

- [<span data-ttu-id="f0f77-119">Language-Integrated Query (LINQ) –C#</span><span class="sxs-lookup"><span data-stu-id="f0f77-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f0f77-120">Language-Integrated Query (LINQ) – Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0f77-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f0f77-121">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f0f77-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="f0f77-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f0f77-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
