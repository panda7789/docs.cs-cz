---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152629"
---
# <a name="samlsecuritytokenrequirement"></a>\<> samlSecurityTokenRequirement
Poskytuje konfiguraci <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> pro <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu, třídu nebo odvozenou třídu jedné z těchto tříd. Reprezentované třídou. <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>samlSecurityTokenRequirement**  
  
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
|mapToWindows|Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního název uživatele. Výchozí hodnota je "false".|  
|issuerCertificateRevocationMode|Hodnota, <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> která určuje režim odvolání, který má být pro certifikát X.509 používán. Výchozí hodnota je "Online".|  
|issuerCertificateValidationMode|Hodnota, <xref:System.ServiceModel.Security.X509CertificateValidationMode> která určuje režim ověření pro certifikát X.509. Výchozí hodnota je "PeerOrChainTrust".|  
|issuerCertificateTrustedStoreLocation|Hodnota, <xref:System.Security.Cryptography.X509Certificates.StoreLocation> která určuje úložiště certifikátů X.509. Výchozí hodnota je "LocalMachine".|  
|emitentCertifikátValidator|Vlastní typ, který <xref:System.IdentityModel.Selectors.X509CertificateValidator>je odvozen od . Pokud `issuerCertificateValidationMode` je atribut "Vlastní", instance tohoto typu se používá pro ověření certifikátu vystavitho.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<názevClaimType>](nameclaimtype.md)|Nastaví typ deklarace, <xref:System.Security.Principal.IIdentity.Name%2A> která určuje vlastnost.|  
|[\<roleClaimType>](roleclaimtype.md)|Určuje typ deklarace identity, který definuje deklarace typu role v kolekci objektů vrácených <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add.md)|Přidá zadanou obslužnou rutinu tokenu do kolekce obslužné rutiny tokenu.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<samlSecurityTokenRequirement>` je reprezentován <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou v objektovém modelu `SamlSecurityTokenRequirement` a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> slouží <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>ke konfiguraci vlastnosti na nebo .  
  
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
