---
title: "- (Odečtena) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5ca2bc8cb34d99421962289930c26de84eaa68e2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="--subtract-entity-sql"></a>-(Odečtena) (entita SQL)
Odečítá od dvou čísel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz některého číselné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem implicitní typ povýšením dva argumenty. Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Pomocí následujícího dotazu Entity SQL-aritmetického operátoru má odečíst dvou čísel. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
