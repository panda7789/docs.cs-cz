---
title: ICorDebugEval::CallFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085162"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction – metoda

Nastaví volání zadané funkce.

Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugEval2:: CallParameterizedFunction –](icordebugeval2-callparameterizedfunction-method.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>Parametry

`pFunction`\
pro Ukazatel na objekt ICorDebugFunction, který určuje funkci, která má být volána.

`nArgs`\
pro Počet argumentů funkce.

`ppArgs`\
pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který určuje argument, který má být předán funkci.

## <a name="remarks"></a>Poznámky

Pokud je funkce virtuální, `CallFunction` provede virtuální odeslání. Pokud je funkce v jiné doméně aplikace, přechod bude proveden, pokud jsou všechny argumenty také v dané doméně aplikace.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** 1,1, 1,0

## <a name="see-also"></a>Viz také:

- [CallParameterizedFunction – metoda](icordebugeval2-callparameterizedfunction-method.md)
