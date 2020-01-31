---
title: 'ICorDebugVirtualUnwinder:: GetContext – Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ff5e5bdd66ec44a0931b51212f07485718507576
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790843"
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
 pro Počet bajtů v `contextBuf`.  
  
 `contextSize`  
 mimo Ukazatel na počet bajtů skutečně zapsaných do `contextBuf`.  
  
 `contextBuf`  
 mimo Bajtové pole obsahující aktuální kontext tohoto unwindu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jakákoli neúspěšná hodnota HRESULT přijatá v mscordbi se považuje za závažnou a způsobí, že rozhraní API ICorDebug vrátí `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
 Nastavte počáteční hodnotu argumentu `contextBuf` na vyrovnávací paměť kontextu vrácenou voláním metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
 Vzhledem k tomu, že unwind může obnovit pouze podmnožinu registrů, jako jsou pouze nestálé Registry, kontext nemusí přesně odpovídat stavu registrace v době samotného volání metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMemoryBuffer – rozhraní](icordebugmemorybuffer-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
