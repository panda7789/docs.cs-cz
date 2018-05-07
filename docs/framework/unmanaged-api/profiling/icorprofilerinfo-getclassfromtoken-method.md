---
title: ICorProfilerInfo::GetClassFromToken – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4b6b7b7b0dbb36724ff5eee2f3f78a3a7422cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>ICorProfilerInfo::GetClassFromToken – metoda
Získá ID třídy, zadaný token metadat. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [ICorProfilerInfo2::getclassfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [v] ID modul, který obsahuje třídu.  
  
 `typeDef`  
 [v] `mdTypeDef` Metadata token, který odkazuje na třídu.  
  
 `cTypeArgs`  
 [out] Ukazatel na ID třídy.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je zastaralá; Místo toho použijte `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pro všechny typy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
