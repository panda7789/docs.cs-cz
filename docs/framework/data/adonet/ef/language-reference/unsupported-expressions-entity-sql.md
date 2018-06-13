---
title: Nepodporované výrazy (entita SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: bf20bb92010d5031e973cb1cc004b6b8f13d0091
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234311"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="ff352-102">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="ff352-102">Unsupported expressions</span></span>

<span data-ttu-id="ff352-103">Toto téma popisuje [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporované v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff352-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="ff352-104">Další informace najdete v tématu [jak Entity SQL se liší od jazyka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ff352-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="ff352-105">Kvantitativní predikáty</span><span class="sxs-lookup"><span data-stu-id="ff352-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="ff352-106"> Umožňuje konstrukce v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="ff352-106"> allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ff352-107">, ale nepodporuje takové konstrukce.</span><span class="sxs-lookup"><span data-stu-id="ff352-107">, however, does not support such constructs.</span></span> <span data-ttu-id="ff352-108">Ekvivalentní výrazy může být napsán v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff352-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="ff352-109">\* – operátor</span><span class="sxs-lookup"><span data-stu-id="ff352-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="ff352-110"> podporuje použití \* operátor v klauzuli SELECT k označení, že všechny sloupce by měl promítat. To není podporováno v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff352-110"> supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="ff352-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff352-111">See also</span></span>

[<span data-ttu-id="ff352-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ff352-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="ff352-113">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ff352-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
