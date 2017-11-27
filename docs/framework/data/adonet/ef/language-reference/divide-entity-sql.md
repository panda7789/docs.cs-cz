---
title: "- (Dělení) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0f215e12f9f86ee08679bdb2e2638c0c8df35ea4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="-divide-entity-sql"></a>/ (Dělení) (entita SQL)
Vydělí jedno číslo jiným.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz k rozdělení. `dividend`je jakýkoli platný výraz některého číselné datové typy.  
  
 `divisor`  
 Číselný výraz k rozdělení dělenec podle. `divisor`je jakýkoli platný výraz některého číselné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 Datový typ, který je výsledkem implicitní typ povýšením dva argumenty. Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá / aritmetické operátor rozdělit jeden kontrolních jiným. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
