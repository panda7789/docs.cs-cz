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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213235"
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
|[GetLocalVarSigToken – metoda](icordebugfunction-getlocalvarsigtoken-method.md)|Získá token metadat pro podpis místní proměnné funkce, která je reprezentovaná touto `ICorDebugFunction` instancí.|  
|[GetModule – metoda](icordebugfunction-getmodule-method.md)|Získá modul, ve kterém je tato funkce definovaná.|  
|[GetNativeCode – metoda](icordebugfunction-getnativecode-method.md)|Získá nativní kód pro tuto funkci.|  
|[GetToken – metoda](icordebugfunction-gettoken-method.md)|Získá token metadat pro tuto funkci.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugFunction`Rozhraní nepředstavuje funkci s parametry obecného typu. Například `ICorDebugFunction` instance by představovala, `Func<T>` ale ne `Func<string>` . Chcete-li získat parametry obecného typu, zavolejte [ICorDebugILFrame2:: EnumerateTypeParameters –](icordebugilframe2-enumeratetypeparameters-method.md) .  
  
 Vztah mezi tokenem metadat metody, `mdMethodDef` a `ICorDebugFunction` objektem metody je závislý na tom, zda je povolena funkce upravit a pokračovat pro funkci:  
  
- Pokud funkce upravit a pokračovat není u této funkce povolená, relace 1:1 mezi `ICorDebugFunction` objektem a `mdMethodDef` tokenem existuje. To znamená, že funkce má jeden `ICorDebugFunction` objekt a jeden `mdMethodDef` token.  
  
- Pokud je u této funkce povolená možnost upravit a pokračovat, existuje relace n:n mezi `ICorDebugFunction` objektem a `mdMethodDef` tokenem. To znamená, že funkce může mít mnoho instancí `ICorDebugFunction` , jednu pro každou verzi funkce, ale pouze jeden `mdMethodDef` token.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:**  CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
