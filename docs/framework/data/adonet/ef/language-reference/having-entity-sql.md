---
title: S (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bfa8b49b486b2bc20009874562c42ec92aa538d1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="having-entity-sql"></a>S (entita SQL)
Určuje podmínku vyhledávání pro skupinu nebo agregace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Určuje podmínku vyhledávání pro skupiny nebo agregace splnění. Při HAVING se používá s GROUP BY ALL, klauzule HAVING přepíše všechny.  
  
## <a name="remarks"></a>Poznámky  
 V klauzuli HAVING slouží k určení další podmínku filtrování na výsledek seskupení. Pokud ve výrazu dotazu je zadána klauzule GROUP BY, předpokládá se skupinu implicitní single-set.  
  
> [!NOTE]
>  HAVING lze použít pouze s [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkaz. Když [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) se nepoužívá, HAVING chová jako klauzuli WHERE.  
  
 V klauzuli HAVING funguje jako klauzule WHERE, s tím rozdílem, že se použije po operaci GROUP BY. To znamená, že v klauzuli HAVING lze vytvořit pouze odkazy na seskupení aliasy a agregace, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Předchozí omezuje skupiny jenom na ty, které obsahují více produktů.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátory HAVING a GROUP BY k zadání podmínek vyhledávání pro skupinu nebo agregace. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
