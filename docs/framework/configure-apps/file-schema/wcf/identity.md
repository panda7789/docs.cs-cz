---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 0f5eace346fd0ed2c0532fb602585c4593d97291
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756686"
---
# <a name="identity"></a>\<identity>
Prvek identita umožňuje vývojáři klientského programu zadat v době návrhu očekávané identity služby. V procesu metody handshake mezi klientem a službou Windows Communication Foundation (WCF) infrastruktura zajistí, aby identitu shod očekávanou službu hodnoty tohoto elementu a proto mohou být ověřeni. Další informace najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <usePrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|certificate|Určuje nastavení certifikátu X.509. Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateElement>. Obsahuje atribut `encodedValue` , který je řetězec, který určuje hodnotu kódovaný pomocí tohoto certifikátu.|  
|certificateReference|Určuje nastavení pro ověřování certifikátu X.509. Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Určuje certifikát X.509 sloužící k ověření služby DNS. Tento prvek obsahuje atribut `value` , který je řetězec a obsahuje skutečnou identitu.|  
|rsa|Určuje hodnotu pole RSA certifikát X.509 sloužící k ověření služby ke klientovi. Tento prvek obsahuje atribut `value` , který je řetězec a obsahuje skutečnou identitu|  
|servicePrincipalName|Určuje identitu hlavní název (SPN) serveru, který je zadaný hlavní název, který klient používá k jednoznačné identifikaci instance služby. Tento prvek obsahuje atribut `value` , který je řetězec a obsahuje skutečný název instančního objektu. Tento prvek je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Určuje identitu hlavní název (UPN) uživatele, což je název typ přihlášení uživatele v síti. Hlavní název uživatele se skládá z použít ve službě Active Directory, za nímž následuje název objektu uživatele v symbolu (\@) a pak, obvykle v systému názvů domény nadřazené domény. Jan v stromu domény Fabrikam.com může mít například hlavní název uživatele [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Tento prvek obsahuje atribut `value` , který je řetězec a obsahuje skutečný název instančního objektu. Tento prvek je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<custom>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Určuje mechanismus rozpoznávání partnera vlastní pro netPeerTcpBinding.|  
|[\<endpoint>](endpoint-element.md)|Nakonfiguruje koncových bodů služby.|  
|[\<koncový bod > z \<klienta >](endpoint-of-client.md)|Nakonfiguruje kanál koncových bodů.|  
|[\<issuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Určuje Token služba zabezpečení (STS) pro federované služby.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Určuje koncový bod metadat pro Token služba zabezpečení (STS) federované služby.|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Definuje parametry pro vydaný token ve vlastní vazby.|  
|[\<localIssuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Určuje místní tokenů zabezpečení služby (STS).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Koncové body: Adresy, vazby a kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
