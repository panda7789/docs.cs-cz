---
title: Průvodce programováním (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: 6f6ab1634769a54bd8dbafe8c9d41b11ff787d50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637995"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="5a928-102">Průvodce programováním (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5a928-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="5a928-103">Tato část obsahuje rámcové informace a příklady pro programování s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a928-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a928-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5a928-104">In This Section</span></span>  
 [<span data-ttu-id="5a928-105">Dotazy v LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5a928-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="5a928-106">Poskytuje informace o tom, jak psát [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="5a928-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="5a928-107">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="5a928-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="5a928-108">Popisuje, jak provádět dotazy <xref:System.Data.DataSet> objekty.</span><span class="sxs-lookup"><span data-stu-id="5a928-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="5a928-109">Porovnání datových řádků</span><span class="sxs-lookup"><span data-stu-id="5a928-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="5a928-110">Popisuje způsob použití <xref:System.Data.DataRowComparer> objekt k porovnání datových řádků.</span><span class="sxs-lookup"><span data-stu-id="5a928-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="5a928-111">Vytvoření datové tabulky z dotazu</span><span class="sxs-lookup"><span data-stu-id="5a928-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="5a928-112">Poskytuje informace o vytváření <xref:System.Data.DataTable> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu pomocí <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a928-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="5a928-113">Postupy: Implementace CopyToDataTable\<T > kde obecný typ není DataRow</span><span class="sxs-lookup"><span data-stu-id="5a928-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="5a928-114">Popisuje, jak implementovat vlastní `CopyToDataTable<T>` metody, kde není obecný parametr T typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="5a928-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="5a928-115">Obecné pole a metody SetField</span><span class="sxs-lookup"><span data-stu-id="5a928-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="5a928-116">Poskytuje informace o Obecné <xref:System.Data.DataRowExtensions.Field%2A> a <xref:System.Data.DataRowExtensions.SetField%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a928-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="5a928-117">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5a928-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="5a928-118">Popisuje použití vázání dat <xref:System.Data.DataView> objektu.</span><span class="sxs-lookup"><span data-stu-id="5a928-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="5a928-119">Ladění dotazů v LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5a928-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="5a928-120">Poskytuje informace o ladění a řešení potíží s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="5a928-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="5a928-121">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5a928-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="5a928-122">Popisuje problémy se zabezpečením v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a928-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="5a928-123">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5a928-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="5a928-124">Poskytuje příklady dotazů, které používají [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátory.</span><span class="sxs-lookup"><span data-stu-id="5a928-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a928-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5a928-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="5a928-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a928-126">See also</span></span>

- [<span data-ttu-id="5a928-127">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5a928-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="5a928-128">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="5a928-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
