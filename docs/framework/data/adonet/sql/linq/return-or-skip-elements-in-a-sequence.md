---
title: Vrácení nebo přeskočení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: a5c32afc913443787ad8371f31f1fe330b126398
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792753"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="2a94c-102">Vrácení nebo přeskočení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="2a94c-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="2a94c-103"><xref:System.Linq.Queryable.Take%2A> Operátor můžete použít k vrácení daného počtu prvků v sekvenci a následném přeskočení na zbytek.</span><span class="sxs-lookup"><span data-stu-id="2a94c-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="2a94c-104"><xref:System.Linq.Queryable.Skip%2A> Operátor můžete použít k přeskočení určitého počtu prvků v sekvenci a následnému vrácení zbytku.</span><span class="sxs-lookup"><span data-stu-id="2a94c-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a94c-105"><xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="2a94c-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="2a94c-106">Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="2a94c-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2a94c-107">překládá <xref:System.Linq.Queryable.Skip%2A> se pomocí poddotazu s klauzulí SQL `NOT EXISTS` .</span><span class="sxs-lookup"><span data-stu-id="2a94c-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="2a94c-108">Tento převod má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="2a94c-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="2a94c-109">Argument musí být sada.</span><span class="sxs-lookup"><span data-stu-id="2a94c-109">The argument must be a set.</span></span> <span data-ttu-id="2a94c-110">Množiny s více sadami se nepodporují, i když jsou seřazené.</span><span class="sxs-lookup"><span data-stu-id="2a94c-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="2a94c-111">Vygenerovaný dotaz může být mnohem složitější než dotaz vygenerovaný pro základní dotaz, na kterém <xref:System.Linq.Queryable.Skip%2A> se používá.</span><span class="sxs-lookup"><span data-stu-id="2a94c-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="2a94c-112">Tato složitost může způsobit snížení výkonu nebo dokonce i vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="2a94c-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a94c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a94c-113">Example</span></span>  
 <span data-ttu-id="2a94c-114">Následující příklad používá `Take` k výběru prvních pět `Employees` najatých.</span><span class="sxs-lookup"><span data-stu-id="2a94c-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="2a94c-115">Všimněte si, že kolekce je nejprve seřazena podle `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="2a94c-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="2a94c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a94c-116">Example</span></span>  
 <span data-ttu-id="2a94c-117">Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> k výběru vše kromě nejdražšího `Products`10.</span><span class="sxs-lookup"><span data-stu-id="2a94c-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="2a94c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a94c-118">Example</span></span>  
 <span data-ttu-id="2a94c-119">Následující příklad kombinuje <xref:System.Linq.Queryable.Skip%2A> metody a <xref:System.Linq.Queryable.Take%2A> pro přeskočení prvních 50 záznamů a potom vrátí další 10.</span><span class="sxs-lookup"><span data-stu-id="2a94c-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="2a94c-120"><xref:System.Linq.Queryable.Take%2A>a <xref:System.Linq.Queryable.Skip%2A> operace jsou dobře definovány pouze proti seřazeným sadám.</span><span class="sxs-lookup"><span data-stu-id="2a94c-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="2a94c-121">Sémantika pro neuspořádané sady nebo více sad není definována.</span><span class="sxs-lookup"><span data-stu-id="2a94c-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="2a94c-122">Z důvodu omezení řazení v SQL se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout pořadí argumentu <xref:System.Linq.Queryable.Take%2A> operátoru OR <xref:System.Linq.Queryable.Skip%2A> na výsledek operátoru.</span><span class="sxs-lookup"><span data-stu-id="2a94c-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a94c-123">Překlad se liší od SQL Server 2000 a SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="2a94c-123">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="2a94c-124">Pokud plánujete použití <xref:System.Linq.Queryable.Skip%2A> s dotazem jakékoli složitosti, použijte SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="2a94c-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="2a94c-125">Vezměte v úvahu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] následující dotaz SQL Server 2000:</span><span class="sxs-lookup"><span data-stu-id="2a94c-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2a94c-126">Přesune řazení na konec v kódu SQL následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2a94c-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
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
  
 <span data-ttu-id="2a94c-127">Když <xref:System.Linq.Queryable.Take%2A> a<xref:System.Linq.Queryable.Skip%2A> jsou zřetězeny, všechna zadaná řazení musí být konzistentní.</span><span class="sxs-lookup"><span data-stu-id="2a94c-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="2a94c-128">V opačném případě nejsou výsledky definovány.</span><span class="sxs-lookup"><span data-stu-id="2a94c-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="2a94c-129">Pro nezáporné konstantní celočíselné argumenty založené na specifikaci SQL, <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definovány.</span><span class="sxs-lookup"><span data-stu-id="2a94c-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a94c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a94c-130">See also</span></span>

- [<span data-ttu-id="2a94c-131">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="2a94c-131">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="2a94c-132">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="2a94c-132">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
