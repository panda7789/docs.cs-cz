---
title: ICorDebugEnum Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4659bbc9c2e3c71a6cf85e51a06bee4f789356b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugenum-interface1"></a>ICorDebugEnum Interface1
Slouží jako abstraktní základní rozhraní pro výčty, které jsou používány ladění aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|Vytvoří kopii tohoto `ICorDebugEnum` objektu.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|Získá počet položek ve výčtu.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|Posune kurzor na začátek výčtu.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|Přesune kurzor dál o zadaný počet položek ve výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 Následující výčty odvozena od `ICorDebugEnum`:  
  
-   "ICorDebugAppDomainEnum"  
  
-   "ICorDebugAssemblyEnum"  
  
-   [ICorDebugBlockingObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   "ICorDebugBreakpointEnum"  
  
-   "ICorDebugChainEnum"  
  
-   Icordebugcodeenum "–"  
  
-   "ICorDebugErrorInfoEnum"  
  
-   [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   "ICorDebugFrameEnum"  
  
-   [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   "ICorDebugModuleEnum"  
  
-   "ICorDebugObjectEnum"  
  
-   "ICorDebugProcessEnum"  
  
-   "ICorDebugStepperEnum"  
  
-   "ICorDebugThreadEnum"  
  
-   "ICorDebugTypeEnum"  
  
-   "ICorDebugValueEnum"  
  
-   [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
