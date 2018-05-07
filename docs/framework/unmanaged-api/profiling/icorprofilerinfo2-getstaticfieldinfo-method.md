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
ms.openlocfilehash: f2ab0d482366b037f92a55f00dd33df8a312e84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo – metoda
Získá hodnotu, která určuje druh static, která platí pro zadané pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] ID třídy, ve kterém je definovaný statické pole.  
  
 `fieldToken`  
 [v] Token metadata pro statické pole.  
  
 `pFieldInfo`  
 [out] Ukazatel na hodnotu [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) výčet určující, zda je zadané pole statické, a pokud ano, druh static, platí pro pole.  
  
## <a name="remarks"></a>Poznámky  
 Tyto informace slouží k určení, které slouží k volání k získání adresy statického pole.  
  
 Kód profileru, měli byste zkontrolovat metadata pro statické pole zajistit, že je ve skutečnosti adresu. Statické literály (konstanty) existují pouze v metadatech a nemají adresu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
