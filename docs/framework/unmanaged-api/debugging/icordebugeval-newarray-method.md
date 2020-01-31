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
ms.openlocfilehash: 13ac5379992f4e768b09a03d31591143ba9bf627
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788727"
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
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,1, 1,0
