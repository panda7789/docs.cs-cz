---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755237"
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;claimsAuthenticationManager&gt;
Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<claimsAuthenticationManager >  
  
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
|– typ|Určuje vlastního typu, který je odvozen od <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy. Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na vlastní typ].|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Pokud je žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nevyužívá podřízených elementů, ale třídy odvozené od <xref:System.Security.Claims.ClaimsAuthenticationManager> můžete definovat podřízené konfigurační prvky.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identity úrovně služeb.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthenticationManager> třída vrátí příchozí deklarace identity. Pokud žádné `type` zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nemusí provádět žádné podřízené elementy. Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu pro implementaci vlastního chování. Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthenticationManager>` element přepsáním <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů. Schéma definované pro podřízené elementy závisí návrháře třídy.  
  
 `<claimsAuthenticationManager>` Nastaví element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
