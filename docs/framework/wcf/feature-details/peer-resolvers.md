---
title: "Překladače partnerských uzlů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79c26ca9e167455dfbd664ea96e574c130cdc3d2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="peer-resolvers"></a>Překladače partnerských uzlů
Aby bylo možné připojit k mřížku, vyžaduje uzlem sdílené IP adresy dalších uzlů. IP adresy jsou získány kontaktováním překladač služby, která přebírá ID OK a vrátí seznam adres odpovídající do uzlů, které jsou registrovány ID tohoto konkrétního OK. Překladač udržuje seznam registrovaných adresy, které vytvoří tak, že každý uzel v mřížce zaregistrovat službu.  
  
 Můžete zadat služby, která PeerResolver používat prostřednictvím `Resolver` vlastnost <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Překladače podporované partnerských uzlů  
 Rovnocenného kanálu podporuje dva typy překladače: řešení protokolu PNRP (Peer Name) a vlastní překladač služby.  
  
 Ve výchozím nastavení používá rovnocenného kanálu službu PNRP peer překladač pro zjišťování partnerské uzly a okolí v mřížce. Pro situacích nebo platformy, kde PNRP není k dispozici nebo je to vhodné [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje služby alternativní, na serveru zjišťování - <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Můžete také explicitně definovat vlastní překladač služby napsáním třídu, která implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokol PNRP (PNRP)  
 PNRP, výchozí překladač pro [!INCLUDE[wv](../../../../includes/wv-md.md)], je služba překladač distribuované, bez serveru. PNRP lze také na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] nainstalováním Advanced Networking Pack. Jakékoli dvě se stejnou verzí PNRP mohou klienti vyhledat navzájem pomocí tohoto protokolu, pokud splňují určité podmínky (třeba nedostatek použitá podniková brána firewall). Všimněte si, že verze PNRP dodává s [!INCLUDE[wv](../../../../includes/wv-md.md)] je novější než verze zahrnuté do balíčku Advanced sítě. Zkontrolujte webu Microsoft Download Center aktualizace PNRP pro [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Vlastní překladač služby  
 Když PNRP služba není dostupná, nebo chcete plnou kontrolu nad shaping mřížky, můžete službu překladač vlastní, na serveru. Tuto službu můžete definovat explicitně napsáním třídu překladač implementace <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní nebo pomocí integrované výchozí implementace, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 V části výchozí implementace služby vyprší registrace klienta po určitou dobu, pokud klient neaktualizuje explicitně registrace. Klienti, kteří používají službu překladač musí mít přehled o horní mez na latenci klient server Chcete-li úspěšně aktualizovat registrace v čase. To zahrnuje výběr příslušné aktualizace časový limit (`RefreshInterval`) ve službě překladač. (Další informace najdete v tématu [uvnitř CustomPeerResolverService: registrace klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Zapisovač aplikace musíte taky zvážit zabezpečení připojení mezi klienty a službou vlastní překladač. Může to provést pomocí nastavení zabezpečení na <xref:System.ServiceModel.NetTcpBinding> že budou klienti používat kontaktovat službu překladač. Je třeba zadat přihlašovací údaje (Pokud se používá) na `ChannelFactory` použít k vytvoření rovnocenného kanálu. Tyto přihlašovací údaje jsou předány `ChannelFactory` použít k vytvoření kanálů pro vlastní překladač.  
  
> [!NOTE]
>  Pokud používáte místní a režimu sítí s vlastní překladač, se důrazně doporučuje, aby aplikace pomocí nebo podpora propojení nebo režimu sítě patří třeba logiky, která vybere jedna adresa specifická pro připojení použít při připojení. Tím se zabrání nepochopení potenciálně způsobené počítače s více adresami specifická pro připojení. V souladu s tím rovnocenného kanálu podporuje pouze pomocí jedné adresy specifická pro připojení v daném okamžiku. Můžete určit tato adresa se `ListenIpAddress` vlastnost <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Ukázka, jak implementovat vlastní překladač, najdete v části [kanál uživatelského sdílené synchronního](http://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Uvnitř CustomPeerResolverService: registrace klientů](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Zabezpečení protokolem Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
