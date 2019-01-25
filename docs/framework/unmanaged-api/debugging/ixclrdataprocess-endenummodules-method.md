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
ms.openlocfilehash: 50ad55674360d7b880af3ddf701cf17005f30ce7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722735"
---
# <a name="ixclrdataprocessendenummodules-method"></a>IXCLRDataProcess::EndEnumModules – metoda

Uvolní prostředky využívané třídou interní iterátory využitých modulu výčtu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a>Parametry
`handle` [out] Popisovač pro vytvoření výčtu moduly.

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 26. pozice tabulce virtuální metody.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).   
**Záhlaví:** Žádná   
**Knihovna:** Žádná   
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   

## <a name="see-also"></a>Viz také:

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
