---
title: Překladače partnerských uzlů
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: a1f5bcfb721ccbc98856e81198a3f7e0b45abe93
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600773"
---
# <a name="peer-resolvers"></a>Překladače partnerských uzlů
Aby bylo možné se připojit k síti, partnerský uzel vyžaduje IP adresy jiných uzlů. IP adresy se získávají kontaktováním služby překladače, která přijímá ID sítě a vrací seznam adres odpovídajících uzlům zaregistrovaným s tímto ID sítě. Překladač uchovává seznam registrovaných adres, které vytvoří tak, že se všechny uzly v síti registrují spolu se službou.  
  
 Můžete určit, která služba PeerResolver se má použít, pomocí `Resolver` vlastnosti <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
## <a name="supported-peer-resolvers"></a>Podporované překladače rovnocenných zařízení  
 Partnerský kanál podporuje dva typy překladačů: protokol PNRP (Peer Name Resolution Protocol) a vlastní služby překladače.  
  
 Ve výchozím nastavení používá rovnocenný kanál službu překladače PNRP peering pro zjišťování partnerských vztahů a sousedů v síti. V situacích a platformách, kde PNRP není k dispozici nebo je možné, Windows Communication Foundation (WCF) poskytuje alternativní službu zjišťování na základě serverů – <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> . Můžete také explicitně definovat vlastní službu překladače, a to tak, že zapíšete třídu, která implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokol PNRP (Peer Name Resolution Protocol)  
 Protokol PNRP je výchozím překladačem pro systém Windows Vista distribuovaná služba pro překládání názvů bez serveru. Protokol PNRP lze také použít v systému Windows XP SP2 instalací pokročilého síťového balíčku. Každý ze dvou klientů, na kterých běží stejná verze PNRP, může každý jiný tento protokol najít za předpokladu, že splňují určité podmínky (například nedostatek používané podnikové brány firewall). Všimněte si, že verze PNRP, která je dodávána s Windows Vista, je novější než verze zahrnutá v sadě Advanced Networking Pack. Aktualizace protokolu PNRP pro systém Windows XP SP2 najdete na webu služby Stažení softwaru společnosti Microsoft.  
  
### <a name="custom-resolver-services"></a>Vlastní služby překladače  
 Pokud není Služba PNRP k dispozici nebo chcete plnou kontrolu nad mřížkou, můžete použít vlastní službu překladače založené na serveru. Tuto službu můžete explicitně definovat tak, že napíšete třídu překladače implementující <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> rozhraní nebo pomocí integrované výchozí implementace <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> .  
  
 V rámci výchozí implementace služby vyprší platnost registrace klientů po určitém časovém limitu, pokud klient explicitně neaktualizuje registraci. Klienti, kteří používají službu překladače, musí znát horní mez při latenci klienta a serveru, aby bylo možné úspěšně aktualizovat registrace v čase. To zahrnuje výběr vhodného časového limitu aktualizace ( `RefreshInterval` ) ve službě překladače. (Další informace najdete v tématu [CustomPeerResolverService: registrace klienta](inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Zapisovač aplikace musí také zvážit zabezpečení spojení mezi klienty a vlastní službou překladače. To můžete provést pomocí nastavení zabezpečení na <xref:System.ServiceModel.NetTcpBinding> klientech, kteří používají ke kontaktování služby překladače. Je nutné zadat přihlašovací údaje (Pokud se používají) na základě `ChannelFactory` použitého k vytvoření rovnocenného kanálu. Tyto přihlašovací údaje jsou předány k `ChannelFactory` použití k vytvoření kanálů pro vlastní překladač.  
  
> [!NOTE]
> Pokud používáte místní a Impromptu sítě s vlastním překladačem, důrazně se doporučuje, aby aplikace využívající nebo podporovaly místní nebo Impromptu sítě zahrnovaly logiku, která při připojování vybere jednu místní adresu propojení. Zabráníte tak případné záměně, které by mohly být způsobeny počítači s více adresami místních odkazů. V souladu s tímto kanálem peer Channel podporuje v jednom okamžiku jenom použití jediné místní adresy. Tuto adresu můžete zadat s `ListenIpAddress` vlastností na <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
 Ukázku implementace vlastního překladače najdete v tématu [překladač peer Channel Custom peer resolver](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Uvnitř CustomPeerResolverService: registrace klienta](inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Viz také

- [Koncepce protokolu Peer Channel](peer-channel-concepts.md)
- [Zabezpečení protokolem Peer Channel](peer-channel-security.md)
- [Vytvoření aplikace protokolu Peer Channel](building-a-peer-channel-application.md)
