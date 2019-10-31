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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138535"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum – rozhraní
Poskytuje enumerátor definující mapování mezi sadou identifikátorů GUID a jejich odpovídajícími typy, které jsou reprezentovány instancemi ICorDebugType. Toto rozhraní dědí metody z rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum –:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt rozhraní `ICorDebugGuidToTypeEnum` lze načíst voláním metody [ICorDebugAppDomain3:: GetCachedWinRTTypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) . Ladicí program může zavolat [následující](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodu rozhraní k načtení objektů [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , které představují mapování spravovaných typů prostředí Windows Runtimeů načtených v doméně aplikace používané pro volání [ ICorDebugAppDomain3:: GetCachedWinRTTypes – –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metoda  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
