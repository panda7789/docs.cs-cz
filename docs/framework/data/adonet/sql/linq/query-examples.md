---
title: Příklady dotazů
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: 74664dd98ac067153894edc934c8f15eec407261
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783107"
---
# <a name="query-examples"></a><span data-ttu-id="c0f35-102">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="c0f35-102">Query Examples</span></span>
<span data-ttu-id="c0f35-103">Tato část obsahuje příklady jazyka Visual Basic a C# z typických [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="c0f35-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="c0f35-104">Vývojářům používajícím Visual Studio můžete najít mnoho dalších příkladů v ukázkovém řešení, která je k dispozici v části Ukázky.</span><span class="sxs-lookup"><span data-stu-id="c0f35-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="c0f35-105">Další informace najdete v tématu [ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0f35-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0f35-106">*DB* se často používá v příkladech kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="c0f35-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="c0f35-107">*DB* je považován za instanci *Northwind* třída, která dědí z <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0f35-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c0f35-108">In This Section</span></span>  
 [<span data-ttu-id="c0f35-109">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="c0f35-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="c0f35-110">Popisuje způsob použití <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c0f35-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="c0f35-111">Vrácení prvního prvku v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="c0f35-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="c0f35-112">Poskytuje příklady použití <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-113">Vrácení nebo přeskočení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="c0f35-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="c0f35-114">Poskytuje příklady použití <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-115">Řazení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="c0f35-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="c0f35-116">Poskytuje příklady použití <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-117">Seskupení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="c0f35-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="c0f35-118">Poskytuje příklady použití <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-119">Odstranění duplicitních prvků z posloupnosti</span><span class="sxs-lookup"><span data-stu-id="c0f35-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="c0f35-120">Poskytuje příklady použití <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-121">Určení, jestli některé nebo všechny elementy v sekvenci nesplňují podmínku</span><span class="sxs-lookup"><span data-stu-id="c0f35-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="c0f35-122">Poskytuje příklady použití <xref:System.Linq.Enumerable.All%2A> a <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-123">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="c0f35-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="c0f35-124">Poskytuje příklady použití <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-125">Vrácení rozdílů množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="c0f35-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="c0f35-126">Poskytuje příklady použití <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-127">Vrácení průniku množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="c0f35-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="c0f35-128">Poskytuje příklady použití <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-129">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="c0f35-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="c0f35-130">Poskytuje příklady použití <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-131">Převod sekvence na pole</span><span class="sxs-lookup"><span data-stu-id="c0f35-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="c0f35-132">Poskytuje příklady použití <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-133">Převod sekvence na obecný seznam</span><span class="sxs-lookup"><span data-stu-id="c0f35-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="c0f35-134">Poskytuje příklady použití <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-135">Převod typu na obecnou položku IEnumerable</span><span class="sxs-lookup"><span data-stu-id="c0f35-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="c0f35-136">Poskytuje příklady použití <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0f35-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="c0f35-137">Formulování spojení a dotazů napříč produkty</span><span class="sxs-lookup"><span data-stu-id="c0f35-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="c0f35-138">Poskytuje příklady použití navigace cizího klíče `from`, `where`, a `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="c0f35-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="c0f35-139">Formulování projekcí</span><span class="sxs-lookup"><span data-stu-id="c0f35-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="c0f35-140">Obsahuje příklady kombinování `select` s jinými funkcemi (například *anonymní typy*) do formuláře projekce dotazů.</span><span class="sxs-lookup"><span data-stu-id="c0f35-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0f35-141">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c0f35-141">Related Sections</span></span>  
 [<span data-ttu-id="c0f35-142">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="c0f35-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="c0f35-143">Vysvětluje pojem standardních operátorů dotazu pomocí C#.</span><span class="sxs-lookup"><span data-stu-id="c0f35-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="c0f35-144">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0f35-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="c0f35-145">Vysvětluje pojem standardních operátorů pro dotazování pomocí jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c0f35-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="c0f35-146">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="c0f35-146">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="c0f35-147">Vysvětluje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá koncepty, které se vztahují na dotazy.</span><span class="sxs-lookup"><span data-stu-id="c0f35-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="c0f35-148">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="c0f35-148">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="c0f35-149">Poskytuje portál na témata, která vysvětluje koncepty programování související s [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0f35-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
