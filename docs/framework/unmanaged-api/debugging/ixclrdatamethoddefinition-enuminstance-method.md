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
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790433"
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

Poskytnutá metoda je součástí rozhraní `IXCLRDataMethodDefinition` a odpovídá čtvrtému slotu tabulky virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [CLRDataSourceType Enumeration](clrdatasourcetype-enumeration.md)
- [Ladění](index.md)
- [Rozhraní IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)
