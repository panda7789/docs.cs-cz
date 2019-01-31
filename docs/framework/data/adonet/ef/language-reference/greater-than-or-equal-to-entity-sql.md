---
title: '>= (Větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 4b7b2aa7be0b978fb6b1317393fb3c6e9a87c621
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289009"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a>> = (větší než nebo rovno) (Entity SQL)
Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Implicitně převést datové typy musí mít oba výrazy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true` Pokud levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz; v opačném případě `false`.  
  
## <a name="example"></a>Příklad  
 Pomocí následujícího dotazu Entity SQL > = – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
