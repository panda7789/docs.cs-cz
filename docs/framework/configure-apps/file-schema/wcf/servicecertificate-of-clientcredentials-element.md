---
title: '&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f6f52eae3ed9ac3236f54c62ce8712656392f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a>&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;
Určuje certifikát pro použití při ověřování služby klienta.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials >  
\<serviceCertificate >  
  
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
|[\<defaultCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|Určuje certifikát X.509, který se má použít při služby nebo služby tokenů zabezpečení neposkytuje jeden prostřednictvím vyjednávání protokolu.|  
|[\<scopedCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Představuje kolekci certifikáty X.509, které jsou součástí konkrétní služby (obor) pro ověřování. Tato kolekce se obvykle používá k určení certifikáty služby pro služby tokenů zabezpečení ve scénáři federované.|  
|[\<ověřování >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|Určuje chování ověřování pro certifikáty služby, které klient používá.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření používaná klientem k vlastnímu ověření služby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element konfigurace určuje nastavení používaná klientem ověřit certifikát předložený služby pomocí ověřování protokolem SSL. Obsahuje taky libovolný certifikát pro službu, která je explicitně nakonfigurovaná na straně klienta, který chcete použít pro šifrování zpráv pomocí zabezpečení zpráv.  
  
 Atributy `serviceCertificate` element jsou stejné jako atributy [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
