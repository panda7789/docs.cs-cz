---
title: '> (Je větší než) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: f2d3a0ed81cf75b7e567dbd07e119629ea47ac69
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833774"
---
# <a name="-greater-than-entity-sql"></a>> (Je větší než) (Entity SQL)
Porovná dva výrazy a určí, zda má levý výraz hodnotu větší než pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Oba výrazy musí mít implicitně převoditelné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`, pokud má levý výraz hodnotu větší než pravý výraz; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru porovnání > Porovná dva výrazy a určí, zda má levý výraz hodnotu větší než pravý výraz. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
