---
title: <certificate> z <clientCertificate> – Element
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 98e60d750dad1529ffb35055d26e278ceb7c873a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113929"
---
# <a name="certificate-of-clientcertificate-element"></a>\<certifikát > z \<clientCertificate > – Element
Určuje certifikát X.509 certifikát používaný k podepisování a šifrování zpráv.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<clientCertificate>  
\<certifikát >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`findValue`|Řetězec, který obsahuje hodnotu vyhledávání v úložišti certifikátů X.509. Typ obsažené v atributu musí splňovat požadavky zadané X509FindType. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu serveru. Platné hodnoty patří:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené do místního počítače.<br />-CurrentUser: úložiště certifikátů přiřazené aktuálnímu uživateli.<br /><br /> Výchozí hodnota je v místním počítači.|  
|`storeName`|Určuje název úložiště certifikátu X.509 otevřete. Platné hodnoty patří:<br /><br /> -Adresáře: Úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: Úložiště certifikátů pro třetí strany certifikačními autoritami (CA).<br />-Certifikační autorita systému: Úložiště certifikátů zprostředkující certifikační autority (CA).<br />– Zakázáno: Úložiště certifikátů pro odvolaných certifikátů.<br />-Můj: Úložiště certifikátů pro osobní certifikáty.<br />-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).<br />-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.<br />-TrustedPublisher: Úložiště certifikátů přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je My.|  
|`X509FindType`|Definuje typ hledání X.509, který se spustí. Platné hodnoty patří:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> Typ součástí `findValue` atribut musí splňovat požadavky na zadaný X509FindType.<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Poznámky  
 `<certificate>` Element se používá, když služba musí mít certifikát klienta předem k bezpečné komunikaci s klientem. Vyvolá se při použití vzoru duplexní komunikaci. Ve vzoru obvyklejší žádostí a odpovědí klient zahrne svůj certifikát v požadavku, který službu používá k šifrování a podepisování odpověď zpět klientovi. Ve vzoru duplexní komunikaci ale služba nemá žádosti z klienta a proto potřebuje certifikát klienta předem pro zabezpečené zprávy do klienta. Proto musíte získat certifikát klienta v vyjednávání out-of-band a vyberte certifikát pro použití tohoto prvku. Další informace o duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, jak najít odpovídající certifikát X.509 a vlastní ověření zadejte `<authentication>` elementu.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
