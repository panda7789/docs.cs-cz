---
title: IXCLRDataProcess::EnumMethodInstanceByAddress Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a51c709b0b331127b74d98c4dc42e2772fd7f2db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166436"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>IXCLRDataProcess::EnumMethodInstanceByAddress Method

Vytvoří výčet metodu instance tohoto procesu začínající na posun adresy.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>Parametry

`handle`\
[in] Popisovač pro vytváření výčtu instancí metody.

`mod`\
[out] Instance výčtu metody.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 28 pozice tabulce virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).   
**Záhlaví:** Žádné   
**Knihovna:** Žádné   
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a>Viz také:

- [CLRDataSourceType Enumeration](clrdatasourcetype-enumeration.md)
- [Ladění](index.md)
- [IXCLRDataProcess – rozhraní](ixclrdataprocess-interface.md)
