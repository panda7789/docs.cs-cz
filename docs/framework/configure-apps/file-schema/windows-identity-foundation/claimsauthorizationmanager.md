---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: a745339cffdada56a9b7f27f3f879b9d437c2da2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195551"
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
Zaregistruje Správce autorizací deklarace identity pro příchozí deklarace identity.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy. Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Pokud není žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthorizationManager>` element nevyužívá podřízených elementů, ale třídy odvozené z <xref:System.Security.Claims.ClaimsAuthorizationManager> můžete definovat podřízené prvky konfigurace.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identit na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování zajišťována <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy vždy povolí příchozí deklarace identity. Pokud ne `type` je zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy, `<claimsAuthorizationManager>` element nepřijímá podřízené prvky. Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu pro implementaci vlastního chování. Odvozené třídy může podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthorizationManager>` element tak, že přepíšete <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů. Schéma definice pro podřízené prvky je až návrháře třídy.  
  
> [!IMPORTANT]
>  Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, konfigurace identity, na který odkazuje `<federationConfiguration>` element nakonfiguruje Správce autorizací deklarace identity a zásadu, která se využívá k Prognózování rozhodování o autorizaci. To platí dokonce i ve scénářích, které nejsou pasivní scénáře pro webové, například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založena na Web. Pokud aplikace není pasivní webové aplikace `<claimsAuthorizationManager>` – element (a jeho podřízených elementů zásad, pokud jsou k dispozici) konfigurace odkazované identity jsou jenom nastavení, která použijí. Všechna ostatní nastavení se ignorují. Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 Tento prvek nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující kód XML je znázorněna konfigurace pro autorizaci deklarací identity Manageru, který implementuje zásady skládá z dvojice akce prostředku, z nichž každý Určuje logický kombinace deklarací, které musí mít žadatele k provedení akce na prostředku. Kód, který implementuje Správce autorizací deklarace identity nemůže použít tyto zásady najdete v `ClaimsBasedAuthorization` vzorku.  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
