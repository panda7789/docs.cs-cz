---
title: FunctionIDMapper – funkce
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866941"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper – funkce
Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](functionenter2-function.md), [FunctionLeave2 –](functionleave2-function.md)a [FunctionTailcall2 –](functiontailcall2-function.md) pro danou funkci. `FunctionIDMapper` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[v] identifikátor funkce, který se má přemapovat.

- `pbHookFunction`

  \[] ukazatel na hodnotu, kterou Profiler nastaví na `true`, pokud chce přijímat zpětná volání `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2`; v opačném případě nastaví tuto hodnotu na `false`.

## <a name="return-value"></a>Návratová hodnota  
 Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`. V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `FunctionIDMapper` je zpětné volání. Je implementován profilerem k přemapování ID funkce na jiný identifikátor, který je užitečnější pro Profiler. `FunctionIDMapper` vrátí alternativní ID, které se má použít pro libovolnou danou funkci. Spouštěcí modul pak dodrží požadavek profileru tím, že předá toto alternativní ID k tradičnímu ID funkce zpět do profileru v parametru `clientData` `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2`, aby identifikoval funkci, pro kterou je zavěšeno volání.  
  
 K určení implementace funkce `FunctionIDMapper` lze použít metodu [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md) . Metodu `ICorProfilerInfo::SetFunctionIDMapper` lze volat pouze jednou a doporučujeme, abyste tak učinili v rámci zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .  
  
 Ve výchozím nastavení se předpokládá, že Profiler, který nastaví příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)a který nastavuje háky prostřednictvím [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), by měl přijímat zpětná volání `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2` pro každou funkci. Profilery ale mohou implementovat `FunctionIDMapper` pro selektivní zamezení příjmu těchto zpětných volání pro určité funkce nastavením `pbHookFunction` na `false`.  
  
 Profilery by měly být odolné vůči případům, kdy více vláken profilované aplikace volá stejnou metodu/funkci současně. V takových případech může Profiler získat více `FunctionIDMapper`ch zpětného volání pro stejný `FunctionID`. Profiler by měl být jistý, aby vracel stejné hodnoty z tohoto zpětného volání, pokud je volán několikrát se stejným `FunctionID`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [SetFunctionIDMapper – metoda](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 – funkce](functionidmapper2-function.md)
- [FunctionEnter2 – funkce](functionenter2-function.md)
- [FunctionLeave2 – funkce](functionleave2-function.md)
- [FunctionTailcall2 – funkce](functiontailcall2-function.md)
- [Globální statické funkce pro profilaci](profiling-global-static-functions.md)
