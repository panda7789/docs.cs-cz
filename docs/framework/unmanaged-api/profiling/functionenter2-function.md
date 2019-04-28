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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 825da3a09f8b8013ffecaedfee0dce2362c8a7b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598971"
---
# <a name="functionenter2-function"></a>FunctionEnter2 – funkce
Profiler upozorní, že ovládací prvek je předáván funkci a poskytuje informace o zásobníku rámce a funkce argumenty. Tato funkce nahrazuje [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identifikátor funkce, do které se předá řízení.  
  
 `clientData`  
 [in] Identifikátor změnu mapování funkce, který dříve zadanou profileru pomocí [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.  
  
 `func`  
 [in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o zásobníku.  
  
 Profiler by měl považovat za to neprůhledného popisovače, který může být předán zpět prováděcí modul v [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.  
  
 `argumentInfo`  
 [in] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která určuje umístění v paměti argumentů funkce.  
  
 Aby bylo možné přistupovat k informací o argumentech, `COR_PRF_ENABLE_FUNCTION_ARGS` musí být nastaven příznak. Profiler může použít [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte příznaky událostí.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty `func` a `argumentInfo` parametry jsou neplatné po `FunctionEnter2` funkce vrátí hodnoty se mohou změnit nebo zničení.  
  
 `FunctionEnter2` Funkce je zpětné volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Prováděcí modul nelze uložit žádné registry před voláním této funkce.  
  
- Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).  
  
- Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.  
  
 Provádění `FunctionEnter2` by neměla blokovat, protože způsobí zpoždění uvolnění paměti. Implementace by se neměly pokoušet uvolňování paměti, protože zásobník nemusí být ve stavu přívětivá kolekce uvolnění paměti. Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionEnter2` vrátí.  
  
 Také `FunctionEnter2` funkce nesmí volat do spravovaného kódu nebo v jakékoli příčina způsob přidělování spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
