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
ms.openlocfilehash: 65c5d2d4f288d927d79c233374edfec54c0b77ae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500647"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 – funkce
Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md), nebo[Functionenter3withinfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) pro danou funkci. `FunctionIDMapper2`také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
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

  \[v] identifikátor funkce, která má být přemapována.

- `clientData`

  \[in] ukazatel na data, která se používají k jednoznačnému rozlišení mezi moduly runtime.

- `pbHookFunction`

  \[out] ukazatel na hodnotu, na kterou Profiler nastavuje `true` , pokud chce přijímat `FunctionEnter3` , `FunctionLeave3` , a `FunctionTailcall3` , nebo `FunctionEnter3WithInfo` , `FunctionLeave3WithInfo` a `FunctionTailcall3WithInfo` zpětná volání; v opačném případě nastaví tuto hodnotu na `false` .

## <a name="return-value"></a>Návratová hodnota  
 Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže být null, pokud `false` není vrácena v `pbHookFunction` . V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje funkci [FunctionIDMapper –](functionidmapper-function.md) o další parametr, který se používá k předání dat klienta. Data klienta slouží k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3:: Setfunctionidmapper2 –](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](functiontailcall3withinfo-function.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
