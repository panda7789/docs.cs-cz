---
title: ICorDebugFunction2::GetVersionNumber – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber – metoda
Získá verzi aplikace upravit a pokračovat v této funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pnVersion`  
 [out] Ukazatel na celé číslo, které je funkce, která je reprezentována tento objekt ICorDebugFunction2 číslo verze.  
  
## <a name="remarks"></a>Poznámky  
 Modul runtime uchovává informace o počtu úprav, které byly provedeny na každý modul během ladicí relace. Číslo verze funkce je jedním více než počet zavedena funkce upravit. Funkce na původní verze je verze 1. Číslo je zvýšena pro modul pokaždé, když [icordebugmodule2::applychanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) je volána v tomto modulu. Proto pokud byl nahrazen tělo funkce ve volání první a třetí `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` může vrátit verze 1, 2 nebo 4 pro tuto funkci, ale verze 3. (Této funkce by měla mít žádná verze 3.)  
  
 Číslo verze je nezávisle sledovaný pro každý modul. Ano Pokud provádíte čtyři úpravy v modulu 1 a žádná modulu 2, přidělí další úpravy v modulu 1 číslo verze 6 k všechny upravená funkce v modulu 1. Pokud stejný upravit úpravy 2 modulu, funkce v modulu 2 dostane číslo verze 2.  
  
 Číslo verze získat `GetVersionNumber` metoda může být nižší než získat [icordebugfunction::getcurrentversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 [Icordebugcode::getversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda provádí stejné operace jako `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
