---
title: Sada (entita SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 3008939798af98d449ec14e4d774ebc1a6e0d89d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763836"
---
# <a name="set-entity-sql"></a>Sada (entita SQL)
Výraz sady se používá k získávání novou kolekci s všechny elementy s duplicitním odebrat převést na kolekci objektů do sady.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný dotaz výraz, která vrátí kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Výraz sady `SET(c)` logicky odpovídá následující příkaz select:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` patří mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava. V tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) přednost informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá pro převod na kolekci objektů do sady výraz sady. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
