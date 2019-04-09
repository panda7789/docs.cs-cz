---
title: ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c8befed8bc810344b2a3344212a6a4a854300e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164655"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
Vytvoří nový unwinder zásobníku, který se spustí uvolnění z počáteční kontextu, (což není nutně listu vlákno).  
  
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
  
## <a name="parameters"></a>Parametry  
 nativeThreadID  
 [in] ID nativní vlákna vlákna, jehož zásobník má být oddělen.  
  
 contextFlags  
 [in] Příznaky, které určují, které části kontextu jsou definovány v `initialContext`.  
  
 cbContext  
 [in] Velikost `initialContext`.  
  
 initialContext  
 [in] Data v kontextu.  
  
 ppUnwinder  
 [out] Ukazatel na adresu objektu rozhraní ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` v případě úspěšného ověření. Jakýkoli jiný `HRESULT` označuje chybu. Všechny neúspěšné `HRESULT` přijatých mscordbi se považuje za závažné a způsobí, že [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody k vrácení `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
