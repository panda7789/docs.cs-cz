---
title: <serviceCertificate> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 086b700b94198aa36e61289178ebbed75d33da98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173560"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate > z \<serviceCredentials >
Určete certifikát X.509, který se použije k ověření služby klientů, kteří používají režim zabezpečených zpráv.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`findValue`|Řetězec, který obsahuje hodnotu vyhledávání v úložišti certifikátů X.509. Typ obsažené v atributu musí splňovat požadavky zadané X509FindType. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu serveru. Platné hodnoty patří:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené do místního počítače.<br />-CurrentUser: úložiště certifikátů přiřazené aktuálnímu uživateli.<br /><br /> Výchozí hodnota je v místním počítači.|  
|`storeName`|Určuje název úložiště certifikátu X.509 otevřete. Platné hodnoty patří:<br /><br /> -Adresáře: Úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: Úložiště certifikátů pro třetí strany certifikačními autoritami (CA).<br />-CertificatAuthority: Úložiště certifikátů zprostředkující certifikační autority (CA).<br />– Zakázáno: Úložiště certifikátů pro odvolaných certifikátů.<br />-Můj: Úložiště certifikátů pro osobní certifikáty.<br />-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).<br />-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.<br />-TrustedPublisher: Úložiště certifikátů přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je My.|  
|`x509FindType`|Definuje typ hledání X.509, který se spustí. Platné hodnoty patří:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> Typ součástí `findValue` atribut musí splňovat požadavky na zadaný X509FindType.<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element slouží k určení certifikátu X.509, který se použije k ověření služby klientů, kteří používají režim zabezpečených zpráv. Pokud používáte certifikát, který bude pravidelně obnovovat, se změní jeho kryptografický otisk. V takovém případě použijte název subjektu, jako `x509FindType` vzhledem k tomu, že certifikát můžete opakováno se stejným názvem subjektu.  
  
 Další informace o používání elementu najdete v tématu [jak: Zadání hodnot přihlašovacích údajů klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Postupy: Zadání hodnot přihlašovacích údajů klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
