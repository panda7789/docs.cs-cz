---
title: ICorDebugHandleValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138479"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue – rozhraní

Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dispose – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Uvolňuje popisovač, na který odkazuje tento objekt `ICorDebugHandleValue`, bez explicitního uvolnění ukazatele rozhraní.|  
|[GetHandleType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Získá hodnotu CorDebugHandleType –, která popisuje druh popisovače, na který odkazuje tento `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt `ICorDebugReferenceValue` je po přerušení v provádění laděného kódu neplatný. `ICorDebugHandleValue` udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud není explicitně uvolněn.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
