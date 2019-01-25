---
title: 'Postupy: Test proxy zjišťování'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 3c159481813266386706b34d172bbf9614a8253d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590510"
---
# <a name="how-to-test-the-discovery-proxy"></a>Postupy: Test proxy zjišťování
Toto je čtvrtý čtyři témat, která ukazuje, jak implementace zjišťování proxy. V předchozím tématu [jak: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), jste implementovali WCF klientská aplikace, která používá proxy zjišťování k vyhledání služby a pak zavolá služba. Toto téma popisuje postup pro ověření proxy zjišťování, služby a pracovní aplikace klienta podle očekávání.  
  
### <a name="run-the-discovery-proxy"></a>Spustit zjišťování Proxy  
  
1.  Otevřete příkazový řádek jako správce.  
  
2.  Může se zobrazit dialogové okno s upozorněním: Brána Windows Firewall zablokovala některé funkce tohoto programu. Pokud se zobrazí tato zpráva, klikněte na tlačítko **Odblokovat** tlačítko.  
  
3.  V příkazovém řádku spusťte zjišťování proxy DiscoveryProxy.exe.  
  
4.  Aplikace by měly zobrazit následující text: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Spustit zjistitelné služby  
  
1.  Otevřete příkazový řádek jako správce.  
  
2.  V příkazovém řádku spusťte Service.exe zjistitelné služby.  
  
3.  DiscoveryProxy.exe by měly zobrazit následující text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Spuštění klientské aplikace  
  
1.  Otevřete příkazový řádek.  
  
2.  V příkazovém řádku spusťte client.exe aplikace.  
  
3.  Klientská aplikace po několik sekund zobrazí následující text: Připojení k [Service-Endpoint].  
  
4.  Service.exe by pak zobrazí následující text: Byla přijata žádost o pozdrav, můžu odpoví.  
  
5.  Client.exe by pak zobrazí následující text: Klient Hello!  
  
### <a name="shut-down-the-applications"></a>Ukončení aplikace  
  
1.  Vypněte klientské aplikace.  
  
2.  Vypnutí služby. Proxy zjišťování se zobrazí následující text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Vypněte proxy zjišťování.  
  
## <a name="see-also"></a>Viz také:
- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Postupy: Implementace Proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [Postupy: Implementace zjistitelné služby, která se registruje pomocí Proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
