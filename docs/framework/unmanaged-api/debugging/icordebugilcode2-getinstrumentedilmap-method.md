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
ms.openlocfilehash: 1f2e481942586e1e5ea6364370ff1385db134dd3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475681"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Vrátí mapu z posunů instrumentována profiler (IL intermediate language) na původní metodu IL posunutí pro tuto instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 Cmap –  
 [in] Kapacita úložiště `map` pole. Další informace naleznete v části Poznámky.  
  
 pcMap  
 [out] Počet hodnot cor_il_map – zapsána do pole mapování.  
  
 map  
 [out] Pole cor_il_map – hodnoty, které poskytují informace o mapování z profileru instrumentována IL IL původní metodu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud profiler nastaví mapování voláním [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metoda, ladicí program může volat tuto metodu načíst mapování a mapování používají interně při výpočtu IL dorovnání u zásobníku trasování a životnost proměnné.  
  
 Pokud `cMap` je 0 a `pcMap` jinou hodnotu než**null**, `pcMap` je nastavena na počet dostupných hodnot cor_il_map –. Pokud `cMap` je nenulová, představuje kapacitu úložiště `map` pole. Po návratu metody `map` obsahuje určitý počet `cMap` položky, a `pcMap` je nastavena na počet aktuálně zapsaných do hodnoty cor_il_map – `map` pole.  
  
 Pokud nebyl byla instrumentována IL nebo pomocí profileru nebylo zadáno mapování, vrátí tato metoda `S_OK` a nastaví `pcMap` na hodnotu 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
