---
title: "FunctionIDMapper – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper
helpviewer_keywords: FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 629bcd5085169fcb136884c53434c29d385642cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper-function"></a>FunctionIDMapper – funkce
Profileru upozorní, že daným identifikátorem funkce může namapovat na alternativní ID, které má být používány [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětných volání pro tuto funkci. `FunctionIDMapper`taky umožňuje profileru indikující, zda chce dostávat zpětných volání pro tuto funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [v] Identifikátor funkce přemapování.  
  
 `pbHookFunction`  
 [out] Ukazatel na hodnotu, která nastaví profileru `true` Pokud chce dostávat `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětná volání; jinak, nastaví tato hodnota `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Profileru vrátí hodnotu, která modul provádění používá jako identifikátor alternativní funkce. Návratová hodnota nemůže být null. Pokud `false` je vrácený v `pbHookFunction`. Návratovou hodnotou null, jinak bude mít nepředvídatelné výsledky, včetně pravděpodobně zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionIDMapper` Je funkce zpětného volání. Je implementováno profileru přemapování funkce ID na některé identifikátor, který je užitečnější pro profileru. `FunctionIDMapper` Vrátí alternativní ID, který se má použít pro jakékoli dané funkce. Spouštěcí modul potom splňuje požadavek profileru pomocí předání této alternativní ID, kromě ID tradiční funkce profileru v `clientData` parametr `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` háky k identifikaci Funkce, pro kterou je volána hák.  
  
 Můžete použít [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metoda k určení implementace `FunctionIDMapper` funkce. Můžete volat `ICorProfilerInfo::SetFunctionIDMapper` metoda jenom jednou a My doporučujeme, abyste provedli takže v [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.  
  
 Ve výchozím nastavení, se předpokládá, že profileru, který nastavuje příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), a který nastaví háky prostřednictvím [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), mělo by se zobrazit `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětných volání pro každou funkci. Však může implementovat profilery `FunctionIDMapper` selektivně tomu, aby tyto zpětných volání pro určité funkce nastavením `pbHookFunction` k `false`.  
  
 Profilery by měl být odolný vůči chybám případů, kdy několik vláken PROFILOVANÉHO aplikace jsou volání stejné metody nebo funkce současně. V takových případech profileru obdržet více `FunctionIDMapper` zpětných volání pro stejné `FunctionID`. Profileru by měl být jistý, vrácení stejné hodnoty z této zpětného volání při volání víckrát se stejným `FunctionID`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Setfunctionidmapper – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [Functionidmapper2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [Functionenter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [Functionleave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Functiontailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [Profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
