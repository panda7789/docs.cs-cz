---
title: "Vlastní vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d51e6e5b72deea417b7313d88a4d58610b401244
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-bindings"></a>Vlastní vazby
Můžete použít <xref:System.ServiceModel.Channels.CustomBinding> třídy, pokud jeden z vazby poskytované systémem nesplňuje požadavky na služby. Všechny vazby se vytvářejí na základě uspořádanou sadu elementů vazby. Vlastní vazby jde integrovat přímo ze sady elementů vazby poskytované systémem nebo může zahrnovat prvky uživatelem definované vlastní vazby. Vlastní vazby elementů, například můžete použít k povolení použití nové přenosy nebo kodéry na koncový bod služby. Pracovní příklady najdete v tématu [vazby ukázky vlastních](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Vytváření vlastních vazeb  
 Vlastní vazby je vytvořený pomocí <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktor z kolekce elementů, které jsou "skládaný" v určitém pořadí vazby:  
  
-   V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> třídu, která umožňuje toku transakcí.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> třídu, která poskytuje relaci a jak jsou definovány ve specifikaci WS-ReliableMessaging řazení mechanismy. Relaci můžete křížová zprostředkovatele protokolu SOAP a přenosu.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.SecurityBindingElement> třídu, která poskytuje funkce zabezpečení, jako je například autorizace, ověřování, ochrana a důvěrnost.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> třídu, která umožňuje mít dva způsobem duplexní komunikace s transportní protokol, který nepodporuje duplexní komunikace nativně, jako je například HTTP.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.OneWayBindingElement>) třídu, která poskytuje jednosměrnou komunikaci.  
  
-   Další je na prvek vazby zabezpečení volitelné datový proud, který může být jedna z následujících.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Dále je požadované zpráva kódování prvku vazby. Můžete použít vlastní kodér zpráv nebo jeden z tři vazby kódování zprávy:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 V dolní části je element požadované přenosu. Můžete použít vlastní přenos nebo jeden z následujících elementů přenosové vazby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje:  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 Následující tabulka shrnuje možnosti pro jednotlivé úrovně.  
  
|Vrstva|Možnosti|Požadováno|  
|-----------|-------------|--------------|  
|Transakce|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Ne|  
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Ne|  
|Kódování|Text, vlastní binární zpráva přenosu optimalizace mechanismus (MTOM),|Ano|  
|Přenos|TCP, HTTP, HTTPS, pojmenované kanály (také označované jako IPC), Peer-to-Peer (P2P), služba Řízení front zpráv (MSMQ), vlastní|Ano|  
  
 Kromě toho můžete definovat vlastní prvky vazby a vložte je mezi některé z předchozích definované vrstvy.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Postupy: Přizpůsobení vazeb poskytovaných systémem](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Vlastní vazba](../../../../docs/framework/wcf/samples/custom-binding.md)
