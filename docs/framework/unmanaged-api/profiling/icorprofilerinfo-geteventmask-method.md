---
title: "ICorProfilerInfo::GetEventMask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f8bfc0dc5686aa560bfa8282256b5e476976136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogeteventmask-method"></a>ICorProfilerInfo::GetEventMask – metoda
Získá aktuální kategorií událostí, pro které profileru chce dostávat oznámení o událostech, modul CLR (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwEvents`  
 [out] Ukazatel na hodnotu 4 bajtů, která určuje kategorie události. Každý bit řídí jinou možnost, chování nebo typ události. Službu bits, jsou popsané v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Měli byste zavolat [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metoda namísto této metody. I když `SetEventMask` metoda nadále podporován, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
