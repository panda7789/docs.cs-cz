---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c7dc9cfff15e70eff0086cfd98a19f3360ab8bb0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423028"
---
# <a name="certificatereference"></a>\<certificateReference >
Určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<serviceCertificate>  
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
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje umístění úložiště certifikátu X.509. Výchozí hodnota je "LocalMachine". Volitelné.|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnotu, která určuje typ hledání, které má být provedena. Výchozí hodnota je "FindBySubjectDistinguishedName". Volitelné.|  
|findValue|Hodnotu vyhledávání v úložišti certifikátů X.509. Volitelné.|  
|isChainIncluded|Určuje, zda by měl provádět ověření pomocí řetězu certifikátů. Výchozí hodnota je "true"; ověření se provádí na základě řetězu certifikátů. Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Nakonfiguruje certifikát používaný k šifrování a dešifrování tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 `<certificateReference>` Prvek určuje nastavení, které se používají k vyhledání a ověřit certifikát X.509 v úložišti certifikátů. Pokud je zadán jako podřízený prvek `<serviceCertificate>` elementu, určuje umístění a ověření nastavení certifikátu X.509, který se používá k šifrování a dešifrování tokenů. `<certificateReference>` Prvek je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídy.
