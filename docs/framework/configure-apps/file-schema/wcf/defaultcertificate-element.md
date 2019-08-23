---
title: Element <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919261"
---
# <a name="defaultcertificate-element"></a>\<defaultCertificate – element >
Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.  
  
 \<system.ServiceModel>  
\<> chování  
oddíl endpointBehaviors  
\<> chování  
\<clientCredentials>  
\<serviceCertificate>  
\<defaultCertificate >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|findValue|Řetezce. Hodnota, kterou chcete vyhledat.|  
|x509FindType|Enumeration. Jedno z polí certifikátu, které chcete vyhledat.|  
|storeLocation|Enumeration. Jedno ze dvou umístění úložiště systému, které chcete vyhledat.|  
|storeName|Enumeration. Jedno ze systémových úložišť, které chcete vyhledat.|  
  
## <a name="findvalue-attribute"></a>findValue – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|String|Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván. Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.|  
  
## <a name="x509findtype-attribute"></a>x509FindType – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Určuje certifikát, který se má použít při ověřování služby pro klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Pro vazby, které používají zabezpečení zpráv založené na certifikátech, se certifikát zadaný pomocí tohoto elementu konfigurace používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi. Ukládá se jeden certifikát, který se použije, když služba nezadá žádný certifikát.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje certifikát, který má být použit pro koncové body, jejichž `http://www.contoso.com` identifikátor URI začíná a certifikát, který má být použit pro všechny ostatní koncové body, které neprovádějí vyjednávání certifikátů.  
  
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

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [\<> ověřování](authentication-of-clientcertificate-element.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
