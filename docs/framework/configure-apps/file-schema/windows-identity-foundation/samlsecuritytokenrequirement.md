---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251893"
---
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityTokenRequirement>
Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd. Reprezentované <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|mapToWindows|Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního názvu uživatele (UPN). Výchozí hodnota je false (NEPRAVDA).|  
|issuerCertificateRevocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509. Výchozí hodnota je "online".|  
|issuerCertificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509. Výchozí hodnota je "PeerOrChainTrust".|  
|issuerCertificateTrustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje úložiště certifikátů X. 509. Výchozí hodnota je "LocalMachine".|  
|issuerCertificateValidator|Vlastní typ, který je odvozen z <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Pokud je `issuerCertificateValidationMode` atribut "Custom", instance tohoto typu se používá pro ověření certifikátu vystavitele.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.|  
|[\<roleClaimType>](roleclaimtype.md)|Určuje typ deklarace identity, který definuje deklarace typu role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](add.md)|Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Element je reprezentován třídou v objektovém modelu a slouží ke konfiguraci vlastnosti v nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>. `<samlSecurityTokenRequirement>`  
  
## <a name="example"></a>Příklad  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
