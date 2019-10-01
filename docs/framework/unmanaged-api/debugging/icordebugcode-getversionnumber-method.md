---
title: ICorDebugCode::GetVersionNumber – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b6fd6e8043f1c62da8994b43a9b9af45fb2e3c0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700813"
---
# <a name="icordebugcodegetversionnumber-method"></a>ICorDebugCode::GetVersionNumber – metoda

Získá číslo založené na čísle, které určuje verzi kódu, kterou představuje tento "ICorDebugCode".

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a>Parametry

 `nVersion`  
 mimo Ukazatel na číslo verze kódu.

## <a name="remarks"></a>Poznámky

 Číslo verze se zvýší pokaždé, když se v kódu provede operace Edit-and-Continue (EnC).

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
