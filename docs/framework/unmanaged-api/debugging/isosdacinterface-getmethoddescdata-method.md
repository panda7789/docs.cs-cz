---
title: ISOSDacInterface::GetMethodDescData – metoda
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
ms.openlocfilehash: 47cea4810b764005e87d00966c15cf138f5913a7
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825950"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface::GetMethodDescData – metoda

Získá data pro danou MethodDesc ukazatele.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a>Parametry

`methodDesc` [in] Adresa MethodDesc.

`ip` [in] IP adresa metody.

`data` [out] Data související s MethodDesc vrácená z interních rozhraních API.

`cRevertedRejitVersions` [out] Počet verzí vrácený rejit.

`rgRevertedRejitData` [out] Data související s verzí vrácený rejit vrácená z interních rozhraních API.

`pcNeededRevertedRejitData` [out] Počet bajtů vyžadovaných k uložení dat spojené s vrácený ReJit verze.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody. Abyste mohli využít, [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) musí být definován jako 64-bit znaménka.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [ISOSDacInterface rozhraní](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
