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
ms.workload: dotnet
ms.openlocfilehash: 0f51f48d6eefcc0f8ae5129526477d6e2a5b2385
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
