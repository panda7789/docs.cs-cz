---
title: ICorDebugAppDomain3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ade4c88f4431dd6db636ea2581bdb936ac8d8e5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538008"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 – rozhraní
Poskytuje metody pro načtení informací o spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy aktuálně načtené v doméně aplikace. Toto rozhraní je rozšířením ICorDebugAppDomain a icordebugappdomain2 – rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Získá enumerátor pro všechny uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Získá enumerátor pro uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v doméně aplikace podle jejich identifikátorů rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je určen pro použití pomocí ladicího programu ve spojení s voláním funkce vyhodnocení `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Když metoda načte identifikátory rozhraní nepodporuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objekt serveru, ladicí program může používat metody definované v tomto rozhraní pro mapování na spravované typy, které odpovídají těchto rozhraní.  
  
 Pokud chcete načíst instanci tohoto rozhraní, spusťte `QueryInterface` instance ICorDebugAppDomain nebo icordebugappdomain2 – rozhraní.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
