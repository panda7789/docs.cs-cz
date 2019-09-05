---
title: SHRNOUT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 327a20bbc53566846e7d828f511bcd1d25cc5504
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250959"
---
# <a name="flatten-entity-sql"></a>SHRNOUT (Entity SQL)
Převede kolekci kolekcí do ploché kolekce. Nová kolekce obsahuje všechny stejné prvky jako starou kolekci, ale bez vnořené struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Arguments  
 `collection`  
 Libovolný platný výraz, který vrátí kolekci hodnot kolekcí, které mají být shrnuty do jedné kolekce.  
  
## <a name="remarks"></a>Poznámky  
 `FLATTEN`je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množin operátorů. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava. Viz [s výjimkou](except-entity-sql.md) pro informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prioritách pro množinové operátory.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá `FLATTEN` operátor k převodu kolekce kolekcí do ploché kolekce. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
