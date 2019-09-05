---
title: NASTAVIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249242"
---
# <a name="set-entity-sql"></a>NASTAVIT (Entity SQL)
Výraz MNOŽINy se používá k převodu kolekce objektů na sadu pomocí získání nové kolekce s odebranými duplicitními prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Výraz `SET(c)` množiny je logicky ekvivalentní následujícímu příkazu SELECT:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET`je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množin operátorů. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava. Viz [s výjimkou](except-entity-sql.md) pro informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prioritách pro množinové operátory.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá výraz SET pro převod kolekce objektů do sady. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
