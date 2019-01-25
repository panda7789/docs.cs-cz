---
title: '&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 2f1d95238a16bfd286a64973c6e5cfb95fe02dc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744875"
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a>&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;
Určuje certifikát používaný při ověřování služby ke klientovi.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<clientCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<defaultCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|Určuje certifikát X.509, který se má použít při služba nebo STS neposkytne pomocí protokolu vyjednávání.|  
|[\<scopedCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Představuje kolekci certifikátů X.509 poskytnuty konkrétní službou pro ověřování. Tato kolekce se obvykle používá k určení certifikáty služeb pro služby tokenu zabezpečení v případě federovaných.|  
|[\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|Určuje chování ověřování pro klientem používané certifikáty služeb.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření, která používá klient ke svému ověření ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace určuje nastavení klient ověřit certifikát předložený službou pomocí ověřování protokolem SSL. Obsahuje také jakýkoliv certifikát pro službu, která je explicitně nakonfigurovaná na straně klienta má použít k zašifrování zprávy do služby pomocí zabezpečení zpráv.  
  
 Atributy `serviceCertificate` jsou stejné jako atributy elementu [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
