---
title: <certificate><clientCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400534"
---
# <a name="certificate-of-clientcertificate-element"></a>\<certificate>\<clientCertificate>elementu
Určuje certifikát X. 509, který se používá k podpisu a šifrování zpráv.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`findValue`|Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509. Typ obsažený v atributu musí splňovat požadavky zadaného X509FindType. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění úložiště certifikátů X. 509, které klient používá k ověření certifikátu serveru proti. Platné hodnoty jsou následující:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.<br />-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.<br /><br /> Výchozí hodnota je LocalMachine.|  
|`storeName`|Určuje název úložiště certifikátů X. 509, které se má otevřít. Platné hodnoty jsou následující:<br /><br /> -AddressBook: úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: úložiště certifikátů pro certifikační autority třetích stran (CAs).<br />-Certifikační autorita: úložiště certifikátů pro zprostředkující certifikační autority (CAs).<br />-Nepovoleno: úložiště certifikátů pro odvolané certifikáty.<br />– Moje: úložiště certifikátů pro osobní certifikáty.<br />-Root: úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).<br />-TrustedPeople: úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.<br />-TrustedPublisher: úložiště certifikátů pro vydavatele přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je Moje.|  
|`X509FindType`|Definuje typ hledání X. 509, které se má provést. Platné hodnoty jsou následující:<br /><br /> - FindByThumbPrint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Typ obsažený v `findValue` atributu musí splňovat požadavky zadaného X509FindType.<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Poznámky  
 `<certificate>`Element se používá v případě, že služba musí mít certifikát klienta předem pro zabezpečenou komunikaci s klientem. K tomu dochází při použití duplexního způsobu komunikace. V typickém vzoru požadavků a odpovědí klient zahrne svůj certifikát do žádosti, kterou služba používá k šifrování a podepsání své odpovědi zpět do klienta. Ve způsobu duplexního přenosu však služba nemá požadavek od klienta, a proto potřebuje certifikát klienta předem, aby bylo možné zprávu zabezpečit klientovi. Proto je nutné získat certifikát klienta při vzdáleném vyjednávání a zadat certifikát pomocí tohoto prvku. Další informace o duplexních službách najdete v tématu [Postupy: Vytvoření duplexního kontraktu](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, jak najít vhodný certifikát X. 509 a typ vlastního ověřování v `<authentication>` elementu.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
