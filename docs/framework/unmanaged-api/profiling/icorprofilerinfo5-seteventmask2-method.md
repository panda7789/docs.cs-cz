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
ms.openlocfilehash: 1e1779c0f4f36b2d7b81832bc90cf5aee0b8a7df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130394"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Nastaví hodnotu, která určuje typy událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime). Poskytuje více funkcí než metoda [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwEventsLow`  
 pro Hodnota 4 bajtu, která určuje kategorie událostí. Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .  
  
 `dwEventsHigh`  
 pro Hodnota 4 bajtu, která určuje kategorie událostí.  Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány ve výčtu [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetEventMask2` slouží k nastavení zpětných volání, ke kterým se Profiler přihlašuje. Obvykle zavoláte metodu [GetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a určíte, které bity jsou nastaveny, proveďte logický nebo jeho `pdwEventsLow` a `pdwEventsHigh` hodnoty a všechny nové bity, které chcete nastavit, a poté zavolejte metodu `SetEventMask2`.  
  
 Tato metoda je doporučená alternativou k metodě [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [GetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
