---
title: ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: f9a9038bd0d268e09d8518fa50534a9959b456de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122189"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a>Parametry  
 nativeThreadID  
 pro ID nativního vlákna vlákna, jehož zásobník má být oddělitelné.  
  
 contextFlags  
 pro Příznaky, které určují, které části kontextu jsou definovány v `initialContext`.  
  
 cbContext  
 pro Velikost `initialContext`.  
  
 initialContext  
 pro Data v kontextu.  
  
 ppUnwinder  
 mimo Ukazatel na adresu objektu rozhraní ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud bylo úspěšné. Všechny ostatní `HRESULT` označují selhání. Jakákoli neúspěšná `HRESULT` přijatá nástrojem mscordbi se považuje za závažnou a způsobí, že metody [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) vrátí `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
