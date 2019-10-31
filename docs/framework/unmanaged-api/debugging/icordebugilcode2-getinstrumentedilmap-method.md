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
ms.openlocfilehash: 7dede4e5af702f1b86b430450db4a669c326c062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131065"
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
 mimo Počet hodnot COR_IL_MAP zapsaných do pole mapy.  
  
 map  
 mimo Pole hodnot COR_IL_MAP, které poskytují informace o mapování z instrumentované úrovně IL na IL původní metody.  
  
## <a name="remarks"></a>Poznámky  
 Pokud profiler nastaví mapování voláním metody [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , ladicí program může zavolat tuto metodu, aby načetla mapování a použila mapování interně při výpočtu posunu Il pro trasování a proměnnou zásobníku. životnosti.  
  
 Pokud je `cMap` 0 a `pcMap` není**null**, `pcMap` je nastaveno na počet dostupných hodnot COR_IL_MAP. Pokud `cMap` není nula, představuje kapacitu úložiště `map` pole. Když se metoda vrátí, `map` obsahuje maximum `cMap`ch položek a `pcMap` je nastavená na počet hodnot COR_IL_MAP skutečně zapsaných do pole `map`.  
  
 Pokud nedošlo k instrumentaci IL nebo mapování nebylo poskytnuto profilerem, vrátí tato metoda `S_OK` a nastaví `pcMap` na hodnotu 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
