---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595411"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Postupy: Určení verze zjišťování zkušebního požadavku

Proxy zjišťování může vystavit několik koncových bodů zjišťování pomocí různých verzí zjišťování. Když požadavek na test vícesměrového vysílání UDP dorazí na proxy server, měl by proxy reagovat se zprávou o potlačení vícesměrového vysílání. Aby to bylo možné, museli byste znát verzi zjišťování žádosti.

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Určení verze zjišťování žádosti sondy

V metodě, která reaguje na požadavek sondy (například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ), použijte statickou <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> vlastnost k vyhledání a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , jak je znázorněno v následujícím kódu.

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [Implementace proxy zjišťování](implementing-a-discovery-proxy.md)
