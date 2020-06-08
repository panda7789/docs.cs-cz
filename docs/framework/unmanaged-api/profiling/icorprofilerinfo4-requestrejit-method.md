---
title: ICorProfilerInfo4::RequestReJIT – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: 7dd82f2dfab885070df4789fe5efc16a49d50e06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495798"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT – metoda
Vyžádá rekompilaci JIT všech instancí zadaných funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 pro Počet funkcí, které mají být rekompilovány.  
  
 `moduleIds`  
 pro Určuje `moduleId` část `module` párů (, `methodDef` ), které identifikují funkce, které mají být znovu zkompilovány.  
  
 `methodIds`  
 pro Určuje `methodId` část `module` párů (, `methodDef` ), které identifikují funkce, které mají být znovu zkompilovány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Byl proveden pokus o označení všech metod pro rekompilaci JIT. Profiler musí implementovat metodu [ICorProfilerCallback4:: rejiterror –](icorprofilercallback4-rejiterror-method.md) k určení, které metody byly úspěšně označeny pro rekompilaci JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Aby bylo toto volání podporováno, Profiler musí implementovat rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .|  
|CORPROF_E_REJIT_NOT_ENABLED|Opětovná kompilace JIT není povolená. Je nutné povolit opětovnou kompilaci JIT během inicializace pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení `COR_PRF_ENABLE_REJIT` příznaku.|  
|E_INVALIDARG|`cFunctions`je 0 nebo `moduleIds` nebo `methodIds` `NULL` .|  
|||  
|E_OUTOFMEMORY|Modul CLR nemohl dokončit požadavek, protože nemá dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Volání, `RequestReJIT` aby modul runtime znovu zkompiluje zadanou sadu funkcí. Profiler kódu pak může použít rozhraní [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) k úpravě kódu, který je generován při rekompilaci funkcí. Tato akce nemá vliv na aktuálně vykonávané funkce, a to pouze na budoucí vyvolání funkce. Pokud byla kterákoli z určených funkcí dříve znovu zkompilována za běhu, požadavek na opětovnou kompilaci je stejný jako vrácení a opětovné kompilování funkce. Chcete-li zachovat reversibility, když kompilátor JIT zkompiluje původní verzi funkce, považuje se za rozhodnutí o vkládání pouze původní verze svých volané. Když kompilátor JIT znovu zkompiluje funkci, považuje aktuální verze (rekompilováno nebo originál) své volané pro vkládání.  
  
 Profiler obvykle volá `RequestReJIT` reakci na vstup uživatele, který vyžaduje, aby nástroj profiler vyvolal jednu nebo více metod. `RequestReJIT`obvykle pozastaví modul runtime za účelem provedení některé z jeho práce a může potenciálně aktivovat uvolňování paměti. V takovém případě by Profiler měl volat `RequestReJIT` z dříve vytvořeného vlákna a nikoli z vlákna vytvořeného modulem CLR, který aktuálně provádí zpětné volání profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
