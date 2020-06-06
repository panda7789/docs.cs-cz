---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251788"
---
# \<tokenReplayCache>
Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|typ|Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy. Další informace o tom, jak zadat vlastní `type` , naleznete v tématu [odkazy na vlastní typ].
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<caches>](caches.md)|Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Mezipaměť pro opětovné přehrání tokenu se používá ke zjišťování předaných tokenů. Detekce opětovného přehrání tokenu je povolena [\<tokenReplayDetection>](tokenreplaydetection.md) prvkem, který také určuje maximální dobu vypršení platnosti tokenů.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro detekci přehráných tokenů.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
