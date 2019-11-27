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
ms.openlocfilehash: dfce86e95ba41a65e72524546072244a47f8360c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442921"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 – metoda
Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v překompilované verzi zadané funkce JIT.  
  
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
 pro ID funkce, která obsahuje kód.  
  
 `pReJitId`  
 pro Identita funkce Rekompilované JIT. V .NET Framework 4,5 musí být identita nula.  
  
 `cMap`  
 pro Maximální velikost `map` pole  
  
 `pcMap`  
 mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.  
  
 `map`  
 mimo Pole struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z nichž každý Určuje posun. Po návratu metody `GetILToNativeMapping2` bude `map` obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping2` je podobná metodě [ICorProfilerInfo:: GetILToNativeMapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) s tím rozdílem, že umožňuje profileru v budoucích verzích určit ID Rekompilované funkce.  
  
> [!NOTE]
> Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) není implementována v .NET Framework 4,5, takže funkce, které byly rekompilovány JIT, nemohou mít mapování Il-to-Native, které se liší od původně kompilované funkce. V takovém případě nelze `GetILToNativeMapping2` volat pomocí nenulového rekompilovaného ID JIT v .NET Framework 4,5.  
  
 Metoda `GetILToNativeMapping2` vrací pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), může být položka pole `ilOffset` nastavena na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po `GetILToNativeMapping2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `map` dostatečně velká, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. To provedete tak, že porovnáte hodnotu `cMap` s hodnotou parametru `pcMap`. Pokud je hodnota `pcMap`, když se vynásobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělte větší `map` vyrovnávací paměť, aktualizujte `cMap` o novou, větší velikost a zavolejte `GetILToNativeMapping2` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetILToNativeMapping2` s nulovou délkou `map` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
