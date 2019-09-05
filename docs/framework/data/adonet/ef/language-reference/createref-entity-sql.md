---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251104"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
Naprefabrikované odkazy na entitu v objektu EntitySet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Identifikátor EntitySet, nikoli řetězcový literál.  
  
 `row_typed_expression`  
 Výraz typu řádek, který odpovídá klíčovým vlastnostem typu entity.  
  
## <a name="remarks"></a>Poznámky  
 `row_typed_expression`musí být strukturálně stejné jako typ klíče pro entitu. To znamená, že musí mít stejný počet a typy polí ve stejném pořadí jako klíče entit.  
  
 V následujícím příkladu jsou Orders a BadOrders oba objekty EntitySet typu Order a ID se považuje za klíčovou vlastnost Order. Příklad ukazuje, jak můžeme vytvořit odkaz na entitu v BadOrders. Všimněte si, že odkaz může být dangling.  To znamená, že odkaz nemusí skutečně identifikovat konkrétní entitu. V těchto případech `DEREF` operace s tímto odkazem vrátí hodnotu null.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor CREATEREF k vytvoření odkazu na entitu v sadě entit. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
