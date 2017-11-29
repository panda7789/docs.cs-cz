---
title: "Stránkování (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6188587a8b588128092f5d9f02f6962159b928e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="paging-entity-sql"></a>Stránkování (entita SQL)
Fyzické stránkování lze provést pomocí [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule v [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule. K provedení fyzické stránkování nepodmíněně, měli byste použít přeskočit a LIMIT. Pokud chcete omezit počet řádků ve výsledku způsobem, bez determinsitic, měli byste použít [horní](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP a SKIP/LIMIT se vzájemně vylučují.  
  
## <a name="top-overview"></a>TOP – přehled  
 Klauzule SELECT může obsahovat volitelné nejvyšší dílčí klauzuli následující volitelné modifikátor všechna nebo DISTINCT. Dílčí klauzule TOP Určuje, že bude vrácen pouze první sadu řádků z výsledku dotazu. Další informace najdete v tématu [horní](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Přeskočit a LIMIT – přehled  
 Přeskočit a omezení jsou součástí klauzuli ORDER by. Pokud se nachází dílčí klauzuli SKIP výrazu v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sadu výsledků dotazu zahrne řádky od na další řádek hned po výrazu SKIP. Například bude 5 PŘESKOČENÍ přeskočte prvních pět řádky a vrátí z šesté řádek dál. Pokud dílčí klauzuli LIMIT výrazu nachází v klauzuli ORDER BY, dotaz seřadí podle specifikace řazení a výsledný počet řádků, bude omezený LIMIT výrazem. Například LIMIT 5 se omezí sadu výsledků do pěti instance nebo řádků. Přeskočit a LIMIT nemusí být použity současně; můžete použít jenom přeskočit nebo omezit pouze s klauzulí ORDER BY. Další informace naleznete v následujících tématech:  
  
-   [PŘESKOČIT](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ŘADIT PODLE](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Postupy: výsledky stránky prostřednictvím dotazu](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
