---
title: '&lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa6bfdf72bd292599867bf7a9571ecd6b408a2c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltidentitygt"></a>&lt;identity&gt;
Prvek identity umožňuje vývojáři klienta zadejte v době návrhu očekávaný identitu služby. V procesu mezi klientem a službou [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastruktury zajišťují, že tyto hodnoty odpovídají hodnotám tohoto elementu identitu očekávanou službu a proto může být ověřen. Další informace najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<systém. ServiceModel >  
\<klient >  
\<koncový bod >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|certificate|Určuje nastavení certifikátu X.509. Tento element je typu <xref:System.ServiceModel.Configuration.CertificateElement>. Obsahuje atribut `encodedValue` tedy řetězec, který určuje hodnotu kódovaný tímto certifikátem.|  
|certificateReference|Určuje nastavení pro ověření certifikátu X.509. Tento element je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Určuje certifikátu X.509. certifikát použitý k ověření služby DNS. Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné identitu.|  
|rsa|Určuje hodnotu pole RSA certifikátu X.509. certifikát použitý k ověření služby klienta. Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné identity|  
|servicePrincipalName|Určuje identitu serveru hlavní název (SPN), což je hlavní název klient používá k jedinečné identifikaci instance služby. Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné hlavní název. Tento element je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Určuje identitu hlavní název (UPN) uživatele, což je typ názvu přihlášení uživatele v síti. Hlavní název uživatele se skládá z názvu objektu uživatele ve službě Active Directory, za nímž následuje použít v symbolu (@) a potom obvykle Domain Name System nadřazené domény. Například Jeff v stromu domény Fabrikam.com může mít hlavní název uživatele [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Tento prvek obsahuje atribut `value` , je řetězec a obsahuje skutečné hlavní název. Tento element je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vlastní >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Určuje vlastní sdílené překladač pro netPeerTcpBinding.|  
|[\<koncový bod >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)|Konfiguruje různé typy koncových bodů.|  
|[\<Issuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Určuje Security Token Service (Služba tokenů zabezpečení) pro federované služby.|  
|[\<issuerMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Určuje koncový bod metadat pro Security Token Service (Služba tokenů zabezpečení) federované služby.|  
|[\<– issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Definuje parametry pro token vydaných v vlastní vazby.|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Určuje místní Security Token Service (STS).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Koncové body: Adresy, vazby a kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
