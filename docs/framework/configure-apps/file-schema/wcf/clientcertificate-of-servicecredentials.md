---
title: "&lt;clientCertificate&gt; – &lt;serviceCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc2dfd94ffbf8ce08dee9c14421f389861e99e77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a>&lt;clientCertificate&gt; – &lt;serviceCredentials&gt;
Definuje certifikátu X.509. certifikát použít k podepisování a šifrování zpráv do formuláře jako klienta služby ve tvaru duplexní komunikace.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<clientCertificate >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ověřování >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|Určuje možnosti ověřování certifikátu klienta.|  
|[\<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|Určuje certifikát, který chcete použít.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje pověření, která mají být použity v ověřování služby, a ověření přihlašovacích údajů klienta související nastavení.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element se používá, pokud služba musí mít certifikát klienta předem pro bezpečnou komunikaci s klientem. K tomu dochází, když pomocí vzoru duplexní komunikace. Ve vzoru typičtější požadavků a odpovědí klienta zahrnuje svůj certifikát v žádosti, které služba používá k šifrování a podepisování odpověď zpět klientovi. Ve vzoru duplexní komunikace ale služba nemá požadavek od klienta a proto potřebuje certifikát klienta předem k zabezpečení zprávy do klienta. Proto musíte získat certifikát klienta v vyjednávání out-of-band a zadat certifikát pomocí tohoto elementu. Další informace o duplexní služby najdete v tématu [postupy: vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Nastavit v tomto elementu certifikát se používá k šifrování zpráv, které mají klienta jenom u vazeb, které jsou nakonfigurovány s `MutualCertificateDuplex` režim ověření zabezpečení zpráv.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [Postupy: vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
