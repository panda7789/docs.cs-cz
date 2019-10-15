---
title: SJEDNOCENí (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: a5a20beb0ab55dcbaf2dbbb75801b50ab9ef6722
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319221"
---
# <a name="union-entity-sql"></a>SJEDNOCENí (Entity SQL)
Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrátí kolekci, která se má zkombinovat s kolekcí, musí být stejného typu nebo ze společného základního nebo odvozeného typu jako `expression`.  
  
 UNION  
 Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce.  
  
 VŠEM  
 Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce, včetně duplicitních hodnot. Pokud není zadán, jsou duplicity z kolekce výsledků odebrány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 UNION je jednou z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava. Informace o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] naleznete v tématu [Except](except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor UNION ALL ke kombinování výsledků dvou dotazů do jedné kolekce. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
