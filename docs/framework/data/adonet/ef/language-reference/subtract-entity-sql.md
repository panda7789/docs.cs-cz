---
title: '- Odečten (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: fe9152100bddac86f3fb7fae1ab3c0b81ae58418
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319332"
---
# <a name="--subtract-entity-sql"></a>-(Odečíst) (Entity SQL)
Odečte dvě čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz libovolného číselného datového typu.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem propagace implicitního typu obou argumentů. Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru-aritmetické operace odečtou dvě čísla. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
