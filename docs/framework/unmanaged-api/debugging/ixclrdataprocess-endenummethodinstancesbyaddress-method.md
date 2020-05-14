---
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395257"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a>IXCLRDataProcess:: EndEnumMethodInstancesByAddress – metoda

Uvolní prostředky používané interními iterátory použitými během výčtu instance.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parametry

`handle`\
mimo Popisovač pro vytváření výčtu instancí metody.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 30 slotu tabulky virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Výčet CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Ladění](index.md)
- [IXCLRDataProcess – rozhraní](ixclrdataprocess-interface.md)
