---
title: <authentication> z <serviceCertificate> – Element
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: b96d53312d672eebd67de82f69cd9a0a2b5bd22e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117756"
---
# <a name="authentication-of-servicecertificate-element"></a>\<ověřování > z \<serviceCertificate > – Element
Určuje nastavení klientského serveru proxy k ověření certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials>  
\<serviceCertificate>  
\<ověřování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|customCertificateValidatorType|řetězec. Typ a sestavení používané pro ověření vlastního typu.|  
|certificateValidationMode|Určuje jeden ze tří režimů používaných pro ověření pověření. Pokud hodnotu `Custom`, pak musí být rovněž dodán customCertificateValidator. Výchozí hodnota je `ChainTrust`.|  
|revocationMode|Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL). Výchozí hodnota je `Online`.|  
|trustedStoreLocation|Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`. Tato hodnota se používá při certifikát služby se vyjedná do klienta. Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště. Výchozí hodnota je `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|String|Určuje název typu a sestavení a další data použít k vyhledání typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: NONE, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: NoCheck, Online, Offline.<br /><br /> Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Jeden z následujících hodnot: LocalMachine nebo CurrentUser. Výchozí hodnota je CurrentUser. Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle v rámci LocalMachine. Pokud klientská aplikace běží pod účtem uživatele, certifikát je obvykle v CurrentUser.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Určuje certifikát používaný při ověřování služby ke klientovi.|  
  
## <a name="remarks"></a>Poznámky  
 `certificateValidationMode` Atribut tento prvek konfigurace určuje úroveň vztahu důvěryhodnosti používá k ověřování certifikátů. Ve výchozím nastavení, úroveň je nastavena `ChainTrust`, která určuje, že každý certifikát musí být nalezena v hierarchii certifikátů důvěryhodné certifikační autority v horní části řetězce s koncovkou. Toto je nejbezpečnější režim. Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že jsou přijímány samostatně vydané certifikáty (peer vztahu důvěryhodnosti) a také certifikáty, které jsou v důvěryhodným řetězem. Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samostatně vydané certifikáty nemusí být zakoupenému od důvěryhodné autority. Při nasazování klienta, použijte `ChainTrust` místo hodnoty. Můžete také nastavit hodnotu `Custom` nebo `None`. Použít `Custom` hodnotu, je nutné nastavit také `customCertificateValidator` atribut na sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní třídy X509CertificateValidator. Další informace najdete v tématu [jak: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode` Atribut určuje, jak kontroluje odvolání certifikátů. Výchozí hodnota je `online` což znamená, že certifikáty se automaticky vráceny na zrušení. Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí dvě úlohy. Určuje první certifikát služby pro klienty při komunikaci s koncovými body, jejichž název domény je `www.contoso.com` přes protokol HTTP. Za druhé Určuje odvolání režimu a úložiště umístění použité během ověřování.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
