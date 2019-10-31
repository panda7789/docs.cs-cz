---
title: ICorDebugEval2::NewParameterizedArray – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9476bcc9706e89fd3d7e0abc14031f70a0aa0ad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084835"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray – metoda
Přidělí nové pole zadaného typu a dimenzí prvku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pElementType`  
 pro Ukazatel na objekt ICorDebugType, který představuje typ elementu uloženého v poli.  
  
 `rank`  
 pro Počet rozměrů pole. V .NET Framework verze 2,0 musí být tato hodnota 1.  
  
 `dims`  
 pro Velikost každého rozměru pole v bajtech.  
  
 `lowBounds`  
 pro Volitelné. Dolní mez každého rozměru pole. Pokud je tato hodnota vynechána, předpokládá se pro každou dimenzi spodní mez nula.  
  
## <a name="remarks"></a>Poznámky  
 Prvky pole mohou být instancemi obecného typu. Pole je vždy vytvořeno v doméně aplikace, ve které je vlákno aktuálně spuštěno. V .NET Framework 2,0 musí být hodnota `rank` 1.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
