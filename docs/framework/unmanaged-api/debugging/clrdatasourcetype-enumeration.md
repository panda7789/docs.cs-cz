---
title: Výčet CLRDataSourceType
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274098"
---
# <a name="clrdatasourcetype-enumeration"></a>Výčet CLRDataSourceType

Poskytuje hodnoty, které jsou používány strukturou CLRDATA_IL_ADDRESS_MAP.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a>Členové

| Člen                        | Popis                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | Označení, že neplatí nic jiného |

## <a name="remarks"></a>Poznámky

Tento výčet je v modulu runtime a není vystavený prostřednictvím žádné hlavičky nebo souborů knihoven. Chcete-li jej použít, definujte výčet definovaný výše v kódu. To je také alias na `CLRDATA_ENUM` to, jak je uvedeno v [Common data types](../common-data-types-unmanaged-api-reference.md).

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlaviček** Žádné  
**Knihovna** Žádné  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [Výčty pro ladění](debugging-enumerations.md)
