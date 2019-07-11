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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67959b2ebbfb62b47a1b2a770e278d043fc66d21
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754927"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus – metoda
Označí funkci reprezentována tento icordebugfunction2 – pro volbu pouze vlastní kód krokování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [in] Nastavte na `true` označit funkce jako uživatelského kódu; v opačném případě nastavte na `false`.  
  
## <a name="return-values"></a>Návratové hodnoty  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Funkci byl úspěšně označen.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Funkci nelze označit jako uživatelský kód, protože není možné ladit.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce pouze můj kód krokovač přeskočí neuživatelský kód. Kód uživatele musí být podmnožinou laditelný kód.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
