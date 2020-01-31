---
title: ISOSDacInterface – rozhraní
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790483"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface – rozhraní

Poskytuje pomocné metody pro přístup k datům z `SOS`.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                               | Popis                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | Načte data pro daný ukazatel MethodDesc. |
| [GetMethodDescPtrFromIP](isosdacinterface-getmethoddescptrfromip-method.md) | Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce. |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| Načte data odpovídající modulu načtenému na dané adrese. |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `436f00f2-b42a-4b9f-870c-e73db66ae930`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
