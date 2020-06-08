---
title: FunctionLeave2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: a2a3d58e0631fceab96c32f9d86fef25973fed84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500660"
---
# <a name="functionleave2-function"></a>FunctionLeave2 – funkce
Upozorní profileru, že se chystá návrat funkce k volajícímu a poskytuje informace o bloku zásobníku a návratové hodnotě funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in] identifikátor funkce, která vrací.

- `clientData`

  \[in] identifikátor přemapované funkce, který profil dřív zadal přes funkci [FunctionIDMapper –](functionidmapper-function.md) .

- `func`

  \[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.

  Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `retvalRange`

  \[in] ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , která určuje umístění paměti návratové hodnoty funkce.

  Aby bylo možné získat přístup k informacím o vrácených hodnotách, `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak. Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.

## <a name="remarks"></a>Poznámky  
 Hodnoty `func` `retvalRange` parametrů a nejsou platné poté, co `FunctionLeave2` funkce vrátí, protože hodnoty se mohou změnit nebo zničit.  
  
 `FunctionLeave2`Funkce je zpětné volání. je nutné ji implementovat. Implementace musí používat `__declspec` `naked` atribut třídy úložiště ().  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionLeave2` by neměla blokovat, protože by se zpozdilo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. Při pokusu o uvolnění paměti modul runtime zablokuje, dokud se `FunctionLeave2` nevrátí.  
  
 `FunctionLeave2`Funkce také nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](functionenter2-function.md)
- [FunctionTailcall2 – funkce](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
