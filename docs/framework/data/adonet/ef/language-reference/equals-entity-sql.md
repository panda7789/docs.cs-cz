---
title: "= (Rovná) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 27faf6c59afd4de2481f474053812b12182e3f58
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="-equals-entity-sql"></a>= (Rovná) (entita SQL)
Porovnání rovnosti dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz. Oba výrazy musí mít implicitně převést datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`Pokud levý výraz rovná pravý výraz; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 == Operátor je ekvivalentní =.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá = – operátor porovnání k porovnání rovnosti dvou výrazů. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
