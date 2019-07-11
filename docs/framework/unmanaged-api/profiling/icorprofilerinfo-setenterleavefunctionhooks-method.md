---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b6f53d5747eca00b898b2cde66d75764ca490cf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772103"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda
Určuje profiler implementovat funkce dřív říkalo "zadejte", "ponechte" a "tailcall" háky spravované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 [in] Ukazatel na implementaci pro použití jako [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) zpětného volání.  
  
 `pFuncLeave`  
 [in] Ukazatel na implementaci pro použití jako [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) zpětného volání.  
  
 `pFuncTailcall`  
 [in] Ukazatel na implementaci pro použití jako [functiontailcall –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) zpětného volání.  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 1.0 může mít hodnotu null pro zakázání tohoto odpovídající zpětného volání každé ukazatel na funkci.  
  
 Najednou může být aktivní pouze jednu sadu zpětná volání. Proto pokud profiler volá obě `SetEnterLeaveFunctionHooks` a [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), pak `SetEnterLeaveFunctionHooks2` přednost.  
  
 `SetEnterLeaveFunctionHooks` Metodu lze volat pouze z okna profilování [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
