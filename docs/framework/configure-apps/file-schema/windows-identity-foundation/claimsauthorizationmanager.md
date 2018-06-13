---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 06824e20286f8905ad3a8ac9d2b4a30366a6ec10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757369"
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
Zaregistruje Správce autorizací příchozí deklarace identity deklarací identity.  
  
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
|– typ|Vlastního typu, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy. Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Pokud je žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthorizationManager>` element nevyužívá podřízených elementů, ale třídy odvozené od <xref:System.Security.Claims.ClaimsAuthorizationManager> můžete definovat podřízené konfigurační prvky.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identity úrovně služeb.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthorizationManager> třída vždycky povolí příchozí deklarace identity. Pokud žádné `type` zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy, `<claimsAuthorizationManager>` element nemusí provádět žádné podřízené elementy. Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu pro implementaci vlastního chování. Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthorizationManager>` element přepsáním <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů. Schéma definované pro podřízené elementy závisí návrháře třídy.  
  
> [!IMPORTANT]
>  Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třída k poskytování řízení přístupu na základě deklarace identity ve vašem kódu konfiguraci identity, která odkazuje `<federationConfiguration>` element nakonfiguruje Správce autorizací deklarace identity a zásadu, která se používá k zajištění rozhodnutí o autorizaci. Je to ve scénářích, které nejsou pasivní scénáře webového, například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založené na webu. Pokud aplikace není pasivní webové aplikace `<claimsAuthorizationManager>` – element (a jeho podřízených elementů zásad, pokud existuje) konfigurace odkazované identity jsou jenom nastavení použité. Všechna ostatní nastavení se ignorují. Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.  
  
 Nastaví tento element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující kód XML zobrazí správce, který implementuje zásady skládá z dvojice akce prostředku, z nichž každý určuje boolean kombinace deklarace identity, které provést akci na prostředku musí mít žadatele o konfiguraci pro autorizaci deklarací identity. Kód, který implementuje Správce autorizací deklarace identity, která je schopen pomocí těchto zásad najdete v `ClaimsBasedAuthorization` ukázka.  
  
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
