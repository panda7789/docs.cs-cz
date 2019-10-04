---
title: SHRNOUT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833810"
---
# <a name="flatten-entity-sql"></a>SHRNOUT (Entity SQL)
Převede kolekci kolekcí do ploché kolekce. Nová kolekce obsahuje všechny stejné prvky jako starou kolekci, ale bez vnořené struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Arguments  
 `collection`  
 Libovolný platný výraz, který vrátí kolekci hodnot kolekcí, které mají být shrnuty do jedné kolekce.  
  
## <a name="remarks"></a>Poznámky  
 `FLATTEN` je jedním z operátorů sady [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava. Viz téma [s výjimkou](except-entity-sql.md) informací o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor `FLATTEN` k převodu kolekce kolekcí do ploché kolekce. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
