---
title: = (Rovná se) (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150309"
---
# <a name="-equals-entity-sql"></a>= (Rovná se) (Entita SQL)
Porovná rovnost dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný výraz Oba výrazy musí mít implicitně konvertibilní datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`pokud je levý výraz roven pravému výrazu; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 Operátor == je ekvivalentní =.  
  
## <a name="example"></a>Příklad  
 Následující entita SQL dotaz používá = operátor porovnání porovnat rovnost dvou výrazů. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
