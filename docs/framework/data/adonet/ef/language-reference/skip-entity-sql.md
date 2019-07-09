---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 88d4c9c987f451e9a653d5b9c213e7158670ed4b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662137"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="5f715-102">Přeskočit (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5f715-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="5f715-103">Fyzické stránkování můžete provádět pomocí dílčí klauzuli SKIP v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="5f715-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="5f715-104">SKIP nelze použít samostatně z klauzule ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="5f715-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f715-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f715-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f715-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f715-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="5f715-107">Počet položek pro přeskočení.</span><span class="sxs-lookup"><span data-stu-id="5f715-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f715-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f715-108">Remarks</span></span>  
 <span data-ttu-id="5f715-109">Pokud výraz dílčí klauzuli SKIP je přítomna v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sada výsledků zahrne řádky začínající od na další řádek hned po výrazu SKIP.</span><span class="sxs-lookup"><span data-stu-id="5f715-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="5f715-110">Například přeskočit 5 přeskočte prvních pět řádků, který se vrátí z řádku šestého vpřed.</span><span class="sxs-lookup"><span data-stu-id="5f715-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f715-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz není platný, pokud modifikátorem hlavní a dílčí klauzuli SKIP jsou k dispozici ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="5f715-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="5f715-112">Dotaz by měl být přepsán změnou výraz TOP na výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="5f715-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f715-113">V systému SQL Server 2000 pomocí přeskočit s klauzulí ORDER BY v neklíčových sloupců může vrátit nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="5f715-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="5f715-114">Větší než zadaný počet řádků se možná přeskočí, pokud neklíčový sloupec v sobě obsahuje duplicitní data.</span><span class="sxs-lookup"><span data-stu-id="5f715-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="5f715-115">To je způsobeno jak SKIP je přeložen pro SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="5f715-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="5f715-116">Například v následujícím kódu více než pět řádků se možná přeskočí, pokud `E.NonKeyColumn` obsahují duplicitní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="5f715-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="5f715-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotazování v [jak: Stránka přes výsledky dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) používá operátor klauzule ORDER BY s PŘESKOČENÍM k určení pořadí řazení použít u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="5f715-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f715-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f715-118">See also</span></span>

- [<span data-ttu-id="5f715-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="5f715-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="5f715-120">[Postupy: Stránkovat výsledky dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5f715-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="5f715-121">Stránkování</span><span class="sxs-lookup"><span data-stu-id="5f715-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="5f715-122">TOP</span><span class="sxs-lookup"><span data-stu-id="5f715-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
