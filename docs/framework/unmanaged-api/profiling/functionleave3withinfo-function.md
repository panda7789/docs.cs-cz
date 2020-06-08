---
title: FunctionLeave3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: 235bae64fe5e6a534f2a650050c6c9ad4aa8fe84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500621"
---
# <a name="functionleave3withinfo-function"></a>FunctionLeave3WithInfo – funkce
Upozorní profiler, že je vrácen ovládací prvek z funkce, a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) pro načtení rámce zásobníku a návratové hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametry

- `functionIDOrClientID`

  \[in] identifikátor funkce, ze které je vrácen ovládací prvek.

- `eltInfo`

  \[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku. Tento popisovač je platný pouze během zpětného volání, na které je předáno.

## <a name="remarks"></a>Poznámky  
 `FunctionLeave3WithInfo`Metoda zpětného volání upozorní Profiler jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) ke kontrole návratové hodnoty. Chcete-li získat přístup k informacím o vrácených hodnotách, je `COR_PRF_ENABLE_FUNCTION_RETVAL` nutné nastavit příznak. Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.  
  
 `FunctionLeave3WithInfo`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionLeave3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionLeave3WithInfo` nevrátí.  
  
 `FunctionLeave3WithInfo`Funkce nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Getfunctionleave3info –](icorprofilerinfo3-getfunctionleave3info-method.md)
- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functiontailcall3withinfo –](functiontailcall3withinfo-function.md)
- [Setenterleavefunctionhooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withinfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2 –](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
