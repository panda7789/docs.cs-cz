---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
Vytvoří nový unwinder zásobníku, která se spouští unwinding z kontextu počáteční (který není nutně listu vlákna).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 nativeThreadID  
 [v] Nativní vlákno ID vlákna, jejichž zásobník má být oddělen.  
  
 contextFlags  
 [v] Příznaky, které určují, jaké části kontextu jsou definovány v `initialContext`.  
  
 cbContext  
 [v] Velikost `initialContext`.  
  
 initialContext  
 [v] Data v kontextu.  
  
 ppUnwinder  
 [out] Ukazatel na adresu objekt rozhraní ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud bylo úspěšné. Žádné jiné `HRESULT` označuje selhání. Všechny selhání `HRESULT` přijatých mscordbi považuje za závažné a způsobí, že [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody vrátit `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
