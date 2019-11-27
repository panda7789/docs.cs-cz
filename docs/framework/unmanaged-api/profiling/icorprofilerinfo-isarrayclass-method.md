---
title: ICorProfilerInfo::IsArrayClass – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 57515ac4670b9b7e25bb496851347a62e1b246df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438726"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass – metoda
Určuje, zda je zadaná třída třídou Array.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 pro ID třídy, která se má prozkoumat  
  
 `pBaseElemType`  
 mimo Ukazatel na hodnotu výčtu CorElementType –, která určuje typ prvků pole.  
  
 `pBaseClassId`  
 mimo Ukazatel na ID třídy prvků pole, je-li k dispozici.  
  
 `pcRank`  
 mimo Ukazatel na celé číslo, které určuje pořadí (tj. počet rozměrů) pole.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zadaná třída třídou Array, metoda `IsArrayClass` vrátí S_OK HRESULT a hodnoty pro výstupní parametry, které nejsou null. V opačném případě vrátí S_FALSE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
