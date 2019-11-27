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
ms.openlocfilehash: 5b6c0159b432d2a70f583357bbcf714b27399633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447181"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda
Získá `ClassID` typu pomocí zadaného tokenu metadat a hodnot `ClassID` jakýchkoli argumentů typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 pro ID modulu, ve kterém se nachází typ  
  
 `typeDef`  
 pro Token metadat `mdTypeDef`, který odkazuje na typ.  
  
 `cTypeArgs`  
 pro Počet parametrů typu pro daný typ. Tato hodnota musí být nula pro neobecné typy.  
  
 `typeArgs`  
 pro Pole hodnot `ClassID`, z nichž každý je argumentem typu. Hodnota `typeArgs` může mít hodnotu NULL, pokud je `cTypeArgs` nastavena na hodnotu nula.  
  
 `pClassID`  
 mimo Ukazatel na `ClassID` zadaného typu.  
  
## <a name="remarks"></a>Poznámky  
 Volání metody `GetClassFromTokenAndTypeArgs` s `mdTypeRef` namísto tokenu metadat `mdTypeDef` může mít nepředvídatelné výsledky; Volající by při předávání měli `mdTypeDef` `mdTypeRef` vyřešit.  
  
 Pokud tento typ ještě není načtený, volání `GetClassFromTokenAndTypeArgs` spustí načítání, což je nebezpečná operace v mnoha kontextech. Například volání této metody během načítání modulů nebo jiných typů může vést k nekonečné smyčce, protože modul runtime se pokusí cyklicky načíst věci.  
  
 Obecně platí, že použití `GetClassFromTokenAndTypeArgs` se nedoporučuje. Pokud jsou profilery zajímat události pro určitý typ, měly by uložit `ModuleID` a `mdTypeDef` tohoto typu a pomocí [ICorProfilerInfo2:: GetClassIDInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) ověřit, zda je daný `ClassID`, který je požadovaného typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
