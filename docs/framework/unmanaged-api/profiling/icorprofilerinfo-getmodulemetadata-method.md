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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1663a36ab36980af709a861b3fb0666be6fecdfb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607472"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData – metoda
Získá instanci rozhraní metadat, který se mapuje na zadaný modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] ID modulu, ke které se namapují instanci rozhraní.  
  
 `dwOpenFlags`  
 [in] Hodnota [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčet, který určuje režim pro otevření souborů manifestu. Pouze `ofRead`, `ofWrite` a `ofNoTransform` bity jsou platné.  
  
 `riid`  
 [in] Odkaz na Identifikátor (GUID) metadat rozhraní, jejichž instance se byla načtena. Zobrazit [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) seznam rozhraní.  
  
 `ppOut`  
 [out] Ukazatel na adresu rozhraní instance metadat.  
  
## <a name="remarks"></a>Poznámky  
 Požádat o metadat, která chcete otevřít v režimu čtení a zápisu, ale to způsobí pomalejší metadat provádění programu, protože změny provedené metadata nelze optimalizovaná, jako kdyby byly z kompilátoru.  
  
 Některé moduly (například moduly prostředků) mají žádná metadata. V takových případech `GetModuleMetaData` vrátí hodnotu HRESULT S_FALSE a s hodnotou null v *`ppOut`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
