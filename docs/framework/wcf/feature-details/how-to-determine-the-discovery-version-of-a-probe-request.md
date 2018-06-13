---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8ac9804b0fe46ca5fbe580d713ec82a2f9bb0128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489778"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Postupy: Určení verze zjišťování zkušebního požadavku
Zjišťování proxy vystavuje několik koncových bodů zjišťování pomocí různých zjišťování verze. Když UDP, vícesměrového vysílání zkušebního požadavku dorazí na proxy server, které proxy server by měl odpovídat zprávy vícesměrového vysílání potlačení. Pokud to chcete provést by mít vědět verze zjišťování požadavku.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Určení verze zjišťování zkušebního požadavku  
  
1.  V metodě odpoví na žádost o test (třeba <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) použít statickou <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost k vyhledání <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak je znázorněno v následujícím kódu.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [Implementace proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Ukázka proxy zjišťování](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
