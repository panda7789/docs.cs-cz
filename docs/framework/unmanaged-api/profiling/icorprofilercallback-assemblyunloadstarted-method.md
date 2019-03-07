---
title: ICorProfilerCallback::AssemblyUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a45c757a9176c77c7dbf58333b66d9b26514265
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471209"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a>ICorProfilerCallback::AssemblyUnloadStarted – metoda
Oznámí profileru, že je sestavení uvolňován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Určuje sestavení, které uvolňován.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `assemblyId` není platná pro požadavek informace po `AssemblyUnloadStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru a získat informace o tomto sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [AssemblyUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
