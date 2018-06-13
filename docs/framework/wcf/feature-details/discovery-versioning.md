---
title: Správa verzí zjišťování
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 18c160e5e08ed9b6733bed9d5e40a4dde00dfd1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489177"
---
# <a name="discovery-versioning"></a>Správa verzí zjišťování
Toto téma obsahuje stručný přehled implementace některé nové funkce zjišťování. Také nabízí přehled o tom, jak vybrat zjišťování verze se má použít.  
  
## <a name="discovery-versioning"></a>Správa verzí zjišťování  
 Funkci zjišťování zahrnuje podporu pro tři verze WS_Discovery protokolu. Zjišťování rozhraní API lze vybrat možnost, která verze protokolu, kterou chcete použít. Tento dokument stručně popisuje nastavení týkající se správy verzí.  
  
 Následující třídy zjišťování teď mají <xref:System.ServiceModel.Discovery.DiscoveryVersion> vlastnost a proveďte <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument v jejich konstruktory:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005  
 Poskytnutí <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako konstruktor parametr díky implementace použít April2005 verze protokolu WS-Discovery. Tato verze odpovídá na publikovanou verzi specifikace protokolu WS-Discovery. Tato verze by měl používat pro spolupráci s využitím April2005 verzi WS-Discovery starší verzi aplikace.  
  
### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11  
 Výchozí verze zjišťování používá rozhraní API je <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Toto je aktuální standardizované verzi protokolu WS-Discovery.  
  
## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1  
 Poskytnutí <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jako parametr konstruktoru vytvoří implementace použít výbor koncept 1 verze protokolu WS-Discovery. Tato verze protokolu by měl používat pro spolupráci s implementací č.1 verze protokolu WS-Discovery.  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Podpora víc koncových bodů UDP zjišťování pro zjišťování různé verze na hostiteli jedné služby  
 Chcete vystavit několik koncových bodů UDP zjišťování pro zjišťování různé verze na hostiteli jedné služby. K tomu musíte zadat adresu jedinečný pro každý koncový bod zjišťování UDP. Následující příklad ukazuje, jak to provést.  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
