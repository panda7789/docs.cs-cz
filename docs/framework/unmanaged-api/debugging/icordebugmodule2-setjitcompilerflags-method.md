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
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792964"
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
 pro Bitová kombinace hodnot výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota `dwFlags` neplatná, metoda `SetJITCompilerFlags` se nezdaří.  
  
 Metodu `SetJITCompilerFlags` lze volat pouze v rámci zpětného volání [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) pro tento modul. Pokusí se ji zavolat po doručení `ICorDebugManagedCallback::LoadModule` zpětného volání se nezdaří.  
  
 Příkaz Upravit a pokračovat není podporován na platformě 64 a systémy Win9x. Proto pokud voláte metodu `SetJITCompilerFlags` na některé z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným v `dwFlags`, metoda `SetJITCompilerFlags` a všechny metody, které jsou specifické pro úpravu a pokračování, například [ICorDebugModule2:: ApplyChanges –](icordebugmodule2-applychanges-method.md), se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
