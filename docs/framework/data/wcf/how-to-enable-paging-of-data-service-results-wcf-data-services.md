---
title: 'Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780049"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje omezit počet entit vrácených dotazem datové služby. Omezení stránky jsou definována v metodě, která je volána při inicializaci služby a lze ji nastavit samostatně pro každou sadu entit.  
  
 Pokud je povoleno stránkování, obsahuje konečná položka v informačním kanálu odkaz na další stránku dat. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).  
  
 V tomto tématu se dozvíte, jak upravit datovou službu a povolit `Customers` stránkování `Orders` vrácených a sad entit. Příklad v tomto tématu používá ukázkovou datovou službu Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Jak povolit stránkování vrácených zákazníků a objednávek sady entit  
  
- V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení odloženého obsahu](loading-deferred-content-wcf-data-services.md)
- [Postupy: Načíst stránkované výsledky](how-to-load-paged-results-wcf-data-services.md)
