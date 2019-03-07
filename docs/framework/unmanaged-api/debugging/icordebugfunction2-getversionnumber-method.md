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
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497168"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber – metoda
Získá verzi této funkce upravit a pokračovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnVersion`  
 [out] Ukazatel na celé číslo, které je číslo verze, která je reprezentována tímto objektem icordebugfunction2 – funkce  
  
## <a name="remarks"></a>Poznámky  
 Modul runtime uchovává informace o počtu úpravy, které byly provedeny pro každý modul během relace ladění. Číslo verze funkce je jeden vyšší než počet úpravy funkce zavedena. Původní verze této funkce je verze 1. Počet se zvýší pro modul pokaždé, když [icordebugmodule2::applychanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) je volána v tomto modulu. Proto pokud tělo funkce jsou nahrazené v první a třetí volání `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` může vrátit verze 1, 2 nebo 4 pro tuto funkci, ale ne verzi 3. (Tato funkce nemá žádné verze 3.)  
  
 Číslo verze je sledována samostatně pro každý modul. Proto pokud provádění čtyři úprav v modulu 1 a žádné v modulu 2, další úpravy na modulu 1 přiřadí číslo verze 6 všechny upravené funkce v modulu 1. Pokud stejný upravit dnešní 2 modulu, funkce v modulu 2 se číslo verze 2.  
  
 Získá číslo verze `GetVersionNumber` metoda může být nižší než, která získá [icordebugfunction::getcurrentversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 [Icordebugcode::getversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda provede stejné operace jako `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
