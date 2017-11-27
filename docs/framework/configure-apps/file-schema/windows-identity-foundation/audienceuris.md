---
title: '&lt;audienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3ce884c19d205df4727dcce96ffdf34144ff1dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltaudienceurisgt"></a>&lt;audienceUris&gt;
Určuje sadu identifikátorů URI, které jsou přípustné identifikátory předávající strany (RP). Tokeny nebudou přijímány, pokud jsou určené pro jednu z povolená cílová skupina identifikátory URI.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<audienceUris >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|<xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnotu, která určuje, zda má být použita omezení cílovou skupinu do příchozího tokenu. Možné hodnoty jsou "Vždy", "Nikdy" a "BearerKeyOnly". Výchozí hodnota je "Vždy". Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<add value=xs:string>`|Přidá identifikátor URI určeného `value` atribut audienceUris kolekce. `value` Atribut je vyžadován. Identifikátor URI je malá a velká písmena.|  
|`<clear>`|Vymaže kolekci audienceUris. Všechny identifikátory se odeberou z kolekce.|  
|`<remove value=xs:string>`|Odebere identifikátor URI určeného `value` atribut z kolekce audienceUris. `value` Atribut je vyžadován. Identifikátor URI je malá a velká písmena.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je kolekce prázdná. použít `<add>`, `<clear>`, a `<remove>` elementy upravit kolekci. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objekty použijte hodnoty v cílové skupině URI kolekce ke konfiguraci libovolné povolené cílové skupiny omezení URI v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekty.  
  
 `<audienceUris>` Element je reprezentována <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídy. Identifikátor jednotlivých URI přidaných do kolekce je reprezentována <xref:System.IdentityModel.Configuration.AudienceUriElement> třídy.  
  
> [!NOTE]
>  Použití `<audienceUris>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu. Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak nakonfigurovat přijatelné cílovou skupinu identifikátory URI, pro aplikaci. Tento příklad konfiguruje jeden identifikátor URI. Přijme tokeny, které jsou určené pro tento identifikátor URI, všechny ostatní budou odmítnuty.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
