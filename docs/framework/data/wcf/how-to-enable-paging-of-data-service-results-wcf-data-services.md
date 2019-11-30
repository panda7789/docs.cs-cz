---
title: 'Postupy: povolení stránkování výsledků datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 6b7cea2475a5c11091a04ef3044bbc958e55fc5d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569093"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Postupy: povolení stránkování výsledků datové služby (WCF Data Services)
WCF Data Services umožňuje omezit počet entit vrácených dotazem datové služby. Omezení stránky jsou definována v metodě, která je volána při inicializaci služby a lze ji nastavit samostatně pro každou sadu entit.  
  
 Pokud je povoleno stránkování, obsahuje konečná položka v informačním kanálu odkaz na další stránku dat. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).  
  
 V tomto tématu se dozvíte, jak upravit datovou službu a povolit stránkování vrácených `Customers` a `Orders` sad entit. Příklad v tomto tématu používá ukázkovou datovou službu Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Jak povolit stránkování vrácených zákazníků a objednávek sady entit  
  
- V kódu pro datovou službu nahraďte zástupný kód ve funkci `InitializeService` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Viz také:

- [Načtení odloženého obsahu](loading-deferred-content-wcf-data-services.md)
- [Postupy: Načtení stránkovaných výsledků](how-to-load-paged-results-wcf-data-services.md)
