---
title: Element &lt;defaultCertificate&gt;
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: a4af1c6ec452b24634fa50162fa71f069e2451f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751009"
---
# <a name="ltdefaultcertificategt-element"></a>Element &lt;defaultCertificate&gt;
Určuje certifikát X.509, který se má použít při služby nebo služby tokenů zabezpečení neposkytuje jeden prostřednictvím vyjednávání protokolu.  
  
 \<system.ServiceModel>  
\<chování >  
část endpointBehaviors  
\<chování >  
\<clientCredentials >  
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
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|findValue|Řetězec. Hodnota, kterou chcete vyhledat.|  
|X509FindType|Výčet. Jeden z pole certifikátu pro vyhledávání.|  
|storeLocation|Výčet. Mezi dvěma systému úložiště prohledávaných umístění.|  
|storeName|Výčet. Jeden z úložiště systému pro vyhledávání.|  
  
## <a name="findvalue-attribute"></a>findValue atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|Hodnota závisí na poli (zadané v atributu X509FindType) být vyhledán. Například pokud hledání kryptografický otisk, hodnota musí být řetězec o délce hexadecimální číslice.|  
  
## <a name="x509findtype-attribute"></a>Atribut x509FindType  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Výčet|Hodnoty patří: CertificateAuthority adresáře, AuthRoot, zakázané, Moje, Root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Určuje certifikát pro použití při ověřování služby klienta.|  
  
## <a name="remarks"></a>Poznámky  
 U vazeb, které používají zabezpečení zpráv pomocí certifikátů certifikát určený element tato konfigurace se používá k šifrování zpráv do služby a očekává se použije pro podepisování odpovědi klientovi službou. Ukládají se jeden certifikát, který se má použít, když je zadán žádný certifikát služby.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje certifikát má použít pro koncové body, jejichž URI začíná http://www.contoso.com a certifikát má použít pro všechny ostatní koncové body, které neprovádět vyjednávání certifikátu.  
  
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
