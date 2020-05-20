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
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420952"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition – rozhraní

Poskytuje metody pro dotazování na informace o definici metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

Následující metody jsou některé z metod, které jsou k dispozici v rozhraní.

| Metoda                                                                                                                          | Popis                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Poskytuje popisovač pro výčet instancí metody pro daný objekt `IXCLRDataAppDomain` . |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Vytvoří výčet instancí této definice metody.                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Uvolní prostředky používané interními iterátory použitými během výčtu instance.         |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [Debugging – rozhraní](debugging-interfaces.md)
