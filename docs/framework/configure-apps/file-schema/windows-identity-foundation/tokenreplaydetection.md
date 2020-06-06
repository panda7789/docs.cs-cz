---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251775"
---
# \<tokenReplayDetection>
Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Hodnota, která určuje, zda je povoleno zjišťování opětovného přehrání tokenu; "true" pro povolení detekce opětovného přehrání tokenu.|  
|expirationPeriod|A <xref:System.TimeSpan> Určuje maximální dobu před tím, než vyprší platnost položky a její odebrání z mezipaměti.  Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 `<tokenReplayDetection>`Element lze zadat na úrovni služby pod `<identityConfiguration>` prvkem nebo na úrovni kolekce obslužné rutiny tokenu zabezpečení pod `<securityTokenHandlerConfiguration>` prvkem. Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.  
  
 Typ mezipaměti pro opětovné přehrání tokenu je určen [\<tokenReplayCache>](tokenreplaycache.md) elementem.
