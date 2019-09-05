---
title: HORNÍ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248975"
---
# <a name="top-entity-sql"></a>HORNÍ (Entity SQL)

Klauzule SELECT může mít volitelnou klauzuli TOP sub podle volitelného modifikátoru ALL/DISTINCT. Dílčí klauzule TOP určuje, že z výsledku dotazu bude vrácena pouze první sada řádků.

## <a name="syntax"></a>Syntaxe

```
[ TOP (n) ]
```

## <a name="arguments"></a>Arguments

`n`Číselný výraz, který určuje počet vrácených řádků. `n`může být jeden numerický literál nebo jeden parametr.

## <a name="remarks"></a>Poznámky

Výraz TOP musí být buď jeden numerický literál, nebo jeden parametr. Je-li použit konstantní literál, musí být literální typ implicitně propagačním objektem EDM. Int64 (Byte, Int16, Int32 nebo Int64 nebo libovolný typ poskytovatele, který je namapován na typ, který je možné použít na EDM. Int64) a jeho hodnota musí být větší než nebo rovna nule. Jinak bude vyvolána výjimka. Pokud je parametr použit jako výraz, musí být typ parametru také implicitně propagačním objektem EDM. Int64, ale během kompilace nebude nijak ověřována skutečná hodnota parametru, protože hodnoty parametrů jsou zpožděny.

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

Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz použije začátek k určení horního řádku, který se má vrátit z výsledku dotazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:

1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.

2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>Viz také:

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
