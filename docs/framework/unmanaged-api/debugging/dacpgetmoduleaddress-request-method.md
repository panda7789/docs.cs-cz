---
title: DacpGetModuleAddress::Request – metoda
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860841"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Request – metoda

Provede požadavek na naplnění struktury z dané běhové struktury.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Parametry

`pDataModule`\
pro Ukazatel na modul dat o počátečních datech.

## <a name="remarks"></a>Poznámky

Tato struktura žije v modulu runtime a není vystavena prostřednictvím žádné hlavičky nebo souborů knihoven. Pokud ho chcete použít, nejjednodušší způsob je napodobení implementace:

- Vraťte hodnotu získanou z volání `Request` metody v `IXCLRDataModule*` parametru s následujícími parametry:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md)\
**Hlavička:** NTato
**Knihovna:** NTato
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [Struktura DacpGetModuleAddress](dacpgetmoduleaddress-structure.md)
