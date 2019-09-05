---
title: '- Rozdělovací (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d4e4c1449b665e6dea22bfcc0ee2277478b4da1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251058"
---
# <a name="-divide-entity-sql"></a>/(Dělení) (Entity SQL)
Vydělí jedno číslo jiným číslem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz, který se má rozdělit `dividend`je libovolný platný výraz libovolného číselného datového typu.  
  
 `divisor`  
 Číselný výraz, podle kterého se má dělenec rozdělit. `divisor`je libovolný platný výraz libovolného číselného datového typu.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem propagace implicitního typu obou argumentů. Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá aritmetický operátor/k rozdělení jednoho čísla jiným. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
