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
ms.openlocfilehash: d461f5dc85c7107e36fc1492ac88f37d42ba9f24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 – metoda
Zadaný modul ID vrátí název souboru modulu, ID modulu nadřazené sestavení a bitová maska, která popisuje vlastnosti modulu.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [v] ID modulu, pro které budou načteny informace.  
  
 `ppBaseLoadAddress`  
 [out] Základní adresa, kdy je načíst modul.  
  
 `cchName`  
 [v] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.  
  
 `pcchName`  
 [out] Ukazatel na celkový počet znaků názvu souboru modulu, která je vrácena.  
  
 `szName`  
 [out] Zadaný volající široká znaková vyrovnávací paměti. Po návratu metody obsahuje tento vyrovnávací paměť názvu souboru modulu.  
  
 `pAssemblyId`  
 [out] Ukazatel na ID nadřazeného sestavení modulu.  
  
 `pdwModuleFlags`  
 [out] Bitová maska hodnoty z [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) výčet, který zadejte vlastnosti modulu.  
  
## <a name="remarks"></a>Poznámky  
 Pro dynamické moduly `szName` parametr metadata název modulu a základní adresa je 0 (nula). Název metadat je hodnota ve sloupci název z tabulky modulu uvnitř metadat. To je také k dispozici jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> vlastnost do spravovaného kódu a jako `szName` parametr [imetadataimport::getscopeprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metodu pro metadata nespravovaného kódu klienta.  
  
 I když `GetModuleInfo2` metoda může být volána při ID modulu existuje, ID nadřazeného sestavení nebudete mít k dispozici, dokud neobdrží profileru [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.  
  
 Když `GetModuleInfo2` vrátí, musíte ověřit, že `szName` vyrovnávací paměť byla dostatečně velký pro obsahovat úplný název souboru modulu. K tomuto účelu porovnat hodnotu, `pcchName` body s hodnotou `cchName` parametr. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělit větší `szName` vyrovnávací paměti, aktualizujte `cchName` s novou, větší velikost a volání `GetModuleInfo2` znovu.  
  
 Alternativně můžete nejdřív volat `GetModuleInfo2` s nulovou délkou `szName` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcchName` a volání `GetModuleInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
