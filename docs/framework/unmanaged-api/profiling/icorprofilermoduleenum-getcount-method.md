---
title: "ICorProfilerModuleEnum::GetCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.GetCount Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62cc7122e25d43998053f0f102e1079252d4d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumgetcount-method"></a>ICorProfilerModuleEnum::GetCount – metoda
Získá počet spravované moduly, které byly načteny do aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [out] Počet modulů runtime v kolekci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
