---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 6ed20ea372314421e4855b1c1ad761c87bf461b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702558"
---
# <a name="top-entity-sql"></a>TOP (Entity SQL)
Klauzule SELECT může mít volitelné dílčí klauzule TOP následující volitelný modifikátor ALL/DISTINCT. Dílčí klauzule TOP Určuje, že bude vrácen pouze první sada řádků z výsledku dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Číselný výraz, který určuje počet řádků, který se má vrátit. `n` může být jeden číselný literál nebo jeden parametr.  
  
## <a name="remarks"></a>Poznámky  
 HLAVNÍ výraz musí být jeden číselný literál nebo jeden parametr. Pokud se používá konstantní literál, typ literálu musí být implicitně možné zvýšit na Edm.Int64 (byte, int16, int32 nebo int64 nebo libovolný typ zprostředkovatele, který se mapuje na typ, který je možné zvýšit na Edm.Int64) a jeho hodnota musí být větší než nebo rovna hodnotě nula. Jinak bude vyvolána výjimka. Pokud parametr je používán jako výraz, typ parametru musí být také implicitně možné zvýšit na Edm.Int64, ale nebudou žádné ověření skutečný parametr hodnoty během kompilace vzhledem k tomu, že hodnoty parametrů jsou pozdní omezená.  
  
 Následuje příklad konstantní výraz TOP:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 Následuje příklad výrazu nejvyšší podle:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 Začátek je Nedeterministický, pokud dotaz má řazení proběhnout. Pokud budete potřebovat deterministické výsledky, použijte [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí ustanovení [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli. TOP a SKIP/LIMIT se vzájemně vylučují.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá k určení nejvyšší jeden řádek, který se má vrátit z výsledku dotazu horní části. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Viz také:
- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
