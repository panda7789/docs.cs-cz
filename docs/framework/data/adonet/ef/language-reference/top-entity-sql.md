---
title: "HORNÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b1d3d1b07a349ab1a5efb4a7c41f9b9b34fc55f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="top-entity-sql"></a>HORNÍ (entita SQL)
Klauzule SELECT může obsahovat volitelné nejvyšší dílčí klauzuli následující volitelné modifikátor všechna nebo DISTINCT. Dílčí klauzule TOP Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Číselný výraz, který určuje počet řádků, který se má vrátit. `n`může být jeden číselný literál nebo jeden parametr.  
  
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
 [VYBERTE](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [PŘESKOČIT](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [ŘADIT PODLE](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
