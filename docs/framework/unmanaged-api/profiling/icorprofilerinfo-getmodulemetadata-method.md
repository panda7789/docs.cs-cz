---
title: "ICorProfilerInfo::GetModuleMetaData – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleMetaData
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad52460bcd6eb320e970cd0ce2078f2e93df353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData – metoda
Získá instanci rozhraní metadata, která se mapuje na zadaný modul.  
  
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
 [v] ID modulu, na kterou bude instance rozhraní namapovaná.  
  
 `dwOpenFlags`  
 [v] Hodnota [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčet, který určuje režim pro otevírání souborů manifestu. Pouze `ofRead`, `ofWrite` a `ofNoTransform` bits jsou platné.  
  
 `riid`  
 [v] Odkaz na ID (GUID) metadat rozhraní, jejichž instance bude načten. V tématu [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) seznam rozhraní.  
  
 `ppOut`  
 [out] Ukazatel na adresu instanci rozhraní metadat.  
  
## <a name="remarks"></a>Poznámky  
 Může požádat o metadata otevřít v režimu pro čtení a zápis, ale tato akce způsobí pomalejší metadata spuštění programu, protože změn metadata nelze optimalizovat jako byly z kompilátoru.  
  
 Některé moduly (například moduly prostředků) mají žádná metadata. V takových případech `GetModuleMetaData` vrátí hodnotu HRESULT S_FALSE a s hodnotou null v *`ppOut`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
