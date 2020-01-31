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
ms.openlocfilehash: d85885d750f3c98e46b3e44418564da18850d3ec
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794490"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber – metoda
Získá verzi této funkce pro úpravu a pokračování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnVersion`  
 mimo Ukazatel na celé číslo, které je číslem verze funkce reprezentované tímto objektem ICorDebugFunction2.  
  
## <a name="remarks"></a>Poznámky  
 Modul runtime uchovává přehled o počtu úprav, které byly provedeny v jednotlivých modulech během relace ladění. Číslo verze funkce je o jednu vyšší, než je počet úprav, které tuto funkci zavedly. Původní verze funkce je verze 1. Číslo se zvyšuje pro modul pokaždé, když [ICorDebugModule2:: ApplyChanges –](icordebugmodule2-applychanges-method.md) je v tomto modulu volán. Proto pokud byl tělo funkce nahrazeno prvním a třetím voláním `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` může pro tuto funkci vracet verze 1, 2 nebo 4, ale ne verze 3. (Tato funkce by nemusela mít verzi 3.)  
  
 Číslo verze se sleduje samostatně pro každý modul. Pokud tedy v modulu 1 provedete čtyři úpravy a v modulu 2 nejsou žádné, vaše další úprava v modulu 1 přiřadí ke všem upraveným funkcím v modulu 1 číslo verze 6. Pokud se ve stejné úpravě dotkne modul 2, funkce v modulu 2 obdrží číslo verze 2.  
  
 Číslo verze získané metodou `GetVersionNumber` může být nižší než hodnota získaná pomocí [ICorDebugFunction:: GetCurrentVersionNumber –](icordebugfunction-getcurrentversionnumber-method.md).  
  
 Metoda [ICorDebugCode:: getčíslo_verze](icordebugcode-getversionnumber-method.md) provede stejnou operaci jako `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
