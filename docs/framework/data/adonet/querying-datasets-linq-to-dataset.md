---
title: "Dotazování datové sady (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21c4b2a37dfc9a7c570b39fa164267f90fa7055d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="6cc67-102">Dotazování datové sady (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="6cc67-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="6cc67-103">Po <xref:System.Data.DataSet> objekt naplněné s daty, můžete začít dotazování ho.</span><span class="sxs-lookup"><span data-stu-id="6cc67-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="6cc67-104">Formulování dotazy s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] je podobný používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti dalších [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-povolené datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="6cc67-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="6cc67-105">Nezapomeňte, ale, že při použití [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazuje přes <xref:System.Data.DataSet> objekt dotazujete výčet <xref:System.Data.DataRow> objekty, místo výčet vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="6cc67-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="6cc67-106">To znamená, že můžete použít některý z členů <xref:System.Data.DataRow> tříd ve vaší [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="6cc67-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="6cc67-107">Umožňuje vytvořit bohatě a složité dotazy.</span><span class="sxs-lookup"><span data-stu-id="6cc67-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="6cc67-108">Stejně jako u jiných implementace [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], můžete vytvořit [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazů ve dvou různých formách: výraz syntaxe využívající dotazy a syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="6cc67-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="6cc67-109">Další informace o těchto dvou formách najdete v tématu [Začínáme s dotazy LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span><span class="sxs-lookup"><span data-stu-id="6cc67-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="6cc67-110">Můžete použít syntaxe výrazu dotazu nebo syntaxe dotazu na základě metod provádět dotazy proti jedné tabulky v <xref:System.Data.DataSet>, před několika tabulkám ve <xref:System.Data.DataSet>, nebo podle tabulky v zadaný <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6cc67-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6cc67-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6cc67-111">In This Section</span></span>  
 [<span data-ttu-id="6cc67-112">Dotazy na jednu tabulku</span><span class="sxs-lookup"><span data-stu-id="6cc67-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="6cc67-113">Popisuje, jak provádět dotazy jedné tabulky.</span><span class="sxs-lookup"><span data-stu-id="6cc67-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="6cc67-114">Dotazy na křížovou tabulku</span><span class="sxs-lookup"><span data-stu-id="6cc67-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="6cc67-115">Popisuje, jak provádět dotazy křížové tabulky.</span><span class="sxs-lookup"><span data-stu-id="6cc67-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="6cc67-116">Dotazy na typové datové sady</span><span class="sxs-lookup"><span data-stu-id="6cc67-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="6cc67-117">Popisuje, jak dotazovat zadali <xref:System.Data.DataSet> objekty.</span><span class="sxs-lookup"><span data-stu-id="6cc67-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc67-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cc67-118">See Also</span></span>  
 [<span data-ttu-id="6cc67-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6cc67-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="6cc67-120">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="6cc67-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
