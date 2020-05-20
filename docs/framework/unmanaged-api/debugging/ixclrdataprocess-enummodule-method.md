---
title: 'IXCLRDataProcess:: EnumModule – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420770"
---
# <a name="ixclrdataprocessenummodule-method"></a>IXCLRDataProcess:: EnumModule – metoda

Vytvoří výčet modulů tohoto procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a>Parametry

`handle`\
[in, out] Popisovač pro vytváření výčtu modulů.

`mod`\
mimo Výčtový modul.

## <a name="remarks"></a>Poznámky

Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 25 slotu tabulky virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Výčet CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Ladění](index.md)
- [IXCLRDataModule – rozhraní](ixclrdatamodule-interface.md)
- [IXCLRDataProcess – rozhraní](ixclrdataprocess-interface.md)
