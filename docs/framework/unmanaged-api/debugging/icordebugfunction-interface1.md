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
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794507"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction – rozhraní

Představuje spravovanou funkci nebo metodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](icordebugfunction-createbreakpoint-method.md)|Vytvoří zarážku na začátku této funkce.|  
|[GetClass – metoda](icordebugfunction-getclass-method.md)|Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.|  
|[GetCurrentVersionNumber – metoda](icordebugfunction-getcurrentversionnumber-method.md)|Získá číslo verze poslední úpravy provedené u této funkce.|  
|[GetILCode – metoda](icordebugfunction-getilcode-method.md)|Získá kód jazyka MSIL (Microsoft Intermediate Language) pro tuto funkci.|  
|[GetLocalVarSigToken – metoda](icordebugfunction-getlocalvarsigtoken-method.md)|Získá token metadat pro místní proměnnou signaturu funkce, která je reprezentovaná touto instancí `ICorDebugFunction`.|  
|[GetModule – metoda](icordebugfunction-getmodule-method.md)|Získá modul, ve kterém je tato funkce definovaná.|  
|[GetNativeCode – metoda](icordebugfunction-getnativecode-method.md)|Získá nativní kód pro tuto funkci.|  
|[GetToken – metoda](icordebugfunction-gettoken-method.md)|Získá token metadat pro tuto funkci.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugFunction` nepředstavuje funkci s parametry obecného typu. Například instance `ICorDebugFunction` by představovala `Func<T>`, ale ne `Func<string>`. Chcete-li získat parametry obecného typu, zavolejte [ICorDebugILFrame2:: EnumerateTypeParameters –](icordebugilframe2-enumeratetypeparameters-method.md) .  
  
 Vztah mezi tokenem metadat metody, `mdMethodDef`a objektem `ICorDebugFunction` metody je závislý na tom, zda je povolena funkce upravit a pokračovat pro funkci:  
  
- Pokud funkce upravit a pokračovat není povolena pro funkci, existuje relace 1:1 mezi objektem `ICorDebugFunction` a tokenem `mdMethodDef`. To znamená, že funkce má jeden objekt `ICorDebugFunction` a jeden `mdMethodDef` token.  
  
- Pokud je u této funkce povolená možnost upravit a pokračovat, mezi objektem `ICorDebugFunction` a tokenem `mdMethodDef` existuje vztah n:n. To znamená, že funkce může mít mnoho instancí `ICorDebugFunction`, jednu pro každou verzi funkce, ale pouze jeden token `mdMethodDef`.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:**  CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
