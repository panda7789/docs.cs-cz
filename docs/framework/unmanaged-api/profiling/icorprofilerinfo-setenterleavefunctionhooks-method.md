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
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497449"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda
Určuje funkce implementované profilerem, které mají být volány u funkcí "Enter", "opustit" a "Tailcall" u spravovaných funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionEnter –](functionenter-function.md) zpětné volání.  
  
 `pFuncLeave`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionLeave –](functionleave-function.md) zpětné volání.  
  
 `pFuncTailcall`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionTailcall –](functiontailcall-function.md) zpětné volání.  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 1,0 může mít každý ukazatel na funkci hodnotu null, aby bylo toto odpovídající zpětné volání zakázáno.  
  
 V jednom okamžiku může být aktivní jenom jedna sada zpětných volání. Proto pokud profiler volá jak `SetEnterLeaveFunctionHooks` a [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), pak `SetEnterLeaveFunctionHooks2` má přednost.  
  
 `SetEnterLeaveFunctionHooks`Metodu lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
