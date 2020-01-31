---
title: ICorDebugGuidToTypeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 2663e5604cdd55472cc148b2d2b38599df81f11e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794443"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum – rozhraní
Poskytuje enumerátor definující mapování mezi sadou identifikátorů GUID a jejich odpovídajícími typy, které jsou reprezentovány instancemi ICorDebugType. Toto rozhraní dědí metody z rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum –:: Next](icordebugguidtotypeenum-next-method.md)|Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt rozhraní `ICorDebugGuidToTypeEnum` lze načíst voláním metody [ICorDebugAppDomain3:: GetCachedWinRTTypes –](icordebugappdomain3-getcachedwinrttypes-method.md) . Ladicí program může zavolat metodu [Next](icordebugguidtotypeenum-next-method.md) tohoto rozhraní k načtení objektů [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , které představují mapování spravovaných typů prostředí Windows Runtimeů načtených v doméně aplikace používané pro volání metody [ICorDebugAppDomain3:: GetCachedWinRTTypes –](icordebugappdomain3-getcachedwinrttypes-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
