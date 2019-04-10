---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32b5148e43a38e5cf8dcce0ae16260d7a6b6a018
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341215"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)
Vrátí kolekci všech jedinečných hodnot z výrazu dotazu k levému operandu EXCEPT, která nejsou také vrácen z výrazu dotazu napravo od EXCEPT operand. Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný výraz platný dotaz, který vrátí kolekce k porovnání s kolekci vrácené z jiného výrazu dotazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 S výjimkou je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava. V následující tabulce jsou uvedeny prioritu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.  
  
|Priorita|Operátory|  
|----------------|---------------|  
|Nejvyšší|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||EXCEPT|  
|Nejnižší|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Příklad  
 Následující dotaz SQL entit vrátí kolekci všech jedinečných hodnot ze dvou výrazů dotazů pomocí operátoru EXCEPT. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
