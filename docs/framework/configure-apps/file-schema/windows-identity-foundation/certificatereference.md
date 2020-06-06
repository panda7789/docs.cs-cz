---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152811"
---
# \<certificateReference>
Určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů.  
  
[**\<configuration>**](../configuration-element.md)\
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
|storeName|Název úložiště certifikátů X. 509. Výchozí hodnota je my. Nepovinný parametr.|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>Hodnota, která určuje umístění úložiště certifikátů X. 509. Výchozí hodnota je "LocalMachine". Nepovinný parametr.|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>Hodnota, která určuje typ hledání, které má být provedeno. Výchozí hodnota je "FindBySubjectDistinguishedName". Nepovinný parametr.|  
|findValue|Hodnota, která se má vyhledat v úložišti certifikátů X. 509 Nepovinný parametr.|  
|isChainIncluded|Určuje, zda má být ověřování provedeno pomocí řetězu certifikátů. Výchozí hodnota je "true"; ověřování se provádí pomocí řetězu certifikátů. Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|Nakonfiguruje certifikát, který se používá k šifrování a dešifrování tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 `<certificateReference>`Element určuje nastavení, která se používají k vyhledání a ověření certifikátu X. 509 v úložišti certifikátů. Pokud je zadána jako podřízený element `<serviceCertificate>` elementu, určuje umístění a nastavení ověřování certifikátu X. 509, který se používá k šifrování a dešifrování tokenů. `<certificateReference>`Element je reprezentován <xref:System.ServiceModel.Configuration.CertificateReferenceElement> třídou.
