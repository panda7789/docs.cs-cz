---
title: "Postupy: testování zjišťování Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55a7fe72b34fc8c099d921e7e295c184817825a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-test-the-discovery-proxy"></a>Postupy: testování zjišťování Proxy
Toto je čtvrtý čtyři témata, která ukazuje, jak implementace zjišťování proxy. V předchozích tématu [postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), můžete implementovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientskou aplikaci, která používá zjišťování proxy k vyhledání služby a potom zavolá Služba. Toto téma popisuje postup ověření zjišťování proxy, služby a pracovní aplikace klienta podle očekávání.  
  
### <a name="run-the-discovery-proxy"></a>Spustit zjišťování Proxy  
  
1.  Otevřete příkazový řádek jako správce.  
  
2.  Mohou se zobrazit dialogové okno s upozorněním: brány Windows Firewall zablokovala některé funkce tohoto programu. Pokud se zobrazí tato zpráva, klikněte **Odblokovat** tlačítko.  
  
3.  V příkazovém řádku spusťte zjišťování proxy, DiscoveryProxy.exe.  
  
4.  Aplikace by měl zobrazit následující text: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Spusťte službu zjistitelný  
  
1.  Otevřete příkazový řádek jako správce.  
  
2.  V příkazovém řádku spusťte službu Service.exe zjistitelný.  
  
3.  DiscoveryProxy.exe by měl zobrazit následující text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Spustit klientskou aplikaci  
  
1.  Otevřete příkazový řádek.  
  
2.  V příkazovém řádku spusťte aplikaci client.exe.  
  
3.  Za několik sekund klientská aplikace zobrazí následující text: připojení k [koncový bod služby].  
  
4.  Service.exe pak by měl zobrazit následující text: s pozdravem přišel požadavek, I bude odpovídat.  
  
5.  Client.exe pak by měl zobrazit následující text: Hello klienta!  
  
### <a name="shut-down-the-applications"></a>Vypnout aplikace  
  
1.  Vypněte klientské aplikace.  
  
2.  Vypnutí služby. Zjišťování proxy zobrazí následující text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Vypněte zjišťování proxy.  
  
## <a name="see-also"></a>Viz také  
 [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Postupy: Implementace zjišťování Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Postupy: implementace zjistitelný služba, která zaregistruje se zjišťování Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [Postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
