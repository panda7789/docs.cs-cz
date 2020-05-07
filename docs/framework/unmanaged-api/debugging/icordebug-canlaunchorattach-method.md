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
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859687"
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
 pro Předat v `true` případě, že máte v plánu spustit s povoleným laděním Win32 nebo připojit s povoleným laděním Win32; v opačném `false`případě předejte.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud služby ladění určí, že spuštění nového procesu nebo připojení k danému procesu je možné, s ohledem na informace o aktuálním počítači a konfiguraci modulu runtime. Možné hodnoty HRESULT:  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je čistě informativní. Rozhraní vám nezastaví spouštění ani připojování k procesu bez ohledu na hodnotu vrácenou `CanLaunchOrAttach`.  
  
 Pokud máte v úmyslu spustit s povoleným laděním Win32 nebo připojit s povoleným `true` laděním Win32, předejte `win32DebuggingEnabled`. Pokud použijete tuto `CanLaunchOrAttach` možnost, může se stát, že se hodnota HRESULT vrátila.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebug – rozhraní](icordebug-interface.md)
