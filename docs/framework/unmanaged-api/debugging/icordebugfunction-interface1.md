---
title: ICorDebugFunction – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917205"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction – rozhraní

Představuje spravovanou funkci nebo metodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Vytvoří zarážku na začátku této funkce.|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.|  
|[GetCurrentVersionNumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Získá číslo verze poslední úpravy provedené u této funkce.|  
|[GetILCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Získá kód jazyka MSIL (Microsoft Intermediate Language) pro tuto funkci.|  
|[GetLocalVarSigToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Získá token metadat pro podpis místní proměnné funkce, která je reprezentovaná touto `ICorDebugFunction` instancí.|  
|[GetModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Získá modul, ve kterém je tato funkce definovaná.|  
|[GetNativeCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Získá nativní kód pro tuto funkci.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Získá token metadat pro tuto funkci.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugFunction` Rozhraní nepředstavuje funkci s parametry obecného typu. Například `ICorDebugFunction` instance by představovala `Func<T>` , ale ne `Func<string>`. Chcete-li získat parametry obecného typu, zavolejte [ICorDebugILFrame2:: EnumerateTypeParameters –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) .  
  
 Vztah mezi tokenem metadat metody, `mdMethodDef`a `ICorDebugFunction` objektem metody je závislý na tom, zda je povolena funkce upravit a pokračovat pro funkci:  
  
- Pokud funkce upravit a pokračovat není u této funkce povolená, relace 1:1 mezi `ICorDebugFunction` objektem `mdMethodDef` a tokenem existuje. To znamená, že funkce má jeden `ICorDebugFunction` objekt a jeden `mdMethodDef` token.  
  
- Pokud je u této funkce povolená možnost upravit a pokračovat, existuje relace n:n mezi `ICorDebugFunction` objektem `mdMethodDef` a tokenem. To znamená, že funkce může mít mnoho instancí `ICorDebugFunction`, jednu pro každou verzi funkce, ale pouze jeden `mdMethodDef` token.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna**  CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
