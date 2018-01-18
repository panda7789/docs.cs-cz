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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d32e5012b4acbf0ecd6830f549de5dccf79bb38b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
  
 [ NOT ]  
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
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
