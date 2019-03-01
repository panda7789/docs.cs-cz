---
title: ICorDebugValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2de5d3a208594a03bfdca837e592f53b3da7f0f0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981410"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue – rozhraní
Reprezentuje hodnotu v laděném procesu. Hodnota může být čtení nebo zápis hodnoty.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Tato metoda teď není implementovaná.|  
|[GetAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Získá adresu této `ICorDebugValue` objektu, který se právě laděn.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Získá velikost v bajtech, to `ICorDebugValue` objektu.|  
|[GetType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Získá základní typ tohoto objektu `ICorDebugValue` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí vlastnictví objektu hodnotou je předána, když bude vrácen. Pro odebrání odkazu z objektu po dokončení se pomocí objektu zodpovídá příjemce.  
  
 V závislosti na tom, kde hodnota byla načtena z nemusí zůstat hodnotu platnou po obnovení procesu. Ano, obecně platí, hodnota by se neměly ukládat ve volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:




- [ICorDebugValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
