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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795687"
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

 Člen `CorDebugStateChange` výčtu je uveden jako argument, pokud ladicí program volá `ProcessStateChanged` metodu buď pomocí [ICorDebugProcess4::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
- [Ladění](index.md)
