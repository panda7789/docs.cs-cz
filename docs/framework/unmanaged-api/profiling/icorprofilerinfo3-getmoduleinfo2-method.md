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
ms.openlocfilehash: e2a4df262e076c960640977bea0d22be19802140
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449665"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 – metoda
Po předaném ID modulu vrátí název souboru modulu, ID nadřazeného sestavení modulu a bitovou masku, která popisuje vlastnosti modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro ID modulu, pro který budou načteny informace.  
  
 `ppBaseLoadAddress`  
 mimo Základní adresa, na které je modul načten.  
  
 `cchName`  
 pro Délka `szName` návratové vyrovnávací paměti ve znacích.  
  
 `pcchName`  
 mimo Ukazatel na celkovou délku znaku v názvu souboru modulu, který je vrácen.  
  
 `szName`  
 mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu. Když se metoda vrátí, tato vyrovnávací paměť obsahuje název souboru modulu.  
  
 `pAssemblyId`  
 mimo Ukazatel na ID nadřazeného sestavení modulu.  
  
 `pdwModuleFlags`  
 mimo Bitová maska hodnot z výčtu [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) , které určují vlastnosti modulu.  
  
## <a name="remarks"></a>Poznámky  
 Pro dynamické moduly je parametr `szName` názvem metadat modulu a základní adresa je 0 (nula). Název metadat je hodnota ve sloupci název z tabulky modulů v metadatech. To je také zveřejněné jako vlastnost <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> pro spravovaný kód a jako parametr `szName` metody [IMetaDataImport:: GetScopeProps –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) na nespravovaný kód klienta metadat.  
  
 I když může být metoda `GetModuleInfo2` volána, jakmile existuje ID modulu, ID nadřazeného sestavení nebude k dispozici, dokud Profiler neobdrží zpětné volání [ICorProfilerCallback:: ModuleAttachedToAssembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .  
  
 Když `GetModuleInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název souboru modulu. To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetModuleInfo2` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetModuleInfo2` s nulovou délkou `szName` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetModuleInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
