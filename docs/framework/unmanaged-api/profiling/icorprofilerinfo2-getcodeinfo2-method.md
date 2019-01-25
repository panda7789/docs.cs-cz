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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22463a56911354c9706bbfbc7d1824aee5d3c74d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725022"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 – metoda
Získá rozsah nativního kódu přidružený k zadanému `FunctionID`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionID`  
 [in] ID funkce, ke kterému je přidružen nativní kód.  
  
 `cCodeInfos`  
 [in] Velikost `codeInfos` pole.  
  
 `pcCodeInfos`  
 [out] Ukazatel na celkový počet [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury k dispozici.  
  
 `codeInfos`  
 [out] Pokud volající vyrovnávací paměti. Po návratu metody obsahuje celou řadu `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Rozsahy jsou seřazeny v pořadí podle zvyšující posun Microsoft intermediate language (MSIL).  
  
 Po `GetCodeInfo2` vrátí, musíte ověřit, že `codeInfos` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `COR_PRF_CODE_INFO` struktury. K tomuto účelu porovnat hodnotu `cCodeInfos` s hodnotou `cchName` parametru. Pokud `cCodeInfos` rozdělené podle velikosti `COR_PRF_CODE_INFO` struktura je menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměti, aktualizujte `cCodeInfos` nové, větší velikosti a volání `GetCodeInfo2` znovu.  
  
 Alternativně můžete nejprve volat `GetCodeInfo2` s nulovou délkou `codeInfos` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit `codeInfos` velikost k hodnotě vrácené ve vyrovnávací paměti `pcCodeInfos`, vynásobený velikostí `COR_PRF_CODE_INFO` strukturu a volání `GetCodeInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [GetCodeInfo3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
