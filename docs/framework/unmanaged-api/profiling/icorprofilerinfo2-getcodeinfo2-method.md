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
ms.openlocfilehash: 5149e3fab023de42d03673ec5d3e5ae888a9ed5a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433289"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 – metoda
Získá rozsahy nativního kódu přidruženého k zadané `FunctionID`.  
  
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
 pro Velikost pole `codeInfos`.  
  
 `pcCodeInfos`  
 mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 mimo Vyrovnávací paměť poskytnutá volajícím. Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Rozsahy jsou seřazené v pořadí od zvýšení posunu jazyka MSIL (Microsoft Intermediate Language).  
  
 Po `GetCodeInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `codeInfos` dostatečně velká, aby obsahovala všechny `COR_PRF_CODE_INFO` struktury. To provedete tak, že porovnáte hodnotu `cCodeInfos` s hodnotou parametru `cchName`. Pokud je `cCodeInfos` dělené velikostí `COR_PRF_CODE_INFO` struktury menší než `pcCodeInfos`, přidělte větší vyrovnávací paměť `codeInfos`, aktualizujte `cCodeInfos` o novou, větší velikost a zavolejte `GetCodeInfo2` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetCodeInfo2` s nulovou délkou `codeInfos` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti `codeInfos` na hodnotu vrácenou v `pcCodeInfos`vynásobenou velikostí `COR_PRF_CODE_INFO` struktury a znovu volat `GetCodeInfo2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCodeInfo3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
