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
ms.openlocfilehash: 702c5f9f2bc08c824bdc0607741a6afd65a3e89b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497254"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs – metoda
Získá `ClassID` typ pomocí zadaného tokenu metadat a `ClassID` hodnot libovolných argumentů typu.  
  
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
 pro `mdTypeDef`Token metadat, který odkazuje na typ.  
  
 `cTypeArgs`  
 pro Počet parametrů typu pro daný typ. Tato hodnota musí být nula pro neobecné typy.  
  
 `typeArgs`  
 pro Pole `ClassID` hodnot, z nichž každý je argumentem typu. Hodnota `typeArgs` může být null, pokud `cTypeArgs` je nastavena na hodnotu nula.  
  
 `pClassID`  
 mimo Ukazatel na `ClassID` určený typ.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetClassFromTokenAndTypeArgs` metody s `mdTypeRef` místo `mdTypeDef` tokenu metadat může mít nepředvídatelné výsledky; volající by `mdTypeRef` při předávání měly přeložit na `mdTypeDef` .  
  
 Pokud typ ještě není načtený, volání spustí `GetClassFromTokenAndTypeArgs` načítání, což je nebezpečná operace v mnoha kontextech. Například volání této metody během načítání modulů nebo jiných typů může vést k nekonečné smyčce, protože modul runtime se pokusí cyklicky načíst věci.  
  
 Obecně platí, že použití `GetClassFromTokenAndTypeArgs` se nedoporučuje. Pokud se profilery zajímá o události pro konkrétní typ, měly by uložit `ModuleID` a daného `mdTypeDef` typu a pomocí [ICorProfilerInfo2:: GetClassIDInfo2 –](icorprofilerinfo2-getclassidinfo2-method.md) ověřit, zda `ClassID` je daný typ určen požadovaným typem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
