---
title: "- (Záporné hodnoty) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0cc2ca457fe8666bddd6f4ab40d2823d9d44c591
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="--negative-entity-sql"></a>-(Záporné) (entita SQL)
Vrátí záporná hodnota číselného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz některého číselné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ `expression`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `expression` je typ nepodepsané výsledný typ bude typ se znaménkem nejvíce má vztah typu `expression`. Například pokud `expression` je typu bajtů, se hodnota typu Int16 bude vrácen.  
  
## <a name="example"></a>Příklad  
 Pomocí následujícího dotazu Entity SQL-aritmetického operátoru vrátit záporná hodnota číselného výrazu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
