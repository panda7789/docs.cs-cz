---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252173"
---
# \<audienceUris>
Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory předávající strany (RP). Tokeny nebudou přijaty, pokud nejsou vymezeny pro některý z povolených identifikátorů URI cílové skupiny.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
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
|režim|<xref:System.IdentityModel.Selectors.AudienceUriMode>Hodnota, která určuje, jestli se má omezení cílové skupiny použít u příchozího tokenu. Možné hodnoty jsou "Always", "Never" a "BearerKeyOnly". Výchozí hodnota je "Always". Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`<add value=xs:string>`|Přidá identifikátor URI určený `value` atributem do kolekce audienceUris. `value` Atribut je vyžadován. Identifikátor URI rozlišuje velká a malá písmena.|  
|`<clear>`|Vymaže kolekci audienceUris. Všechny identifikátory jsou z kolekce odebrané.|  
|`<remove value=xs:string>`|Odstraní identifikátor URI určený `value` atributem z kolekce audienceUris. `value` Atribut je vyžadován. Identifikátor URI rozlišuje velká a malá písmena.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je kolekce prázdná. `<add>` `<clear>` `<remove>` pro úpravu kolekce použijte prvky, a. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler><xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>objekty a používají hodnoty v kolekci identifikátorů URI cílové skupiny ke konfiguraci libovolných povolených omezení identifikátorů URI cílové skupiny v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objektech.  
  
 `<audienceUris>`Element je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídou. Jednotlivé identifikátory URI přidané do kolekce jsou reprezentovány <xref:System.IdentityModel.Configuration.AudienceUriElement> třídou.  
  
> [!NOTE]
> Použití `<audienceUris>` prvku jako podřízeného prvku [\<identityConfiguration>](identityconfiguration.md) elementu je zastaralé, ale je stále podporováno z důvodu zpětné kompatibility. Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje, jak nakonfigurovat přijatelné identifikátory URI cílové skupiny pro aplikaci. Tento příklad nakonfiguruje jeden identifikátor URI. Tokeny vymezené pro tento identifikátor URI budou přijaty, ostatní budou odmítnuty.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
