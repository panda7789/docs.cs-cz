---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: d88f79dbfcd27f0ca0d1e26815d7d2bbee731bcf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331270"
---
# <a name="in-entity-sql"></a>IN (Entity SQL)
Určuje, zda hodnota odpovídá libovolné hodnotě v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Libovolný platný výraz, který vrací hodnotu tak, aby odpovídaly.  
  
 [ NOT ]  
 Určuje, že `Boolean` ve výsledku bude negovat.  
  
 `expression`  
 Libovolný platný výraz, který vrátí kolekce, kterou chcete testovat pro shodu. Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je hodnota nalezena v kolekci. Hodnota Null, pokud je hodnota null nebo kolekci má hodnotu null; v opačném případě `false`. Pomocí NOT IN Neguje výsledky IN.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor k určení, zda hodnota odpovídá libovolné hodnotě v kolekci. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
