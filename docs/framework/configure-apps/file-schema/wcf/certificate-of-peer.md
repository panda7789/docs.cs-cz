---
title: "&lt;certificate&gt; – &lt;peer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1449bab5d585183d73da5ca0d2234857d9d92151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltcertificategt-of-ltpeergt"></a>&lt;certificate&gt; – &lt;peer&gt;
Určuje certifikát používají partnerského uzlu.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<sdílené >  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`findValue`|Řetězec, který obsahuje hodnotu k vyhledání v úložišti certifikátů X.509. Typ obsažený v atributu musí splňovat požadavky na zadané `x509FindType`. Výchozí hodnota je prázdný řetězec.|  
|`storeLocation`|Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu druhé strany proti. Platné hodnoty patří:<br /><br /> -LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.<br />-CurrentUser: úložiště certifikátů přiřazená aktuálnímu uživateli.<br /><br /> Výchozí hodnota je v místním počítači.|  
|`storeName`|Určuje název úložiště certifikátu X.509 otevřete. Platné hodnoty patří:<br /><br /> -Adresáře: Úložiště certifikátů pro ostatní uživatele.<br />-AuthRoot: Certifikát úložiště pro třetí strany certifikačních autorit (CA).<br />-CertificateAuthority: Úložiště certifikátů pro zprostředkující certifikační autority (CA).<br />-Nepovolené: Certifikát úložiště pro odvolané certifikáty.<br />-: Úložiště certifikátů my Pro osobní certifikáty.<br />-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).<br />-TrustedPeople: Úložiště certifikátů přímo důvěryhodné osoby a prostředky.<br />-TrustedPublisher: Úložiště certifikátů pro přímo důvěryhodných vydavatelů.<br /><br /> Výchozí hodnota je můj.|  
|`X509FindType`|Definuje typ vyhledávání X.509 provést. Platné hodnoty patří:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName.<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Typ obsažený v `findValue` atributu musí splňovat požadavky na zadané `X509FindType`.<br /><br /> Výchozí hodnota je FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Určuje, že aktuální přihlašovací údaje pro uzel sdílené.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element konfigurace obsahuje `X509Certificate2` instance používané při ověřování okolí sdílené v mřížce.  
  
 Další informace o programování peer-to-peer, najdete v části [Peer-to-Peer sítě](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Ověřování zpráv rovnocenného kanálu](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování rovnocenného kanálu](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
