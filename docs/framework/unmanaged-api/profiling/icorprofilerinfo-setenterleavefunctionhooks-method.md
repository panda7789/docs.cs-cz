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
ms.openlocfilehash: a2d45e98f3e7b71375b14c43c4bff4929bc79494
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860933"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda
Určuje profiler implementovat funkce dřív říkalo "zadejte", "ponechte" a "tailcall" háky spravované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
