---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
Představuje spravovanou funkci nebo metodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Vytvoří zarážku na začátku této funkce.|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Získá objekt ICorDebugClass, který představuje třídu, ke které tato funkce je členem skupiny.|  
|[GetCurrentVersionNumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Získá číslo verze nejnovější úpravy provedené v této funkce.|  
|[GetILCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Získá kód (MSIL intermediate language) společnosti Microsoft pro tuto funkci.|  
|[GetLocalVarSigToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Získá token metadata pro místní proměnné podpis funkce, která je reprezentována to `ICorDebugFunction` instance.|  
|[GetModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Získá modul, ve kterém je definována funkce.|  
|[GetNativeCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Získá nativní kód pro tuto funkci.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Získá token metadata pro tuto funkci.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugFunction` Rozhraní nepředstavuje funkce s parametry obecného typu. Například `ICorDebugFunction` instance by představují `Func<T>` ale ne `Func<string>`. Volání [icordebugilframe2::enumeratetypeparameters –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) získat parametry obecného typu.  
  
 Vztah mezi metodu na token metadata, `mdMethodDef`a metody `ICorDebugFunction` objektu je závislá na povolení upravit a pokračovat na funkci:  
  
-   Je-li upravit a pokračovat není povolena pro funkci, mezi existuje relace 1: 1 `ICorDebugFunction` objektu a `mdMethodDef` tokenu. To znamená, funkce má jeden `ICorDebugFunction` objektů a jeden `mdMethodDef` tokenu.  
  
-   Pokud upravit a pokračovat, je povolena pro funkci, mezi existuje relace n: 1 `ICorDebugFunction` objektu a `mdMethodDef` tokenu. To znamená, funkce může obsahovat mnoho instancí `ICorDebugFunction`, jedna pro každou verzi funkce, ale pouze jedna `mdMethodDef` tokenu.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
