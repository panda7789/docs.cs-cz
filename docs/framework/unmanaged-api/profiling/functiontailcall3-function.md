---
title: "FunctionTailcall3 – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3
helpviewer_keywords: FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5d274c966a345e0e2984018bcd8aa1e2dade03b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall3-function"></a>FunctionTailcall3 – funkce
Upozorní profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionOrRemappedID`  
 [v] Identifikátor aktuálně prováděné funkce, která se chystáte provést, tail volání.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionTailcall3` Funkce zpětného volání upozorní profileru, jako jsou volaná funkce. Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaší implementace této funkce.  
  
 `FunctionTailcall3` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
 Implementace `FunctionTailcall3` by neměly blokovat, protože zpozdí uvolňování paměti. Implementace neměli uvolňování, protože zásobník nemusí být ve stavu paměti procházející kolekci. Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionTailcall3` vrátí.  
  
 `FunctionTailcall3` Funkce nesmí volání do spravovaného kódu nebo způsobit přidělení spravované paměti žádným způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [Functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [Functiontailcall3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Setenterleavefunctionhooks3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [Setenterleavefunctionhooks3withinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [Setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [Setfunctionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [Profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
