---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252147"
---
# <a name="certificatereference"></a>\<certificateReference >
Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**  
  
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
|storeName|Název úložiště certifikátů X. 509. Výchozí hodnota je my. Volitelný parametr.|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje umístění úložiště certifikátů X. 509. Výchozí hodnota je "LocalMachine". Volitelný parametr.|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType> Hodnota, která určuje typ hledání, které má být provedeno. Výchozí hodnota je "FindBySubjectDistinguishedName". Volitelný parametr.|  
|findValue|Hodnota, která se má vyhledat v úložišti certifikátů X. 509 Volitelný parametr.|  
|isChainIncluded|Určuje, zda má být ověřování provedeno pomocí řetězu certifikátů. Výchozí hodnota je "true"; ověřování se provádí pomocí řetězu certifikátů. Volitelný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 `<certificateReference>` Element určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů. Pokud je zadána jako podřízený element `<serviceCertificate>` elementu, určuje umístění a nastavení ověřování certifikátu X. 509, který se používá k šifrování a dešifrování tokenů. Element je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement>třídou. `<certificateReference>`
