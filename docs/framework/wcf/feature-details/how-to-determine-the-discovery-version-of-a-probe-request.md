---
title: "Postupy: Určení verze zjišťování zkušebního požadavku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 383d96e661ca7872108b40f69be86ef4e1ca63b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
 [Implementace Proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Ukázka proxy serveru zjišťování](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
