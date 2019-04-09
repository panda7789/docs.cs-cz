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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69db53c03d68e30507ff3ab2b11b663970d59af0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090807"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo – metoda
Dané ID modulu vrátí název souboru modulu a ID modulu nadřazené sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
## <a name="remarks"></a>Poznámky  
 Pro dynamické moduly `szName` parametru je prázdný řetězec a je základní adresa 0 (nula).  
  
 I když `GetModuleInfo` metoda může být volána jako ID modulu existuje, ID nadřazeného sestavení nebude k dispozici, dokud profiler obdrží [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.  
  
 Když `GetModuleInfo` vrátí, musíte ověřit, že `szName` vyrovnávací paměť je dostatečně velký, aby obsahovat úplný název souboru modulu. K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetModuleInfo` znovu.  
  
 Alternativně můžete nejprve volat `GetModuleInfo` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcchName` a volat `GetModuleInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [GetModuleInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
