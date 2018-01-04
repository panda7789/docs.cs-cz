---
title: "ICorDebugProcess::GetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e45d101db946747463ba4200bc5dd3b95d21391
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext – metoda
Získá kontext pro dané vlákno v tomto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [v] ID vlákna, pro které k načtení kontextu.  
  
 `contextSize`  
 [v] Velikost `context` pole.  
  
 `context`  
 [ve out] Pole bajtů, které popisují obsah podprocesu.  
  
 Kontext určuje architekturu procesoru, na kterém je prováděna vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program by měly volat tuto metodu, nikoli Win32 `GetThreadContext` metoda, protože vlákno ve skutečnosti může být ve stavu "napadenému", ve kterém jeho kontext dočasně změnit. Tato metoda by měla používá, pokud se vlákna v nativním kódu. Použití [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.  
  
 S daty vrácenými je struktura kontext pro aktuální platformě. Stejně jako v Win32 `GetThreadContext` metoda, měli byste inicializovat volající `context` parametr před voláním této metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
