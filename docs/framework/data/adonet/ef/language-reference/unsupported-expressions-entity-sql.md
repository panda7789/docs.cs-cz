---
title: Nepodporované výrazy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489867"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="84839-102">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="84839-102">Unsupported expressions</span></span>

<span data-ttu-id="84839-103">Toto téma popisuje výrazů příkazů jazyka Transact-SQL, které nejsou podporovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84839-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="84839-104">Další informace najdete v tématu [jak Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="84839-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="84839-105">Číselná predikátů</span><span class="sxs-lookup"><span data-stu-id="84839-105">Quantified predicates</span></span>

<span data-ttu-id="84839-106">Příkaz Transact-SQL umožňuje má následující formu konstrukcí:</span><span class="sxs-lookup"><span data-stu-id="84839-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="84839-107">, ale nepodporuje tyto konstrukty.</span><span class="sxs-lookup"><span data-stu-id="84839-107">, however, does not support such constructs.</span></span> <span data-ttu-id="84839-108">Ekvivalentní výrazů je možné psát v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="84839-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="84839-109">\* – operátor</span><span class="sxs-lookup"><span data-stu-id="84839-109">\* operator</span></span>

<span data-ttu-id="84839-110">Příkaz Transact-SQL podporuje použití \* operátoru v klauzuli SELECT k označení, že všechny sloupce by měl projekci navýšení kapacity. To není podporováno v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84839-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="84839-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84839-111">See also</span></span>

- [<span data-ttu-id="84839-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="84839-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="84839-113">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84839-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
