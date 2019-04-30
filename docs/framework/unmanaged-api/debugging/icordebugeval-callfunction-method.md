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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66e51dc15f7d44ede26634571fa04c58e9735694
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934768"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction – metoda

Nastaví zadanou funkci volání.

Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [icordebugeval2::callparameterizedfunction –](icordebugeval2-callparameterizedfunction-method.md) místo.

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
[in] Ukazatel na objekt ICorDebugFunction, který určuje funkci, která se má volat.

`nArgs`\
[in] Počet argumentů pro funkce.

`ppArgs`\
[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který určuje argument předaný do funkce.

## <a name="remarks"></a>Poznámky

Pokud je virtuální, funkce `CallFunction` provede virtuální odeslání. Pokud je funkce v různých aplikační domény, přechod dojde, pokud jsou všechny argumenty také v této doméně aplikace.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** CorDebug.idl, CorDebug.h

**Knihovna:** CorGuids.lib

**Verze rozhraní .NET framework:** 1.1, 1.0

## <a name="see-also"></a>Viz také:

- [CallParameterizedFunction – metoda](icordebugeval2-callparameterizedfunction-method.md)