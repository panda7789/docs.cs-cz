---
title: "Příklady dotazů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e7d7a0a1f641603887675ed0c1faebd5c06b273
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="query-examples"></a><span data-ttu-id="58a82-102">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="58a82-102">Query Examples</span></span>
<span data-ttu-id="58a82-103">Tato část obsahuje [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] a C# Příklady typických [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="58a82-103">This section provides [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="58a82-104">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] najdete mnoho další příklady v ukázkové řešení, která je k dispozici v části Ukázky.</span><span class="sxs-lookup"><span data-stu-id="58a82-104">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="58a82-105">Další informace najdete v tématu [ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="58a82-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58a82-106">*DB* se často používá v příklady kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="58a82-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="58a82-107">*DB* se považuje za instanci *Northwind* třídy, která dědí z <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="58a82-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58a82-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="58a82-108">In This Section</span></span>  
 [<span data-ttu-id="58a82-109">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="58a82-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="58a82-110">Popisuje způsob použití <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="58a82-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="58a82-111">Vrátí první prvek v pořadí</span><span class="sxs-lookup"><span data-stu-id="58a82-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="58a82-112">Obsahuje příklady použití <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-113">Vrátí nebo přeskočit elementy v pořadí</span><span class="sxs-lookup"><span data-stu-id="58a82-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="58a82-114">Obsahuje příklady použití <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-115">Řazení elementů v pořadí</span><span class="sxs-lookup"><span data-stu-id="58a82-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="58a82-116">Obsahuje příklady použití <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-117">Prvky skupiny v pořadí</span><span class="sxs-lookup"><span data-stu-id="58a82-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="58a82-118">Obsahuje příklady použití <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-119">Odstranit elementy s duplicitním z řady</span><span class="sxs-lookup"><span data-stu-id="58a82-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="58a82-120">Obsahuje příklady použití <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-121">Určit, zda některé nebo všechny elementy v pořadí nesplňuje podmínku</span><span class="sxs-lookup"><span data-stu-id="58a82-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="58a82-122">Obsahuje příklady použití <xref:System.Linq.Enumerable.All%2A> a <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-123">Řetězení dvě pořadí</span><span class="sxs-lookup"><span data-stu-id="58a82-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="58a82-124">Obsahuje příklady použití <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-125">Vrátí množinových rozdílů mezi dvěma pořadí</span><span class="sxs-lookup"><span data-stu-id="58a82-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="58a82-126">Obsahuje příklady použití <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-127">Vrátí sadu průnik dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="58a82-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="58a82-128">Obsahuje příklady použití <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-129">Vrátí sadu sjednocení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="58a82-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="58a82-130">Obsahuje příklady použití <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-131">Převod na pole sekvenci</span><span class="sxs-lookup"><span data-stu-id="58a82-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="58a82-132">Obsahuje příklady použití <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-133">Převést na seznam obecná posloupnost</span><span class="sxs-lookup"><span data-stu-id="58a82-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="58a82-134">Obsahuje příklady použití <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-135">Převést typ na obecný IEnumerable</span><span class="sxs-lookup"><span data-stu-id="58a82-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="58a82-136">Obsahuje příklady použití <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="58a82-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="58a82-137">Formulovali spojení a dotazy smíšený produkt</span><span class="sxs-lookup"><span data-stu-id="58a82-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="58a82-138">Obsahuje příklady použití navigační cizího klíče v `from`, `where`, a `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="58a82-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="58a82-139">Formulovali projekce</span><span class="sxs-lookup"><span data-stu-id="58a82-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="58a82-140">Obsahuje příklady kombinování `select` s jinými funkcemi (například *anonymní typy*) do formuláře dotazu projekce.</span><span class="sxs-lookup"><span data-stu-id="58a82-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="58a82-141">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="58a82-141">Related Sections</span></span>  
 [<span data-ttu-id="58a82-142">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="58a82-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="58a82-143">Popisuje koncept standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="58a82-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="58a82-144">Koncepty dotazu</span><span class="sxs-lookup"><span data-stu-id="58a82-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="58a82-145">Vysvětluje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá koncepty, které platí pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="58a82-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="58a82-146">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="58a82-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="58a82-147">Poskytuje portál na témata, které vysvětlují, související s koncepty programování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58a82-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
