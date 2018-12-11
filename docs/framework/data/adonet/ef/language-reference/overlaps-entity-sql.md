---
title: PŘEKRYTÍ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: f0c5d79b437ff06603ea10404357aa0b3270bc53
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150769"
---
# <a name="overlaps-entity-sql"></a>PŘEKRYTÍ (Entity SQL)
Určuje, jestli dvě kolekce mají společné prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný výraz platný dotaz, který vrátí kolekce k porovnání s kolekci vrácené z jiného výrazu dotazu. Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se dvě kolekce mají společné prvky; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 PŘEKRYTÍ nabízí funkčně ekvivalentní následujícímu:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 PŘEKRYTÍ je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava. Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory, naleznete v tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru PŘEKRÝVÁ se určuje, zda mají dvě kolekce společné hodnoty. Dotaz je založen na modelu Sales AdventureWorks. Chcete-li zkompilovat a spustit, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
