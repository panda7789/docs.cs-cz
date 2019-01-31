---
title: < = (je menší než nebo rovno) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 68a4c91800dce2ab6a632e849a8c58c378150535
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284710"
---
# <a name="-less-than-or-equal-to-entity-sql"></a>\<= (Je menší než nebo rovno) (Entity SQL)
Porovná dva výrazy k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Implicitně převést datové typy musí mít oba výrazy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true` Pokud levý výraz má hodnotu menší než nebo rovna pravý výraz; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá < = – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
