---
title: <security> z <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936630"
---
# <a name="security-of-netpeerbinding"></a>\<> zabezpečení > \<netPeerBinding
Definuje nastavení [ \<zabezpečení NetPeerTcpBinding >](netpeertcpbinding.md), včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.  
  
 \<system.ServiceModel>  
\<> vazeb  
\<netPeerBinding>  
\<> vazby  
\<> zabezpečení  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelný parametr. Určuje typ zabezpečení, který používají partneři nakonfigurované s touto vazbou. Výchozí hodnota je `Message`. Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Message|Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.|  
|Žádné|Zabezpečení je zakázané.|  
|Přepravu|Zabezpečení je k dispozici pomocí protokolu HTTPS.|  
|TransportWithMessageCredential|Protokol HTTPS zajišťuje ověřování a důvěrnost. Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> přenosu](transport-of-netpeertcpbinding.md)|Definuje typ přenosu pro zabezpečené zprávy odesílané partnerskými uzly nakonfigurovanými pomocí této vazby. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazby](../../../misc/binding.md)|Definuje všechny schopnosti [ \<vazby NetPeerTcpBinding >](netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečení může být specifické pro zprávy nebo pro přenos.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
