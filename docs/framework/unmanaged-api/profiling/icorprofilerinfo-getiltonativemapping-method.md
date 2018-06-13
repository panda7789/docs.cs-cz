---
title: ICorProfilerInfo::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61b097fad670c49680d6a2cc0f99ca0d53ef4691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456915"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping – metoda
Získá mapu od společnosti Microsoft (MSIL intermediate language) posune do nativní posunutí pro kód obsažené v zadanou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která obsahuje kód.  
  
 `cMap`  
 [v] Maximální velikost `map` pole.  
  
 `pcMap`  
 [out] Celkový počet dostupných cor_debug_il_to_native_map – struktury.  
  
 `map`  
 [out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí. Po `GetILToNativeMapping` metoda vrátí `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Chcete-li sdělit, že určitých rozsahů nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` pole nastaveno na hodnotu [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.  
  
 Po `GetILToNativeMapping` vrátí, musíte ověřit, že `map` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametr. Pokud `pcMap` hodnotu, pokud se násobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělit větší `map` vyrovnávací paměti, aktualizujte `cMap` s novou, větší velikost a volání `GetILToNativeMapping` znovu.  
  
 Alternativně můžete nejdřív volat `GetILToNativeMapping` s nulovou délkou `map` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcMap` a volání `GetILToNativeMapping` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [GetILToNativeMapping2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
