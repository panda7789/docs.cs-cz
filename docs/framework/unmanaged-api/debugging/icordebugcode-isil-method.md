---
title: ICorDebugCode::IsIL – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: 77e55c4c3644ac4bd76f5c92152f4ee86cf5fa9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125568"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL – metoda

Získá hodnotu, která označuje, zda tento "ICorDebugCode" představuje kód, který byl zkompilován v jazyce MSIL (Microsoft Intermediate Language).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>Parametry

`pbIL`  
[out] `true`, pokud tento `ICorDebugCode` představuje kód, který byl zkompilován v jazyce MSIL; v opačném případě `false`.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
