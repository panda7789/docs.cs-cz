---
title: IXCLRDataProcess – rozhraní
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178378"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess – rozhraní

Poskytuje metody pro dotazování na informace o procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                               | Popis                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Získá `AppDomain` v procesu jeho jedinečné id.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Poskytuje popisovač pro výčet modulů procesu.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Vyjmenovává moduly tohoto procesu.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Uvolní prostředky používané interními iterátory používanými při výčtu modulu.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Poskytuje popisovač pro výčet instance metody `AppDomain` počínaje danou adresou. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Vyjmenovává instance metody tohoto procesu počínaje posunem adresy.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Uvolní prostředky používané interními iterátory používanými při výčtu instancí.             |

## <a name="remarks"></a>Poznámky

Toto rozhraní žije uvnitř modulu runtime a není vystaveno prostřednictvím žádné hlavičky nebo soubory knihovny. Je to však rozhraní COM, `IUnknown` které je `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` odvozeno z s identifikátorem GUID, které lze získat prostřednictvím obvyklých mechanismů COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).
**Záhlaví:** Žádný  
**Knihovna:** Žádný  
**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [ladění](index.md)
- [Debugging – rozhraní](debugging-interfaces.md)
