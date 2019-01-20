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
ms.openlocfilehash: 3f22752446413c622a20340541b0ac328f63c77b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416123"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface::GetMethodDescData – metoda

Získá data dané [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a>Parametry

`methodDesc` [in] Adresa MethodDesc.

`ip` [in] IP adresa metody.

`data` [out] Data související s MethodDesc vrácená z interních rozhraních API. Struktura potřebuje aspoň 168 bajtů.

`cRevertedRejitVersions` [out] Počet verzí vrácený rejit.

`rgRevertedRejitData` [out] Data související s verzí vrácený rejit vrácená z interních rozhraních API. Struktura potřebuje aspoň 24 bajtů.

`pcNeededRevertedRejitData` [out] Počet bajtů vyžadovaných k uložení dat spojené s vrácený ReJit verze.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody. Také `CLRDATA_ADDRESS` jsou 64bitové celé číslo bez znaménka.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [ISOSDacInterface rozhraní](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
