---
title: NASTAVIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 9d4cdeac317509fd61741a19276a6764a1c2bfce
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319355"
---
# <a name="set-entity-sql"></a>NASTAVIT (Entity SQL)
Výraz MNOŽINy se používá k převodu kolekce objektů na sadu pomocí získání nové kolekce s odebranými duplicitními prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Výraz množiny `SET(c)` je logicky ekvivalentní následujícímu příkazu SELECT:  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` je jedním z operátorů sady [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava. Viz téma [s výjimkou](except-entity-sql.md) informací o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá výraz SET pro převod kolekce objektů do sady. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
