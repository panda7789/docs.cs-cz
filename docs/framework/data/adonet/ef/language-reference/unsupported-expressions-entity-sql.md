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
# <a name="unsupported-expressions"></a>Nepodporované výrazy

Toto téma popisuje výrazů příkazů jazyka Transact-SQL, které nejsou podporovány v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Další informace najdete v tématu [jak Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Číselná predikátů

Příkaz Transact-SQL umožňuje má následující formu konstrukcí:

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

Příkaz Transact-SQL podporuje použití * operátoru v klauzuli SELECT k označení, že všechny sloupce by měl projekci navýšení kapacity. To není podporováno v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Jak se Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
