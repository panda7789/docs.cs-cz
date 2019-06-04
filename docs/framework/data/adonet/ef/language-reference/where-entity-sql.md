---
title: KDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489851"
---
# <a name="where-entity-sql"></a><span data-ttu-id="a9725-102">KDE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a9725-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="a9725-103">Přímo po použití klauzule WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a9725-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9725-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9725-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a9725-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a9725-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a9725-106">Typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="a9725-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9725-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9725-107">Remarks</span></span>  
 <span data-ttu-id="a9725-108">Klauzule WHERE má stejnou sémantiku, jak je popsáno příkazů jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="a9725-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="a9725-109">Omezuje objekty vytvořený podle výrazu dotazu tím, že omezíte prvků zdrojové kolekce na ty, které předávají podmínku.</span><span class="sxs-lookup"><span data-stu-id="a9725-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="a9725-110">Výraz `e` musí být typu logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="a9725-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="a9725-111">Použití klauzule WHERE přímo po klauzuli FROM a před všechny seskupení, řazení nebo projekce probíhá.</span><span class="sxs-lookup"><span data-stu-id="a9725-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="a9725-112">Všechny názvy elementů, které jsou definovány v klauzuli FROM jsou viditelné pro výraz v klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="a9725-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9725-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9725-113">See also</span></span>

- [<span data-ttu-id="a9725-114">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a9725-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="a9725-115">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="a9725-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
