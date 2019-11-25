---
title: LINQ na objekty
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: ef7d6fe232a788ab77661e9c5f313a80df4779b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354308"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="39d1e-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="39d1e-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="39d1e-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="39d1e-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="39d1e-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="39d1e-105">The collection may be user-defined or may be returned by a .NET Framework API.</span><span class="sxs-lookup"><span data-stu-id="39d1e-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="39d1e-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span><span class="sxs-lookup"><span data-stu-id="39d1e-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="39d1e-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span><span class="sxs-lookup"><span data-stu-id="39d1e-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="39d1e-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span><span class="sxs-lookup"><span data-stu-id="39d1e-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="39d1e-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span><span class="sxs-lookup"><span data-stu-id="39d1e-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="39d1e-110">They are more concise and readable, especially when filtering multiple conditions.</span><span class="sxs-lookup"><span data-stu-id="39d1e-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="39d1e-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span><span class="sxs-lookup"><span data-stu-id="39d1e-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="39d1e-112">They can be ported to other data sources with little or no modification.</span><span class="sxs-lookup"><span data-stu-id="39d1e-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="39d1e-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span><span class="sxs-lookup"><span data-stu-id="39d1e-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="39d1e-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span><span class="sxs-lookup"><span data-stu-id="39d1e-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="39d1e-115">It is not intended to be exhaustive.</span><span class="sxs-lookup"><span data-stu-id="39d1e-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39d1e-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="39d1e-116">In This Section</span></span>  
 [<span data-ttu-id="39d1e-117">LINQ and Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="39d1e-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span><span class="sxs-lookup"><span data-stu-id="39d1e-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="39d1e-119">Also includes links to topics that demonstrate these principles.</span><span class="sxs-lookup"><span data-stu-id="39d1e-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="39d1e-120">LINQ and Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="39d1e-121">Links to a sample that demonstrates how LINQ uses reflection.</span><span class="sxs-lookup"><span data-stu-id="39d1e-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="39d1e-122">LINQ and File Directories (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="39d1e-123">Explains how LINQ can be used to interact with file systems.</span><span class="sxs-lookup"><span data-stu-id="39d1e-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="39d1e-124">Also includes links to topics that demonstrate these concepts.</span><span class="sxs-lookup"><span data-stu-id="39d1e-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="39d1e-125">How to: Query an ArrayList with LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="39d1e-126">Demonstrates how to query an ArrayList in C#.</span><span class="sxs-lookup"><span data-stu-id="39d1e-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="39d1e-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="39d1e-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="39d1e-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="39d1e-129">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d1e-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="39d1e-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span><span class="sxs-lookup"><span data-stu-id="39d1e-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
