---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252087"
---
# \<claimsAuthorizationManager>
Registruje Správce autorizací deklarací identity pro příchozí deklarace identity.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
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
|typ|Vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy. Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Pokud neexistuje žádný `type` atribut, nebo pokud `type` atribut odkazuje na <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, `<claimsAuthorizationManager>` element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthorizationManager> mohou však definovat podřízené prvky konfigurace.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy vždy autorizuje příchozí deklarace identity. Pokud není `type` zadán žádný atribut nebo pokud `type` atribut specifikuje <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu, `<claimsAuthorizationManager>` element nepřijímá podřízené prvky. Můžete určit `type` atribut pro registraci typu odvozeného od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy pro implementaci vlastního chování. Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthorizationManager>` prvku přepsáním <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metody pro zpracování těchto elementů. Schéma definované pro podřízené prvky je až do návrháře třídy.  
  
> [!IMPORTANT]
> Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu, konfigurace identity, na kterou se odkazuje element, `<federationConfiguration>` konfiguruje správce autorizací deklarací identity a zásadu, která se používá k rozhodování o autorizaci. To platí i ve scénářích, které nejsou pasivními webovými scénáři, například v aplikacích Windows Communication Foundation (WCF) nebo v aplikaci, která není založená na webu. Pokud aplikace není pasivní webovou aplikací, použije se pro daný `<claimsAuthorizationManager>` prvek (a jeho podřízené prvky zásad, pokud jsou k dispozici) odkazovaná konfigurace identity pouze nastavení. Všechna ostatní nastavení se ignorují. Další informace naleznete v tématu [\<federationConfiguration>](federationconfiguration.md) elementu.  
  
 Tento prvek nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje konfiguraci pro Správce autorizací deklarací identity, která implementuje zásady složené z párů prostředků a akcí, každý z nich určuje logické kombinace deklarací identity, které musí žadatel provést k provedení akce na prostředku. Kód, který implementuje Správce autorizací deklarací identity, který je schopný použít tuto zásadu, najdete v `ClaimsBasedAuthorization` ukázce.  
  
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
