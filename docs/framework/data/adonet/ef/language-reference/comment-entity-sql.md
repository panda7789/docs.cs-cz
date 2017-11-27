---
title: "--(Komentář) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1961542e615bbbd99bbc517bdd7d649be3f3ef07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="---comment-entity-sql"></a>--(Komentář) (entita SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]dotazy může obsahovat komentáře. Dvě pomlčky (`--`) spustit řádek poznámky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  
 `text_of_comment`  
 Je řetězec znaků, který obsahuje text poznámky.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL demonstruje použití komentáře. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
