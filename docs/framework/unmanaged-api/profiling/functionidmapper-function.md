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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175171"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper – funkce
Upozorní profiler, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v [funkcích FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)a [FunctionTailcall2](functiontailcall2-function.md) pro tuto funkci. `FunctionIDMapper`také umožňuje profiler k označení, zda chce přijímat zpětná volání pro tuto funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in] Identifikátor funkce, který má být přemapován.

- `pbHookFunction`

  \[out] Ukazatel na hodnotu, kterou `true` nastaví profiler, `FunctionLeave2`pokud `FunctionTailcall2` chce přijímat `FunctionEnter2`, a zpětná volání; v opačném případě nastaví tuto hodnotu na `false`.

## <a name="return-value"></a>Návratová hodnota  
 Profiler vrátí hodnotu, která používá modul provádění jako alternativní identifikátor funkce. Vrácená hodnota nemůže `false` být null, pokud není vrácena v `pbHookFunction`. V opačném případě null vrácená hodnota bude mít nepředvídatelné výsledky, včetně případné zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `FunctionIDMapper` je zpětné volání. Je implementován profiler přemapovat ID funkce na jiný identifikátor, který je užitečnější pro profiler. Vrátí `FunctionIDMapper` alternativní ID, které má být použito pro danou funkci. Modul provádění pak respektuje profiler požadavek předáním tohoto alternativního ID, kromě tradiční id funkce, `clientData` zpět `FunctionEnter2`do `FunctionLeave2`profileru v parametru , a `FunctionTailcall2` háčky, k identifikaci funkce, pro které je volán hák.  
  
 Metodu [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) můžete použít k určení `FunctionIDMapper` implementace funkce. Můžete volat `ICorProfilerInfo::SetFunctionIDMapper` metodu pouze jednou a doporučujeme tak učinit v [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) zpětné volání.  
  
 Ve výchozím nastavení se předpokládá, že profiler, který nastaví příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), a který nastaví háčky přes [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) `FunctionEnter2`nebo `FunctionLeave2` [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), by měl přijímat , a `FunctionTailcall2` zpětná volání pro každou funkci. Profilovací programy však mohou implementovat `FunctionIDMapper` selektivně vyhnout přijímání `pbHookFunction` `false`těchto zpětná volání pro určité funkce nastavením na .  
  
 Profilovací programy by měly být tolerantní k případům, kdy více vláken profilované aplikace volá stejnou metodu/funkci současně. V takových případech profiler může `FunctionIDMapper` přijímat více zpětná volání pro stejné `FunctionID`. Profiler by měl být jistý vrátit stejné hodnoty z tohoto zpětného `FunctionID`volání, pokud je volána vícekrát se stejným .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [SetFunctionIDMapper – metoda](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 – funkce](functionidmapper2-function.md)
- [FunctionEnter2 – funkce](functionenter2-function.md)
- [FunctionLeave2 – funkce](functionleave2-function.md)
- [FunctionTailcall2 – funkce](functiontailcall2-function.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
