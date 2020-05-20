---
title: 'ISOSDacInterface:: GetMethodDescData – metoda'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421017"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface:: GetMethodDescData – metoda

Načte data pro daný ukazatel MethodDesc.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>Parametry

`methodDesc`\
pro Adresa MethodDesc.

`ip`\
pro IP adresa metody

`data`\
mimo Data přidružená k MethodDesc, která se vrací z interních rozhraní API.

`cRevertedRejitVersions`\
mimo Počet vrácených verzí ReJIT.

`rgRevertedRejitData`\
mimo Data přidružená k obnoveným verzím ReJIT, která se vrátila z interních rozhraní API.

`pcNeededRevertedRejitData`\
mimo Počet bajtů vyžadovaných k uložení dat přidružených k vráceným verzím ReJit.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 21. pozici tabulky virtuálních metod. Aby je bylo možné použít, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) musí být definován jako 64-bit unsigned integer.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [ISOSDacInterface – rozhraní](isosdacinterface-interface.md)
