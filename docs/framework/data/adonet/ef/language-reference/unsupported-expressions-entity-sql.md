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
# <a name="unsupported-expressions"></a>Nepodporované výrazy

Toto téma popisuje výrazy jazyka Transact-SQL, které nejsou podporovány [!INCLUDE[esql](../../../../../../includes/esql-md.md)]v. Další informace najdete v tématu [jak Entity SQL se liší od jazyka Transact-SQL](how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Kvantifikované predikáty

Transact-SQL umožňuje vytvořit následující formu:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Nicméně nepodporuje takové konstrukce. Ekvivalentní výrazy lze zapsat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* – operátor

Transact-SQL podporuje použití operátoru * v klauzuli SELECT k označení toho, že všechny sloupce by měly být vycházející z projektu. Tato podpora není v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji podporována.

## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Jak se Entity SQL liší od Transact-SQL](how-entity-sql-differs-from-transact-sql.md)
