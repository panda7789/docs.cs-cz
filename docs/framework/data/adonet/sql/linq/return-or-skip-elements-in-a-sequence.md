---
title: "Vrátí nebo přeskočit elementy v pořadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b5d52fd3326448c428dac16c210321889f83ea23
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="3f96b-102">Vrátí nebo přeskočit elementy v pořadí</span><span class="sxs-lookup"><span data-stu-id="3f96b-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="3f96b-103">Použití <xref:System.Linq.Queryable.Take%2A> operátor a vrátí zadaný počet elementů v pořadí a pak přeskočit zbytek.</span><span class="sxs-lookup"><span data-stu-id="3f96b-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="3f96b-104">Použití <xref:System.Linq.Queryable.Skip%2A> operátor přeskočit zadaný počet elementů v pořadí a pak se vraťte zbytek.</span><span class="sxs-lookup"><span data-stu-id="3f96b-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f96b-105"><xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když jsou použity v dotazy pro SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="3f96b-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="3f96b-106">Další informace najdete v tématu "Přeskočit a trvat výjimky v systému SQL Server 2000" položky v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3f96b-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3f96b-107">Přeloží <xref:System.Linq.Queryable.Skip%2A> pomocí poddotazu SQL `NOT EXISTS` klauzule.</span><span class="sxs-lookup"><span data-stu-id="3f96b-107"> translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="3f96b-108">Tento překlad má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="3f96b-108">This translation has the following limitations:</span></span>  
  
-   <span data-ttu-id="3f96b-109">Argument musí být sada.</span><span class="sxs-lookup"><span data-stu-id="3f96b-109">The argument must be a set.</span></span> <span data-ttu-id="3f96b-110">Multisets nejsou podporovány, i v případě, že řazení.</span><span class="sxs-lookup"><span data-stu-id="3f96b-110">Multisets are not supported, even if ordered.</span></span>  
  
-   <span data-ttu-id="3f96b-111">Vygenerovaný dotazu může být mnohem složitější než dotazu generované pro základní dotaz, na kterém <xref:System.Linq.Queryable.Skip%2A> platí.</span><span class="sxs-lookup"><span data-stu-id="3f96b-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="3f96b-112">Tato složitost může způsobit snížení výkonu nebo i vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="3f96b-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f96b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f96b-113">Example</span></span>  
 <span data-ttu-id="3f96b-114">Následující příklad používá `Take` vybrat prvních pět `Employees` pronajaty formou.</span><span class="sxs-lookup"><span data-stu-id="3f96b-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="3f96b-115">Všimněte si, že kolekce je nejdřív seřazené podle `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="3f96b-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="3f96b-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f96b-116">Example</span></span>  
 <span data-ttu-id="3f96b-117">Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> vyberte všechny kromě nejnákladnější 10 `Products`.</span><span class="sxs-lookup"><span data-stu-id="3f96b-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="3f96b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f96b-118">Example</span></span>  
 <span data-ttu-id="3f96b-119">Následující příklad kombinuje <xref:System.Linq.Queryable.Skip%2A> a <xref:System.Linq.Queryable.Take%2A> metody pro přeskočte prvních 50 záznamy a pak se vraťte další 10.</span><span class="sxs-lookup"><span data-stu-id="3f96b-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="3f96b-120"><xref:System.Linq.Queryable.Take%2A>a <xref:System.Linq.Queryable.Skip%2A> operace jsou dobře definované pouze proti seřazené sady.</span><span class="sxs-lookup"><span data-stu-id="3f96b-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="3f96b-121">Pro multisets nebo Neseřazený sady sémantiky není definován.</span><span class="sxs-lookup"><span data-stu-id="3f96b-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="3f96b-122">Z důvodu omezení na pořadí v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argument <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> operátor výsledek operátor.</span><span class="sxs-lookup"><span data-stu-id="3f96b-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f96b-123">Překlad se liší pro [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] a [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f96b-123">Translation is different for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] and [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span> <span data-ttu-id="3f96b-124">Pokud budete chtít použít <xref:System.Linq.Queryable.Skip%2A> s dotazem jakékoli složitosti, použijte [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f96b-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span>  
  
 <span data-ttu-id="3f96b-125">Vezměte v úvahu následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3f96b-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3f96b-126">Přesune řazení na konec v kódu SQL následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3f96b-126"> moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="3f96b-127">Když <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou zřetězen dohromady, všechny zadané pořadí musí být konzistentní.</span><span class="sxs-lookup"><span data-stu-id="3f96b-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="3f96b-128">Jinak výsledky nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="3f96b-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="3f96b-129">Pro nezáporné, konstantní argumenty pro integrální podle specifikace SQL obě <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definovaný.</span><span class="sxs-lookup"><span data-stu-id="3f96b-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f96b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f96b-130">See Also</span></span>  
 [<span data-ttu-id="3f96b-131">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="3f96b-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="3f96b-132">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="3f96b-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
