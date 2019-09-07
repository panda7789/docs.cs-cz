---
title: <serviceCertificate> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 513dcad7f4325d653df87fe9cc27572c25e153c5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399674"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate > \<ServiceCredentials >
Zadejte certifikát X. 509, který bude použit k ověření služby klientům pomocí režimu zabezpečení zpráv.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**  
  
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
|`findValue`|Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509. Typ obsažený v atributu musí splňovat požadavky zadaného X509FindType. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění úložiště certifikátů X. 509, které klient používá k ověření certifikátu serveru proti. Platné hodnoty jsou následující:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.<br />-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.<br /><br /> Výchozí hodnota je LocalMachine.|  
|`storeName`|Určuje název úložiště certifikátů X. 509, které se má otevřít. Platné hodnoty jsou následující:<br /><br /> - AddressBook: Úložiště certifikátů pro ostatní uživatele.<br />- AuthRoot: Úložiště certifikátů pro certifikační autority třetích stran (CAs).<br />- CertificatAuthority: Úložiště certifikátů pro zprostředkující certifikační autority (CAs).<br />Zakázané Úložiště certifikátů pro odvolané certifikáty.<br />Složkách Úložiště certifikátů pro osobní certifikáty.<br />Zobrazuje Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).<br />TrustedPeople Úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.<br />- TrustedPublisher: Úložiště certifikátů pro vydavatele přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je my.|  
|`x509FindType`|Definuje typ hledání X. 509, které se má provést. Platné hodnoty jsou následující:<br /><br /> - FindByThumbprint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Typ obsažený v `findValue` atributu musí splňovat požadavky zadaného X509FindType.<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí tohoto prvku můžete zadat certifikát X. 509, který se použije k ověření služby pro klienty v režimu zabezpečení zpráv. Pokud používáte certifikát, který se bude pravidelně obnovovat, změní se jeho kryptografický otisk. V takovém případě použijte název `x509FindType` subjektu, protože certifikát je možné vystavit znovu se stejným názvem subjektu.  
  
 Další informace o použití prvku naleznete v tématu [How to: Zadejte hodnoty](../../../wcf/how-to-specify-client-credential-values.md)přihlašovacích údajů klienta.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Postupy: Zadat hodnoty přihlašovacích údajů klienta](../../../wcf/how-to-specify-client-credential-values.md)
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
