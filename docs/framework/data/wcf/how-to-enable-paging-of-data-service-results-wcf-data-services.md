---
title: 'Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: be5bd41494c27724a360b785b8706b618447e7de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523452"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje omezit počet entit vrácených dotazem dat služby. Stránky omezení jsou definovány v metodě, která je volána, když služba je inicializována a je možné nastavit zvlášť pro každou sadu entit.  
  
 Když je povoleno stránkování, poslední položku v informačním kanálu obsahuje odkaz na další stránku data. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Toto téma ukazuje, jak změnit datové služby umožňující stránkování vrácené `Customers` a `Orders` sady entit. V příkladu v tomto tématu se používá ukázková datová služba Northwind. Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Jak povolit stránkování vrácené zákazníci a objednávky sady entit  
  
-   V kódu pro datovou službu, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Viz také:
- [Načtení odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [Postupy: Načtení stránkovaných výsledků](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
