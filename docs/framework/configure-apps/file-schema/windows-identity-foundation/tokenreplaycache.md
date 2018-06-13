---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 79022319944c4042c6f62a7521784b826b90d4ce
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755120"
---
# <a name="lttokenreplaycachegt"></a>&lt;tokenReplayCache&gt;
Zaregistruje mezipaměti opětovného přehrání tokenu se službou nebo kolekci obslužná rutina tokenu zabezpečení.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<ukládá do mezipaměti >  
\<tokenReplayCache >  
  
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
|– typ|Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy. Další informace o tom, jak zadat vlastní `type`, najdete v části [odkazy na vlastní typ].
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ukládá do mezipaměti >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Zaregistruje mezipamětí používaný službou nebo kolekci obslužná rutina tokenu zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Mezipaměť opětovného přehrání tokenu slouží ke zjištění přehraná tokeny. Rozpoznání opětovného přehrání tokenu je povoleno podle [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, který určuje také maximální dobu vypršení platnosti tokenů.  
  
## <a name="example"></a>Příklad  
 Následující kód XML zobrazuje konfiguraci vlastní mezipaměti pro zjišťování přehraná tokeny.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
