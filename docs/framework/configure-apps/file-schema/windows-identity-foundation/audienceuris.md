---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216643"
---
# <a name="ltaudienceurisgt"></a>&lt;audienceUris&gt;
Určuje sadu identifikátorů URI, které jsou přípustné identifikátory předávající strany (RP). Tokeny nebudou přijímány, pokud jsou určená pro jeden z identifikátorů URI povolená cílová skupina.  
  
 \<system.identityModel>  
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
|režim|<xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnota, která určuje, zda má být použita omezení cílovou skupinu na příchozí token. Možné hodnoty jsou "Always", "Nikdy" a "BearerKeyOnly". Výchozí hodnota je "Always". Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<add value=xs:string>`|Přidá určený identifikátor URI `value` atribut audienceUris kolekce. `value` Atribut je vyžadován. Identifikátor URI je velká a malá písmena.|  
|`<clear>`|Vymaže kolekci audienceUris. Všechny identifikátory se odeberou z kolekce.|  
|`<remove value=xs:string>`|Odstraní určený identifikátor URI `value` atribut z kolekce audienceUris. `value` Atribut je vyžadován. Identifikátor URI je velká a malá písmena.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je kolekce prázdná. použít `<add>`, `<clear>`, a `<remove>` prvků, které se změnit kolekci. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objektů použijte hodnoty v cílové skupině identifikátor URI kolekce ke konfiguraci libovolné povolené cílové skupiny omezení identifikátor URI v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekty.  
  
 `<audienceUris>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídy. Je reprezentován jednotlivé identifikátor URI přidat do kolekce <xref:System.IdentityModel.Configuration.AudienceUriElement> třídy.  
  
> [!NOTE]
>  Použití `<audienceUris>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována. Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak nakonfigurovat přijatelné cílovou skupinu identifikátory URI pro aplikaci. Tento příklad konfiguruje jednoho identifikátoru URI. Přijme tokeny oboru pro tento identifikátor URI, všechny ostatní budou odmítnuty.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
