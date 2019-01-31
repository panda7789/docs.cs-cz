---
title: <certificateReference> pro <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 44bfb2fd77c4f4db6f7fede296b1cdb74e8d5e7c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254827"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > pro \<identity >
Určuje nastavení pro ověřování certifikátu X.509. Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tuto identitu ověří, deklarací identity předkládaných server obsahovat deklaraci identity použít k vytvoření této identity.  
  
 \<identity>  
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
|findValue|Určuje hodnotu vyhledávání v úložišti certifikátů X.509. Typ obsažený v tomto atributu musí splňovat požadavky na zadané `X509FindType` hodnotu. Výchozí hodnota je prázdný řetězec.|  
|isChainIncluded|Logická hodnota určující, pokud je ověřování prováděno pomocí certifikačního řetězce.|  
|storeLocation|Určuje umístění úložiště certifikátů, který může klient použít pro ověření certifikátu serveru.<br /><br /> Platné hodnoty patří:<br /><br /> -LocalMachine: Úložiště certifikátů přiřazené do místního počítače.<br />-CurrentUser: Úložiště certifikátů přiřazené aktuálnímu uživateli.<br /><br /> Výchozí hodnota je v místním počítači.<br /><br /> Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Určuje název úložiště certifikátu X.509 otevřete.<br /><br /> Platné hodnoty patří:<br /><br /> -Adresáře: Úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: Úložiště certifikátů pro třetí strany certifikačními autoritami (CA).<br />-CertificateAuthority: Úložiště certifikátů zprostředkující certifikační autority.<br />– Zakázáno: Úložiště certifikátů pro odvolaných certifikátů.<br />-Můj: Úložiště certifikátů pro osobní certifikáty.<br />-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority.<br />-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.<br />-TrustedPublisher: Úložiště certifikátů přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je My.<br /><br /> Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Určuje typ vyhledávání X.509, který se spustí. Typ součástí `findValue` atribut musí splňovat požadavky na zadaný X509FindType.<br /><br /> Platné hodnoty patří:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.<br /><br /> Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje nastavení, které umožňují ověřování z koncového bodu jiné koncové body výměna zpráv s ním.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
