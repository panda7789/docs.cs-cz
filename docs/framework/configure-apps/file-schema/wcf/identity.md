---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: d5d06953c67b90e8367f2c0d01a670a46f487526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925415"
---
# <a name="identity"></a>\<> identity
Prvek identita umožňuje vývojáři klienta zadat v době návrhu očekávanou identitu služby. V procesu handshake mezi klientem a službou infrastruktura Windows Communication Foundation (WCF) zajistí, že identita očekávané služby bude odpovídat hodnotám tohoto prvku, a proto může být ověřena. Další informace najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<> klienta  
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
|certificate|Určuje nastavení certifikátu X. 509. Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateElement>. Obsahuje atribut `encodedValue` , který je řetězec, který určuje hodnotu zakódovanou tímto certifikátem.|  
|certificateReference|Určuje nastavení pro ověřování certifikátu X. 509. Tento prvek je typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Určuje DNS certifikátu X. 509, který se používá k ověření služby. Tento element obsahuje atribut `value` , který je řetězec, a obsahuje skutečnou identitu.|  
|rsa|Určuje hodnotu pole RSA certifikátu X. 509, která se používá k ověření služby klientovi. Tento element obsahuje atribut `value` , který je řetězec, a obsahuje skutečnou identitu.|  
|servicePrincipalName|Určuje identitu hlavního názvu serveru (SPN), což je hlavní název, který klient používá k jednoznačné identifikaci instance služby. Tento prvek obsahuje atribut `value` , který je řetězec, a obsahuje skutečný hlavní název. Tento prvek je typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Určuje identitu hlavního názvu uživatele (UPN), což je typ přihlašovacího jména uživatele v síti. Hlavní název uživatele se skládá z názvu uživatelského objektu používaného ve službě Active Directory, po kterém následuje symbol (\@) a pak obvykle nadřazená doména systému názvů domén. Například Jan ve stromu domény Fabrikam.com může mít hlavní název [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)uživatele (UPN).  Tento prvek obsahuje atribut `value` , který je řetězec, a obsahuje skutečný hlavní název. Tento prvek je typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<custom>](custom.md)|Určuje vlastní překladač rovnocenných uzlů pro netPeerTcpBinding.|  
|[\<endpoint>](endpoint-element.md)|Nakonfiguruje koncové body služby.|  
|[\<koncový bod > \<> klienta](endpoint-of-client.md)|Nakonfiguruje koncové body kanálu.|  
|[\<issuer>](issuer.md)|Určuje službu tokenů zabezpečení (STS) pro federované služby.|  
|[\<issuerMetadata>](issuermetadata.md)|Určuje koncový bod metadat pro službu tokenů zabezpečení (STS) federované služby.|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Definuje parametry pro vydaný token ve vlastní vazbě.|  
|[\<localIssuer>](localissuer.md)|Určuje místní službu tokenů zabezpečení (STS).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Bod Adresy, vazby a kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
