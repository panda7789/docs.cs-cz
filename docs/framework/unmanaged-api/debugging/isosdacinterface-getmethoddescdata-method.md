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
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396948"
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

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [ISOSDacInterface – rozhraní](isosdacinterface-interface.md)
