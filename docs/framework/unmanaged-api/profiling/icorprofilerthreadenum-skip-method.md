---
title: ICorProfilerThreadEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 4218faf1c324175424ab20305224f7f2fa51bb7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494212"
---
# <a name="icorprofilerthreadenumskip-method"></a>ICorProfilerThreadEnum::Skip – metoda
Posune kurzor čítače výčtu z aktuální pozice pro přeskočení zadaného počtu prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet prvků, které mají být přeskočeny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`celt`prvky se přeskočily.|  
|S_FALSE|Méně než `celt` prvků bylo vynecháno, což znamená, že žádné další prvky nejsou k dispozici.|  
  
## <a name="remarks"></a>Poznámky  
 Nová pozice kurzoru tohoto enumerátoru je (aktuální pozice) + `celt` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerThreadEnum – rozhraní](icorprofilerthreadenum-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
