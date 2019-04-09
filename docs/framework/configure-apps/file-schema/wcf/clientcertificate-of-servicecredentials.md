---
title: <clientCertificate> of <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 26ebac6439a90959e3a926e6a36c9044251a4aae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107980"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<clientCertificate> of \<serviceCredentials>
Určuje certifikát X.509 použitý k podepisování a šifrování zpráv do formuláře klienta služby v duplexním komunikačním režimu.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<clientCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ověřování >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|Určuje možnosti ověřování klientského certifikátu.|  
|[\<certifikát >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|Určuje certifikát, který chcete použít.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element se používá při služba musí mít certifikát klienta předem k bezpečné komunikaci s klientem. Vyvolá se při použití vzoru duplexní komunikaci. Ve vzoru obvyklejší žádostí a odpovědí klient zahrne svůj certifikát v požadavku, který službu používá k šifrování a podepisování odpověď zpět klientovi. Ve vzoru duplexní komunikaci ale služba nemá žádosti z klienta a proto potřebuje certifikát klienta předem pro zabezpečené zprávy do klienta. Proto musíte získat certifikát klienta v vyjednávání out-of-band a vyberte certifikát pro použití tohoto prvku. Další informace o duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Certifikát, nastavte v tomto elementu se používá k šifrování zpráv klienta jenom u vazeb, které jsou nakonfigurovány s `MutualCertificateDuplex` režim ověřování zabezpečení zprávy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Postupy: Vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
