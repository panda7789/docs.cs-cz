---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: e2d2c4cd6fd62cf5785d6b69aa399a74f8d04d30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326733"
---
# <a name="modulo-entity-sql"></a>(Modulo) (Entity SQL)
Vrátí zbytek jeden výraz hodnotou druhého.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz, který se má dělit. `dividend` je libovolný platný výraz některou z číselných datových typů.  
  
 `divisor`  
 Číselný výraz, který se má dělit dělenec. `divisor` je libovolný platný výraz některou z číselných datových typů.  
  
## <a name="result-types"></a>Typy výsledků  
 Edm.Int32  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá aritmetického operátoru % vrátit zbývající jeden výraz hodnotou druhého. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
