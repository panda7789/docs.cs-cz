---
title: FunctionIDMapper2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 7f83469920956d73a275f510b0d3c3e94a4caa8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440680"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 – funkce
Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) pro danou funkci. `FunctionIDMapper2` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 pro Identifikátor funkce, která má být přemapována.  
  
 `clientData`  
 pro Ukazatel na data, která se používají k jednoznačnému rozlišení mezi moduly runtime.  
  
 `pbHookFunction`  
 mimo Ukazatel na hodnotu, kterou Profiler nastaví na `true`, pokud chce přijmout `FunctionEnter3`, `FunctionLeave3`a `FunctionTailcall3`nebo `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`a `FunctionTailcall3WithInfo` zpětná volání; v opačném případě nastaví tuto hodnotu na `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`. V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje funkci [FunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) o další parametr, který se používá k předání dat klienta. Data klienta slouží k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo:: SetFunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3:: Setfunctionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [Functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [Functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
