---
title: Přeskočit (entita SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 3b63ca6ade93331b9d1c3ef3e8de15ed520864dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="skip-entity-sql"></a><span data-ttu-id="8d636-102">Přeskočit (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="8d636-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="8d636-103">Fyzické stránkování můžete provést pomocí dílčí klauzuli SKIP v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="8d636-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="8d636-104">SKIP nelze použít samostatně z klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="8d636-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d636-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d636-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d636-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="8d636-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="8d636-107">Počet položek tak, aby přeskočil.</span><span class="sxs-lookup"><span data-stu-id="8d636-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d636-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d636-108">Remarks</span></span>  
 <span data-ttu-id="8d636-109">Pokud se nachází dílčí klauzuli SKIP výrazu v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sadu výsledků dotazu zahrne řádky začínající z na další řádek hned po výrazu SKIP.</span><span class="sxs-lookup"><span data-stu-id="8d636-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="8d636-110">Například bude 5 PŘESKOČENÍ přeskočte prvních pět řádky a vrátí z šesté řádek dál.</span><span class="sxs-lookup"><span data-stu-id="8d636-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d636-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz je neplatný, pokud modifikátor TOP a dílčí klauzuli SKIP se nacházejí ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="8d636-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="8d636-112">Dotaz by měl být přepsána změnou výraz TOP na výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="8d636-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d636-113">V [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], pomocí přeskočit s klauzulí ORDER BY v neklíčových sloupců může vrátit nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d636-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="8d636-114">Více než zadaný počet řádků může přeskočen. Pokud neklíčový sloupec obsahuje duplicitní data v ní.</span><span class="sxs-lookup"><span data-stu-id="8d636-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="8d636-115">Je to z důvodu jak SKIP je přeložená pro [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d636-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="8d636-116">Například v následujícím kódu více než pět řádků může být přeskočeno `E.NonKeyColumn` obsahuje duplicitní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="8d636-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="8d636-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotazu v [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) příklad používá operátor ORDER BY s PŘESKOČENÍM k určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="8d636-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d636-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d636-118">See Also</span></span>  
 [<span data-ttu-id="8d636-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="8d636-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="8d636-120">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="8d636-120">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="8d636-121">Stránkování</span><span class="sxs-lookup"><span data-stu-id="8d636-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="8d636-122">TOP</span><span class="sxs-lookup"><span data-stu-id="8d636-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
