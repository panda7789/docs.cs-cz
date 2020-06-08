---
title: FunctionEnter2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 8c88e97f8187ac347f4ff39890c8d87ee80c8f9e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500712"
---
# <a name="functionenter2-function"></a>FunctionEnter2 – funkce
Upozorňuje profileru, že řízení je předáno funkci a poskytuje informace o bloku zásobníku a argumentech funkce. Tato funkce nahrazuje funkci [FunctionEnter –](functionenter-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in] identifikátor funkce, do které byl ovládací prvek předán.

- `clientData`

  \[in] identifikátor přemapované funkce, který Profiler předtím určil pomocí funkce [FunctionIDMapper –](functionidmapper-function.md) .
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.
  
  Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `argumentInfo`

  \[in] ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , která určuje umístění v paměti argumentů funkce.

  Aby bylo možné získat přístup k informacím o argumentech, `COR_PRF_ENABLE_FUNCTION_ARGS` musí být nastaven příznak. Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.

## <a name="remarks"></a>Poznámky  
 Hodnoty `func` `argumentInfo` parametrů a nejsou platné poté, co `FunctionEnter2` funkce vrátí, protože hodnoty se mohou změnit nebo zničit.  
  
 `FunctionEnter2`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionEnter2` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionEnter2` nevrátí.  
  
 `FunctionEnter2`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionLeave2 – funkce](functionleave2-function.md)
- [FunctionTailcall2 – funkce](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
