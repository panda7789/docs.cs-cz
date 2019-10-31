---
title: ICorDebugProcess::SetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 3c57021061c1566b369cdd43847e3994cf54e2da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139671"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext – metoda
Nastaví kontext pro dané vlákno v tomto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 pro ID vlákna, pro které chcete nastavit kontext.  
  
 `contextSize`  
 pro Velikost pole `context`.  
  
 `context`  
 pro Pole bajtů, které popisují kontext vlákna.  
  
 Kontext určuje architekturu procesoru, ve kterém je vlákno spuštěno.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program by měl volat tuto metodu namísto funkce Win32 `SetThreadContext`, protože vlákno může být ve skutečnosti ve stavu "napadeno", ve kterém byl jeho kontext dočasně změněn. Tato metoda by měla být použita pouze v případě, že vlákno je v nativním kódu. Použijte [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu. Nikdy byste neměli muset změnit kontext vlákna během události ladění OOB (out-of-band).  
  
 Předaná data musí být kontextové struktury pro aktuální platformu.  
  
 Tato metoda může poškodit modul runtime, pokud je použit nesprávně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
