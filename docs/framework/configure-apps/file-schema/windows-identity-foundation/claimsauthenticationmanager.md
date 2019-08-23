---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941819"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthenticationManager>  
  
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
|– typ|Určuje vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy. Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].|  
  
### <a name="child-elements"></a>Podřízené elementy  
 `type` Pokud neexistuje žádný atribut, nebo <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Pokud atribut `<claimsAuthenticationManager>` odkazuje na třídu, element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> mohou však definovat podřízené prvky konfigurace.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy vychází z příchozích deklarací identity. Pokud není `type` zadán žádný atribut nebo `type` Pokud atribut `<claimsAuthenticationManager>` specifikuje <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, element nepřijímá podřízené prvky. Můžete určit `type` atribut pro registraci typu odvozeného <xref:System.Security.Claims.ClaimsAuthenticationManager> od třídy pro implementaci vlastního chování. Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthenticationManager>` prvku <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> přepsáním metody pro zpracování těchto elementů. Schéma definované pro podřízené prvky je až do návrháře třídy.  
  
 `<claimsAuthenticationManager>` Prvek<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> nastaví vlastnost.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
