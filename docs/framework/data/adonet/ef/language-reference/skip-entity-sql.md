---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319344"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="7f8a5-102">Přeskočit (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7f8a5-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="7f8a5-103">Fyzické stránkování můžete provádět pomocí dílčí klauzule SKIP v klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="7f8a5-104">Klauzuli SKIP nelze použít odděleně od klauzule ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f8a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f8a5-105">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="7f8a5-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7f8a5-106">Arguments</span></span>

`n` \
<span data-ttu-id="7f8a5-107">Počet položek, které se mají přeskočit</span><span class="sxs-lookup"><span data-stu-id="7f8a5-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f8a5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f8a5-108">Remarks</span></span>

<span data-ttu-id="7f8a5-109">Pokud je v klauzuli ORDER BY přítomna dílčí klauzule SKIP Expression, výsledky se seřadí podle specifikace řazení a sada výsledků bude zahrnovat řádky začínající z dalšího řádku hned za výrazem SKIP.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="7f8a5-110">Například PŘESKOČENí 5 přeskočí prvních pět řádků a vrátí se z šestého řádku předá.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="7f8a5-111">Dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je neplatný, je-li ve stejném výrazu dotazu přítomen jak modifikátor TOP, tak dílčí klauzule SKIP.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="7f8a5-112">Dotaz by měl být přepsán změnou HORNÍho výrazu na výraz LIMIT.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="7f8a5-113">V SQL Server 2000 mohou vracet nesprávné výsledky pomocí příkazu přeskočit s řazením na jiné než klíčové sloupce.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="7f8a5-114">Pokud neklíčový sloupec obsahuje duplicitní data, může být vynecháno více než zadaný počet řádků.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="7f8a5-115">Je to kvůli tomu, jak je PŘESKOČENí přeloženo pro SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="7f8a5-116">Například v následujícím kódu může být vynecháno více než pět řádků, pokud `E.NonKeyColumn` má duplicitní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7f8a5-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="7f8a5-117">Dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v tématu [Postupy: stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) používá operátor ORDER by with Skip k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="7f8a5-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f8a5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f8a5-118">See also</span></span>

- [<span data-ttu-id="7f8a5-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="7f8a5-119">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="7f8a5-120">[Postupy: stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f8a5-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="7f8a5-121">Stránkování</span><span class="sxs-lookup"><span data-stu-id="7f8a5-121">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="7f8a5-122">TOP</span><span class="sxs-lookup"><span data-stu-id="7f8a5-122">TOP</span></span>](top-entity-sql.md)
