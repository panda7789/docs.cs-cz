---
title: ICorProfilerInfo5::GetEventMask2 – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 758e5b71443b127c80c820eb8531056530e81b13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495694"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z modulu CLR (Common Language Runtime).  Poskytuje funkce, které nejsou poskytovány metodou [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEventsLow`  
 mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí. Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu.  
  
 `pdwEventsHigh`  
 mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.  Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány v [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
 `GetEventMask2`Metoda se používá k určení, která zpětná volání profileru se přihlásí k odběru. Obvykle provedete logické `pdwEventsLow` `pdwEventsHigh` hodnoty, hodnoty a a jakékoli nové bity, které chcete nastavit, a potom zavoláte metodu [SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .  
  
 Tato metoda je doporučená alternativou k metodě [GetEventMask –](icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo5 – rozhraní](icorprofilerinfo5-interface.md)
- [Metoda SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)
