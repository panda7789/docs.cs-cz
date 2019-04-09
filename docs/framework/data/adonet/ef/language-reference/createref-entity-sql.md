---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 7003805429df36fec82e5d57811ed38af6323379
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095604"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
Fabricates odkazy na entity v element entityset.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Identifikátor objektu entityset, není řetězcový literál.  
  
 `row_typed_expression`  
 Výraz zadaný řádek, který odpovídá klíčové vlastnosti typu entity.  
  
## <a name="remarks"></a>Poznámky  
 `row_typed_expression` musí být strukturálně ekvivalentní typ klíče entity. To znamená musí mít stejný počet a typy polí ve stejném pořadí jako klíče entity.  
  
 V následujícím příkladu objednávky a BadOrders jsou oba objekty EntitySet typu pořadí a Id je považován za jednu klíčovou vlastnost pořadí. Příklad ukazuje, jak jsme může vytvořit odkaz na entitu v BadOrders. Všimněte si, že odkaz může být dangling.  Odkaz na tedy nemusí ve skutečnosti identifikovat konkrétní entity. V těchto případech se `DEREF` operace na tento odkaz, vrátí hodnotu null.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru CREATEREF vyrobit odkazy na entity v sadě entit. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
