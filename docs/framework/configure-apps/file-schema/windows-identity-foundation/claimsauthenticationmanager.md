---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252094"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Zaregistruje Správce ověřování deklarací identity pro příchozí deklarace identity.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Komponenty ClaimsAuthenticationManager >**  
  
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
