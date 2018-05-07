---
title: FunctionEnter3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 466b90f814d267fb289b2804beccd58fc442e341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="functionenter3-function"></a>FunctionEnter3 – funkce
Upozorní profileru, že se ovládací prvek předán do funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionOrRemappedID`  
 [v] Identifikátor funkce, ke kterému je předán ovládacího prvku.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionEnter3` Funkce zpětného volání upozorní profileru, protože funkce je volána, ale nemá podpora argument kontroly. Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaší implementace této funkce.  
  
 `FunctionEnter3` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [Functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [Functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Setenterleavefunctionhooks3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [Setenterleavefunctionhooks3withinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [Setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [Setfunctionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
