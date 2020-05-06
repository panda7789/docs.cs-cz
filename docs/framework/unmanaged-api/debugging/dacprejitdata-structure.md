---
title: DacpReJitData – struktura
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 4436ece72b0a6a405fc41cba5413093fc42ce750
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860775"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData – struktura

Definuje základní informace o dané metodě instrumentace profileru.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>Členové

| Člen           | Popis                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | Číslo revize ReJit pro metodu.                                                          |
| `flags`          | Příznak označující aktuální stav instrumentace ReJit metody pro danou verzi. |
| `NativeCodeAddr` | Základní adresa implementace rejitted metody.                                         |

## <a name="remarks"></a>Poznámky

Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven. Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše. Pokud nepoužíváte kompilátory od `ms_struct` společnosti Microsoft, musí být struktura definována také pomocí balení.

## <a name="requirements"></a>Požadavky
**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [Struktury pro ladění](debugging-structures.md)
