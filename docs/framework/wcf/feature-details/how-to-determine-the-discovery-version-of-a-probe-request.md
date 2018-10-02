---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 98dfd5ec5d3c180b619e2f15d95037feae8ebbaf
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48031572"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Postupy: Určení verze zjišťování zkušebního požadavku
Proxy zjišťování může vystavit několik koncových bodů zjišťování pomocí zjišťování různých verzí. Když vícesměrového vysílání UDP dorazí požadavek testu na proxy serveru proxy server by měl odpovědět vícesměrovou zprávu. Pokud to chcete udělat byste museli znát verze zjišťování požadavku.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>K určení verze zjišťování zkušebního požadavku  
  
1.  V metodě, která bude reagovat na požadavek testu (například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) pomocí statické <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost k vyhledání <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak je znázorněno v následujícím kódu.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Viz také  

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
- [Implementace proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  