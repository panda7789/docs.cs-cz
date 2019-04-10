---
title: = (Rovná se) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: ad9eda5a3544ea157d06c57876b1b0454a25dba1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215674"
---
# <a name="-equals-entity-sql"></a>= (Rovná se) (Entity SQL)
Porovná rovnost dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz. Implicitně převést datové typy musí mít oba výrazy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true` Pokud levý výraz rovná pravý výraz; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 == – Operátor je ekvivalentní =.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá = – operátor porovnání k porovnání rovnosti dvou výrazů. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
