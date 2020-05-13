---
title: ICorDebugProcess4::P rocessStateChanged – metoda
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213566"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::P rocessStateChanged – metoda

Upozorní kanál ICorDebug, že proces ladicího programu mimo proces pokračuje v provádění laděného objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametry

 `eChange`\
pro Člen [výčtu CorDebugStateChange](cordebugstatechange-enumeration.md) popisující změnu stavu provádění procesu.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `ICorDebugProcess4` rozhraní a odpovídá čtvrtému slotu tabulky virtuální metody.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** NTato

 **Knihovna:** NTato

 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také

- [ICorDebugProcess4 – rozhraní](icordebugprocess4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
