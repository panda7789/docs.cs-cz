---
title: 'IXCLRDataProcess:: EnumMethodInstanceByAddress – metoda'
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
ms.openlocfilehash: f3800a5980304394dd648111fe23a3bb0890c575
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395113"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>IXCLRDataProcess:: EnumMethodInstanceByAddress – metoda

Vytvoří výčet instancí metody tohoto procesu počínaje posunem adresy.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>Parametry

`handle`\
pro Popisovač pro vytváření výčtu instancí metody.

`mod`\
mimo Instance metody výčtu.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá slotu vysílání 29. tabulky virtuálních metod.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).
**Hlavička:** Žádná **Knihovna:** žádné **.NET Framework verze:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také

- [Výčet CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Ladění](index.md)
- [IXCLRDataProcess – rozhraní](ixclrdataprocess-interface.md)
