---
title: < = (je menší než nebo rovno) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: b3c8fef47b06b9fdd0a1619a9e56d3d916d9dd2d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319638"
---
# <a name="-less-than-or-equal-to-entity-sql"></a>\< = (je menší než nebo rovno) (Entity SQL)
Porovná dva výrazy a určí, zda má levý výraz hodnotu menší nebo rovnu pravému výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Oba výrazy musí mít implicitně převoditelné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`, pokud má levý výraz hodnotu menší nebo rovnu pravému výrazu; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru < = Compare Porovná dva výrazy a určí, zda má levý výraz hodnotu menší nebo roven pravému výrazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
