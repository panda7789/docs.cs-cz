---
title: V (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553b2037ef9b1eead3a3f4745d0cb6fdfcde27ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="in-entity-sql"></a>V (entita SQL)
Určuje, zda hodnota odpovídá libovolná hodnota v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Libovolný platný výraz, který vrací hodnotu tak, aby odpovídaly.  
  
 [NOT]  
 Určuje, že `Boolean` být Negované výsledek IN.  
  
 `expression`  
 Jakýkoli platný výraz, který vrátí kolekce k testování shody. Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je hodnota nalezena v kolekci. Hodnota Null, pokud hodnota je null nebo kolekce hodnotu null. v opačném `false`. Pomocí NOT IN Neguje výsledky IN.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor k určení, zda hodnota odpovídá libovolná hodnota v kolekci. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
