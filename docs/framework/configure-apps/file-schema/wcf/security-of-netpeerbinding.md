---
title: <security> of <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 6348bc6f6c0d3a9656fbe57bf71f531d1287a949
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170089"
---
# <a name="security-of-netpeerbinding"></a>\<zabezpečení > z \<netPeerBinding >
Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), včetně typ ověřování, který používá a zabezpečení pro přenos zpráv.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netPeerBinding>  
\<Vytvoření vazby >  
\<security>  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelné. Určuje typ zabezpečení používané partnerské uzly, které jsou konfigurovány pomocí této vazby. Výchozí hodnota je `Message`. Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Zpráva|Zabezpečení protokolu SOAP poskytuje ověřování, integritu a důvěrnost.|  
|Žádné|Zabezpečení je zakázaná.|  
|Přenos|Zabezpečení je k dispozici pomocí protokolu HTTPS.|  
|TransportWithMessageCredential|HTTPS zajišťuje ověřování a zachováním důvěrnosti. Zprávy protokolu SOAP poskytuje typy bohaté přihlašovacích údajů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<přenos >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|Definuje typ přenosu pro zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečení může být buď nebo přenosu specifické pro zprávy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu pověření](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
