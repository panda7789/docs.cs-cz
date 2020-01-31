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
ms.openlocfilehash: 12d4e63480f03bfad613f30362ddaeaf12b57a88
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791052"
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
|`E_FAIL`|Aktuální instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) představuje místní proměnnou.|

## <a name="remarks"></a>Poznámky

Index argumentu lze použít k načtení metadat pro tento argument.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorDebugVariableHome – rozhraní](icordebugvariablehome-interface.md)
