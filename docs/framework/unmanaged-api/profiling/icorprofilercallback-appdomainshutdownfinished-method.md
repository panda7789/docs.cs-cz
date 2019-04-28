---
title: ICorProfilerCallback::AppDomainShutdownFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d927bd21903bda6fd8a34992145eb495a3342382
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598256"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished – metoda
Oznámí profileru, že byl odpojen od procesu domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `appDomainId`  
 [in] Určuje doménu, ve kterém jsou uložené sestavení aplikace.  
  
 `hrStatus`  
 [in] HRESULT, která určuje, zda byla doména aplikace úspěšně odpojen.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `appDomainId` není platná pro požadavek informace po [icorprofilercallback::appdomainshutdownstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) metoda vrátí hodnotu.  
  
 Některé části uvolnění domény aplikace může pokračovat po `AppDomainCreationFinished` zpětného volání. Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu. Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolnění domény aplikace proběhla úspěšně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
