---
title: "Průvodce programováním (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1332bf297dae4baae62d2abd731d236ad49be4ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="37693-102">Průvodce programováním (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="37693-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="37693-103">Tato část obsahuje koncepční informace a příklady pro programování s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37693-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37693-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="37693-104">In This Section</span></span>  
 [<span data-ttu-id="37693-105">Dotazy v LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="37693-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="37693-106">Poskytuje informace o tom, jak psát [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="37693-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="37693-107">Dotazování datové sady</span><span class="sxs-lookup"><span data-stu-id="37693-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="37693-108">Popisuje postup dotazu <xref:System.Data.DataSet> objekty.</span><span class="sxs-lookup"><span data-stu-id="37693-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="37693-109">Porovnání DataRows</span><span class="sxs-lookup"><span data-stu-id="37693-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="37693-110">Popisuje postup použití <xref:System.Data.DataRowComparer> objekt k porovnání dat řádků.</span><span class="sxs-lookup"><span data-stu-id="37693-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="37693-111">Vytváření DataTable z dotazu</span><span class="sxs-lookup"><span data-stu-id="37693-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="37693-112">Poskytuje informace o vytváření <xref:System.Data.DataTable> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu pomocí <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="37693-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="37693-113">Postupy: implementace CopyToDataTable\<T > kde obecného typu T není DataRow</span><span class="sxs-lookup"><span data-stu-id="37693-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="37693-114">Popisuje, jak implementovat vlastní `CopyToDataTable<T>` metoda, kde T obecný parametr není typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="37693-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="37693-115">Obecné pole a SetField metody</span><span class="sxs-lookup"><span data-stu-id="37693-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="37693-116">Poskytuje informace o Obecné <xref:System.Data.DataRowExtensions.Field%2A> a <xref:System.Data.DataRowExtensions.SetField%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="37693-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="37693-117">Datové vazby a LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="37693-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="37693-118">Popisuje použití datových vazeb <xref:System.Data.DataView> objektu.</span><span class="sxs-lookup"><span data-stu-id="37693-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="37693-119">Ladění LINQ na dotazy, datové sady</span><span class="sxs-lookup"><span data-stu-id="37693-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="37693-120">Poskytuje informace o ladění a řešení potíží s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="37693-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="37693-121">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="37693-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="37693-122">Popisuje problémy se zabezpečením v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37693-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="37693-123">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="37693-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="37693-124">Obsahuje příklady dotazů, které používají [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátory.</span><span class="sxs-lookup"><span data-stu-id="37693-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="37693-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="37693-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="37693-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="37693-126">See Also</span></span>  
 [<span data-ttu-id="37693-127">Technologie LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="37693-127">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [<span data-ttu-id="37693-128">NEBYL v sestavení: Průvodce programováním v obecné LINQ</span><span class="sxs-lookup"><span data-stu-id="37693-128">NOT IN BUILD: LINQ General Programming Guide</span></span>](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049)  
 [<span data-ttu-id="37693-129">LINQ Framework</span><span class="sxs-lookup"><span data-stu-id="37693-129">LINQ Framework</span></span>](http://msdn.microsoft.com/en-us/897ea0fc-40db-4694-bbe5-7dd339d5bf94)
