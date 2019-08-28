---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: b6335086ce5b61cf23db2bf967d1a82f322e83b3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043627"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="bfb49-102">Přeskočit (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bfb49-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="bfb49-103">Fyzické stránkování můžete provádět pomocí dílčí klauzule SKIP v klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="bfb49-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="bfb49-104">Klauzuli SKIP nelze použít odděleně od klauzule ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="bfb49-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfb49-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfb49-105">Syntax</span></span>

```
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="bfb49-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="bfb49-106">Arguments</span></span>

`n` \
<span data-ttu-id="bfb49-107">Počet položek, které se mají přeskočit</span><span class="sxs-lookup"><span data-stu-id="bfb49-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfb49-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfb49-108">Remarks</span></span>

<span data-ttu-id="bfb49-109">Pokud je v klauzuli ORDER BY přítomna dílčí klauzule SKIP Expression, výsledky se seřadí podle specifikace řazení a sada výsledků bude zahrnovat řádky začínající z dalšího řádku hned za výrazem SKIP.</span><span class="sxs-lookup"><span data-stu-id="bfb49-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="bfb49-110">Například PŘESKOČENí 5 přeskočí prvních pět řádků a vrátí se z šestého řádku předá.</span><span class="sxs-lookup"><span data-stu-id="bfb49-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="bfb49-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz je neplatný, pokud je ve stejném výrazu dotazu přítomen modifikátor Top a dílčí klauzule Skip.</span><span class="sxs-lookup"><span data-stu-id="bfb49-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="bfb49-112">Dotaz by měl být přepsán změnou HORNÍho výrazu na výraz LIMIT.</span><span class="sxs-lookup"><span data-stu-id="bfb49-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="bfb49-113">V SQL Server 2000 mohou vracet nesprávné výsledky pomocí příkazu přeskočit s řazením na jiné než klíčové sloupce.</span><span class="sxs-lookup"><span data-stu-id="bfb49-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="bfb49-114">Pokud neklíčový sloupec obsahuje duplicitní data, může být vynecháno více než zadaný počet řádků.</span><span class="sxs-lookup"><span data-stu-id="bfb49-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="bfb49-115">Je to kvůli tomu, jak je PŘESKOČENí přeloženo pro SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="bfb49-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="bfb49-116">Například v následujícím kódu může být vynecháno více než pět řádků, pokud `E.NonKeyColumn` má duplicitní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="bfb49-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`

<span data-ttu-id="bfb49-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz na[postupy: Stránka prostřednictvím výsledků](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) dotazu používá operátor ORDER by s skipem k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="bfb49-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfb49-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfb49-118">See also</span></span>

- [<span data-ttu-id="bfb49-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="bfb49-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="bfb49-120">[Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bfb49-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="bfb49-121">Stránkování</span><span class="sxs-lookup"><span data-stu-id="bfb49-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="bfb49-122">TOP</span><span class="sxs-lookup"><span data-stu-id="bfb49-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
