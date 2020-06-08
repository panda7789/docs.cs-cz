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
ms.openlocfilehash: 9a6ee58cda5e0b673b3ff1378240f89323e30194
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496033"
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
 pro Maximální velikost `map` pole.  
  
 `pcMap`  
 mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.  
  
 `map`  
 mimo Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z nichž každý Určuje posun. Poté `GetILToNativeMapping2` , co metoda vrátí, `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping2`je podobný metodě [ICorProfilerInfo:: GetILToNativeMapping –](icorprofilerinfo-getiltonativemapping-method.md) , s tím rozdílem, že umožňuje profileru v budoucích verzích určit ID Rekompilované funkce.  
  
> [!NOTE]
> Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap –](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) není implementována v .NET Framework 4,5, takže funkce, které byly rekompilovány JIT, nemohou mít mapování Il-to-Native, které se liší od původně kompilované funkce. V takovém případě `GetILToNativeMapping2` jej nelze volat s nenulovým rekompilovaným ID JIT v .NET Framework 4,5.  
  
 `GetILToNativeMapping2`Metoda vrací pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur. Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), položka v poli může mít své `ilOffset` pole nastaveno na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po `GetILToNativeMapping2` návratu je nutné ověřit, zda `map` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Chcete-li to provést, porovnejte hodnotu `cMap` s hodnotou `pcMap` parametru. Pokud je `pcMap` hodnota, když je vynásobena velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, větší než `cMap` , přidělte větší `map` vyrovnávací paměť, aktualizujte `cMap` novou, větší velikost a zavolejte `GetILToNativeMapping2` znovu.  
  
 Případně můžete `GetILToNativeMapping2` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `map` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetILToNativeMapping – metoda](icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
