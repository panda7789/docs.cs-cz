---
title: "ICorProfilerInfo::GetModuleInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8309b57f2940805e23010feac17b6d37f1a58af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo – metoda
Zadaný modul ID vrátí název souboru modulu a ID modulu nadřazené sestavení.  
  
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
  
## <a name="remarks"></a>Poznámky  
 Pro dynamické moduly `szName` parametr je řetězec prázdný, a základní adresa je 0 (nula).  
  
 I když `GetModuleInfo` metoda může být volána při ID modulu existuje, ID nadřazeného sestavení nebudete mít k dispozici, dokud neobdrží profileru [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.  
  
 Když `GetModuleInfo` vrátí, musíte ověřit, že `szName` vyrovnávací paměť byla dostatečně velký pro obsahovat úplný název souboru modulu. K tomuto účelu porovnat hodnotu, `pcchName` body s hodnotou `cchName` parametr. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělit větší `szName` vyrovnávací paměti, aktualizujte `cchName` s novou, větší velikost a volání `GetModuleInfo` znovu.  
  
 Alternativně můžete nejdřív volat `GetModuleInfo` s nulovou délkou `szName` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcchName` a volání `GetModuleInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [GetModuleInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
