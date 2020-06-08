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
ms.openlocfilehash: 722a1e0adea41a13ca25829c53372c29187b80bd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500465"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished – metoda
Upozorní profileru, že doména aplikace byla uvolněna z procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `appDomainId`

  \[v] identifikuje doménu, ve které jsou uložena sestavení aplikace.

- `hrStatus`

  \[in] HRESULT, který označuje, zda byla doména aplikace úspěšně uvolněna.

## <a name="remarks"></a>Poznámky  
 Hodnota `appDomainId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: appdomainshutdownstarted –](icorprofilercallback-appdomainshutdownstarted-method.md) .  
  
 Některé části odložení aplikační domény můžou pokračovat i po `AppDomainCreationFinished` zpětném volání. Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání. Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část uvolňování domény aplikace byla úspěšně dokončena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
