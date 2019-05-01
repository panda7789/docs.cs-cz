---
title: Nepodporované výrazy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: a47ff46ca99a84500bc5dfecc19bb31652e9b4b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034070"
---
# <a name="unsupported-expressions"></a>Nepodporované výrazy

Toto téma popisuje [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Další informace najdete v tématu [jak Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Číselná predikátů

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] umožňuje následující formu konstrukcí:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)], ale nepodporuje tyto konstrukty. Ekvivalentní výrazů je možné psát v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* – operátor

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] podporuje použití * operátoru v klauzuli SELECT k označení, že všechny sloupce by měl projekci navýšení kapacity. To není podporováno v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Jak se Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
