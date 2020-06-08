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
ms.openlocfilehash: b3c0bee44bf49c7966b8fefcfe6460c6255375c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502987"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping – metoda
Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v zadané funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID funkce, která obsahuje kód.  
  
 `cMap`  
 pro Maximální velikost `map` pole.  
  
 `pcMap`  
 mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.  
  
 `map`  
 mimo Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z nichž každý Určuje posun. Poté `GetILToNativeMapping` , co metoda vrátí, `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping`Metoda vrací pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur. Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), položka v poli může mít své `ilOffset` pole nastaveno na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po `GetILToNativeMapping` návratu je nutné ověřit, zda `map` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Chcete-li to provést, porovnejte hodnotu `cMap` s hodnotou `pcMap` parametru. Pokud je `pcMap` hodnota, když je vynásobena velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, větší než `cMap` , přidělte větší `map` vyrovnávací paměť, aktualizujte `cMap` novou, větší velikost a zavolejte `GetILToNativeMapping` znovu.  
  
 Případně můžete `GetILToNativeMapping` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `map` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [GetILToNativeMapping2 – metoda](icorprofilerinfo4-getiltonativemapping2-method.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
