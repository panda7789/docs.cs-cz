---
title: ICorProfilerInfo4::GetCodeInfo3 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
ms.openlocfilehash: 54e522aaaf23ae81b96b6be7168a9a13f28a16d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496133"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 – metoda
Získá rozsahy nativního kódu přidruženého k Rekompilované verzi JIT zadané funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionID`  
 pro ID funkce, ke které je přidružen nativní kód.  
  
 `reJitId`  
 pro Identita funkce Rekompilované JIT.  
  
 `cCodeInfos`  
 pro Velikost `codeInfos` pole.  
  
 `pcCodeInfos`  
 mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 mimo Vyrovnávací paměť poskytnutá volajícím. Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 `GetCodeInfo3`Metoda je podobná [GetCodeInfo2 –](icorprofilerinfo2-getcodeinfo2-method.md), s tím rozdílem, že získá znovu zkompilované ID JIT funkce, která obsahuje zadanou IP adresu.  
  
> [!NOTE]
> `GetCodeInfo3`může aktivovat uvolňování paměti, zatímco [GetCodeInfo2 –](icorprofilerinfo2-getcodeinfo2-method.md) nebude. Další informace najdete v [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.  
  
 Po `GetCodeInfo3` návratu je nutné ověřit, zda `codeInfos` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . Chcete-li to provést, porovnejte hodnotu `cCodeInfos` s hodnotou `cchName` parametru. Pokud `cCodeInfos` je dělena velikostí [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury menší než `pcCodeInfos` , přidělte větší `codeInfos` vyrovnávací paměť, aktualizujte `cCodeInfos` novou, větší velikost a zavolejte `GetCodeInfo3` znovu.  
  
 Případně můžete `GetCodeInfo3` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `codeInfos` vyrovnávací paměti. Pak můžete nastavit `codeInfos` Velikost vyrovnávací paměti na hodnotu vrácenou v `pcCodeInfos` , vynásobenou velikostí [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury a volat `GetCodeInfo3` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCodeInfo2 – metoda](icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
