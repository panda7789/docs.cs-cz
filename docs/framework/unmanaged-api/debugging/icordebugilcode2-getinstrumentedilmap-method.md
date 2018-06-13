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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a712ed9e3534ca6bb2962989f1ab3750a25d539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417899"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Vrátí mapu od posuny instrumentovány profileru převodní jazyk (IL) do původního metoda IL posunutí pro tuto instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 cMap  
 [v] Úložnou kapacitu `map` pole. Další informace naleznete v části Poznámky.  
  
 pcMap  
 [out] Počet hodnot cor_il_map – zapsána do pole mapy.  
  
 map  
 [out] Pole cor_il_map – hodnoty, které poskytují informace o mapování z instrumentovány profileru IL IL původní metody.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je profileru nastaví mapování voláním [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody ladicího programu můžete volat tuto metodu pro načtení mapování a mapování interně při výpočtu IL posune pro zásobníku trasování a proměnné životnosti.  
  
 Pokud `cMap` je 0 a `pcMap` jinou hodnotu než**null**, `pcMap` je nastaven na počet dostupných hodnot cor_il_map –. Pokud `cMap` je nulová, představuje kapacitu úložiště `map` pole. Po návratu metody `map` obsahuje maximálně `cMap` položky, a `pcMap` je nastaven na počet hodnot cor_il_map – ve skutečnosti zapsána do `map` pole.  
  
 Pokud IL nebyla byly instrumentovány nebo mapování nebyl poskytované profileru, tato metoda vrátí hodnotu `S_OK` a nastaví `pcMap` na hodnotu 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [ICorDebugILCode2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
