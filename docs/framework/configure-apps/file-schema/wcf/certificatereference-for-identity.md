---
title: <certificateReference> pro <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 49c731b2637c15e0b968d8c2523c51c8e138e7bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926173"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > pro \<> identity
Určuje nastavení pro ověřování certifikátu X. 509. Klient zabezpečeného Windows Communication Foundation (WCF), který se připojí ke koncovému bodu s touto identitou, ověří, že deklarace prezentované serverem obsahují deklaraci identity, která se používá k vytvoření této identity.  
  
 \<> identity  
\<certificateReference >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|findValue|Určuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509. Typ obsažený v tomto atributu musí splňovat požadavky zadané `X509FindType` hodnoty. Výchozí hodnota je prázdný řetězec.|  
|isChainIncluded|Logická hodnota, která určuje, zda je ověření provedeno pomocí řetězu certifikátů.|  
|storeLocation|Určuje umístění úložiště certifikátů, které může klient použít k ověření certifikátu serveru.<br /><br /> Platné hodnoty jsou následující:<br /><br /> LocalMachine Úložiště certifikátů přiřazené k místnímu počítači.<br />CurrentUser Úložiště certifikátů přiřazené k aktuálnímu uživateli.<br /><br /> Výchozí hodnota je LocalMachine.<br /><br /> Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Určuje název úložiště certifikátů X. 509, které se má otevřít.<br /><br /> Platné hodnoty jsou následující:<br /><br /> - AddressBook: Úložiště certifikátů pro ostatní uživatele.<br />- AuthRoot: Úložiště certifikátů pro certifikační autority třetích stran (CAs).<br />CertificateAuthority Úložiště certifikátů pro zprostředkující certifikační autority.<br />Zakázané Úložiště certifikátů pro odvolané certifikáty.<br />Složkách Úložiště certifikátů pro osobní certifikáty.<br />Zobrazuje Úložiště certifikátů pro důvěryhodné kořenové certifikační autority.<br />TrustedPeople Úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.<br />- TrustedPublisher: Úložiště certifikátů pro vydavatele přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je my.<br /><br /> Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Určuje typ vyhledávání X. 509, který se má provést. Typ obsažený v `findValue` atributu musí splňovat požadavky zadaného X509FindType.<br /><br /> Platné hodnoty jsou následující:<br /><br /> - FindByThumbPrint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.<br /><br /> Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Určuje nastavení, které umožní ověřování koncového bodu jinými koncovými body výměny zpráv.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
