---
title: ICorDebugCodeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 076b5d628dfe83decdbbe2f5e74c50e08262c580
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700683"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next – metoda

Získá zadaný počet instancí "ICorDebugCode" z výčtu počínaje aktuální pozicí.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>Parametry

 `celt`  
 pro Počet instancí `ICorDebugCode`, které mají být načteny.

 `values`  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt @no__t 0.

 `pceltFetched`  
 mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugCode`. Tato hodnota může být null, pokud `celt` je jedna.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 
