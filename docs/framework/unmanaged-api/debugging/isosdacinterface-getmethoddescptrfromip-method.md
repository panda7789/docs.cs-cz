---
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP – metoda'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421004"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>ISOSDacInterface:: GetMethodDescPtrFromIP – metoda

Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>Parametry

`ip`\
pro Adresa v rámci metody za běhu.

`ppMD`\
mimo Adresa `MethodDesc` pro konkrétní metodu.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí [ `ISOSDacInterface` rozhraní](isosdacinterface-interface.md) a odpovídá slotu 22 tabulky virtuálních metod.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [ISOSDacInterface – rozhraní](isosdacinterface-interface.md)
