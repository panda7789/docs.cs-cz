---
title: '! = (Nerovná se) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: f5fdbbf2892781ce44dfe73e8cd80fbe0f74cf1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760334"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Nerovná se) (Entity SQL)
Porovná dva výrazy k určení, zda levý výraz není roven pravý výraz. ! = – Operátor (není rovno) je funkčně srovnatelný s <> operátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Implicitně převést datové typy musí mít oba výrazy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true` Pokud levý výraz není roven pravý výraz; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá! = – operátor porovnání dvou výrazů k určení, zda levý výraz není roven pravý výraz. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
