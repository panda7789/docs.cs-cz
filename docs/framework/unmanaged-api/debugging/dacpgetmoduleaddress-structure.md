---
title: DacpGetModuleAddress – struktura
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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860823"
---
# <a name="dacpgetmoduleaddress-structure"></a>DacpGetModuleAddress – struktura

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
| [Žádost](dacpgetmoduleaddress-request-method.md) | Provede požadavek na naplnění struktury z dané běhové struktury. |

## <a name="remarks"></a>Poznámky

Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven. Chcete-li jej použít, definujte strukturu, jak je uvedeno `CLRDATA_ADDRESS` výše, kde je 64-bit unsigned integer.

## <a name="requirements"></a>Požadavky
**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [Struktury pro ladění](debugging-structures.md)
