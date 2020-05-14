---
title: 'ICorDebugVirtualUnwinder:: GetContext – Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: e203db78b40bf4305316046cfcd679f3d10d1876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396437"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder:: GetContext – Metoda
Získá aktuální kontext tohoto unwind.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `contextFlags`  
 pro Příznaky, které určují, které části kontextu se mají vrátit (definované v souboru WinNT. h).  
  
 `cbContextBuf`  
 pro Počet bajtů v `contextBuf` .  
  
 `contextSize`  
 mimo Ukazatel na počet bajtů, které jsou ve skutečnosti zapsány `contextBuf` .  
  
 `contextBuf`  
 mimo Bajtové pole obsahující aktuální kontext tohoto unwindu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jakákoli neúspěšná hodnota HRESULT přijatá v mscordbi se považuje za závažnou a způsobí, že rozhraní ICorDebug API vrátí `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Poznámky  
 Nastavte počáteční hodnotu `contextBuf` argumentu na vyrovnávací paměť kontextu vrácenou voláním metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
 Vzhledem k tomu, že unwind může obnovit pouze podmnožinu registrů, jako jsou pouze nestálé Registry, kontext nemusí přesně odpovídat stavu registrace v době samotného volání metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMemoryBuffer – rozhraní](icordebugmemorybuffer-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
