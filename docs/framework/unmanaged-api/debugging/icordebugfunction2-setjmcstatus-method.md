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
ms.openlocfilehash: 15b102be5a792f982edeb320199576bdddbd859a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412357"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus – metoda
Označí funkce reprezentována tento ICorDebugFunction2 pro pouze můj kód krokování s.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [v] Nastavte na `true` označit funkce jako uživatelský kód; jinak hodnota nastavena na `false`.  
  
## <a name="return-values"></a>Návratové hodnoty  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Funkci byl úspěšně označen.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Funkci nelze označit jako uživatelského kódu, protože nelze ladit.|  
  
## <a name="remarks"></a>Poznámky  
 Pouze můj kód krokovač přeskočí bez uživatelského kódu. Uživatelský kód musí být podmnožinou debuggable kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
