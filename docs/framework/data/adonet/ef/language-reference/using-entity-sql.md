---
title: "POMOCÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d1a47102c7057918c981b53f920afef09b20afad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="using-entity-sql"></a>POMOCÍ (entita SQL)
Určuje oborů názvů používaných ve výrazu dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Určuje alias kratší ke kvalifikaci v oboru názvů s.  
  
 `namespace`  
 Libovolný platný obor názvů.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru USING zadejte oborů názvů používaných ve výrazu dotazu. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Viz také  
 [Obory názvů](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
