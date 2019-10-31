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
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114736"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z modulu CLR (Common Language Runtime).  Poskytuje funkce, které nejsou poskytovány metodou [ICorProfilerInfo:: GetEventMask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEventsLow`  
 mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí. Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .  
  
 `pdwEventsHigh`  
 mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.  Každý bit ovládá jinou schopnost, chování nebo typ události. Bity jsou popsány ve výčtu [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetEventMask2` slouží k určení, která zpětná volání profileru se přihlásí k odběru. Obvykle provedete logickou hodnotu nebo `pdwEventsLow` a `pdwEventsHigh` hodnoty a jakékoli nové bity, které chcete nastavit, a potom zavoláte metodu [SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
 Tato metoda je doporučená alternativou k metodě [GetEventMask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [SetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
