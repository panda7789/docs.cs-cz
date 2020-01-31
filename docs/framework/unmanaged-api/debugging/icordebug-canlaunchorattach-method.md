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
ms.openlocfilehash: 28b9fb5a25981e5e37a5f1bbb797baeac45e0028
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793566"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach – metoda
Vrátí hodnotu HRESULT, která označuje, zda je možné spustit nový proces nebo připojit k zadanému existujícímu procesu v rámci kontextu aktuálního počítače a konfigurace modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwProcessId`  
 pro ID existujícího procesu.  
  
 `win32DebuggingEnabled`  
 pro Předejte `true`, pokud máte v plánu spustit s povoleným laděním Win32 nebo připojit s povoleným laděním Win32. v opačném případě předejte `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud služby ladění určí, že spuštění nového procesu nebo připojení k danému procesu je možné, s ohledem na informace o aktuálním počítači a konfiguraci modulu runtime. Možné hodnoty HRESULT:  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je čistě informativní. Rozhraní vám nezastaví spouštění ani připojování k procesu bez ohledu na hodnotu vrácenou `CanLaunchOrAttach`.  
  
 Pokud máte v úmyslu spustit s povoleným laděním Win32 nebo připojit s povoleným laděním Win32, předejte `true` `win32DebuggingEnabled`. Hodnota HRESULT vrácená funkcí `CanLaunchOrAttach` se může lišit, pokud použijete tuto možnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](icordebug-interface.md)
