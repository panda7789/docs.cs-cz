---
title: CLRDataSourceType Enumeration
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
ms.openlocfilehash: c8b3f338659e2784db8deca3e1776e7926c30c32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506081"
---
# <a name="clrdatasourcetype-enumeration"></a>CLRDataSourceType Enumeration

Obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a>Členové

| Člen                        | Popis                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | K označení, že se nic jiného vztahuje |

## <a name="remarks"></a>Poznámky

Tento výčet se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Pro použití je třeba definujte výčet definované výše ve vašem kódu. Toto je také s aliasem se přiřadila `CLRDATA_ENUM` jak je uvedeno v [běžné typy dat](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
