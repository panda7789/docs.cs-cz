---
title: DacpGetModulAddress::Metoda požadavku
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
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179201"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModulAddress::Metoda požadavku

Provede požadavek na naplnění struktury z dané struktury runtime.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Parametry

`pDataModule`\
[v] Ukazatel na modul dat osiva.

## <a name="remarks"></a>Poznámky

Tato struktura žije uvnitř runtime a není vystavena prostřednictvím žádné záhlaví nebo soubory knihovny. Chcete-li jej použít, nejjednodušší způsob je napodobit implementaci:

- Vrátí hodnotu získanou voláním `Request` metody parametru `IXCLRDataModule*` s následujícími parametry:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná **knihovna:** Žádná  
**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [ladění](index.md)
- [DacpGetModuleAddress rozhraní](dacpgetmoduleaddress-structure.md)
