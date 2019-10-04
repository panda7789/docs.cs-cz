---
title: '>= (Je větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833748"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a>> = (je větší než nebo rovno) (Entity SQL)
Porovná dva výrazy a určí, zda má levý výraz hodnotu větší nebo rovnu pravému výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Oba výrazy musí mít implicitně převoditelné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`, pokud má levý výraz hodnotu větší nebo rovnou pravému výrazu; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru > = Compare Porovná dva výrazy a určí, zda má levý výraz hodnotu větší nebo rovnu pravému výrazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
