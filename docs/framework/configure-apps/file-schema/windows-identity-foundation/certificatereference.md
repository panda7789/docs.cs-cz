---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
Určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|storeName|Název úložiště certifikátu X.509. Výchozí hodnota je "Moje". Volitelné.|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje umístění úložiště certifikátů X.509. Výchozí hodnota je "LocalMachine". Volitelné.|  
|X509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnotu, která určuje typ vyhledávání, která má být zpracována. Výchozí hodnota je "FindBySubjectDistinguishedName". Volitelné.|  
|findValue|Hodnota k vyhledání v úložišti certifikátů X.509. Volitelné.|  
|isChainIncluded|Určuje, zda má být provedena ověření pomocí řetězu certifikátů. Výchozí hodnota je "true"; ověření se provádí na základě řetězu certifikátů. Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 `<certificateReference>` Element určuje nastavení, které se používají k vyhledání a ověření certifikátu X.509. certifikát v úložišti certifikátů. Pokud je zadán jako podřízený element `<serviceCertficate>` elementu, určuje umístění a ověření nastavení certifikátu X.509, který se používá k šifrování a dešifrování tokenů. `<certificateReference>` Element je reprezentována <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídy.
