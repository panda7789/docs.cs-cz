---
title: CLRDATA_IL_ADDRESS_MAP – struktura
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179367"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP – struktura

Definuje IL pro mapování adres.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a>Členové

| Člen         | Popis                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | Il posun pro oblast obsažené adresy              |
| `startAddress` | Počáteční adresa rozsahu.                        |
| `endAddress`   | Koncová adresa rozsahu.                          |
| `type`         | Typ dat. Tato hodnota se v současné době nepoužívá. |

## <a name="remarks"></a>Poznámky

Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny. Chcete-li jej použít, definujte `CLRDATA_ADDRESS` strukturu, jak je uvedeno výše, kde je 64bitové nepodepsané celé číslo.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
**Záhlaví:** Žádný  
**Knihovna:** Žádné **verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Výčet clrdatasourcetype](clrdatasourcetype-enumeration.md)
- [ladění](index.md)
- [Struktury pro ladění](debugging-structures.md)
