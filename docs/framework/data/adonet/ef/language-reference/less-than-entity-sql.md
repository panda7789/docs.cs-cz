---
title: '&lt; (Méně než) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 0c2185f824cfbe201b4138d0082e3edcf93e6a7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598313"
---
# <a name="lt-less-than-entity-sql"></a>&lt; (Méně než) (Entity SQL)
Porovná dva výrazy k určení, zda levý výraz má hodnotu menší, než pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Implicitně převést datové typy musí mít oba výrazy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true` Pokud levý výraz má hodnotu menší, než pravý výraz; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá < – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu menší, než pravý výraz. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
