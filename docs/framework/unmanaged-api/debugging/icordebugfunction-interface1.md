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
ms.openlocfilehash: 550b85474c1ccd7e125549e86df906439caf410e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621502"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction – rozhraní

Představuje spravovanou funkci nebo metodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Vytvoří zarážku na začátku této funkce.|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Získá ICorDebugClass objekt, který představuje třídu, tato funkce je členem skupiny.|  
|[GetCurrentVersionNumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Získá číslo verze nejnovější úpravy provedené v této funkce.|  
|[GetILCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Získá kód Microsoft intermediate language (MSIL) pro tuto funkci.|  
|[GetLocalVarSigToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Získá metadata pro místní proměnné podpis funkce, která je reprezentována tento token `ICorDebugFunction` instance.|  
|[GetModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Získá modul, ve kterém je definována funkce.|  
|[GetNativeCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Získá nativní kód pro tuto funkci.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Získá token metadat pro tuto funkci.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugFunction` Rozhraní nepředstavuje funkce s parametry obecného typu. Například `ICorDebugFunction` představuje instanci `Func<T>` , ale ne `Func<string>`. Volání [icordebugilframe2::enumeratetypeparameters –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) zobrazíte parametry obecného typu.  
  
 Vztah mezi tokenu metadat metodu, `mdMethodDef`a metody `ICorDebugFunction` objektu je závislá na Určuje, zda je povoleno upravit a pokračovat na funkci:  
  
- Pokud funkce upravit a pokračovat není povoleno ve funkci, po jejím obnovení relace existuje mezi `ICorDebugFunction` objektu a `mdMethodDef` token. To znamená, že funkce má jeden `ICorDebugFunction` objekt a jeden `mdMethodDef` token.  
  
- Pokud je povoleno upravit a pokračovat na funkce, mezi existuje vztah mnoha k jednomu jinému `ICorDebugFunction` objektu a `mdMethodDef` token. To znamená, funkce může mít mnoho instancí `ICorDebugFunction`, jeden pro každou verzi funkce, ale pouze jeden `mdMethodDef` token.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:**  CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
