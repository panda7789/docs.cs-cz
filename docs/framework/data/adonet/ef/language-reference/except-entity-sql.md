---
title: "S výjimkou (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 546503d3fc51c863779c26f363721bf81be054b9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="except-entity-sql"></a>S výjimkou (entita SQL)
Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operand EXCEPT nejsou také vrácená z dotazu výrazu napravo od EXCEPT operand. Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí kolekce k porovnání s kolekcí vrácená z jiného výrazu dotazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 S výjimkou je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava. V následující tabulce jsou uvedeny prioritu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.  
  
|Priorita|Operátory|  
|----------------|---------------|  
|Nejvyšší|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||S VÝJIMKOU|  
|Nejnižší|EXISTUJE<br /><br /> PŘEKRYTÍ.<br /><br /> VYROVNÁNÍ<br /><br /> NASTAVENÍ|  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru EXCEPT vracet kolekci všech jedinečných hodnot ze dvou výrazů dotazu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
