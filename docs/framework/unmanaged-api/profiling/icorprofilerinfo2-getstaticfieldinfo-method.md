---
title: ICorProfilerInfo2::GetStaticFieldInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: e74bab058adda759db1fb549022608eedfef5d80
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432985"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo – metoda
Získá hodnotu, která označuje druh statického typu, který se vztahuje k určenému poli.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 pro ID třídy, ve které je definováno statické pole.  
  
 `fieldToken`  
 pro Token metadat pro statické pole  
  
 `pFieldInfo`  
 mimo Ukazatel na hodnotu výčtu [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) , která označuje, zda je zadané pole statické, a pokud ano, druh statického, který se vztahuje k poli.  
  
## <a name="remarks"></a>Poznámky  
 Tyto informace lze použít k určení, která funkce má být volána, aby získala adresu statického pole.  
  
 Kód profileru by měl stále kontrolovat metadata pro statické pole, aby se zajistilo, že má ve skutečnosti adresu. Statické literály (tj. konstanty) existují pouze v metadatech a nemají adresu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
