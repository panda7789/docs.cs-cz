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
ms.openlocfilehash: cbea6c0562c68ae5d18247dc97bc53eb9dfbfd7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965925"
---
# <a name="dacpgetmoduleaddress-structure"></a>Struktura DacpGetModuleAddress

Definuje kontejner pro žádost o adresu modulu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
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
| [Požadavek](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | Provede požadavek na naplnit struktura ze struktury daného modulu runtime. |

## <a name="remarks"></a>Poznámky

Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Pro použití je třeba definovat strukturu jak je uvedeno výše, kde `CLRDATA_ADDRESS` je 64-bit znaménka.

## <a name="requirements"></a>Požadavky
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádné  
**Knihovna:** Žádné  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
