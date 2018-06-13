---
title: HORNÍ (entita SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 25afda64aafcd5a97dee7ad4cee25b152ef55907
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764655"
---
# <a name="top-entity-sql"></a>HORNÍ (entita SQL)
Klauzule SELECT může obsahovat volitelné nejvyšší dílčí klauzuli následující volitelné modifikátor všechna nebo DISTINCT. Dílčí klauzule TOP Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Číselný výraz, který určuje počet řádků, který se má vrátit. `n` může být jeden číselný literál nebo jeden parametr.  
  
## <a name="remarks"></a>Poznámky  
 Výraz TOP musí být jeden číselný literál nebo jeden parametr. Pokud se použije konstantní literál, musí být typu literálu implicitně možné zvýšit na Edm.Int64 (bajtů, int16, int32 nebo int64 nebo žádný typ zprostředkovatele, který se mapuje na typ, který je možné zvýšit na Edm.Int64) a jeho hodnota musí být větší než nebo rovna hodnotě nula. V opačném případě bude vyvolána výjimka. Pokud parametr je použit jako výraz, typ parametru musí být také implicitně možné zvýšit na Edm.Int64, ale nebude žádné ověření skutečný parametr hodnoty během kompilace vzhledem k tomu, že jsou hodnoty parametru pozdní vázaný.  
  
 Následuje příklad konstantní výraz TOP:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 Následuje příklad umožňující jako výraz TOP:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 HORNÍ je Nedeterministický, pokud je seřazen dotazu. Pokud budete potřebovat výsledku deterministický, použijte [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule v [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule. TOP a SKIP/LIMIT se vzájemně vylučují.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá horní k určení nejvyšší jeden řádek, který se má vrátit z výsledku dotazu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Viz také  
 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
