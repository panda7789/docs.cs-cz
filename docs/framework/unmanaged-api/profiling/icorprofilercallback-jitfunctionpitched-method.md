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
ms.openlocfilehash: 2715a5b6b03a5ad33a6f18fb736fce3911bfbef0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500023"
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
  
 Hodnota `functionId` není platná, dokud není funkce znovu zkompilována. Když je funkce znovu zkompilována, `functionId` bude použita stejná hodnota.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
