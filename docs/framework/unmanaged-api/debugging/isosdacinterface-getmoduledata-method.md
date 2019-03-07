---
title: ISOSDacInterface::GetModuleData – metoda
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: ed151f998ed7d28ba7ae170839ce2fa3a1ee6135
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490447"
---
# <a name="isosdacinterfacegetmoduledata-method"></a>ISOSDacInterface::GetModuleData – metoda

Načte data odpovídající modul načíst na dané adrese.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a>Parametry

`moduleAddr`\
[in] Adresa načíst informace pro modul.

`data`\
[out] [DacpModuleData struktura](dacpmoduledata-structure.md) k ukládání informací načteného modulu.


## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 13 pozice tabulce virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [ISOSDacInterface rozhraní](isosdacinterface-interface.md)