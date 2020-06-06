---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252165"
---
# \<caches>
Registruje mezipaměti používané pro tokeny relací a detekci opětovného přehrání tokenu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|Registruje mezipaměť pro tokeny relace se službou nebo kolekcí obslužné rutiny tokenu zabezpečení.|  
|[\<tokenReplayCache>](tokenreplaycache.md)|Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 `<caches>`Element lze zadat na úrovni služby pod `<identityConfiguration>` prvkem nebo na úrovni kolekce obslužné rutiny tokenu zabezpečení pod `<securityTokenHandlerConfiguration>` prvkem. Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.  
  
 `<caches>`Element je reprezentován <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídou. Nakonfigurované mezipaměti jsou reprezentovány <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídou.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro tokeny zabezpečení relace ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ). Konfigurace je pořízena z `ClaimsAwareWebFarm` ukázky.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
