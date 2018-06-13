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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f34fee19c796f65d315fcbd26d55e1d5322303a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453025"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass – metoda
Určuje, zda je pro zadanou třídu třídu pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] ID třídy prověřit.  
  
 `pBaseElemType`  
 [out] Ukazatel na hodnotu CorElementType – výčet, který určuje typ prvků pole.  
  
 `pBaseClassId`  
 [out] Ukazatel na ID třídy prvků pole, pokud je k dispozici.  
  
 `pcRank`  
 [out] Ukazatel na celé číslo, které určuje pořadí pole (tj, počet dimenzí).  
  
## <a name="remarks"></a>Poznámky  
 Pokud pro zadanou třídu je třída pole, `IsArrayClass` metoda vrátí S_OK HRESULT a hodnoty pro všechny nesmí být nulová výstupní parametry. V opačném případě vrátí S_FALSE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
