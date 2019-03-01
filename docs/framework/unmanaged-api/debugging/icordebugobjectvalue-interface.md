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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cae8a695ccf313b846c8860309c3461a821fe38
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977211"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue – rozhraní

Podtřída ICorDebugValue"", který představuje hodnotu, která obsahuje objekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Získá ukazatel rozhraní common language runtime (CLR) <xref:System.Type> objektu, který tato `ICorDebugObjectValue` odkazy.|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Není implementováno.|  
|[GetFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Získá ukazatel rozhraní k [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , který představuje hodnotu zadaného pole z dané třídy.|  
|[GetManagedCopy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Zastaralé. Nevolejte tuto metodu.|  
|[GetVirtualMethod – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Není implementováno.|  
|[IsValueClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Získá hodnotu určující, zda objekt odkazovaný tímto objektem `ICorDebugObjectValue` je typ hodnoty.|  
|[SetFromManagedCopy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Zastaralé. Nevolejte tuto metodu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugObjectValue` Zůstává v platnosti, dokud se pokračuje se v laděném procesu.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

