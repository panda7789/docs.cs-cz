---
title: ICorDebugProcess::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 41c5116d23655730f3586dc656aa69c8ae817b6c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792627"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext – metoda
Získá kontext pro dané vlákno v tomto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 pro ID vlákna, pro které má být načten kontext.  
  
 `contextSize`  
 pro Velikost pole `context`.  
  
 `context`  
 [in, out] Pole bajtů, které popisují kontext vlákna.  
  
 Kontext určuje architekturu procesoru, ve kterém je vlákno spuštěno.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program by měl volat tuto metodu, spíše než Win32 `GetThreadContext` metoda, protože vlákno může být ve skutečnosti ve stavu "napadeno", ve kterém byl jeho kontext dočasně změněn. Tato metoda by měla být použita pouze v případě, že vlákno je v nativním kódu. Použijte [ICorDebugRegisterSet](icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.  
  
 Vrácená data jsou kontextovou strukturou pro aktuální platformu. Stejně jako u metody Win32 `GetThreadContext` by volající měl inicializovat parametr `context` před voláním této metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
