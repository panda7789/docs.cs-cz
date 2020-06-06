---
title: Element <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400418"
---
# <a name="defaultcertificate-element"></a>Element \<defaultCertificate>
Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
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
|findValue|Řetězec. Hodnota, kterou chcete vyhledat.|  
|x509FindType|Enumeration. Jedno z polí certifikátu, které chcete vyhledat.|  
|storeLocation|Enumeration. Jedno ze dvou umístění úložiště systému, které chcete vyhledat.|  
|storeName|Enumeration. Jedno ze systémových úložišť, které chcete vyhledat.|  
  
## <a name="findvalue-attribute"></a>findValue – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Řetězec|Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván. Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.|  
  
## <a name="x509findtype-attribute"></a>x509FindType – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|CurrentUser nebo LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|Výčet|Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Určuje certifikát, který se má použít při ověřování služby pro klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Pro vazby, které používají zabezpečení zpráv založené na certifikátech, se certifikát zadaný pomocí tohoto elementu konfigurace používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi. Ukládá se jeden certifikát, který se použije, když služba nezadá žádný certifikát.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje certifikát, který má být použit pro koncové body, jejichž identifikátor URI začíná `http://www.contoso.com` a certifikát, který má být použit pro všechny ostatní koncové body, které neprovádějí vyjednávání certifikátů.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
