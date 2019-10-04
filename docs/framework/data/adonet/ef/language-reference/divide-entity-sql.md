---
title: '- Rozdělovací (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 79fdbebc648daac4f695387d52d2a915383f99ca
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833889"
---
# <a name="-divide-entity-sql"></a>/(Dělení) (Entity SQL)
Vydělí jedno číslo jiným číslem.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz, který se má rozdělit `dividend` je libovolný platný výraz libovolného číselného datového typu.  
  
 `divisor`  
 Číselný výraz, podle kterého se má dělenec rozdělit. `divisor` je libovolný platný výraz libovolného číselného datového typu.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem propagace implicitního typu obou argumentů. Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá aritmetický operátor/k rozdělení jednoho čísla jiným. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
