---
title: ICorProfilerInfo2::GetArrayObjectInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6e6f4f6bdfba8deecb3661d88a881759da043ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo – metoda
Získá podrobné informace o objektu array.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a>Parametry  
 `objectId`  
 [v] ID objektu platné pole.  
  
 `cDimensions`  
 [v] Pořadí (počet dimenzí) pole.  
  
 `pDimensionSizes`  
 [out] Pole, které obsahuje celá čísla, každý představuje velikost dimenze pole.  
  
 `pDimensionLowerBounds`  
 [out] Pole obsahující celá čísla, každý představuje dolní hranice elementu dimenze pole.  
  
 `ppData`  
 [out] Ukazatel na adresu nezpracovaná vyrovnávací paměti pro pole, které je rozložená podle konvence C++.  
  
## <a name="remarks"></a>Poznámky  
 `pDimensionSizes` a `pDimensionLowerBounds` jsou paralelní pole, takže prvky umístěné ve stejném indexu v každém poli jsou charakteristické vlastnosti třídy na stejnou entitu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
