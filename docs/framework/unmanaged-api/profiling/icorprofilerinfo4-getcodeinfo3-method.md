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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912706"
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
 mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
  
 `codeInfos`  
 mimo Vyrovnávací paměť poskytnutá volajícím. Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Metoda je podobná GetCodeInfo2 –, s tím rozdílem, že získá znovu zkompilované ID JIT funkce, která obsahuje zadanou IP adresu. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) `GetCodeInfo3`  
  
> [!NOTE]
> `GetCodeInfo3`může aktivovat uvolňování paměti, zatímco [GetCodeInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nebude. Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.  
  
 Po `GetCodeInfo3` návratu je nutné ověřit `codeInfos` , zda byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . Chcete-li to provést, porovnejte `cCodeInfos` hodnotu s hodnotou `cchName` parametru. Je `cCodeInfos` -li děleno velikostí struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměť, aktualizujte `cCodeInfos` novou, větší velikost a zavolejte `GetCodeInfo3` znovu.  
  
 Případně můžete pro získání správné velikosti `GetCodeInfo3` vyrovnávací paměti nejprve zavolat s `codeInfos` nulovou délkou vyrovnávací paměti. Pak můžete `codeInfos` nastavit velikost vyrovnávací paměti na hodnotu vrácenou `pcCodeInfos`v, vynásobenou velikostí [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury a volat `GetCodeInfo3` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCodeInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
