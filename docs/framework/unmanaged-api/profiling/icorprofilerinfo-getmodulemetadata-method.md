---
title: ICorProfilerInfo::GetModuleMetaData – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: c7bf8e3ebedb17a4536b604909434c3e004fc828
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439824"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData – metoda
Získá instanci rozhraní metadat, která se mapuje na určený modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro ID modulu, ke kterému bude namapována instance rozhraní.  
  
 `dwOpenFlags`  
 pro Hodnota výčtu [CorOpenFlags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) , která určuje režim otevírání souborů manifestu. Platné jsou pouze bity `ofRead`, `ofWrite` a `ofNoTransform`.  
  
 `riid`  
 pro Referenční identifikátor (GUID) rozhraní metadat, jehož instance bude načtena. Seznam rozhraní naleznete v tématu [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) .  
  
 `ppOut`  
 mimo Ukazatel na adresu instance rozhraní metadat.  
  
## <a name="remarks"></a>Poznámky  
 Můžete požádat, aby se metadata otevírala v režimu pro čtení i zápis, ale výsledkem bude pomalejší spuštění tohoto programu, protože změny v metadatech nejdou optimalizovat, protože byly z kompilátoru.  
  
 Některé moduly (například moduly prostředků) nemají žádná metadata. V těchto případech `GetModuleMetaData` vrátí hodnotu HRESULT S_FALSE a hodnotu null v hodnotě *`ppOut`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
