---
title: ICorProfilerCallback::JITFunctionPitched – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 9bb3934be4a2f4de4a3a235a00522c801331e1eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448427"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched – metoda
Upozorní profileru, že byla z paměti odebrána funkce, která byla zkompilována za běhu (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID odebrané funkce  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zavolána funkce odebrané, Profiler obdrží nové události kompilace JIT, když je funkce znovu zkompilována. Kompilátor JIT (Common Language Runtime) v současné době neodebere funkce z paměti, takže toto zpětné volání se v tuto chvíli nepoužívá a profil nebude přijímat.  
  
 Hodnota `functionId` není platná, dokud nebude funkce znovu zkompilována. Když je funkce znovu zkompilována, bude použita stejná hodnota `functionId`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
