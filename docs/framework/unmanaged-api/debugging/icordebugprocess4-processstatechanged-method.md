---
title: Metoda ICorDebugProcess4::ProcessStateChanged
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178633"
---
# <a name="icordebugprocess4processstatechanged-method"></a>Metoda ICorDebugProcess4::ProcessStateChanged

Upozorní kanál ICorDebug, že ladicí program mimo proces pokračuje v provádění ladicího programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametry

 `eChange`\
[v] Člen [cordebugStateChange výčtu](cordebugstatechange-enumeration.md) popisující změnu ve stavu provádění procesu.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `ICorDebugProcess4` rozhraní a odpovídá čtvrtému slotu tabulky virtuální metody.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).

 **Záhlaví:** Žádný

 **Knihovna:** Žádný

 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také

- [ICorDebugProcess4 – rozhraní](icordebugprocess4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ladění](index.md)
