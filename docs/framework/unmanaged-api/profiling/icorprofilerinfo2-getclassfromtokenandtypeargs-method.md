---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d4d5ec9119cdcf89e507f133288f569e6fb37ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072516"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda
Získá `ClassID` typu pomocí tokenu Zadaná metadata a `ClassID` hodnot ve všech argumentů typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] ID modulu, ve kterém se typ nachází.  
  
 `typeDef`  
 [in] `mdTypeDef` Token metadat, který odkazuje na typ.  
  
 `cTypeArgs`  
 [in] Počet parametrů typu pro daný typ. Tato hodnota musí být nula pro obecné typy.  
  
 `typeArgs`  
 [in] Pole `ClassID` hodnot, z nichž každý je argument typu. Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastavena na hodnotu nula.  
  
 `pClassID`  
 [out] Ukazatel `ClassID` zadaného typu.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetClassFromTokenAndTypeArgs` metodu s `mdTypeRef` místo `mdTypeDef` tokenu metadat může mít nepředvídatelné výsledky; musí se překládat volající `mdTypeRef` do `mdTypeDef` při předávání ho.  
  
 Pokud dosud není načtený typ, voláním `GetClassFromTokenAndTypeArgs` aktivují načítání, což je nebezpečné operace v mnoha kontextech. Například volání této metody při načítání modulů nebo jiných typů může vést k nekonečné smyčce jak modul runtime pokusí se načíst cyklicky věci.  
  
 Obecně platí, využívání `GetClassFromTokenAndTypeArgs` se nedoporučuje. Pokud profilery zajímají události pro určitý typ, měli uložit `ModuleID` a `mdTypeDef` tohoto typu a použití [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) ke kontrole, jestli daný `ClassID` je požadovaného typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
