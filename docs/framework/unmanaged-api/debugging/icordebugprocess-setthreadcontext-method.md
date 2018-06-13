---
title: ICorDebugProcess::SetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9ed79eb799971dfcbc9fd787cd0290795f79d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417963"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext – metoda
Nastaví kontext pro dané vlákno v tomto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [v] ID vlákna, pro kterou chcete nastavit kontext.  
  
 `contextSize`  
 [v] Velikost `context` pole.  
  
 `context`  
 [v] Pole bajtů, které popisují obsah podprocesu.  
  
 Kontext určuje architekturu procesoru, na kterém je prováděna vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program by měly volat tuto metodu, nikoli Win32 `SetThreadContext` fungovat, protože vlákno ve skutečnosti může být ve stavu "napadenému", ve kterém jeho kontext dočasně změnit. Tato metoda by měla používá, pokud se vlákna v nativním kódu. Použití [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu. Nikdy by měl budete muset upravit kontextu vlákno během ladění událost out-of-band (OOB).  
  
 Data předaná musí být kontextu strukturu pro aktuální platformě.  
  
 Tato metoda může poškodit modul runtime, pokud používá nesprávně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
