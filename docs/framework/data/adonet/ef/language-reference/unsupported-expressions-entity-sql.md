---
title: Nepodporované výrazy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 956fe117eb0c59392c3999046bc70deaed268ac6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248785"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="e55f4-102">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="e55f4-102">Unsupported expressions</span></span>

<span data-ttu-id="e55f4-103">Toto téma popisuje výrazy jazyka Transact-SQL, které nejsou podporovány [!INCLUDE[esql](../../../../../../includes/esql-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="e55f4-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="e55f4-104">Další informace najdete v tématu [jak Entity SQL se liší od jazyka Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e55f4-104">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="e55f4-105">Kvantifikované predikáty</span><span class="sxs-lookup"><span data-stu-id="e55f4-105">Quantified predicates</span></span>

<span data-ttu-id="e55f4-106">Transact-SQL umožňuje vytvořit následující formu:</span><span class="sxs-lookup"><span data-stu-id="e55f4-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e55f4-107">Nicméně nepodporuje takové konstrukce.</span><span class="sxs-lookup"><span data-stu-id="e55f4-107">, however, does not support such constructs.</span></span> <span data-ttu-id="e55f4-108">Ekvivalentní výrazy lze zapsat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e55f4-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="e55f4-109">\* – operátor</span><span class="sxs-lookup"><span data-stu-id="e55f4-109">\* operator</span></span>

<span data-ttu-id="e55f4-110">Transact-SQL podporuje použití operátoru \* v klauzuli SELECT k označení toho, že všechny sloupce by měly být vycházející z projektu. Tato podpora není v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji podporována.</span><span class="sxs-lookup"><span data-stu-id="e55f4-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="e55f4-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e55f4-111">See also</span></span>

- [<span data-ttu-id="e55f4-112">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e55f4-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="e55f4-113">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e55f4-113">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
