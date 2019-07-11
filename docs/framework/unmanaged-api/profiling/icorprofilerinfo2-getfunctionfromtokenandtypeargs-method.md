---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31fad9e82d0b93360f92676f6357c136ae60634a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771126"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda
Získá `FunctionID` funkce s použitím Zadaná metadata token, který obsahuje třídy, a `ClassID` hodnot ve všech argumentů typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] ID modulu, ve kterém se funkce nachází.  
  
 `funcDef`  
 [in] `mdMethodDef` Token metadat, který odkazuje na funkci.  
  
 `classId`  
 [in] ID funkce obsahující třídy.  
  
 `cTypeArgs`  
 [in] Počet parametrů typu pro danou funkci. Tato hodnota musí být nula pro funkce, který není obecný.  
  
 `typeArgs`  
 [in] Pole `ClassID` hodnot, z nichž každý je argument funkce. Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastavena na hodnotu nula.  
  
 `pFunctionID`  
 [out] Ukazatel `FunctionID` zadané funkce.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetFunctionFromTokenAndTypeArgs` metodou `mdMethodRef` metadat místo `mdMethodDef` tokenu metadat může mít nepředvídatelné výsledky. Volající musí se překládat `mdMethodRef` do `mdMethodDef` při předávání ho.  
  
 Pokud funkce dosud není načtený, volání `GetFunctionFromTokenAndTypeArgs` způsobí, že načítání pravděpodobnější, což je nebezpečné operace v mnoha kontextech. Například volání této metody při načítání modulů nebo typy může vést k nekonečné smyčce jak modul runtime pokusí se načíst cyklicky věci.  
  
 Obecně platí, využívání `GetFunctionFromTokenAndTypeArgs` se nedoporučuje. Pokud profilery zajímají události pro určitou funkci, měli uložit `ModuleID` a `mdMethodDef` této funkce a použití [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) ke kontrole, jestli daný `FunctionID` je který požadované funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
