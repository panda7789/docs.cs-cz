---
title: "OMEZENÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c890bf6950f94c04350902276193f5a43239f63f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="limit-entity-sql"></a>OMEZENÍ (entita SQL)
Fyzické stránkování lze provést pomocí dílčí klauzuli LIMIT v klauzuli ORDER by. LIMIT nelze použít samostatně z klauzule ORDER by.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Počet položek, které bude možné vybrat.  
  
 Pokud dílčí klauzuli LIMIT výrazu nachází v klauzuli ORDER BY, dotaz seřadí podle specifikace řazení a výsledný počet řádků, bude omezený LIMIT výrazem. Například LIMIT 5 se omezí sadu výsledků do 5 instance nebo řádků. LIMIT je funkčně srovnatelný horní s tím rozdílem, že LIMIT vyžaduje klauzule ORDER by nacházet. Přeskočit a LIMIT můžete použít nezávisle klauzule ORDER by.  
  
> [!NOTE]
>  Entity Sql dotazu bude považovat za neplatné, pokud nejvyšší modifikátor a dílčí klauzuli SKIP se nachází ve stejném výrazu dotazu. Dotaz by měl být přepsána změnou jako výraz TOP na výrazu omezení.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru Order limit pro určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Viz také  
 [ŘADIT PODLE](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Postupy: výsledky stránky prostřednictvím dotazu](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Stránkování](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [HORNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
