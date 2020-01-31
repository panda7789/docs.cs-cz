---
title: IXCLRDataMethodDefinition – rozhraní
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790423"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition – rozhraní

Poskytuje metody pro dotazování na informace o definici metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

Následující metody jsou některé z metod, které jsou k dispozici v rozhraní.

| Metoda                                                                                                                          | Popis                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Poskytuje popisovač pro výčet instancí metody pro daný `IXCLRDataAppDomain`. |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Vytvoří výčet instancí této definice metody.                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Uvolní prostředky používané interními iterátory použitými během výčtu instance.         |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
