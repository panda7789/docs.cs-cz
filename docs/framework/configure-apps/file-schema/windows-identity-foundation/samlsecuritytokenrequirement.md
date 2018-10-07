---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: c9856dae971691baf9dabe845bdecae90cbc8aa5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847295"
---
# <a name="ltsamlsecuritytokenrequirementgt"></a>&lt;samlSecurityTokenRequirement&gt;
Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd. Reprezentována <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídy.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
\<samlSecurityTokenRequirement >  
  
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
|mapToWindows|Určuje, zda obslužná rutina tokenů mělo mapovat ověřování tokenu účet Windows s použitím příchozí deklarace identity UPN. Výchozí hodnota je "false".|  
|issuerCertificateRevocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509. Výchozí hodnota je "Online".|  
|issuerCertificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509. Výchozí hodnota je "PeerOrChainTrust".|  
|issuerCertificateTrustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509. Výchozí hodnota je "LocalMachine".|  
|issuerCertificateValidator|Vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Pokud `issuerCertificateValidationMode` atribut je "Vlastní", instance tohoto typu se používá k ověření certifikátu vystavitele.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<nameClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|Nastaví typ deklarace identity, která určuje, <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.|  
|[\<roleClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužné rutiny tokenů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 `<samlSecurityTokenRequirement>` Element je reprezentována <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídy v objektovém modelu a slouží ke konfiguraci `SamlSecurityTokenRequirement` vlastnosti <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
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
