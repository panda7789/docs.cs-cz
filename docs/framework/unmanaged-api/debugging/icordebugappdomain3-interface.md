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
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025894"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 – rozhraní
Poskytuje metody pro načtení informací o spravované reprezentace typů prostředí Windows Runtime aktuálně načtené v doméně aplikace. Toto rozhraní je rozšířením ICorDebugAppDomain a icordebugappdomain2 – rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Získá enumerátor pro všechny typy v mezipaměti prostředí Windows Runtime.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Získá enumerátor pro uložené v mezipaměti typy Windows Runtime v doméně aplikace podle jejich identifikátorů rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je určen pro použití pomocí ladicího programu ve spojení s voláním funkce vyhodnocení `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Metoda načte identifikátory rozhraní nepodporuje objekt prostředí Windows Runtime serveru, se může ladicí program je namapovat na spravované typy, které odpovídají těchto rozhraní pomocí metody definované v tomto rozhraní.  
  
 Pokud chcete načíst instanci tohoto rozhraní, spusťte `QueryInterface` instance ICorDebugAppDomain nebo icordebugappdomain2 – rozhraní.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
