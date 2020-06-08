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
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500491"
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

  \[in] HRESULT, který označuje, zda bylo úspěšně vytvořeno vytvoření domény aplikace.

## <a name="remarks"></a>Poznámky  
 ID aplikace není platné pro žádnou žádost o informace, dokud `AppDomainCreationFinished` není volána metoda.  
  
 Některé části načtení aplikační domény můžou pokračovat i po `AppDomainCreationFinished` zpětném volání. Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání. Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část vytváření domény aplikace byla úspěšně dokončena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
