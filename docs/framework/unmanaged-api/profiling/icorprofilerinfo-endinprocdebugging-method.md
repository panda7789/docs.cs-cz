---
title: ICorProfilerInfo::EndInprocDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf7e2e7de54b065f25f3a1873d760ab5051cc91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a>ICorProfilerInfo::EndInprocDebugging – metoda
Ukončí relaci ladění v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProfilerContext`  
 [v] Hodnota, která identifikuje relaci ladění. Tato hodnota musí být stejný jako dostali [icorprofilerinfo::begininprocdebugging –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metoda.  
  
## <a name="remarks"></a>Poznámky  
 Je třeba volat [icorprofilerinfo::begininprocdebugging –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) a `EndInprocDebugging` v rámci stejné metody zpětného volání.  
  
 Ladění služby CLR podporované omezené v procesu ladění v rozhraní .NET Framework verze 1.0 a 1.1. V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění. Však z důvodu zpětné vazby zákazníka, v rámci procesu ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
