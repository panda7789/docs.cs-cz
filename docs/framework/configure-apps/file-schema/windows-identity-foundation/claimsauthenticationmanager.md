---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152746"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Registruje správce ověřování deklarací identity pro příchozí deklarace identity.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|type|Určuje vlastní typ, který je <xref:System.Security.Claims.ClaimsAuthenticationManager> odvozen od třídy. Další informace o tom, `type` jak zadat atribut, naleznete v tématu [Vlastní odkazy typu].|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Pokud neexistuje `type` žádný atribut nebo `type` pokud atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> odkazuje `<claimsAuthenticationManager>` na třídu, prvek nepřijímá podřízené prvky; třídy odvozené <xref:System.Security.Claims.ClaimsAuthenticationManager> z však můžete definovat podřízené konfigurační prvky.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<identityKonfigurace>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy odráží příchozí deklarace identity. Pokud `type` není zadán žádný `type` atribut nebo <xref:System.Security.Claims.ClaimsAuthenticationManager> pokud atribut `<claimsAuthenticationManager>` určuje třídu, prvek nepřevezme podřízené prvky. Můžete zadat `type` atribut pro registraci typu <xref:System.Security.Claims.ClaimsAuthenticationManager> odvozeného od třídy k implementaci vlastního chování. Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthenticationManager>` prvku přepsáním <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody zpracování těchto prvků. Schéma definované pro podřízené prvky je na návrháři třídy.  
  
 Element `<claimsAuthenticationManager>` nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
