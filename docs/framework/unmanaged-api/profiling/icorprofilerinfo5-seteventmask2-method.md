---
title: ICorProfilerInfo5::SetEventMask2 – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 8027cdcde8281c363207e309bf65fcd90c03b626
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495616"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Nastaví hodnotu, která určuje typy událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime). Poskytuje více funkcí než metoda [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwEventsLow`  
 pro Hodnota 4 bajtu, která určuje kategorie událostí. Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu.  
  
 `dwEventsHigh`  
 pro Hodnota 4 bajtu, která určuje kategorie událostí.  Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány v [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
 `SetEventMask2`Metoda slouží k nastavení zpětných volání, ke kterým se Profiler přihlašuje. Obvykle zavoláte metodu [GetEventMask2 –](icorprofilerinfo5-geteventmask2-method.md) k určení, které bity jsou nastaveny, proveďte logické nebo její hodnoty a `pdwEventsLow` `pdwEventsHigh` všechny nové bity, které chcete nastavit, a poté zavolejte `SetEventMask2` metodu.  
  
 Tato metoda je doporučená alternativou k metodě [SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo5 – rozhraní](icorprofilerinfo5-interface.md)
- [Metoda GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)
