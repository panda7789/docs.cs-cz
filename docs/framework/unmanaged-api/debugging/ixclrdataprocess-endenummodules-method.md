---
title: IXCLRDataProcess::EndEnumModules – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611429"
---
# <a name="ixclrdataprocessendenummodules-method"></a>IXCLRDataProcess::EndEnumModules – metoda

Uvolní prostředky využívané třídou interní iterátory využitých modulu výčtu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parametry

`handle`\
[out] Popisovač pro vytvoření výčtu moduly.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 26. pozice tabulce virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).
**Záhlaví:** Žádný **knihovny:** Žádný **verze rozhraní .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [IXCLRDataProcess Interface](ixclrdataprocess-interface.md)
