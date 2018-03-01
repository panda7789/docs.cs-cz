---
title: "ICorProfilerInfo4::GetILToNativeMapping2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d5ce076ad66214f786f7e221a0443edf7986c5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 – metoda
Získá mapu od společnosti Microsoft (MSIL intermediate language) posune do nativní posunutí pro kód obsažené ve verzi překompilovat JIT zadanou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která obsahuje kód.  
  
 `pReJitId`  
 [v] Identita překompilovat JIT funkce. Identita musí být nula v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `cMap`  
 [v] Maximální velikost `map` pole.  
  
 `pcMap`  
 [out] Celkový počet dostupných cor_debug_il_to_native_map – struktury.  
  
 `map`  
 [out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí. Po `GetILToNativeMapping2` metoda vrátí `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping2`je podobná [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metoda, s tím rozdílem, že bude možné profileru zadat ID Rekompilované funkce v budoucnosti uvolní.  
  
> [!NOTE]
>  [Icorprofilerfunctioncontrol::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) metoda není implementována v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], takže funkce, které byly překompilovat JIT nemůže mít IL nativní mapování, která se liší od původně kompilované funkce. Jako takový `GetILToNativeMapping2` nejde volat s nenulovou překompilovat JIT ID v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `GetILToNativeMapping2` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Chcete-li sdělit, že určitých rozsahů nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` pole nastaveno na hodnotu [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.  
  
 Po `GetILToNativeMapping2` vrátí, musíte ověřit, že `map` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametr. Pokud `pcMap` hodnotu, pokud se násobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělit větší `map` vyrovnávací paměti, aktualizujte `cMap` s novou, větší velikost a volání `GetILToNativeMapping2` znovu.  
  
 Alternativně můžete nejdřív volat `GetILToNativeMapping2` s nulovou délkou `map` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcMap` a volání `GetILToNativeMapping2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
