---
title: FunctionEnter3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: ff4b32185e604611eaaead2847c11bc139d405a6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500686"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo – funkce
Upozorňuje profileru, že řízení je předáno funkci, a poskytuje popisovač, který lze předat [metodě ICorProfilerInfo3:: GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) pro načtení rámce zásobníku a argumentů funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametry

- `functionIDOrClientID`

  \[in] identifikátor funkce, do které byl ovládací prvek předán.

- `eltInfo`

  \[in] neprůhledný popisovač, který představuje informace o daném snímku zásobníku. Tento popisovač je platný pouze během zpětného volání, na které je předáno.

## <a name="remarks"></a>Poznámky  
 `FunctionEnter3WithInfo`Metoda zpětného volání oznámí Profiler jako volání funkcí a umožňuje profileru použít [metodu ICorProfilerInfo3:: GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) ke kontrole hodnot argumentů. Chcete-li získat přístup k informacím o argumentech, je `COR_PRF_ENABLE_FUNCTION_ARGS` nutné nastavit příznak. Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít [metodu ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.  
  
 `FunctionEnter3WithInfo`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec(naked)` atribut třídy úložiště.  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionEnter3WithInfo` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemusí být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionEnter3WithInfo` nevrátí.  
  
 `FunctionEnter3WithInfo`Funkce nesmí volat spravovanému kódu nebo způsobit přidělení spravované paměti jakýmkoli způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Getfunctionenter3info –](icorprofilerinfo3-getfunctionenter3info-method.md)
- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
