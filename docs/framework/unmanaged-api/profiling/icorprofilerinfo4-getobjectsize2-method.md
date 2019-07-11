---
title: ICorProfilerInfo4::GetObjectSize2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f72984da8f75eec35517da6ec1f8a73bc96c4609
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780807"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 – metoda
Vrátí velikost zadaného objektu. Nahrazuje [icorprofilerinfo::getobjectsize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metody pomocí generování sestav velikosti objektů, které jsou větší, než co lze vyjádřit v `ULONG`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] ID objektu.  
  
 `pcSize`  
 [out] Ukazatel objekt velikost v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Různé objekty stejné typy často mají stejnou velikost. Některé typy, například pole nebo řetězce, ale může mít jinou velikost pro každý objekt.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
