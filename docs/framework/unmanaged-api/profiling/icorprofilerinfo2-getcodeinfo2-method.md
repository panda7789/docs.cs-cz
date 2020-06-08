---
title: ICorProfilerInfo2::GetCodeInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502890"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 – metoda
Získá rozsahy nativního kódu přidruženého k zadanému `FunctionID` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionID`  
 pro ID funkce, ke které je přidružen nativní kód.  
  
 `cCodeInfos`  
 pro Velikost `codeInfos` pole.  
  
 `pcCodeInfos`  
 mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 mimo Vyrovnávací paměť poskytnutá volajícím. Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Rozsahy jsou seřazené v pořadí od zvýšení posunu jazyka MSIL (Microsoft Intermediate Language).  
  
 Po `GetCodeInfo2` návratu je nutné ověřit, zda `codeInfos` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `COR_PRF_CODE_INFO` struktury. Chcete-li to provést, porovnejte hodnotu `cCodeInfos` s hodnotou `cchName` parametru. `cCodeInfos`Je-li děleno velikostí `COR_PRF_CODE_INFO` struktury menší než `pcCodeInfos` , přidělte větší `codeInfos` vyrovnávací paměť, aktualizujte `cCodeInfos` novou, větší velikost a zavolejte `GetCodeInfo2` znovu.  
  
 Případně můžete `GetCodeInfo2` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `codeInfos` vyrovnávací paměti. Pak můžete nastavit `codeInfos` Velikost vyrovnávací paměti na hodnotu vrácenou v `pcCodeInfos` , vynásobenou velikostí `COR_PRF_CODE_INFO` struktury a volat `GetCodeInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCodeInfo3 – metoda](icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
