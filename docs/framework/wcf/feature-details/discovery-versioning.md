---
title: Správa verzí zjišťování
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 4a1ca07fc6773ce6f883d654abfedab4986341e1
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425257"
---
# <a name="discovery-versioning"></a>Správa verzí zjišťování

Toto téma nabízí stručný přehled o implementaci některé nové funkce zjišťování. Poskytuje také přehled o tom, jak vybrat zjišťování verze se má použít.

## <a name="discovery-versioning"></a>Správa verzí zjišťování

Funkce zjišťování zahrnuje podporu pro tři verze WS_Discovery protokolu. Zjišťování rozhraní API umožňuje zvolit, kterou verzi protokolu, kterou chcete použít. Tento dokument stručně popisuje nastavení týkající se správy verzí.

Teď máte následující třídy pro zjišťování <xref:System.ServiceModel.Discovery.DiscoveryVersion> vlastnost a zkuste <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument v jejich konstruktory:

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005

Poskytuje <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako konstruktor parametr provádí implementace použít April2005 verzi protokolu WS-Discovery. Tato verze odpovídá na publikovanou verzi specifikace protokolu WS-Discovery. Tato verze by měla sloužit pro spolupráci s využitím April2005 verzi WS-Discovery starší verzi aplikace.

### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11

Výchozí verze zjišťování používá rozhraní API je <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Toto je aktuální standardizované verzi protokolu WS-Discovery.

## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1

Poskytuje <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jako parametr konstruktoru učiní implementace použít koncept výboru 1 verzi protokolu WS-Discovery. Tato verze protokolu by měl používat pro spolupráci s implementací č.1 verzi protokolu WS-Discovery.

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Podpora více koncových bodů UDP zjišťování pro zjišťování různé verze v jedné službě hostiteli

Můžete chtít vystavit několik koncových bodů UDP zjišťování pro zjišťování různé verze na hostiteli jedinou službou. K tomu musíte zadat adresu jedinečný pro každý koncový bod zjišťování UDP. Následující příklad ukazuje, jak to provést.

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
