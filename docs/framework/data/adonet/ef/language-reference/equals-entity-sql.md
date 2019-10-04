---
title: = (Je rovno) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833842"
---
# <a name="-equals-entity-sql"></a>= (Je rovno) (Entity SQL)
Porovná rovnost dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Oba výrazy musí mít implicitně převoditelné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`, pokud je levý výraz roven pravému výrazu; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Operátor = = je ekvivalentem =.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor porovnání k porovnání rovnosti dvou výrazů. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
