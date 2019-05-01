---
title: Příklady LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: 07ad4a993187c91babb74fae9d05f17b66c2098b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033940"
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="5dd79-102">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="5dd79-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="5dd79-103">Tato část obsahuje LINQ na DataSet programovací příklady použití standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="5dd79-103">This section provides LINQ to DataSet programming examples that use the standard query operators.</span></span> <span data-ttu-id="5dd79-104"><xref:System.Data.DataSet> Používá v těchto příkladech je vyplněna pomocí `FillDataSet` metodu, která je zadána v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5dd79-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="5dd79-105">Další informace najdete v tématu [přehled standardních operátorů dotazu (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [přehled operátory standardního dotazu (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5dd79-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5dd79-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5dd79-106">In This Section</span></span>  
 [<span data-ttu-id="5dd79-107">Příklady výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="5dd79-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="5dd79-108">Obsahuje následující příklady:</span><span class="sxs-lookup"><span data-stu-id="5dd79-108">Contains the following examples:</span></span>  
  
- [<span data-ttu-id="5dd79-109">Projekce</span><span class="sxs-lookup"><span data-stu-id="5dd79-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
- [<span data-ttu-id="5dd79-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="5dd79-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
- [<span data-ttu-id="5dd79-111">Segmentace</span><span class="sxs-lookup"><span data-stu-id="5dd79-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
- [<span data-ttu-id="5dd79-112">Řazení</span><span class="sxs-lookup"><span data-stu-id="5dd79-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
- [<span data-ttu-id="5dd79-113">Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="5dd79-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
- [<span data-ttu-id="5dd79-114">Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="5dd79-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
- [<span data-ttu-id="5dd79-115">Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="5dd79-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="5dd79-116">Příklady dotazů založených na metodách</span><span class="sxs-lookup"><span data-stu-id="5dd79-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="5dd79-117">Obsahuje následující příklady:</span><span class="sxs-lookup"><span data-stu-id="5dd79-117">Contains the following examples:</span></span>  
  
- [<span data-ttu-id="5dd79-118">Projekce</span><span class="sxs-lookup"><span data-stu-id="5dd79-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
- [<span data-ttu-id="5dd79-119">Segmentace</span><span class="sxs-lookup"><span data-stu-id="5dd79-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
- [<span data-ttu-id="5dd79-120">Řazení</span><span class="sxs-lookup"><span data-stu-id="5dd79-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
- [<span data-ttu-id="5dd79-121">Množinové operátory</span><span class="sxs-lookup"><span data-stu-id="5dd79-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
- [<span data-ttu-id="5dd79-122">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="5dd79-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
- [<span data-ttu-id="5dd79-123">Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="5dd79-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
- [<span data-ttu-id="5dd79-124">Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="5dd79-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
- [<span data-ttu-id="5dd79-125">Spojení</span><span class="sxs-lookup"><span data-stu-id="5dd79-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="5dd79-126">Příklady operátorů specifických pro datovou sadu</span><span class="sxs-lookup"><span data-stu-id="5dd79-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="5dd79-127">Obsahuje příklady, které ukazují, jak používat <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda a <xref:System.Data.DataRowComparer> třídy.</span><span class="sxs-lookup"><span data-stu-id="5dd79-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd79-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5dd79-128">See also</span></span>

- [<span data-ttu-id="5dd79-129">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="5dd79-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="5dd79-130">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="5dd79-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
