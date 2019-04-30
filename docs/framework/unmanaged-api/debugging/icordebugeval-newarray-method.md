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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1abe307e3b9fa607912f98e456a11176eb17c56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934755"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray – metoda
Přidělí nové pole typu zadaného elementu a dimenze.  
  
 Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [icordebugeval2::newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Hodnota corelementtype – výčet, který určuje typ prvku pole.  
  
 `pElementClass`  
 [in] Ukazatel na ICorDebugClass objekt, který určuje třídu elementu. Tato hodnota může mít hodnotu null, pokud typ prvku je primitivního typu.  
  
 `rank`  
 [in] Počet rozměrů pole. V rozhraní .NET Framework 2.0 tato hodnota musí být 1.  
  
 `dims`  
 [in] Velikost v bajtech každého rozměru pole.  
  
 `lowBounds`  
 [in] Volitelné. Dolní mez každé dimenze matice. Pokud je tato hodnota vynechána, předpokládá se pro jednotlivé rozměry dolní mez nula.  
  
## <a name="remarks"></a>Poznámky  
 Pole je vytvořen vždy v aplikační doméně, ve které vlákno právě probíhá.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0
