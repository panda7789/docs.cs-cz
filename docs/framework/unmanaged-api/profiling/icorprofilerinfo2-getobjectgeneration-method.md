---
title: ICorProfilerInfo2::GetObjectGeneration – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: 1263202c1fe524c924a88b9356e5ab9116cea553
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502857"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration – metoda
Načte segment haldy, která obsahuje zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 pro ID objektu  
  
 `range`  
 mimo Ukazatel na strukturu [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , která popisuje rozsah (tj. blok) paměti v rámci generace, která je podchází uvolňování paměti. Tento rozsah obsahuje zadaný objekt.  
  
## <a name="remarks"></a>Poznámky  
 `GetObjectGeneration`Metodu lze volat z jakéhokoliv zpětného volání profileru za předpokladu, že uvolňování paměti neprobíhá. To znamená, že může být volána z libovolného zpětného volání s výjimkou těch, ke kterým dochází mezi [ICorProfilerCallback2:: GarbageCollectionStarted –](icorprofilercallback2-garbagecollectionstarted-method.md) a [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
