---
title: IXCLRDataModule – rozhraní
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790397"
---
# <a name="ixclrdatamodule-interface"></a>IXCLRDataModule – rozhraní

Poskytuje metody pro dotazování na informace o načteném modulu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                | Popis                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [GetMethodDefinitionByToken](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | Získá definici metody odpovídající danému tokenu metadat. |
| [Požadavek](ixclrdatamodule-request-method.md)                                       | Žádosti o naplnění vyrovnávací paměti dané daty modulu.       |
| [GetVersionId](ixclrdatamodule-getversionid-method.md)                             | Získá ID verze modulu.                                       |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Ladění](index.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
