---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 321f6c5ae62ce21249ae4c1081b8e98427bc3df2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425735"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="93ff1-102">Přeskočit (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="93ff1-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="93ff1-103">Fyzické stránkování můžete provádět pomocí dílčí klauzuli SKIP v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="93ff1-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="93ff1-104">SKIP nelze použít samostatně z klauzule ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="93ff1-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ff1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93ff1-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="93ff1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="93ff1-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="93ff1-107">Počet položek pro přeskočení.</span><span class="sxs-lookup"><span data-stu-id="93ff1-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93ff1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93ff1-108">Remarks</span></span>  
 <span data-ttu-id="93ff1-109">Pokud výraz dílčí klauzuli SKIP je přítomna v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sada výsledků zahrne řádky začínající od na další řádek hned po výrazu SKIP.</span><span class="sxs-lookup"><span data-stu-id="93ff1-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="93ff1-110">Například přeskočit 5 přeskočte prvních pět řádků, který se vrátí z řádku šestého vpřed.</span><span class="sxs-lookup"><span data-stu-id="93ff1-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93ff1-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz není platný, pokud modifikátorem hlavní a dílčí klauzuli SKIP jsou k dispozici ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="93ff1-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="93ff1-112">Dotaz by měl být přepsán změnou výraz TOP na výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="93ff1-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93ff1-113">V [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], pomocí přeskočit s klauzulí ORDER BY v neklíčových sloupců může vrátit nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="93ff1-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="93ff1-114">Větší než zadaný počet řádků se možná přeskočí, pokud neklíčový sloupec v sobě obsahuje duplicitní data.</span><span class="sxs-lookup"><span data-stu-id="93ff1-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="93ff1-115">Je to kvůli jak SKIP je přeložen pro [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93ff1-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="93ff1-116">Například v následujícím kódu více než pět řádků se možná přeskočí, pokud `E.NonKeyColumn` obsahují duplicitní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="93ff1-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="93ff1-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotazování v [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) příklad používá operátor klauzule ORDER BY s PŘESKOČENÍM k určení pořadí řazení použít u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="93ff1-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ff1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="93ff1-118">See Also</span></span>  
 [<span data-ttu-id="93ff1-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="93ff1-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="93ff1-120">Postupy: výsledky stránky pomocí dotazu</span><span class="sxs-lookup"><span data-stu-id="93ff1-120">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="93ff1-121">Stránkování</span><span class="sxs-lookup"><span data-stu-id="93ff1-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="93ff1-122">TOP</span><span class="sxs-lookup"><span data-stu-id="93ff1-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
