---
title: ICorDebugILCode2::GetInstrumentedILMap – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 728a6c83dc321fa28dc4ff84c4e874d886524b36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788561"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Vrátí mapu z posunu s instrumentací prostředního jazyka (IL) na původní posunutí metody IL pro tuto instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 cMap  
 pro Kapacita úložiště pole `map`. Další informace naleznete v části Poznámky.  
  
 pcMap  
 mimo Počet hodnot COR_IL_MAP zapsaných do pole map.  
  
 map  
 mimo Pole hodnot COR_IL_MAP, které poskytují informace o mapování z instrumentované úrovně IL na IL původní metody.  
  
## <a name="remarks"></a>Poznámky  
 Pokud profiler nastaví mapování voláním metody [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , ladicí program může zavolat tuto metodu, aby načetla mapování a použila mapování interně při výpočtu posunu Il pro trasování zásobníku a pro dobu života proměnných.  
  
 Pokud je `cMap` 0 a `pcMap` není**null**, `pcMap` je nastaveno na počet dostupných COR_IL_MAP hodnot. Pokud `cMap` není nula, představuje kapacitu úložiště `map` pole. Když se metoda vrátí, `map` obsahuje maximálně `cMap` položek a `pcMap` je nastavená na počet COR_IL_MAP hodnot skutečně zapsaných do pole `map`.  
  
 Pokud nedošlo k instrumentaci IL nebo mapování nebylo poskytnuto profilerem, vrátí tato metoda `S_OK` a nastaví `pcMap` na hodnotu 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 – rozhraní](icordebugilcode2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
