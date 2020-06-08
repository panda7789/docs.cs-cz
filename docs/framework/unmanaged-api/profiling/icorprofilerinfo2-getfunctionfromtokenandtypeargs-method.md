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
ms.openlocfilehash: 7f1276e1adeece086ca7b6791eb6e870faf4d010
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502870"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs – metoda
Získá `FunctionID` funkci pomocí zadaného tokenu metadat obsahujícího třídu a `ClassID` hodnot libovolných argumentů typu.  
  
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
 pro ID modulu, ve kterém je funkce umístěna.  
  
 `funcDef`  
 pro `mdMethodDef`Token metadat, který odkazuje na funkci.  
  
 `classId`  
 pro ID obsahující třídy funkce  
  
 `cTypeArgs`  
 pro Počet parametrů typu pro danou funkci. Pro neobecné funkce musí být tato hodnota nula.  
  
 `typeArgs`  
 pro Pole `ClassID` hodnot, z nichž každý je argumentem funkce. Hodnota `typeArgs` může být null, pokud `cTypeArgs` je nastavena na hodnotu nula.  
  
 `pFunctionID`  
 mimo Ukazatel na `FunctionID` určenou funkci.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetFunctionFromTokenAndTypeArgs` metody s `mdMethodRef` metadaty namísto `mdMethodDef` tokenu metadat může mít nepředvídatelné výsledky. Volající by při předávání měli metodu vyřešit `mdMethodRef` na `mdMethodDef` .  
  
 Pokud funkce ještě není načtená, volání `GetFunctionFromTokenAndTypeArgs` způsobí nasazování, což je nebezpečná operace v mnoha kontextech. Například volání této metody během načítání modulů nebo typů může vést k nekonečné smyčce, protože modul runtime se pokusí cyklicky načíst věci.  
  
 Obecně platí, že použití `GetFunctionFromTokenAndTypeArgs` se nedoporučuje. Pokud se profilery zajímá o události pro konkrétní funkci, měly by uložit `ModuleID` a příslušné `mdMethodDef` funkce a pomocí [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) ověřit, zda daná `FunctionID` funkce má požadovanou funkci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
