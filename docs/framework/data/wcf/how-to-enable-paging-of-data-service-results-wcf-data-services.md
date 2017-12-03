---
title: "Postupy: povolení stránkování výsledků služby dat (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9156ddbe9482683660524898aa0c6ce3673cd75f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Postupy: povolení stránkování výsledků služby dat (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje omezit počet vrácených dotazem služby data entity. Stránka omezení jsou definovány v metodu, která je volána, když služba je inicializován a můžete nastavit samostatně pro každou sadu entit.  
  
 Pokud je povoleno stránkování, poslední položku v informačním kanálu obsahuje odkaz na další stránku data. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Toto téma ukazuje, jak změnit datové služby pro povolení stránkování z vráceného `Customers` a `Orders` sady entit. Příklad v tomto tématu používá službu Northwind ukázková data. Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Postup povolení stránkování vrácený zákazníci a objednávky sad entit  
  
-   V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Viz také  
 [Odložené načtení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Postupy: načtení stránkovaného výsledky](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
