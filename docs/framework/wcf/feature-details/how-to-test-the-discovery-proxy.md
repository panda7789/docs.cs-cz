---
title: 'Postupy: Test proxy zjišťování'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 78921d0a26f1116c87c2931b1472a161d6fed145
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592811"
---
# <a name="how-to-test-the-discovery-proxy"></a>Postupy: Test proxy zjišťování
Toto je čtvrtá část čtyř témat, která ukazuje, jak implementovat proxy zjišťování. V předchozím tématu [Postupy: implementace klientské aplikace, která používá proxy zjišťování k vyhledání služby](client-app-discovery-proxy-to-find-a-service.md), jste implementovali klientskou aplikaci WCF, která používá proxy zjišťování k vyhledání služby a následné volání služby. Toto téma popisuje, jak ověřit proxy zjišťování, službu a klientská aplikace fungují podle očekávání.  
  
### <a name="run-the-discovery-proxy"></a>Spustit proxy zjišťování  
  
1. Otevřete příkazový řádek jako správce.  
  
2. Může se zobrazit dialogové okno s upozorněním, že brána Windows Firewall zablokovala některé funkce tohoto programu. Pokud se zobrazí tato zpráva, klikněte na tlačítko **odblokovat** .  
  
3. V příkazovém řádku spusťte proxy zjišťování objektu DiscoveryProxy. exe.  
  
4. Aplikace by měla zobrazit následující text: `Proxy started. Hit Enter to exit` .  
  
### <a name="run-the-discoverable-service"></a>Spuštění zjistitelné služby  
  
1. Otevřete příkazový řádek jako správce.  
  
2. V příkazovém řádku spusťte zjistitelnou službu Service. exe.  
  
3. Objektu DiscoveryProxy. exe by měl zobrazit následující text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Spuštění klientské aplikace  
  
1. Otevřete příkazový řádek.  
  
2. V příkazovém řádku spusťte aplikaci Client. exe.  
  
3. Po několika sekundách se klientská aplikace zobrazí následující text: připojení ke službě [Service-Endpoint].  
  
4. V souboru Service. exe by se pak měl zobrazit následující text: přijatý požadavek na pozdrav, který reaguje.  
  
5. Soubor Client. exe by pak měl zobrazovat následující text: Hello Client!  
  
### <a name="shut-down-the-applications"></a>Vypnutí aplikací  
  
1. Ukončete klientskou aplikaci.  
  
2. Ukončete službu. Proxy zjišťování zobrazí následující text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .  
  
3. Vypněte proxy zjišťování.  
  
## <a name="see-also"></a>Viz také

- [Přehled zjišťování WCF](wcf-discovery-overview.md)
- [Postupy: Implementace zjišťování proxy](how-to-implement-a-discovery-proxy.md)
- [Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby](client-app-discovery-proxy-to-find-a-service.md)
