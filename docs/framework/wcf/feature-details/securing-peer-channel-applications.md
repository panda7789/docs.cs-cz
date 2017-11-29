---
title: "Zabezpečení aplikací rovnocenného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02bad6b5c7460655f4d3a5851e4e74d7de12111f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="securing-peer-channel-applications"></a>Zabezpečení aplikací rovnocenného kanálu
Jako další vazby v části [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` má povoleno ve výchozím nastavení zabezpečení a nabízí jak zabezpečení na základě přenosu a zprávy (nebo oba). Toto téma popisuje tyto dva typy zabezpečení. Typ zabezpečení je určen podle značky režimu bezpečnostní specifikací vazba (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Zabezpečení na základě přenosu  
 Rovnocenného kanálu podporuje dva typy ověřování přihlašovacích údajů pro zabezpečení přenosu, které vyžadují nastavení se `ClientCredentialSettings.Peer` vlastnost u přidruženého `ChannelFactory`:  
  
-   Heslo. Klienti používají znalosti tajné heslo k ověření připojení. Pokud se používá tento typ přihlašovacích údajů, `ClientCredentialSettings.Peer.MeshPassword` musí mít platné heslo a volitelně `X509Certificate2` instance.  
  
-   Certifikát. Slouží k ověřování konkrétní aplikace. Pokud tento typ přihlašovacích údajů se používá, je nutné použít konkrétní implementaci <xref:System.IdentityModel.Selectors.X509CertificateValidator> v `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Zabezpečení na základě zpráv  
 Pomocí zabezpečení zpráv, aplikace můžete přihlásit odchozích zpráv, tak, aby všechny přijímající strany můžete ověřit, že je zpráva odeslána důvěryhodná strana a není byla zpráva manipulováno. Rovnocenného kanálu v současné době podporuje pouze podepisování zpráv pověření X.509.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
-   Tato část popisuje doporučené postupy pro zabezpečení aplikací rovnocenného kanálu.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Povolit zabezpečení aplikací rovnocenného kanálu  
 Z důvodu distribuovaná povaha protokoly rovnocenného kanálu je obtížné vynutit OK členství, důvěrnost a ochrany osobních údajů v zabezpečená OK. Je také důležité pamatovat pro zabezpečení komunikace mezi klienty a překladač služby. V části řešení protokolu PNRP (Peer Name), použijte zabezpečené názvy vyhnout falšování identity a další běžné útoky. Zabezpečení služby vlastní překladač povolením zabezpečení připojení klienti použít ke kontaktování překladač služby, včetně zabezpečení i na základě zpráv a přenosu.  
  
### <a name="use-the-strongest-possible-security-model"></a>Použití modelu nejvyšší možné zabezpečení  
 Například pokud každý člen oka musí být určena jednotlivě, použijte ověřování pomocí certifikátů modelu. Pokud tento způsob není možný, použijte ověřování založené na heslech následující aktuální doporučení k jejich zabezpečení. To zahrnuje, sdílení hesel jenom s důvěryhodná strana, přenos hesel pomocí zabezpečené médium, změna hesel často a zajistíte, že hesla jsou silné (alespoň osm znaků dlouhé, zahrnuli aspoň jedno písmeno z obou případech číslici, a zvláštní znak).  
  
### <a name="never-accept-self-signed-certificates"></a>Nikdy přijmout certifikáty podepsané svým držitelem  
 Nikdy přijmout podle názvy předmětu certifikátu pověření. Upozorňujeme, že každý, kdo může vytvořit certifikát a každý, kdo může zvolte název, který se ověřování. Abyste se vyhnuli možnost falšování identity, ověřte certifikáty založené na vydání autority pověření (důvěryhodného vystavitele nebo certifikát kořenové certifikační autority).  
  
### <a name="use-message-authentication"></a>Ověřování zpráv  
 Ověřte, jestli zprávu pochází z důvěryhodného zdroje a zpráva nikdo má manipulováno během přenosu pomocí ověřování zpráv. Bez ověřování zpráv je snadné pro škodlivého klienta zfalšovat nebo manipulovat s zprávy v mřížce.  
  
## <a name="peer-channel-code-examples"></a>Příklady kódu rovnocenného kanálu  
 [Scénáře rovnocenných kanálů](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Vytvoření aplikace rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
