---
title: ICorDebugCode::GetSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89df0e9be0600b51dcc8a68c5aba3f06e86e1b53
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700803"
---
# <a name="icordebugcodegetsize-method"></a>ICorDebugCode::GetSize – metoda

Získá velikost binárního kódu reprezentovaného tímto "ICorDebugCode" (v bajtech).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a>Parametry

 `pcBytes`  
 mimo Ukazatel na velikost binárního kódu, který představuje tento objekt `ICorDebugCode` v bajtech.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
 
