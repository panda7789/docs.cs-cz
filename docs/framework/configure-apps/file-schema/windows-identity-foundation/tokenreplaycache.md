---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e43e79416ddb8862cbc6e52d9d449a02b123af83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttokenreplaycachegt"></a>&lt;tokenReplayCache&gt;
Zaregistruje mezipaměti opětovného přehrání tokenu se službou nebo kolekci obslužná rutina tokenu zabezpečení.  
  
 \<system.identityModel >  
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
