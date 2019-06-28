---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425271"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Postupy: Určení verze zjišťování zkušebního požadavku

Proxy zjišťování může vystavit několik koncových bodů zjišťování pomocí zjišťování různých verzí. Když vícesměrového vysílání UDP požadavek testu dorazí na proxy server, proxy server by měl odpovědět vícesměrovou zprávu. Pokud to chcete udělat, byste mít znát verze zjišťování požadavku.

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>K určení verze zjišťování zkušebního požadavku

V metodě, která bude reagovat na požadavek testu (například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) pomocí statické <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> vlastnost k vyhledání <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, jak je znázorněno v následujícím kódu.

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Implementace proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
