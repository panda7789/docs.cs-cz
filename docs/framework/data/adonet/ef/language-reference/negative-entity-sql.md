---
title: '- Příznivé (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319528"
---
# <a name="--negative-entity-sql"></a>-(Negativní) (Entity SQL)
Vrátí záporné hodnoty číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz libovolného číselného datového typu.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ `expression`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je `expression` typ bez znaménka, typ výsledku bude podepsaný typ, který se nejvíce blíží typu `expression`. Například pokud je `expression` typu Byte, bude vrácena hodnota typu Int16.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru-aritmetické operace vrátí záporné hodnoty číselného výrazu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
