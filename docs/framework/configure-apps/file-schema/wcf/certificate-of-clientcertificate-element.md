---
title: '&lt;certificate&gt; elementu &lt;clientCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bef4067d0fa74aa90841040ca5e6b3ea22f1e499
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a>&lt;certificate&gt; elementu &lt;clientCertificate&gt;
Určuje X.509 certifikát používaný k podepisování a šifrování zpráv.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<clientCertificate >  
\<certifikátu >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`findValue`|Řetězec, který obsahuje hodnotu k vyhledání v úložišti certifikátů X.509. Typ obsažený v atributu musí splňovat požadavky na zadaný X509FindType. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu serveru proti. Platné hodnoty patří:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.<br />-CurrentUser: úložiště certifikátů přiřazená aktuálnímu uživateli.<br /><br /> Výchozí hodnota je v místním počítači.|  
|`storeName`|Určuje název úložiště certifikátu X.509 otevřete. Platné hodnoty patří:<br /><br /> -Adresáře: Úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: Certifikát úložiště pro třetí strany certifikační autority (CA).<br />-Certifikační autorita: Úložiště certifikátů pro zprostředkující certifikační autority (CA).<br />-Nepovolené: Certifikát úložiště pro odvolané certifikáty.<br />-: Úložiště certifikátů my Pro osobní certifikáty.<br />-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).<br />-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.<br />-TrustedPublisher: Úložiště certifikátů pro přímo důvěryhodné vydavatele.<br /><br /> Výchozí hodnota je můj.|  
|`X509FindType`|Definuje typ vyhledávání X.509 provést. Platné hodnoty patří:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName.<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Typ obsažený v `findValue` atributu musí splňovat požadavky na zadaný X509FindType.<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Poznámky  
 `<certificate>` Element se používá, když služba musí mít certifikát klienta předem pro bezpečnou komunikaci s klientem. K tomu dochází, když pomocí vzoru duplexní komunikace. Ve vzoru typičtější požadavků a odpovědí klienta zahrnuje svůj certifikát v žádosti, které služba používá k šifrování a podepisování odpověď zpět klientovi. Ve vzoru duplexní komunikace ale služba nemá požadavek od klienta a proto potřebuje certifikát klienta předem k zabezpečení zprávy do klienta. Proto musíte získat certifikát klienta v vyjednávání out-of-band a zadat certifikát pomocí tohoto elementu. Další informace o duplexní služby najdete v tématu [postupy: vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, jak se najít odpovídající certifikátu X.509. certifikát a vlastní ověření zadejte `<authentication>` elementu.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Postupy: vytvoření služby, který využívá validátor vlastní certifikát](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
