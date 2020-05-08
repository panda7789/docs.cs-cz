---
title: ICorDebugEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: 7575be3f5074243b251c80b8dd5bdbb12e5d50fd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976320"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum – rozhraní

Slouží jako abstraktní základní rozhraní pro enumerátory, které používá ladicí aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](icordebugenum-clone-method.md)|Vytvoří kopii tohoto `ICorDebugEnum` objektu.|  
|[GetCount – metoda](icordebugenum-getcount-method.md)|Získá počet položek ve výčtu.|  
|[Reset – metoda](icordebugenum-reset-method.md)|Přesune kurzor na začátek výčtu.|  
|[Skip – metoda](icordebugenum-skip-method.md)|Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.|  
  
## <a name="remarks"></a>Poznámky  
 Následující enumerátory jsou odvozeny `ICorDebugEnum`z:  
  
- ICorDebugAppDomainEnum  
  
- ICorDebugAssemblyEnum  
  
- [ICorDebugBlockingObjectEnum –](icordebugblockingobjectenum-interface.md)  
  
- ICorDebugBreakpointEnum  
  
- ICorDebugChainEnum  
  
- ICorDebugCodeEnum  
  
- ICorDebugErrorInfoEnum  
  
- [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)  
  
- ICorDebugFrameEnum  
  
- [ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md)  
  
- [ICorDebugGuidToTypeEnum –](icordebugguidtotypeenum-interface.md)  
  
- [ICorDebugHeapEnum –](icordebugheapenum-interface.md)  
  
- [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md)  
  
- ICorDebugModuleEnum  
  
- ICorDebugObjectEnum  
  
- ICorDebugProcessEnum  
  
- ICorDebugStepperEnum  
  
- ICorDebugThreadEnum  
  
- ICorDebugTypeEnum  
  
- ICorDebugValueEnum  
  
- [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
