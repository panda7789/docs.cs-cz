---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941957"
---
# <a name="audienceuris"></a>\<audienceUris>
Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory předávající strany (RP). Tokeny nebudou přijaty, pokud nejsou vymezeny pro některý z povolených identifikátorů URI cílové skupiny.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<audienceUris>  
  
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
|režim|<xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnota, která určuje, jestli se má omezení cílové skupiny použít u příchozího tokenu. Možné hodnoty jsou "Always", "Never" a "BearerKeyOnly". Výchozí hodnota je "Always". Volitelný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<add value=xs:string>`|Přidá identifikátor URI určený `value` atributem do kolekce audienceUris. `value` Atribut je vyžadován. Identifikátor URI rozlišuje velká a malá písmena.|  
|`<clear>`|Vymaže kolekci audienceUris. Všechny identifikátory jsou z kolekce odebrané.|  
|`<remove value=xs:string>`|Odstraní identifikátor URI určený `value` atributem z kolekce audienceUris. `value` Atribut je vyžadován. Identifikátor URI rozlišuje velká a malá písmena.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je kolekce prázdná. pro `<add>`úpravu `<clear>`kolekce použijte `<remove>` prvky, a. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>objekty <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a používají hodnoty v kolekci identifikátorů URI cílové skupiny ke konfiguraci libovolných povolených omezení <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> identifikátorů URI cílové skupiny v objektech.  
  
 Element je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection>třídou. `<audienceUris>` Jednotlivé identifikátory URI přidané do kolekce jsou reprezentovány <xref:System.IdentityModel.Configuration.AudienceUriElement> třídou.  
  
> [!NOTE]
> Použití `<audienceUris>` prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) bylo zastaralé, ale je stále podporováno pro zpětnou kompatibilitu. Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak nakonfigurovat přijatelné identifikátory URI cílové skupiny pro aplikaci. Tento příklad nakonfiguruje jeden identifikátor URI. Tokeny vymezené pro tento identifikátor URI budou přijaty, ostatní budou odmítnuty.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
