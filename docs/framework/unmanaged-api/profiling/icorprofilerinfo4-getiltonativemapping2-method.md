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
ms.openlocfilehash: a8ffdb04bdf3fd2f605e2dffc5065a0d786bbaf7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967907"
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
 mimo Celkový počet dostupných struktur COR_DEBUG_IL_TO_NATIVE_MAP.  
  
 `map`  
 mimo Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z nichž každý Určuje posun. Poté, co `map` `COR_DEBUG_IL_TO_NATIVE_MAP` metoda vrátí, bude obsahovat některé nebo všechny struktury. `GetILToNativeMapping2`  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping2`je podobný metodě [ICorProfilerInfo:: GetILToNativeMapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) , s tím rozdílem, že umožňuje profileru v budoucích verzích určit ID Rekompilované funkce.  
  
> [!NOTE]
> Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) není implementována v .NET Framework 4,5, takže funkce, které byly rekompilovány JIT, nemohou mít mapování Il-to-Native, které se liší od původně kompilované funkce. V takovém `GetILToNativeMapping2` případě jej nelze volat s nenulovým rekompilovaným ID JIT v .NET Framework 4,5.  
  
 `GetILToNativeMapping2` Metoda vrací`COR_DEBUG_IL_TO_NATIVE_MAP` pole struktur. Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), položka v poli může mít své `ilOffset` pole nastaveno na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po `GetILToNativeMapping2` návratu je nutné ověřit `map` , zda byla vyrovnávací paměť `COR_DEBUG_IL_TO_NATIVE_MAP` dostatečně velká, aby obsahovala všechny struktury. Chcete-li to provést, porovnejte `cMap` hodnotu s hodnotou `pcMap` parametru. `cMap` `COR_DEBUG_IL_TO_NATIVE_MAP` `GetILToNativeMapping2` `map` `cMap`Pokud je hodnota,kdyžjevynásobenavelikostístruktury,většínež,přiděltevětšívyrovnávacípaměť,aktualizujtenovou,většívelikostazavolejteznovu.`pcMap`  
  
 Případně můžete pro získání správné velikosti `GetILToNativeMapping2` vyrovnávací paměti nejprve zavolat s `map` nulovou délkou vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
