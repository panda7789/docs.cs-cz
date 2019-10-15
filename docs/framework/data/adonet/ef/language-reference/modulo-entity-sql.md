---
title: Operace (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 4bbdbe53403cfec2568cfac320fc7ab1ad2725b0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319600"
---
# <a name="modulo-entity-sql"></a>Operace (Entity SQL)
Vrátí zbytek jednoho výrazu děleného jiným.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz, který se má rozdělit `dividend` je libovolný platný výraz libovolného číselného datového typu.  
  
 `divisor`  
 Číselný výraz, podle kterého se má dělenec rozdělit. `divisor` je libovolný platný výraz libovolného číselného datového typu.  
  
## <a name="result-types"></a>Typy výsledků  
 EDM. Int32  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí aritmetického operátoru% vrátí zbytek jednoho výrazu děleného jiným. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
