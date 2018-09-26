---
title: '&lt;Mezipaměti&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: a91a389e53354e4f5b26e1510fc2f025300d65cc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084238"
---
# <a name="ltcachesgt"></a>&lt;Mezipaměti&gt;
Zaregistruje mezipaměti používané pro tokeny relace a rozpoznání opětovného přehrání tokenu.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<ukládá do mezipaměti >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|Registruje mezipaměti relace tokeny služby nebo kolekci obslužné rutiny tokenů zabezpečení.|  
|[\<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|Registruje mezipaměti opětovného přehrání tokenu služby nebo kolekci obslužné rutiny tokenů zabezpečení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identit na úrovni služby.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 A `<caches>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu. Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.  
  
 `<caches>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídy. Jsou reprezentovány nakonfigurovanou mezipamětí <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro uchování relace tokenů zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>). Konfigurace se přebírá ze `ClaimsAwareWebFarm` vzorku.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
