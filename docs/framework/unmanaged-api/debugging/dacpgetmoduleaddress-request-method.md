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
ms.openlocfilehash: 07ad83da2bc608e3c5925664a68eec4a548860e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739226"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Request – metoda

Provede požadavek na naplnit struktura ze struktury daného modulu runtime.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Parametry

`pDataModule`\
[in] Ukazatel na data modulu počáteční hodnoty.

## <a name="remarks"></a>Poznámky

Tato struktura se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Jeho použití, je nejjednodušší tak, aby napodoboval implementace:

- Návratová hodnota získaný z volání funkce `Request` metodu `IXCLRDataModule*` parametr s následujícími parametry: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádné     
**Knihovna:** Žádné  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [DacpGetModuleAddress Interface](dacpgetmoduleaddress-structure.md)
