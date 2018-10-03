---
title: '&lt;komponenty claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 0ec7e44363f87e54eae97b70352f520fe87540be
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032289"
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;komponenty claimsAuthenticationManager&gt;
Zaregistruje manažera ověřování deklarací identity pro příchozí deklarace identity.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<komponenty claimsAuthenticationManager >  
  
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
|– typ|Určuje, která je odvozena z vlastního typu <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy. Další informace o tom, jak zadat `type` atributu naleznete v tématu [vlastní typ reference].|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Pokud není žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nevyužívá podřízených elementů, ale třídy odvozené z <xref:System.Security.Claims.ClaimsAuthenticationManager> můžete definovat podřízené prvky konfigurace.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identit na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí chování zajišťována <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy vypisuje příchozí deklarace identity. Pokud ne `type` je zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthenticationManager>` element nepřijímá podřízené prvky. Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu pro implementaci vlastního chování. Odvozené třídy může podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthenticationManager>` element tak, že přepíšete <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů. Schéma definice pro podřízené prvky je až návrháře třídy.  
  
 `<claimsAuthenticationManager>` Nastaví element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
