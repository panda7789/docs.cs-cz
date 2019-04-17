---
title: IXCLRDataProcess::GetAppDomainByUniqueId Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8b468d40ef8eb523ba8881627fae15cf9b7c7b80
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614019"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a>IXCLRDataProcess::GetAppDomainByUniqueId Method

Získá `AppDomain` v procesu podle jejího jedinečného identifikátoru.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a>Parametry

`id`\
[in] Jedinečný identifikátor třídy AppDomain

`appDomain`\
[out] Domény aplikace

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody. `IXCLRDataAppDomain*` Vrátila se používá k interakci s ostatními rozhraními API.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).
**Záhlaví:** Žádný **knihovny:** Žádný **verze rozhraní .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [IXCLRDataProcess Interface](ixclrdataprocess-interface.md)
