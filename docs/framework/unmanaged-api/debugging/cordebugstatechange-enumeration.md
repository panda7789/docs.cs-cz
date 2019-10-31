---
title: Výčet CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133727"
---
# <a name="cordebugstatechange-enumeration"></a>Výčet CorDebugStateChange

Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Členové

| Člen            | Popis                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | Proces dosáhl nového stavu paměti prostřednictvím dopředné spuštění.            |
| `FLUSH_ALL`       | Paměť procesu může být libovolně jiná než dříve. |

## <a name="remarks"></a>Poznámky

 Člen `CorDebugStateChange` výčtu je uveden jako argument, pokud ladicí program volá metodu `ProcessStateChanged` buď pomocí [ICorDebugProcess4::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [Ladění](index.md)
