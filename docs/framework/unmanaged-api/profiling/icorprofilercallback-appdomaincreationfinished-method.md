---
title: ICorProfilerCallback::AppDomainCreationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 1cf3f2b62b388b6c2d6fcd75b1b07a67d5b2e49f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866699"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished – metoda
Oznamuje profileru, že byla vytvořena doména aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a>Parametry

- `appDomainId`

  \[v] identifikuje doménu, která byla vytvořena.

- `hrStatus`

  \[in] hodnota HRESULT, která indikuje, jestli se úspěšně dokončilo vytváření domény aplikace.

## <a name="remarks"></a>Poznámky  
 ID aplikace není platné pro žádnou žádost o informace, dokud není volána metoda `AppDomainCreationFinished`.  
  
 Některé části načtení aplikační domény můžou po zpětném volání `AppDomainCreationFinished` pokračovat. Selhání HRESULT v `hrStatus` označuje selhání. Úspěšnost HRESULT v `hrStatus` však znamená, že první část vytváření domény aplikace byla úspěšně dokončena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
