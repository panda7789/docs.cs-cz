---
title: ICorDebugEval::NewArray – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 496a6a7e01dec8aa90ba4e849c431ccd499ef53d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976197"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray – metoda
Přidělí nové pole zadaného typu a dimenzí prvku.  
  
 Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugEval2:: newparameterizedarray –](icordebugeval2-newparameterizedarray-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 pro Hodnota výčtu CorElementType –, která určuje typ prvku pole.  
  
 `pElementClass`  
 pro Ukazatel na objekt ICorDebugClass, který určuje třídu prvku. Tato hodnota může být null, pokud je typ prvku primitivní typ.  
  
 `rank`  
 pro Počet rozměrů pole. V .NET Framework 2,0 musí být tato hodnota 1.  
  
 `dims`  
 pro Velikost každého rozměru pole v bajtech.  
  
 `lowBounds`  
 pro Volitelné. Dolní mez každého rozměru pole. Pokud je tato hodnota vynechána, předpokládá se pro každou dimenzi spodní mez nula.  
  
## <a name="remarks"></a>Poznámky  
 Pole je vždy vytvořeno v doméně aplikace, ve které je vlákno aktuálně prováděno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,1, 1,0
