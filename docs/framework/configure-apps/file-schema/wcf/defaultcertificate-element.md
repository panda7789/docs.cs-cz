---
title: Element &lt;defaultCertificate&gt;
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 9b99ee36fdb924ea12f3023984a3aa4b590937e8
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847851"
---
# <a name="ltdefaultcertificategt-element"></a>Element &lt;defaultCertificate&gt;
Určuje certifikát X.509, který se má použít při služba nebo STS neposkytne pomocí protokolu vyjednávání.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<třídu clientCredentials >  
\<serviceCertificate >  
\<defaultCertificate >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|findValue|řetězec. Hodnota, kterou chcete vyhledat.|  
|X509FindType|Výčet. Jeden z pole certifikátu k prohledání.|  
|storeLocation|Výčet. Jedno ze dvou systémových úložišť k prohledání.|  
|storeName|Výčet. Jedno ze systémových úložišť k prohledání.|  
  
## <a name="findvalue-attribute"></a>findValue atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Hodnota závisí na poli (určenému atributem X509FindType) být vyhledán. Například pokud hledání kryptografickým otiskem, hodnota musí být řetězec šestnáctkových čísel.|  
  
## <a name="x509findtype-attribute"></a>Atribut x509FindType  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: adresáře, AuthRoot, CertificateAuthority zakázané, My, Root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Určuje certifikát používaný při ověřování služby ke klientovi.|  
  
## <a name="remarks"></a>Poznámky  
 U vazeb, které používají zabezpečení na základě certifikátů zpráv certifikát určený tento prvek konfigurace se používá k šifrování zpráv ve službě a měl by používat službu pro podepisování odpovědi klientovi. Ukládají se jeden certifikát má být použit při služby je určen žádný certifikát.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje certifikát používaný pro koncové body, jehož identifikátor URI začíná `http://www.contoso.com` a certifikát má použít pro všechny ostatní koncové body, které neprovádějte vyjednávání certifikátu.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [\<ověřování >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
