---
title: ICorProfilerInfo3::GetStringLayout2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57a21a3e4c1324e15a8418dacb8cfe7c5163f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2 – metoda
Získá informace o rozložení objektu řetězce. Tato metoda nahrazuje [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStringLengthOffset`  
 [out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, uchovávající délky řetězce sám sebe. Délka se ukládají jako `DWORD`.  
  
 `pBufferOffset`  
 [out] Ukazatel na posun vyrovnávací paměti, relativně k `ObjectID` ukazatele, který ukládá řetězec široké znaky.  
  
## <a name="remarks"></a>Poznámky  
 Řetězce mohou nebo nemusí být ukončené hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
