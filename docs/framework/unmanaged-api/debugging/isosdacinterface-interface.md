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
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420965"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface – rozhraní

Poskytuje pomocné metody pro přístup k datům z `SOS` .

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                               | Popis                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | Načte data pro daný ukazatel MethodDesc. |
| [GetMethodDescPtrFromIP](isosdacinterface-getmethoddescptrfromip-method.md) | Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce. |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| Načte data odpovídající modulu načtenému na dané adrese. |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** NTato  
**Knihovna:** NTato  
**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Viz také

- [Ladění](index.md)
- [Debugging – rozhraní](debugging-interfaces.md)
