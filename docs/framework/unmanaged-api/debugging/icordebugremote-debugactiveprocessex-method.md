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
ms.openlocfilehash: b78bff2994cefc6c35a4bd59133338392c3a1b24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791977"
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
 pro Ukazatel na [rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md). Tento parametr slouží k určení počítače, na kterém je spuštěn proces.  
  
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

- [ICorDebugRemote – rozhraní](icordebugremote-interface.md)
- [ICorDebug – rozhraní](icordebug-interface.md)

- [Rozhraní pro ladění](debugging-interfaces.md)
