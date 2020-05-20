---
title: 'ISOSDacInterface:: GetModuleData – metoda'
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
ms.openlocfilehash: b302100eb6cbfa83896cd358762c496ea01f7509
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420978"
---
# <a name="isosdacinterfacegetmoduledata-method"></a>ISOSDacInterface:: GetModuleData – metoda

Načte data odpovídající modulu načtenému na dané adrese.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a>Parametry

`moduleAddr`\
pro Adresa modulu, pro který mají být načteny informace.

`data`\
mimo [Struktura DacpModuleData](dacpmoduledata-structure.md) pro uchovávání informací načteného modulu.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `ISOSDacInterface` rozhraní a odpovídá slotu 14 tabulky virtuálních metod.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [ISOSDacInterface – rozhraní](isosdacinterface-interface.md)
