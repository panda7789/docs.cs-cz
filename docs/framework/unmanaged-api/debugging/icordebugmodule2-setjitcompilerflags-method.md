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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c71ccbc62ea026a55a7e84f6925a78850594a813
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942510"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags – metoda
Nastaví příznaky, které řídí tento icordebugmodule2 – kompilace just-in-time (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Bitová kombinace hodnot [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) hodnot výčtu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `dwFlags` hodnota není platná, `SetJITCompilerFlags` metoda se nezdaří.  
  
 `SetJITCompilerFlags` Metodu lze volat pouze v rámci [icordebugmanagedcallback::LoadModule –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) zpětné volání pro tento modul. Pokusí se jeho po volání `ICorDebugManagedCallback::LoadModule` byla doručena zpětné volání se nezdaří.  
  
 Upravit a pokračovat není podporována na 64-bit nebo platformách Win9x. Proto při volání `SetJITCompilerFlags` metodu na některý z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastavit `dwFlags`, `SetJITCompilerFlags` metoda a všechny metody konkrétní upravit a pokračovat, jako například [icordebugmodule2 –:: Applychanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
