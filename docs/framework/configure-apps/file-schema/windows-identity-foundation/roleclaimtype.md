---
title: '&lt;RoleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 565bf30d334c62c8132c60f411e89f7b260c54f1
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841510"
---
# <a name="ltroleclaimtypegt"></a>&lt;RoleClaimType&gt;
Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužné rutiny tokenů.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
\<samlSecurityTokenRequirement >  
\<roleClaimType >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
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
|value|Řetězec určující identifikátor URI, který představuje typ deklarace identity z deklarací identity pro deklarace typu role.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.|  
  
## <a name="remarks"></a>Poznámky  
 `<roleClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.  
  
## <a name="example"></a>Příklad  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
