---
title: ICorDebugProcess2::GetVersion – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 5f618f6779f6931785bba18f70fb1ac9baf46753
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137196"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion – metoda

Získá číslo verze modulu CLR (Common Language Runtime), který je spuštěn v tomto procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>Parametry

`version`\
mimo Ukazatel na strukturu COR_VERSION, která ukládá číslo verze modulu runtime.

## <a name="remarks"></a>Poznámky

Metoda `GetVersion` vrátí kód chyby, pokud nebyl v procesu načten modul runtime.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
