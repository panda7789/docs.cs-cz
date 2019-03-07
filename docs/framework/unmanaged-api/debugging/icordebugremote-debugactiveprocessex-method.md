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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba0ff6e545a5da5d7733a157b73ddd66e717de9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477111"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx – metoda
Spustí nějaký proces ve vzdáleném počítači v ladicím programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [in] Ukazatel [icordebugremotetarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Tento parametr slouží k určení počítače, na kterém je proces spuštěn.  
  
 `id`  
 [in] ID procesu, ke kterému je ladicí program připojit.  
  
 `win32Attach`  
 [in] `true` Pokud ladicí program by měl chovat jako ladicí program systému Win32 pro proces a odeslání nespravované zpětná volání; v opačném případě `false`.  
  
 `ppProcess`  
 [out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, ke kterému je připojen ladicí program.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně připojeno k procesu ve vzdáleném počítači.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nelze se připojit k procesu ve vzdáleném počítači.  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu není v Silverlightu podporovaný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
