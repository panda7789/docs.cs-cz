---
title: ICorDebugRemote::DebugActiveProcessEx – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: 83cc4eadca7c337c06c5fbf9f0e74306c2b9cb99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131278"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx – metoda
Spustí proces na vzdáleném počítači v rámci ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 pro Ukazatel na [rozhraní ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Tento parametr slouží k určení počítače, na kterém je spuštěn proces.  
  
 `id`  
 pro ID procesu, ke kterému má být připojen ladicí program.  
  
 `win32Attach`  
 [in] `true`, jestli se má ladicí program chovat jako ladicí program Win32 pro proces a odeslání nespravovaných zpětných volání; v opačném případě `false`.  
  
 `ppProcess`  
 mimo Ukazatel na adresu objektu "ICorDebugProcess", který představuje proces, ke kterému byl připojen ladicí program.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně připojeno k procesu na vzdáleném počítači.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nelze se připojit k procesu na vzdáleném počítači.  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu není v Silverlightu podporované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
