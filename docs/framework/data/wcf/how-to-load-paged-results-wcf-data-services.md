---
title: 'Postupy: Načtení stránkovaných výsledků (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: 0be7dcbefb23d2f2b283ac498f3b0ea43278f2d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517249"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Postupy: Načtení stránkovaných výsledků (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje datové služby a omezit počet entit, které jsou vráceny v odpověď o jedné informačního kanálu. Pokud k tomu dojde, poslední položku v informačním kanálu obsahuje odkaz na další stránku data. Identifikátor URI další stránky dat se získá voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metodu <xref:System.Data.Services.Client.QueryOperationResponse%601>, která je vrácena, pokud <xref:System.Data.Services.Client.DataServiceQuery%601> provádí. Identifikátor URI reprezentovaný tímto objektem se pak použije k načtení další stránky výsledků. Další informace najdete v tématu [načítání odložené obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `do…while` smyčce načtení `Customers` entit na základě stránkové výsledky z datové služby.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vrátí související `Orders` entity s každým `Customers` entity a použije `do…while` smyčce načtení `Customers` stránky entity a vnořený `while` smyčce načtení stránky související `Orders` entity z datové služby .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [Postupy: Načtení souvisejících entit](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
