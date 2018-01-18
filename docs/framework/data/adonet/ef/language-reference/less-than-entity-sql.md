---
title: "&lt;(Méně než) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5bf1560c0bebafcfdbf79ca9a9906c9df23b7cae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="lt-less-than-entity-sql"></a>&lt;(Méně než) (Entita SQL)
Porovná dva výrazy a určit, zda má hodnotu menší, než pravý výraz levý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz. Oba výrazy musí mít implicitně převést datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`Pokud levý výraz má hodnotu menší, než pravý výraz; v opačném `false`.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá < – operátor porovnání k porovnání dvou výrazů k určení, zda má hodnotu menší, než pravý výraz levý výraz. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
