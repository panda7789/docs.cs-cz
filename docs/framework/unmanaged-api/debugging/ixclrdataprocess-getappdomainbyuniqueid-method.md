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
ms.openlocfilehash: cf610e3af26c60dd9bf738bff8785890394d0f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710271"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a>IXCLRDataProcess::GetAppDomainByUniqueId Method

Získá `AppDomain` v procesu podle jejího jedinečného identifikátoru.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

### <a name="parameters"></a>Parametry
`id` [in] Jedinečný identifikátor třídy AppDomain

`appDomain` [out] Domény aplikace

## <a name="remarks"></a>Poznámky

Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody. `IXCLRDataAppDomain*` Vrátila se používá k interakci s ostatními rozhraními API.

## <a name="requirements"></a>Požadavky
**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
