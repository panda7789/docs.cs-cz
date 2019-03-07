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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71c7dcc5d337e7585e380981cc2ec4b5192e5151
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481726"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 – funkce
Oznámí profileru, že daný identifikátor funkce může přemapován na alternativní ID se použije v [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) zpětná volání pro tuto funkci. `FunctionIDMapper2` také umožňuje profileru označíte, zda si přeje přijmout zpětná volání pro tuto funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identifikátor funkce pro přemapování.  
  
 `clientData`  
 [in] Ukazatel na data, která se používá k rozlišení mezi moduly runtime.  
  
 `pbHookFunction`  
 [out] Ukazatel na hodnotu, která profiler nastaví na `true` Pokud chce přijmout `FunctionEnter3`, `FunctionLeave3`, a `FunctionTailcall3`, nebo `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, a `FunctionTailcall3WithInfo` zpětná volání; jinak nastaví tuto hodnotu a `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Profiler vrací hodnotu, která spouštěcí modul používá jako alternativní identifikátor funkce. Návratová hodnota nemůže mít hodnotu null není-li `false` se vrátí v `pbHookFunction`. Jinak nulová návratová hodnota vytváří nepředvídatelné výsledky včetně případného zastavení procesu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce s dalším parametrem, který se používá k předávání dat klienta. Data klienta se používají k rozlišování mezi moduly runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3::SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
