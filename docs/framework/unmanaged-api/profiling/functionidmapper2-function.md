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
ms.openlocfilehash: af0ef412395394bb660ae6ed64fb154caef41655
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866915"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 – funkce
Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md), nebo[Functionenter3withinfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) pro danou funkci. `FunctionIDMapper2` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[v] identifikátor funkce, který se má přemapovat.

- `clientData`

  \[in] ukazatel na data, která se používají k jednoznačnému rozlišení mezi moduly runtime.

- `pbHookFunction`

  \[] ukazatel na hodnotu, kterou Profiler nastaví na `true`, pokud chce přijmout `FunctionEnter3`, `FunctionLeave3`a `FunctionTailcall3`nebo `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`a `FunctionTailcall3WithInfo` zpětná volání. v opačném případě nastaví tuto hodnotu na `false`.

## <a name="return-value"></a>Návratová hodnota  
 Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`. V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje funkci [FunctionIDMapper –](functionidmapper-function.md) o další parametr, který se používá k předání dat klienta. Data klienta slouží k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3::SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Globální statické funkce pro profilaci](profiling-global-static-functions.md)
