---
title: IXCLRDataMethodDefinition::EndEnumInstances Method
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7901ba3ac95052e265df619d06996b4c9ce8baa6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416076"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a>IXCLRDataMethodDefinition::EndEnumInstances Method

Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a>Parametry

`handle` [out] Popisovač pro vytváření výčtu instancí.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá na páté slot v tabulce virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataMethodDefinition rozhraní](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
