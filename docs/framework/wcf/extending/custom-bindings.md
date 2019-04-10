---
title: Vlastní vazby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 314409f5ac4ecb4b18f3b8d3f2aeb08a507ec9e9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207263"
---
# <a name="custom-bindings"></a>Vlastní vazby
Můžete použít <xref:System.ServiceModel.Channels.CustomBinding> třídy, pokud jedna z vazeb poskytovaných systémem nesplňuje požadavky na vaši službu. Všechny vazby jsou konstruovány ze seřazené sady elementů vazby. Vlastní vazby se dají ze sady prvků vazeb poskytovaných systémem nebo může obsahovat elementy uživatelem definované vlastní vazby. Můžete použít vlastní vazby prvky, například umožní použít nové přenosy nebo kodérů na koncový bod služby. Příklady práce, naleznete v tématu [vlastní vazby ukázky](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Další informace najdete v tématu [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Vytvoření vlastní vazby  
 Vlastní vazby je vytvořený <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktoru z kolekce vazby prvky, které jsou "skládaný" v určitém pořadí:  
  
-   V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> třídu, která umožňuje toku transakce.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> třída, která poskytuje relaci a jak je definováno ve specifikaci WS-ReliableMessaging řazení mechanismy. Relaci můžete různé zprostředkovatele protokolu SOAP a přenosu.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.SecurityBindingElement> třída, která poskytuje funkce zabezpečení, jako je například autorizace, ověřování, ochrany a zachováním důvěrnosti.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> třídu, která umožňuje mít dva stejně, jako duplexní komunikaci s přenosový protokol, který nepodporuje duplexní komunikaci nativně, jako je například HTTP.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.OneWayBindingElement>) třída, která poskytuje jednosměrnou komunikaci.  
  
-   Dále je element vazby zabezpečení volitelné datového proudu, který může být jedna z následujících akcí.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Dále je element vazby kódování zprávy vyžaduje. Můžete použít vlastní kodér zpráv nebo jeden ze tří vazby kódování zprávy:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 V dolní části je prvek vyžaduje přenos. Můžete použít vlastní přenos nebo jednu z následujících elementů přenosové vazby, kterou poskytuje Windows Communication Foundation (WCF):  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 Následující tabulka shrnuje možnosti pro každou vrstvu.  
  
|Vrstva|Možnosti|Požadováno|  
|-----------|-------------|--------------|  
|Transakce|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Ne|  
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Ne|  
|Kódování|Text, vlastní binární soubor, zpráv přenosu optimalizace mechanismus (MTOM),|Ano|  
|Přenos|TCP, HTTP, HTTPS, pojmenované kanály (označované také jako IPC) Peer-to-Peer (P2P), služba Řízení front zpráv (MSMQ), vlastní|Ano|  
  
 Kromě toho můžete definovat vlastní elementy vazby a vložit mezi všechny předchozí definované vrstvy.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Postupy: Přizpůsobení vazeb poskytovaných systémem](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Vlastní vazba](../../../../docs/framework/wcf/samples/custom-binding.md)
