---
title: ICorProfilerInfo4::GetILToNativeMapping2 – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad83c376816c2203cd78a83b8664fa90b0e109fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780831"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 – metoda
Získá mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů pro kód obsažený ve verzi překompilován JIT zadanou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, která obsahuje kód.  
  
 `pReJitId`  
 [in] Identita funkce překompilován JIT. Identita musí být nula v rozhraní .NET Framework 4.5.  
  
 `cMap`  
 [in] Maximální velikost `map` pole.  
  
 `pcMap`  
 [out] Celkový počet struktur cor_debug_il_to_native_map – k dispozici.  
  
 `map`  
 [out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí. Po `GetILToNativeMapping2` vrátí metoda `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping2` se podobá [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metody, s tím rozdílem, že bude možné profiler k určení ID překompilovanou funkce v budoucích verzí.  
  
> [!NOTE]
>  [Icorprofilerfunctioncontrol::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) metoda není implementovaná v rozhraní .NET Framework 4.5, funkce, které byly překompilován JIT nemůže mít IL na nativní mapování, která se liší od původně zkompilované funkce. V důsledku toho `GetILToNativeMapping2` nelze volat s nenulovou hodnotu ID překompilován JIT v rozhraní .NET Framework 4.5.  
  
 `GetILToNativeMapping2` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Chcete-li sdělit, že určité rozsahy nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` nastaveno na hodnotu [cordebugiltonativemappingtypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.  
  
 Po `GetILToNativeMapping2` vrátí, musíte ověřit, že `map` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametru. Pokud `pcMap` hodnotu, pokud se násobí velikost `COR_DEBUG_IL_TO_NATIVE_MAP` strukturu, je větší než `cMap`, přidělte větší `map` vyrovnávací paměti, aktualizujte `cMap` nové, větší velikosti a volání `GetILToNativeMapping2` znovu.  
  
 Alternativně můžete nejprve volat `GetILToNativeMapping2` s nulovou délkou `map` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
