---
title: CLRDATA_IL_ADDRESS_MAP Structure
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
ms.openlocfilehash: 3aac7e24fa9cd03350aebf5f441063bcedfaed04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644765"
---
# <a name="clrdatailaddressmap-structure"></a>CLRDATA_IL_ADDRESS_MAP Structure

Definuje mapování adresy IL.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
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
| `ilOffset`     | Posun IL pro rozsah adres omezením              |
| `startAddress` | Počáteční adresa rozsahu.                        |
| `endAddress`   | Koncová adresa rozsahu.                          |
| `type`         | Typ data. Tato hodnota není aktuálně používá. |

## <a name="remarks"></a>Poznámky

Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná   
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [CLRDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
