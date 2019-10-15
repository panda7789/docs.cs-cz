---
title: HORNÍ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 16be25336bac386c993eae7527c9377be1073d1e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319278"
---
# <a name="top-entity-sql"></a>HORNÍ (Entity SQL)

Klauzule SELECT může mít volitelnou klauzuli TOP sub podle volitelného modifikátoru ALL/DISTINCT. Dílčí klauzule TOP určuje, že z výsledku dotazu bude vrácena pouze první sada řádků.

## <a name="syntax"></a>Syntaxe

```sql
[ TOP (n) ]
```

## <a name="arguments"></a>Arguments

`n` číselný výraz, který určuje počet vrácených řádků. `n` může být jeden numerický literál nebo jeden parametr.

## <a name="remarks"></a>Poznámky

Výraz TOP musí být buď jeden numerický literál, nebo jeden parametr. Je-li použit konstantní literál, musí být literální typ implicitně propagačním objektem EDM. Int64 (Byte, Int16, Int32 nebo Int64 nebo libovolný typ poskytovatele, který je namapován na typ, který je možné použít na EDM. Int64) a jeho hodnota musí být větší než nebo rovna nule. V opačném případě bude vyvolána výjimka. Pokud je parametr použit jako výraz, musí být typ parametru také implicitně propagačním objektem EDM. Int64, ale během kompilace nebude nijak ověřována skutečná hodnota parametru, protože hodnoty parametrů jsou zpožděny.

Následuje příklad konstantního výrazu TOP:

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

Následuje příklad parametrizovaného HORNÍho výrazu:

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

Klauzule TOP není deterministické, pokud dotaz není seřazen. Pokud vyžadujete deterministický výsledek, použijte dílčí klauzule [Skip](skip-entity-sql.md) a [limit](limit-entity-sql.md) v klauzuli [ORDER by](order-by-entity-sql.md) . Klauzule TOP a SKIP a LIMIT se vzájemně vylučují.

## <a name="example"></a>Příklad

Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá začátek k určení horního řádku, který se má vrátit z výsledku dotazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:

1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a>Viz také:

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
