---
title: ICorProfilerCallback::AppDomainShutdownStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd1e5daada8793e94980afc5f0cf509915bd288e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a>ICorProfilerCallback::AppDomainShutdownStarted – metoda
Upozorní profileru, že domény aplikace odpojení z procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `appDomainId`  
 [v] Určuje doménu, ve kterém jsou uloženy sestavení aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `appDomainId` není platná pro všechny žádosti o informace po `AppDomainShutdownStarted` metoda vrátí – Toto je poslední možnost okna profilování a získat informace o této domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
