---
title: "ICorProfilerCallback::ModuleUnloadFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f9f048d60d2d463e3d846fadda91932a9a2a091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a>ICorProfilerCallback::ModuleUnloadFinished – metoda
Aby modul dokončil uvolnění upozorní profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [v] ID modul, který byl odpojen.  
  
 `hrStatus`  
 [v] HRESULT, která určuje, zda byl modul úspěšně odpojen.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `moduleId` není platná pro požadavek informace po [icorprofilercallback::moduleunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) metoda vrátí.  
  
 Některé části uvolnění třídy, může pokračovat i po `ModuleUnloadFinished` zpětného volání. Selhání HRESULT v `hrStatus` znamená chybu. Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění modulu proběhl úspěšně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
