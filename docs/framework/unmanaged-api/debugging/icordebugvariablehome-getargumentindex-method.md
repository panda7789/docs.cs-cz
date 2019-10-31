---
title: 'ICorDebugVariableHome:: GetArgumentIndex – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125143"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome:: GetArgumentIndex – metoda

Získá index argumentu funkce.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parametry

`pArgumentIndex`\
mimo Ukazatel na index argumentu.

## <a name="return-value"></a>Návratová hodnota

Metoda vrací následující hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|`S_OK`|Volání metody vrátilo platný index argumentu.|
|`E_FAIL`|Aktuální instance [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) představuje místní proměnnou.|

## <a name="remarks"></a>Poznámky

Index argumentu lze použít k načtení metadat pro tento argument.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorDebugVariableHome – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
