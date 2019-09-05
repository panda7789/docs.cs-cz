---
title: SJEDNOCENí (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 34eac0dfd28d39ec68f084ea10dd46693f44eea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248788"
---
# <a name="union-entity-sql"></a>SJEDNOCENí (Entity SQL)
Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci, která má být kombinována s kolekcí, všechny výrazy musí být stejného typu nebo typu společný základní nebo odvozený `expression`typ.  
  
 UNION  
 Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce.  
  
 VŠEM  
 Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce, včetně duplicitních hodnot. Pokud není zadán, jsou duplicity z kolekce výsledků odebrány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 Union je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinových operátorů. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava. Informace o prioritách pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory naleznete v tématu [Except](except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor UNION ALL ke kombinování výsledků dvou dotazů do jedné kolekce. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
