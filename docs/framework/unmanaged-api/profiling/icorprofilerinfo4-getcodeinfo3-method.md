---
title: "ICorProfilerInfo4::GetCodeInfo3 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetCodeInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b669714774ecfccad436f064350569d27ef13883
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 – metoda
Získá rozsah nativního kódu přidružené verze překompilovat JIT zadanou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionID`  
 [v] ID funkce, ke kterému je přiřazeno nativního kódu.  
  
 `reJitId`  
 [v] Identita překompilovat JIT funkce.  
  
 `cCodeInfos`  
 [v] Velikost `codeInfos` pole.  
  
 `pcCodeInfos`  
 [out] Ukazatel na celkový počet [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury, které jsou k dispozici.  
  
 `codeInfos`  
 [out] Zadaný volající vyrovnávací paměti. Po návratu metody obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 `GetCodeInfo3` Metoda je podobná [getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)kromě toho, že se budou získávat překompilovat JIT ID funkce, která obsahuje zadaná IP adresa.  
  
> [!NOTE]
>  `GetCodeInfo3`můžete aktivovat uvolňování paměti, zatímco [getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nikoli. Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Rozsah jsou seřazeny v pořadí podle zvýšení posun Common mezilehlá jazyk (CIL).  
  
 Po `GetCodeInfo3` vrátí, musíte ověřit, že `codeInfos` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury. K tomuto účelu porovnat hodnotu `cCodeInfos` s hodnotou `cchName` parametr. Pokud `cCodeInfos` dělený velikost [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktura je menší než `pcCodeInfos`, přidělit větší `codeInfos` vyrovnávací paměti, aktualizujte `cCodeInfos` s novou, větší velikost a volání `GetCodeInfo3` znovu.  
  
 Alternativně můžete nejdřív volat `GetCodeInfo3` s nulovou délkou `codeInfos` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Pak můžete nastavit `codeInfos` velikost k hodnotě vrácené ve vyrovnávací paměti `pcCodeInfos`, násobenou velikost [cor_prf_code_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) strukturu a volání `GetCodeInfo3` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetCodeInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
