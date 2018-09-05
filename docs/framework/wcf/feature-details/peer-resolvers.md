---
title: Překladače partnerských uzlů
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 01320d98953c8fdc057aeec840ace4b818fcf115
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43670594"
---
# <a name="peer-resolvers"></a>Překladače partnerských uzlů
Aby bylo možné připojit k sítě, vyžaduje partnerský uzel IP adresy z ostatních uzlů. Získávají se IP adresy kontaktováním překladač služby, která přijímá ID sítě a vrátí seznam hodnot adresy odpovídající uzly zaregistrovaný s ID tohoto konkrétního sítě. Překladač udržuje seznam registrovaných adresy, které se vytvoří tak, že každý uzel v mřížce zaregistrovat do služby.  
  
 Můžete určit, které služby PeerResolver prostřednictvím `Resolver` vlastnost <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Překladače podporované partnerských uzlů  
 Protokolu peer Channel podporuje dva typy překladače: překlad protokolu PNRP (Peer Name) a vlastní mechanismus rozpoznávání služeb.  
  
 Ve výchozím nastavení používá protokolu Peer Channel služba překladač PNRP peer pro zjišťování partnerské uzly a okolí v mřížce. Pro situace/platformy, kde PNRP není k dispozici nebo není vhodná, Windows Communication Foundation (WCF) poskytuje službu zjišťování alternativní, serverových - <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Můžete také explicitně definovat vlastní mechanismus rozpoznávání služby napsáním třídu, která implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokol PNRP (PNRP)  
 Protokol PNRP, výchozí překladač pro [!INCLUDE[wv](../../../../includes/wv-md.md)], je služba překladač distribuované, bez serveru. Protokol PNRP lze také na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] nainstalováním sady rozšířeného sítě. Žádné dva se stejnou verzí PNRP mohli klienti najít navzájem pomocí tohoto protokolu, pokud splňují určité podmínky (například chybějící použitá podniková brána firewall). Všimněte si, že verze PNRP, který je součástí [!INCLUDE[wv](../../../../includes/wv-md.md)] je novější než verze součástí balíčku rozšířeného sítě. Zkontrolujte webu Microsoft Download Center aktualizace PNRP pro [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Vlastní mechanismus rozpoznávání služeb  
 Když Služba PNRP není k dispozici, nebo chcete úplnou kontrolu nad tvarování sítě, můžete použít vlastní, serverových překladač služby. Tuto službu můžete definovat explicitně napsáním překladač třída implementace <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní nebo pomocí integrované výchozí implementace <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 Pod výchozí implementace služby registrace klienta vyprší po určitou dobu Pokud klient neaktualizuje explicitně registrace. Klienti, kteří používají službě překládání musí mít přehled o horní mez na latenci klient server aby bylo možné úspěšně obnovit registrace v čase. To znamená příslušnou aktualizaci časového limitu (`RefreshInterval`) ve službě překládání. (Další informace najdete v tématu [uvnitř CustomPeerResolverService: registrace klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Zapisovač aplikace musíte taky zvážit zabezpečení připojení mezi klienty a službě vlastní překládání. Může to provést pomocí nastavení zabezpečení na <xref:System.ServiceModel.NetTcpBinding> , že klienti používají navázání kontaktu se službou překladač. Je nutné zadat přihlašovací údaje (Pokud se používá) na `ChannelFactory` použitý k vytvoření protokolu Peer Channel. Tyto přihlašovací údaje jsou předány `ChannelFactory` použitý k vytvoření kanálů pro vlastní překládání.  
  
> [!NOTE]
>  Pokud používáte vlastní mechanismus rozpoznávání neocenitelní a místní sítí, se důrazně doporučuje, že aplikace používá nebo specifická pro připojení nebo neocenitelní sítě obsahují logiku, která vybere jedna adresa specifická pro připojení používat při připojování. To zabraňuje záměny potenciálně způsobené počítače s více adresami specifická pro připojení. V souladu s touto protokolu Peer Channel podporuje pouze pomocí jedné adresy specifická pro připojení v daný okamžik. Můžete zadat tuto adresu se `ListenIpAddress` vlastnost <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Ukázku toho, jak implementovat vlastní mechanismus rozpoznávání, naleznete v tématu [Peer Channel vlastní rozpoznávání partnera](https://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Uvnitř CustomPeerResolverService: registrace klientů](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Zabezpečení protokolem Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
