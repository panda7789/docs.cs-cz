---
title: Struktura CLRDATA_ADDRESS_RANGE
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3a8832a0eb173da00715bd0441b7efd337eae932
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416074"
---
# <a name="clrdataaddressrange-structure"></a>Struktura CLRDATA_ADDRESS_RANGE

Definuje rozsah adres.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a>Členové

| Člen         | Popis                     |
| -------------- | ------------------------------- |
| `startAddress` | Počáteční adresa rozsahu. |
| `endAddress`   | Koncová adresa rozsahu.   |

## <a name="remarks"></a>Poznámky

Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
