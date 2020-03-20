---
title: DacpModuleData – struktura
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179191"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData – struktura

Definuje vyrovnávací paměť přenosu pro informace modulu za běhu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>Členové

| Člen    | Popis                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Adresa objektu modulu.                                           |
| `File`    | Ukazatel na přenosný spustitelný soubor (PE).                       |
| `ilBase`  | Adresa základny načteného obrázku.                                 |
| `payLoad` | Vyrovnávací paměť datové části pro další informace o modulu používané modulem runtime. |

## <a name="remarks"></a>Poznámky

Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny. Chcete-li jej použít, definujte strukturu, jak je uvedeno výše.

## <a name="requirements"></a>Požadavky
**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádný  
**Knihovna:** Žádný  
**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [ladění](index.md)
- [Struktury pro ladění](debugging-structures.md)
