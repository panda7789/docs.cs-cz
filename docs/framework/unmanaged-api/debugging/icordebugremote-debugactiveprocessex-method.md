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
ms.openlocfilehash: e0e3cdbff5054ec990c40c333ed4bd4029a91f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx – metoda
Spustí proces ve vzdáleném počítači v rámci ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [v] Ukazatel na [ICorDebugRemoteTarget rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Tento parametr slouží k určení počítače, na kterém je spuštěn proces.  
  
 `id`  
 [v] ID procesu, ke kterému má být připojen ladicí program.  
  
 `win32Attach`  
 [v] `true` Pokud ladicí program by měl chovat jako Win32 ladicí program pro proces a odesílání nespravované zpětná volání; jinak `false`.  
  
 `ppProcess`  
 [out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, který byl připojen ladicí program.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Pro proces ve vzdáleném počítači se úspěšně připojil.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nelze připojit k procesu ve vzdáleném počítači.  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu není podporována v programu Silverlight.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
