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
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210186"
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
 Pokud `dwFlags` je hodnota neplatná, `SetJITCompilerFlags` metoda se nezdaří.  
  
 `SetJITCompilerFlags`Metodu lze volat pouze v rámci zpětného volání [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) pro tento modul. Pokusy o jeho volání po `ICorDebugManagedCallback::LoadModule` doručení zpětného volání se nezdaří.  
  
 Příkaz Upravit a pokračovat není podporován na platformě 64 a systémy Win9x. Proto pokud voláte `SetJITCompilerFlags` metodu na některé z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným v `dwFlags` , `SetJITCompilerFlags` Metoda a všechny metody specifické pro příkaz Upravit a pokračovat, například [ICorDebugModule2:: ApplyChanges –](icordebugmodule2-applychanges-method.md), selžou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
