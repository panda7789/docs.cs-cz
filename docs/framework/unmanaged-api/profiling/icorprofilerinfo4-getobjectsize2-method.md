---
title: "ICorProfilerInfo4::GetObjectSize2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetObjectSize2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0aa13a056929c9cb4f63c52f1e993f110cfca7be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 – metoda
Vrátí velikost zadaný objekt. Nahradí [icorprofilerinfo::getobjectsize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metoda velikosti objektů, které jsou větší než co může být vyjádřený v generování sestav `ULONG`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `objectId`  
 [v] ID objektu.  
  
 `pcSize`  
 [out] Ukazatel na objektu velikost v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Různé objekty stejné typy často mít stejnou velikost. Některé typy, jako je například pole nebo řetězce, ale může mít různou velikost pro každý objekt.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
