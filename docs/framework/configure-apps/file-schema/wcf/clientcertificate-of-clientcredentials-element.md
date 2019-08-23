---
title: <clientCertificate><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: 3450df921da8c72a555c2faf424c51e0063cb235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926122"
---
# <a name="clientcertificate-of-clientcredentials-element"></a>\<ClientCertificate > \<elementu ClientCredentials >
Definuje certifikát X. 509, který se používá k ověření klienta ke službě.  
  
 \<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
\<clientCredentials>  
\<clientCertificate>  
  
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
|`storeLocation`|Určuje umístění certifikátu X. 509, který klient používá ke svému ověření ke službě. Platné hodnoty jsou následující:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.<br />-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.<br /><br /> Výchozí hodnota je LocalMachine. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Určuje název úložiště certifikátů X. 509, které se má hledat. Platné hodnoty jsou následující:<br /><br /> - AddressBook: Úložiště certifikátů pro ostatní uživatele.<br />- AuthRoot: Úložiště certifikátů pro certifikační autority třetích stran.<br />CertificateAuthority Úložiště certifikátů pro zprostředkující certifikační autority (CAs).<br />Zakázané Úložiště certifikátů pro odvolané certifikáty.<br />Složkách Úložiště certifikátů pro osobní certifikáty.<br />Zobrazuje Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).<br />TrustedPeople Úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.<br />- TrustedPublisher: Úložiště certifikátů pro vydavatele přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je my. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Definuje typ hledání X. 509, které se má provést. Typ obsažený v `findValue` atributu musí splňovat požadavky tohoto atributu. Platné hodnoty jsou následující:<br /><br /> - FindByThumbPrint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace Určuje certifikát použitý k ověření klienta s tímto elementem. Další informace najdete v tématu [jak: Zadejte hodnoty](../../../wcf/how-to-specify-client-credential-values.md)přihlašovacích údajů klienta.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Zadat hodnoty přihlašovacích údajů klienta](../../../wcf/how-to-specify-client-credential-values.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
