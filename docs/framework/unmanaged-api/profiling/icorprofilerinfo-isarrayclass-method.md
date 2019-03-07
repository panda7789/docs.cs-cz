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
ms.openlocfilehash: bf8e74094b15163fe86e18c397f4637557df8329
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468231"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass – metoda
Určuje, zda dané třídy je třída pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] ID třídy prověřit.  
  
 `pBaseElemType`  
 [out] Ukazatel na hodnotu corelementtype – výčet, který označuje typ prvků pole.  
  
 `pBaseClassId`  
 [out] Ukazatel na ID třídy prvků pole, pokud je k dispozici.  
  
 `pcRank`  
 [out] Ukazatel na celé číslo označující pořadí (to znamená, počet rozměrů) v poli.  
  
## <a name="remarks"></a>Poznámky  
 Pokud dané třídy je třída pole, `IsArrayClass` metoda vrátí hodnotu S_OK HRESULT a hodnoty pro všechny nenulové výstupní parametry. V opačném případě vrátí S_FALSE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
