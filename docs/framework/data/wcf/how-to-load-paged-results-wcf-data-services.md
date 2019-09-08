---
title: 'Postupy: Načíst stránkované výsledky (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: e718aad904a43d118a243afafc17834cba31f028
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790454"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Postupy: Načíst stránkované výsledky (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]povoluje datové službě omezit počet entit, které jsou vráceny v jednom kanálu odpovědí. Pokud k tomu dojde, poslední položka v informačním kanálu obsahuje odkaz na další stránku dat. Identifikátor URI pro další stránku dat je získán voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody <xref:System.Data.Services.Client.QueryOperationResponse%601>, <xref:System.Data.Services.Client.DataServiceQuery%601> která je vrácena při spuštění. Identifikátor URI reprezentovaný tímto objektem se pak použije k načtení další stránky výsledků. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se `do…while` používá smyčka `Customers` k načtení entit ze stránkovaných výsledků z datové služby.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Příklad  
 Tento příklad vrátí související `Orders` entity s každou `Customers` entitou a pomocí `do…while` smyčky načte `Customers` stránky entit a vnořenou `while` smyčku pro načtení stránek souvisejících `Orders` entit z datové služby. .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení odloženého obsahu](loading-deferred-content-wcf-data-services.md)
- [Postupy: Načíst související entity](how-to-load-related-entities-wcf-data-services.md)
