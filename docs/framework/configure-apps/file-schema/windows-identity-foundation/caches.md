---
title: '&lt;Mezipaměti&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a9766b826eb7a708b4b4e99b6bd984f9fc76812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755211"
---
# <a name="ltcachesgt"></a>&lt;Mezipaměti&gt;
Zaregistruje mezipamětí použít pro tokeny relace a rozpoznání opětovného přehrání tokenu.  
  
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
|[\<sessionSecurityTokenCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|Zaregistruje mezipaměti pro tokeny relaci se službou nebo kolekci obslužná rutina tokenu zabezpečení.|  
|[\<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|Zaregistruje mezipaměti opětovného přehrání tokenu se službou nebo kolekci obslužná rutina tokenu zabezpečení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identity úrovně služeb.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.|  
  
## <a name="remarks"></a>Poznámky  
 A `<caches>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu. Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.  
  
 `<caches>` Element je reprezentována <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> třídy. Nakonfigurovanou mezipamětí jsou reprezentované pomocí <xref:System.IdentityModel.Configuration.IdentityModelCaches> třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro uchování relace tokeny zabezpečení (<xref:System.IdentityModel.Tokens.SessionSecurityToken>). Konfigurace jsou převzaty z `ClaimsAwareWebFarm` ukázka.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
