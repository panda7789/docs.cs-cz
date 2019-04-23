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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0106b2dd1151e302c0082b306d999ab5a1c4322
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177746"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo – metoda
Získá hodnotu, která označuje druh statické, které platí pro zadané pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] ID třídy, ve kterém je definována statické pole.  
  
 `fieldToken`  
 [in] Token metadat pro statické pole.  
  
 `pFieldInfo`  
 [out] Ukazatel na hodnotu [cor_prf_static_type –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) výčet určující, zda je zadané pole statické, a pokud ano, druh statické, která platí pro pole.  
  
## <a name="remarks"></a>Poznámky  
 Tyto informace slouží k určení funkce volání za účelem získání adresy statické pole.  
  
 Profiler kódu, měli byste zkontrolovat metadata pro statické pole k zajištění, že ve skutečnosti má adresu. Statických literálů (to znamená, konstanty) existují pouze v metadatech a nemají adresu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
