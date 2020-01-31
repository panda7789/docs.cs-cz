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
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790377"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess – rozhraní

Poskytuje metody pro dotazování na informace o procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                               | Popis                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Načte `AppDomain` v procesu podle jeho jedinečného ID.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Poskytuje popisovač pro zobrazení výčtu modulů procesu.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Vytvoří výčet modulů tohoto procesu.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Uvolňuje prostředky používané vnitřními iterátory použitými při výčtu modulů.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Poskytuje popisovač pro zobrazení výčtu instancí metody `AppDomain` začínajících na dané adrese. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Vytvoří výčet instancí metody tohoto procesu počínaje posunem adresy.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Uvolní prostředky používané interními iterátory použitými během výčtu instance.             |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).   
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
