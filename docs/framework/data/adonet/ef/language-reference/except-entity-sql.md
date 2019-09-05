---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: d00fdeed01de80e441d28e2bcd5da084571b0361
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251035"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)
Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operandu EXCEPT, který není také vrácen z výrazu dotazu napravo od operandu EXCEPT. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 Výjimkou je jeden z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinových operátorů. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava. V následující tabulce je uvedena priorita [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátorů set.  
  
|Priorita|Operátory|  
|----------------|---------------|  
|Lineárně|INTERSECT|  
||UNION<br /><br /> SJEDNOTIT VŠE|  
||EXCEPT|  
|Menší|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor EXCEPT k vrácení kolekce libovolných různých hodnot ze dvou výrazů dotazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
