---
title: ICorDebugModule2::SetJITCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137365"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags – metoda
Nastaví příznaky, které řídí kompilaci JIT (just-in-time) tohoto ICorDebugModule2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 pro Bitová kombinace hodnot výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota `dwFlags` neplatná, metoda `SetJITCompilerFlags` se nezdaří.  
  
 Metodu `SetJITCompilerFlags` lze volat pouze v rámci zpětného volání [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) pro tento modul. Pokusí se ji zavolat po doručení `ICorDebugManagedCallback::LoadModule` zpětného volání se nezdaří.  
  
 Příkaz Upravit a pokračovat není podporován na platformě 64 a systémy Win9x. Proto pokud zavoláte metodu `SetJITCompilerFlags` na některé z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným v `dwFlags`, metoda `SetJITCompilerFlags` a všechny metody specifické pro úpravy a pokračování, jako například [ICorDebugModule2:: ApplyChanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
