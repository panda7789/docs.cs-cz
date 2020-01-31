---
title: Struktura DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789205"
---
# <a name="dacpgetmoduleaddress-structure"></a>Struktura DacpGetModuleAddress

Definuje kontejner pro požadavek na adresu modulu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>Členové

| Člen      | Popis                |
| ----------- | -------------------------- |
| `ModulePtr` | Ukazatel na modul. |

## <a name="methods"></a>Metody

| Metoda                                                                                               | Popis                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Požadavek](dacpgetmoduleaddress-request-method.md) | Provede požadavek na naplnění struktury z dané běhové struktury. |

## <a name="remarks"></a>Poznámky

Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven. Pokud ho chcete použít, definujte strukturu, jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit unsigned integer.

## <a name="requirements"></a>Požadavky
**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [Struktury pro ladění](debugging-structures.md)
