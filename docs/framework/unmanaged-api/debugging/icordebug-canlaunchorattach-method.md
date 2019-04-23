---
title: ICorDebug::CanLaunchOrAttach – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf0065f1ed12ad3a37819b0a15d734a2b51ff5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125603"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach – metoda
Vrátí hodnotu HRESULT, která určuje, zda je možné v rámci kontextu aktuální konfiguraci počítače a modul runtime spustí nový proces nebo připojení k zadané existující procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwProcessId`  
 [in] ID existující proces.  
  
 `win32DebuggingEnabled`  
 [in] Předejte `true` Pokud plánujete spustit s povoleným laděním Win32, nebo se připojit s Win32 ladění povoleno; jinak předejte `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud ladění služby určit, který spouští se nový proces nebo připojení k dané procesu je možné, uvedené informace o aktuální konfiguraci počítače a modulu runtime. Jsou možné hodnoty HRESULT:  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je pouze informační. Rozhraní nezastaví spouštění nebo připojení k procesu, bez ohledu na hodnotu vrácenou `CanLaunchOrAttach`.  
  
 Pokud budete chtít spustit s povoleným laděním Win32 nebo připojení s povoleným laděním Win32, předejte `true` pro `win32DebuggingEnabled`. Vrácená hodnota HRESULT `CanLaunchOrAttach` mohou lišit, pokud použijete tuto možnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
