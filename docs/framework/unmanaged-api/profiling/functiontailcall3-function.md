---
title: FunctionTailcall3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 55955cd47bd32fb4294b0b8e852dd692702bd74f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500530"
---
# <a name="functiontailcall3-function"></a>FunctionTailcall3 – funkce
Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>Parametry

- `functionOrRemappedID`

  \[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.

## <a name="remarks"></a>Poznámky  
 `FunctionTailcall3`Funkce zpětného volání oznámí profileru jako volání funkcí. K registraci implementace této funkce použijte [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .  
  
 `FunctionTailcall3`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionTailcall3` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionTailcall3` nevrátí.  
  
 `FunctionTailcall3`Funkce nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo – funkce](functiontailcall3withinfo-function.md)
- [Setenterleavefunctionhooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withinfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2 –](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
