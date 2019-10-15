---
title: PŘEKRYVy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: bdee9281fd406a3d029d3a10536cbdd48d2f7a58
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319418"
---
# <a name="overlaps-entity-sql"></a>PŘEKRYVy (Entity SQL)
Určuje, zda dvě kolekce mají společné prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, pokud mají dvě kolekce společné prvky; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 PŘEKRYVy poskytují funkčně ekvivalentní následujícímu:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 Překrytí je jedním z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava. Informace o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] naleznete v tématu [Except](except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor překrytí k určení, zda dvě kolekce mají společnou hodnotu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Pro zkompilování a spuštění použijte následující postup:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
