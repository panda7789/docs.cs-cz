---
title: ICorDebugVirtualUnwinder::GetContext – metoda
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3125fd5081e68237714bcb10f760b73ce7509f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119220"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext – metoda
Získá aktuální kontext tohoto unwinder.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `contextFlags`  
 [in] Příznaky, které určují, které části kontext, který má vrátit (definované v souboru WinNT.h).  
  
 `cbContextBuf`  
 [in] Počet bajtů v `contextBuf`.  
  
 `contextSize`  
 [out] Ukazatel na počet bajtů zapsaný ve skutečnosti na `contextBuf`.  
  
 `contextBuf`  
 [out] Bajtové pole obsahující aktuální kontext tohoto unwinder.  
  
## <a name="return-value"></a>Návratová hodnota  
 Žádné služeb při selhání přijme mscordbi hodnotu HRESULT je považovat za fatální a způsobí, že icordebug – rozhraní API vrátit `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
 Nastavit počáteční hodnotu `contextBuf` argument do vyrovnávací paměti kontextu vrácená voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
 Protože odvíjení může pouze obnovení část registrů, jako je například stálé zaregistruje pouze, kontext nemusí přesně odpovídat stav registrace při volání metody skutečný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMemoryBuffer – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
