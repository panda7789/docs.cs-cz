---
title: FunctionTailcall3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: f076044b44859cc39d90be528ee6648f5eaa626c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500582"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo – funkce
Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) pro načtení rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametry  

- `functionIDOrClientID`

  \[in] identifikátor aktuálně vykonávané funkce, která se chystá udělat volání funkce tail.

- `eltInfo`

  \[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku. Tento popisovač je platný pouze během zpětného volání, na které je předáno.

## <a name="remarks"></a>Poznámky  
 `FunctionTailcall3WithInfo`Metoda zpětného volání upozorní Profiler jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) ke kontrole rámce zásobníku. Chcete-li získat přístup k informacím o snímku zásobníku, je `COR_PRF_ENABLE_FRAME_INFO` nutné nastavit příznak. Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.  
  
 `FunctionTailcall3WithInfo`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionTailcall3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionTailcall3WithInfo` nevrátí.  
  
 Také funkce Functiontailcall3withinfo – nesmí volat do spravovaného kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [Functionenter3withinfo –](functiontailcall3-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [Setenterleavefunctionhooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withinfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2 –](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
