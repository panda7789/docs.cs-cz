---
title: ICorProfilerInfo3::GetModuleInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 188517104d4163ad1b391c2bab3bc41a2697e63d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478073"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 – metoda
Dané ID modulu vrátí název souboru modulu, ID modulu nadřazené sestavení a bitová maska, která popisuje vlastnosti modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] ID modulu, pro kterou budou načteny informace.  
  
 `ppBaseLoadAddress`  
 [out] Základní adresa, načtení modulu.  
  
 `cchName`  
 [in] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.  
  
 `pcchName`  
 [out] Celkový počet znaků z modulů název souboru, který je vrácen ukazatel.  
  
 `szName`  
 [out] Pokud volající širokého znaku vyrovnávací paměti. Po návratu metody obsahuje tuto vyrovnávací paměť názvu souboru modulu.  
  
 `pAssemblyId`  
 [out] Ukazatel na ID nadřazeného sestavení modulu.  
  
 `pdwModuleFlags`  
 [out] Bitová maska hodnot z [cor_prf_module_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) výčet, který určit vlastnosti modulu.  
  
## <a name="remarks"></a>Poznámky  
 Pro dynamické moduly `szName` parametr je název metadata modulu a základní adresa je 0 (nula). Název metadat je hodnota ve sloupci název z tabulky modulu uvnitř metadat. To je také vystavena jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> vlastnost do spravovaného kódu a jako `szName` parametr [imetadataimport::getscopeprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metodu pro nespravované metadat klientský kód.  
  
 I když `GetModuleInfo2` metoda může být volána jako ID modulu existuje, ID nadřazeného sestavení nebude k dispozici, dokud profiler obdrží [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.  
  
 Když `GetModuleInfo2` vrátí, musíte ověřit, že `szName` vyrovnávací paměť je dostatečně velký, aby obsahovat úplný název souboru modulu. K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetModuleInfo2` znovu.  
  
 Alternativně můžete nejprve volat `GetModuleInfo2` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcchName` a volat `GetModuleInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
