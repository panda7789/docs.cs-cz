---
title: ICorProfilerInfo::GetEventMask – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2881dbe83b0d9f6e2ae3c4f478bbecdca444b78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991871"
---
# <a name="icorprofilerinfogeteventmask-method"></a>ICorProfilerInfo::GetEventMask – metoda
Získá aktuální kategorie událostí, pro které profileru chce obdržet oznámení událostí z common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEvents`  
 [out] Ukazatel na 4bajtovou hodnotu, která určuje kategorie událostí. Každý bit určuje různé možnosti, chování nebo typ události. Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Měli byste zavolat [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metoda namísto této metody. I když `SetEventMask` metody jsou nadále podporované, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
