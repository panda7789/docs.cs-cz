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
ms.openlocfilehash: c6fdb7040620bb7a5b6aea6e0dc41e08d6f346d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210355"
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
 pro Kapacita úložiště `map` pole. Další informace naleznete v části Poznámky.  
  
 pcMap  
 mimo Počet hodnot COR_IL_MAP zapsaných do pole map.  
  
 map  
 mimo Pole hodnot COR_IL_MAP, které poskytují informace o mapování z instrumentované úrovně IL na IL původní metody.  
  
## <a name="remarks"></a>Poznámky  
 Pokud profiler nastaví mapování voláním metody [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , ladicí program může zavolat tuto metodu, aby načetla mapování a použila mapování interně při výpočtu posunu Il pro trasování zásobníku a pro dobu života proměnných.  
  
 Pokud `cMap` je 0 a `pcMap` je**nenulová**, `pcMap` je nastaveno na počet dostupných COR_IL_MAPch hodnot. Pokud `cMap` je hodnota nenulová, představuje kapacitu úložiště `map` pole. Když metoda vrátí, `map` obsahuje maximálně `cMap` položek a `pcMap` je nastavena na počet COR_IL_MAP hodnot skutečně zapsaných do `map` pole.  
  
 Pokud se IL neinstrumentoval nebo mapování neposkytl Profiler, vrátí tato metoda `S_OK` a nastaví `pcMap` na 0.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [Rozhraní ICorDebugILCode2](icordebugilcode2-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
