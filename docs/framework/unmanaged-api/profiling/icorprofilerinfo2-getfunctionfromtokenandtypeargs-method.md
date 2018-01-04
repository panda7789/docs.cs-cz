---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b225b87eab6e65055618c8b6659459637e8a01be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda
Získá `FunctionID` funkce pomocí Zadaná metadata token, který obsahuje třídy, a `ClassID` argumentů hodnoty libovolného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [v] ID modulu, ve kterém se funkce nachází.  
  
 `funcDef`  
 [v] `mdMethodDef` Metadata token, který odkazuje na funkci.  
  
 `classId`  
 [v] ID třídy obsahující funkce.  
  
 `cTypeArgs`  
 [v] Počet typů parametrů pro danou funkci. Tato hodnota musí být nula pro neobecný funkce.  
  
 `typeArgs`  
 [v] Pole `ClassID` hodnoty, z nichž každý je argument funkce. Hodnota `typeArgs` může mít hodnotu NULL, pokud `cTypeArgs` je nastaven na hodnotu nula.  
  
 `pFunctionID`  
 [out] Ukazatel `FunctionID` zadané funkce.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetFunctionFromTokenAndTypeArgs` metoda s `mdMethodRef` metadata místo `mdMethodDef` metadata token může mít vést k neočekávaným výsledkům. Volající musí se překládat `mdMethodRef` k `mdMethodDef` při předání.  
  
 Pokud funkce dosud není načtený, volání `GetFunctionFromTokenAndTypeArgs` způsobí, že dojde k, načítání, což je nebezpečné operace v mnoha kontextech. Například voláním této metody během načítání moduly nebo typů může vést k nekonečné smyčce jako modul runtime, pokusí se načíst pravidelného věcí.  
  
 Obecně platí, použití `GetFunctionFromTokenAndTypeArgs` se nedoporučuje. Pokud profilery zájem o události pro určitou funkci, měli uložit `ModuleID` a `mdMethodDef` této funkce a použití [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) zkontrolujte zda danou `FunctionID` je který požadované funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
