---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152811"
---
# <a name="certificatereference"></a>\<certifikátReference>
Určuje nastavení, která se používají k vyhledání a ověření certifikátu X.509 v úložišti certifikátů.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
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
|Storename|Název úložiště certifikátů X.509. Výchozí hodnota je "My". Nepovinný parametr.|  
|Storelocation|Hodnota, <xref:System.Security.Cryptography.X509Certificates.StoreLocation> která určuje umístění úložiště certifikátů X.509. Výchozí hodnota je "LocalMachine". Nepovinný parametr.|  
|x509FindType|Hodnota, <xref:System.Security.Cryptography.X509Certificates.X509FindType> která určuje typ hledání, které má být provedeno. Výchozí hodnota je "FindBySubjectDistinguishedName". Nepovinný parametr.|  
|Findvalue|Hodnota, kterou chcete vyhledat v úložišti certifikátů X.509. Nepovinný parametr.|  
|isChainIncluded|Určuje, zda má být ověření provedeno pomocí řetězu certifikátů. Výchozí hodnota je "true"; ověření se provádí pomocí řetězu certifikátů. Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|Konfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<certificateReference>` určuje nastavení, které se používá k vyhledání a ověření certifikátu X.509 v úložišti certifikátů. Pokud je zadán jako podřízený `<serviceCertificate>` prvek prvku, určuje umístění a nastavení ověření certifikátu X.509, který se používá k šifrování a dešifrování tokenů. Prvek `<certificateReference>` je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídou.
