---
title: ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 9fc4facda6253d0c68dcf89b2a1b06e639734efe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788853"
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
 `S_OK`, pokud bylo úspěšné. Všechny ostatní `HRESULT` označují selhání. Jakákoli neúspěšná `HRESULT` přijatá nástrojem mscordbi se považuje za závažnou a způsobí, že metody [ICorDebug](icordebug-interface.md) vrátí `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget2 – rozhraní](icordebugdatatarget2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
