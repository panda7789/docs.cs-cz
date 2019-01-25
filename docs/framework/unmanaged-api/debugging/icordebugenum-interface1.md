---
title: ICorDebugEnum – rozhraní 1
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
ms.openlocfilehash: 97080f7d850e67d635f9a65ee85ad3ddddbb244d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732749"
---
# <a name="icordebugenum-interface1"></a>ICorDebugEnum – rozhraní 1
Slouží jako abstraktní základní rozhraní pro enumerátory, které jsou používány ladění aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|Vytvoří kopii tohoto `ICorDebugEnum` objektu.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|Získá počet položek ve výčtu.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|Přesune kurzor na začátek výčtu.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|Přesune kurzor vpřed o zadaný počet položek ve výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 Následující výčty jsou odvozeny z `ICorDebugEnum`:  
  
-   "ICorDebugAppDomainEnum"  
  
-   Icordebugassemblyenum "–"  
  
-   [Icordebugblockingobjectenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   Icordebugbreakpointenum "–"  
  
-   Icordebugchainenum "–"  
  
-   Icordebugcodeenum "–"  
  
-   Icordebugerrorinfoenum "–"  
  
-   [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   Icordebugframeenum "–"  
  
-   [Icordebuggcreferenceenum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [Icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [Icordebugheapsegmentenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   Icordebugmoduleenum "–"  
  
-   Icordebugobjectenum "–"  
  
-   Icordebugprocessenum "–"  
  
-   Icordebugstepperenum "–"  
  
-   Icordebugthreadenum "–"  
  
-   Icordebugtypeenum "–"  
  
-   Icordebugvalueenum "–"  
  
-   [Icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
