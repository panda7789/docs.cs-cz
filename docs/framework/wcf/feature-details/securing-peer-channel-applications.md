---
title: Zabezpečení aplikací rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: a747923f81f4773eb58a4b7500cf4fc1c006f889
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146238"
---
# <a name="securing-peer-channel-applications"></a>Zabezpečení aplikací rovnocenného kanálu
Jako v jiných vazbách [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` má povolené ve výchozím nastavení zabezpečení a nabízí i zabezpečení na základě přenosu a zprávy (nebo obojí). Toto téma popisuje tyto dva typy zabezpečení. Typ zabezpečení je určen podle klíčových slov režim zabezpečení ve specifikaci vazby (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Zabezpečení přenosu  
 Protokolu peer Channel podporuje dva typy ověřování pověření zabezpečení přenosu. oba vyžadují nastavení si `ClientCredentialSettings.Peer` vlastnosti přidruženého `ChannelFactory`:  
  
-   Heslo. Klienti používají znalost tajného kódu hesla pro ověření připojení. Když se používá tento typ přihlašovacích údajů, `ClientCredentialSettings.Peer.MeshPassword` musí mít platné heslo a volitelně `X509Certificate2` instance.  
  
-   certifikát. Slouží k ověřování konkrétní aplikace. Pokud tento typ přihlašovacích údajů se používá, je nutné použít konkrétní implementaci <xref:System.IdentityModel.Selectors.X509CertificateValidator> v `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Zabezpečení na základě zpráv  
 Pomocí zabezpečení zpráv, aplikaci mohl odchozí zprávy tak, aby všechny přijímající strany můžete ověřit, že je zpráva odeslána důvěryhodná strana a zpráva nebyla manipulováno. V současné době protokolu Peer Channel podporuje pouze podepisování zpráv přihlašovacích údajů X.509.  
  
## <a name="best-practices"></a>Doporučené postupy  
  
-   Tato část popisuje osvědčené postupy pro zabezpečení aplikací rovnocenného kanálu.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Povolit zabezpečení aplikací protokolu Peer Channel  
 Z důvodu distribuovaná povaha protokoly protokolu Peer Channel je obtížné vynucovat síť členství, důvěrnost a ochrana osobních údajů v nezabezpečené síti. Taky je dobré si uvědomit pro zabezpečení komunikace mezi klienty a službě překládání. V části překlad protokolu PNRP (Peer Name), použijte zabezpečené názvů, které se vyhnout falšování identity a dalších běžných útoků. Zabezpečení služby vlastní mechanismus rozpoznávání tím, že zabezpečení týkající se použití připojení klientů ke kontaktování službě překládání, včetně zabezpečení na základě zpráv a přenosu i.  
  
### <a name="use-the-strongest-possible-security-model"></a>Použití modelu nejsilnější možné zabezpečení  
 Například pokud každý člen síť musí být určena jednotlivě, použijte ověřování na základě modelu. Pokud tento způsob není možný, zajistěte jejich zabezpečení pomocí následujících doporučení pro aktuální ověřování pomocí hesla. Jedná se o sdílení hesel pouze s považujete za důvěryhodné, přenášení hesel pomocí zabezpečené médium hesla často mění a zajistit správnost silných hesel (alespoň osm znaků dlouhé, zahrňte v obou případech platí, číslice, alespoň jedno písmeno a speciální znak).  
  
### <a name="never-accept-self-signed-certificates"></a>Nikdy přijmout certifikáty podepsané svým držitelem  
 Nikdy přijmout certifikát přihlašovacích údajů podle názvů předmětu. Všimněte si, že kdokoli může vytvořit certifikát a kdokoli zvolte název, který se ověřuje. Abyste předešli falšování, ověřte certifikáty založené na vydání autority pověření (důvěryhodného vystavitele nebo kořenové certifikační autority).  
  
### <a name="use-message-authentication"></a>Použít ověřování zpráv  
 Ověřte, že zpráva pochází z důvěryhodného zdroje a že nikdo nemanipuloval s touto zprávou během přenosu pomocí ověřování zpráv. Bez ověřování zpráv je to jednoduché škodlivého klienta zfalšovat nebo manipulovat se zprávy v mřížce.  
  
## <a name="peer-channel-code-examples"></a>Příklady kódu pro protokolu peer Channel  
 [Scénáře protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení protokolem Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
