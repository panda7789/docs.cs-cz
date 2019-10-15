---
title: < (Méně než) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: fb3f4a1c6bc0df6af3c27836f7b53b2701776366
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319684"
---
# <a name="-less-than-entity-sql"></a>\< (méně než) (Entity SQL)
Porovná dva výrazy a určí, zda má levý výraz hodnotu menší než pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Oba výrazy musí mít implicitně převoditelné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`, pokud má levý výraz hodnotu menší než pravý výraz; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru porovnání < Porovná dva výrazy a určí, zda má levý výraz hodnotu menší než pravý výraz. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
