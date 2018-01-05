---
title: "ICorProfilerCallback::ModuleAttachedToAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6183014bf5487d0eebccf2fb70a13c363212046b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly – metoda
Upozorní profileru, že se modul připojen k její nadřazené sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [v] ID modulu, který bude připojen.  
  
 `AssemblyId`  
 [v] ID nadřazené sestavení, ke kterému je připojený modul.  
  
## <a name="remarks"></a>Poznámky  
 Modul lze načíst prostřednictvím tabulku importních adres (IAT), prostřednictvím volání `LoadLibrary`, nebo prostřednictvím odkazu metadat. V důsledku toho běžné zavaděč language runtime (CLR) má více cest kód pro určení sestavení, ve kterém je umístěn modul. Proto je možné, že po [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) je volána, modul nebude vědět, jaké sestavení je v a získání ID nadřazeného sestavení není možné. `ModuleAttachedToAssembly` Metoda je volána, když modul je připojen k její nadřazené sestavení a její nadřazené sestavení nelze získat ID.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
