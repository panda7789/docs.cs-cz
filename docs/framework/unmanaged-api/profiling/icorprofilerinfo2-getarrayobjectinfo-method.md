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
ms.openlocfilehash: 368b8f270797beb525e0745a29990667913f4071
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497349"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo – metoda
Získá podrobné informace o objektu Array.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 pro ID platného objektu Array.  
  
 `cDimensions`  
 pro Pořadí (počet rozměrů) pole.  
  
 `pDimensionSizes`  
 mimo Pole obsahující celá čísla, která představují velikost rozměru pole.  
  
 `pDimensionLowerBounds`  
 mimo Pole obsahující celá čísla, z nichž každá představuje dolní mez dimenze pole.  
  
 `ppData`  
 mimo Ukazatel na adresu nezpracované vyrovnávací paměti pro pole, které je stanoveno podle konvence jazyka C++.  
  
## <a name="remarks"></a>Poznámky  
 `pDimensionSizes`A `pDimensionLowerBounds` jsou paralelní pole, takže prvky nacházející se ve stejném indexu v každém poli jsou charakteristiky stejné entity.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
