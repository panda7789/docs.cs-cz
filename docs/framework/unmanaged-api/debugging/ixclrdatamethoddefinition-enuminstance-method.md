---
title: 'IXCLRDataMethodDefinition:: EnumInstance – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ae1ef2a3c8cf9e042ab9ab233ed993f8e36b2fce
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420939"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>IXCLRDataMethodDefinition:: EnumInstance – metoda

Vytvoří výčet instancí této definice metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a>Parametry

`handle`\
[in, out] Popisovač pro vytváření výčtu instancí.

`instance`\
mimo Výčtová instance.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá šesté pozici tabulky virtuálních metod.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Výčet CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Ladění](index.md)
- [IXCLRDataMethodDefinition – rozhraní](ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance – rozhraní](ixclrdatamethodinstance-interface.md)
