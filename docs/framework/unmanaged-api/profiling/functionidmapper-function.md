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
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440700"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper – funkce
Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)a [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) pro danou funkci. `FunctionIDMapper` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 pro Identifikátor funkce, která má být přemapována.  
  
 `pbHookFunction`  
 mimo Ukazatel na hodnotu, kterou Profiler nastaví, aby `true`, pokud chce přijímat `FunctionEnter2`, `FunctionLeave2`a zpětná volání `FunctionTailcall2`; v opačném případě nastaví tuto hodnotu na `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`. V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `FunctionIDMapper` je zpětné volání. Je implementován profilerem k přemapování ID funkce na jiný identifikátor, který je užitečnější pro Profiler. `FunctionIDMapper` vrátí alternativní ID, které se má použít pro libovolnou danou funkci. Spouštěcí modul pak dodrží požadavek profileru tím, že předá toto alternativní ID k tradičnímu ID funkce zpět do profileru v parametru `clientData` `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2`, aby identifikoval funkci, pro kterou je zavěšeno volání.  
  
 K určení implementace funkce `FunctionIDMapper` lze použít metodu [ICorProfilerInfo:: SetFunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) . Metodu `ICorProfilerInfo::SetFunctionIDMapper` lze volat pouze jednou a doporučujeme, abyste tak učinili v rámci zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .  
  
 Ve výchozím nastavení se předpokládá, že Profiler, který nastaví příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)a který nastavuje háky prostřednictvím [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), by měl přijímat zpětná volání `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2` pro každou funkci. Profilery ale mohou implementovat `FunctionIDMapper` pro selektivní zamezení příjmu těchto zpětných volání pro určité funkce nastavením `pbHookFunction` na `false`.  
  
 Profilery by měly být odolné vůči případům, kdy více vláken profilované aplikace volá stejnou metodu/funkci současně. V takových případech může Profiler získat více `FunctionIDMapper`ch zpětného volání pro stejný `FunctionID`. Profiler by měl být jistý, aby vracel stejné hodnoty z tohoto zpětného volání, pokud je volán několikrát se stejným `FunctionID`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [SetFunctionIDMapper – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
