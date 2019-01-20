---
title: IXCLRDataModule Interface
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
ms.openlocfilehash: e306834166051ae48fd283d51f18d9458091578f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416109"
---
# <a name="ixclrdatamodule-interface"></a>IXCLRDataModule Interface

Poskytuje metody pro dotazování na informace o u načteného modulu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                | Popis                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [GetMethodDefinitionByToken](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getmethoddefinitionbytoken-method.md) | Získá definici metody odpovídající token daná metadata. |
| [Požadavek](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-request-method.md)                                       | Požadavky k naplnění vyrovnávací paměť přidělená s daty modulu.       |
| [GetVersionId](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getversionid-method.md)                             | Získá ID modulu verze.                                       |

## <a name="remarks"></a>Poznámky

Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , který můžete získat prostřednictvím obvykle COM mechanismů.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Záhlaví:** Žádná  
**Knihovna:** Žádná  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
