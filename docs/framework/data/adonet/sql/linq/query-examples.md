---
title: Příklady dotazů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5b1681f609d8715167defcb1df57cc270b61e53a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="query-examples"></a><span data-ttu-id="0fa8a-102">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="0fa8a-102">Query Examples</span></span>
<span data-ttu-id="0fa8a-103">Tato část obsahuje Visual Basic a C# Příklady typických [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="0fa8a-104">Vývojáři pomocí sady Visual Studio najdete v části Ukázky mnoho další příklady v ukázkové řešení, která je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="0fa8a-105">Další informace najdete v tématu [ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="0fa8a-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0fa8a-106">*DB* se často používá v příklady kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="0fa8a-107">*DB* se považuje za instanci *Northwind* třídy, která dědí z <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fa8a-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0fa8a-108">In This Section</span></span>  
 [<span data-ttu-id="0fa8a-109">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="0fa8a-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="0fa8a-110">Popisuje způsob použití <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="0fa8a-111">Vrácení prvního prvku v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0fa8a-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="0fa8a-112">Obsahuje příklady použití <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-113">Vrácení nebo přeskočení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0fa8a-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="0fa8a-114">Obsahuje příklady použití <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-115">Řazení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0fa8a-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="0fa8a-116">Obsahuje příklady použití <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-117">Seskupení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0fa8a-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="0fa8a-118">Obsahuje příklady použití <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-119">Odstranění duplicitních prvků z posloupnosti</span><span class="sxs-lookup"><span data-stu-id="0fa8a-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="0fa8a-120">Obsahuje příklady použití <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-121">Určení, jestli některé nebo všechny elementy v sekvenci nesplňují podmínku</span><span class="sxs-lookup"><span data-stu-id="0fa8a-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="0fa8a-122">Obsahuje příklady použití <xref:System.Linq.Enumerable.All%2A> a <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-123">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="0fa8a-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="0fa8a-124">Obsahuje příklady použití <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-125">Vrácení rozdílů množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="0fa8a-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="0fa8a-126">Obsahuje příklady použití <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-127">Vrácení průniku množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="0fa8a-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="0fa8a-128">Obsahuje příklady použití <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-129">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="0fa8a-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="0fa8a-130">Obsahuje příklady použití <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-131">Převod sekvence na pole</span><span class="sxs-lookup"><span data-stu-id="0fa8a-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="0fa8a-132">Obsahuje příklady použití <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-133">Převod sekvence na obecný seznam</span><span class="sxs-lookup"><span data-stu-id="0fa8a-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="0fa8a-134">Obsahuje příklady použití <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-135">Převod typu na obecnou položku IEnumerable</span><span class="sxs-lookup"><span data-stu-id="0fa8a-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="0fa8a-136">Obsahuje příklady použití <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="0fa8a-137">Formulování spojení a dotazů napříč produkty</span><span class="sxs-lookup"><span data-stu-id="0fa8a-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="0fa8a-138">Obsahuje příklady použití navigační cizího klíče v `from`, `where`, a `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="0fa8a-139">Formulování projekcí</span><span class="sxs-lookup"><span data-stu-id="0fa8a-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="0fa8a-140">Obsahuje příklady kombinování `select` s jinými funkcemi (například *anonymní typy*) do formuláře dotazu projekce.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0fa8a-141">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0fa8a-141">Related Sections</span></span>  
 [<span data-ttu-id="0fa8a-142">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="0fa8a-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="0fa8a-143">Popisuje koncept standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="0fa8a-144">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="0fa8a-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="0fa8a-145">Vysvětluje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá koncepty, které platí pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="0fa8a-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="0fa8a-146">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="0fa8a-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="0fa8a-147">Poskytuje portál na témata, které vysvětlují, související s koncepty programování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0fa8a-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
