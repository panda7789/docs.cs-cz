---
title: <security> z <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738658"
---
# <a name="security-of-netpeerbinding"></a>\<security> z \<netPeerBinding>
Definuje nastavení zabezpečení [\<netPeerTcpBinding>](netpeertcpbinding.md) , včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
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
|režim|Nepovinný parametr. Určuje typ zabezpečení, který používají partneři nakonfigurované s touto vazbou. Výchozí hodnota je `Message`. Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .|  
  
## <a name="mode-attribute"></a>mode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Zpráva|Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.|  
|Žádné|Zabezpečení je zakázané.|  
|Přenos|Zabezpečení je k dispozici pomocí protokolu HTTPS.|  
|TransportWithMessageCredential|Protokol HTTPS zajišťuje ověřování a důvěrnost. Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|Definuje typ přenosu pro zabezpečené zprávy odesílané partnerskými uzly nakonfigurovanými pomocí této vazby. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby pro [\<netPeerTcpBinding>](netpeertcpbinding.md) .|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečení může být specifické pro zprávy nebo pro přenos.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
