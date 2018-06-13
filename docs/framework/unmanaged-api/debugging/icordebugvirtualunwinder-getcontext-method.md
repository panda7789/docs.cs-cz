---
title: ICorDebugVirtualUnwinder::GetContext – metoda
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96410466f17bf6b4e8fff235d434f470cabd9249
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422881"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext – metoda
Získá aktuální kontext tento unwinder.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `contextFlags`  
 [v] Příznaky, které určují, které části kontext, který má vrátit (definované v souboru WinNT.h).  
  
 `cbContextBuf`  
 [v] Počet bajtů v `contextBuf`.  
  
 `contextSize`  
 [out] Ukazatel na počet bajtů ve skutečnosti zapsána do `contextBuf`.  
  
 `contextBuf`  
 [out] Bajtové pole, která obsahuje aktuální kontext tento unwinder.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny selhání hodnota HRESULT přijatých mscordbi považuje za závažné a způsobí, že rozhraní API ICorDebug vrátit `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
 Nastavit počáteční hodnotu `contextBuf` argument do vyrovnávací paměti kontextu vrácený volání [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metoda.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
 Protože unwinding může pouze obnovení a podmnožina registrů, jako je například stálé zaregistruje pouze, kontext nemusí přesně odpovídat stav registrace v době volání skutečné metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMemoryBuffer – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
