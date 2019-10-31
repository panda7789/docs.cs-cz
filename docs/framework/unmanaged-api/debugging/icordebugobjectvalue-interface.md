---
title: ICorDebugObjectValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129756"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue – rozhraní

Podtřída "ICorDebugValue", která představuje hodnotu, která obsahuje objekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Získá ukazatel rozhraní modulu CLR (Common Language Runtime) <xref:System.Type> objektu, na který odkazuje tento `ICorDebugObjectValue`.|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Není implementováno.|  
|[GetFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Získá ukazatel rozhraní na [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , který představuje hodnotu zadaného pole zadané třídy.|  
|[GetManagedCopy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Zastaralé. Nevolejte tuto metodu.|  
|[GetVirtualMethod – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Není implementováno.|  
|[IsValueClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Získá hodnotu, která označuje, zda je objekt, na který odkazuje tento `ICorDebugObjectValue` hodnotový typ.|  
|[SetFromManagedCopy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Zastaralé. Nevolejte tuto metodu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugObjectValue` zůstává platný, dokud proces, který se právě ladí, nebude pokračovat.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
