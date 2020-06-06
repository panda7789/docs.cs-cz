---
title: <clientCertificate><clientCredentials>elementu
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: fb95ef3168378227e41e55c6fd5e5b772cb7ad0f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400519"
---
# <a name="clientcertificate-of-clientcredentials-element"></a>\<clientCertificate>\<clientCredentials>elementu
Definuje certifikát X. 509, který se používá k ověření klienta ke službě.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`findValue`|Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509. Typ obsažený v atributu musí splňovat požadavky `X509FindType` hodnoty atributu. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění certifikátu X. 509, který klient používá ke svému ověření ke službě. Platné hodnoty jsou následující:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.<br />-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.<br /><br /> Výchozí hodnota je LocalMachine. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .|  
|`storeName`|Určuje název úložiště certifikátů X. 509, které se má hledat. Platné hodnoty jsou následující:<br /><br /> -AddressBook: úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: úložiště certifikátů pro certifikační autority (CAs) třetích stran.<br />-CertificateAuthority: úložiště certifikátů pro zprostředkující certifikační autority (CAs).<br />-Nepovoleno: úložiště certifikátů pro odvolané certifikáty.<br />– Moje: úložiště certifikátů pro osobní certifikáty.<br />-Root: úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).<br />-TrustedPeople: úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.<br />-TrustedPublisher: úložiště certifikátů pro vydavatele přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je Moje. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreName> .|  
|X509FindType|Definuje typ hledání X. 509, které se má provést. Typ obsažený v `findValue` atributu musí splňovat požadavky tohoto atributu. Platné hodnoty jsou následující:<br /><br /> - FindByThumbPrint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509FindType> .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace Určuje certifikát použitý k ověření klienta s tímto elementem. Další informace najdete v tématu [Postupy: určení hodnot přihlašovacích údajů klienta](../../../wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Zadání hodnot přihlašovacích údajů klienta](../../../wcf/how-to-specify-client-credential-values.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
