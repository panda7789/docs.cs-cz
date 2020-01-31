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
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866928"
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

  \[v] identifikátor přemapované funkce, který Profiler dříve zadal prostřednictvím funkce [FunctionIDMapper –](functionidmapper-function.md) .

- `func`

  \[in] `COR_PRF_FRAME_INFO` hodnota, která odkazuje na informace o snímku zásobníku.

  Profiler by měl považovat za neprůhledný popisovač, který lze předat zpět spouštěcímu modulu v metodě [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `retvalRange`

  \[in] ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , která určuje umístění paměti návratové hodnoty funkce.

  Aby bylo možné získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`. Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.

## <a name="remarks"></a>Poznámky  
 Hodnoty parametrů `func` a `retvalRange` nejsou po vrácení `FunctionLeave2` funkce platné, protože hodnoty se mohou změnit nebo zničit.  
  
 Funkce `FunctionLeave2` je zpětné volání; je nutné jej implementovat. Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).  
  
 Spouštěcí modul neuloží žádné Registry před voláním této funkce.  
  
- Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.  
  
 Implementace `FunctionLeave2` by neměla zablokovat, protože bude odloženo uvolňování paměti. Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti. V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionLeave2` nevrátí.  
  
 Také funkce `FunctionLeave2` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter2 – funkce](functionenter2-function.md)
- [FunctionTailcall2 – funkce](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Globální statické funkce pro profilaci](profiling-global-static-functions.md)
