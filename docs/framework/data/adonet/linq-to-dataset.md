---
title: LINQ na DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de0f11149c2ec587372b9e25f39f35f8552503c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset"></a><span data-ttu-id="5c136-102">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="5c136-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="5c136-103">umožňuje snadnější a rychlejší dotazu přes data uložená v mezipaměti <xref:System.Data.DataSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="5c136-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="5c136-104">Konkrétně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy z programovací jazyk, samostatně, místo pomocí samostatných dotazovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="5c136-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="5c136-105">To je užitečné zejména pro [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] vývojáři, kteří teď můžete využít výhod kontrolu syntaxe kompilaci, zadáním statické, a poskytuje podporu technologie IntelliSense [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] jejich dotazů.</span><span class="sxs-lookup"><span data-stu-id="5c136-105">This is especially useful for [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="5c136-106">Můžete také použít k dotazu přes data, která byla konsolidována z jednoho nebo více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="5c136-106"> can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="5c136-107">To umožňuje mnoho scénářů, které vyžadují flexibilitu při jak data jsou reprezentována a zpracovávají, jako je například dotazování místně agregovaná data a střední vrstvy ukládání do mezipaměti ve webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="5c136-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="5c136-108">Obecné sestavy, analýzu a aplikace pro business intelligence klást tato metoda manipulaci.</span><span class="sxs-lookup"><span data-stu-id="5c136-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="5c136-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkce je zveřejněna primárně prostřednictvím metody rozšíření v <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy.</span><span class="sxs-lookup"><span data-stu-id="5c136-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="5c136-110">staví na a používá existující [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architekturu a není určena k nahrazení [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c136-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="5c136-111">Existující kód ADO.NET 2.0 budou nadále fungovat v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c136-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="5c136-112">Vztah [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] k [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] a úložiště dat je znázorněno v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="5c136-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="5c136-113">![LINQ na DataSet je založena na zprostředkovatele ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="5c136-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c136-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5c136-114">In This Section</span></span>  
 [<span data-ttu-id="5c136-115">Začínáme</span><span class="sxs-lookup"><span data-stu-id="5c136-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="5c136-116">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="5c136-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="5c136-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5c136-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="5c136-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c136-118">See Also</span></span>  
 [<span data-ttu-id="5c136-119">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="5c136-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="5c136-120">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5c136-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="5c136-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5c136-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
