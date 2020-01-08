---
title: Průvodce programováním (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: dc13af06cf6c439d739d76904f206ebc50ba3187
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634804"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="66f72-102">Průvodce programováním (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="66f72-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="66f72-103">Tato část obsahuje koncepční informace a příklady pro programování s LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="66f72-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66f72-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="66f72-104">In This Section</span></span>  
 [<span data-ttu-id="66f72-105">Dotazy v LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="66f72-105">Queries in LINQ to DataSet</span></span>](queries-in-linq-to-dataset.md)  
 <span data-ttu-id="66f72-106">Poskytuje informace o tom, jak zapisovat LINQ to DataSet dotazy.</span><span class="sxs-lookup"><span data-stu-id="66f72-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="66f72-107">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="66f72-107">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="66f72-108">Popisuje způsob dotazování <xref:System.Data.DataSet> objektů.</span><span class="sxs-lookup"><span data-stu-id="66f72-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="66f72-109">Porovnání datových řádků</span><span class="sxs-lookup"><span data-stu-id="66f72-109">Comparing DataRows</span></span>](comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="66f72-110">Popisuje, jak použít objekt <xref:System.Data.DataRowComparer> k porovnání datových řádků.</span><span class="sxs-lookup"><span data-stu-id="66f72-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="66f72-111">Vytvoření datové tabulky z dotazu</span><span class="sxs-lookup"><span data-stu-id="66f72-111">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="66f72-112">Poskytuje informace o vytváření <xref:System.Data.DataTable> z LINQ to DataSetho dotazu pomocí metody <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="66f72-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="66f72-113">Postupy: implementace CopyToDataTable\<T >, kde obecný typ T není DataRow</span><span class="sxs-lookup"><span data-stu-id="66f72-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="66f72-114">Popisuje, jak implementovat vlastní metodu `CopyToDataTable<T>`, kde obecný parametr T není typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="66f72-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="66f72-115">Obecné pole a metody SetField</span><span class="sxs-lookup"><span data-stu-id="66f72-115">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="66f72-116">Poskytuje informace o obecných <xref:System.Data.DataRowExtensions.Field%2A> a <xref:System.Data.DataRowExtensions.SetField%2A> metodách.</span><span class="sxs-lookup"><span data-stu-id="66f72-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="66f72-117">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="66f72-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="66f72-118">Popisuje datovou vazbu pomocí objektu <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="66f72-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="66f72-119">Ladění dotazů v LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="66f72-119">Debugging LINQ to DataSet Queries</span></span>](debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="66f72-120">Poskytuje informace o ladění a řešení potíží s LINQ to DataSet dotazy.</span><span class="sxs-lookup"><span data-stu-id="66f72-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="66f72-121">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="66f72-121">Security</span></span>](security-linq-to-dataset.md)  
 <span data-ttu-id="66f72-122">Popisuje problémy se zabezpečením v LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="66f72-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="66f72-123">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="66f72-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)  
 <span data-ttu-id="66f72-124">Poskytuje příklady dotazů, které používají operátory LINQ.</span><span class="sxs-lookup"><span data-stu-id="66f72-124">Provides query examples that use the LINQ operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="66f72-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="66f72-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="66f72-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66f72-126">See also</span></span>

- [<span data-ttu-id="66f72-127">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="66f72-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="66f72-128"> (LINQ)</span><span class="sxs-lookup"><span data-stu-id="66f72-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
