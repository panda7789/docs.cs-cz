---
title: '- (Dělení) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: c3b477a63adf3c3d51f28449e94c2b716422296c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330854"
---
# <a name="-divide-entity-sql"></a>/ (Dělení) (Entity SQL)
Rozdělí jedno číslo jiným.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz, který se má dělit. `dividend` je libovolný platný výraz některou z číselných datových typů.  
  
 `divisor`  
 Číselný výraz, který se má dělit dělenec. `divisor` je libovolný platný výraz některou z číselných datových typů.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů. Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá / aritmetický operátor dělit jednu číslici jiného. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
