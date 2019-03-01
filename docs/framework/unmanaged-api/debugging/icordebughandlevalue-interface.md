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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dddc1665dff5c1a0629d25aa99066ce6eeca94a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981436"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue – rozhraní

Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dispose – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Uvolní popisovač odkazovaná tímto objektem `ICorDebugHandleValue` objektu bez explicitně ukazatel rozhraní.|  
|[GetHandleType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Získá hodnotu cordebughandletype –, který popisuje typ, který odkazuje tento popisovač `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugReferenceValue` Objektu je ukončit platnost přerušením provádění laděného kódu. `ICorDebugHandleValue` Udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud je explicitně uvolněn.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
