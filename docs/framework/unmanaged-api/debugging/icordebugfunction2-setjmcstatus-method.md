---
title: ICorDebugFunction2::SetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137785"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus – metoda
Označuje funkci představovanou tímto ICorDebugFunction2 pro Pouze můj kód krokování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 pro Nastavte na `true` pro označení funkce jako uživatelského kódu; v opačném případě nastavte na `false`.  
  
## <a name="return-values"></a>Návratové hodnoty  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Funkce byla úspěšně označena.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Funkci nelze označit jako uživatelský kód, protože nemůže být Laděna.|  
  
## <a name="remarks"></a>Poznámky  
 Pouze můj kód stepper přeskočí jiný než uživatelský kód. Uživatelský kód musí být podmnožinou laděného kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
