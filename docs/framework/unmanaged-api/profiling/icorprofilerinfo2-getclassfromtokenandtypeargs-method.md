---
title: "ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 332be5616ac11fc89df8c8d54aa5c0cbc49491ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda
Získá `ClassID` typu pomocí tokenu Zadaná metadata a `ClassID` argumentů hodnoty libovolného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [v] ID modulu, ve které je umístěn typu.  
  
 `typeDef`  
 [v] `mdTypeDef` Metadata token, který odkazuje na typ.  
  
 `cTypeArgs`  
 [v] Počet parametrů typu pro daný typ. Tato hodnota musí být nula pro neobecný typy.  
  
 `typeArgs`  
 [v] Pole `ClassID` hodnoty, z nichž každý je argumentem typu. Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastaven na hodnotu nula.  
  
 `pClassID`  
 [out] Ukazatel `ClassID` zadaného typu.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetClassFromTokenAndTypeArgs` metoda s `mdTypeRef` místo `mdTypeDef` metadata token může mít nepředvídatelné výsledky; volající musí se překládat `mdTypeRef` k `mdTypeDef` při předání.  
  
 Pokud dosud není načtený typ, voláním `GetClassFromTokenAndTypeArgs` aktivují načítání, což je nebezpečné operace v mnoha kontextech. Například voláním této metody během načítání moduly nebo jiné typy může vést k nekonečné smyčce jako modul runtime, pokusí se načíst pravidelného věcí.  
  
 Obecně platí, použití `GetClassFromTokenAndTypeArgs` se nedoporučuje. Pokud události pro určitý typ zajímá profilery, měli uložit `ModuleID` a `mdTypeDef` tohoto typu a použití [ICorProfilerInfo2::getclassidinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) zkontrolujte zda daný `ClassID` , je požadovaný typ.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilerinfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
