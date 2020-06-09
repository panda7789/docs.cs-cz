---
title: Zabezpečení aplikací rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: a77449710e9093bc8ea2d5446e6359c26a3d1c1e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589874"
---
# <a name="securing-peer-channel-applications"></a>Zabezpečení aplikací rovnocenného kanálu
Podobně jako u jiných vazeb v rámci WinFX `NetPeerTcpBinding` má zabezpečení povoleno ve výchozím nastavení a nabízí jak zabezpečení založené na přenosu, tak i obojí. Toto téma pojednává o těchto dvou typech zabezpečení. Typ zabezpečení je určen příznakem režim zabezpečení ve specifikaci vazby ( <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A> `Mode` ).  
  
## <a name="transport-based-security"></a>Zabezpečení na základě přenosu  
 Partnerský kanál podporuje dva typy ověřovacích přihlašovacích údajů pro zabezpečení přenosů, které vyžadují nastavení `ClientCredentialSettings.Peer` vlastnosti u přidruženého `ChannelFactory` :  
  
- Heslo. Klienti používají k ověřování připojení znalosti tajného hesla. Když se použije tento typ přihlašovacích údajů, `ClientCredentialSettings.Peer.MeshPassword` musí mít platné heslo a volitelně taky `X509Certificate2` instanci.  
  
- Certifikát. Používá se konkrétní ověřování aplikace. Pokud se používá tento typ přihlašovacích údajů, musíte použít konkrétní implementaci <xref:System.IdentityModel.Selectors.X509CertificateValidator> v nástroji v `ClientCredentialSettings.Peer.PeerAuthentication` .  
  
## <a name="message-based-security"></a>Zabezpečení na základě zpráv  
 Pomocí zabezpečení zpráv může aplikace podepsat odchozí zprávy, aby všichni přijímající strany mohli ověřit, že je zpráva odeslána důvěryhodnou stranou a že zpráva nebyla zfalšována. V současné době podporuje partnerský kanál pouze podpis zprávy X. 509 přihlašovacích údajů.  
  
## <a name="best-practices"></a>Osvědčené postupy  
  
- Tato část popisuje osvědčené postupy pro zabezpečení aplikací v partnerském kanálu.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Povolení zabezpečení u aplikací s rovnocenným kanálem  
 Z důvodu distribuované povahy protokolů rovnocenného kanálu je obtížné vymáhat členství v síti, důvěrnost a ochranu osobních údajů v nezabezpečené síti. Je také důležité pamatovat na zabezpečení komunikace mezi klienty a službou překladače. V části protokol PNRP (Peer Name Resolution Protocol) Používejte zabezpečené názvy, abyste se vyhnuli falšování a dalším běžným útokům. Zabezpečte vlastní službu resolver tím, že povolíte zabezpečení pro klienty připojení, které se budou používat ke kontaktování služby překladače, včetně zabezpečení na základě zpráv a přenosů.  
  
### <a name="use-the-strongest-possible-security-model"></a>Použití nejsilnějšího možného modelu zabezpečení  
 Například pokud je nutné jednotlivě identifikovat jednotlivé členy sítě, použijte model ověřování založený na certifikátech. Pokud to není možné, použijte k zajištění zabezpečení ověřování na základě hesla podle aktuálních doporučení. To zahrnuje i hesla pro sdílení, a to jenom u důvěryhodných stran, odesílání hesel pomocí zabezpečeného média, často se měnící hesla a zajištění silného hesla (aspoň osm znaků), zahrňte aspoň jedno písmeno z obou případů, číslici a speciální znak.  
  
### <a name="never-accept-self-signed-certificates"></a>Nikdy nepřijímat certifikáty podepsané svým držitelem  
 Nikdy nepřijímejte přihlašovací údaje certifikátu na základě názvů subjektů. Mějte na paměti, že kdokoli může vytvořit certifikát a kdokoli může zvolit název, který ověřujete. Abyste se vyhnuli možnosti falšování identity, ověřte certifikáty na základě přihlašovacích údajů pro vydávající autoritu (buď důvěryhodného vystavitele nebo kořenové certifikační autority).  
  
### <a name="use-message-authentication"></a>Použít ověřování zpráv  
 Použijte ověřování zpráv k ověření, že zpráva pochází z důvěryhodného zdroje a že nikdo nepoškodil zprávu během přenosu. Bez ověřování zpráv je možné, že se zlými úmysly, kteří mají oprávnění k falšování nebo manipulaci se zprávami v síti, snadno poškodit.  
  
## <a name="peer-channel-code-examples"></a>Příklady kódu rovnocenného kanálu  
 [Scénáře rovnocenných kanálů](peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení protokolem Peer Channel](peer-channel-security.md)
- [Vytvoření aplikace protokolu Peer Channel](building-a-peer-channel-application.md)
