---
title: <security> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738633"
---
# <a name="security-of-webhttpbinding"></a>\<security> z \<webHttpBinding>
Určuje požadavky na zabezpečení pro koncový bod nakonfigurovaný pomocí [\<webHttpBinding>](webhttpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Určuje, zda koncový bod nepoužívá zabezpečení na úrovni přenosu nebo žádné zabezpečení. Výchozí formát je `None`. Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode> .|  
  
## <a name="mode-attribute"></a>Mode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázané.|  
|Přenos|Zabezpečení je k dispozici pomocí protokolu HTTPS. Služba musí být nakonfigurovaná s certifikáty SSL. Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby. Ověřování klienta je řízeno pomocí `ClientCredentialType` atributu [\<transport>](transport-of-webhttpbinding.md) .|  
|TransportCredentialOnly|Tento režim neposkytuje integritu a důvěrnost zpráv. Poskytuje ověřování klientů založené na protokolu HTTP. Tento režim by se měl používat opatrně. Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|Prvek vazby, který slouží ke konfiguraci koncových bodů pro webové služby Windows Communication Foundation (WCF), které reagují na požadavky HTTP namísto zpráv SOAP.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [Programovací model webových služeb HTTP WCF](../../../wcf/feature-details/wcf-web-http-programming-model.md)
