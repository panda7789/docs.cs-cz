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
ms.openlocfilehash: 391b848d3b3f66f6af6bf3adbefb6e94d526e748
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213501"
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

`GetVersion`Metoda vrátí kód chyby, pokud nebyl v procesu načten modul runtime.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
