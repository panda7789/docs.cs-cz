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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2de19252b5c978fef38124636e4098ae5ece1b0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097935"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper – funkce
Oznámí profileru, že daný identifikátor funkce může přemapován na alternativní ID se použije v [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětná volání pro tuto funkci. `FunctionIDMapper` také umožňuje profileru označíte, zda si přeje přijmout zpětná volání pro tuto funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identifikátor funkce pro přemapování.  
  
 `pbHookFunction`  
 [out] Ukazatel na hodnotu, která profiler nastaví na `true` Pokud chce přijmout `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětná volání; jinak nastaví tuto hodnotu na `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Profiler vrací hodnotu, která spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže mít hodnotu null není-li `false` se vrátí v `pbHookFunction`. Návratovou hodnotou null, jinak bude mít nepředvídatelné výsledky, včetně případného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionIDMapper` Je funkce zpětného volání. Je implementováno pomocí profileru přemapování ID funkce na jiný identifikátor, který je užitečnější profileru. `FunctionIDMapper` Vrátí alternativní ID se má použít pro jakékoli dané funkce. Prováděcí modul pak respektuje předáním této alternativní ID, kromě ID tradičních funkce zpět do okna profilování v profileru požadavek `clientData` parametr `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` háky k identifikaci Funkce, pro který se nazývá zavěšení.  
  
 Můžete použít [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metodu k určení provádění `FunctionIDMapper` funkce. Můžete volat `ICorProfilerInfo::SetFunctionIDMapper` metoda pouze jednou a My doporučujeme, abyste udělali, [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.  
  
 Ve výchozím nastavení, předpokládá se, že profiler, který nastavuje příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), a který nastaví háky prostřednictvím [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), mělo by se zobrazit `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětná volání pro každou funkci. Však může implementovat profilery `FunctionIDMapper` selektivně zabránili tato zpětná volání pro určité funkce tak, že nastavíte `pbHookFunction` k `false`.  
  
 Profilovací programy by měl být odolný vůči chybám případů, kdy více vláken profilované aplikace jsou volání stejné metody/funkce současně. V takových případech může profiler se zobrazit více `FunctionIDMapper` zpětná volání pro stejnou `FunctionID`. Profiler by měl být určité vrácení stejné hodnoty z této zpětné volání, když je volána více než jednou se stejným `FunctionID`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [SetFunctionIDMapper – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
