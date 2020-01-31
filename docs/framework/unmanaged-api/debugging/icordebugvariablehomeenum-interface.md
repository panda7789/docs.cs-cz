---
title: ICorDebugVariableHomeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790948"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum – rozhraní
Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icordebugvariablehomeenum-next-method.md)|Získá zadaný počet instancí [ICorDebugVariableHome](icordebugvariablehome-interface.md) , které obsahují informace o místních proměnných a argumentech ve funkci.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugVariableHomeEnum` implementuje rozhraní ICorDebugEnum.  
  
 Instance `ICorDebugVariableHomeEnum` se naplní instancemi [ICorDebugVariableHome](icordebugvariablehome-interface.md) voláním metody [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) . Každá instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) v kolekci představuje místní proměnnou nebo argument ve funkci. Objekty [ICorDebugVariableHome](icordebugvariablehome-interface.md) v kolekci lze vyčíslit voláním metody [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugVariableHome – rozhraní](icordebugvariablehome-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
