---
title: S VÝJIMKou (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833859"
---
# <a name="except-entity-sql"></a>S VÝJIMKou (Entity SQL)
Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operandu EXCEPT, který není také vrácen z výrazu dotazu napravo od operandu EXCEPT. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 VÝJIMKou je jeden z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava. Následující tabulka ukazuje prioritu operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Priorita|Operátory|  
|----------------|---------------|  
|Lineárně|INTERSECT|  
||UNION<br /><br /> SJEDNOTIT VŠE|  
||EXCEPT|  
|Menší|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor EXCEPT k vrácení kolekce libovolných různých hodnot ze dvou výrazů dotazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
