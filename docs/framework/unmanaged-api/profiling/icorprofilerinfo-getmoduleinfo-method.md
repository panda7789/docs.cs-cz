---
title: ICorProfilerInfo::GetModuleInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438890"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo – metoda
Po předaném ID modulu vrátí název souboru modulu a ID nadřazeného sestavení modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
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
  
## <a name="remarks"></a>Poznámky  
 Pro dynamické moduly je parametr `szName` prázdným řetězcem a základní adresa je 0 (nula).  
  
 I když může být metoda `GetModuleInfo` volána, jakmile existuje ID modulu, ID nadřazeného sestavení nebude k dispozici, dokud Profiler neobdrží zpětné volání [ICorProfilerCallback:: ModuleAttachedToAssembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .  
  
 Když `GetModuleInfo` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název souboru modulu. To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetModuleInfo` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetModuleInfo` s nulovou délkou `szName` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetModuleInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [GetModuleInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
