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
ms.openlocfilehash: 327ef9f74e94e3b1b20e78eb6a833038b5bfe16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
Představuje spravovanou funkci nebo metodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Createbreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Vytvoří zarážku na začátku této funkce.|  
|[Getclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Získá objekt ICorDebugClass, který představuje třídu, ke které tato funkce je členem skupiny.|  
|[Getcurrentversionnumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Získá číslo verze nejnovější úpravy provedené v této funkce.|  
|[Getilcode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Získá kód (MSIL intermediate language) společnosti Microsoft pro tuto funkci.|  
|[Getlocalvarsigtoken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Získá token metadata pro místní proměnné podpis funkce, která je reprezentována to `ICorDebugFunction` instance.|  
|[Getmodule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Získá modul, ve kterém je definována funkce.|  
|[Getnativecode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Získá nativní kód pro tuto funkci.|  
|[Gettoken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Získá token metadata pro tuto funkci.|  
  
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
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
