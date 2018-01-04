---
title: "ICorProfilerCallback::FunctionUnloadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.FunctionUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 957b5a89dbb3e780b0e5512afe405e669fdbecce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a>ICorProfilerCallback::FunctionUnloadStarted – metoda
Upozorní profileru, že modul runtime bylo zahájeno Unload funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která odpojení.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `functionId` parametr je platný už po návratu tato metoda volajícímu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
