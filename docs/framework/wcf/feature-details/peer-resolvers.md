---
title: Překladače partnerských uzlů
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 0547bb37b03235c61f43cec365551438f7931ad1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909917"
---
# <a name="peer-resolvers"></a>Překladače partnerských uzlů
Aby bylo možné se připojit k síti, partnerský uzel vyžaduje IP adresy jiných uzlů. IP adresy se získávají kontaktováním služby překladače, která přijímá ID sítě a vrací seznam adres odpovídajících uzlům zaregistrovaným s tímto ID sítě. Překladač uchovává seznam registrovaných adres, které vytvoří tak, že se všechny uzly v síti registrují spolu se službou.  
  
 Můžete určit, která služba PeerResolver se má použít `Resolver` , pomocí vlastnosti. <xref:System.ServiceModel.NetPeerTcpBinding>  
  
## <a name="supported-peer-resolvers"></a>Podporované překladače rovnocenných zařízení  
 Partnerský kanál podporuje dva typy překladačů: Protokol PNRP (Peer Name Resolution Protocol) a vlastní služby překladače.  
  
 Ve výchozím nastavení používá rovnocenný kanál službu překladače PNRP peering pro zjišťování partnerských vztahů a sousedů v síti. V <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>situacích a platformách, kde PNRP není k dispozici nebo je možné, Windows Communication Foundation (WCF) poskytuje alternativní službu zjišťování na základě serverů –. Můžete také explicitně definovat vlastní službu překladače, a to tak, že zapíšete třídu, která implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokol PNRP (Peer Name Resolution Protocol)  
 Protokol PNRP je výchozím překladačem [!INCLUDE[wv](../../../../includes/wv-md.md)]pro, který je distribuovaná služba pro překládání názvů bez serveru. Protokol PNRP se dá použít taky [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] v případě, že nainstalujete pokročilou síťovou sadu. Každý ze dvou klientů, na kterých běží stejná verze PNRP, může každý jiný tento protokol najít za předpokladu, že splňují určité podmínky (například nedostatek používané podnikové brány firewall). Všimněte si, že verze protokolu PNRP, která [!INCLUDE[wv](../../../../includes/wv-md.md)] je dodávána, je novější než verze obsažená v sadě Advanced Networking Pack. Informace o aktualizacích PNRP pro [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]najdete na webu Microsoft Download Center.  
  
### <a name="custom-resolver-services"></a>Vlastní služby překladače  
 Pokud není Služba PNRP k dispozici nebo chcete plnou kontrolu nad mřížkou, můžete použít vlastní službu překladače založené na serveru. Tuto službu můžete explicitně definovat tak, že napíšete třídu překladače implementující <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní nebo pomocí integrované výchozí <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>implementace.  
  
 V rámci výchozí implementace služby vyprší platnost registrace klientů po určitém časovém limitu, pokud klient explicitně neaktualizuje registraci. Klienti, kteří používají službu překladače, musí znát horní mez při latenci klienta a serveru, aby bylo možné úspěšně aktualizovat registrace v čase. To zahrnuje výběr vhodného časového limitu aktualizace (`RefreshInterval`) ve službě překladače. (Další informace najdete v tématu [CustomPeerResolverService: Registrace](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)klienta.)  
  
 Zapisovač aplikace musí také zvážit zabezpečení spojení mezi klienty a vlastní službou překladače. To můžete provést pomocí nastavení zabezpečení na <xref:System.ServiceModel.NetTcpBinding> klientech, kteří používají ke kontaktování služby překladače. Je nutné zadat přihlašovací údaje (Pokud se `ChannelFactory` používají) na základě použitého k vytvoření rovnocenného kanálu. Tyto přihlašovací údaje jsou předány `ChannelFactory` k použití k vytvoření kanálů pro vlastní překladač.  
  
> [!NOTE]
> Pokud používáte místní a Impromptu sítě s vlastním překladačem, důrazně se doporučuje, aby aplikace využívající nebo podporovaly místní nebo Impromptu sítě zahrnovaly logiku, která při připojování vybere jednu místní adresu propojení. Zabráníte tak případné záměně, které by mohly být způsobeny počítači s více adresami místních odkazů. V souladu s tímto kanálem peer Channel podporuje v jednom okamžiku jenom použití jediné místní adresy. Tuto adresu můžete zadat s `ListenIpAddress` vlastností <xref:System.ServiceModel.NetPeerTcpBinding>na.  
  
 Ukázku implementace vlastního překladače najdete v tématu [překladač peer Channel Custom peer resolver](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Uvnitř CustomPeerResolverService: Registrace klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Viz také:

- [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Zabezpečení protokolem Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
