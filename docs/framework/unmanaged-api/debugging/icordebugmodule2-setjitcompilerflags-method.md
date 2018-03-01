---
title: "ICorDebugModule2::SetJITCompilerFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cfc25e9ce15996360cd0e3c68805d3707b325f79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags – metoda
Nastaví příznaky, které řídí tento ICorDebugModule2 kompilace v běhu (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [v] Bitové kombinace [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) hodnot výčtu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `dwFlags` hodnota je neplatná, `SetJITCompilerFlags` metoda se nezdaří.  
  
 `SetJITCompilerFlags` Metodu lze volat pouze z uvnitř [icordebugmanagedcallback::LoadModule –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) zpětného volání pro tento modul. Pokusí se ji po volání `ICorDebugManagedCallback::LoadModule` zpětného volání byla doručena se nezdaří.  
  
 Upravit a pokračovat není podporována na 64-bit nebo systémy Windows 9 x platformy. Proto při volání `SetJITCompilerFlags` metoda na některou z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným `dwFlags`, `SetJITCompilerFlags` metoda a všechny metody, které jsou specifické pro upravit a pokračovat, jako například [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
