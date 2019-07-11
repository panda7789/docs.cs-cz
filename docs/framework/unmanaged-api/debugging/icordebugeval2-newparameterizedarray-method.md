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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 973f975885bbbf5cbed74adef7b9f4f423c42583
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753652"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray – metoda
Přidělí nové pole typu zadaného elementu a dimenze.  
  
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
 [in] Ukazatel na objekt ICorDebugType, který představuje typ prvků uložených v poli.  
  
 `rank`  
 [in] Počet rozměrů pole. V rozhraní .NET Framework verze 2.0 tato hodnota musí být 1.  
  
 `dims`  
 [in] Velikost v bajtech každého rozměru pole.  
  
 `lowBounds`  
 [in] Volitelné. Dolní mez každé dimenze matice. Pokud je tato hodnota vynechána, předpokládá se pro jednotlivé rozměry dolní mez nula.  
  
## <a name="remarks"></a>Poznámky  
 Prvky pole mohou být instancí obecného typu. Pole je vytvořen vždy v aplikační doméně, ve kterém je spuštěn podproces. V rozhraní .NET Framework 2.0, hodnota `rank` musí být 1.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
