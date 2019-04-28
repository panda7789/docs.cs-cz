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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723066"
---
# <a name="cordebugstatechange-enumeration"></a>Výčet CorDebugStateChange

Popisuje množství dat uložených v mezipaměti, který musí být odstraněn podle změn do procesu.

## <a name="syntax"></a>Syntaxe

```
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Členové

| Člen            | Popis                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | Proces byl dosažen nový stav paměti prostřednictvím dopředné spuštění.            |
| `FLUSH_ALL`       | Paměť procesu může být libovolně jiný než dříve. |

## <a name="remarks"></a>Poznámky

 Členem `CorDebugStateChange` výčtu je zadaný jako argument při volání ladicího programu `ProcessStateChanged` metoda buď pomocí [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) nebo [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Požadavky

 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Záhlaví:** CorDebug.idl, CorDebug.h

 **Knihovna:** CorGuids.lib

 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [Ladění](index.md)
