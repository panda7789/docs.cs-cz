---
title: ICorProfilerCallback::AssemblyUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d757a0455992bc82ead922a5fbf4c71f11a9085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished – metoda
Upozorní profileru sestavení byl odpojen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemblyId`  
 [v] Identifikuje sestavení, které odpojení.  
  
 `hrStatus`  
 [v] HRESULT, která určuje, zda byla sestavení úspěšně odpojen.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `assemblyId` není platná pro požadavek informace po [icorprofilercallback::assemblyunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) metoda vrátí.  
  
 Některé části uvolnění sestavení může pokračovat po `AssemblyUnloadFinished` zpětného volání. Selhání HRESULT v `hrStatus` znamená chybu. Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění sestavení proběhl úspěšně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
